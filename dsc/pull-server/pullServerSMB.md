---
ms.date: 04/11/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en DSC SMB-hämtningsserver
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404727"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Konfigurera en DSC SMB-hämtningsserver

Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

En DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) hämtningsservern är en dator som är värd för SMB-filresurser som gör DSC-konfigurationsfiler och DSC-resurser tillgängliga för målnoder när de noderna som ber om.

Om du vill använda en SMB-pullserver för DSC, behöver du:

- Konfigurera en SMB-filresurs på en server med PowerShell 4.0 eller senare
- Konfigurera en klient som kör PowerShell 4.0 eller senare för att hämta från den SMB-resursen

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Använda xSmbShare resursen för att skapa en SMB-filresurs

Det finns ett antal sätt att konfigurera en SMB-filresurs, men låt oss titta på hur du kan göra detta med hjälp av DSC.

### <a name="install-the-xsmbshare-resource"></a>Installera xSmbShare resursen

Anropa den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att installera den **xSmbShare** modulen.

> [!NOTE]
> `Install-Module` ingår i den **PowerShellGet** modulen, som ingår i PowerShell 5.0. Du kan ladda ned den **PowerShellGet** -modulen för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler förhandsversion](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> Den **xSmbShare** innehåller DSC-resurs **xSmbShare**, som kan användas för att skapa en SMB-filresurs.

### <a name="create-the-directory-and-file-share"></a>Skapa katalog och filresursen

Följande konfiguration använder den **filen** resursen för att skapa katalogen för resursen och **xSmbShare** resursen för att konfigurera SMB-resurs:

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
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

Konfigurationen skapar katalogen `C:\DscSmbShare`, om den inte redan finns, och sedan använder den katalogen som en SMB-filresurs. **FullAccess** ska ges till alla konton som krävs för att skriva till eller ta bort från filresursen. **Läsåtkomst** måste anges till klientnoder som få konfigurationer och/eller DSC-resurser från resursen.

> [!NOTE]
> DSC körs som system-kontot som standard så att själva datorn måste ha åtkomst till resursen.

### <a name="give-file-system-access-to-the-pull-client"></a>Ge behörighet till pull-klienten

Ge **läsåtkomst** till en klient noden kan noden för att få åtkomst till SMB-resursen, men inte till filer eller mappar i som delar. Du måste uttryckligen bevilja klienten noder åtkomst till SMB-delade mappen och undermappar. Vi kan göra detta med DSC genom att lägga till med hjälp av den **cNtfsPermissionEntry** resurs, som finns i den [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modulen. Lägger till följande konfiguration en **cNtfsPermissionEntry** block som beviljar ReadAndExecute åtkomst till pull-klienten:

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

## <a name="placing-configurations-and-resources"></a>Placera konfigurationer och resurser

Spara konfigurationen MOF-filer och/eller DSC-resurser som du vill att klientnoder att dra in den SMB-delade mappen.

Alla MOF-konfigurationsfilen måste ha namnet *ConfigurationID*.mof, där *ConfigurationID* är värdet för den **ConfigurationID** egenskapen för den målnoden MGM. Mer information om hur du konfigurerar pull-klienter finns i [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigID.md).

> [!NOTE]
> Du måste använda konfigurations-ID om du använder en SMB-pullserver. Konfigurationsnamn har inte stöd för SMB.

Varje Resursmodul måste zippade och med namnet enligt följande mönster `{Module Name}_{Module Version}.zip`. Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 ”xWebAdministration_3.2.1.0.zip”. Varje version av en modul måste finnas i en enda zip-fil. Olika versioner av en modul i en zip-fil stöds inte. Innan packa upp DSC-resurs-moduler för användning med pull-server måste du göra små ändringar i katalogstrukturen.

Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Innan du paketering för hämtningsservern helt enkelt ta bort den `{Module version}` mapp så blir sökvägen `{Module Folder}\DscResources\{DSC Resource Folder}\`. Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den SMB-delade mappen.

## <a name="creating-the-mof-checksum"></a>Skapa MOF-kontrollsumma

En MOF-konfigurationsfilen måste kopplas till en kontrollsumma-fil så att en LCM på målnoden verifiera konfigurationen.
Om du vill skapa en kontrollsumma, anropa den [New DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet. Cmdlet: en tar en `Path` parameter som anger den mapp där konfigurationen MOF finns. Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på mof-konfigurationsfilen.
Om det finns flera olika konfigurationer MOF-filer i en angiven mapp, skapas en kontrollsumma för varje konfiguration i mappen.

Filen kontrollsumma måste finnas i samma katalog som MOF-konfigurationsfilen (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard), och har samma namn som den `.checksum` tillägget sist.

> [!NOTE]
> Om du ändrar MOF-konfigurationsfilen på något sätt, måste du också återskapa filen kontrollsumma.

## <a name="setting-up-a-pull-client-for-smb"></a>Konfigurera en hämtningsklient för SMB

Om du vill konfigurera en klient som tar emot konfigurationer och/eller resurser från en SMB-resurs kan du konfigurera klientens lokala Configuration Manager (LCM) med **ConfigurationRepositoryShare** och **ResourceRepositoryShare** block som anger den resurs som ska hämta konfigurationer och DSC-resurser.

Läs mer om hur du konfigurerar LCM [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigID.md).

> [!NOTE]
> För enkelhetens skull det här exemplet används den **PSDscAllowPlainTextPassword** att skicka lösenord i klartext till den **Credential** parametern. Läs om hur skicka autentiseringsuppgifter säkrare [alternativ för autentiseringsuppgifter i konfigurationsdata](../configurations/configDataCredentials.md).
>
> Du **måste** anger en **ConfigurationID** i den **inställningar** block med en metaconfiguration för en SMB-hämtningsserver, även om du endast hämtar resurser.

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

## <a name="acknowledgements"></a>Erkännanden

Särskilda tack till följande personer:

- Mike F. Robbins vars inlägg om hur du använder SMB DSC hjälpte informera innehållet i det här avsnittet. Sin blogg var [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk som skapats i **cNtfsAccessControl** modulen. Källan för den här modulen är på [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Se även

[Windows PowerShell Desired State Configuration-översikt](../overview/overview.md)

[Tillämpa konfigurationer](enactingConfigurations.md)

[Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)
