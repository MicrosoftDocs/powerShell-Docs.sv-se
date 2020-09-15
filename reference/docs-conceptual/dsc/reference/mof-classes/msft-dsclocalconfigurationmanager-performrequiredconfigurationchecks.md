---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden
ms.openlocfilehash: ea4294ffdcb2580fa7b39b18966b642d58073eb6
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464459"
---
# <a name="performrequiredconfigurationchecks-method"></a>PerformRequiredConfigurationChecks-metoden

Startar en konsekvens kontroll med hjälp av Schemaläggaren.

## <a name="syntax"></a>Syntax

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parametrar

**Flaggor** \[ i \] en bitmask som anger vilken typ av konsekvens kontroll som ska köras. Följande värden är giltiga och kan kombineras med hjälp av en bitvis **or** -åtgärd:

|Värde |Beskrivning |
|:--- |:---|
|**1** | En normal konsekvens kontroll. |
|**2** | En fortsättning på konsekvens kontroll efter en omstart. Värdet får inte kombineras med andra värden. |
|**4** | Konfigurationen ska hämtas från den hämtnings server som anges i metaconfiguration för noden. Värdet ska alltid kombineras med **1**, för värdet **5**. |
|**8** | Skicka status till rapport servern. |

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
