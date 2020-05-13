---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera den lokala Configuration Manager
ms.openlocfilehash: 5847a29efd165724ffe9f1f0e89cfaf358ade31c
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271856"
---
# <a name="configuring-the-local-configuration-manager"></a>Konfigurera den lokala Configuration Manager

> Gäller för: Windows PowerShell 5,0

Den lokala Configuration Manager (LCM) är motorn för önskad tillstånds konfiguration (DSC).
LCM körs på varje målnod och ansvarar för parsning och konfiguration som skickas till noden.
Det är också ansvarigt för ett antal andra aspekter av DSC, inklusive följande.

- Bestämmer uppdaterings läget (push eller pull).
- Ange hur ofta en nod hämtar och agerar för konfigurationer.
- Kopplar noden till pull-tjänsten.
- Ange partiella konfigurationer.

Du kan använda en särskild typ av konfiguration för att konfigurera LCM för att ange var och en av dessa beteenden.
I följande avsnitt beskrivs hur du konfigurerar LCM.

Windows PowerShell 5,0 introducerade nya inställningar för att hantera lokala Configuration Manager.
Information om hur du konfigurerar LCM i Windows PowerShell 4,0 finns i [Konfigurera den lokala Configuration Manager i tidigare versioner av Windows PowerShell](metaconfig4.md).

## <a name="writing-and-enacting-an-lcm-configuration"></a>Skriva och agera på en LCM-konfiguration

Om du vill konfigurera LCM skapar du och kör en särskild typ av konfiguration som tillämpar LCM-inställningar.
Om du vill ange en LCM-konfiguration använder du attributet DscLocalConfigurationManager.
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

Processen för att tillämpa inställningar på LCM liknar att använda en DSC-konfiguration.
Du kommer att skapa en LCM-konfiguration, kompilera den till en MOF-fil och tillämpa den på noden.
Till skillnad från DSC-konfigurationer tillämpar du inte en LCM-konfiguration genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .
I stället anropar du [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)och anger sökvägen till LCM-konfigurationens MOF som en parameter.
När du har fördefinierat LCM-konfigurationen kan du se egenskaperna för LCM genom att anropa cmdleten [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) .

En LCM-konfiguration kan bara innehålla block för en begränsad uppsättning resurser.
I det föregående exemplet är den enda resurs som heter är **Inställningar**.
De andra tillgängliga resurserna är:

* **ConfigurationRepositoryWeb**: anger en http-pull-tjänst för konfigurationer.
* **ConfigurationRepositoryShare**: anger en SMB-resurs för konfigurationer.
* **ResourceRepositoryWeb**: anger en http pull-tjänst för moduler.
* **ResourceRepositoryShare**: anger en SMB-resurs för moduler.
* **ReportServerWeb**: anger en http-pull-tjänst som rapporter skickas till.
* **PartialConfiguration**: tillhandahåller data för att aktivera partiella konfigurationer.

## <a name="basic-settings"></a>Grundläggande inställningar

Förutom att ange slut punkter för pull-tjänster/sökvägar och partiella konfigurationer konfigureras alla egenskaper för LCM i ett **inställnings** block.
Följande egenskaper är tillgängliga i ett **inställnings** block.

|  Egenskap  |  Typ  |  Beskrivning   |
|----------- |------- |--------------- |
| ActionAfterReboot| sträng| Anger vad som händer efter en omstart under tillämpning av en konfiguration. De möjliga värdena är __"ContinueConfiguration"__ och __"StopConfiguration"__. <ul><li> __ContinueConfiguration__: Fortsätt att använda den aktuella konfigurationen efter omstart av datorn. Detta är standardvärdet</li><li>__StopConfiguration__: stoppa den aktuella konfigurationen efter omstart av datorn.</li></ul>|
| AllowModuleOverwrite| boolesk| __$True__ om nya konfigurationer som hämtats från pull-tjänsten tillåts skriva över de gamla på målnoden. Annars $FALSE.|
| CertificateID| sträng| Tumavtryck för ett certifikat som används för att skydda autentiseringsuppgifter som skickas i en konfiguration. Mer information finns i [vill du skydda autentiseringsuppgifter i Windows PowerShell Desired State Configuration?](https://devblogs.microsoft.com/powershell/want-to-secure-credentials-in-windows-powershell-desired-state-configuration/). <br> __Obs!__ detta hanteras automatiskt om du använder Azure Automation DSC-pull.|
| ConfigurationDownloadManagers| CimInstance []| Föråldrade. Använd __ConfigurationRepositoryWeb__ -och __ConfigurationRepositoryShare__ -block för att definiera slut punkter för konfigurations-pull-tjänster.|
| ConfigurationID| sträng| För bakåtkompatibilitet med äldre hämtnings tjänst versioner. Ett GUID som identifierar konfigurations filen som ska hämtas från en pull-tjänst. Noden hämtar konfigurationer i pull-tjänsten om namnet på konfigurations-MOF: en heter ConfigurationID. mof.<br> __Obs:__ Om du ställer in den här egenskapen fungerar inte att registrera noden med en pull-tjänst genom att använda __RegistrationKey__ . Mer information finns i [Konfigurera en pull-klient med konfigurations namn](../pull-server/pullClientConfigNames.md).|
| ConfigurationMode| sträng | Anger hur LCM faktiskt tillämpar konfigurationen på målnoden. Möjliga värden är __"ApplyOnly"__,__"ApplyAndMonitor"__ och __"ApplyAndAutoCorrect"__. <ul><li>__ApplyOnly__: DSC tillämpar konfigurationen och gör ingenting ytterligare om inte en ny konfiguration skickas till målnoden eller när en ny konfiguration hämtas från en tjänst. Efter första tillämpning av en ny konfiguration söker DSC inte efter avvikelse från ett tidigare konfigurerat tillstånd. Observera att DSC försöker tillämpa konfigurationen tills den har slutförts innan __ApplyOnly__ börjar gälla. </li><li> __ApplyAndMonitor__: Detta är standardvärdet. LCM använder alla nya konfigurationer. Efter den första körningen av en ny konfiguration, om mål-noden går från det önskade läget, rapporterar DSC den avvikelsen i loggarna. Observera att DSC försöker tillämpa konfigurationen tills den har slutförts innan __ApplyAndMonitor__ börjar gälla.</li><li>__ApplyAndAutoCorrect__: DSC använder alla nya konfigurationer. Efter den första tillämpningen av en ny konfiguration, om mål noden går från det önskade läget, rapporterar DSC den avvikelsen i loggarna och tillämpar sedan den aktuella konfigurationen igen.</li></ul>|
| ConfigurationModeFrequencyMins| UInt32| Hur ofta, i minuter, är den aktuella konfigurationen markerad och tillämpas. Den här egenskapen ignoreras om egenskapen ConfigurationMode är inställd på ApplyOnly. Standardvärdet är 15.|
| DebugMode| sträng| Möjliga värden är __none__, __ForceModuleImport__och __all__. <ul><li>Ange till __ingen__ om du vill använda cachelagrade resurser. Detta är standardinställningen och ska användas i produktions scenarier.</li><li>Inställningen till __ForceModuleImport__, gör att LCM kan läsa in alla DSC-resursprogram på nytt, även om de tidigare har lästs in och cachelagrats. Detta påverkar prestandan för DSC-åtgärder eftersom varje modul läses in på nytt vid användning. Normalt använder du det här värdet vid fel sökning av en resurs</li><li>I den här versionen är __alla__ samma som __ForceModuleImport__</li></ul> |
| RebootNodeIfNeeded| boolesk| Ange det här för `$true` att tillåta resurser att starta om noden med hjälp av `$global:DSCMachineStatus` flaggan. Annars måste du starta om noden manuellt för alla konfigurationer som kräver det. Standardvärdet är `$false`. Om du vill använda den här inställningen när ett villkor för omstart utförs av något annat än DSC (till exempel Windows Installer) kombinerar du den här inställningen med __PendingReboot__ -resursen i [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) -modulen.|
| RefreshMode| sträng| Anger hur LCM hämtar konfigurationer. De möjliga värdena är __"Disabled"__, __"push"__ och __"pull"__. <ul><li>__Inaktive__rad: DSC-konfigurationer har inaktiverats för den här noden.</li><li> __Push__: konfigurationer initieras genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) . Konfigurationen tillämpas omedelbart på noden. Detta är standardvärdet.</li><li>__Hämta:__ Noden är konfigurerad för att regelbundet söka efter konfigurationer från en pull-tjänst eller SMB-sökväg. Om den här egenskapen är inställd på __Hämta__måste du ange en http-sökväg (tjänst) eller en SMB-sökväg (resurs) i ett __ConfigurationRepositoryWeb__ -eller __ConfigurationRepositoryShare__ -block.</li></ul>|
| RefreshFrequencyMins| Uint32| Det tidsintervall, i minuter, då LCM kontrollerar en pull-tjänst för att hämta uppdaterade konfigurationer. Värdet ignoreras om LCM inte har kon figurer ATS i pull-läge. Standardvärdet är 30.|
| ReportManagers| CimInstance []| Föråldrade. Använd __ReportServerWeb__ -block för att definiera en slut punkt för att skicka rapporterings data till en pull-tjänst.|
| ResourceModuleManagers| CimInstance []| Föråldrade. Använd __ResourceRepositoryWeb__ -och __ResourceRepositoryShare__ -block för att definiera http-slutpunkter för pull-tjänster respektive SMB-sökvägar.|
| PartialConfigurations| CimInstance| Inte implementerat. Använd inte.|
| StatusRetentionTimeInDays | UInt32| Antalet dagar som LCM behåller statusen för den aktuella konfigurationen.|

> [!NOTE]
> LCM startar **ConfigurationModeFrequencyMins** -cykeln baserat på:
>
> - En ny Metaconfig tillämpas med hjälp av`Set-DscLocalConfigurationManager`
> - Omstart av datorn
>
> För alla villkor där timer-processen upplever en krasch, kommer den att identifieras inom 30 sekunder och cykeln startas om.
> En samtidig åtgärd kan fördröja cykeln från att startas, om den här åtgärdens varaktighet överskrider den konfigurerade cykel frekvensen, kommer nästa timer inte att starta.
>
> Metaconfig konfigureras till exempel med en frekvens på 15 minuter och hämtning sker vid T1.  Noden slutförs inte i 16 minuter.  Den första 15 minuters cykeln ignoreras och nästa hämtning sker vid T1 + 15 + 15.

## <a name="pull-service"></a>Pull-tjänst

LCM-konfigurationen stöder definition av följande typer av pull service-slutpunkter:

- **Konfigurations Server**: en lagrings plats för DSC-konfigurationer. Definiera konfigurations servrar med hjälp av **ConfigurationRepositoryWeb** (för webbaserade servrar) och **ConfigurationRepositoryShare** -block (för SMB-baserade servrar).
- **Resurs Server**: en lagrings plats för DSC-resurser, paketerade som PowerShell-moduler. Definiera resurs servrar genom att använda **ResourceRepositoryWeb** (för webbaserade servrar) och **ResourceRepositoryShare** -block (för SMB-baserade servrar).
- **Report Server**: en tjänst som DSC skickar rapport data till. Definiera rapport servrar genom att använda **ReportServerWeb** -block. En rapport Server måste vara en webb tjänst.

Mer information om pull-tjänsten finns i [pull-tjänsten för önskad tillstånds konfiguration](../pull-server/pullServer.md).

## <a name="configuration-server-blocks"></a>Konfigurations Server block

Om du vill definiera en webbaserad konfigurations Server skapar du ett **ConfigurationRepositoryWeb** -block.
En **ConfigurationRepositoryWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|boolesk|Ange till **$True** om du vill tillåta anslutningar från noden till servern utan autentisering. Ange till **$false** för att kräva autentisering.|
|CertificateID|sträng|Tumavtryck för ett certifikat som används för att autentisera till servern.|
|ConfigurationNames|Sträng []|En matris med namn på konfigurationer som ska hämtas av målnoden. Dessa används endast om noden har registrerats med pull-tjänsten med hjälp av en **RegistrationKey**. Mer information finns i [Konfigurera en pull-klient med konfigurations namn](../pull-server/pullClientConfigNames.md).|
|RegistrationKey|sträng|Ett GUID som registrerar noden med pull-tjänsten. Mer information finns i [Konfigurera en pull-klient med konfigurations namn](../pull-server/pullClientConfigNames.md).|
|ServerURL|sträng|URL: en för konfigurations tjänsten.|
|ProxyURL*|sträng|URL-adressen till den http-proxy som ska användas vid kommunikation med konfigurations tjänsten.|
|ProxyCredential*|PSCredential|Autentiseringsuppgifter som ska användas för HTTP-proxyn.|

> [!NOTE]
> * Stöds i Windows-versioner 1809 och senare.

Ett exempel skript för att förenkla konfigureringen av ConfigurationRepositoryWeb-värdet för lokala noder finns i [skapa DSC-metaconfigurations](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Om du vill definiera en SMB-baserad konfigurations Server skapar du ett **ConfigurationRepositoryShare** -block.
En **ConfigurationRepositoryShare** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|Autentiseringsuppgift|MSFT_Credential|De autentiseringsuppgifter som används för att autentisera till SMB-resursen.|
|Sök|sträng|Sökvägen till SMB-resursen.|

## <a name="resource-server-blocks"></a>Resurs Server block

Om du vill definiera en webbaserad resurs Server skapar du ett **ResourceRepositoryWeb** -block.
En **ResourceRepositoryWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|boolesk|Ange till **$True** om du vill tillåta anslutningar från noden till servern utan autentisering. Ange till **$false** för att kräva autentisering.|
|CertificateID|sträng|Tumavtryck för ett certifikat som används för att autentisera till servern.|
|RegistrationKey|sträng|Ett GUID som identifierar noden för pull-tjänsten.|
|ServerURL|sträng|Webb adressen till konfigurations servern.|
|ProxyURL*|sträng|URL-adressen till den http-proxy som ska användas vid kommunikation med konfigurations tjänsten.|
|ProxyCredential*|PSCredential|Autentiseringsuppgifter som ska användas för HTTP-proxyn.|

> [!NOTE]
> * Stöds i Windows-versioner 1809 och senare.

Ett exempel skript för att förenkla konfigureringen av ResourceRepositoryWeb-värdet för lokala noder finns i [skapa DSC-metaconfigurations](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

Om du vill definiera en SMB-baserad resurs Server skapar du ett **ResourceRepositoryShare** -block.
**ResourceRepositoryShare** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|Autentiseringsuppgift|MSFT_Credential|De autentiseringsuppgifter som används för att autentisera till SMB-resursen. Ett exempel på att skicka autentiseringsuppgifter finns i [Konfigurera en DSC SMB-pull-server](../pull-server/pullServerSMB.md)|
|Sök|sträng|Sökvägen till SMB-resursen.|

## <a name="report-server-blocks"></a>Report Server-block

Om du vill definiera en rapport Server skapar du ett **ReportServerWeb** -block.
Rapport Server rollen är inte kompatibel med SMB-baserad pull-tjänst.
**ReportServerWeb** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|AllowUnsecureConnection|boolesk|Ange till **$True** om du vill tillåta anslutningar från noden till servern utan autentisering. Ange till **$false** för att kräva autentisering.|
|CertificateID|sträng|Tumavtryck för ett certifikat som används för att autentisera till servern.|
|RegistrationKey|sträng|Ett GUID som identifierar noden för pull-tjänsten.|
|ServerURL|sträng|Webb adressen till konfigurations servern.|
|ProxyURL*|sträng|URL-adressen till den http-proxy som ska användas vid kommunikation med konfigurations tjänsten.|
|ProxyCredential*|PSCredential|Autentiseringsuppgifter som ska användas för HTTP-proxyn.|

> [!NOTE]
> * Stöds i Windows-versioner 1809 och senare.

Ett exempel skript för att förenkla konfigureringen av ReportServerWeb-värdet för lokala noder finns i [skapa DSC-metaconfigurations](https://docs.microsoft.com/azure/automation/automation-dsc-onboarding#generating-dsc-metaconfigurations)

## <a name="partial-configurations"></a>Partiella konfigurationer

Om du vill definiera en partiell konfiguration skapar du ett **PartialConfiguration** -block.
Mer information om ofullständiga konfigurationer finns i [DSC-delvis konfigurationer](../pull-server/partialConfigs.md).
**PartialConfiguration** definierar följande egenskaper.

|Egenskap|Typ|Beskrivning|
|---|---|---|
|ConfigurationSource|sträng []|En matris med namn på konfigurations servrar, som tidigare definierats i **ConfigurationRepositoryWeb** -och **ConfigurationRepositoryShare** -block, där del konfigurationen hämtas från.|
|DependsOn|sträng{}|En lista med namn på andra konfigurationer som måste slutföras innan den här del konfigurationen tillämpas.|
|Description|sträng|Text som används för att beskriva den partiella konfigurationen.|
|ExclusiveResources|sträng []|En matris med resurser som är exklusiva till denna del konfiguration.|
|RefreshMode|sträng|Anger hur LCM får den här del konfigurationen. De möjliga värdena är __"Disabled"__, __"push"__ och __"pull"__. <ul><li>__Inaktiverat__: den här del konfigurationen är inaktive rad.</li><li> __Push__: den partiella konfigurationen skickas till noden genom att anropa cmdleten [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) . När alla ofullständiga konfigurationer för noden antingen har push-överförts eller hämtats från en tjänst kan du starta konfigurationen genom att anropa `Start-DscConfiguration –UseExisting` . Detta är standardvärdet.</li><li>__Hämta:__ Noden är konfigurerad för att regelbundet söka efter delvis konfiguration från en pull-tjänst. Om den här egenskapen är inställd på __Hämta__måste du ange en pull-tjänst i en __ConfigurationSource__ -egenskap. Mer information om Azure Automation pull service finns i [Översikt över Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview).</li></ul>|
|ResourceModuleSource|sträng []|En matris med namnen på resurs servrar som nödvändiga resurser ska hämtas från för den här del konfigurationen. Dessa namn måste referera till tjänst slut punkter som tidigare definierats i **ResourceRepositoryWeb** -och **ResourceRepositoryShare** -block.|

__Obs!__ partiella konfigurationer stöds med Azure Automation DSC, men bara en konfiguration kan hämtas från varje Automation-konto per nod.

## <a name="see-also"></a>Se även

### <a name="concepts"></a>Begrepp
[Översikt över önskad tillstånds konfiguration](../overview/overview.md)

[Komma igång med Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-getting-started)

### <a name="other-resources"></a>Andra resurser

[Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)

[Konfigurera en pull-klient med konfigurations namn](../pull-server/pullClientConfigNames.md)
