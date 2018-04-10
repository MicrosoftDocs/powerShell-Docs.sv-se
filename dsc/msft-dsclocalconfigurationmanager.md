---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 598bd7490043975d9d965c12a7337fb3475b3ded
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager-klass

Den lokala Configuration Manager (MGM) som styr tillstånd konfigurationsfiler och använder Configuration Agent för att tillämpa konfigurationerna.

Följande syntax är förenklad från kod Managed Object Format (MOF) och innehåller alla ärvda egenskaper.

## <a name="syntax"></a>Syntax
------

``` syntax
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Medlemmar
-------

Den **MSFT_DSCLocalConfigurationManager** klassen har följande medlemmar:

-   [Metoder] []

### <a name="methods"></a>Metoder

Den **MSFT_DSCLocalConfigurationManager** klassen har dessa metoder.

|Metod |Beskrivning |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Använder Configuration Agent för att använda den konfiguration som är i vänteläge.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Inaktiverar felsökning av DSC-resurs.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Aktiverar felsökning av DSC-resurs.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Hämtar Configuration Agent utdata som är relaterade till ett visst jobb.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Hämta statushistorik konfiguration.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Hämtar MGM inställningarna som används för att styra Configuration Agent.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Startar en konsekvenskontroll.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Tar bort konfigurationsfilerna.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Direkt anropar den **hämta** metoden för en DSC-resurs.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Direkt anropar den **ange** metoden för en DSC-resurs.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Direkt anropar den **Test** metoden för en DSC-resurs.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Samlar tillbaka till en tidigare konfiguration.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Skickar konfiguration dokumentet till noden hanterade och sparar den som en väntande ändring.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Skicka konfiguration dokumentet till hanterade noder och börja använda Configuration Agent för att tillämpa konfigurationen. Använd GetConfigurationResultOutput för att hämta resultatet utdata.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Anger MGM inställningarna som används för att styra Configuration Agent.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Stoppar den konfiguration som pågår.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.|





## <a name="requirements"></a>Krav
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration