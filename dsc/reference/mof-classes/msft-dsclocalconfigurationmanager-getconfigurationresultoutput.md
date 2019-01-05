---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048650"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen

Hämtar Configuration-agenten utdata som är associerade med ett specifikt jobb.

## <a name="syntax"></a>Syntax

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parametrar

*jobId* \[i\] ID för jobbet som du vill hämta utdata.

*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från en föregående bokmärke.

*utdata* \[ut\] utdata för det angivna jobbet.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)