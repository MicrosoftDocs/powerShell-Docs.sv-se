---
ms.date: 12/12/2018
keywords: DSC, powershell, resurs, galleriet, inställning
title: Installera ytterligare DSC-resurser
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405213"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="23535-103">Installera ytterligare DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="23535-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="23535-104">PowerShell innehåller flera Out-of the box-resurser för Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="23535-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="23535-105">Den **PSDesiredStateConfiguration** modulen innehåller alla OOB DSC-resurser tillgängliga på dina specifika instansen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23535-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="23535-106">Det här är en lista över OOB-resurser som ingår i PowerShell 4.0 och en beskrivning av resursens funktioner.</span><span class="sxs-lookup"><span data-stu-id="23535-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="23535-107">Detta är en ofullständig lista eftersom antalet OOB-resurser har vuxit med respektive version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23535-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="23535-108">Resurs</span><span class="sxs-lookup"><span data-stu-id="23535-108">Resource</span></span>  |<span data-ttu-id="23535-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="23535-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="23535-110">**Filen**</span><span class="sxs-lookup"><span data-stu-id="23535-110">**File**</span></span>|<span data-ttu-id="23535-111">Kontrollerar tillståndet för filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="23535-111">Controls the state of files and directories.</span></span> <span data-ttu-id="23535-112">Kopierar filer från en **källa** till en **mål** och uppdaterar dem när de **källa** ändringar genom att jämföra datum, kontrollsummor och hashvärden.</span><span class="sxs-lookup"><span data-stu-id="23535-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="23535-113">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="23535-113">**Archive**</span></span>|<span data-ttu-id="23535-114">Har packats upp Arkiv och en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="23535-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="23535-115">Verifierar Arkiv med en angiven **kontrollsumma**.</span><span class="sxs-lookup"><span data-stu-id="23535-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="23535-116">**Miljö**</span><span class="sxs-lookup"><span data-stu-id="23535-116">**Environment**</span></span>|<span data-ttu-id="23535-117">Hanterar miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="23535-117">Manages environment variables.</span></span>|
|<span data-ttu-id="23535-118">**Grupp**</span><span class="sxs-lookup"><span data-stu-id="23535-118">**Group**</span></span>|<span data-ttu-id="23535-119">Hanterar lokala grupper och styr medlemskap.</span><span class="sxs-lookup"><span data-stu-id="23535-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="23535-120">**Log**</span><span class="sxs-lookup"><span data-stu-id="23535-120">**Log**</span></span>|<span data-ttu-id="23535-121">Skriver meddelanden till den `Microsoft-Windows-Desired State Configuration/Analytic` händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="23535-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="23535-122">**Paketet**</span><span class="sxs-lookup"><span data-stu-id="23535-122">**Package**</span></span>|<span data-ttu-id="23535-123">Installerar eller avinstallerar paket med hjälp av **argument**, **LogPath**, **ReturnCode**, andra inställningar.</span><span class="sxs-lookup"><span data-stu-id="23535-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="23535-124">**registret**</span><span class="sxs-lookup"><span data-stu-id="23535-124">**Registry**</span></span>|<span data-ttu-id="23535-125">Hanterar registernycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="23535-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="23535-126">**Skriptet**</span><span class="sxs-lookup"><span data-stu-id="23535-126">**Script**</span></span>|<span data-ttu-id="23535-127">Låter dig utforma din egen [get testmängd](../resources/get-test-set.md) skript block.</span><span class="sxs-lookup"><span data-stu-id="23535-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="23535-128">**Tjänsten**</span><span class="sxs-lookup"><span data-stu-id="23535-128">**Service**</span></span>|<span data-ttu-id="23535-129">Konfigurerar Windows-tjänster.</span><span class="sxs-lookup"><span data-stu-id="23535-129">Configures Windows services.</span></span>|
|<span data-ttu-id="23535-130">**Användaren**</span><span class="sxs-lookup"><span data-stu-id="23535-130">**User**</span></span> |<span data-ttu-id="23535-131">Hanterar lokala användare och attribut.</span><span class="sxs-lookup"><span data-stu-id="23535-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="23535-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="23535-132">**WindowsFeature**</span></span>|<span data-ttu-id="23535-133">Hanterar roller och funktioner.</span><span class="sxs-lookup"><span data-stu-id="23535-133">Manages roles and features.</span></span>|
|<span data-ttu-id="23535-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="23535-134">**WindowsProcess**</span></span>|<span data-ttu-id="23535-135">Konfigurerar Windows-processer.</span><span class="sxs-lookup"><span data-stu-id="23535-135">Configures Windows processes.</span></span>|

<span data-ttu-id="23535-136">OOB-resurser kan en bra utgångspunkt för vanliga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="23535-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="23535-137">Om OOB-resurser inte uppfyller dina behov kan du skriva din egen [anpassade resursen](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="23535-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="23535-138">Innan du skriver en anpassad resurs för att lösa problemet, bör du titta igenom stora antalet DSC-resurser som redan har skapats av både Microsoft och PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="23535-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="23535-139">Du kan hitta DSC-resurser i både den [PowerShell-galleriet](https://www.powershellgallery.com/) och [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="23535-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="23535-140">Du kan också installera DSC-resurser direkt från PowerShell-konsolen med [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="23535-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="23535-141">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="23535-141">Installing PowerShellGet</span></span>

<span data-ttu-id="23535-142">Att fastställa om du redan har **PowerShell** hämta, eller om du vill ha hjälp med att installera den finns i guiden följande: [Installera PowerShellGet](/powershell/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="23535-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="23535-143">Hitta DSC-resurser med PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="23535-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="23535-144">En gång **PowerShellGet** är installerad på datorn, kan du hitta och installera DSC-resurser som finns i den [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="23535-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="23535-145">Använd först den [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet för att hitta DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="23535-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="23535-146">När du kör `Find-DSCResource` för första gången, visas följande meddelande att installera ”NuGet-providern”.</span><span class="sxs-lookup"><span data-stu-id="23535-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

<span data-ttu-id="23535-147">När du trycker på ”y”, ”NuGet”-providern har installerats ser du en lista över DSC-resurser som du kan installera från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="23535-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="23535-148">Lista visas inte eftersom det är mycket stort.</span><span class="sxs-lookup"><span data-stu-id="23535-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="23535-149">Du kan också ange den `-Name` med jokertecken, parametern eller `-Filter` parametern utan jokertecken för att begränsa sökningen.</span><span class="sxs-lookup"><span data-stu-id="23535-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="23535-150">Det här exemplet försöker hitta en ”tidszon” DSC-resurs med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="23535-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23535-151">Det finns för närvarande en bugg i den `Find-DSCResource` cmdlet som förhindrar med jokertecken i både den `-Name` och `-Filter` parametrar.</span><span class="sxs-lookup"><span data-stu-id="23535-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="23535-152">Det andra exemplet nedan visar en lösning med hjälp av `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="23535-152">The second example below shows a workaround using `Where-Object`.</span></span>

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

<span data-ttu-id="23535-153">Du kan också använda `Where-Object` att hitta DSC-resurser med mer detaljerade filtrering.</span><span class="sxs-lookup"><span data-stu-id="23535-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="23535-154">Den här metoden blir långsammare än att använda inbyggda filtrering parametrar.</span><span class="sxs-lookup"><span data-stu-id="23535-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="23535-155">Mer information om filtrering finns [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="23535-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="23535-156">Installera DSC-resurser med PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="23535-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="23535-157">Om du vill installera en DSC-resurs i [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, anger namnet på modulen visas under **modulen** i sökresultaten.</span><span class="sxs-lookup"><span data-stu-id="23535-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="23535-158">”Tidszon” resursen finns i modulen ”ComputerManagementDSC” så att det inte modulen i detta exempel installeras.</span><span class="sxs-lookup"><span data-stu-id="23535-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="23535-159">Om du inte har betrott PowerShell-galleriet, visas varningen nedan behöver bekräfta och anvisningar om hur du hur du undviker efterföljande anvisningarna på installerar.</span><span class="sxs-lookup"><span data-stu-id="23535-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="23535-160">Tryck på y om du vill fortsätta att installera modulen.</span><span class="sxs-lookup"><span data-stu-id="23535-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="23535-161">Efter installationen, kan du kontrollera att din nya resurs är installerad med hjälp av [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="23535-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="23535-162">Du kan också visa andra resurser i din nyligen installerade modulen genom att ange den `-ModuleName` parametern.</span><span class="sxs-lookup"><span data-stu-id="23535-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a><span data-ttu-id="23535-163">Se även</span><span class="sxs-lookup"><span data-stu-id="23535-163">See also</span></span>

- [<span data-ttu-id="23535-164">Vad är resurser?</span><span class="sxs-lookup"><span data-stu-id="23535-164">What are Resources?</span></span>](../resources/resources.md)
