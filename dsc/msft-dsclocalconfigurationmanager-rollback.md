---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen

Återställer konfigurationen till en tidigare version.

<a name="syntax"></a>Syntax
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Parametrar
----------

*configurationNumber* \[i\] anger den begärda konfigurationen.

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