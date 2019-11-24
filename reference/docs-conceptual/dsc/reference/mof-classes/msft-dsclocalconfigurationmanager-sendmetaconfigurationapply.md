---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendMetaConfigurationApply-metoden
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942596"
---
# <a name="sendmetaconfigurationapply-method"></a>SendMetaConfigurationApply-metoden

Anger de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.

## <a name="syntax"></a>Syntax

```mof
uint32 SendMetaConfigurationApply(
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
