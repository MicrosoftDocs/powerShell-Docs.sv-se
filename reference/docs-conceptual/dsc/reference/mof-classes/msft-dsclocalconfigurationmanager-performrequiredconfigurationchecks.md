---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942687"
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

*Flags* \[in @ no__t-2 en bitmask som anger vilken typ av konsekvens kontroll som ska köras. Följande värden är giltiga och kan kombineras med hjälp av en bitvis **or** -åtgärd:

|Value |Beskrivning |
|:--- |:---|
|**1** | En normal konsekvens kontroll. |
|**2** | En fortsättning på konsekvens kontroll efter en omstart. Värdet får inte kombineras med andra värden. |
|**4** | Konfigurationen ska hämtas från den hämtnings server som anges i metaconfiguration för noden. Värdet ska alltid kombineras med **1**, för värdet **5**. |
|**8** | Skicka status till rapport servern. |

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)