---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942687"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="8c57b-103">PerformRequiredConfigurationChecks-metoden</span><span class="sxs-lookup"><span data-stu-id="8c57b-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="8c57b-104">Startar en konsekvens kontroll med hjälp av Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="8c57b-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c57b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8c57b-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="8c57b-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="8c57b-106">Parameters</span></span>

<span data-ttu-id="8c57b-107">*Flaggor* \[i\] en bitmask som anger vilken typ av konsekvens kontroll som ska köras.</span><span class="sxs-lookup"><span data-stu-id="8c57b-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="8c57b-108">Följande värden är giltiga och kan kombineras med hjälp av en bitvis **or** -åtgärd:</span><span class="sxs-lookup"><span data-stu-id="8c57b-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="8c57b-109">Värde</span><span class="sxs-lookup"><span data-stu-id="8c57b-109">Value</span></span> |<span data-ttu-id="8c57b-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8c57b-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="8c57b-111">**1**</span><span class="sxs-lookup"><span data-stu-id="8c57b-111">**1**</span></span> | <span data-ttu-id="8c57b-112">En normal konsekvens kontroll.</span><span class="sxs-lookup"><span data-stu-id="8c57b-112">A normal consistency check.</span></span> |
|<span data-ttu-id="8c57b-113">**2**</span><span class="sxs-lookup"><span data-stu-id="8c57b-113">**2**</span></span> | <span data-ttu-id="8c57b-114">En fortsättning på konsekvens kontroll efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="8c57b-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="8c57b-115">Värdet får inte kombineras med andra värden.</span><span class="sxs-lookup"><span data-stu-id="8c57b-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="8c57b-116">**4**</span><span class="sxs-lookup"><span data-stu-id="8c57b-116">**4**</span></span> | <span data-ttu-id="8c57b-117">Konfigurationen ska hämtas från den hämtnings server som anges i metaconfiguration för noden.</span><span class="sxs-lookup"><span data-stu-id="8c57b-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="8c57b-118">Värdet ska alltid kombineras med **1**, för värdet **5**.</span><span class="sxs-lookup"><span data-stu-id="8c57b-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="8c57b-119">**8**</span><span class="sxs-lookup"><span data-stu-id="8c57b-119">**8**</span></span> | <span data-ttu-id="8c57b-120">Skicka status till rapport servern.</span><span class="sxs-lookup"><span data-stu-id="8c57b-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="8c57b-121">Returvärde</span><span class="sxs-lookup"><span data-stu-id="8c57b-121">Return value</span></span>

<span data-ttu-id="8c57b-122">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="8c57b-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c57b-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8c57b-123">Remarks</span></span>

<span data-ttu-id="8c57b-124">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="8c57b-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c57b-125">Krav</span><span class="sxs-lookup"><span data-stu-id="8c57b-125">Requirements</span></span>

<span data-ttu-id="8c57b-126">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="8c57b-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8c57b-127">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c57b-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8c57b-128">Se även</span><span class="sxs-lookup"><span data-stu-id="8c57b-128">See also</span></span>

[<span data-ttu-id="8c57b-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8c57b-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
