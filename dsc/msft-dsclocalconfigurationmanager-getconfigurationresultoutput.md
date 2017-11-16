---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfigurationResultOutput-metoden i klassen MSFT_DSCLocalConfigurationManager

Hämtar Configuration Agent utdata som är associerade med ett specifikt jobb.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parametrar
----------

*jobId* \[i\]  
ID för jobbet som du vill hämta utdata.

*resumeOutputBookmark* \[i\]  
Anger att utdata ska vara en fortsättning från föregående bokmärke.

*utdata* \[ut\]  
Utdata för jobbet.

## <a name="return-value"></a>Returvärde
------------

Returnerar noll på lyckade; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Se även


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 



