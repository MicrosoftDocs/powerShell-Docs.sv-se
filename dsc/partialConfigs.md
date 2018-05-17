---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Partiell PowerShell Desired State Configuration-konfigurationer
ms.openlocfilehash: e6d80b065ad9e68517d2952b7643e4c611d82a0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a>Partiell PowerShell Desired State Configuration-konfigurationer

>Gäller för: Windows PowerShell 5.0 och senare.

I PowerShell 5.0 kan önskad tillstånd Configuration (DSC) konfigurationer som ska levereras i fragment och från flera källor. Den lokala Configuration Manager (MGM) på målnoden sätter ihop fragment innan du tillämpar dem som en enda konfiguration. Den här funktionen tillåter delning kontroll över konfiguration mellan olika team eller enskilda användare.
Till exempel om två eller flera grupper med utvecklare samarbeta på en tjänst kan kanske de var vill skapa konfigurationer för att hantera sin del av tjänsten. Var och en av de här konfigurationerna kan hämtas från olika pull-servrar och de gick att lägga till under de olika faserna i utvecklingen av. Partiell konfigurationer kan också olika personer eller grupper för att styra olika aspekter av hur du konfigurerar noder utan att behöva koordinera redigering av ett enda dokument. Ett team kan vara ansvariga för att distribuera en virtuell dator och operativsystem, medan ett annat team kan distribuera andra program och tjänster på den virtuella datorn. Varje team kan skapa egna konfigurationer, utan någon av dem att i onödan komplicerade med partiellt konfigurationer.

Du kan använda partiella konfigurationer i push-läge, pull-läge eller en kombination av båda.

## <a name="partial-configurations-in-push-mode"></a>Partiell konfigurationer i push-läge
Om du vill använda delvis konfigurationer i push-läge, konfigurerar du MGM på målnoden för att ta emot de partiella konfigurationerna. Varje partiella konfiguration måste skickas till målet med hjälp av cmdleten publicera DSCConfiguration. Målnoden kombinerar sedan partiella konfigurationen i konfigurationen för en och du kan använda konfigurationen genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a>Konfigurera MGM för push-läge partiella konfigurationer
Om du vill konfigurera MGM för partiellt konfigurationer i push-läge, som du skapar en **DSCLocalConfigurationManager** konfiguration med en **PartialConfiguration** block för varje partiella konfiguration. Mer information om hur du konfigurerar MGM finns [Windows konfigurera den lokala Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx).
I följande exempel visas en MGM konfiguration som förväntar sig konfigurationer av två delar, en som distribuerar Operativsystemet och en som distribuerar och konfigurerar SharePoint.

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

Den **RefreshMode** för varje partiella konfiguration har värdet ”Push”. Namnen på de **PartialConfiguration** block (i det här fallet ”ServiceAccountConfig” och ”SharePointConfig”) måste matcha exakt namnen på de konfigurationer som pushas till målnoden.

>**Obs:** namngivna för varje **PartialConfiguration** block måste matcha det faktiska namnet på konfigurationen som den har angetts i konfigurationsskript inte namnet på MOF-filen som ska vara antingen namnet på den målnoden eller `localhost`.

### <a name="publishing-and-starting-push-mode-partial-configurations"></a>Publicera och starta partiella konfigurationer för push-läge

Sedan anropar [publicera DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) för varje konfiguration kan skicka mapparna som innehåller configuration-dokument som den **sökväg** parametrar. `Publish-DSCConfiguration`placerar configuration MOF-filer till målnoder. När du har publicerat båda konfigurationerna kan du anropa `Start-DSCConfiguration –UseExisting` på målnoden.

Till exempel om du har sammanställt följande konfiguration MOF dokument på noden redigering:

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


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

Du skulle publicera och köra konfigurationerna på följande sätt:

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

>**Obs:** användaren som kör den [publicera DSCConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet måste ha administratörsbehörighet på målnoden.

## <a name="partial-configurations-in-pull-mode"></a>Partiell konfigurationer i pull-läge

Partiell konfigurationer som kan hämtas från en eller flera pull-servrar (Mer information om pull-servrar finns [Windows PowerShell önskad tillstånd Pull Konfigurationsservrar](pullServer.md). Du måste konfigurera MGM på målnoden till pull-konfigurationer som delar ett namn och hitta korrekt configuration-dokument på pull-servrar för att göra detta.

### <a name="configuring-the-lcm-for-pull-node-configurations"></a>Konfigurera MGM för pull-nodkonfigurationer

Om du vill konfigurera MGM om du vill dra partiella konfigurationer från en pull-server du definierar pull-server i antingen en **ConfigurationRepositoryWeb** (för en HTTP-pull-server) eller **ConfigurationRepositoryShare** () för en SMB-pull-server) block. Skapa sedan **PartialConfiguration** block som refererar till den pull-servern med hjälp av den **ConfigurationSource** egenskapen. Du måste också skapa en **inställningar** block vill ange att MGM om du använder pull-läge och ange den **ConfigurationNames** eller **ConfigurationID** som pull-server och mål nod Använd för att identifiera konfigurationer. Följande meta-konfiguration definierar en HTTP-pull-server med namnet CONTOSO PullSrv och två delar konfigurationer som använder som pull-server.

Mer information om hur du konfigurerar MGM med **ConfigurationNames**, se [ställa in en pull-klient som använder konfigurationsnamn](pullClientConfigNames.md).
Information om hur du konfigurerar MGM med **ConfigurationID**, se [installera en pull-klient med hjälp av konfigurations-ID](pullClientConfigID.md).

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a>Konfigurera MGM för pull-läge konfigurationer med konfigurationsnamn

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a>Konfigurera MGM för pull-läge konfigurationer med hjälp av ConfigurationID

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

Du kan dra partiella konfigurationer från mer än en pull-server – du behöver bara definiera varje pull-server och referera till lämplig pull-server i varje **PartialConfiguration** block.

När du har skapat meta-konfigurationen måste du köra det för att skapa ett configuration-dokument (en MOF-fil) och sedan anropa [Set DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) att konfigurera MGM.

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a>Namnge och placera configuration-dokument på hämtningsservern (ConfigurationNames)

Partiell configuration-dokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för pull-server (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`).

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a>Namnge configuration dokument på hämtningsservern i PowerShell 5.1

Om du hämtar bara en partiell konfiguration från en enskild hämtningsservern kan configuration dokumentet ha vilket namn.
Om du hämtar mer än en partiell konfiguration från en pull-server configuration dokumentet kan namnges antingen `<ConfigurationName>.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen eller `<ConfigurationName>.<NodeName>.mof`, där  _ConfigurationName_ är namnet på den partiella konfigurationen och _nodnamn_ är namnet på målnoden.
Detta gör att du kan pull konfigurationer från hämtningsservern i Azure Automation DSC.


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a>Namnge configuration dokument på hämtningsservern i PowerShell 5.0

Av konfigurationsdokument måste ha namnet på följande sätt: `ConfigurationName.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen. I vårt exempel bör konfigurationsdokument vara namnet på följande sätt:

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a>Namnge och placera configuration-dokument på hämtningsservern (ConfigurationID)

Partiell configuration-dokument måste placeras i den angivna mappen i den **ConfigurationPath** i den `web.config` -filen för pull-server (vanligtvis `C:\Program Files\WindowsPowerShell\DscService\Configuration`). Av konfigurationsdokument måste ha namnet på följande sätt: _ConfigurationName_. _ConfigurationID_`.mof`, där _ConfigurationName_ är namnet på den partiella konfigurationen och _ConfigurationID_ definieras konfigurations-ID i MGM på måldatorn noden. I vårt exempel bör konfigurationsdokument vara namnet på följande sätt:

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a>Kör delvis konfigurationer från en pull-server

När MGM på målnoden har konfigurerats och konfigurationen dokument har skapats och korrekt med namnet på hämtningsservern målnoden hämtar partiella konfigurationer, kombinera dem och tillämpa den resulterande konfigurationen regelbundet intervall som anges av den **RefreshFrequencyMins** -egenskapen för MGM. Om du vill framtvinga en uppdatering kan du anropa den [uppdatering DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet hämtar konfigurationerna och sedan `Start-DSCConfiguration –UseExisting` tillämpa dem.


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a>Partiell konfigurationer i blandat läge för sändning och mottagning

Du kan också blanda push och pull-lägen för partiellt konfigurationer. Det vill säga kan du ha en partiell konfiguration som hämtas från en pull-server, medan en annan partiell konfiguration är nedtryckt. Ange uppdatera-läge för varje partiella konfiguration enligt beskrivningen i föregående avsnitt.
Till exempel följande meta-konfiguration beskriver det här exemplet med den `ServiceAccountConfig` partiella konfigurationen i pull-läge och `SharePointConfig` partiella konfigurationen i push-läge.

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a>Blandat sändnings- och mottagningsläge med ConfigurationNames

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a>Blandat sändnings- och mottagningsläge med ConfigurationID

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

Observera att den **RefreshMode** anges i inställningsblocket är ”dra”, men **RefreshMode** för den `SharePointConfig` partiella konfigurationen är ”Push”.

Namn och hitta MOF konfigurationsfiler som beskrivs ovan för deras respektive uppdatering lägen. Anropa **publicera DSCConfiguration** att publicera den `SharePointConfig` partiella konfiguration och antingen vänta tills den `ServiceAccountConfig` konfigurationen som ska hämtas från servern pull eller framtvinga en uppdatering genom att anropa [ Uppdatera DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).

## <a name="example-serviceaccountconfig-partial-configuration"></a>ServiceAccountConfig partiell exempelkonfiguration

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
## <a name="example-sharepointconfig-partial-configuration"></a>SharePointConfig partiell exempelkonfiguration
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
##<a name="see-also"></a>Se även

**Begrepp**
[Windows PowerShell önskad Tillståndskonfiguration Pull-servrar](pullServer.md)

[Windows konfigurera den lokala Configuration Manager](https://technet.microsoft.com/library/mt421188.aspx)