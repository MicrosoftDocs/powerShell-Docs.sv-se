---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfigurationStatus-metoden i klassen MSFT_DSCLocalConfigurationManager

Hämta statushistorik konfiguration.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parametrar
----------

*Alla* \[i\]  
**SANT** om den här metoden ska returnera information om alla konfigurationen som körs på datorn, inklusive program för konfiguration och konsekvenskontrollen.

*configurationStatus* \[ut\]  
På RETUR, innehåller en inbäddad instans av den **MSFT_DSCConfigurationStatus** klass som definierar inställningar.

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


 

 



