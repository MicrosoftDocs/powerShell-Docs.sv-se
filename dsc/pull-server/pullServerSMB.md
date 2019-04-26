---
ms.date: 04/11/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en DSC SMB-hämtningsserver
ms.openlocfilehash: 9d087a08861b2f4683e81efd1e25f857b8b75e07
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079293"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="837a0-103">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="837a0-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="837a0-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="837a0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="837a0-105">Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="837a0-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="837a0-106">Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="837a0-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="837a0-107">En DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) hämtningsservern är en dator som är värd för SMB-filresurser som gör DSC-konfigurationsfiler och DSC-resurser tillgängliga för målnoder när de noderna som ber om.</span><span class="sxs-lookup"><span data-stu-id="837a0-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="837a0-108">Om du vill använda en SMB-pullserver för DSC, behöver du:</span><span class="sxs-lookup"><span data-stu-id="837a0-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="837a0-109">Konfigurera en SMB-filresurs på en server med PowerShell 4.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="837a0-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="837a0-110">Konfigurera en klient som kör PowerShell 4.0 eller senare för att hämta från den SMB-resursen</span><span class="sxs-lookup"><span data-stu-id="837a0-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="837a0-111">Använda xSmbShare resursen för att skapa en SMB-filresurs</span><span class="sxs-lookup"><span data-stu-id="837a0-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="837a0-112">Det finns ett antal sätt att konfigurera en SMB-filresurs, men låt oss titta på hur du kan göra detta med hjälp av DSC.</span><span class="sxs-lookup"><span data-stu-id="837a0-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="837a0-113">Installera xSmbShare resursen</span><span class="sxs-lookup"><span data-stu-id="837a0-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="837a0-114">Anropa den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att installera den **xSmbShare** modulen.</span><span class="sxs-lookup"><span data-stu-id="837a0-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="837a0-115">`Install-Module` ingår i den **PowerShellGet** modulen, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="837a0-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="837a0-116">Du kan ladda ned den **PowerShellGet** -modulen för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler förhandsversion](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="837a0-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="837a0-117">Den **xSmbShare** innehåller DSC-resurs **xSmbShare**, som kan användas för att skapa en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="837a0-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="837a0-118">Skapa katalog och filresursen</span><span class="sxs-lookup"><span data-stu-id="837a0-118">Create the directory and file share</span></span>

<span data-ttu-id="837a0-119">Följande konfiguration använder den **filen** resursen för att skapa katalogen för resursen och **xSmbShare** resursen för att konfigurera SMB-resurs:</span><span class="sxs-lookup"><span data-stu-id="837a0-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="837a0-120">Konfigurationen skapar katalogen `C:\DscSmbShare`, om den inte redan finns, och sedan använder den katalogen som en SMB-filresurs.</span><span class="sxs-lookup"><span data-stu-id="837a0-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="837a0-121">**FullAccess** ska ges till alla konton som krävs för att skriva till eller ta bort från filresursen.</span><span class="sxs-lookup"><span data-stu-id="837a0-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="837a0-122">**Läsåtkomst** måste anges till klientnoder som få konfigurationer och/eller DSC-resurser från resursen.</span><span class="sxs-lookup"><span data-stu-id="837a0-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="837a0-123">DSC körs som system-kontot som standard så att själva datorn måste ha åtkomst till resursen.</span><span class="sxs-lookup"><span data-stu-id="837a0-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="837a0-124">Ge behörighet till pull-klienten</span><span class="sxs-lookup"><span data-stu-id="837a0-124">Give file system access to the pull client</span></span>

<span data-ttu-id="837a0-125">Ge **läsåtkomst** till en klient noden kan noden för att få åtkomst till SMB-resursen, men inte till filer eller mappar i som delar.</span><span class="sxs-lookup"><span data-stu-id="837a0-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="837a0-126">Du måste uttryckligen bevilja klienten noder åtkomst till SMB-delade mappen och undermappar.</span><span class="sxs-lookup"><span data-stu-id="837a0-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="837a0-127">Vi kan göra detta med DSC genom att lägga till med hjälp av den **cNtfsPermissionEntry** resurs, som finns i den [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modulen.</span><span class="sxs-lookup"><span data-stu-id="837a0-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="837a0-128">Lägger till följande konfiguration en **cNtfsPermissionEntry** block som beviljar ReadAndExecute åtkomst till pull-klienten:</span><span class="sxs-lookup"><span data-stu-id="837a0-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="837a0-129">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="837a0-129">Placing configurations and resources</span></span>

<span data-ttu-id="837a0-130">Spara konfigurationen MOF-filer och/eller DSC-resurser som du vill att klientnoder att dra in den SMB-delade mappen.</span><span class="sxs-lookup"><span data-stu-id="837a0-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="837a0-131">Alla MOF-konfigurationsfilen måste ha namnet *ConfigurationID*.mof, där *ConfigurationID* är värdet för den **ConfigurationID** egenskapen för den målnoden MGM.</span><span class="sxs-lookup"><span data-stu-id="837a0-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="837a0-132">Mer information om hur du konfigurerar pull-klienter finns i [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="837a0-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="837a0-133">Du måste använda konfigurations-ID om du använder en SMB-pullserver.</span><span class="sxs-lookup"><span data-stu-id="837a0-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="837a0-134">Konfigurationsnamn har inte stöd för SMB.</span><span class="sxs-lookup"><span data-stu-id="837a0-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="837a0-135">Varje Resursmodul måste zippade och med namnet enligt följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="837a0-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="837a0-136">Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 ”xWebAdministration_3.2.1.0.zip”.</span><span class="sxs-lookup"><span data-stu-id="837a0-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="837a0-137">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="837a0-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="837a0-138">Olika versioner av en modul i en zip-fil stöds inte.</span><span class="sxs-lookup"><span data-stu-id="837a0-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="837a0-139">Innan packa upp DSC-resurs-moduler för användning med pull-server måste du göra små ändringar i katalogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="837a0-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="837a0-140">Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="837a0-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="837a0-141">Innan du paketering för hämtningsservern helt enkelt ta bort den `{Module version}` mapp så blir sökvägen `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="837a0-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="837a0-142">Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den SMB-delade mappen.</span><span class="sxs-lookup"><span data-stu-id="837a0-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="837a0-143">Skapa MOF-kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="837a0-143">Creating the MOF checksum</span></span>

<span data-ttu-id="837a0-144">En MOF-konfigurationsfilen måste kopplas till en kontrollsumma-fil så att en LCM på målnoden verifiera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="837a0-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="837a0-145">Om du vill skapa en kontrollsumma, anropa den [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="837a0-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="837a0-146">Cmdlet: en tar en `Path` parameter som anger den mapp där konfigurationen MOF finns.</span><span class="sxs-lookup"><span data-stu-id="837a0-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="837a0-147">Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på mof-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="837a0-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="837a0-148">Om det finns flera olika konfigurationer MOF-filer i en angiven mapp, skapas en kontrollsumma för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="837a0-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="837a0-149">Filen kontrollsumma måste finnas i samma katalog som MOF-konfigurationsfilen (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard), och har samma namn som den `.checksum` tillägget sist.</span><span class="sxs-lookup"><span data-stu-id="837a0-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="837a0-150">Om du ändrar MOF-konfigurationsfilen på något sätt, måste du också återskapa filen kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="837a0-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="837a0-151">Konfigurera en hämtningsklient för SMB</span><span class="sxs-lookup"><span data-stu-id="837a0-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="837a0-152">Om du vill konfigurera en klient som tar emot konfigurationer och/eller resurser från en SMB-resurs kan du konfigurera klientens lokala Configuration Manager (LCM) med **ConfigurationRepositoryShare** och **ResourceRepositoryShare** block som anger den resurs som ska hämta konfigurationer och DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="837a0-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="837a0-153">Läs mer om hur du konfigurerar LCM [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="837a0-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="837a0-154">För enkelhetens skull det här exemplet används den **PSDscAllowPlainTextPassword** att skicka lösenord i klartext till den **Credential** parametern.</span><span class="sxs-lookup"><span data-stu-id="837a0-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="837a0-155">Läs om hur skicka autentiseringsuppgifter säkrare [alternativ för autentiseringsuppgifter i konfigurationsdata](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="837a0-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="837a0-156">Du **måste** anger en **ConfigurationID** i den **inställningar** block med en metaconfiguration för en SMB-hämtningsserver, även om du endast hämtar resurser.</span><span class="sxs-lookup"><span data-stu-id="837a0-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

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

## <a name="acknowledgements"></a><span data-ttu-id="837a0-157">Erkännanden</span><span class="sxs-lookup"><span data-stu-id="837a0-157">Acknowledgements</span></span>

<span data-ttu-id="837a0-158">Särskilda tack till följande personer:</span><span class="sxs-lookup"><span data-stu-id="837a0-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="837a0-159">Mike F. Robbins vars inlägg om hur du använder SMB DSC hjälpte informera innehållet i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="837a0-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="837a0-160">Sin blogg var [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="837a0-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="837a0-161">Serge Nikalaichyk som skapats i **cNtfsAccessControl** modulen.</span><span class="sxs-lookup"><span data-stu-id="837a0-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="837a0-162">Källan för den här modulen är på [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="837a0-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="837a0-163">Se även</span><span class="sxs-lookup"><span data-stu-id="837a0-163">See also</span></span>

[<span data-ttu-id="837a0-164">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="837a0-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="837a0-165">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="837a0-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="837a0-166">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="837a0-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
