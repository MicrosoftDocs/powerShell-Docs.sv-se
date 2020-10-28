---
ms.date: 07/17/2020
ms.topic: reference
title: SendMetaConfigurationApply-metoden
description: SendMetaConfigurationApply-metoden
ms.openlocfilehash: 27c58819c0249ace011c475e500e565e5daed9bb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648964"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="123d7-103">SendMetaConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="123d7-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="123d7-104">Anger de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="123d7-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="123d7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="123d7-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="123d7-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="123d7-106">Parameters</span></span>

<span data-ttu-id="123d7-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="123d7-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="123d7-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="123d7-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="123d7-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="123d7-109">Return value</span></span>

<span data-ttu-id="123d7-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="123d7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="123d7-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="123d7-111">Remarks</span></span>

<span data-ttu-id="123d7-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="123d7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="123d7-113">Krav</span><span class="sxs-lookup"><span data-stu-id="123d7-113">Requirements</span></span>

<span data-ttu-id="123d7-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="123d7-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="123d7-115">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="123d7-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="123d7-116">Se även</span><span class="sxs-lookup"><span data-stu-id="123d7-116">See also</span></span>

[<span data-ttu-id="123d7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="123d7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
