---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a82db-103">PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="a82db-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a82db-104">Startar en konsekvenskontroll med Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="a82db-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="a82db-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a82db-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="a82db-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a82db-106">Parameters</span></span>
----------

<span data-ttu-id="a82db-107">*Flaggorna* \[i\] en bitmask som anger vilken typ av kontroll av att köra.</span><span class="sxs-lookup"><span data-stu-id="a82db-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="a82db-108">Följande värden är giltiga och kan kombineras med hjälp av en bitvis **eller** igen:</span><span class="sxs-lookup"><span data-stu-id="a82db-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="a82db-109">Värde</span><span class="sxs-lookup"><span data-stu-id="a82db-109">Value</span></span> |<span data-ttu-id="a82db-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a82db-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="a82db-111">**1**</span><span class="sxs-lookup"><span data-stu-id="a82db-111">**1**</span></span> | <span data-ttu-id="a82db-112">En normal konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="a82db-112">A normal consistency check.</span></span> |
|<span data-ttu-id="a82db-113">**2**</span><span class="sxs-lookup"><span data-stu-id="a82db-113">**2**</span></span> | <span data-ttu-id="a82db-114">En förlängning av en konsekvenskontroll efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="a82db-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="a82db-115">Det här värdet får inte kombineras med andra värden.</span><span class="sxs-lookup"><span data-stu-id="a82db-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="a82db-116">**4**</span><span class="sxs-lookup"><span data-stu-id="a82db-116">**4**</span></span> | <span data-ttu-id="a82db-117">Konfigurationen ska dras från hämtningsservern som anges i metakonfigurationen för noden.</span><span class="sxs-lookup"><span data-stu-id="a82db-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="a82db-118">Det här värdet alltid ska kombineras med **1**, för ett värde för **5**.</span><span class="sxs-lookup"><span data-stu-id="a82db-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="a82db-119">**8**</span><span class="sxs-lookup"><span data-stu-id="a82db-119">**8**</span></span> | <span data-ttu-id="a82db-120">Skicka status till rapportservern.</span><span class="sxs-lookup"><span data-stu-id="a82db-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="a82db-121">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a82db-121">Return value</span></span>
------------

<span data-ttu-id="a82db-122">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a82db-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a82db-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a82db-123">Remarks</span></span>

<span data-ttu-id="a82db-124">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a82db-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a82db-125">Krav</span><span class="sxs-lookup"><span data-stu-id="a82db-125">Requirements</span></span>
------------
><span data-ttu-id="a82db-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a82db-126">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a82db-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a82db-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a82db-128">Se även</span><span class="sxs-lookup"><span data-stu-id="a82db-128">See also</span></span>


[<span data-ttu-id="a82db-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a82db-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)