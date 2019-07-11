---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DisableDebugConfiguration-metoden
ms.openlocfilehash: e3eab98c734b3fd1593ceb2b5d4b40fa69a3bf97
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727170"
---
# <a name="disabledebugconfiguration-method"></a>DisableDebugConfiguration-metoden

Inaktiverar felsökning av DSC-resurs.

## <a name="syntax"></a>Syntax

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>Parametrar

Den här metoden har inga parametrar.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
