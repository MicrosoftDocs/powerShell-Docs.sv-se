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
# <a name="setting-up-a-dsc-smb-pull-server"></a>Konfigurera en DSC SMB-hämtningsserver

Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

En DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) -pull-server är en dator som är värd för SMB-filresurser som gör DSC-KONFIGURATIONSFILER och DSC-resurser tillgängliga för att rikta noder när dessa noder begär det.

Om du vill använda en SMB-pull-server för DSC måste du:

- Konfigurera en SMB-filresurs på en server som kör PowerShell 4,0 eller senare
- Konfigurera en klient som kör PowerShell 4,0 eller senare för att hämta från den SMB-resursen

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Använda xSmbShare-resursen för att skapa en SMB-filresurs

Det finns ett antal sätt att konfigurera en SMB-filresurs, men vi ska titta på hur du kan göra detta med hjälp av DSC.

### <a name="install-the-xsmbshare-resource"></a>Installera xSmbShare-resursen

Anropa cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) för att installera **xSmbShare** -modulen.

> [!NOTE]
> `Install-Module` ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0.
> **XSmbShare** innehåller DSC- **xSmbShare** som kan användas för att skapa en SMB-filresurs.

### <a name="create-the-directory-and-file-share"></a>Skapa katalogen och fil resursen

Följande konfiguration använder **fil** resursen för att skapa katalogen för resursen och **xSmbShare** -RESURSEN för att konfigurera SMB-resursen:

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

Konfigurationen skapar katalogen `C:\DscSmbShare` , om den inte redan finns, och använder den katalogen som en SMB-filresurs. **FullAccess** bör ges till alla konton som behöver skrivas till eller tas bort från fil resursen. **ReadAccess** måste ges till alla-klientsessioner som får konfigurationer och/eller DSC-resurser från resursen.

> [!NOTE]
> DSC körs som standard system kontot, så själva datorn måste ha åtkomst till resursen.

### <a name="give-file-system-access-to-the-pull-client"></a>Ge fil system åtkomst till pull-klienten

Genom att ge **ReadAccess** till en-klusternod kan noden få åtkomst till SMB-resursen, men inte till filer eller mappar i resursen. Du måste uttryckligen bevilja klient noderna åtkomst till mappen SMB-resurs och undermappar. Vi kan göra detta med DSC genom att lägga till med hjälp av **cNtfsPermissionEntry** -resursen, som finns i [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) -modulen.
Följande konfiguration lägger till ett **cNtfsPermissionEntry** -block som ger ReadAndExecute åtkomst till pull-klienten:

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

Spara eventuella konfigurations-MOF-filer och/eller DSC-resurser som du vill att klientsessioner ska hämta i mappen SMB-resurs.

En MOF-konfigurationsfil måste ha namnet *ConfigurationID* . MOF, där *ConfigurationID* är värdet för egenskapen **ConfigurationID** i nodens LCM. Mer information om hur du konfigurerar pull-klienter finns i [Konfigurera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).

> [!NOTE]
> Du måste använda konfigurations-ID: n om du använder en SMB-pull-server. Konfigurations namn stöds inte för SMB.

Varje resurs-modul måste vara zippad och namngiven enligt följande mönster `{Module Name}_{Module Version}.zip` . Till exempel skulle en modul med namnet xWebAdminstration med en modul version av 3.1.2.0 heta "xWebAdministration_3.2.1.0.zip". Varje version av en modul måste finnas i en enda zip-fil. Separata versioner av en modul i en zip-fil stöds inte.
Innan du packar upp DSC-resurspooler för användning med pull server måste du göra en liten ändring i katalog strukturen.

Standardformat för moduler som innehåller DSC-resurser i WMF 5,0 är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\` .

Innan du packar upp för pull-servern tar du bara bort `{Module version}` mappen så att sökvägen blir `{Module Folder}\DscResources\{DSC Resource Folder}\` . Med den här ändringen zip-mappen enligt beskrivningen ovan och placera dessa zip-filer i mappen SMB-resurs.

## <a name="creating-the-mof-checksum"></a>Skapa MOF-kontrollsumma

En konfigurations-MOF-fil måste kombineras med en kontroll Summa fil så att en LCM på en målnod kan verifiera konfigurationen. Om du vill skapa en kontroll Summa anropar du cmdleten [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) . Cmdleten tar en `Path` parameter som anger den mapp där MOF-konfigurationsfilen finns. Cmdleten skapar en kontroll Summa fil med namnet `ConfigurationMOFName.mof.checksum` , där `ConfigurationMOFName` är namnet på MOF-konfigurationsfilen. Om det finns fler än en konfigurations-MOF-fil i den angivna mappen skapas en kontroll summa för varje konfiguration i mappen.

Kontroll Summa filen måste finnas i samma katalog som MOF-filen för konfiguration ( `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard) och ha samma namn med `.checksum` tillägget bifogad.

> [!NOTE]
> Om du ändrar konfigurations-MOF-filen på valfritt sätt måste du också återskapa kontroll Summa filen.

## <a name="setting-up-a-pull-client-for-smb"></a>Konfigurera en pull-klient för SMB

Om du vill konfigurera en klient som hämtar konfigurationer och/eller resurser från en SMB-resurs konfigurerar du klientens lokala Configuration Manager (LCM) med **ConfigurationRepositoryShare** -och **ResourceRepositoryShare** -block som anger den resurs som ska hämta konfigurationer och DSC-resurser.

Mer information om hur du konfigurerar LCM finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigID.md).

> [!NOTE]
> För enkelhetens skull använder det här exemplet **PSDscAllowPlainTextPassword** för att skicka ett lösen ord i klartext till parametern **Credential** . Information om hur du skickar autentiseringsuppgifter säkrare finns i [alternativ för autentiseringsuppgifter i konfigurations data](../configurations/configDataCredentials.md). Du **måste** ange en **ConfigurationID** i **inställnings** blocket för en metaconfiguration för en SMB-pull-server, även om du bara ska hämta resurser.

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

## <a name="acknowledgements"></a>Erkännanden

Särskilt tack för följande individer:

- Mike F. Robbins, vars inlägg på att använda SMB för DSC, hjälpte att informera innehållet i det här avsnittet. Hans blogg är på [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, som skapade **cNtfsAccessControl** -modulen. Källan för den här modulen finns på [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Se även

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md)

[Tillämpa konfigurationer](enactingConfigurations.md)

[Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)
