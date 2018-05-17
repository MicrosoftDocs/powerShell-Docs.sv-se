---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DisableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: fef4337e4e9c5cc72b457704899498624476f131
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
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