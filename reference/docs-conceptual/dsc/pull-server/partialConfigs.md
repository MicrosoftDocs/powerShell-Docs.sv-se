---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: PowerShell Desired State Configuration, delvis konfigurationer
ms.openlocfilehash: 842acad221d468ca5e4c9e660f0205c567bcc220
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500776"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>PowerShell Desired State Configuration, delvis konfigurationer

_Gäller för: Windows PowerShell 5,0 och senare._

I PowerShell 5,0 tillåter önskad tillstånds konfiguration (DSC) konfigurationer att levereras i fragment och från flera källor. Den lokala Configuration Manager (LCM) på målnoden placerar fragmenten tillsammans innan de tillämpas som en enda konfiguration. Den här funktionen gör det möjligt att dela kontroll över konfigurationen mellan team eller individer. Om två eller flera team utvecklare samarbetar med en tjänst kan de exempelvis var och en vilja skapa konfigurationer för att hantera sin del av tjänsten. Var och en av dessa konfigurationer kan hämtas från olika hämtnings servrar och de kan läggas till i olika utvecklings steg. Partiella konfigurationer gör det också möjligt för olika individer eller team att styra olika aspekter av konfigurering av noder utan att behöva koordinera redigeringen av ett enda konfigurations dokument. Ett team kan till exempel vara ansvarigt för att distribuera en virtuell dator och ett operativ system, medan ett annat team kan distribuera andra program och tjänster på den virtuella datorn. Med del konfigurationer kan varje team skapa en egen konfiguration, utan att något av dem är onödigt komplicerat.

Du kan använda partiella konfigurationer i push-läge, pull-läge eller en kombination av de två.

## <a name="partial-configurations-in-push-mode"></a>Partiella konfigurationer i push-läge

Om du vill använda partiella konfigurationer i push-läge konfigurerar du LCM på målnoden för att ta emot del konfigurationerna. Varje del konfiguration måste flyttas till målet med hjälp av `Publish-DSCConfiguration`-cmdleten. Målnoden kombinerar sedan den partiella konfigurationen till en enda konfiguration och du kan tillämpa konfigurationen genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Konfigurera LCM för ofullständiga konfigurationer i push-läge

Om du vill konfigurera LCM för partiella konfigurationer i push-läge, skapar du en **DSCLocalConfigurationManager** -konfiguration med ett **PartialConfiguration** -block för varje del konfiguration. Mer information om hur du konfigurerar LCM finns i [Windows konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md). I följande exempel visas en LCM-konfiguration som förväntar sig två delar av konfigurationer – en som distribuerar operativ systemet och en som distribuerar och konfigurerar SharePoint.

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

**RefreshMode** för varje delvis konfiguration anges till "push". Namnen på **PartialConfiguration** -blocken (i det här fallet "ServiceAccountConfig" och "SharePointConfig") måste matcha exakt namnen på de konfigurationer som flyttas till målnoden.

> [!Note]
> Namnet på varje **PartialConfiguration** -block måste matcha det faktiska namnet på konfigurationen som det anges i konfigurations skriptet, inte namnet på MOF-filen, som antingen ska vara namnet på målnoden eller `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publicera och starta partiella konfigurationer i push-läge

Sedan anropar du [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) för varje konfiguration och skickar mapparna som innehåller konfigurations dokumenten som **Sök vägs** parametrar. `Publish-DSCConfiguration`placerar MOF-filerna för konfiguration på målnoden. När du har publicerat båda konfigurationerna kan du anropa `Start-DSCConfiguration –UseExisting` på målnoden.

Om du till exempel har kompilerat följande konfiguration MOF-dokument på noden redigering:

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

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

Du publicerar och kör konfigurationerna på följande sätt:

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
> Användaren som kör cmdleten [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) måste ha administratörs behörighet på målnoden.

## <a name="partial-configurations-in-pull-mode"></a>Partiella konfigurationer i pull-läge

Partiella konfigurationer kan hämtas från en eller flera hämtnings servrar (mer information om hämtnings servrar finns i [Windows PowerShell Desired State Configuration pull-servrar](pullServer.md). Om du vill göra detta måste du konfigurera LCM på målnoden för att hämta de partiella konfigurationerna och namnge och hitta de konfigurations dokument som är korrekt på pull-servrarna.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Konfigurera LCM för pull-nodkonfigurationer

Om du vill konfigurera LCM för att hämta partiella konfigurationer från en pull-server definierar du hämtnings servern i antingen en **ConfigurationRepositoryWeb** (för en http-pull-server) eller **CONFIGURATIONREPOSITORYSHARE** (för SMB pull server)-block. Sedan skapar du **PartialConfiguration** -block som refererar till pull-servern med hjälp av egenskapen **ConfigurationSource** . Du måste också skapa ett **inställnings** block för att ange att LCM använder pull-läge och för att ange **ConfigurationNames** eller **ConfigurationID** som pull-servern och mål-noden använder för att identifiera konfigurationerna. Följande meta-konfiguration definierar en HTTP pull-server med namnet CONTOSO-PullSrv och två ofullständiga konfigurationer som använder den hämtnings servern.

Mer information om hur du konfigurerar LCM med hjälp av **ConfigurationNames**finns i [Konfigurera en pull-klient med hjälp av konfigurations namn](pullClientConfigNames.md). Information om hur du konfigurerar LCM med hjälp av **ConfigurationID**finns i [Konfigurera en pull-klient med konfigurations-ID](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Konfigurera LCM för pull-läge-konfigurationer med hjälp av konfigurations namn

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Konfigurera LCM för pull-läge-konfigurationer med ConfigurationID

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

Du kan hämta delvis konfigurationer från fler än en pull-server – du behöver bara definiera varje pull-server och sedan referera till lämplig pull-server i varje **PartialConfiguration** -block.

När du har skapat meta-konfigurationen måste du köra den för att skapa ett konfigurations dokument (en MOF-fil) och sedan anropa [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) för att konfigurera LCM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Namnge och placera konfigurations dokumenten på pull-servern (ConfigurationNames)

De partiella konfigurations dokumenten måste placeras i den mapp som anges som **ConfigurationPath** i `web.config`-filen för pull-servern (vanligt vis `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Namnge konfigurations dokument på hämtnings servern i PowerShell 5,1

Om du bara hämtar en delvis konfiguration från en enskild hämtnings Server kan konfigurations dokumentet ha ett namn. Om du hämtar fler än en partiell konfiguration från en pull-server, kan konfigurations dokumentet antingen namnges `<ConfigurationName>.mof`, där *ConfigurationName* är namnet på den partiella konfigurationen eller `<ConfigurationName>.<NodeName>.mof`, där *ConfigurationName* är namnet på den partiella konfigurationen och *nodnamn* är namnet på mål-noden. På så sätt kan du hämta konfigurationer från Azure Automation DSC-pull-server.

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Namnge konfigurations dokument på hämtnings servern i PowerShell 5,0

Konfigurations dokumenten måste ha följande namn: `ConfigurationName.mof`, där *ConfigurationName* är namnet på den partiella konfigurationen. I vårt exempel ska konfigurations dokumenten namnges enligt följande:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Namnge och placera konfigurations dokumenten på pull-servern (ConfigurationID)

De partiella konfigurations dokumenten måste placeras i den mapp som anges som **ConfigurationPath** i `web.config`-filen för pull-servern (vanligt vis `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Konfigurations dokumenten måste namnges enligt följande: `<ConfigurationName>.<ConfigurationID>.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen och _ConfigurationID_ är det konfigurations-ID som definierats i LCM på målnoden. I vårt exempel ska konfigurations dokumenten namnges enligt följande:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a>Köra partiella konfigurationer från en hämtnings Server

När LCM på mål noden har kon figurer ATS och konfigurations dokumenten har skapats och på rätt sätt har namngetts på hämtnings servern, hämtar målnoden de ofullständiga konfigurationerna, kombinerar dem och tillämpar den resulterande konfigurationen med jämna mellanrum som anges i egenskapen **RefreshFrequencyMins** för LCM. Om du vill framtvinga en uppdatering kan du anropa cmdleten [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) för att hämta konfigurationerna och sedan `Start-DSCConfiguration –UseExisting` tillämpa dem.

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Partiella konfigurationer i blandade push-och pull-lägen

Du kan också blanda push-och pull-lägen för partiella konfigurationer. Det innebär att du kan ha en delvis konfiguration som hämtas från en pull-server, medan en annan del av konfigurationen skickas. Ange uppdaterings läget för varje partiell konfiguration enligt beskrivningen i föregående avsnitt. Följande meta-konfiguration beskriver till exempel samma exempel, med `ServiceAccountConfig` partiell konfiguration i pull-läge och `SharePointConfig` partiell konfiguration i push-läge.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Blandade push-och pull-lägen med ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Blandade push-och pull-lägen med ConfigurationID

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

Observera att **RefreshMode** som anges i inställnings blocket är "pull", men **RefreshMode** för `SharePointConfig` partiella konfigurationen är "push".

Namnge och leta upp MOF-filerna för konfigurationen enligt beskrivningen ovan för respektive uppdaterings läge.
Anropa `Publish-DSCConfiguration` för att publicera `SharePointConfig` partiella konfigurationen och antingen väntar på att `ServiceAccountConfig` konfigurationen ska hämtas från hämtnings servern eller framtvinga en uppdatering genom att anropa [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).

## <a name="example-serviceaccountconfig-partial-configuration"></a>Exempel ServiceAccountConfig delvis konfiguration

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

## <a name="example-sharepointconfig-partial-configuration"></a>Exempel SharePointConfig delvis konfiguration

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

[Hämtnings servrar för önskad tillstånds konfiguration i Windows PowerShell](pullServer.md)

[Windows konfigurerar den lokala Configuration Manager](../managing-nodes/metaConfig.md)
