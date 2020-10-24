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
# <a name="working-with-software-installations"></a><span data-ttu-id="1f0e8-104">Arbeta med programinstallationer</span><span class="sxs-lookup"><span data-stu-id="1f0e8-104">Working with Software Installations</span></span>

<span data-ttu-id="1f0e8-105">Program som har utformats för att använda Windows Installer kan nås via WMI: s **Win32_Product** -klass, men inte alla program som används idag använder Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-105">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="1f0e8-106">Program som använder alternativa installations rutiner hanteras vanligt vis inte av Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-106">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="1f0e8-107">Specifika metoder för att arbeta med dessa program beror på installations programmet och de beslut som fattas av programutvecklaren.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-107">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="1f0e8-108">Exempel: program som installeras genom att kopiera filerna till en mapp på datorn kan vanligt vis inte hanteras med hjälp av tekniker som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-108">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="1f0e8-109">Du kan hantera dessa program som filer och mappar med hjälp av de metoder som beskrivs i [arbeta med filer och mappar](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="1f0e8-109">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="1f0e8-110">Den **Win32_Product** klassen är inte fråga optimerad.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-110">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="1f0e8-111">Frågor som använder filter för jokertecken gör att WMI kan använda MSI-providern för att räkna upp alla installerade produkter och sedan tolka den fullständiga listan i turordning för att hantera filtret.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-111">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="1f0e8-112">Detta initierar också en konsekvens kontroll av installerade paket, verifierar och reparerar installationen.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-112">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="1f0e8-113">Verifieringen är en långsam process och kan resultera i fel i händelse loggarna.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-113">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="1f0e8-114">Mer information om att söka [KB-artikel 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="1f0e8-114">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="1f0e8-115">Visa Windows Installer program</span><span class="sxs-lookup"><span data-stu-id="1f0e8-115">Listing Windows Installer Applications</span></span>

<span data-ttu-id="1f0e8-116">Om du vill visa en lista över de program som har installerats med Windows Installer på ett lokalt system eller fjärrsystem använder du följande enkla WMI-fråga:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-116">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="1f0e8-117">Om du vill visa alla egenskaper för **Win32_Product** -objektet som ska visas använder du **egenskaps** parametern för cmdletarna för formatering, till exempel `Format-List` cmdleten, med värdet `*` (all).</span><span class="sxs-lookup"><span data-stu-id="1f0e8-117">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="1f0e8-118">Du kan också använda `Get-CimInstance` **filter** parametern för att välja endast Microsoft .NET 2,0-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-118">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="1f0e8-119">Värdet för **filter** parametern använder WMI Query Language (WQL) syntax, inte Windows PowerShell-syntax.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-119">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="1f0e8-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-120">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="1f0e8-121">Om du vill visa en lista över de egenskaper som intresserar dig använder du **egenskaps** parametern för cmdletarna för att Visa önskade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-121">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="1f0e8-122">Visa alla program som inte går att installera</span><span class="sxs-lookup"><span data-stu-id="1f0e8-122">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="1f0e8-123">Eftersom de flesta standard program registrerar en avinstallation med Windows kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-123">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="1f0e8-124">Det finns inget garanterat sätt att hitta alla program på ett system.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-124">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="1f0e8-125">Det är dock möjligt att hitta alla program med listor som visas i **Lägg till eller ta bort program** i följande register nyckel:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-125">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="1f0e8-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="1f0e8-127">Vi kan granska den här nyckeln för att hitta program.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-127">We can examine this key to find applications.</span></span> <span data-ttu-id="1f0e8-128">Vi kan göra det enklare att Visa avinstallations nyckeln genom att mappa en PowerShell-enhet till den här register platsen:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="1f0e8-129">Nu har vi en enhet med namnet "Uninstall:" som kan användas för att snabbt och bekvämt söka efter programinstallationer.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="1f0e8-130">Vi kan hitta antalet installerade program genom att räkna antalet register nycklar i Uninstall: PowerShell-enheten:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="1f0e8-131">Vi kan söka i den här listan över program ytterligare med hjälp av en mängd olika tekniker, från och med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="1f0e8-131">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="1f0e8-132">Använd följande kommando för att hämta en lista över program och spara dem i `$UninstallableApplications` variabeln:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-132">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="1f0e8-133">Om du vill visa värdena för register posterna i register nycklarna under Uninstall använder du metoden GetValue i register nycklarna.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="1f0e8-134">Metodens värde är namnet på register posten.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="1f0e8-135">Om du till exempel vill hitta visnings namnen för program i avinstallations nyckeln använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="1f0e8-136">Det finns ingen garanti för att dessa värden är unika.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="1f0e8-137">I följande exempel visas två installerade objekt som "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="1f0e8-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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

## <a name="installing-applications"></a><span data-ttu-id="1f0e8-138">Installera program</span><span class="sxs-lookup"><span data-stu-id="1f0e8-138">Installing Applications</span></span>

<span data-ttu-id="1f0e8-139">Du kan använda **Win32_Product** -klassen för att installera Windows Installer-paket, via fjärr anslutning eller lokalt.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="1f0e8-140">För att installera ett program måste du starta PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="1f0e8-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="1f0e8-141">När du installerar via fjärr anslutning använder du en nätverks Sök väg för Universal Naming Convention (UNC) för att ange sökvägen till. MSI-paketet, eftersom WMI-undersystemet inte förstår PowerShell-sökvägar.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="1f0e8-142">Om du till exempel vill installera NewPackage.msi paketet som finns på nätverks resursen `\\AppServ\dsp` på fjärrdatorn PC01, skriver du följande kommando i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="1f0e8-143">Program som inte använder Windows Installer teknik kan ha programspecifika metoder för automatisk distribution.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="1f0e8-144">Kontrol lera programmets dokumentation eller kontakta program leverantörens support system.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="1f0e8-145">Ta bort program</span><span class="sxs-lookup"><span data-stu-id="1f0e8-145">Removing Applications</span></span>

<span data-ttu-id="1f0e8-146">Att ta bort ett Windows Installer-paket med PowerShell fungerar på ungefär samma sätt som när du installerar ett paket.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="1f0e8-147">Här är ett exempel som väljer vilket paket som ska avinstalleras baserat på dess namn. i vissa fall kan det vara lättare att filtrera med **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="1f0e8-148">Det är inte riktigt enkelt att ta bort andra program, även när du har gjort det lokalt.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="1f0e8-149">Vi kan hitta kommando rads avinstallations strängar för dessa program genom att extrahera egenskapen **UninstallString** .</span><span class="sxs-lookup"><span data-stu-id="1f0e8-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="1f0e8-150">Den här metoden fungerar för Windows Installer program och för äldre program som visas under avinstallations nyckeln:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="1f0e8-151">Du kan filtrera utdata efter visnings namnet om du vill:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="1f0e8-152">Dessa strängar är dock inte direkt användbara från PowerShell-prompten utan någon ändring.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="1f0e8-153">Uppgradera Windows Installer program</span><span class="sxs-lookup"><span data-stu-id="1f0e8-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="1f0e8-154">Om du vill uppgradera ett program måste du känna till namnet på programmet och sökvägen till program uppgraderings paketet.</span><span class="sxs-lookup"><span data-stu-id="1f0e8-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="1f0e8-155">Med den informationen kan du uppgradera ett program med ett enda PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="1f0e8-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
