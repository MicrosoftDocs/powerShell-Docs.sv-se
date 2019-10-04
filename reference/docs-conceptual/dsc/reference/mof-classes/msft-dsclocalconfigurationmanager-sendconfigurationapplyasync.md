---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941546"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync-metoden

Skickar konfigurations dokumentet asynkront till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.

## <a name="syntax"></a>Syntax

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parametrar

*ConfigurationData* \[in @ no__t-2 miljö data för konfigurationen.

*tvinga* \[in @ no__t-2 **True** så att konfigurationen stoppas.

*jobId* \[in @ no__t-2 ID för det jobb som konfigurationen ska skickas till.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
