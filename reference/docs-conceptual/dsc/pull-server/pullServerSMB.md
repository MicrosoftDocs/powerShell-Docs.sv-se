---
ms.date: 04/11/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en DSC SMB-hämtningsserver
ms.openlocfilehash: be41f7a708f1a129919fae8300fc4307441097f7
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500709"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="699c2-103">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="699c2-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="699c2-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="699c2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="699c2-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="699c2-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="699c2-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="699c2-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="699c2-107">En DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) -pull-server är en dator som är värd för SMB-filresurser som gör DSC-KONFIGURATIONSFILER och DSC-resurser tillgängliga för att rikta noder när dessa noder begär det.</span><span class="sxs-lookup"><span data-stu-id="699c2-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="699c2-108">Om du vill använda en SMB-pull-server för DSC måste du:</span><span class="sxs-lookup"><span data-stu-id="699c2-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="699c2-109">Konfigurera en SMB-filresurs på en server som kör PowerShell 4,0 eller senare</span><span class="sxs-lookup"><span data-stu-id="699c2-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="699c2-110">Konfigurera en klient som kör PowerShell 4,0 eller senare för att hämta från den SMB-resursen</span><span class="sxs-lookup"><span data-stu-id="699c2-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="699c2-111">Använda xSmbShare-resursen för att skapa en SMB-filresurs</span><span class="sxs-lookup"><span data-stu-id="699c2-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="699c2-112">Det finns ett antal sätt att konfigurera en SMB-filresurs, men vi ska titta på hur du kan göra detta med hjälp av DSC.</span><span class="sxs-lookup"><span data-stu-id="699c2-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="699c2-113">Installera xSmbShare-resursen</span><span class="sxs-lookup"><span data-stu-id="699c2-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="699c2-114">Anropa cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xSmbShare** -modulen.</span><span class="sxs-lookup"><span data-stu-id="699c2-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="699c2-115">`Install-Module` ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="699c2-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span>
> <span data-ttu-id="699c2-116">**XSmbShare** innehåller DSC- **xSmbShare**som kan användas för att skapa en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="699c2-116">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="699c2-117">Skapa katalogen och fil resursen</span><span class="sxs-lookup"><span data-stu-id="699c2-117">Create the directory and file share</span></span>

<span data-ttu-id="699c2-118">Följande konfiguration använder **fil** resursen för att skapa katalogen för resursen och **xSmbShare** -RESURSEN för att konfigurera SMB-resursen:</span><span class="sxs-lookup"><span data-stu-id="699c2-118">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="699c2-119">Konfigurationen skapar katalogen `C:\DscSmbShare`, om den inte redan finns, och sedan används den katalogen som en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="699c2-119">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="699c2-120">**FullAccess** bör ges till alla konton som behöver skrivas till eller tas bort från fil resursen.</span><span class="sxs-lookup"><span data-stu-id="699c2-120">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="699c2-121">**ReadAccess** måste ges till alla-klientsessioner som får konfigurationer och/eller DSC-resurser från resursen.</span><span class="sxs-lookup"><span data-stu-id="699c2-121">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="699c2-122">DSC körs som standard system kontot, så själva datorn måste ha åtkomst till resursen.</span><span class="sxs-lookup"><span data-stu-id="699c2-122">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="699c2-123">Ge fil system åtkomst till pull-klienten</span><span class="sxs-lookup"><span data-stu-id="699c2-123">Give file system access to the pull client</span></span>

<span data-ttu-id="699c2-124">Genom att ge **ReadAccess** till en-klusternod kan noden få åtkomst till SMB-resursen, men inte till filer eller mappar i resursen.</span><span class="sxs-lookup"><span data-stu-id="699c2-124">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="699c2-125">Du måste uttryckligen bevilja klient noderna åtkomst till mappen SMB-resurs och undermappar.</span><span class="sxs-lookup"><span data-stu-id="699c2-125">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="699c2-126">Vi kan göra detta med DSC genom att lägga till med hjälp av **cNtfsPermissionEntry** -resursen, som finns i [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) -modulen.</span><span class="sxs-lookup"><span data-stu-id="699c2-126">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span>
<span data-ttu-id="699c2-127">Följande konfiguration lägger till ett **cNtfsPermissionEntry** -block som ger ReadAndExecute åtkomst till pull-klienten:</span><span class="sxs-lookup"><span data-stu-id="699c2-127">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="699c2-128">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="699c2-128">Placing configurations and resources</span></span>

<span data-ttu-id="699c2-129">Spara eventuella konfigurations-MOF-filer och/eller DSC-resurser som du vill att klientsessioner ska hämta i mappen SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="699c2-129">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="699c2-130">En MOF-konfigurationsfil måste ha namnet *ConfigurationID*. MOF, där *ConfigurationID* är värdet för egenskapen **ConfigurationID** i nodens LCM.</span><span class="sxs-lookup"><span data-stu-id="699c2-130">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="699c2-131">Mer information om hur du konfigurerar pull-klienter finns i [Konfigurera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="699c2-131">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="699c2-132">Du måste använda konfigurations-ID: n om du använder en SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="699c2-132">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="699c2-133">Konfigurations namn stöds inte för SMB.</span><span class="sxs-lookup"><span data-stu-id="699c2-133">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="699c2-134">Varje resurs-modul måste vara zippad och namngiven enligt följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="699c2-134">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="699c2-135">Till exempel skulle en modul med namnet xWebAdminstration med en modul version av 3.1.2.0 heta "xWebAdministration_3.2.1.0. zip".</span><span class="sxs-lookup"><span data-stu-id="699c2-135">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="699c2-136">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="699c2-136">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="699c2-137">Separata versioner av en modul i en zip-fil stöds inte.</span><span class="sxs-lookup"><span data-stu-id="699c2-137">Separate versions of a module in a zip file are not supported.</span></span>
<span data-ttu-id="699c2-138">Innan du packar upp DSC-resurspooler för användning med pull server måste du göra en liten ändring i katalog strukturen.</span><span class="sxs-lookup"><span data-stu-id="699c2-138">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="699c2-139">Standardformat för moduler som innehåller DSC-resurs i WMF 5,0 är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="699c2-139">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="699c2-140">Innan du packar upp för pull-servern tar du bara bort mappen `{Module version}` så att sökvägen blir `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="699c2-140">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="699c2-141">Med den här ändringen zip-mappen enligt beskrivningen ovan och placera dessa zip-filer i mappen SMB-resurs.</span><span class="sxs-lookup"><span data-stu-id="699c2-141">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="699c2-142">Skapa MOF-kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="699c2-142">Creating the MOF checksum</span></span>

<span data-ttu-id="699c2-143">En konfigurations-MOF-fil måste kombineras med en kontroll Summa fil så att en LCM på en målnod kan verifiera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="699c2-143">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="699c2-144">Om du vill skapa en kontroll Summa anropar du cmdleten [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) .</span><span class="sxs-lookup"><span data-stu-id="699c2-144">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="699c2-145">Cmdleten använder en `Path` parameter som anger den mapp där MOF-konfigurationsfilen finns.</span><span class="sxs-lookup"><span data-stu-id="699c2-145">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="699c2-146">Cmdleten skapar en kontroll Summa fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på MOF-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="699c2-146">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="699c2-147">Om det finns fler än en konfigurations-MOF-fil i den angivna mappen skapas en kontroll summa för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="699c2-147">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="699c2-148">Kontroll Summa filen måste finnas i samma katalog som MOF-konfigurationsfilen (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard) och ha samma namn med tillägget `.checksum` tillägget.</span><span class="sxs-lookup"><span data-stu-id="699c2-148">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="699c2-149">Om du ändrar konfigurations-MOF-filen på valfritt sätt måste du också återskapa kontroll Summa filen.</span><span class="sxs-lookup"><span data-stu-id="699c2-149">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="699c2-150">Konfigurera en pull-klient för SMB</span><span class="sxs-lookup"><span data-stu-id="699c2-150">Setting up a pull client for SMB</span></span>

<span data-ttu-id="699c2-151">Om du vill konfigurera en klient som hämtar konfigurationer och/eller resurser från en SMB-resurs konfigurerar du klientens lokala Configuration Manager (LCM) med **ConfigurationRepositoryShare** -och **ResourceRepositoryShare** -block som anger den resurs som ska hämta konfigurationer och DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="699c2-151">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="699c2-152">Mer information om hur du konfigurerar LCM finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="699c2-152">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="699c2-153">För enkelhetens skull använder det här exemplet **PSDscAllowPlainTextPassword** för att skicka ett lösen ord i klartext till parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="699c2-153">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="699c2-154">Information om hur du skickar autentiseringsuppgifter säkrare finns i [alternativ för autentiseringsuppgifter i konfigurations data](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="699c2-154">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span> <span data-ttu-id="699c2-155">Du **måste** ange en **ConfigurationID** i **inställnings** blocket för en metaconfiguration för en SMB-pull-server, även om du bara ska hämta resurser.</span><span class="sxs-lookup"><span data-stu-id="699c2-155">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="699c2-156">Erkännanden</span><span class="sxs-lookup"><span data-stu-id="699c2-156">Acknowledgements</span></span>

<span data-ttu-id="699c2-157">Särskilt tack för följande individer:</span><span class="sxs-lookup"><span data-stu-id="699c2-157">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="699c2-158">Mike F. Robbins, vars inlägg på att använda SMB för DSC, hjälpte att informera innehållet i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="699c2-158">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="699c2-159">Hans blogg är på [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="699c2-159">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="699c2-160">Serge Nikalaichyk, som skapade **cNtfsAccessControl** -modulen.</span><span class="sxs-lookup"><span data-stu-id="699c2-160">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="699c2-161">Källan för den här modulen finns på [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="699c2-161">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="699c2-162">Se även</span><span class="sxs-lookup"><span data-stu-id="699c2-162">See also</span></span>

[<span data-ttu-id="699c2-163">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="699c2-163">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="699c2-164">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="699c2-164">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="699c2-165">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="699c2-165">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
