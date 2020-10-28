---
ms.date: 07/17/2020
ms.topic: reference
title: RemoveConfiguration-metoden
description: RemoveConfiguration-metoden
ms.openlocfilehash: d5988ac014c457407c56a097c9a376427376eb3f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650733"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="4afb8-103">RemoveConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="4afb8-103">RemoveConfiguration method</span></span>

<span data-ttu-id="4afb8-104">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="4afb8-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="4afb8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4afb8-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="4afb8-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="4afb8-106">Parameters</span></span>

<span data-ttu-id="4afb8-107">**Steg** \[ i \] anger vilket konfigurations dokument som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="4afb8-107">**Stage** \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="4afb8-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="4afb8-108">The following values are valid:</span></span>

|<span data-ttu-id="4afb8-109">Värde</span><span class="sxs-lookup"><span data-stu-id="4afb8-109">Value</span></span> |<span data-ttu-id="4afb8-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4afb8-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="4afb8-111">**1**</span><span class="sxs-lookup"><span data-stu-id="4afb8-111">**1**</span></span> | <span data-ttu-id="4afb8-112">**Aktuellt** konfigurations dokument (aktuell. MOF).</span><span class="sxs-lookup"><span data-stu-id="4afb8-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="4afb8-113">**2**</span><span class="sxs-lookup"><span data-stu-id="4afb8-113">**2**</span></span> | <span data-ttu-id="4afb8-114">**Väntande** konfigurations dokument (väntar. MOF).</span><span class="sxs-lookup"><span data-stu-id="4afb8-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="4afb8-115">**4**</span><span class="sxs-lookup"><span data-stu-id="4afb8-115">**4**</span></span> | <span data-ttu-id="4afb8-116">**Föregående** konfigurations dokument (föregående. MOF).</span><span class="sxs-lookup"><span data-stu-id="4afb8-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="4afb8-117">*Tvinga* \[ i \] **True** för att framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4afb8-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4afb8-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="4afb8-118">Return value</span></span>

<span data-ttu-id="4afb8-119">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="4afb8-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4afb8-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4afb8-120">Remarks</span></span>

<span data-ttu-id="4afb8-121">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="4afb8-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4afb8-122">Krav</span><span class="sxs-lookup"><span data-stu-id="4afb8-122">Requirements</span></span>

<span data-ttu-id="4afb8-123">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="4afb8-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4afb8-124">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4afb8-124">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4afb8-125">Se även</span><span class="sxs-lookup"><span data-stu-id="4afb8-125">See also</span></span>

[<span data-ttu-id="4afb8-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4afb8-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
