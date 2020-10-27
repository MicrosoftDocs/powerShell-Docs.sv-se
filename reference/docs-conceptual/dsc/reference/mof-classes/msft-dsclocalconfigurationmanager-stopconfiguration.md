---
ms.date: 07/17/2020
ms.topic: reference
title: StopConfiguration-metoden
description: StopConfiguration-metoden
ms.openlocfilehash: 854c0dbe8554c08413735a5a7bc872776e0b0a6c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644617"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="ffedb-103">StopConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="ffedb-103">StopConfiguration method</span></span>

<span data-ttu-id="ffedb-104">Stoppar den konfigurations ändring som pågår.</span><span class="sxs-lookup"><span data-stu-id="ffedb-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="ffedb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ffedb-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ffedb-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ffedb-106">Parameters</span></span>

<span data-ttu-id="ffedb-107">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="ffedb-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ffedb-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ffedb-108">Return value</span></span>

<span data-ttu-id="ffedb-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="ffedb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ffedb-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ffedb-110">Remarks</span></span>

<span data-ttu-id="ffedb-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ffedb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ffedb-112">Krav</span><span class="sxs-lookup"><span data-stu-id="ffedb-112">Requirements</span></span>

<span data-ttu-id="ffedb-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ffedb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ffedb-114">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ffedb-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ffedb-115">Se även</span><span class="sxs-lookup"><span data-stu-id="ffedb-115">See also</span></span>

[<span data-ttu-id="ffedb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ffedb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
