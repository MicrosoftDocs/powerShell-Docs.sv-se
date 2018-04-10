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
---
# <a name="working-with-software-installations"></a><span data-ttu-id="1220a-103">Arbeta med programinstallationer</span><span class="sxs-lookup"><span data-stu-id="1220a-103">Working with Software Installations</span></span>

<span data-ttu-id="1220a-104">Program som är utformade för att använda Windows Installer kan nås via WMI **Win32_Product** klass, men inte alla program som används idag med hjälp av Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="1220a-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="1220a-105">Eftersom Windows Installer innehåller bredast utbud av vanliga tekniker för att arbeta med program kan installeras, fokuserar vi främst på programmen.</span><span class="sxs-lookup"><span data-stu-id="1220a-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="1220a-106">Program som använder alternativa installationsprogrammet rutiner vanligtvis hanteras inte av Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="1220a-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="1220a-107">Specifika tekniker för att arbeta med dessa program beror på installationsprogrammet och programutvecklaren beslut.</span><span class="sxs-lookup"><span data-stu-id="1220a-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="1220a-108">Program som har installerats genom att kopiera vanligtvis programfilerna på datorn kan inte hanteras av med metoder som beskrivs här.</span><span class="sxs-lookup"><span data-stu-id="1220a-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="1220a-109">Du kan hantera de här programmen filer och mappar med hjälp av de metoder som beskrivs i avsnittet ”Arbeta med filer och mappar”.</span><span class="sxs-lookup"><span data-stu-id="1220a-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="1220a-110">Visar en lista över Windows Installer-program</span><span class="sxs-lookup"><span data-stu-id="1220a-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="1220a-111">Använd följande enkla WMI-fråga om du vill visa de program som installerats med Windows Installer på en lokal eller fjärransluten dator:</span><span class="sxs-lookup"><span data-stu-id="1220a-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="1220a-112">Om du vill visa alla egenskaper i objektet Win32_Product visas, använder du parametern egenskaper formatering cmdlets, till exempel Format-List-cmdlet med ett värde för \* (alla).</span><span class="sxs-lookup"><span data-stu-id="1220a-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

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

<span data-ttu-id="1220a-113">Du kan använda den **Get-WmiObject Filter** parametern att välja endast Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="1220a-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="1220a-114">Eftersom det filter som används i det här kommandot är en WMI-filter, använder WMI WQL (Query Language) syntax, inte Windows PowerShell-syntax.</span><span class="sxs-lookup"><span data-stu-id="1220a-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="1220a-115">I stället:</span><span class="sxs-lookup"><span data-stu-id="1220a-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="1220a-116">Observera att WQL-frågor ofta använda tecken som blanksteg eller likhetstecken som har en särskild innebörd i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1220a-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="1220a-117">Därför är det klokt att alltid ange värdet för parametern Filter inom citattecken.</span><span class="sxs-lookup"><span data-stu-id="1220a-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="1220a-118">Du kan också använda Windows PowerShell escape-tecken, ett backtick (\`), även om det inte kan förbättra läsbarhet.</span><span class="sxs-lookup"><span data-stu-id="1220a-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="1220a-119">Följande kommando motsvarar det föregående kommandot returnerar samma resultat och använder backtick för att undanta specialtecken i stället för hela Filtersträngen textkommando.</span><span class="sxs-lookup"><span data-stu-id="1220a-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="1220a-120">Använd parametern egenskapen formatering cmdlet för att lista egenskaperna om du vill visa endast de egenskaper som intresserar dig.</span><span class="sxs-lookup"><span data-stu-id="1220a-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

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

<span data-ttu-id="1220a-121">Slutligen installerade program, ett enkelt att hitta bara namnen på **Format hela** instruktionen förenklar utdata:</span><span class="sxs-lookup"><span data-stu-id="1220a-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="1220a-122">Nu har vi titta på program som används av Windows Installer för installation på flera olika sätt, men vi har inte upp andra program.</span><span class="sxs-lookup"><span data-stu-id="1220a-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="1220a-123">Eftersom de flesta program registrerar sina avinstallationsprogrammet med Windows, kan vi arbetar med dem lokalt genom att söka efter dem i Windows-registret.</span><span class="sxs-lookup"><span data-stu-id="1220a-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="1220a-124">Visar en lista över alla Uninstallable program</span><span class="sxs-lookup"><span data-stu-id="1220a-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="1220a-125">Även om det finns inget garanterad sätt att hitta alla program på ett system, är det möjligt att söka efter alla program med listor visas i dialogrutan Lägg till eller ta bort program.</span><span class="sxs-lookup"><span data-stu-id="1220a-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="1220a-126">Lägg till eller ta bort program hittar programmen i följande registernyckel:</span><span class="sxs-lookup"><span data-stu-id="1220a-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="1220a-127">**HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion\\avinstallera**.</span><span class="sxs-lookup"><span data-stu-id="1220a-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="1220a-128">Vi kan även undersöka den här nyckeln om du vill söka efter program.</span><span class="sxs-lookup"><span data-stu-id="1220a-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="1220a-129">Om du vill göra det enklare att visa nyckeln Uninstall, mappa vi en Windows PowerShell-enhet till denna plats i registret:</span><span class="sxs-lookup"><span data-stu-id="1220a-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="1220a-130">Den **HKLM:** enheten är mappad till roten i **HKEY_LOCAL_MACHINE**, så vi använde den här enheten i sökvägen till nyckeln Uninstall.</span><span class="sxs-lookup"><span data-stu-id="1220a-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="1220a-131">I stället för **HKLM:** kunde vi angett registersökvägen genom att använda antingen **HKLM** eller **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="1220a-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="1220a-132">Fördelen med att använda en befintlig enhet i registret är att du kan använda fliken slutförande för att fylla i namn nycklar, så vi inte behöver ange dem.</span><span class="sxs-lookup"><span data-stu-id="1220a-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="1220a-133">Nu har vi en enhet med namnet ”avinstallera” som kan användas för att snabbt och enkelt leta efter programinstallationer.</span><span class="sxs-lookup"><span data-stu-id="1220a-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="1220a-134">Vi kan ta reda på antalet installerade program genom att räkna antalet registernycklar i avinstallationen: Windows PowerShell-enhet:</span><span class="sxs-lookup"><span data-stu-id="1220a-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="1220a-135">Vi kan söka denna lista över ytterligare program med hjälp av en mängd olika tekniker, börjar med **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="1220a-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="1220a-136">Hämta en lista över program och spara dem i den **$UninstallableApplications** variabel, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="1220a-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="1220a-137">Vi använder långa namn på variabler för tydlighetens skull.</span><span class="sxs-lookup"><span data-stu-id="1220a-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="1220a-138">Det finns ingen anledning att använda långa namn för faktiska används.</span><span class="sxs-lookup"><span data-stu-id="1220a-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="1220a-139">Du kan använda fliken slutförande för variabelnamn, men du kan också använda 1 – 2 tecken namn för hastighet.</span><span class="sxs-lookup"><span data-stu-id="1220a-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="1220a-140">Längre, beskrivande namn är mest användbara när du utvecklar koden för återanvändning.</span><span class="sxs-lookup"><span data-stu-id="1220a-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="1220a-141">Använd metoden GetValue registernycklar för att visa värden registerposter i registernycklarna under avinstallationen.</span><span class="sxs-lookup"><span data-stu-id="1220a-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="1220a-142">Värdet för metoden är namnet på posten i registret.</span><span class="sxs-lookup"><span data-stu-id="1220a-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="1220a-143">Till exempel för att hitta visningsnamnen för program i nyckeln Uninstall, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="1220a-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="1220a-144">Det är inte säkert att dessa värden är unika.</span><span class="sxs-lookup"><span data-stu-id="1220a-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="1220a-145">I följande exempel visas två installerade objekt som ”Windows Media Encoder 9 Series”:</span><span class="sxs-lookup"><span data-stu-id="1220a-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="1220a-146">Installera program</span><span class="sxs-lookup"><span data-stu-id="1220a-146">Installing Applications</span></span>

<span data-ttu-id="1220a-147">Du kan använda den **Win32_Product** klassen för att installera Windows Installer-paket via fjärranslutning eller lokalt.</span><span class="sxs-lookup"><span data-stu-id="1220a-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="1220a-148">I Windows Vista, Windows Server 2008 och senare versioner av Windows för att installera ett program måste du starta Windows PowerShell med alternativet ”Kör som administratör”.</span><span class="sxs-lookup"><span data-stu-id="1220a-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="1220a-149">När du installerar via fjärranslutning, måste du använda en nätverkssökväg för Universal Naming Convention (UNC) för att ange sökvägen till MSI-paketet, eftersom undersystemet WMI inte förstår sökvägar för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1220a-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="1220a-150">Till exempel att installera paketet NewPackage.msi finns i nätverksresursen \\ \\AppServ\\dsp på fjärrdatorn PC01, Skriv följande kommando i Kommandotolken för Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1220a-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="1220a-151">Program som inte använder Windows Installer-tekniken kan ha programspecifika metoder tillgängliga för automatisk distribution.</span><span class="sxs-lookup"><span data-stu-id="1220a-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="1220a-152">För att fastställa om det finns en metod för automatisering av distribution finns i dokumentationen för programmet eller kontakta tillverkaren av programmet stöd för system.</span><span class="sxs-lookup"><span data-stu-id="1220a-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="1220a-153">I vissa fall, även om leverantören av tillämpningsprogrammet inte specifikt utforma program för installation av automation kanske installer tillverkaren vissa tekniker för automatisering.</span><span class="sxs-lookup"><span data-stu-id="1220a-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="1220a-154">Ta bort program</span><span class="sxs-lookup"><span data-stu-id="1220a-154">Removing Applications</span></span>

<span data-ttu-id="1220a-155">Tar bort en Windows Installer-paketet med hjälp av Windows PowerShell fungerar på ungefär samma sätt som installerar ett paket.</span><span class="sxs-lookup"><span data-stu-id="1220a-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="1220a-156">Här är ett exempel som väljer att avinstallera paketet baserat på dess namn. i vissa fall kan det vara lättare att filtrera med den **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="1220a-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="1220a-157">Ta bort andra program är inte var så enkel, även när klar lokalt.</span><span class="sxs-lookup"><span data-stu-id="1220a-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="1220a-158">Vi kan hitta kommandoraden avinstallera strängar för dessa program genom att extrahera den **UninstallString** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1220a-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="1220a-159">Den här metoden fungerar för Windows Installer-program och äldre program som visas under nyckeln Uninstall:</span><span class="sxs-lookup"><span data-stu-id="1220a-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="1220a-160">Du kan filtrera resultatet av visningsnamn, om du vill:</span><span class="sxs-lookup"><span data-stu-id="1220a-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="1220a-161">Dock kan dessa strängar inte användas direkt från Windows PowerShell-Kommandotolken utan några ändringar.</span><span class="sxs-lookup"><span data-stu-id="1220a-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="1220a-162">Uppgradera Windows Installer-program</span><span class="sxs-lookup"><span data-stu-id="1220a-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="1220a-163">Om du vill uppgradera ett program som du behöver känna till namnet på programmet och sökvägen till programmet uppgraderingspaket.</span><span class="sxs-lookup"><span data-stu-id="1220a-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="1220a-164">Med denna information kan du uppgradera ett program med ett enda Windows PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="1220a-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```