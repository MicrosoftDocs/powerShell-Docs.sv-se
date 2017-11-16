---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ApplyConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>ApplyConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager

Använder Configuration Agent för att använda den konfiguration som är i vänteläge. 

Om det finns ingen konfiguration väntande, återställer den här metoden den aktuella konfigurationen.


## <a name="syntax"></a>Syntax
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar
----------

*Tvinga* \[i\]  
Om det här är **SANT**, den aktuella konfigurationen används igen, även om det finns en konfiguration väntande.

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

 

 



