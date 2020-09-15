---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden
ms.openlocfilehash: ea4294ffdcb2580fa7b39b18966b642d58073eb6
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464459"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="692a7-103">PerformRequiredConfigurationChecks-metoden</span><span class="sxs-lookup"><span data-stu-id="692a7-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="692a7-104">Startar en konsekvens kontroll med hjälp av Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="692a7-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="692a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="692a7-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="692a7-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="692a7-106">Parameters</span></span>

<span data-ttu-id="692a7-107">**Flaggor** \[ i \] en bitmask som anger vilken typ av konsekvens kontroll som ska köras.</span><span class="sxs-lookup"><span data-stu-id="692a7-107">**Flags** \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="692a7-108">Följande värden är giltiga och kan kombineras med hjälp av en bitvis **or** -åtgärd:</span><span class="sxs-lookup"><span data-stu-id="692a7-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="692a7-109">Värde</span><span class="sxs-lookup"><span data-stu-id="692a7-109">Value</span></span> |<span data-ttu-id="692a7-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="692a7-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="692a7-111">**1**</span><span class="sxs-lookup"><span data-stu-id="692a7-111">**1**</span></span> | <span data-ttu-id="692a7-112">En normal konsekvens kontroll.</span><span class="sxs-lookup"><span data-stu-id="692a7-112">A normal consistency check.</span></span> |
|<span data-ttu-id="692a7-113">**2**</span><span class="sxs-lookup"><span data-stu-id="692a7-113">**2**</span></span> | <span data-ttu-id="692a7-114">En fortsättning på konsekvens kontroll efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="692a7-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="692a7-115">Värdet får inte kombineras med andra värden.</span><span class="sxs-lookup"><span data-stu-id="692a7-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="692a7-116">**4**</span><span class="sxs-lookup"><span data-stu-id="692a7-116">**4**</span></span> | <span data-ttu-id="692a7-117">Konfigurationen ska hämtas från den hämtnings server som anges i metaconfiguration för noden.</span><span class="sxs-lookup"><span data-stu-id="692a7-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="692a7-118">Värdet ska alltid kombineras med **1**, för värdet **5**.</span><span class="sxs-lookup"><span data-stu-id="692a7-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="692a7-119">**8**</span><span class="sxs-lookup"><span data-stu-id="692a7-119">**8**</span></span> | <span data-ttu-id="692a7-120">Skicka status till rapport servern.</span><span class="sxs-lookup"><span data-stu-id="692a7-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="692a7-121">Returvärde</span><span class="sxs-lookup"><span data-stu-id="692a7-121">Return value</span></span>

<span data-ttu-id="692a7-122">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="692a7-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="692a7-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="692a7-123">Remarks</span></span>

<span data-ttu-id="692a7-124">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="692a7-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="692a7-125">Krav</span><span class="sxs-lookup"><span data-stu-id="692a7-125">Requirements</span></span>

<span data-ttu-id="692a7-126">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="692a7-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="692a7-127">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="692a7-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="692a7-128">Se även</span><span class="sxs-lookup"><span data-stu-id="692a7-128">See also</span></span>

[<span data-ttu-id="692a7-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="692a7-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
