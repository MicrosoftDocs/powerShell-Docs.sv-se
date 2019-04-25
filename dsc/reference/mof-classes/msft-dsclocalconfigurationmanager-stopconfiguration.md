---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078257"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

Stoppar konfigurationsändring som håller på att skapas.

## <a name="syntax"></a>Syntax

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar

*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)