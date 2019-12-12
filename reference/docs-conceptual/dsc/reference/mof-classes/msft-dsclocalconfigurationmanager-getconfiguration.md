---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfiguration-metoden
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942715"
---
# <a name="getconfiguration-method"></a>GetConfiguration-metoden

Skickar konfigurations dokumentet till den hanterade noden och använder **Get** -metoden för konfigurations agenten för att tillämpa konfigurationen.

## <a name="syntax"></a>Syntax

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parametrar

*configurationData* \[i\] anger de konfigurations data som ska skickas.

*konfigurationer* \[ut\] vid retur innehåller en inbäddad instans av konfigurationerna.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
