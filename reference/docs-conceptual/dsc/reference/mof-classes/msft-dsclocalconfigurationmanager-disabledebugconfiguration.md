---
ms.date: 07/14/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DisableDebugConfiguration-metoden
ms.openlocfilehash: 52d55ff6b1fd126482bbaa9480efc131ab2f100c
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463762"
---
# <a name="disabledebugconfiguration-method"></a>DisableDebugConfiguration-metoden

Inaktiverar fel sökning av DSC-resurs.

## <a name="syntax"></a>Syntax

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>Parametrar

Den här metoden har inga parametrar.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
