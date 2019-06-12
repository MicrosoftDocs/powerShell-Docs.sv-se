---
ms.date: 06/03/2019
keywords: PowerShell cmdlet
title: Arbeta med programinstallationer
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830294"
---
# <a name="working-with-software-installations"></a>Arbeta med programinstallationer

Program som är utformade för att använda Windows Installer kan nås via WMI **Win32_Product** klass, men inte alla program som används idag använder installationsprogrammet för Windows.
Program som använder alternativa installationsprogrammet rutiner hanteras vanligtvis inte av Windows Installer.
Specifika tekniker för att arbeta med dessa program är beroende av den installationsprogram för programvara och de beslut som görs av programutvecklaren. Program som har installerats genom att kopiera filerna till en mapp på datorn vanligtvis kan exempelvis inte hanteras med hjälp av tekniker som beskrivs här. Du kan hantera de här programmen filer och mappar med hjälp av metoder som beskrivs i [arbeta med filer och mappar](Working-with-Files-and-Folders.md).

> [!CAUTION]
> Den **Win32_Product** klass är inte optimerad-fråga. Frågor som använder jokertecken filter orsaka WMI för att räkna upp alla installerade produkter och parsa en fullständig lista i tur och ordning för att hantera filtret med MSI-providern. Detta initierar också en konsekvenskontroll av paket installeras, verifiera och reparera installationen. Verifieringen är lång tid och kan resultera i fel i händelseloggarna. Mer information om du söker efter [KB-artikel 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Visa en lista över Windows Installer-program

Om du vill visa de program som installeras med Windows Installer på en lokal eller fjärransluten dator, använder du följande enkla WMI-fråga:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Att visa alla egenskaper för den **Win32_Product** objekt ska visas, Använd den **egenskaper** parametern formatering cmdlets som de `Format-List` cmdlet med ett värde på `*` (alla).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

Du kan använda den `Get-CimInstance` **Filter** parametern att välja endast Microsoft .NET Framework 2.0. Värdet för den **Filter** parametern använder WMI-frågespråket (WQL) syntax, inte Windows PowerShell-syntax. Till exempel:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

Om du vill visa egenskaperna som intresserar dig, använder den **egenskapen** parametern formatering cmdletar att lista de önskade egenskaperna.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Visa en lista över alla Uninstallable program

Eftersom de flesta program registrera en avinstallation med Windows, kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret. Det finns ingen garanterad sättet att hitta alla program på ett system. Det är dock möjligt att hitta alla program med listor som visas i **Lägg till eller ta bort program**. **Lägg till eller ta bort program** söker efter de här programmen i följande registernyckel:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Vi kan granska den här nyckeln för att hitta program. Om du vill göra det enklare att visa nyckeln Uninstall, kan vi ansluta en PowerShell-enhet till den platsen som:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
Nu har vi en enhet med namnet ”avinstallera”: som kan användas för att snabbt och enkelt leta efter programinstallationer. Vi kan hitta antalet installerade program genom att räkna antalet registernycklar i avinstallationen: PowerShell-enhet:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

Vi kan söka denna lista över ytterligare program med hjälp av en mängd olika tekniker, från och med **Get-ChildItem**. Hämta en lista över program och spara dem i den **$UninstallableApplications** variabel, använder du följande kommando:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

För att visa värdena för registerposterna i registernycklarna under avinstallationen, använder du metoden GetValue i registernycklarna. Värdet för metoden är namnet på registerposten.

Till exempel för att hitta visningsnamnen för program i nyckeln Uninstall, använder du följande kommando:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Det är inte säkert att dessa värden är unika. I följande exempel visas två installerade objekt som ”Windows Media Encoder 9 Series”:

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Installera program

Du kan använda den **Win32_Product** klassen för att installera Windows Installer-paket via fjärranslutning eller lokalt.

> [!NOTE]
> Om du vill installera ett program måste du starta PowerShell med alternativet ”Kör som administratör”.

När du installerar via fjärranslutning, måste du använda en nätverkssökväg för Universal Naming Convention (UNC) för att ange sökvägen till MSI-paketet, eftersom undersystemet WMI inte förstår PowerShell-sökvägar. Till exempel att installera paketet NewPackage.msi finns i nätverksresursen `\\AppServ\dsp` på fjärrdatorn PC01, skriver du följande kommando i PowerShell-Kommandotolken:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Program som inte använder Windows Installer-tekniken kan ha programspecifika metoder för automatisk distribution. Läs i dokumentationen till programmet eller kontakta tillverkaren av programmet supportsystem.

## <a name="removing-applications"></a>Ta bort program

Ta bort en Windows Installer-paketet med hjälp av PowerShell fungerar på ungefär samma sätt som installerar ett paket. Här är ett exempel som väljer att avinstallera paketet baserat på dess namn. i vissa fall kan det vara enklare att filtrera med den **IdentifyingNumber**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Ta bort andra program är inte var så enkel, även när du är klar lokalt. Vi kan hitta kommandoraden avinstallera strängar för dessa program genom att extrahera den **UninstallString** egenskapen.
Den här metoden fungerar för Windows Installer-program och för äldre program som visas under nyckeln Uninstall:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Du kan filtrera resultatet efter visningsnamn, om du vill:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Men kan dessa strängar inte användas direkt från PowerShell-prompten utan några ändringar.

## <a name="upgrading-windows-installer-applications"></a>Uppgradera Windows Installer-program

Om du vill uppgradera ett program som du behöver veta namnet på programmet och sökvägen på uppgraderingspaketet för programmet. Med denna information kan du uppgradera ett program med ett enda PowerShell-kommando:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
