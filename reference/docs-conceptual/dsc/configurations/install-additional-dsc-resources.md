---
ms.date: 12/12/2018
keywords: DSC, PowerShell, resurs, Galleri, installation
title: Installera ytterligare DSC-resurser
ms.openlocfilehash: 7a6a935349358e11a77d2f00c0bf88e0ad18c097
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417791"
---
# <a name="install-additional-dsc-resources"></a><span data-ttu-id="42db9-103">Installera ytterligare DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="42db9-103">Install Additional DSC Resources</span></span>

<span data-ttu-id="42db9-104">PowerShell innehåller flera färdiga resurser för önskad tillstånds konfiguration (DSC).</span><span class="sxs-lookup"><span data-stu-id="42db9-104">PowerShell includes several Out-of-the-box resources for Desired State Configuration (DSC).</span></span> <span data-ttu-id="42db9-105">**PSDesiredStateConfiguration** -modulen innehåller alla OOB DSC-resurser som är tillgängliga på din speciella instans av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42db9-105">The **PSDesiredStateConfiguration** module contains all of the OOB DSC resources available on your specific instance of PowerShell.</span></span>

<span data-ttu-id="42db9-106">Det här är en lista över OOB-resurser som ingår i PowerShell 4,0 och en beskrivning av resursens funktioner.</span><span class="sxs-lookup"><span data-stu-id="42db9-106">This is a list of the OOB resources included in PowerShell 4.0 and a description of the resource's capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="42db9-107">Det här är en ofullständig lista eftersom antalet OOB-resurser har växt med varje version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42db9-107">This is an incomplete list, as the number of OOB resources has grown with each version of PowerShell.</span></span>

|<span data-ttu-id="42db9-108">Resurs</span><span class="sxs-lookup"><span data-stu-id="42db9-108">Resource</span></span>  |<span data-ttu-id="42db9-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="42db9-109">Description</span></span>  |
|---------|---------|
|<span data-ttu-id="42db9-110">**Fil**</span><span class="sxs-lookup"><span data-stu-id="42db9-110">**File**</span></span>|<span data-ttu-id="42db9-111">Styr tillstånd för filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="42db9-111">Controls the state of files and directories.</span></span> <span data-ttu-id="42db9-112">Kopierar filer från en **källa** till ett **mål** och uppdaterar dem när **källan** ändras genom att jämföra datum, kontroll summor och hash-värden.</span><span class="sxs-lookup"><span data-stu-id="42db9-112">Copies files from a **Source** to a **Destination** and updates them when the **Source** changes by comparing dates, checksums, and hashes.</span></span>|
|<span data-ttu-id="42db9-113">**Arkiv**</span><span class="sxs-lookup"><span data-stu-id="42db9-113">**Archive**</span></span>|<span data-ttu-id="42db9-114">Packar upp arkiv och en angiven plats.</span><span class="sxs-lookup"><span data-stu-id="42db9-114">Unpacks archives and a specified location.</span></span> <span data-ttu-id="42db9-115">Validerar arkiven med en angiven **kontroll Summa**.</span><span class="sxs-lookup"><span data-stu-id="42db9-115">Validates the archives with a specified **Checksum**.</span></span>|
|<span data-ttu-id="42db9-116">**Miljö**</span><span class="sxs-lookup"><span data-stu-id="42db9-116">**Environment**</span></span>|<span data-ttu-id="42db9-117">Hanterar miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="42db9-117">Manages environment variables.</span></span>|
|<span data-ttu-id="42db9-118">**Grupp**</span><span class="sxs-lookup"><span data-stu-id="42db9-118">**Group**</span></span>|<span data-ttu-id="42db9-119">Hanterar medlemskap i lokala grupper och kontroll grupper.</span><span class="sxs-lookup"><span data-stu-id="42db9-119">Manages local groups and controls group membership.</span></span>|
|<span data-ttu-id="42db9-120">**log**</span><span class="sxs-lookup"><span data-stu-id="42db9-120">**Log**</span></span>|<span data-ttu-id="42db9-121">Skriver meddelanden till händelse loggen `Microsoft-Windows-Desired State Configuration/Analytic`.</span><span class="sxs-lookup"><span data-stu-id="42db9-121">Writes messages to the `Microsoft-Windows-Desired State Configuration/Analytic` event log.</span></span>|
|<span data-ttu-id="42db9-122">**Paketfilerna**</span><span class="sxs-lookup"><span data-stu-id="42db9-122">**Package**</span></span>|<span data-ttu-id="42db9-123">Installerar eller avinstallerar paket med **argument**, **LogPath**, **ReturnCode**, andra inställningar.</span><span class="sxs-lookup"><span data-stu-id="42db9-123">Installs or uninstalls packages using **Arguments**, **LogPath**, **ReturnCode**, other settings.</span></span>|
|<span data-ttu-id="42db9-124">**Registernyckeln**</span><span class="sxs-lookup"><span data-stu-id="42db9-124">**Registry**</span></span>|<span data-ttu-id="42db9-125">Hanterar register nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="42db9-125">Manages registry keys and values.</span></span>|
|<span data-ttu-id="42db9-126">**Skript**</span><span class="sxs-lookup"><span data-stu-id="42db9-126">**Script**</span></span>|<span data-ttu-id="42db9-127">Gör att du kan skapa egna skript block för [Get-test-uppsättning](../resources/get-test-set.md) .</span><span class="sxs-lookup"><span data-stu-id="42db9-127">Allows you to design your own [get-test-set](../resources/get-test-set.md) script blocks.</span></span>|
|<span data-ttu-id="42db9-128">**Tjänst**</span><span class="sxs-lookup"><span data-stu-id="42db9-128">**Service**</span></span>|<span data-ttu-id="42db9-129">Konfigurerar Windows-tjänster.</span><span class="sxs-lookup"><span data-stu-id="42db9-129">Configures Windows services.</span></span>|
|<span data-ttu-id="42db9-130">**Användare**</span><span class="sxs-lookup"><span data-stu-id="42db9-130">**User**</span></span> |<span data-ttu-id="42db9-131">Hanterar lokala användare och attribut.</span><span class="sxs-lookup"><span data-stu-id="42db9-131">Manages local users and attributes.</span></span>|
|<span data-ttu-id="42db9-132">**WindowsFeature**</span><span class="sxs-lookup"><span data-stu-id="42db9-132">**WindowsFeature**</span></span>|<span data-ttu-id="42db9-133">Hanterar roller och funktioner.</span><span class="sxs-lookup"><span data-stu-id="42db9-133">Manages roles and features.</span></span>|
|<span data-ttu-id="42db9-134">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="42db9-134">**WindowsProcess**</span></span>|<span data-ttu-id="42db9-135">Konfigurerar Windows-processer.</span><span class="sxs-lookup"><span data-stu-id="42db9-135">Configures Windows processes.</span></span>|

<span data-ttu-id="42db9-136">OOB-resurserna gör det möjligt att använda en lämplig start punkt för vanliga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="42db9-136">The OOB resources allow a good starting point for common operations.</span></span> <span data-ttu-id="42db9-137">Om OOB-resurserna inte uppfyller dina behov kan du skriva en egen [anpassad resurs](../resources/authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="42db9-137">If the OOB resources do not meet your needs, you can write your own [Custom Resource](../resources/authoringResource.md).</span></span> <span data-ttu-id="42db9-138">Innan du skriver en anpassad resurs för att lösa problemet bör du titta igenom det stora antalet DSC-resurser som redan har skapats av både Microsoft och PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="42db9-138">Before you write a custom resource to solve your problem, you should look through the vast number of DSC resources that have already been created by both Microsoft and the PowerShell community.</span></span>

<span data-ttu-id="42db9-139">Du hittar DSC-resurser i både [PowerShell-galleriet](https://www.powershellgallery.com/) -och [GitHub](https://github.com/).</span><span class="sxs-lookup"><span data-stu-id="42db9-139">You can find DSC resources in both the [PowerShell Gallery](https://www.powershellgallery.com/) and [GitHub](https://github.com/).</span></span> <span data-ttu-id="42db9-140">Du kan också installera DSC-resurser direkt från PowerShell-konsolen med hjälp av [PowerShellGet](/powershell/module/powershellget/).</span><span class="sxs-lookup"><span data-stu-id="42db9-140">You can also install DSC resources directly from the PowerShell console using [PowerShellGet](/powershell/module/powershellget/).</span></span>

## <a name="installing-powershellget"></a><span data-ttu-id="42db9-141">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="42db9-141">Installing PowerShellGet</span></span>

<span data-ttu-id="42db9-142">Om du vill kontrol lera om du redan har **PowerShell** , eller om du vill ha hjälp med att installera den, kan du läsa följande guide: [installerar PowerShellGet](/powershell/scripting/gallery/installing-psget).</span><span class="sxs-lookup"><span data-stu-id="42db9-142">To determine if you already have **PowerShell** get, or to get help installing it, see the following guide: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).</span></span>

## <a name="finding-dsc-resources-using-powershellget"></a><span data-ttu-id="42db9-143">Hitta DSC-resurser med PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="42db9-143">Finding DSC resources using PowerShellGet</span></span>

<span data-ttu-id="42db9-144">När **PowerShellGet** har installerats på systemet kan du söka efter och installera DSC-resurser som finns i [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="42db9-144">Once **PowerShellGet** is installed on your system, you can find and install DSC resources hosted in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>

<span data-ttu-id="42db9-145">Använd först cmdleten [find-dscresource Keyword Supports](/powershell/module/powershellget/find-dscresource) för att hitta DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="42db9-145">First, use the [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet to find DSC resources.</span></span> <span data-ttu-id="42db9-146">När du kör `Find-DSCResource` för första gången visas följande uppmanad att installera "NuGet Provider".</span><span class="sxs-lookup"><span data-stu-id="42db9-146">When you run `Find-DSCResource` for the first time, you see the following prompt to install the "NuGet provider".</span></span>

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

<span data-ttu-id="42db9-147">När du har tryckt på "y" installeras "NuGet"-providern. du ser en lista över DSC-resurser som du kan installera från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="42db9-147">After pressing 'y', the "NuGet" provider is installed, you see a list of DSC resources that you can install from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="42db9-148">Listan visas inte eftersom den är mycket stor.</span><span class="sxs-lookup"><span data-stu-id="42db9-148">List is not shown because it is very large.</span></span>

<span data-ttu-id="42db9-149">Du kan också ange `-Name` parameter med jokertecken eller `-Filter` parameter utan jokertecken för att begränsa sökningen.</span><span class="sxs-lookup"><span data-stu-id="42db9-149">You can also specify the `-Name` parameter using wildcards, or `-Filter` parameter without wildcards to narrow down your search.</span></span> <span data-ttu-id="42db9-150">Det här exemplet försöker hitta en "TimeZone" DSC-resurs med hjälp av jokertecken.</span><span class="sxs-lookup"><span data-stu-id="42db9-150">This example attempts to find a "TimeZone" DSC resource using the wildcards.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42db9-151">För närvarande finns det ett fel i `Find-DSCResource` cmdlet som förhindrar användning av jokertecken i både parametrarna `-Name` och `-Filter`.</span><span class="sxs-lookup"><span data-stu-id="42db9-151">Currently there is a bug in the `Find-DSCResource` cmdlet that prevents using wildcards in both the `-Name` and `-Filter` parameters.</span></span> <span data-ttu-id="42db9-152">I det andra exemplet nedan visas en lösning med `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="42db9-152">The second example below shows a workaround using `Where-Object`.</span></span>

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

<span data-ttu-id="42db9-153">Du kan också använda `Where-Object` för att hitta DSC-resurser med mer detaljerad filtrering.</span><span class="sxs-lookup"><span data-stu-id="42db9-153">You can also use `Where-Object` to find DSC resources with more granular filtering.</span></span> <span data-ttu-id="42db9-154">Den här metoden går långsammare än att använda inbyggda filtrerings parametrar.</span><span class="sxs-lookup"><span data-stu-id="42db9-154">This approach will be slower than using built in filtering parameters.</span></span>

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

<span data-ttu-id="42db9-155">Mer information om filtrering finns i [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="42db9-155">For more information on filtering, see [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span>

## <a name="installing-dsc-resources-using-powershellget"></a><span data-ttu-id="42db9-156">Installera DSC-resurser med PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="42db9-156">Installing DSC Resources using PowerShellGet</span></span>

<span data-ttu-id="42db9-157">Om du vill installera en DSC-resurs använder du cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) och anger namnet på modulen som visas under **Modulnamn** i Sök resultatet.</span><span class="sxs-lookup"><span data-stu-id="42db9-157">To install a DSC resource, use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, specifying the name of the module shown under **Module** name in your search results.</span></span>

<span data-ttu-id="42db9-158">"TimeZone"-resursen finns i modulen "ComputerManagementDSC", så att är den modul som det här exemplet installerar.</span><span class="sxs-lookup"><span data-stu-id="42db9-158">The "TimeZone" resource exists in the "ComputerManagementDSC" module, so that is the module this example installs.</span></span>

> [!NOTE]
> <span data-ttu-id="42db9-159">Om du inte har betrott PowerShell-galleriet ser du varningen nedan och ber om bekräftelse och instruerar dig att undvika efterföljande frågor om installationer.</span><span class="sxs-lookup"><span data-stu-id="42db9-159">If you have not trusted the PowerShell gallery, you see the warning below asking for confirmation, and instructing you how to avoid subsequent prompts on installs.</span></span>

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="42db9-160">Tryck på "y" för att fortsätta installera modulen.</span><span class="sxs-lookup"><span data-stu-id="42db9-160">Press 'y' to continue installing the module.</span></span> <span data-ttu-id="42db9-161">Efter installationen kan du kontrol lera att den nya resursen är installerad med hjälp av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span><span class="sxs-lookup"><span data-stu-id="42db9-161">After install, you can verify that your new resource is installed using [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).</span></span>

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

<span data-ttu-id="42db9-162">Du kan också visa andra resurser i den nyligen installerade modulen genom att ange parametern `-ModuleName`.</span><span class="sxs-lookup"><span data-stu-id="42db9-162">You can also view other resources in your newly installed module, by specifying the `-ModuleName` parameter.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="42db9-163">Se även</span><span class="sxs-lookup"><span data-stu-id="42db9-163">See also</span></span>

- [<span data-ttu-id="42db9-164">Vad är resurser?</span><span class="sxs-lookup"><span data-stu-id="42db9-164">What are Resources?</span></span>](../resources/resources.md)
