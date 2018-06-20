---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med programinstallationer
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952825"
---
# <a name="working-with-software-installations"></a>Arbeta med programinstallationer

Program som är utformade för att använda Windows Installer kan nås via WMI **Win32_Product** klass, men inte alla program som används idag med hjälp av Windows Installer. Eftersom Windows Installer innehåller bredast utbud av vanliga tekniker för att arbeta med program kan installeras, fokuserar vi främst på programmen. Program som använder alternativa installationsprogrammet rutiner vanligtvis hanteras inte av Windows Installer. Specifika tekniker för att arbeta med dessa program beror på installationsprogrammet och programutvecklaren beslut.

> [!NOTE]
> Program som har installerats genom att kopiera vanligtvis programfilerna på datorn kan inte hanteras av med metoder som beskrivs här. Du kan hantera de här programmen filer och mappar med hjälp av de metoder som beskrivs i avsnittet ”Arbeta med filer och mappar”.

### <a name="listing-windows-installer-applications"></a>Visar en lista över Windows Installer-program

Använd följande enkla WMI-fråga om du vill visa de program som installerats med Windows Installer på en lokal eller fjärransluten dator:

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

Om du vill visa alla egenskaper i objektet Win32_Product visas, använder du parametern egenskaper formatering cmdlets, till exempel Format-List-cmdlet med ett värde för \* (alla).

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

Du kan använda den **Get-WmiObject Filter** parametern att välja endast Microsoft .NET Framework 2.0. Eftersom det filter som används i det här kommandot är en WMI-filter, använder WMI WQL (Query Language) syntax, inte Windows PowerShell-syntax. I stället:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

Observera att WQL-frågor ofta använda tecken som blanksteg eller likhetstecken som har en särskild innebörd i Windows PowerShell. Därför är det klokt att alltid ange värdet för parametern Filter inom citattecken. Du kan också använda Windows PowerShell escape-tecken, ett backtick (\`), även om det inte kan förbättra läsbarhet. Följande kommando motsvarar det föregående kommandot returnerar samma resultat och använder backtick för att undanta specialtecken i stället för hela Filtersträngen textkommando.

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

Använd parametern egenskapen formatering cmdlet för att lista egenskaperna om du vill visa endast de egenskaper som intresserar dig.

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

Slutligen installerade program, ett enkelt att hitta bara namnen på **Format hela** instruktionen förenklar utdata:

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

Nu har vi titta på program som används av Windows Installer för installation på flera olika sätt, men vi har inte upp andra program. Eftersom de flesta program registrerar sina avinstallationsprogrammet med Windows, kan vi arbetar med dem lokalt genom att söka efter dem i Windows-registret.

### <a name="listing-all-uninstallable-applications"></a>Visar en lista över alla Uninstallable program

Även om det finns inget garanterad sätt att hitta alla program på ett system, är det möjligt att söka efter alla program med listor visas i dialogrutan Lägg till eller ta bort program. Lägg till eller ta bort program hittar programmen i följande registernyckel:

**HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion\\avinstallera**.

Vi kan även undersöka den här nyckeln om du vill söka efter program. Om du vill göra det enklare att visa nyckeln Uninstall, mappa vi en Windows PowerShell-enhet till denna plats i registret:

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> Den **HKLM:** enheten är mappad till roten i **HKEY_LOCAL_MACHINE**, så vi använde den här enheten i sökvägen till nyckeln Uninstall. I stället för **HKLM:** kunde vi angett registersökvägen genom att använda antingen **HKLM** eller **HKEY_LOCAL_MACHINE**. Fördelen med att använda en befintlig enhet i registret är att du kan använda fliken slutförande för att fylla i namn nycklar, så vi inte behöver ange dem.

Nu har vi en enhet med namnet ”avinstallera” som kan användas för att snabbt och enkelt leta efter programinstallationer. Vi kan ta reda på antalet installerade program genom att räkna antalet registernycklar i avinstallationen: Windows PowerShell-enhet:

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

Vi kan söka denna lista över ytterligare program med hjälp av en mängd olika tekniker, börjar med **Get-ChildItem**. Hämta en lista över program och spara dem i den **$UninstallableApplications** variabel, använder du följande kommando:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> Vi använder långa namn på variabler för tydlighetens skull. Det finns ingen anledning att använda långa namn för faktiska används. Du kan använda fliken slutförande för variabelnamn, men du kan också använda 1 – 2 tecken namn för hastighet. Längre, beskrivande namn är mest användbara när du utvecklar koden för återanvändning.

Använd metoden GetValue registernycklar för att visa värden registerposter i registernycklarna under avinstallationen. Värdet för metoden är namnet på posten i registret.

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

### <a name="installing-applications"></a>Installera program

Du kan använda den **Win32_Product** klassen för att installera Windows Installer-paket via fjärranslutning eller lokalt.

> [!NOTE]
> I Windows Vista, Windows Server 2008 och senare versioner av Windows för att installera ett program måste du starta Windows PowerShell med alternativet ”Kör som administratör”.

När du installerar via fjärranslutning, måste du använda en nätverkssökväg för Universal Naming Convention (UNC) för att ange sökvägen till MSI-paketet, eftersom undersystemet WMI inte förstår sökvägar för Windows PowerShell. Till exempel att installera paketet NewPackage.msi finns i nätverksresursen \\ \\AppServ\\dsp på fjärrdatorn PC01, Skriv följande kommando i Kommandotolken för Windows PowerShell:

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

Program som inte använder Windows Installer-tekniken kan ha programspecifika metoder tillgängliga för automatisk distribution. För att fastställa om det finns en metod för automatisering av distribution finns i dokumentationen för programmet eller kontakta tillverkaren av programmet stöd för system. I vissa fall, även om leverantören av tillämpningsprogrammet inte specifikt utforma program för installation av automation kanske installer tillverkaren vissa tekniker för automatisering.

### <a name="removing-applications"></a>Ta bort program

Tar bort en Windows Installer-paketet med hjälp av Windows PowerShell fungerar på ungefär samma sätt som installerar ett paket. Här är ett exempel som väljer att avinstallera paketet baserat på dess namn. i vissa fall kan det vara lättare att filtrera med den **IdentifyingNumber**:

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

Ta bort andra program är inte var så enkel, även när klar lokalt. Vi kan hitta kommandoraden avinstallera strängar för dessa program genom att extrahera den **UninstallString** egenskapen. Den här metoden fungerar för Windows Installer-program och äldre program som visas under nyckeln Uninstall:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Du kan filtrera resultatet av visningsnamn, om du vill:

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Dock kan dessa strängar inte användas direkt från Windows PowerShell-Kommandotolken utan några ändringar.

### <a name="upgrading-windows-installer-applications"></a>Uppgradera Windows Installer-program

Om du vill uppgradera ett program som du behöver känna till namnet på programmet och sökvägen till programmet uppgraderingspaket. Med denna information kan du uppgradera ett program med ett enda Windows PowerShell-kommando:

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```