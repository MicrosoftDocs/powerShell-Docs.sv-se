---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationStatus-metoden
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942694"
---
# <a name="getconfigurationstatus-method"></a>GetConfigurationStatus-metoden

Hämta konfigurations status historik.

## <a name="syntax"></a>Syntax

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parametrar

*Alla* \[i\] **True** om den här metoden ska returnera information om all konfiguration som körs på datorn, inklusive konfigurations programmet och konsekvens kontrollen.

*configurationStatus* \[ut\] vid retur innehåller en inbäddad instans av **MSFT_DSCConfigurationStatus** -klassen som definierar inställningarna.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se också

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
