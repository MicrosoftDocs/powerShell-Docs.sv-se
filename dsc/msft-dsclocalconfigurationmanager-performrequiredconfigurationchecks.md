---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7f675-103">PerformRequiredConfigurationChecks-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7f675-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7f675-104">Startar en konsekvenskontroll med Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="7f675-104">Starts a consistency check by using the Task Scheduler.</span></span>

<a name="syntax"></a><span data-ttu-id="7f675-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f675-105">Syntax</span></span>
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a><span data-ttu-id="7f675-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7f675-106">Parameters</span></span>
----------

<span data-ttu-id="7f675-107">*Flaggorna* \[i\]</span><span class="sxs-lookup"><span data-stu-id="7f675-107">*Flags* \[in\]</span></span>  
<span data-ttu-id="7f675-108">En bitmask som anger vilken typ av kontroll av att köra.</span><span class="sxs-lookup"><span data-stu-id="7f675-108">A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="7f675-109">Följande värden är giltiga och kan kombineras med hjälp av en bitvis **eller** igen:</span><span class="sxs-lookup"><span data-stu-id="7f675-109">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="7f675-110">Värde</span><span class="sxs-lookup"><span data-stu-id="7f675-110">Value</span></span> |<span data-ttu-id="7f675-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7f675-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="7f675-112">**1**</span><span class="sxs-lookup"><span data-stu-id="7f675-112">**1**</span></span> | <span data-ttu-id="7f675-113">En normal konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="7f675-113">A normal consistency check.</span></span> |
|<span data-ttu-id="7f675-114">**2**</span><span class="sxs-lookup"><span data-stu-id="7f675-114">**2**</span></span> | <span data-ttu-id="7f675-115">En förlängning av en konsekvenskontroll efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="7f675-115">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="7f675-116">Det här värdet får inte kombineras med andra värden.</span><span class="sxs-lookup"><span data-stu-id="7f675-116">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="7f675-117">**4**</span><span class="sxs-lookup"><span data-stu-id="7f675-117">**4**</span></span> | <span data-ttu-id="7f675-118">Konfigurationen ska dras från hämtningsservern som anges i metakonfigurationen för noden.</span><span class="sxs-lookup"><span data-stu-id="7f675-118">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="7f675-119">Det här värdet alltid ska kombineras med **1**, för ett värde för **5**.</span><span class="sxs-lookup"><span data-stu-id="7f675-119">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="7f675-120">**8**</span><span class="sxs-lookup"><span data-stu-id="7f675-120">**8**</span></span> | <span data-ttu-id="7f675-121">Skicka status till rapportservern.</span><span class="sxs-lookup"><span data-stu-id="7f675-121">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="7f675-122">Returvärde</span><span class="sxs-lookup"><span data-stu-id="7f675-122">Return value</span></span>
------------

<span data-ttu-id="7f675-123">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="7f675-123">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7f675-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7f675-124">Remarks</span></span>

<span data-ttu-id="7f675-125">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="7f675-125">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7f675-126">Krav</span><span class="sxs-lookup"><span data-stu-id="7f675-126">Requirements</span></span>
------------
><span data-ttu-id="7f675-127">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7f675-127">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7f675-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7f675-128">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7f675-129">Se även</span><span class="sxs-lookup"><span data-stu-id="7f675-129">See also</span></span>


[<span data-ttu-id="7f675-130">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7f675-130">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



