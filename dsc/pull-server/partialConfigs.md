---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: PowerShell Desired State Configuration partiella konfigurationer
ms.openlocfilehash: b2b17e35597707eb97ecdcea9dda4466deeab0cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683900"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell Desired State Configuration partiella konfigurationer

_Gäller för: Windows PowerShell 5.0 och senare._

I PowerShell 5.0 kan Desired State Configuration (DSC) konfigurationer som ska levereras i fragment och från flera källor. Den lokala Configuration Manager (LCM) på målnoden placerar fragmenten tillsammans innan du tillämpar dem som en enda konfiguration. Den här funktionen tillåter delning kontrollen över konfiguration mellan team eller enskilda användare. Till exempel om två eller flera team med utvecklare samarbetar med en tjänst, vilja de var skapa konfigurationer för att hantera sina ingår i tjänsten. Var och en av de här konfigurationerna kan hämtas från olika pull-servrar och de kan läggas till under de olika faserna i utvecklingen av. Partiella konfigurationer kan också olika individer eller team att styra olika aspekter av konfigurerat noder utan att behöva samordna redigering av ett enda configuration-dokument. Till exempel kanske ett team ansvarar för att distribuera en virtuell dator och operativsystem, medan ett annat team kan distribuera andra program och tjänster på den virtuella datorn. Varje team kan skapa egna konfigurationer, utan någon av dem är onödigt komplicerat med partiella konfigurationer.

Du kan använda partiella konfigurationer i push-läge, pull-läge eller en kombination av båda.

## <a name="partial-configurations-in-push-mode"></a>Partiella konfigurationer i push-läge

För att använda partiella konfigurationer i push-läge måste konfigurera du LCM på målnoden att ta emot partiella konfigurationer. Varje partiell konfiguration måste skickas till målet med hjälp av den `Publish-DSCConfiguration` cmdlet. Målnoden kombinerar sedan partiell konfiguration i en enda konfiguration och du kan tillämpa konfigurationen genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Konfigurera LCM för push-läge partiella konfigurationer

Om du vill konfigurera LCM för partiella konfigurationer i push-läget, skapar du en **DSCLocalConfigurationManager** med en **PartialConfiguration** block för varje partiell konfiguration. Läs mer om hur du konfigurerar LCM [Windows konfigurerar den lokala Konfigurationshanteraren](/powershell/dsc/metaConfig). I följande exempel visas en LCM-konfiguration som förväntar sig två partiella konfigurationer – en som distribuerar Operativsystemet och en som distribuerar och konfigurerar SharePoint.

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

Den **RefreshMode** för varje partiell konfiguration är inställd på ”Push”. Namnen på de **PartialConfiguration** block (i det här fallet ”ServiceAccountConfig” och ”SharePointConfig”) måste överensstämma exakt namnen på de konfigurationer som skickas till målnoden.

> [!Note]
> Namngivna för var och en **PartialConfiguration** block måste matcha namnet på konfigurationen som det anges i konfigurationsskript inte namnet på den MOF-fil som ska vara antingen namnet på målnoden eller `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publicera och starta push-läge partiella konfigurationer

Du sedan anropa [publicera-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) för varje konfiguration kan skicka mapparna som innehåller configuration-dokument som de **sökväg** parametrar. `Publish-DSCConfiguration`placerar configuration MOF-filer till målnoder. När du har publicerat båda konfigurationerna kan du anropa `Start-DSCConfiguration –UseExisting` på målnoden.

Exempel: Om du har skapat i följande konfiguration MOF-dokument på noden redigering:

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

Du skulle publicera och köra konfigurationerna som på följande sätt:

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> Användaren som kör den [publicera-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet måste ha administratörsbehörighet på målnoden.

## <a name="partial-configurations-in-pull-mode"></a>Partiella konfigurationer i pull-läge

Partiella konfigurationer kan hämtas från en eller flera pull-servrar (Mer information om pull-servrar finns i [Windows PowerShell Desired State Configuration Pull servrar](pullServer.md). Om du vill göra detta måste behöva du konfigurera LCM på målnoden att hämta partiella konfigurationer och namnge och hitta korrekt configuration-dokument på pull-servrar.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Konfigurera LCM för pull-nodkonfigurationer

Om du vill konfigurera MGM om du vill dra partiella konfigurationer från en pull-server du definierar hämtningsservern i antingen en **ConfigurationRepositoryWeb** (för en HTTP-pull-server) eller **ConfigurationRepositoryShare** () för en SMB-pullserver) block. Du kan sedan skapa **PartialConfiguration** block som refererar till den pull-servern med hjälp av den **ConfigurationSource** egenskapen. Du måste också skapa en **inställningar** block anger att LCM använder pull-läge och ange den **ConfigurationNames** eller **ConfigurationID** som hämtningsservern och mål noden används för att identifiera konfigurationerna. Följande meta-konfigurationen definierar en HTTP-pull-server med namnet CONTOSO PullSrv och två partiella konfigurationer som använder som pull-servern.

Mer information om hur du konfigurerar en LCM med hjälp av **ConfigurationNames**, se [konfigurera en hämtningsklient med konfigurationsnamn](pullClientConfigNames.md). Information om hur du konfigurerar en LCM med hjälp av **ConfigurationID**, se [konfigurera en hämtningsklient med konfigurations-ID](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Konfigurera LCM för pull-läge konfigurationer med konfigurationsnamn

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Konfigurera LCM för pull-läge konfigurationer med hjälp av ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

Du kan hämta partiella konfigurationer från mer än en pull-server – du behöver bara definiera varje pull-server och sedan referera till lämplig hämtningsservern i varje **PartialConfiguration** block.

När du har skapat meta-konfigurationen, måste du köra det för att skapa en konfigurationsdokumentet (en MOF-fil) och sedan anropa [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) konfigurera LCM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Namnge och placera configuration-dokument på hämtningsservern (ConfigurationNames)

Partiell konfigurationsdokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för hämtningsservern (vanligtvis `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Namnge configuration dokument på hämtningsservern i PowerShell 5.1

Om du hämtar bara en partiell konfiguration från en enskild pull-server kan configuration dokumentet ha vilket namn. Om du hämtar mer än en partiell konfiguration från en pull-server configuration dokumentet döpa antingen `<ConfigurationName>.mof`, där *ConfigurationName* är namnet på partiell konfiguration eller `<ConfigurationName>.<NodeName>.mof`, där *ConfigurationName* är namnet på partiell konfiguration och *nodnamn* är namnet på målnoden. Detta kan du pull konfigurationer från Azure Automation DSC-hämtningsservern.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Namnge configuration dokument på hämtningsservern i PowerShell 5.0

Av konfigurationsdokument måste ha namnet på följande sätt: `ConfigurationName.mof`, där *ConfigurationName* är namnet på partiell konfiguration. I vårt exempel ska configuration dokument namnges enligt följande:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Namnge och placera configuration-dokument på hämtningsservern (ConfigurationID)

Partiell konfigurationsdokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för hämtningsservern (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Av konfigurationsdokument måste ha namnet på följande sätt: `<ConfigurationName>.<ConfigurationID>.mof`, där _ConfigurationName_ är namnet på partiell konfiguration och _ConfigurationID_ är konfigurationen ID i den LCM på målnoden. I vårt exempel ska configuration dokument namnges enligt följande:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Kör partiella konfigurationer från en pull-server

När LCM på målnoden har konfigurerats och konfigurationen dokument har skapats och rätt namn på hämtningsservern målnoden hämtar partiella konfigurationer kan kombinera dem och tillämpa den resulterande konfigurationen enligt de vanliga intervall som anges av den **RefreshFrequencyMins** egenskapen för LCM. Om du vill framtvinga en uppdatering kan du anropa den [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdleten för att hämta konfigurationer, och sedan `Start-DSCConfiguration –UseExisting` att de ska appliceras.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Partiella konfigurationer i blandat sändnings- och mottagningsläge

Du kan även blanda push och pull-lägen för partiella konfigurationer. Det vill säga att du kan ha en partiell konfiguration som hämtas från en pull-server, medan en annan partiell konfiguration skickas. Ange uppdatering för varje partiell konfiguration enligt beskrivningen i föregående avsnitt. Till exempel följande meta-konfiguration beskriver det här exemplet med den `ServiceAccountConfig` partiell konfiguration i pull-läge och `SharePointConfig` partiell konfiguration i push-läget.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Blandade sändnings- och mottagningsläge med ConfigurationNames

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Blandade sändnings- och mottagningsläge med ConfigurationID

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

Observera att den **RefreshMode** anges i inställningsblocket är ”Pull”, men **RefreshMode** för den `SharePointConfig` partiell konfiguration är ”Push”.

Namnge och leta upp configuration MOF-filer enligt beskrivningen ovan för sina respektive uppdatering lägen.
Anropa `Publish-DSCConfiguration` att publicera den `SharePointConfig` partiell konfiguration och antingen vänta tills den `ServiceAccountConfig` konfigurationen som ska hämtas från hämtningsservern eller tvingar fram en uppdatering genom att anropa [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>ServiceAccountConfig partiellt exempelkonfiguration

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a>SharePointConfig partiellt exempelkonfiguration

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a>Se även

[Windows PowerShell Desired State Configuration Pull-servrar](pullServer.md)

[Windows som konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md)