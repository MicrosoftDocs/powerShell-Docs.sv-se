---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: EnableDebugConfiguration-metoden
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464102"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration-metoden

Aktiverar fel sökning av DSC-resurs.

## <a name="syntax"></a>Syntax

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parametrar

**BreakAll** \[ i \] anger en Bryt punkt på varje rad i resurs skriptet.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
