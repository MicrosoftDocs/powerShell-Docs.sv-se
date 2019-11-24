---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941574"
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

*jobId* \[i\] ID: t för det jobb som utdata ska hämtas till.

*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från ett tidigare bok märke.

*utdata* \[ut\] utdata för det angivna jobbet.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se också

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
