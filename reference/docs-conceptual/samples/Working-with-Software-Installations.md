---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Arbeta med programinstallationer
description: Den här artikeln visar hur du använder WMI för att hantera program vara som är installerad i Windows.
ms.openlocfilehash: 3cf8e3c58e9f2814e2551b3602bd7b47b375aed8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500886"
---
# <a name="working-with-software-installations"></a>Arbeta med programinstallationer

Program som har utformats för att använda Windows Installer kan nås via WMI: s **Win32_Product** -klass, men inte alla program som används idag använder Windows Installer.
Program som använder alternativa installations rutiner hanteras vanligt vis inte av Windows Installer.
Specifika metoder för att arbeta med dessa program beror på installations programmet och de beslut som fattas av programutvecklaren. Exempel: program som installeras genom att kopiera filerna till en mapp på datorn kan vanligt vis inte hanteras med hjälp av tekniker som beskrivs här. Du kan hantera dessa program som filer och mappar med hjälp av de metoder som beskrivs i [arbeta med filer och mappar](Working-with-Files-and-Folders.md).

> [!CAUTION]
> Den **Win32_Product** klassen är inte fråga optimerad. Frågor som använder filter för jokertecken gör att WMI kan använda MSI-providern för att räkna upp alla installerade produkter och sedan tolka den fullständiga listan i turordning för att hantera filtret. Detta initierar också en konsekvens kontroll av installerade paket, verifierar och reparerar installationen. Verifieringen är en långsam process och kan resultera i fel i händelse loggarna. Mer information om att söka [KB-artikel 974524](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Visa Windows Installer program

Om du vill visa en lista över de program som har installerats med Windows Installer på ett lokalt system eller fjärrsystem använder du följande enkla WMI-fråga:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

Om du vill visa alla egenskaper för **Win32_Product** -objektet som ska visas använder du **egenskaps** parametern för cmdletarna för formatering, till exempel `Format-List` cmdleten, med värdet `*` (all).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
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

Du kan också använda `Get-CimInstance` **filter** parametern för att välja endast Microsoft .NET 2,0-körningsmiljön. Värdet för **filter** parametern använder WMI Query Language (WQL) syntax, inte Windows PowerShell-syntax. Exempel:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

Om du vill visa en lista över de egenskaper som intresserar dig använder du **egenskaps** parametern för cmdletarna för att Visa önskade egenskaper.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Visa alla program som inte går att installera

Eftersom de flesta standard program registrerar en avinstallation med Windows kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret. Det finns inget garanterat sätt att hitta alla program på ett system. Det är dock möjligt att hitta alla program med listor som visas i **Lägg till eller ta bort program** i följande register nyckel:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

Vi kan granska den här nyckeln för att hitta program. Vi kan göra det enklare att Visa avinstallations nyckeln genom att mappa en PowerShell-enhet till den här register platsen:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

Nu har vi en enhet med namnet "Uninstall:" som kan användas för att snabbt och bekvämt söka efter programinstallationer. Vi kan hitta antalet installerade program genom att räkna antalet register nycklar i Uninstall: PowerShell-enheten:

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

Vi kan söka i den här listan över program ytterligare med hjälp av en mängd olika tekniker, från och med `Get-ChildItem` . Använd följande kommando för att hämta en lista över program och spara dem i `$UninstallableApplications` variabeln:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Om du vill visa värdena för register posterna i register nycklarna under Uninstall använder du metoden GetValue i register nycklarna. Metodens värde är namnet på register posten.

Om du till exempel vill hitta visnings namnen för program i avinstallations nyckeln använder du följande kommando:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Det finns ingen garanti för att dessa värden är unika. I följande exempel visas två installerade objekt som "Windows Media Encoder 9 Series":

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a>Installera program

Du kan använda **Win32_Product** -klassen för att installera Windows Installer-paket, via fjärr anslutning eller lokalt.

> [!NOTE]
> För att installera ett program måste du starta PowerShell med alternativet "kör som administratör".

När du installerar via fjärr anslutning använder du en nätverks Sök väg för Universal Naming Convention (UNC) för att ange sökvägen till. MSI-paketet, eftersom WMI-undersystemet inte förstår PowerShell-sökvägar. Om du till exempel vill installera NewPackage.msi paketet som finns på nätverks resursen `\\AppServ\dsp` på fjärrdatorn PC01, skriver du följande kommando i PowerShell-prompten:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Program som inte använder Windows Installer teknik kan ha programspecifika metoder för automatisk distribution. Kontrol lera programmets dokumentation eller kontakta program leverantörens support system.

## <a name="removing-applications"></a>Ta bort program

Att ta bort ett Windows Installer-paket med PowerShell fungerar på ungefär samma sätt som när du installerar ett paket. Här är ett exempel som väljer vilket paket som ska avinstalleras baserat på dess namn. i vissa fall kan det vara lättare att filtrera med **IdentifyingNumber**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

Det är inte riktigt enkelt att ta bort andra program, även när du har gjort det lokalt. Vi kan hitta kommando rads avinstallations strängar för dessa program genom att extrahera egenskapen **UninstallString** .
Den här metoden fungerar för Windows Installer program och för äldre program som visas under avinstallations nyckeln:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Du kan filtrera utdata efter visnings namnet om du vill:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Dessa strängar är dock inte direkt användbara från PowerShell-prompten utan någon ändring.

## <a name="upgrading-windows-installer-applications"></a>Uppgradera Windows Installer program

Om du vill uppgradera ett program måste du känna till namnet på programmet och sökvägen till program uppgraderings paketet. Med den informationen kan du uppgradera ett program med ett enda PowerShell-kommando:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
