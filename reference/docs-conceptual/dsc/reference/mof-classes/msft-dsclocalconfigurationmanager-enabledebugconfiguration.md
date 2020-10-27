---
ms.date: 07/17/2020
ms.topic: reference
title: EnableDebugConfiguration-metoden
description: EnableDebugConfiguration-metoden
ms.openlocfilehash: 536366e6e1627a249f3bc2dc19bfd8ff3de42117
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644770"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="db03c-103">EnableDebugConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="db03c-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="db03c-104">Aktiverar fel sökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="db03c-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="db03c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="db03c-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="db03c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="db03c-106">Parameters</span></span>

<span data-ttu-id="db03c-107">**BreakAll** \[ i \] anger en Bryt punkt på varje rad i resurs skriptet.</span><span class="sxs-lookup"><span data-stu-id="db03c-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="db03c-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="db03c-108">Return value</span></span>

<span data-ttu-id="db03c-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="db03c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="db03c-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="db03c-110">Remarks</span></span>

<span data-ttu-id="db03c-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="db03c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="db03c-112">Krav</span><span class="sxs-lookup"><span data-stu-id="db03c-112">Requirements</span></span>

<span data-ttu-id="db03c-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="db03c-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="db03c-114">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="db03c-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="db03c-115">Se även</span><span class="sxs-lookup"><span data-stu-id="db03c-115">See also</span></span>

[<span data-ttu-id="db03c-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="db03c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
