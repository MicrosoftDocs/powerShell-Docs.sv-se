---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApply-metoden
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942603"
---
# <a name="sendconfigurationapply-method"></a>SendConfigurationApply-metoden

Skickar konfigurations dokumentet till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.

## <a name="syntax"></a>Syntax

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar

*ConfigurationData* \[i\] miljö data för konfigurationen.

*tvinga* \[i\] **Sant** för att tvinga konfigurationen att stoppas.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se också

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
