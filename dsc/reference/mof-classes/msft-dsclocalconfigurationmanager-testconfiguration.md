---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726960"
---
# <a name="testconfiguration-method"></a>TestConfiguration-metoden

Skickar konfigurationsdokumentet till hanterad nod och verifierar den aktuella konfigurationen mot dokumentet.

## <a name="syntax"></a>Syntax

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parametrar

*configurationData* \[i\] miljödata för confuguration.

*InDesiredState* \[ut\] på RETUR, anger du om hanterad nod är i tillståndet anges i konfigurationsdokumentet.

*ResourcesInDesiredState* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_ResourceInDesiredState** klass som anger resurser som finns i önskat läge.

*ResourcesNotInDesiredState* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte ingår i önskat läge.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
