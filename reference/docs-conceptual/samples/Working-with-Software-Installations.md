---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med programinstallationer
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984348"
---
# <a name="working-with-software-installations"></a>Arbeta med programinstallationer

Program som är utformade för att använda Windows Installer kan nås via WMI **Win32_Product** klass, men inte alla program som används idag använder installationsprogrammet för Windows. Eftersom Windows Installer innehåller lugnet standard tekniker för att arbeta med program som kan installeras, fokuserar vi främst på dessa program. Program som använder alternativa installationsprogrammet rutiner Allmänt hanteras inte av Windows Installer. Specifika tekniker för att arbeta med dessa program beror på den installationsprogram för programvara och de beslut som görs av programutvecklaren.

> [!NOTE]
> Program som är installerade genom att kopiera vanligtvis programfilerna på datorn kan inte hanteras med hjälp av tekniker som beskrivs här. Du kan hantera de här programmen filer och mappar med hjälp av de metoder som beskrivs i avsnittet ”Arbeta med filer och mappar”.

## <a name="listing-windows-installer-applications"></a>Visa en lista över Windows Installer-program

Om du vill visa de program som installeras med Windows Installer på en lokal eller fjärransluten dator, använder du följande enkla WMI-fråga:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Använd parametern egenskaper för cmdletarna formatering som Format-List-cmdlet för att visa alla egenskaper för objektet Win32_Product det som visningen på, med värdet \* (alla).

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

Du kan använda den **Get-WmiObject Filter** parametern att välja endast Microsoft .NET Framework 2.0. Eftersom det filter som används i det här kommandot är ett WMI-filter, använder WMI-frågespråket (WQL) syntax, inte Windows PowerShell-syntax. Instead,:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Observera att WQL-frågor ofta använda tecken som blanksteg eller likhetstecknen som har en särskild betydelse i Windows PowerShell. Därför är det klokt att alltid ange värdet för Filterparametern inom citattecken. Du kan också använda Windows PowerShell escape-tecknet, en backtick (\`), men det inte kan förbättra läsbarheten. Följande kommando motsvarar det föregående kommandot och returnerar samma resultat, men använder backtick för att undvika specialtecken, i stället för att citera hela Filtersträngen.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Visa endast de egenskaper som intresserar dig genom att använda parametern egenskapen formatering cmdletar för att lista de önskade egenskaperna.

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

Slutligen installerade program, en enkel att hitta bara namnen på **Format hela** instruktionen förenklar utdata:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Nu har vi flera olika sätt att titta på program som använde Windows Installer för installationen, men vi har inte vara andra program. Eftersom de flesta program registrera sina avinstallationsprogrammet med Windows, kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret.

## <a name="listing-all-uninstallable-applications"></a>Visa en lista över alla Uninstallable program

Även om det finns inget garanterad sätt att hitta alla program på ett system, går det att hitta alla program med listor som visas i dialogrutan Lägg till eller ta bort program. Lägg till eller ta bort program söker efter de här programmen i följande registernyckel:

**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.

Vi kan också granska den här nyckeln för att hitta program. Om du vill göra det enklare att visa nyckeln Uninstall, kan vi ansluta en Windows PowerShell-enhet till den platsen som:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> Den **HKLM:** enhet har mappats till roten **HKEY_LOCAL_MACHINE**, så vi använde den här enheten i sökvägen till nyckeln Uninstall. I stället för **HKLM:** kunde vi angett registersökvägen genom att använda antingen **HKLM** eller **HKEY_LOCAL_MACHINE**. Fördelen med att använda en befintlig register-enhet är att vi kan använda tabbifyllning för att fylla i nycklar-namn, så vi inte behöver ange dem.

Nu har vi en enhet med namnet ”avinstallera” som kan användas för att snabbt och enkelt söka efter programinstallationer. Vi kan hitta antalet installerade program genom att räkna antalet registernycklar i avinstallationen: Windows PowerShell-enhet:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Vi kan söka denna lista över ytterligare program med hjälp av en mängd olika tekniker, från och med **Get-ChildItem**. Hämta en lista över program och spara dem i den **$UninstallableApplications** variabel, använder du följande kommando:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Vi använder långa namn på variabler för tydlighetens skull. I själva verket får finns det ingen anledning att använda långa namn. Du kan använda tabbifyllning för variabelnamn, men du kan också använda 1 – 2 tecken namn för hastighet. Längre, beskrivande namn är mest användbara när du utvecklar kod för återanvändning.

För att visa värdena för registerposterna i registernycklarna under avinstallationen, använder du metoden GetValue i registernycklarna. Värdet för metoden är namnet på registerposten.

Till exempel för att hitta visningsnamnen för program i nyckeln Uninstall, använder du följande kommando:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Det är inte säkert att dessa värden är unika. I följande exempel visas två installerade objekt som ”Windows Media Encoder 9 Series”:

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a>Installera program

Du kan använda den **Win32_Product** klassen för att installera Windows Installer-paket via fjärranslutning eller lokalt.

> [!NOTE]
> På Windows Vista, Windows Server 2008 och senare versioner av Windows, om du vill installera ett program, måste du starta Windows PowerShell med alternativet ”Kör som administratör”.

När du installerar via fjärranslutning, måste du använda en nätverkssökväg för Universal Naming Convention (UNC) för att ange sökvägen till MSI-paketet, eftersom undersystemet WMI inte förstår Windows PowerShell-sökvägar. Till exempel att installera paketet NewPackage.msi finns i nätverksresursen \\ \\AppServ\\dsp på fjärrdatorn PC01, Skriv följande kommando i Windows PowerShell-Kommandotolken:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Program som inte använder Windows Installer-tekniken kan ha programspecifika metoder för automatisk distribution. För att avgöra om det finns en metod för distribution, i dokumentationen till programmet eller kontakta tillverkaren av programmet supportsystem. I vissa fall kan även om programleverantören inte specifikt utforma programmet för installationen automation kanske installationsprogram för programvara tillverkare vissa tekniker för automatisering.

## <a name="removing-applications"></a>Ta bort program

Ta bort en Windows Installer-paketet med hjälp av Windows PowerShell fungerar på ungefär samma sätt som installerar ett paket. Här är ett exempel som väljer att avinstallera paketet baserat på dess namn. i vissa fall kan det vara enklare att filtrera med den **IdentifyingNumber**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Ta bort andra program är inte var så enkel, även när du är klar lokalt. Vi kan hitta kommandoraden avinstallera strängar för dessa program genom att extrahera den **UninstallString** egenskapen. Den här metoden fungerar för Windows Installer-program och för äldre program som visas under nyckeln Uninstall:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Du kan filtrera resultatet efter visningsnamn, om du vill:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Men kan dessa strängar inte användas direkt från Windows PowerShell-prompten utan några ändringar.

## <a name="upgrading-windows-installer-applications"></a>Uppgradera Windows Installer-program

Om du vill uppgradera ett program som du behöver veta namnet på programmet och sökvägen på uppgraderingspaketet för programmet. Med denna information kan du uppgradera ett program med ett enda Windows PowerShell-kommando:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```