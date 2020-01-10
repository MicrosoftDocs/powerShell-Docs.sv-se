---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Arbeta med programinstallationer
ms.openlocfilehash: d164064418ad7a0209166c81a7c3cc32a9db300a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737159"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="9b778-103">Arbeta med programinstallationer</span><span class="sxs-lookup"><span data-stu-id="9b778-103">Working with Software Installations</span></span>

<span data-ttu-id="9b778-104">Program som har utformats för att använda Windows Installer kan nås via WMI: s **Win32_Product** -klass, men inte alla program som används idag använder Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9b778-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="9b778-105">Program som använder alternativa installations rutiner hanteras vanligt vis inte av Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9b778-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="9b778-106">Specifika metoder för att arbeta med dessa program beror på installations programmet och de beslut som fattas av programutvecklaren.</span><span class="sxs-lookup"><span data-stu-id="9b778-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="9b778-107">Exempel: program som installeras genom att kopiera filerna till en mapp på datorn kan vanligt vis inte hanteras med hjälp av tekniker som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="9b778-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="9b778-108">Du kan hantera dessa program som filer och mappar med hjälp av de metoder som beskrivs i [arbeta med filer och mappar](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="9b778-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="9b778-109">Den **Win32_Product** klassen är inte fråga optimerad.</span><span class="sxs-lookup"><span data-stu-id="9b778-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="9b778-110">Frågor som använder filter för jokertecken gör att WMI kan använda MSI-providern för att räkna upp alla installerade produkter och sedan tolka den fullständiga listan i turordning för att hantera filtret.</span><span class="sxs-lookup"><span data-stu-id="9b778-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="9b778-111">Detta initierar också en konsekvens kontroll av installerade paket, verifierar och reparerar installationen.</span><span class="sxs-lookup"><span data-stu-id="9b778-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="9b778-112">Verifieringen är en långsam process och kan resultera i fel i händelse loggarna.</span><span class="sxs-lookup"><span data-stu-id="9b778-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="9b778-113">Mer information om att söka [KB-artikel 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="9b778-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="9b778-114">Visa Windows Installer program</span><span class="sxs-lookup"><span data-stu-id="9b778-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="9b778-115">Om du vill visa en lista över de program som har installerats med Windows Installer på ett lokalt system eller fjärrsystem använder du följande enkla WMI-fråga:</span><span class="sxs-lookup"><span data-stu-id="9b778-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="9b778-116">Om du vill visa alla egenskaper för **Win32_Product** -objektet som ska visas använder du **egenskaps** parametern för cmdletarna för formatering, till exempel `Format-List`-cmdlet, med värdet `*` (alla).</span><span class="sxs-lookup"><span data-stu-id="9b778-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="9b778-117">Du kan också använda `Get-CimInstance` **filter** parameter för att välja endast Microsoft .NET 2,0-körning.</span><span class="sxs-lookup"><span data-stu-id="9b778-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="9b778-118">Värdet för **filter** parametern använder WMI Query Language (WQL) syntax, inte Windows PowerShell-syntax.</span><span class="sxs-lookup"><span data-stu-id="9b778-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="9b778-119">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="9b778-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="9b778-120">Om du vill visa en lista över de egenskaper som intresserar dig använder du **egenskaps** parametern för cmdletarna för att Visa önskade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9b778-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="9b778-121">Visa alla program som inte går att installera</span><span class="sxs-lookup"><span data-stu-id="9b778-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="9b778-122">Eftersom de flesta standard program registrerar en avinstallation med Windows kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret.</span><span class="sxs-lookup"><span data-stu-id="9b778-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="9b778-123">Det finns inget garanterat sätt att hitta alla program på ett system.</span><span class="sxs-lookup"><span data-stu-id="9b778-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="9b778-124">Det är dock möjligt att hitta alla program med listor som visas i **Lägg till eller ta bort program** i följande register nyckel:</span><span class="sxs-lookup"><span data-stu-id="9b778-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="9b778-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="9b778-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="9b778-126">Vi kan granska den här nyckeln för att hitta program.</span><span class="sxs-lookup"><span data-stu-id="9b778-126">We can examine this key to find applications.</span></span> <span data-ttu-id="9b778-127">Vi kan göra det enklare att Visa avinstallations nyckeln genom att mappa en PowerShell-enhet till den här register platsen:</span><span class="sxs-lookup"><span data-stu-id="9b778-127">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="9b778-128">Nu har vi en enhet med namnet "Uninstall:" som kan användas för att snabbt och bekvämt söka efter programinstallationer.</span><span class="sxs-lookup"><span data-stu-id="9b778-128">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="9b778-129">Vi kan hitta antalet installerade program genom att räkna antalet register nycklar i Uninstall: PowerShell-enheten:</span><span class="sxs-lookup"><span data-stu-id="9b778-129">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="9b778-130">Vi kan söka i den här listan med program ytterligare genom att använda en mängd olika tekniker, från och med `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="9b778-130">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="9b778-131">Om du vill hämta en lista över program och spara dem i variabeln `$UninstallableApplications` använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="9b778-131">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="9b778-132">Om du vill visa värdena för register posterna i register nycklarna under Uninstall använder du metoden GetValue i register nycklarna.</span><span class="sxs-lookup"><span data-stu-id="9b778-132">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="9b778-133">Metodens värde är namnet på register posten.</span><span class="sxs-lookup"><span data-stu-id="9b778-133">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="9b778-134">Om du till exempel vill hitta visnings namnen för program i avinstallations nyckeln använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="9b778-134">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="9b778-135">Det finns ingen garanti för att dessa värden är unika.</span><span class="sxs-lookup"><span data-stu-id="9b778-135">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="9b778-136">I följande exempel visas två installerade objekt som "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="9b778-136">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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
                               HelpLink            : http://go.microsoft.com/fwlink/?LinkID=91955
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

## <a name="installing-applications"></a><span data-ttu-id="9b778-137">Installera program</span><span class="sxs-lookup"><span data-stu-id="9b778-137">Installing Applications</span></span>

<span data-ttu-id="9b778-138">Du kan använda **Win32_Product** -klassen för att installera Windows Installer-paket, via fjärr anslutning eller lokalt.</span><span class="sxs-lookup"><span data-stu-id="9b778-138">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="9b778-139">För att installera ett program måste du starta PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="9b778-139">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="9b778-140">När du installerar via fjärr anslutning använder du en nätverks Sök väg för Universal Naming Convention (UNC) för att ange sökvägen till. MSI-paketet, eftersom WMI-undersystemet inte förstår PowerShell-sökvägar.</span><span class="sxs-lookup"><span data-stu-id="9b778-140">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="9b778-141">Om du till exempel vill installera NewPackage. MSI-paketet som finns på nätverks resursen `\\AppServ\dsp` på fjärrdatorn PC01 skriver du följande kommando i PowerShell-prompten:</span><span class="sxs-lookup"><span data-stu-id="9b778-141">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="9b778-142">Program som inte använder Windows Installer teknik kan ha programspecifika metoder för automatisk distribution.</span><span class="sxs-lookup"><span data-stu-id="9b778-142">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="9b778-143">Kontrol lera programmets dokumentation eller kontakta program leverantörens support system.</span><span class="sxs-lookup"><span data-stu-id="9b778-143">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="9b778-144">Ta bort program</span><span class="sxs-lookup"><span data-stu-id="9b778-144">Removing Applications</span></span>

<span data-ttu-id="9b778-145">Att ta bort ett Windows Installer-paket med PowerShell fungerar på ungefär samma sätt som när du installerar ett paket.</span><span class="sxs-lookup"><span data-stu-id="9b778-145">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="9b778-146">Här är ett exempel som väljer vilket paket som ska avinstalleras baserat på dess namn. i vissa fall kan det vara lättare att filtrera med **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="9b778-146">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="9b778-147">Det är inte riktigt enkelt att ta bort andra program, även när du har gjort det lokalt.</span><span class="sxs-lookup"><span data-stu-id="9b778-147">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="9b778-148">Vi kan hitta kommando rads avinstallations strängar för dessa program genom att extrahera egenskapen **UninstallString** .</span><span class="sxs-lookup"><span data-stu-id="9b778-148">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="9b778-149">Den här metoden fungerar för Windows Installer program och för äldre program som visas under avinstallations nyckeln:</span><span class="sxs-lookup"><span data-stu-id="9b778-149">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9b778-150">Du kan filtrera utdata efter visnings namnet om du vill:</span><span class="sxs-lookup"><span data-stu-id="9b778-150">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9b778-151">Dessa strängar är dock inte direkt användbara från PowerShell-prompten utan någon ändring.</span><span class="sxs-lookup"><span data-stu-id="9b778-151">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="9b778-152">Uppgradera Windows Installer program</span><span class="sxs-lookup"><span data-stu-id="9b778-152">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="9b778-153">Om du vill uppgradera ett program måste du känna till namnet på programmet och sökvägen till program uppgraderings paketet.</span><span class="sxs-lookup"><span data-stu-id="9b778-153">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="9b778-154">Med den informationen kan du uppgradera ett program med ett enda PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="9b778-154">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
