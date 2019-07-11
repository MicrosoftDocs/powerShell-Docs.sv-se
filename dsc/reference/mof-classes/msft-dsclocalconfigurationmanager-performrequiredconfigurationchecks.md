---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734401"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="e6700-103">PerformRequiredConfigurationChecks-metoden</span><span class="sxs-lookup"><span data-stu-id="e6700-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="e6700-104">Startar en konsekvenskontroll med Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="e6700-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6700-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6700-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="e6700-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e6700-106">Parameters</span></span>

<span data-ttu-id="e6700-107">*Flaggor* \[i\] en bitmask som anger vilken typ av konsekvenskontroll ska köras.</span><span class="sxs-lookup"><span data-stu-id="e6700-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="e6700-108">Följande värden är giltiga och kan kombineras med hjälp av en bitvis **eller** igen:</span><span class="sxs-lookup"><span data-stu-id="e6700-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="e6700-109">Värde</span><span class="sxs-lookup"><span data-stu-id="e6700-109">Value</span></span> |<span data-ttu-id="e6700-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6700-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e6700-111">**1**</span><span class="sxs-lookup"><span data-stu-id="e6700-111">**1**</span></span> | <span data-ttu-id="e6700-112">En normal konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="e6700-112">A normal consistency check.</span></span> |
|<span data-ttu-id="e6700-113">**2**</span><span class="sxs-lookup"><span data-stu-id="e6700-113">**2**</span></span> | <span data-ttu-id="e6700-114">En förlängning av en konsekvenskontroll efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="e6700-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="e6700-115">Det här värdet får inte kombineras med andra värden.</span><span class="sxs-lookup"><span data-stu-id="e6700-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="e6700-116">**4**</span><span class="sxs-lookup"><span data-stu-id="e6700-116">**4**</span></span> | <span data-ttu-id="e6700-117">Konfigurationen ska hämtas från hämtningsservern som anges i metaconfiguration för noden.</span><span class="sxs-lookup"><span data-stu-id="e6700-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="e6700-118">Det här värdet alltid att kombineras med **1**, för ett värde för **5**.</span><span class="sxs-lookup"><span data-stu-id="e6700-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="e6700-119">**8**</span><span class="sxs-lookup"><span data-stu-id="e6700-119">**8**</span></span> | <span data-ttu-id="e6700-120">Skicka status till rapportservern.</span><span class="sxs-lookup"><span data-stu-id="e6700-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="e6700-121">Returvärde</span><span class="sxs-lookup"><span data-stu-id="e6700-121">Return value</span></span>

<span data-ttu-id="e6700-122">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="e6700-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6700-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e6700-123">Remarks</span></span>

<span data-ttu-id="e6700-124">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="e6700-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6700-125">Krav</span><span class="sxs-lookup"><span data-stu-id="e6700-125">Requirements</span></span>

<span data-ttu-id="e6700-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e6700-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e6700-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6700-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e6700-128">Se även</span><span class="sxs-lookup"><span data-stu-id="e6700-128">See also</span></span>

[<span data-ttu-id="e6700-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e6700-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
