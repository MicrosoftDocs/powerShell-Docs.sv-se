---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
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

*ConfigurationData* \[i\] miljö data för konfigurationen.

*tvinga* \[i\] **Sant** för att tvinga konfigurationen att stoppas.

*jobId* \[i\] ID: t för det jobb som konfigurationen ska skickas till.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
