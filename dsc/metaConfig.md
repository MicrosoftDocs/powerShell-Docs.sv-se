---
ms.date: 2017-10-11
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera den lokala Configuration Manager
ms.openlocfilehash: 947bc17347204f6f15a24f83b449582afe65a4ee
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurera den lokala Configuration Manager

> Gäller för: Windows PowerShell 5.0

Den lokala Configuration Manager (MGM) är motorn för önskad tillstånd Configuration DSC ().
MGM körs på varje målnoden och är ansvarig för parsning och anta konfigurationer som skickas till noden.
Det är också ansvarig för ett antal andra aspekter av DSC, inklusive följande.

- Avgör uppdatera läge (sändning eller hämtning).
- Ange hur ofta en nod tar emot och utfärdar konfigurationer.
- Koppla noden med pull-tjänsten.
- Ange partiella konfigurationer.

Du kan använda en särskild typ av konfiguration för att konfigurera MGM om du vill ange var och en av dessa beteenden.
I följande avsnitt beskrivs hur du konfigurerar MGM.

> **Obs**: det här avsnittet gäller MGM som introducerades i Windows PowerShell 5.0.
Information om hur du konfigurerar MGM i Windows PowerShell 4.0 finns [Windows PowerShell 4.0 önskad tillstånd Configuration Local Configuration Manager](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Skriva och anta en MGM-konfiguration

Om du vill konfigurera MGM om du skapar och kör en särskild typ av konfigurationen som gäller MGM inställningar.
Om du vill ange en MGM konfiguration kan du använda attributet DscLocalConfigurationManager.
Nedan visas en enkel konfiguration som anger MGM till push-läge.

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

Processen för att tillämpa inställningar för MGM liknar tillämpa DSC-konfigurationen.
Skapar en MGM konfiguration, du kompilera den till en MOF-fil, och tillämpa det på noden.
Till skillnad från DSC-konfigurationer du inte tillämpar en MGM konfiguration genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.
I stället kan du anropa [Set DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx), ange sökväg till MGM konfigurationen MOF som en parameter.
När du tillämpar konfigurationen MGM om du kan se egenskaperna för MGM genom att anropa den [Get-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.

En MGM konfiguration kan innehålla endast för en begränsad uppsättning resurser.
I föregående exempel är den enda resurs med namnet är **inställningar**.
De tillgängliga resurserna är:

* **ConfigurationRepositoryWeb**: Anger en HTTP-pull-tjänst för konfigurationer.
* **ConfigurationRepositoryShare**: Anger en SMB-resurs för konfigurationer.
* **ResourceRepositoryWeb**: Anger en HTTP-pull-tjänst för moduler.
* **ResourceRepositoryShare**: Anger en SMB-resurs för moduler.
* **ReportServerWeb**: Anger en HTTP-pull-tjänst som rapporterna skickas.
* **PartialConfiguration**: tillhandahåller data för att aktivera partiella konfigurationer.

## <a name="basic-settings"></a>Grundläggande inställningar

Förutom att ange pull service slutpunkter/sökvägar och delar konfigurationer, alla egenskaper för MGM konfigureras i en **inställningar** block.
Följande egenskaper är tillgängliga i en **inställningar** block.

|  Egenskap  |  Typ  |  Beskrivning   |
|----------- |------- |--------------- |
| ActionAfterReboot| sträng| Anger vad som händer när en omstart vid tillämpningen av en konfiguration. Möjliga värden är __”ContinueConfiguration”__ och __”StopConfiguration”__. <ul><li> __ContinueConfiguration__: fortsätta använda den aktuella konfigurationen efter omstart av datorn. Detta är standardvärdet</li><li>__StopConfiguration__: stoppa den aktuella konfigurationen efter omstart av datorn.</li></ul>|
| AllowModuleOverwrite| bool| __$TRUE__ om nya konfigurationer som hämtas från tjänsten pull tillåts att skriva över gamla på målnoden. Annars $FALSE.|
| CertificateID| sträng| Tumavtryck för ett certifikat som används för att säkra autentiseringsuppgifter som angavs i en konfiguration. Mer information finns i [vill skydda autentiseringsuppgifter i Windows PowerShell Desired State Configuration](http://blogs.msdn.com/b/powershell/archive/2014/01/31/want-to-secure-credentials-in-windows-powershell-desired-state-configuration.aspx)?. <br> __Obs:__ detta hanteras automatiskt om med pull-tjänsten för Azure Automation DSC.|
| ConfigurationDownloadManagers| CimInstance[]| Föråldrad. Använd __ConfigurationRepositoryWeb__ och __ConfigurationRepositoryShare__ block definiera configuration pull-tjänstens slutpunkter.|
| ConfigurationID| sträng| För bakåtkompatibilitet kompatibilitet med äldre pull service versioner. Ett GUID som identifierar konfigurationsfil för att hämta från en pull-tjänst. Noden hämtar konfigurationer på pull-tjänsten om namnet på konfigurationen MOF heter ConfigurationID.mof.<br> __Obs:__ om du anger egenskapen registreras noden med en pull-tjänsten med hjälp av __RegistrationKey__ fungerar inte. Mer information finns i [ställa in en pull-klient med konfigurationsnamn](pullClientConfigNames.md).|
| ConfigurationMode| sträng | Anger hur MGM faktiskt gäller konfigurationen av att målnoder. Möjliga värden är __”ApplyOnly”__,__”ApplyandMonitior”__, och __”ApplyandAutoCorrect”__. <ul><li>__ApplyOnly__: DSC gäller konfigurationen av och inget ytterligare såvida inte en ny konfiguration flyttas till målnoden eller när en ny konfiguration hämtas från en tjänst. DSC kontrollerar inte om inte ett tidigare konfigurerade tillstånd efter första gången för en ny konfiguration. Observera att DSC ska försöka använda konfigurationen tills den lyckas innan __ApplyOnly__ träder i kraft. </li><li> __ApplyAndMonitor__: Detta är standardvärdet. MGM gäller alla nya konfigurationer. Efter första gången för en ny konfiguration om målnoden drifts från det önskade läget rapporterar DSC diskrepans i loggarna. Observera att DSC ska försöka använda konfigurationen tills den lyckas innan __ApplyAndMonitor__ träder i kraft.</li><li>__ApplyAndAutoCorrect__: DSC gäller alla nya konfigurationer. Efter första gången för en ny konfiguration om målnoden drifts från önskade tillstånd DSC rapporterar diskrepans i loggarna och tillämpar sedan den aktuella konfigurationen igen.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Hur ofta i minuter för den aktuella konfigurationen kontrolleras och tillämpas. Den här egenskapen ignoreras om egenskapen ConfigurationMode anges till ApplyOnly. Standardvärdet är 15.|
| DebugMode| sträng| Möjliga värden är __ingen__, __ForceModuleImport__, och __alla__. <ul><li>Ange till __ingen__ att använda cachelagrade resurser. Detta är standardinställningen och ska användas i produktionen scenarier.</li><li>Ange till __ForceModuleImport__, gör MGM om du vill läsa in alla moduler som resursen DSC, även om de tidigare har lästs in och cachelagras. Detta påverkar prestanda för DSC-åtgärder som varje modul laddas på användning. Använder vanligtvis det här värdet när du felsöker en resurs</li><li>I den här versionen __alla__ är samma som __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| bool| Ställ in på __$true__ att automatiskt starta om noden efter en konfiguration som kräver omstart har tillämpats. I annat fall behöver du manuellt starta om noden för valfri konfiguration som kräver. Standardvärdet är __$false__. Om du vill använda den här inställningen när en omstart villkoret trätt i kraft av något annat än DSC (till exempel Windows Installer), kombinera den här inställningen med det [xPendingReboot](https://github.com/powershell/xpendingreboot) modul.|
| RefreshMode| sträng| Anger hur MGM hämtar konfigurationer. Möjliga värden är __”inaktiverad”__, __”Push”__, och __”Pull”__. <ul><li>__Inaktiverad__: DSC-konfigurationer har inaktiverats för den här noden.</li><li> __Push-__: konfigurationer initieras genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet. Konfigurationen tillämpas omedelbart på noden. Det här är standardkonfigurationen.</li><li>__Pull:__ noden är konfigurerad för att regelbundet kontrollera konfigurationer från en pull-tjänsten eller SMB-sökväg. Om den här egenskapen anges till __hämtar__, måste du ange en HTTP (service) eller SMB (resurs) sökväg i en __ConfigurationRepositoryWeb__ eller __ConfigurationRepositoryShare__ block.</li></ul>|
| RefreshFrequencyMins| Uint32| Tidsintervall i minuter, som kontrollerar MGM en pull-tjänst för att få uppdaterade konfigurationer. Det här värdet ignoreras om MGM inte har konfigurerats på pull-läge. Standardvärdet är 30.|
| ReportManagers| CimInstance[]| Föråldrad. Använd __ReportServerWeb__ block att definiera en slutpunkt för att skicka rapportdata till en pull-tjänst.|
| ResourceModuleManagers| CimInstance[]| Föråldrad. Använd __ResourceRepositoryWeb__ och __ResourceRepositoryShare__ block definiera pull service HTTP-slutpunkter eller SMB-sökvägar respektive.|
| PartialConfigurations| CimInstance| Inte implementerat. Använd inte.|
| StatusRetentionTimeInDays | UInt32| Antal dagar som MGM håller status för den aktuella konfigurationen.|

## <a name="pull-service"></a>Pull-tjänsten

DSC-inställningarna gör det möjligt för en nod som ska hanteras genom att dra konfigurationer och moduler och publicera reporting data till en fjärrplats.
Aktuella alternativ för pull-tjänsten är:

- Azure Automation önskade tillstånd konfigurationstjänsten
- En instans för pull-tjänsten som körs på Windows Server
- En SMB-resurs (inte stöder publicerar reporting data)

MGM konfigurationen har stöd för definiera följande typer av slutpunkter för pull:

- **Konfigurationsservern**: en lagringsplats för DSC-konfigurationer. Definiera configuration-servrar med hjälp av **ConfigurationRepositoryWeb** (för Webbaserad servrar) och **ConfigurationRepositoryShare** (för SMB-baserade servrar) block.
- **Resursservern**: en lagringsplats för DSC-resurser, paketeras i PowerShell-moduler. Definiera resursservrar med **ResourceRepositoryWeb** (för Webbaserad servrar) och **ResourceRepositoryShare** (för SMB-baserade servrar) block.
- **Rapportservern**: en tjänst som DSC skickar rapportdata till. Definiera rapportservrar med **ReportServerWeb** block. En rapportserver måste vara en webbtjänst.

**Den rekommenderade lösningen**, och alternativet med de funktioner som är tillgängliga, är [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started).

Azure-tjänsten kan hantera noder lokalt i privat Datacenter eller i offentliga moln, till exempel Azure och AWS.
Överväg att begränsa utgående trafik till endast publicerade Azure IP-adressintervall för privata miljöer där servrarna inte kan ansluta direkt till Internet, (se [IP-intervall för Azure-Datacenter](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Tjänsten online-funktioner som inte är tillgängliga i pull-tjänsten på Windows Server inkluderar:
- Krypteras alla data under överföring och i vila
- Klientcertifikat skapas och hanteras automatiskt
- Hemligheter lagra för att centralt hantera [lösenord/autentiseringsuppgifterna](https://docs.microsoft.com/en-us/azure/automation/automation-credentials), eller [variabler](https://docs.microsoft.com/en-us/azure/automation/automation-variables) , till exempel servernamn eller anslutningssträngar
- Centralt hantera nod [MGM konfiguration](metaConfig.md#basic-settings)
- Tilldela centralt konfigurationer till klientnoder
- Versionen konfiguration ändras till ”Kanarieöarna grupper” för att testa innan det nådde produktion
- Grafisk rapportering
  - Information om status på nivån för DSC-resurs i granularitet
  - Detaljerade felmeddelanden från klientdatorer för felsökning
- [Integrering med Azure logganalys](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-diagnostics) för aviseringar, automatiserade åtgärder Android/iOS-app för rapportering och aviseringar

För information om hur du konfigurerar och använder HTTP pull-tjänsten på Windows Server, se [ställer in en DSC pull server](pullServer.md).
Du vara medveten om att det är en begränsad implementering med bara grundläggande funktioner för att lagra konfigurationer och moduler och avbildar rapportdata i till en lokal databas.

## <a name="configuration-server-blocks"></a>Configuration server-block

För att definiera en webbaserad konfigurationsservern, skapar du en **ConfigurationRepositoryWeb** block.
En **ConfigurationRepositoryWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|bool|Ange till **$TRUE** att tillåta anslutningar från noden till servern utan autentisering. Ange till **$FALSE** kräver autentisering.|
|CertificateID|sträng|Tumavtryck för ett certifikat som används för att autentisera till servern.|
|ConfigurationNames|String]|En matris med namnen på de konfigurationer som ska hämtas av målnoden. De används endast om noden är registrerad med pull-tjänsten med hjälp av en **RegistrationKey**. Mer information finns i [ställa in en pull-klient med konfigurationsnamn](pullClientConfigNames.md).|
|RegistrationKey|sträng|En GUID som registrerar noden med pull-tjänsten. Mer information finns i [ställa in en pull-klient med konfigurationsnamn](pullClientConfigNames.md).|
|ServerURL|sträng|URL till konfigurationstjänsten.|

Ett exempelskript för att förenkla konfigurera ConfigurationRepositoryWeb värdet för lokala noder är tillgängliga - finns [genererar DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Om du vill definiera en server med SMB-baserad konfiguration du skapar en **ConfigurationRepositoryShare** block.
En **ConfigurationRepositoryShare** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|autentiseringsuppgifter|MSFT_Credential|De autentiseringsuppgifter som används för att autentisera till SMB-resursen.|
|Källsökväg|sträng|Sökvägen till SMB-resursen.|

## <a name="resource-server-blocks"></a>Resursen server block

För att definiera en webbaserad resursservern, skapar du en **ResourceRepositoryWeb** block.
En **ResourceRepositoryWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|bool|Ange till **$TRUE** att tillåta anslutningar från noden till servern utan autentisering. Ange till **$FALSE** kräver autentisering.|
|CertificateID|sträng|Tumavtryck för ett certifikat som används för att autentisera till servern.|
|RegistrationKey|sträng|Ett GUID som identifierar noden till pull-tjänsten.|
|ServerURL|sträng|URL till konfigurationsservern.|

Ett exempelskript för att förenkla konfigurera ResourceRepositoryWeb värdet för lokala noder är tillgängliga - finns [genererar DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

För att definiera en SMB-baserade resursservern, skapar du en **ResourceRepositoryShare** block.
**ResourceRepositoryShare** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|autentiseringsuppgifter|MSFT_Credential|De autentiseringsuppgifter som används för att autentisera till SMB-resursen. Ett exempel på Skicka autentiseringsuppgifter finns [ställer in en DSC SMB pull-server](pullServerSMB.md)|
|Källsökväg|sträng|Sökvägen till SMB-resursen.|

## <a name="report-server-blocks"></a>Report server-block

Om du vill definiera en rapportserver som du skapar en **ReportServerWeb** block.
Serverrollen rapporten är inte kompatibel med SMB-baserade pull-tjänsten.
**ReportServerWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|bool|Ange till **$TRUE** att tillåta anslutningar från noden till servern utan autentisering. Ange till **$FALSE** kräver autentisering.|
|CertificateID|sträng|Tumavtryck för ett certifikat som används för att autentisera till servern.|
|RegistrationKey|sträng|Ett GUID som identifierar noden till pull-tjänsten.|
|ServerURL|sträng|URL till konfigurationsservern.|

Ett exempelskript för att förenkla konfigurera ReportServerWeb värdet för lokala noder är tillgängliga - finns [genererar DSC metaconfigurations](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Partiell konfigurationer

Om du vill definiera en partiell konfiguration du skapar en **PartialConfiguration** block.
Mer information om konfigurationer som delvis finns [DSC partiell konfigurationer](partialConfigs.md).
**PartialConfiguration** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|ConfigurationSource|String]|En matris med namnet på konfiguration, som tidigare definierats i **ConfigurationRepositoryWeb** och **ConfigurationRepositoryShare** block, där den partiella konfigurationen hämtas från.|
|dependsOn|strängen {}|En lista över namnen på andra konfigurationer som måste slutföras innan den här partiella konfigurationen tillämpas.|
|Beskrivning|sträng|Text som används för att beskriva den partiella konfigurationen.|
|ExclusiveResources|String]|En matris med exklusivt för den här konfigurationen som delar resurser.|
|RefreshMode|sträng|Anger hur MGM hämtar partiella konfigurationen. Möjliga värden är __”inaktiverad”__, __”Push”__, och __”Pull”__. <ul><li>__Inaktiverad__: partiell konfigurationen är inaktiverad.</li><li> __Push-__: partiell konfigurationen skickas till noden genom att anropa den [publicera DscConfiguration](https://technet.microsoft.com/en-us/library/mt517875.aspx) cmdlet. När alla delar konfigurationer för noden är nedtryckt eller hämtas från en tjänst, konfigurationen kan startas genom att anropa `Start-DscConfiguration –UseExisting`. Det här är standardkonfigurationen.</li><li>__Pull:__ noden är konfigurerad för att regelbundet kontrollera partiella konfigurationen från en pull-tjänst. Om den här egenskapen anges till __Pull__, måste du ange en pull-tjänst i ett __ConfigurationSource__ egenskapen. Mer information om Azure Automation pull-tjänsten finns [översikt över Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|String]|En matris med namnen på resursservrar som du vill hämta nödvändiga resurser för den här partiella konfigurationen. Dessa namn måste referera till slutpunkter som tidigare definierats i **ResourceRepositoryWeb** och **ResourceRepositoryShare** block.|

__Obs:__ partiella konfigurationer stöds med Azure Automation DSC, men bara en konfiguration som kan hämtas från varje automation-konto per nod.

## <a name="see-also"></a>Se även

### <a name="concepts"></a>Begrepp
[Desired State Configuration-översikt](overview.md)

[Komma igång med Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Andra resurser

[Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx)

[Installera en pull-klient med konfigurationsnamn](pullClientConfigNames.md)
