---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404900"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

Tar bort filerna.

## <a name="syntax"></a>Syntax

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parametrar

*Steg* \[i\] anger vilka konfigurationsdokumentet att ta bort. Följande värden är giltiga:

|Värde |Beskrivning |
|:--- |:---|
|**1** | Den **aktuella** konfigurationsdokumentet (current.mof). |
|**2** | Den **väntande** konfigurationsdokumentet (pending.mof).  |
|**4** | Den **föregående** konfigurationsdokumentet (previous.mof). |

*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)