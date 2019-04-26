---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DisableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ec5a401de4cb93f302f8572c0408e3f32d8876ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078902"
---
# <a name="disabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>DisableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

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