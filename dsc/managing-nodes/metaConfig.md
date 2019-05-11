---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera den lokala Konfigurationshanteraren
ms.openlocfilehash: 15d696587d54d4a6464096cfb78757c41e9185c6
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229495"
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurera den lokala Konfigurationshanteraren

> Gäller för: Windows PowerShell 5.0

Den lokala Configuration Manager (LCM) är motorn av Desired State Configuration (DSC).
LCM körs på varje målnoden och är ansvarig för parsning och tillämpa konfigurationer som skickas till noden.
Det är också ansvarig för ett antal andra aspekter av DSC, inklusive följande.

- Fastställa uppdatering läge (sändning eller hämtning).
- Anger hur ofta en nod hämtar och utfärdar konfigurationer.
- Koppla noden med pull-tjänsten.
- Ange partiella konfigurationer.

Du kan använda en särskild typ av konfiguration för att konfigurera MGM om du vill ange var och en av dessa beteenden.
I följande avsnitt beskrivs hur du konfigurerar LCM.

Windows PowerShell 5.0 introduceras nya inställningar för att hantera lokala Configuration Manager.
Information om att konfigurera LCM i Windows PowerShell 4.0 finns i [konfigurera den lokala Konfigurationshanteraren i tidigare versioner av Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Skriva och tillämpa en LCM-konfiguration

Om du vill konfigurera LCM, skapa och kör en särskild typ av konfiguration som gäller LCM inställningar.
Om du vill ange en LCM-konfiguration, kan du använda DscLocalConfigurationManager-attributet.
Nedan visas en enkel konfiguration som anger LCM till push-läge.

```powershell
[DSCLocalConfigurationManager()]
configuration LCMConfig
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
        }
    }
}
```

Processen för att tillämpa inställningar för MGM liknar tillämpar en DSC-konfiguration.
Du ska skapa en konfiguration för LCM, kompilera den till en MOF-fil och tillämpa den på noden.
Till skillnad från DSC-konfigurationer, du inte tillämpar en LCM-konfiguration genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.
I stället kan du anropa [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager), ange sökvägen till LCM konfigurationen MOF som en parameter.
När du tillämpar LCM konfigurationen du kan se egenskaperna för LCM genom att anropa den [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.

En LCM-konfiguration kan innehålla block endast för en begränsad uppsättning resurser.
I exemplet ovan är den enda resurs med namnet **inställningar**.
De tillgängliga resurserna är:

* **ConfigurationRepositoryWeb**: Anger en HTTP-hämtningstjänsten för konfigurationer.
* **ConfigurationRepositoryShare**: Anger en SMB-resurs för konfigurationer.
* **ResourceRepositoryWeb**: Anger en HTTP-hämtningstjänsten för moduler.
* **ResourceRepositoryShare**: Anger en SMB-resurs för moduler.
* **ReportServerWeb**: Anger en HTTP-hämtningstjänsten som rapporterna skickas.
* **PartialConfiguration**: tillhandahåller data för att aktivera partiella konfigurationer.

## <a name="basic-settings"></a>Grundläggande inställningar

Förutom att ange pull tjänstens slutpunkter/sökvägar och partiella konfigurationer kan alla egenskaper för LCM har konfigurerats i en **inställningar** block.
Följande egenskaper är tillgängliga i en **inställningar** block.

|  Egenskap  |  Typ  |  Beskrivning   |
|----------- |------- |--------------- |
| ActionAfterReboot| sträng| Anger vad som händer när en omstart vid tillämpningen av en konfiguration. Möjliga värden är __”ContinueConfiguration”__ och __”StopConfiguration”__. <ul><li> __ContinueConfiguration__: Fortsätt använda den aktuella konfigurationen efter omstart av datorn. Detta är standardvärdet</li><li>__StopConfiguration__: Stoppa den aktuella konfigurationen efter omstart av datorn.</li></ul>|
| AllowModuleOverwrite| Bool| __$TRUE__ om nya konfigurationer som laddats ned från pull-tjänsten ska kunna skriva över gamla på målnoden. Annars $FALSE.|
| CertificateID| sträng| Tumavtrycket för ett certifikat som används för att skydda autentiseringsuppgifter som angavs i en konfiguration. Mer information finns i [behöver du säkra autentiseringsuppgifter i Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Obs:__ detta sköts automatiskt om du använder Azure Automation DSC-hämtningstjänsten.|
| ConfigurationDownloadManagers| CimInstance[]| Föråldrad. Använd __ConfigurationRepositoryWeb__ och __ConfigurationRepositoryShare__ förutsättningarna för att definiera configuration pull tjänstens slutpunkter.|
| ConfigurationID| sträng| För bakåtkompatibilitet kompatibilitet med äldre pull service versioner. Ett GUID som identifierar konfigurationsfilen för att hämta från en pull-tjänsten. Noden hämtar konfigurationer på pull-tjänsten om namnet på konfigurationen MOF heter ConfigurationID.mof.<br> __Obs:__ Om du ställer in den här egenskapen registrera noden med en pull-tjänsten med hjälp av __RegistrationKey__ fungerar inte. Mer information finns i [konfigurera en hämtningsklient med konfigurationsnamn](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| sträng | Anger hur LCM faktiskt tillämpar konfigurationen målnoder. Möjliga värden är __”ApplyOnly”__,__”ApplyAndMonitor”__, och __”ApplyAndAutoCorrect”__. <ul><li>__ApplyOnly__: DSC gäller konfigurationen av och gör ingenting ytterligare såvida inte en ny konfiguration skickas till målnoden eller när en ny konfiguration hämtas från en tjänst. Efter första gången av en ny konfiguration kontrollerar inte DSC för drift från ett tidigare konfigurerade tillstånd. Observera att DSC ska försöka att tillämpa konfigurationen tills den lyckas innan __ApplyOnly__ träder i kraft. </li><li> __ApplyAndMonitor__: Det här är standardkonfigurationen. LCM gäller alla nya konfigurationer. Efter första gången av en ny konfiguration rapporterar DSC avvikelse i loggarna om målnoden drifts från önskat tillstånd. Observera att DSC ska försöka att tillämpa konfigurationen tills den lyckas innan __ApplyAndMonitor__ träder i kraft.</li><li>__ApplyAndAutoCorrect__: DSC gäller alla nya konfigurationer. Efter första gången av en ny konfiguration om målnoden drifts från önskat tillstånd DSC rapporterar avvikelse i loggar och tillämpar sedan den aktuella konfigurationen igen.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Hur ofta på några minuter, den aktuella konfigurationen är markerad och tillämpas. Den här egenskapen ignoreras om egenskapen ConfigurationMode anges till ApplyOnly. Standardvärdet är 15.|
| DebugMode| sträng| Möjliga värden är __ingen__, __ForceModuleImport__, och __alla__. <ul><li>Ange __ingen__ att använda cachelagrade resurser. Detta är standardinställningen och ska användas i produktionsscenarier.</li><li>Ställa in __ForceModuleImport__, orsakar MGM om du vill läsa in alla DSC-resurs-moduler, även om de tidigare har lästs in och cachelagras. Detta påverkar prestanda för DSC-åtgärder som varje modul laddas på användning. Använder vanligtvis det här värdet när du felsöker en resurs</li><li>I den här versionen __alla__ är samma som __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| Bool| Ställ in på `$true` så att resurser för att starta om en nod med hjälp av den `$global:DSCMachineStatus` flaggan. I annat fall kommer du behöva manuellt starta om noden för alla konfigurationer som kräver. Standardvärdet är `$false`. Om du vill använda den här inställningen när ett villkor för omstart är branschrekommendationer när det gäller av något annat än DSC (till exempel Windows Installer), kombinera den här inställningen med det [xPendingReboot](https://github.com/powershell/xpendingreboot) modulen.|
| RefreshMode| sträng| Anger hur LCM hämtar konfigurationer. Möjliga värden är __”inaktiverad”__, __”Push”__, och __”Pull”__. <ul><li>__Inaktiverad__: DSC-konfigurationer har inaktiverats för den här noden.</li><li> __Push-__: Konfigurationer initieras genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Konfigurationen tillämpas omedelbart på noden. Det här är standardkonfigurationen.</li><li>__Hämta:__ Noden är konfigurerad att regelbundet kontrollera konfigurationerna från en pull-tjänsten eller SMB-sökväg. Om den här egenskapen anges till __hämta__, måste du ange en HTTP (tjänst) eller SMB (resurs)-sökväg i en __ConfigurationRepositoryWeb__ eller __ConfigurationRepositoryShare__ block.</li></ul>|
| RefreshFrequencyMins| UInt32| Tidsintervall i minuter, då LCM kontrollerar en pull-tjänsten för att hämta uppdaterade konfigurationer. Det här värdet ignoreras om LCM inte har konfigurerats i pull-läge. Standardvärdet är 30.|
| ReportManagers| CimInstance[]| Föråldrad. Använd __ReportServerWeb__ förutsättningarna för att definiera en slutpunkt för att skicka rapportdata till en pull-tjänst.|
| ResourceModuleManagers| CimInstance[]| Föråldrad. Använd __ResourceRepositoryWeb__ och __ResourceRepositoryShare__ förutsättningarna för att definiera pull tjänsten HTTP-slutpunkter eller SMB-sökvägar, respektive.|
| PartialConfigurations| CimInstance| Inte implementerat. Använd inte.|
| StatusRetentionTimeInDays | UInt32| Antal dagar som LCM ser till att statusen för den aktuella konfigurationen.|

> [!NOTE]
> LCM startar den **ConfigurationModeFrequencyMins** cykel baserat på:
>
> - En ny metaconfig tillämpas med hjälp av `Set-DscLocalConfigurationManager`
> - En omstart av datorn
>
> För alla villkor där en krasch som identifieras inom 30 sekunder och cykeln inträffar i processen för timer startas.
> En samtidig åtgärd kan försena cykeln startas, om varaktigheten för den här åtgärden överskrider den konfigurera cykel frekvensen nästa timern startar inte.
>
> Exempelvis metaconfig är konfigurerad med en 15 minuters pull frekvens och en hämtning uppstår på T1.  Noden inte är klar för 16 minuter.  Den första 15 minuters cykeln ignoreras och nästa pull inträffar vid T1 + 15 + 15.

## <a name="pull-service"></a>Hämtningstjänsten

MGM konfigurationen har stöd för att definiera följande typerna av pull-tjänstslutpunkter:

- **Konfigurationsservern**: En lagringsplats för DSC-konfigurationer. Definiera konfigurationsservrar med **ConfigurationRepositoryWeb** (för web-baserade servrar) och **ConfigurationRepositoryShare** (för SMB-baserade servrar) block.
- **Resursservern**: En lagringsplats för DSC-resurser, paketerad som PowerShell-moduler. Definiera resursservrar med **ResourceRepositoryWeb** (för web-baserade servrar) och **ResourceRepositoryShare** (för SMB-baserade servrar) block.
- **Rapportservern**: En tjänst som DSC skickar rapportdata till. Definiera rapportservrar med **ReportServerWeb** block. En rapportserver måste vara en webbtjänst.

Mer information om pull-tjänsten finns [Desired State Configuration-hämtningstjänsten](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Configuration server block

För att definiera en webbaserad konfigurationsserver, skapar du en **ConfigurationRepositoryWeb** block.
En **ConfigurationRepositoryWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|Bool|Ange **$TRUE** att tillåta anslutningar från noden till servern utan autentisering. Ange **$FALSE** kan kräva autentisering.|
|CertificateID|sträng|Tumavtrycket för ett certifikat som används för att autentisera till servern.|
|ConfigurationNames|String[]|En matris med namnen på de konfigurationer som ska hämtas av målnoden. De används endast om noden är registrerad med pull-tjänsten med hjälp av en **RegistrationKey**. Mer information finns i [konfigurera en hämtningsklient med konfigurationsnamn](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|sträng|Ett GUID som registrerar noden med pull-tjänsten. Mer information finns i [konfigurera en hämtningsklient med konfigurationsnamn](../pull-server/pullClientConfigNames.md).|
|ServerURL|sträng|URL till tjänsten för konfiguration.|
|ProxyURL*|sträng|URL: en för http-proxy ska användas vid kommunikation med tjänsten för konfiguration.|
|ProxyCredential*|pscredential|Autentiseringsuppgifter som ska användas för http-proxy.|

>! Obs \* stöds i Windows 1809 och senare.

Ett exempelskript för att förenkla konfigurera ConfigurationRepositoryWeb-värde för lokala noder är tillgängliga – Se [generera DSC metaconfigurations](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

För att definiera en SMB-baserad konfiguration-server, skapar du en **ConfigurationRepositoryShare** block.
En **ConfigurationRepositoryShare** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|Autentiseringsuppgifter|MSFT_Credential|De autentiseringsuppgifter som används för att autentisera till SMB-resursen.|
|SourcePath|sträng|Sökvägen till SMB-resurs.|

## <a name="resource-server-blocks"></a>Resursen server block

För att definiera en webbaserad resursservern, skapar du en **ResourceRepositoryWeb** block.
En **ResourceRepositoryWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|Bool|Ange **$TRUE** att tillåta anslutningar från noden till servern utan autentisering. Ange **$FALSE** kan kräva autentisering.|
|CertificateID|sträng|Tumavtrycket för ett certifikat som används för att autentisera till servern.|
|RegistrationKey|sträng|Ett GUID som identifierar noden till pull-tjänsten.|
|ServerURL|sträng|URL till konfigurationsservern.|
|ProxyURL*|sträng|URL: en för http-proxy ska användas vid kommunikation med tjänsten för konfiguration.|
|ProxyCredential*|pscredential|Autentiseringsuppgifter som ska användas för http-proxy.|

>! Obs \* stöds i Windows 1809 och senare.

Ett exempelskript för att förenkla konfigurera ResourceRepositoryWeb-värde för lokala noder är tillgängliga – Se [generera DSC metaconfigurations](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

För att definiera en SMB-baserad resurs-server, skapar du en **ResourceRepositoryShare** block.
**ResourceRepositoryShare** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|Autentiseringsuppgifter|MSFT_Credential|De autentiseringsuppgifter som används för att autentisera till SMB-resursen. Ett exempel på Skicka autentiseringsuppgifter finns i [att konfigurera en DSC SMB-hämtningsserver](../pull-server/pullServerSMB.md)|
|SourcePath|sträng|Sökvägen till SMB-resurs.|

## <a name="report-server-blocks"></a>Report server-block

För att definiera en rapportserver, skapar du en **ReportServerWeb** block.
Report server-rollen är inte kompatibel med SMB-baserade pull-tjänsten.
**ReportServerWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|Bool|Ange **$TRUE** att tillåta anslutningar från noden till servern utan autentisering. Ange **$FALSE** kan kräva autentisering.|
|CertificateID|sträng|Tumavtrycket för ett certifikat som används för att autentisera till servern.|
|RegistrationKey|sträng|Ett GUID som identifierar noden till pull-tjänsten.|
|ServerURL|sträng|URL till konfigurationsservern.|
|ProxyURL*|sträng|URL: en för http-proxy ska användas vid kommunikation med tjänsten för konfiguration.|
|ProxyCredential*|pscredential|Autentiseringsuppgifter som ska användas för http-proxy.|

>! Obs \* stöds i Windows 1809 och senare.

Ett exempelskript för att förenkla konfigurera ReportServerWeb-värde för lokala noder är tillgängliga – Se [generera DSC metaconfigurations](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Partiella konfigurationer

För att definiera en partiell konfiguration, skapar du en **PartialConfiguration** block.
Mer information om hur partiella konfigurationer finns i [partiellt DSC-konfigurationer](../pull-server/partialConfigs.md).
**PartialConfiguration** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|ConfigurationSource|string[]|En matris med namnen på konfigurationsservrar som tidigare definierats i **ConfigurationRepositoryWeb** och **ConfigurationRepositoryShare** block där partiell konfiguration hämtas från.|
|DependsOn|sträng{}|En lista över namnen på andra konfigurationer som måste slutföras innan den här partiella konfigurationen tillämpas.|
|Beskrivning|sträng|Text som används för att beskriva partiell konfiguration.|
|ExclusiveResources|string[]|En matris med resurser som är exklusivt för den här partiell konfiguration.|
|RefreshMode|sträng|Anger hur LCM hämtar den här partiell konfiguration. Möjliga värden är __”inaktiverad”__, __”Push”__, och __”Pull”__. <ul><li>__Inaktiverad__: Den här partiell konfiguration är inaktiverad.</li><li> __Push-__: Partiell konfiguration skickas till noden genom att anropa den [publicera-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet. När alla partiella konfigurationer för noden är antingen pushas eller hämtas från en tjänst, konfigurationen kan startas genom att anropa `Start-DscConfiguration –UseExisting`. Det här är standardkonfigurationen.</li><li>__Hämta:__ Noden är konfigurerad att regelbundet kontrollera partiell konfiguration från en pull-tjänst. Om den här egenskapen anges till __Pull__, måste du ange en pull-tjänst i en __ConfigurationSource__ egenskapen. Läs mer om Azure Automation-hämtningstjänsten [översikt över Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|string[]|En matris med namnen på resursservrar som att ladda ned nödvändiga resurser för den här partiell konfiguration. Dessa namn måste referera till tjänstslutpunkter som tidigare definierats i **ResourceRepositoryWeb** och **ResourceRepositoryShare** block.|

__Obs:__ partiella konfigurationer stöds med Azure Automation DSC, men bara en konfiguration kan hämtas från varje automation-konto per nod.

## <a name="see-also"></a>Se även

### <a name="concepts"></a>Begrepp
[Desired State Configuration-översikt](../overview/overview.md)

[Komma igång med Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Andra resurser

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Konfigurera en hämtningsklient med konfigurationsnamn](../pull-server/pullClientConfigNames.md)
