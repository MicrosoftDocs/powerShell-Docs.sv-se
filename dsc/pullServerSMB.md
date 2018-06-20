---
ms.date: 04/11/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en DSC SMB-hämtningsserver
ms.openlocfilehash: 92c03c99afd612fa2b5475e8c26991ff080584e9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189677"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Konfigurera en DSC SMB-hämtningsserver

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

En DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull-server är en dator som värd för SMB-filresurser som gör DSC-konfigurationsfiler och DSC resurser tillgängliga för målnoder när de noderna som ber om.

Om du vill använda en SMB-pull-server för DSC, behöver du:
- Konfigurera en SMB-filresurs på en server som kör PowerShell 4.0 eller senare
- Konfigurera en klient som kör PowerShell 4.0 eller senare för att hämta från den SMB-resursen

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Med xSmbShare resurs för att skapa en SMB-filresurs

Det finns ett antal sätt att konfigurera en SMB-filresurs, men vi ska titta på hur du kan göra detta med hjälp av DSC.

### <a name="install-the-xsmbshare-resource"></a>Installera xSmbShare resursen

Anropa den [installera modulen](https://technet.microsoft.com/library/dn807162.aspx) för att installera den **xSmbShare** modul.
>**Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0. Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186). Den **xSmbShare** innehåller DSC-resursen **xSmbShare**, som kan användas för att skapa en SMB filresurs.

### <a name="create-the-directory-and-file-share"></a>Skapa katalogen och filresursen

Följande konfiguration använder den [filen](fileResource.md) resurs för att skapa katalogen för resursen och **xSmbShare** resurs för att konfigurera SMB-resurs:

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

Konfigurationen skapar katalogen `C:\DscSmbShare` om den inte redan finns, och sedan använder katalogen som en SMB filresurs. **FullAccess** bör ges till något konto som behöver skriva till eller ta bort från filresursen och **läsåtkomst** ges till klientnoder som får konfigurationer och/eller DSC-resurser från (Detta beror på att resursen DSC körs som system-kontot som standard, så du själva datorn har åtkomst till resursen).


### <a name="give-file-system-access-to-the-pull-client"></a>Ge behörighet till pull-klienten

Ger **läsåtkomst** noden till en klient kan noden för att få åtkomst till SMB-resursen, men inte till filer eller mappar i som delar. Du måste uttryckligen bevilja klienten noder åtkomst till SMB-delade mappen och undermappar. Vi kan göra detta med DSC genom att lägga till med hjälp av den **cNtfsPermissionEntry** resurs, som ingår i den [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) modul. Följande konfiguration lägger till en **cNtfsPermissionEntry** block som ger ReadAndExecute åtkomst till pull-klienten:

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

## <a name="placing-configurations-and-resources"></a>Placera konfigurationer och resurser

Spara konfigurationen MOF-filer och/eller DSC-resurser som du vill att klientnoder att dra in SMB-delade mappen.

Alla configuration MOF-filen måste ha namnet _ConfigurationID_MOF, där _ConfigurationID_ är värdet för den **ConfigurationID** -egenskapen för nodens target MGM. Mer information om hur du konfigurerar pull-klienter finns [installera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).

>**Obs:** måste du använda konfigurations-ID om du använder en SMB-pull-server. Konfigurationsnamn stöds inte för SMB.

Varje Resursmodul behöver zippade och namnet enligt de följande mönster `{Module Name}_{Module Version}.zip`. Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 'xWebAdministration_3.2.1.0.zip'. Varje version av en modul måste finnas i en enda zip-fil. Eftersom det finns endast en version av en resurs i formatet modulen lades till i WMF 5.0 med varje zip-filen stöds inte stöd för flera modulversioner i en katalog. Detta innebär att innan du paketering in DSC resurs moduler för användning med pull-server måste du göra en mindre ändring i katalogstrukturen. Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulen mappen}\{Modulversion} \DscResources\{DSC resursmapp}\'. Innan paketering för pull-server bara ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulen mappen} \DscResources\{DSC resursmapp}\'. Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i mappen SMB-resursen.

## <a name="creating-the-mof-checksum"></a>Skapa MOF-kontrollsumma
En konfiguration MOF-fil måste kombineras med en fil kontrollsummor så att en MGM på målnoden kan validera konfigurationen.
Om du vill skapa en kontrollsumma anropa den [ny DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet. Cmdlet tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns. Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på konfigurationens mof-fil.
Om det finns mer än en konfiguration MOF-filer i den angivna mappen, skapas en kontrollsumma för varje konfiguration i mappen.

Filen kontrollsumma måste finnas i samma katalog som konfigurationsfilen MOF (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` som standard), och har samma namn som den `.checksum` tillägg läggs.

>**Obs**: Om du ändrar konfigurationen MOF-filen på något sätt, måste du också återskapa filen kontrollsumma.

## <a name="setting-up-a-pull-client-for-smb"></a>Installera en pull-klient för SMB

Om du vill konfigurera en klient som tar emot konfigurationer och/eller resurser från en SMB-resurs måste du konfigurera klientens lokala Configuration Manager (MGM) med **ConfigurationRepositoryShare** och **ResourceRepositoryShare** block som anger resursen som du vill dra konfigurationer och DSC-resurser.

Mer information om hur du konfigurerar MGM finns [installera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).

>**Obs:** för enkelhetens skull det här exemplet används den **PSDscAllowPlainTextPassword** att skicka lösenord i klartext för den **autentiseringsuppgifter** parameter. Information om autentiseringsuppgifter skickas säkrare finns [autentiseringsuppgifter alternativ i konfigurationsdata](configDataCredentials.md).

>**Obs:** måste du ange en **ConfigurationID** i den **inställningar** block med en metakonfigurationen för en SMB-pull-server, även om du endast hämtar resurser.

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

Särskild tack vare följande:

- Mike F. Robbins vars inlägg om hur du använder SMB DSC hjälpt informera innehållet i det här avsnittet. Hans blogg är på [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk som skapats av **cNtfsAccessControl** modul. Källan för den här modulen är på https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Se även
- [Windows PowerShell Desired State Configuration-översikt](overview.md)
- [Tillämpa konfigurationer](enactingConfigurations.md)
- [Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)