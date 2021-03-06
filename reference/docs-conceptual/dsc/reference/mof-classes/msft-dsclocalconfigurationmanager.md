---
ms.date: 07/14/2020
ms.topic: reference
title: MSFT_DSCLocalConfigurationManager-klass
description: MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 31112c7d15884699171ec732ac20b6960b0858a9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644811"
---
# <a name="msft_dsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager-klass

Den lokala Configuration Manager (LCM) som styr tillståndet för konfigurationsfiler och använder konfigurations agenten för att tillämpa konfigurationerna.

Följande syntax är förenklad från Managed Object Format (MOF) kod och innehåller alla ärvda egenskaper.

## <a name="syntax"></a>Syntax

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Medlemmar

**MSFT_DSCLocalConfigurationManager** -klassen har följande medlemmar:

- Indatametod []

### <a name="methods"></a>Metoder

Klassen **MSFT_DSCLocalConfigurationManager** har dessa metoder.

|Metoder |Beskrivning |
|:--- |:---|
| [ApplyConfiguration (boolesk)](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Använder konfigurations agenten för att tillämpa den konfiguration som väntar.|
| [DisableDebugConfiguration ()](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Inaktiverar fel sökning av DSC-resurs.|
| [EnableDebugConfiguration (boolesk)](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Aktiverar fel sökning av DSC-resurs.|
| [GetConfiguration ()](msft-dsclocalconfigurationmanager-getconfiguration.md)| Skickar konfigurations dokumentet till den hanterade noden och använder **Get** -metoden för konfigurations agenten för att tillämpa konfigurationen.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Hämtar konfigurations agentens utdata som är relaterade till ett speciellt jobb.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Hämta konfigurations status historik.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Hämtar de LCM-inställningar som används för att kontrol lera konfigurations agenten.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Startar konsekvens kontrollen.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Tar bort konfigurationsfilerna.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Anropar direkt **Get** -metoden för en DSC-resurs.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Anropar **set** -metoden för en DSC-resurs direkt.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Anropar direkt **test** metoden för en DSC-resurs.|
| [Ånger](msft-dsclocalconfigurationmanager-rollback.md)| Återställer till en tidigare konfiguration.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Skickar konfigurations dokumentet till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Skicka konfigurations dokumentet till den hanterade noden och börja använda konfigurations agenten för att tillämpa konfigurationen. Använd GetConfigurationResultOutput för att hämta resultatet av utdata.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Anger de LCM-inställningar som används för att kontrol lera konfigurations agenten.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Stoppar den konfiguration som pågår.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Skickar konfigurations dokumentet till den hanterade noden och verifierar den aktuella konfigurationen mot dokumentet.|

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration
