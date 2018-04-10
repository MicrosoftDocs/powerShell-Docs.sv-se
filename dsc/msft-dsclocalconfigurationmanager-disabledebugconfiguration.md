---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DisableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 9392a721a542c89be8794882a800b374f11ca5fd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="disabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>DisableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

Inaktiverar felsökning av DSC-resurs.

<a name="syntax"></a>Syntax
------

```mof
uint32 DisableDebugConfiguration();
```

<a name="parameters"></a>Parametrar
----------

Den här metoden har inga parametrar.

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