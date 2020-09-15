---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464085"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput-metoden

Hämtar konfigurations agentens utdata som är associerad med ett speciellt jobb.

## <a name="syntax"></a>Syntax

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
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

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
