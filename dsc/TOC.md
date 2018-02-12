# [Översikt](overview.md)

## [Desired State Configuration-översikt för beslutsfattare](decisionMaker.md)

## [Desired State Configuration-översikt för tekniker](DscForEngineers.md)

## [DSC-snabbstart](quickStart.md)

# [Konfigurationer](configurations.md)

## [Tillämpa konfigurationer](enactingConfigurations.md)

## [Avgränsa konfigurations- och miljödata](separatingEnvData.md)

## [Använd resurser med flera versioner](sxsResource.md)

## [Kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md)

## [Ange beroenden mellan noder](crossNodeDependencies.md)

## [Konfigurationsdata](configData.md)

### [Alternativ för autentiseringsuppgifter i konfigurationsdata](configDataCredentials.md)

## [Kapslingskonfigurationer](compositeConfigs.md)

## [Säkra MOF-konfigurationsfilen](secureMOF.md)

## [Partiella konfigurationer](partialConfigs.md)

## [Skrivhjälp för DSC-konfigurationer](configHelp.md)

## [Konfigurera en virtuell dator vid första uppstart med hjälp av DSC](bootstrapDsc.md)

### [DSCAutomationHostEnabled-registernyckel](DSCAutomationHostEnabled.md)

# [Resurser](resources.md)

## [Inbyggda resurser](builtInResource.md)

### [Arkivera resursen](archiveResource.md)

### [Miljöresurs](environmentResource.md)

### [Filresurs](fileResource.md)

### [Gruppresurs](groupResource.md)

### [GroupSet-resurs](groupSetResource.md)

### [Loggresurs](logResource.md)

### [Paketresurs](packageResource.md)

### [ProcessSet-resurs](processSetResource.md)

### [Registerresurser](registryResource.md)

### [Skriptresurs](scriptResource.md)

### [Tjänstresurs](serviceResource.md)

### [ServiceSet-resurs](serviceSetResource.md)

### [Användarresurs](userResource.md)

### [WaitForAllResource](waitForAllResource.md)

### [WaitForAnyResource](waitForAnyResource.md)

### [WaitForSomeResource](waitForSomeResource.md)

### [WindowsFeature-resurs](windowsfeatureResource.md)

### [WindowsFeatureSet-resurs](windowsFeatureSetResource.md)

### [WindowsOptionalFeature-resurs](windowsOptionalFeatureResource.md)

### [WindowsOptionalFeatureSet-resurs](windowsOptionalFeatureSetResource.md)

### [WindowsPackageCab-resurs](windowsPackageCabResource.md)

### [WindowsProcess-resurs](windowsProcessResource.md)

## [Redigera anpassade resurser](authoringResource.md) 

### [MOF-baserade anpassade resurser](authoringResourceMOF.md)

#### [MOF-baserad resurs i C#](authoringResourceMofCS.md)

### [MOF-baserade anpassade resurser](authoringResourceClass.md)

### [Sammansatta resurser](authoringResourceComposite.md)

### [Skapa en enskild instans DSC-resurs (metodtips)](singleInstance.md)

### [Checklista för resursskapande](resourceAuthoringChecklist.md)

## [Felsök DSC-resurser](debugResource.md)

## [Anropa DSC-resursmetoder direkt](directCallResource.md)

# Lokal konfigurationshanterare

## [Konfigurera den lokala konfigurationshanteraren (LCM)](metaConfig.md)

## [Konfigurera LCM i PowerShell 4.0](metaConfig4.md)

# DSC-pullmodellen

## [DSC-pulltjänsten](pullServer.md)

## [Konfigurera en DSC SMB-pullserver](pullServerSMB.md)

## [Konfigurera en pullklient](pullClient.md)

### [Konfigurera en pullklient med konfigurationsnamn](pullClientConfigNames.md)

### [Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)

## [Använd en DSC-rapportserver](reportServer.md)

## [Metodtips för pullservern](secureServer.md)

# [DSC-exempel](dscExamples.md)

## [Skapa en CI/CD-pipeline med DSC, Pester och Visual Studio Team Services](dscCiCd.md)

## [Avgränsa konfigurations- och miljödata](separatingEnvData.md)

# [Felsök DSC](troubleshooting.md)

# [Använd DSC på Nano Server](nanoDsc.md)

# DSC på Linux

## [Kom igång med DSC för Linux](lnxGettingStarted.md)

## [Inbyggda resurser för Linux](lnxBuiltInResources.md)

### [nxArchive-resurs](lnxArchiveResource.md)

### [nxEnvironment-resurs](lnxEnvironmentResource.md)

### [nxFile-resurs](lnxFileResource.md)

### [nxFileLine-resurs](lnxFileLineResource.md)

### [nxGroup-resurs](lnxGroupResource.md)

### [nxPackage-resurs](lnxPackageResource.md)

### [nxService-resurs](lnxServiceResource.md)

### [nxSshAuthorizedKeys-resurs](lnxSshAuthorizedKeysResource.md)

### [nxUser-resurs](lnxUserResource.md)

# [Använd DSC på Microsoft Azure](azureDsc.md)

# DSC MOF-referens

## [MSFT_DSCLocalConfigurationManager-klass](msft-dsclocalconfigurationmanager.md)

### [ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass](msft-dsclocalconfigurationmanager-applyconfiguration.md)

### [DisableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)

### [EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)

### [GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-getconfiguration.md)

### [GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)

### [GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)

### [GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)

### [PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)

### [RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-removeconfiguration.md)

### [ResourceGet-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-resourceget.md)

### [ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-resourceset.md)

### [ResourceTest-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-resourcetest.md)

### [RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-rollback.md)

### [SendConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-sendconfiguration.md)

### [SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)

### [SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)

### [SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)

### [StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-stopconfiguration.md)

### [TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen](msft-dsclocalconfigurationmanager-testconfiguration.md)

# Fler resurser

## [Vitböcker](whitepapers.md)
