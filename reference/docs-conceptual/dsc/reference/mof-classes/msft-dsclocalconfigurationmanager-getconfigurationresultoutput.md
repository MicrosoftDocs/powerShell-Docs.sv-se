---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput-metoden
description: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644703"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput-metoden

Hämtar konfigurations agentens utdata som är associerad med ett speciellt jobb.

## <a name="syntax"></a>Syntax

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parametrar

**jobId** \[ i \] ID: t för det jobb för vilket utdata ska hämtas.

**resumeOutputBookmark** \[ i \] anger att utdata ska vara en fortsättning från ett tidigare bok märke.

**utdata** \[ ut \] utdata för det angivna jobbet.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
