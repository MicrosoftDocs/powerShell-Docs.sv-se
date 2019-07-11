---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 09b30edd48384c0e8412e0e6ee926a719249c5b8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726884"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager-klass

Den lokala Configuration Manager (LCM) som styr tillstånd för konfigurationsfiler och använder konfigurationen agenten för att tillämpa konfigurationerna.

Följande syntax är förenklad från kod Managed Object Format (MOF) och innehåller alla ärvda egenskaper.

## <a name="syntax"></a>Syntax

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Medlemmar

Den **MSFT_DSCLocalConfigurationManager** klassen har följande medlemmar:

- [Methods][]

### <a name="methods"></a>Metoder

Den **MSFT_DSCLocalConfigurationManager** klassen har dessa metoder.

|Metod |Beskrivning |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Använder Configuration-agenten för att tillämpa konfigurationen som väntar.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Inaktiverar felsökning av DSC-resurs.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Aktiverar felsökning av DSC-resurs.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Skickar konfigurationsdokumentet till hanterad nod och använder den **hämta** metod för Configuration agenten att tillämpa konfigurationen.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Hämtar Configuration-agenten utdata som är relaterade till ett specifikt jobb.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Hämta statushistorik konfiguration.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Hämtar LCM-inställningar som används för att kontrollera konfigurationen Agent.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Startar en konsekvenskontroll.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Tar bort filerna.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Direkt anropar den **hämta** -metoden för en DSC-resurs.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Direkt anropar den **ange** -metoden för en DSC-resurs.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Direkt anropar den **Test** -metoden för en DSC-resurs.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Samlar in tillbaka till en tidigare konfiguration.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Skickar konfigurationsdokumentet till hanterad nod och sparar den som en väntande ändring.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Skickar konfigurationsdokumentet till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Skicka konfigurationsdokumentet till hanterad nod och börja använda Configuration agenten för att tillämpa konfigurationen. Använd GetConfigurationResultOutput för att hämta resultatet utdata.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Anger LCM-inställningar som används för att styra agenten konfiguration.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Stoppar konfigurationen som håller på att skapas.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Skickar konfigurationsdokumentet till hanterad nod och verifierar den aktuella konfigurationen mot dokumentet.|

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration
