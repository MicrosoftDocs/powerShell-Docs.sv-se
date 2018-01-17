---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
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

 

 



