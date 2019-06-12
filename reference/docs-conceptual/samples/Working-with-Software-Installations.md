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
# <a name="working-with-software-installations"></a><span data-ttu-id="ab454-103">Arbeta med programinstallationer</span><span class="sxs-lookup"><span data-stu-id="ab454-103">Working with Software Installations</span></span>

<span data-ttu-id="ab454-104">Program som är utformade för att använda Windows Installer kan nås via WMI **Win32_Product** klass, men inte alla program som används idag använder installationsprogrammet för Windows.</span><span class="sxs-lookup"><span data-stu-id="ab454-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="ab454-105">Program som använder alternativa installationsprogrammet rutiner hanteras vanligtvis inte av Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="ab454-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="ab454-106">Specifika tekniker för att arbeta med dessa program är beroende av den installationsprogram för programvara och de beslut som görs av programutvecklaren.</span><span class="sxs-lookup"><span data-stu-id="ab454-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="ab454-107">Program som har installerats genom att kopiera filerna till en mapp på datorn vanligtvis kan exempelvis inte hanteras med hjälp av tekniker som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="ab454-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="ab454-108">Du kan hantera de här programmen filer och mappar med hjälp av metoder som beskrivs i [arbeta med filer och mappar](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="ab454-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="ab454-109">Den **Win32_Product** klass är inte optimerad-fråga.</span><span class="sxs-lookup"><span data-stu-id="ab454-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="ab454-110">Frågor som använder jokertecken filter orsaka WMI för att räkna upp alla installerade produkter och parsa en fullständig lista i tur och ordning för att hantera filtret med MSI-providern.</span><span class="sxs-lookup"><span data-stu-id="ab454-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="ab454-111">Detta initierar också en konsekvenskontroll av paket installeras, verifiera och reparera installationen.</span><span class="sxs-lookup"><span data-stu-id="ab454-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="ab454-112">Verifieringen är lång tid och kan resultera i fel i händelseloggarna.</span><span class="sxs-lookup"><span data-stu-id="ab454-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="ab454-113">Mer information om du söker efter [KB-artikel 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="ab454-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="ab454-114">Visa en lista över Windows Installer-program</span><span class="sxs-lookup"><span data-stu-id="ab454-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="ab454-115">Om du vill visa de program som installeras med Windows Installer på en lokal eller fjärransluten dator, använder du följande enkla WMI-fråga:</span><span class="sxs-lookup"><span data-stu-id="ab454-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

<span data-ttu-id="ab454-116">Att visa alla egenskaper för den **Win32_Product** objekt ska visas, Använd den **egenskaper** parametern formatering cmdlets som de `Format-List` cmdlet med ett värde på `*` (alla).</span><span class="sxs-lookup"><span data-stu-id="ab454-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

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

<span data-ttu-id="ab454-117">Du kan använda den `Get-CimInstance` **Filter** parametern att välja endast Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ab454-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="ab454-118">Värdet för den **Filter** parametern använder WMI-frågespråket (WQL) syntax, inte Windows PowerShell-syntax.</span><span class="sxs-lookup"><span data-stu-id="ab454-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="ab454-119">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="ab454-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="ab454-120">Om du vill visa egenskaperna som intresserar dig, använder den **egenskapen** parametern formatering cmdletar att lista de önskade egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="ab454-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

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

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="ab454-121">Visa en lista över alla Uninstallable program</span><span class="sxs-lookup"><span data-stu-id="ab454-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="ab454-122">Eftersom de flesta program registrera en avinstallation med Windows, kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret.</span><span class="sxs-lookup"><span data-stu-id="ab454-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="ab454-123">Det finns ingen garanterad sättet att hitta alla program på ett system.</span><span class="sxs-lookup"><span data-stu-id="ab454-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="ab454-124">Det är dock möjligt att hitta alla program med listor som visas i **Lägg till eller ta bort program**.</span><span class="sxs-lookup"><span data-stu-id="ab454-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs**.</span></span> <span data-ttu-id="ab454-125">**Lägg till eller ta bort program** söker efter de här programmen i följande registernyckel:</span><span class="sxs-lookup"><span data-stu-id="ab454-125">**Add or Remove Programs** finds these applications in the following registry key:</span></span>

<span data-ttu-id="ab454-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="ab454-126">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="ab454-127">Vi kan granska den här nyckeln för att hitta program.</span><span class="sxs-lookup"><span data-stu-id="ab454-127">We can examine this key to find applications.</span></span> <span data-ttu-id="ab454-128">Om du vill göra det enklare att visa nyckeln Uninstall, kan vi ansluta en PowerShell-enhet till den platsen som:</span><span class="sxs-lookup"><span data-stu-id="ab454-128">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
<span data-ttu-id="ab454-129">Nu har vi en enhet med namnet ”avinstallera”: som kan användas för att snabbt och enkelt leta efter programinstallationer.</span><span class="sxs-lookup"><span data-stu-id="ab454-129">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="ab454-130">Vi kan hitta antalet installerade program genom att räkna antalet registernycklar i avinstallationen: PowerShell-enhet:</span><span class="sxs-lookup"><span data-stu-id="ab454-130">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```
(Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="ab454-131">Vi kan söka denna lista över ytterligare program med hjälp av en mängd olika tekniker, från och med **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="ab454-131">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="ab454-132">Hämta en lista över program och spara dem i den **$UninstallableApplications** variabel, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ab454-132">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="ab454-133">För att visa värdena för registerposterna i registernycklarna under avinstallationen, använder du metoden GetValue i registernycklarna.</span><span class="sxs-lookup"><span data-stu-id="ab454-133">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="ab454-134">Värdet för metoden är namnet på registerposten.</span><span class="sxs-lookup"><span data-stu-id="ab454-134">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="ab454-135">Till exempel för att hitta visningsnamnen för program i nyckeln Uninstall, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ab454-135">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="ab454-136">Det är inte säkert att dessa värden är unika.</span><span class="sxs-lookup"><span data-stu-id="ab454-136">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="ab454-137">I följande exempel visas två installerade objekt som ”Windows Media Encoder 9 Series”:</span><span class="sxs-lookup"><span data-stu-id="ab454-137">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

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

## <a name="installing-applications"></a><span data-ttu-id="ab454-138">Installera program</span><span class="sxs-lookup"><span data-stu-id="ab454-138">Installing Applications</span></span>

<span data-ttu-id="ab454-139">Du kan använda den **Win32_Product** klassen för att installera Windows Installer-paket via fjärranslutning eller lokalt.</span><span class="sxs-lookup"><span data-stu-id="ab454-139">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="ab454-140">Om du vill installera ett program måste du starta PowerShell med alternativet ”Kör som administratör”.</span><span class="sxs-lookup"><span data-stu-id="ab454-140">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="ab454-141">När du installerar via fjärranslutning, måste du använda en nätverkssökväg för Universal Naming Convention (UNC) för att ange sökvägen till MSI-paketet, eftersom undersystemet WMI inte förstår PowerShell-sökvägar.</span><span class="sxs-lookup"><span data-stu-id="ab454-141">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="ab454-142">Till exempel att installera paketet NewPackage.msi finns i nätverksresursen `\\AppServ\dsp` på fjärrdatorn PC01, skriver du följande kommando i PowerShell-Kommandotolken:</span><span class="sxs-lookup"><span data-stu-id="ab454-142">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="ab454-143">Program som inte använder Windows Installer-tekniken kan ha programspecifika metoder för automatisk distribution.</span><span class="sxs-lookup"><span data-stu-id="ab454-143">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="ab454-144">Läs i dokumentationen till programmet eller kontakta tillverkaren av programmet supportsystem.</span><span class="sxs-lookup"><span data-stu-id="ab454-144">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="ab454-145">Ta bort program</span><span class="sxs-lookup"><span data-stu-id="ab454-145">Removing Applications</span></span>

<span data-ttu-id="ab454-146">Ta bort en Windows Installer-paketet med hjälp av PowerShell fungerar på ungefär samma sätt som installerar ett paket.</span><span class="sxs-lookup"><span data-stu-id="ab454-146">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="ab454-147">Här är ett exempel som väljer att avinstallera paketet baserat på dess namn. i vissa fall kan det vara enklare att filtrera med den **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="ab454-147">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="ab454-148">Ta bort andra program är inte var så enkel, även när du är klar lokalt.</span><span class="sxs-lookup"><span data-stu-id="ab454-148">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="ab454-149">Vi kan hitta kommandoraden avinstallera strängar för dessa program genom att extrahera den **UninstallString** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="ab454-149">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="ab454-150">Den här metoden fungerar för Windows Installer-program och för äldre program som visas under nyckeln Uninstall:</span><span class="sxs-lookup"><span data-stu-id="ab454-150">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="ab454-151">Du kan filtrera resultatet efter visningsnamn, om du vill:</span><span class="sxs-lookup"><span data-stu-id="ab454-151">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="ab454-152">Men kan dessa strängar inte användas direkt från PowerShell-prompten utan några ändringar.</span><span class="sxs-lookup"><span data-stu-id="ab454-152">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="ab454-153">Uppgradera Windows Installer-program</span><span class="sxs-lookup"><span data-stu-id="ab454-153">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="ab454-154">Om du vill uppgradera ett program som du behöver veta namnet på programmet och sökvägen på uppgraderingspaketet för programmet.</span><span class="sxs-lookup"><span data-stu-id="ab454-154">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="ab454-155">Med denna information kan du uppgradera ett program med ett enda PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="ab454-155">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
