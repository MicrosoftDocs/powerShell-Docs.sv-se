---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>TestConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager

Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.

<a name="syntax"></a>Syntax
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parametrar
----------

*configurationData* \[i\]  
Miljödata för confuguration.

*InDesiredState* \[ut\]  
Anger om hanterad nod är i tillståndet anges i konfigurationen dokumentet på return.

*ResourcesInDesiredState* \[ut\]  
På RETUR, innehåller en inbäddad instans av den **MSFT_ResourceInDesiredState** klass som anger resurser som ingår i tillståndet.

*ResourcesNotInDesiredState* \[ut\]  
På RETUR, innehåller en inbäddad instans av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte är i tillståndet önskade.

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


 

 



