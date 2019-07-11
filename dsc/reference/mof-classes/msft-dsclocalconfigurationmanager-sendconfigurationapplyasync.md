---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734296"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync-metoden

Skickar konfigurationsdokumentet asynkront till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.

## <a name="syntax"></a>Syntax

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parametrar

*ConfigurationData* \[i\] miljödata om konfigurationen.

*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.

*jobId* \[i\] ID för jobbet för att skicka konfigurationen.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
