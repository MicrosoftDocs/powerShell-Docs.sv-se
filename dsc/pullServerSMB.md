---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en DSC SMB-hämtningsserver
ms.openlocfilehash: e4e313746e95af86c5d17a8de0549451b1399b6c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="cd60d-103">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="cd60d-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="cd60d-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cd60d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd60d-105">Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="cd60d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="cd60d-106">Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="cd60d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="cd60d-107">En DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull-server är en dator som värd för SMB-filresurser som gör DSC-konfigurationsfiler och DSC resurser tillgängliga för målnoder när de noderna som ber om.</span><span class="sxs-lookup"><span data-stu-id="cd60d-107">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="cd60d-108">Om du vill använda en SMB-pull-server för DSC, behöver du:</span><span class="sxs-lookup"><span data-stu-id="cd60d-108">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="cd60d-109">Konfigurera en SMB-filresurs på en server som kör PowerShell 4.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="cd60d-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="cd60d-110">Konfigurera en klient som kör PowerShell 4.0 eller senare för att hämta från den SMB-resursen</span><span class="sxs-lookup"><span data-stu-id="cd60d-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="cd60d-111">Med xSmbShare resurs för att skapa en SMB-filresurs</span><span class="sxs-lookup"><span data-stu-id="cd60d-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="cd60d-112">Det finns ett antal sätt att konfigurera en SMB-filresurs, men vi ska titta på hur du kan göra detta med hjälp av DSC.</span><span class="sxs-lookup"><span data-stu-id="cd60d-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="cd60d-113">Installera xSmbShare resursen</span><span class="sxs-lookup"><span data-stu-id="cd60d-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="cd60d-114">Anropa den [installera modulen](https://technet.microsoft.com/library/dn807162.aspx) för att installera den **xSmbShare** modul.</span><span class="sxs-lookup"><span data-stu-id="cd60d-114">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="cd60d-115">**Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="cd60d-115">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="cd60d-116">Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="cd60d-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="cd60d-117">Den **xSmbShare** innehåller DSC-resursen **xSmbShare**, som kan användas för att skapa en SMB filresurs.</span><span class="sxs-lookup"><span data-stu-id="cd60d-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="cd60d-118">Skapa katalogen och filresursen</span><span class="sxs-lookup"><span data-stu-id="cd60d-118">Create the directory and file share</span></span>

<span data-ttu-id="cd60d-119">Följande konfiguration använder den [filen](fileResource.md) resurs för att skapa katalogen för resursen och **xSmbShare** resurs för att konfigurera SMB-resurs:</span><span class="sxs-lookup"><span data-stu-id="cd60d-119">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

    }

}
```

<span data-ttu-id="cd60d-120">Konfigurationen skapar katalogen `C:\DscSmbShare` om den inte redan finns, och sedan använder katalogen som en SMB filresurs.</span><span class="sxs-lookup"><span data-stu-id="cd60d-120">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="cd60d-121">**FullAccess** bör ges till något konto som behöver skriva till eller ta bort från filresursen och **läsåtkomst** ges till klientnoder som får konfigurationer och/eller DSC-resurser från (Detta beror på att resursen DSC körs som system-kontot som standard, så du själva datorn har åtkomst till resursen).</span><span class="sxs-lookup"><span data-stu-id="cd60d-121">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="cd60d-122">Ge behörighet till pull-klienten</span><span class="sxs-lookup"><span data-stu-id="cd60d-122">Give file system access to the pull client</span></span>

<span data-ttu-id="cd60d-123">Ger **läsåtkomst** noden till en klient kan noden för att få åtkomst till SMB-resursen, men inte till filer eller mappar i som delar.</span><span class="sxs-lookup"><span data-stu-id="cd60d-123">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="cd60d-124">Du måste uttryckligen bevilja klienten noder åtkomst till SMB-delade mappen och undermappar.</span><span class="sxs-lookup"><span data-stu-id="cd60d-124">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="cd60d-125">Vi kan göra detta med DSC genom att lägga till med hjälp av den **cNtfsPermissionEntry** resurs, som ingår i den [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modul.</span><span class="sxs-lookup"><span data-stu-id="cd60d-125">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="cd60d-126">Följande konfiguration lägger till en **cNtfsPermissionEntry** block som ger ReadAndExecute åtkomst till pull-klienten:</span><span class="sxs-lookup"><span data-stu-id="cd60d-126">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="cd60d-127">Placera konfigurationer och resurser</span><span class="sxs-lookup"><span data-stu-id="cd60d-127">Placing configurations and resources</span></span>

<span data-ttu-id="cd60d-128">Spara konfigurationen MOF-filer och/eller DSC-resurser som du vill att klientnoder att dra in SMB-delade mappen.</span><span class="sxs-lookup"><span data-stu-id="cd60d-128">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="cd60d-129">Alla configuration MOF-filen måste ha namnet _ConfigurationID_MOF, där _ConfigurationID_ är värdet för den **ConfigurationID** -egenskapen för nodens target MGM.</span><span class="sxs-lookup"><span data-stu-id="cd60d-129">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="cd60d-130">Mer information om hur du konfigurerar pull-klienter finns [installera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="cd60d-130">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="cd60d-131">**Obs:** måste du använda konfigurations-ID om du använder en SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="cd60d-131">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="cd60d-132">Konfigurationsnamn stöds inte för SMB.</span><span class="sxs-lookup"><span data-stu-id="cd60d-132">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="cd60d-133">Varje Resursmodul behöver zippade och namnet enligt de följande mönster `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="cd60d-133">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="cd60d-134">Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="cd60d-134">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="cd60d-135">Varje version av en modul måste finnas i en enda zip-fil.</span><span class="sxs-lookup"><span data-stu-id="cd60d-135">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="cd60d-136">Eftersom det finns endast en version av en resurs i formatet modulen lades till i WMF 5.0 med varje zip-filen stöds inte stöd för flera modulversioner i en katalog.</span><span class="sxs-lookup"><span data-stu-id="cd60d-136">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="cd60d-137">Detta innebär att innan du paketering in DSC resurs moduler för användning med pull-server måste du göra en mindre ändring i katalogstrukturen.</span><span class="sxs-lookup"><span data-stu-id="cd60d-137">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="cd60d-138">Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulen mappen}\{Modulversion} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="cd60d-138">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="cd60d-139">Innan paketering för pull-server bara ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulen mappen} \DscResources\{DSC resursmapp}\'.</span><span class="sxs-lookup"><span data-stu-id="cd60d-139">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="cd60d-140">Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i mappen SMB-resursen.</span><span class="sxs-lookup"><span data-stu-id="cd60d-140">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="cd60d-141">Skapa MOF-kontrollsumma</span><span class="sxs-lookup"><span data-stu-id="cd60d-141">Creating the MOF checksum</span></span>
<span data-ttu-id="cd60d-142">En konfiguration MOF-fil måste kombineras med en fil kontrollsummor så att en MGM på målnoden kan validera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="cd60d-142">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="cd60d-143">Om du vill skapa en kontrollsumma anropa den [ny DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cd60d-143">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="cd60d-144">Cmdlet tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns.</span><span class="sxs-lookup"><span data-stu-id="cd60d-144">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="cd60d-145">Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på konfigurationens mof-fil.</span><span class="sxs-lookup"><span data-stu-id="cd60d-145">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="cd60d-146">Om det finns mer än en konfiguration MOF-filer i den angivna mappen, skapas en kontrollsumma för varje konfiguration i mappen.</span><span class="sxs-lookup"><span data-stu-id="cd60d-146">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="cd60d-147">Filen kontrollsumma måste finnas i samma katalog som konfigurationsfilen MOF (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard), och har samma namn som den `.checksum` tillägg läggs.</span><span class="sxs-lookup"><span data-stu-id="cd60d-147">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="cd60d-148">**Obs**: Om du ändrar konfigurationen MOF-filen på något sätt, måste du också återskapa filen kontrollsumma.</span><span class="sxs-lookup"><span data-stu-id="cd60d-148">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="cd60d-149">Installera en pull-klient för SMB</span><span class="sxs-lookup"><span data-stu-id="cd60d-149">Setting up a pull client for SMB</span></span>

<span data-ttu-id="cd60d-150">Om du vill konfigurera en klient som tar emot konfigurationer och/eller resurser från en SMB-resurs måste du konfigurera klientens lokala Configuration Manager (MGM) med **ConfigurationRepositoryShare** och **ResourceRepositoryShare** block som anger resursen som du vill dra konfigurationer och DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="cd60d-150">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="cd60d-151">Mer information om hur du konfigurerar MGM finns [installera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="cd60d-151">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="cd60d-152">**Obs:** för enkelhetens skull det här exemplet används den **PSDscAllowPlainTextPassword** att skicka lösenord i klartext för den **autentiseringsuppgifter** parameter.</span><span class="sxs-lookup"><span data-stu-id="cd60d-152">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="cd60d-153">Information om autentiseringsuppgifter skickas säkrare finns [autentiseringsuppgifter alternativ i konfigurationsdata](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="cd60d-153">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="cd60d-154">**Obs:** måste du ange en **ConfigurationID** i den **inställningar** block med en metakonfigurationen för en SMB-pull-server, även om du endast hämtar resurser.</span><span class="sxs-lookup"><span data-stu-id="cd60d-154">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="cd60d-155">Erkännanden</span><span class="sxs-lookup"><span data-stu-id="cd60d-155">Acknowledgements</span></span>

<span data-ttu-id="cd60d-156">Särskild tack vare följande:</span><span class="sxs-lookup"><span data-stu-id="cd60d-156">Special thanks to the following:</span></span>

- <span data-ttu-id="cd60d-157">Mike F. Robbins vars inlägg om hur du använder SMB DSC hjälpt informera innehållet i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="cd60d-157">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="cd60d-158">Hans blogg är på [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="cd60d-158">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="cd60d-159">Serge Nikalaichyk som skapats av **cNtfsAccessControl** modul.</span><span class="sxs-lookup"><span data-stu-id="cd60d-159">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="cd60d-160">Källan för den här modulen är på https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="cd60d-160">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd60d-161">Se även</span><span class="sxs-lookup"><span data-stu-id="cd60d-161">See also</span></span>
- [<span data-ttu-id="cd60d-162">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="cd60d-162">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="cd60d-163">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="cd60d-163">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="cd60d-164">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="cd60d-164">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)