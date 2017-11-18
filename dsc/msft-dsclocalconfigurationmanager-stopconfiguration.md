---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>StopConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager

Stoppar konfigurationsändringen som pågår.

<a name="syntax"></a>Syntax
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a>Parametrar
----------

*Tvinga* \[i\]  
**SANT** att tvinga konfigurationen som ska sluta.

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


 

 


