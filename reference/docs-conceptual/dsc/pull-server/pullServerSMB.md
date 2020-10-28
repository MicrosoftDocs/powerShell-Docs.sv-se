---
ms.date: 04/11/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en DSC SMB-hämtningsserver
description: En DSC SMB-pull-server är en dator som är värd för SMB-filresurser som gör DSC-konfigurationsfiler och DSC-resurser tillgängliga för att rikta noder när dessa noder begär det.
ms.openlocfilehash: 4ac1b0db719fa124d6fa9a654acb64ec24d9ea41
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658424"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="e3830-104">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="e3830-104">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="e3830-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="e3830-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3830-106">Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="e3830-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="e3830-107">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="e3830-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="e3830-108">En DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) -pull-server är en dator som är värd för SMB-filresurser som gör DSC-KONFIGURATIONSFILER och DSC-resurser tillgängliga för att rikta noder när dessa noder begär det.</span><span class="sxs-lookup"><span data-stu-id="e3830-108">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="e3830-109">Om du vill använda en SMB-pull-server för DSC måste du:</span><span class="sxs-lookup"><span data-stu-id="e3830-109">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="e3830-110">Konfigurera en SMB-filresurs på en server som kör PowerShell 4,0 eller senare</span><span class="sxs-lookup"><span data-stu-id="e3830-110">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="e3830-111">Konfigurera en klient som kör PowerShell 4,0 eller senare för att hämta från den SMB-resursen</span><span class="sxs-lookup"><span data-stu-id="e3830-111">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="e3830-112">Använda xSmbShare-resursen för att skapa en SMB-filresurs</span><span class="sxs-lookup"><span data-stu-id="e3830-112">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="e3830-113">Det finns ett antal sätt att konfigurera en SMB-filresurs, men vi ska titta på hur du kan göra detta med hjälp av DSC.</span><span class="sxs-lookup"><span data-stu-id="e3830-113">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="e3830-114">Installera xSmbShare-resursen</span><span class="sxs-lookup"><span data-stu-id="e3830-114">Install the xSmbShare resource</span></span>

<span data-ttu-id="e3830-115">Anropa cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xSmbShare** -modulen.</span><span class="sxs-lookup"><span data-stu-id="e3830-115">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="e3830-116">`Install-Module` ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="e3830-116">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span>
> <span data-ttu-id="e3830-117">**XSmbShare** innehåller DSC- **xSmbShare** som kan användas för att skapa en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="e3830-117">The **xSmbShare** contains the DSC resource **xSmbShare** , which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="e3830-118">Skapa katalogen och fil resursen</span><span class="sxs-lookup"><span data-stu-id="e3830-118">Create the directory and file share</span></span>

<span data-ttu-id="e3830-119">Följande konfiguration använder **fil** resursen för att skapa katalogen för resursen och **xSmbShare** -RESURSEN för att konfigurera SMB-resursen:</span><span class="sxs-lookup"><span data-stu-id="e3830-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="e3830-120">Konfigurationen skapar katalogen `C:\DscSmbShare` , om den inte redan finns, och använder den katalogen som en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="e3830-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="e3830-121">**FullAccess** bör ges till alla konton som behöver skrivas till eller tas bort från fil resursen.</span><span class="sxs-lookup"><span data-stu-id="e3830-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="e3830-122">**ReadAccess** måste ges till alla-klientsessioner som får konfigurationer och/eller DSC-resurser från resursen.</span><span class="sxs-lookup"><span data-stu-id="e3830-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="e3830-123">DSC körs som standard system kontot, så själva datorn måste ha åtkomst till resursen.</span><span class="sxs-lookup"><span data-stu-id="e3830-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="e3830-124">Ge fil system åtkomst till pull-klienten</span><span class="sxs-lookup"><span data-stu-id="e3830-124">Give file system access to the pull client</span></span>

<span data-ttu-id="e3830-125">Genom att ge **ReadAccess** till en-klusternod kan noden få åtkomst till SMB-resursen, men inte till filer eller mappar i resursen.</span><span class="sxs-lookup"><span data-stu-id="e3830-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="e3830-126">Du måste uttryckligen bevilja klient noderna åtkomst till mappen SMB-resurs och undermappar.</span><span class="sxs-lookup"><span data-stu-id="e3830-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="e3830-127">Vi kan göra detta med DSC genom att lägga till med hjälp av **cNtfsPermissionEntry** -resursen, som finns i [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) -modulen.</span><span class="sxs-lookup"><span data-stu-id="e3830-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span>
<span data-ttu-id="e3830-128">Följande konfiguration lägger till ett **cNtfsPermissionEntry** -block som ger ReadAndExecute åtkomst till pull-klienten:</span><span class="sxs-lookup"><span data-stu-id="e3830-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="e3830-129">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="e3830-129">Placing configurations and resources</span></span>

<span data-ttu-id="e3830-130">Spara eventuella konfigurations-MOF-filer och/eller DSC-resurser som du vill att klientsessioner ska hämta i mappen SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="e3830-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="e3830-131">En MOF-konfigurationsfil måste ha namnet *ConfigurationID* . MOF, där *ConfigurationID* är värdet för egenskapen **ConfigurationID** i nodens LCM.</span><span class="sxs-lookup"><span data-stu-id="e3830-131">Any configuration MOF file must be named *ConfigurationID* .mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="e3830-132">Mer information om hur du konfigurerar pull-klienter finns i [Konfigurera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="e3830-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e3830-133">Du måste använda konfigurations-ID: n om du använder en SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="e3830-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="e3830-134">Konfigurations namn stöds inte för SMB.</span><span class="sxs-lookup"><span data-stu-id="e3830-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="e3830-135">Varje resurs-modul måste vara zippad och namngiven enligt följande mönster `{Module Name}_{Module Version}.zip` .</span><span class="sxs-lookup"><span data-stu-id="e3830-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="e3830-136">Till exempel skulle en modul med namnet xWebAdminstration med en modul version av 3.1.2.0 heta "xWebAdministration_3.2.1.0.zip".</span><span class="sxs-lookup"><span data-stu-id="e3830-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="e3830-137">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="e3830-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="e3830-138">Separata versioner av en modul i en zip-fil stöds inte.</span><span class="sxs-lookup"><span data-stu-id="e3830-138">Separate versions of a module in a zip file are not supported.</span></span>
<span data-ttu-id="e3830-139">Innan du packar upp DSC-resurspooler för användning med pull server måste du göra en liten ändring i katalog strukturen.</span><span class="sxs-lookup"><span data-stu-id="e3830-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="e3830-140">Standardformat för moduler som innehåller DSC-resurser i WMF 5,0 är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\` .</span><span class="sxs-lookup"><span data-stu-id="e3830-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="e3830-141">Innan du packar upp för pull-servern tar du bara bort `{Module version}` mappen så att sökvägen blir `{Module Folder}\DscResources\{DSC Resource Folder}\` .</span><span class="sxs-lookup"><span data-stu-id="e3830-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="e3830-142">Med den här ändringen zip-mappen enligt beskrivningen ovan och placera dessa zip-filer i mappen SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="e3830-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="e3830-143">Skapa MOF-kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="e3830-143">Creating the MOF checksum</span></span>

<span data-ttu-id="e3830-144">En konfigurations-MOF-fil måste kombineras med en kontroll Summa fil så att en LCM på en målnod kan verifiera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="e3830-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="e3830-145">Om du vill skapa en kontroll Summa anropar du cmdleten [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) .</span><span class="sxs-lookup"><span data-stu-id="e3830-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="e3830-146">Cmdleten tar en `Path` parameter som anger den mapp där MOF-konfigurationsfilen finns.</span><span class="sxs-lookup"><span data-stu-id="e3830-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="e3830-147">Cmdleten skapar en kontroll Summa fil med namnet `ConfigurationMOFName.mof.checksum` , där `ConfigurationMOFName` är namnet på MOF-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="e3830-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="e3830-148">Om det finns fler än en konfigurations-MOF-fil i den angivna mappen skapas en kontroll summa för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="e3830-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="e3830-149">Kontroll Summa filen måste finnas i samma katalog som MOF-filen för konfiguration ( `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard) och ha samma namn med `.checksum` tillägget bifogad.</span><span class="sxs-lookup"><span data-stu-id="e3830-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="e3830-150">Om du ändrar konfigurations-MOF-filen på valfritt sätt måste du också återskapa kontroll Summa filen.</span><span class="sxs-lookup"><span data-stu-id="e3830-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="e3830-151">Konfigurera en pull-klient för SMB</span><span class="sxs-lookup"><span data-stu-id="e3830-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="e3830-152">Om du vill konfigurera en klient som hämtar konfigurationer och/eller resurser från en SMB-resurs konfigurerar du klientens lokala Configuration Manager (LCM) med **ConfigurationRepositoryShare** -och **ResourceRepositoryShare** -block som anger den resurs som ska hämta konfigurationer och DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="e3830-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="e3830-153">Mer information om hur du konfigurerar LCM finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="e3830-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e3830-154">För enkelhetens skull använder det här exemplet **PSDscAllowPlainTextPassword** för att skicka ett lösen ord i klartext till parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="e3830-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="e3830-155">Information om hur du skickar autentiseringsuppgifter säkrare finns i [alternativ för autentiseringsuppgifter i konfigurations data](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="e3830-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span> <span data-ttu-id="e3830-156">Du **måste** ange en **ConfigurationID** i **inställnings** blocket för en metaconfiguration för en SMB-pull-server, även om du bara ska hämta resurser.</span><span class="sxs-lookup"><span data-stu-id="e3830-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="e3830-157">Erkännanden</span><span class="sxs-lookup"><span data-stu-id="e3830-157">Acknowledgements</span></span>

<span data-ttu-id="e3830-158">Särskilt tack för följande individer:</span><span class="sxs-lookup"><span data-stu-id="e3830-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="e3830-159">Mike F. Robbins, vars inlägg på att använda SMB för DSC, hjälpte att informera innehållet i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e3830-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="e3830-160">Hans blogg är på [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="e3830-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="e3830-161">Serge Nikalaichyk, som skapade **cNtfsAccessControl** -modulen.</span><span class="sxs-lookup"><span data-stu-id="e3830-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="e3830-162">Källan för den här modulen finns på [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="e3830-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3830-163">Se även</span><span class="sxs-lookup"><span data-stu-id="e3830-163">See also</span></span>

[<span data-ttu-id="e3830-164">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3830-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="e3830-165">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="e3830-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="e3830-166">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="e3830-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
