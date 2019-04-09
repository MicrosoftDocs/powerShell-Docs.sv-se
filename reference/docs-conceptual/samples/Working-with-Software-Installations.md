---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med programinstallationer
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293239"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="caa4c-103">Arbeta med programinstallationer</span><span class="sxs-lookup"><span data-stu-id="caa4c-103">Working with Software Installations</span></span>

<span data-ttu-id="caa4c-104">Program som är utformade för att använda Windows Installer kan nås via WMI **Win32_Product** klass, men inte alla program som används idag använder installationsprogrammet för Windows.</span><span class="sxs-lookup"><span data-stu-id="caa4c-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="caa4c-105">Eftersom Windows Installer innehåller lugnet standard tekniker för att arbeta med program som kan installeras, fokuserar vi främst på dessa program.</span><span class="sxs-lookup"><span data-stu-id="caa4c-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="caa4c-106">Program som använder alternativa installationsprogrammet rutiner Allmänt hanteras inte av Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="caa4c-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="caa4c-107">Specifika tekniker för att arbeta med dessa program beror på den installationsprogram för programvara och de beslut som görs av programutvecklaren.</span><span class="sxs-lookup"><span data-stu-id="caa4c-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="caa4c-108">Program som är installerade genom att kopiera vanligtvis programfilerna på datorn kan inte hanteras med hjälp av tekniker som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="caa4c-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="caa4c-109">Du kan hantera de här programmen filer och mappar med hjälp av de metoder som beskrivs i avsnittet ”Arbeta med filer och mappar”.</span><span class="sxs-lookup"><span data-stu-id="caa4c-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="caa4c-110">Visa en lista över Windows Installer-program</span><span class="sxs-lookup"><span data-stu-id="caa4c-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="caa4c-111">Om du vill visa de program som installeras med Windows Installer på en lokal eller fjärransluten dator, använder du följande enkla WMI-fråga:</span><span class="sxs-lookup"><span data-stu-id="caa4c-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="caa4c-112">Använd parametern egenskaper för cmdletarna formatering som Format-List-cmdlet för att visa alla egenskaper för objektet Win32_Product det som visningen på, med värdet \* (alla).</span><span class="sxs-lookup"><span data-stu-id="caa4c-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

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

<span data-ttu-id="caa4c-113">Du kan använda den **Get-WmiObject Filter** parametern att välja endast Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="caa4c-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="caa4c-114">Eftersom det filter som används i det här kommandot är ett WMI-filter, använder WMI-frågespråket (WQL) syntax, inte Windows PowerShell-syntax.</span><span class="sxs-lookup"><span data-stu-id="caa4c-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="caa4c-115">Instead,:</span><span class="sxs-lookup"><span data-stu-id="caa4c-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="caa4c-116">Observera att WQL-frågor ofta använda tecken som blanksteg eller likhetstecknen som har en särskild betydelse i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="caa4c-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="caa4c-117">Därför är det klokt att alltid ange värdet för Filterparametern inom citattecken.</span><span class="sxs-lookup"><span data-stu-id="caa4c-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="caa4c-118">Du kan också använda Windows PowerShell escape-tecknet, en backtick (\`), men det inte kan förbättra läsbarheten.</span><span class="sxs-lookup"><span data-stu-id="caa4c-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="caa4c-119">Följande kommando motsvarar det föregående kommandot och returnerar samma resultat, men använder backtick för att undvika specialtecken, i stället för att citera hela Filtersträngen.</span><span class="sxs-lookup"><span data-stu-id="caa4c-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="caa4c-120">Visa endast de egenskaper som intresserar dig genom att använda parametern egenskapen formatering cmdletar för att lista de önskade egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="caa4c-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

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

<span data-ttu-id="caa4c-121">Slutligen installerade program, en enkel att hitta bara namnen på **Format hela** instruktionen förenklar utdata:</span><span class="sxs-lookup"><span data-stu-id="caa4c-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="caa4c-122">Nu har vi flera olika sätt att titta på program som använde Windows Installer för installationen, men vi har inte vara andra program.</span><span class="sxs-lookup"><span data-stu-id="caa4c-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="caa4c-123">Eftersom de flesta program registrera sina avinstallationsprogrammet med Windows, kan vi arbeta med dem lokalt genom att söka efter dem i Windows-registret.</span><span class="sxs-lookup"><span data-stu-id="caa4c-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="caa4c-124">Visa en lista över alla Uninstallable program</span><span class="sxs-lookup"><span data-stu-id="caa4c-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="caa4c-125">Även om det finns inget garanterad sätt att hitta alla program på ett system, går det att hitta alla program med listor som visas i dialogrutan Lägg till eller ta bort program.</span><span class="sxs-lookup"><span data-stu-id="caa4c-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="caa4c-126">Lägg till eller ta bort program söker efter de här programmen i följande registernyckel:</span><span class="sxs-lookup"><span data-stu-id="caa4c-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="caa4c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span><span class="sxs-lookup"><span data-stu-id="caa4c-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="caa4c-128">Vi kan också granska den här nyckeln för att hitta program.</span><span class="sxs-lookup"><span data-stu-id="caa4c-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="caa4c-129">Om du vill göra det enklare att visa nyckeln Uninstall, kan vi ansluta en Windows PowerShell-enhet till den platsen som:</span><span class="sxs-lookup"><span data-stu-id="caa4c-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="caa4c-130">Den **HKLM:** enhet har mappats till roten **HKEY_LOCAL_MACHINE**, så vi använde den här enheten i sökvägen till nyckeln Uninstall.</span><span class="sxs-lookup"><span data-stu-id="caa4c-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="caa4c-131">I stället för **HKLM:** kunde vi angett registersökvägen genom att använda antingen **HKLM** eller **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="caa4c-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="caa4c-132">Fördelen med att använda en befintlig register-enhet är att vi kan använda tabbifyllning för att fylla i nycklar-namn, så vi inte behöver ange dem.</span><span class="sxs-lookup"><span data-stu-id="caa4c-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="caa4c-133">Nu har vi en enhet med namnet ”avinstallera” som kan användas för att snabbt och enkelt söka efter programinstallationer.</span><span class="sxs-lookup"><span data-stu-id="caa4c-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="caa4c-134">Vi kan hitta antalet installerade program genom att räkna antalet registernycklar i avinstallationen: Windows PowerShell-enhet:</span><span class="sxs-lookup"><span data-stu-id="caa4c-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="caa4c-135">Vi kan söka denna lista över ytterligare program med hjälp av en mängd olika tekniker, från och med **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="caa4c-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="caa4c-136">Hämta en lista över program och spara dem i den **$UninstallableApplications** variabel, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="caa4c-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="caa4c-137">Vi använder långa namn på variabler för tydlighetens skull.</span><span class="sxs-lookup"><span data-stu-id="caa4c-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="caa4c-138">I själva verket får finns det ingen anledning att använda långa namn.</span><span class="sxs-lookup"><span data-stu-id="caa4c-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="caa4c-139">Du kan använda tabbifyllning för variabelnamn, men du kan också använda 1 – 2 tecken namn för hastighet.</span><span class="sxs-lookup"><span data-stu-id="caa4c-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="caa4c-140">Längre, beskrivande namn är mest användbara när du utvecklar kod för återanvändning.</span><span class="sxs-lookup"><span data-stu-id="caa4c-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="caa4c-141">För att visa värdena för registerposterna i registernycklarna under avinstallationen, använder du metoden GetValue i registernycklarna.</span><span class="sxs-lookup"><span data-stu-id="caa4c-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="caa4c-142">Värdet för metoden är namnet på registerposten.</span><span class="sxs-lookup"><span data-stu-id="caa4c-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="caa4c-143">Till exempel för att hitta visningsnamnen för program i nyckeln Uninstall, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="caa4c-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="caa4c-144">Det är inte säkert att dessa värden är unika.</span><span class="sxs-lookup"><span data-stu-id="caa4c-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="caa4c-145">I följande exempel visas två installerade objekt som ”Windows Media Encoder 9 Series”:</span><span class="sxs-lookup"><span data-stu-id="caa4c-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="caa4c-146">Installera program</span><span class="sxs-lookup"><span data-stu-id="caa4c-146">Installing Applications</span></span>

<span data-ttu-id="caa4c-147">Du kan använda den **Win32_Product** klassen för att installera Windows Installer-paket via fjärranslutning eller lokalt.</span><span class="sxs-lookup"><span data-stu-id="caa4c-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="caa4c-148">På Windows Vista, Windows Server 2008 och senare versioner av Windows, om du vill installera ett program, måste du starta Windows PowerShell med alternativet ”Kör som administratör”.</span><span class="sxs-lookup"><span data-stu-id="caa4c-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="caa4c-149">När du installerar via fjärranslutning, måste du använda en nätverkssökväg för Universal Naming Convention (UNC) för att ange sökvägen till MSI-paketet, eftersom undersystemet WMI inte förstår Windows PowerShell-sökvägar.</span><span class="sxs-lookup"><span data-stu-id="caa4c-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="caa4c-150">Till exempel att installera paketet NewPackage.msi finns i nätverksresursen \\ \\AppServ\\dsp på fjärrdatorn PC01, Skriv följande kommando i Windows PowerShell-Kommandotolken:</span><span class="sxs-lookup"><span data-stu-id="caa4c-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="caa4c-151">Program som inte använder Windows Installer-tekniken kan ha programspecifika metoder för automatisk distribution.</span><span class="sxs-lookup"><span data-stu-id="caa4c-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="caa4c-152">För att avgöra om det finns en metod för distribution, i dokumentationen till programmet eller kontakta tillverkaren av programmet supportsystem.</span><span class="sxs-lookup"><span data-stu-id="caa4c-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="caa4c-153">I vissa fall kan även om programleverantören inte specifikt utforma programmet för installationen automation kanske installationsprogram för programvara tillverkare vissa tekniker för automatisering.</span><span class="sxs-lookup"><span data-stu-id="caa4c-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="caa4c-154">Ta bort program</span><span class="sxs-lookup"><span data-stu-id="caa4c-154">Removing Applications</span></span>

<span data-ttu-id="caa4c-155">Ta bort en Windows Installer-paketet med hjälp av Windows PowerShell fungerar på ungefär samma sätt som installerar ett paket.</span><span class="sxs-lookup"><span data-stu-id="caa4c-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="caa4c-156">Här är ett exempel som väljer att avinstallera paketet baserat på dess namn. i vissa fall kan det vara enklare att filtrera med den **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="caa4c-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="caa4c-157">Ta bort andra program är inte var så enkel, även när du är klar lokalt.</span><span class="sxs-lookup"><span data-stu-id="caa4c-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="caa4c-158">Vi kan hitta kommandoraden avinstallera strängar för dessa program genom att extrahera den **UninstallString** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="caa4c-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="caa4c-159">Den här metoden fungerar för Windows Installer-program och för äldre program som visas under nyckeln Uninstall:</span><span class="sxs-lookup"><span data-stu-id="caa4c-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="caa4c-160">Du kan filtrera resultatet efter visningsnamn, om du vill:</span><span class="sxs-lookup"><span data-stu-id="caa4c-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="caa4c-161">Men kan dessa strängar inte användas direkt från Windows PowerShell-prompten utan några ändringar.</span><span class="sxs-lookup"><span data-stu-id="caa4c-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="caa4c-162">Uppgradera Windows Installer-program</span><span class="sxs-lookup"><span data-stu-id="caa4c-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="caa4c-163">Om du vill uppgradera ett program som du behöver veta namnet på programmet och sökvägen på uppgraderingspaketet för programmet.</span><span class="sxs-lookup"><span data-stu-id="caa4c-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="caa4c-164">Med denna information kan du uppgradera ett program med ett enda Windows PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="caa4c-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```