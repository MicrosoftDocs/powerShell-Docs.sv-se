---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendMetaConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendMetaConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager

Anger Local Configuration Manager-inställningar som används för att styra Configuration Agent.

<a name="syntax"></a>Syntax
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parametrar
----------

*ConfigurationData* \[i\]  
Miljödata för konfigurationen.

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


 

 



