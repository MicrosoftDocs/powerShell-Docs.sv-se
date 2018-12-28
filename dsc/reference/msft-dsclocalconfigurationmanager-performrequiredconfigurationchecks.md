---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404685"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen

Startar en konsekvenskontroll med Schemaläggaren.

## <a name="syntax"></a>Syntax

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parametrar

*Flaggor* \[i\] en bitmask som anger vilken typ av konsekvenskontroll ska köras. Följande värden är giltiga och kan kombineras med hjälp av en bitvis **eller** igen:

|Värde |Beskrivning |
|:--- |:---|
|**1** | En normal konsekvenskontroll. |
|**2** | En förlängning av en konsekvenskontroll efter en omstart. Det här värdet får inte kombineras med andra värden. |
|**4** | Konfigurationen ska hämtas från hämtningsservern som anges i metaconfiguration för noden. Det här värdet alltid att kombineras med **1**, för ett värde för **5**. |
|**8** | Skicka status till rapportservern. |

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)