---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApply-metoden
description: SendConfigurationApply-metoden
ms.openlocfilehash: 9bd63220644e096b348f71ee9d4ac216af6a7ccc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648982"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="473d6-103">SendConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="473d6-103">SendConfigurationApply method</span></span>

<span data-ttu-id="473d6-104">Skickar konfigurations dokumentet till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="473d6-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="473d6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="473d6-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="473d6-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="473d6-106">Parameters</span></span>

<span data-ttu-id="473d6-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="473d6-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="473d6-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="473d6-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="473d6-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="473d6-109">Return value</span></span>

<span data-ttu-id="473d6-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="473d6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="473d6-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="473d6-111">Remarks</span></span>

<span data-ttu-id="473d6-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="473d6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="473d6-113">Krav</span><span class="sxs-lookup"><span data-stu-id="473d6-113">Requirements</span></span>

<span data-ttu-id="473d6-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="473d6-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="473d6-115">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="473d6-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="473d6-116">Se även</span><span class="sxs-lookup"><span data-stu-id="473d6-116">See also</span></span>

[<span data-ttu-id="473d6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="473d6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
