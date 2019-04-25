---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078444"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="df0a4-103">PerformRequiredConfigurationChecks-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="df0a4-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="df0a4-104">Startar en konsekvenskontroll med Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="df0a4-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="df0a4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="df0a4-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="df0a4-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="df0a4-106">Parameters</span></span>

<span data-ttu-id="df0a4-107">*Flaggor* \[i\] en bitmask som anger vilken typ av konsekvenskontroll ska köras.</span><span class="sxs-lookup"><span data-stu-id="df0a4-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="df0a4-108">Följande värden är giltiga och kan kombineras med hjälp av en bitvis **eller** igen:</span><span class="sxs-lookup"><span data-stu-id="df0a4-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="df0a4-109">Värde</span><span class="sxs-lookup"><span data-stu-id="df0a4-109">Value</span></span> |<span data-ttu-id="df0a4-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="df0a4-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="df0a4-111">**1**</span><span class="sxs-lookup"><span data-stu-id="df0a4-111">**1**</span></span> | <span data-ttu-id="df0a4-112">En normal konsekvenskontroll.</span><span class="sxs-lookup"><span data-stu-id="df0a4-112">A normal consistency check.</span></span> |
|<span data-ttu-id="df0a4-113">**2**</span><span class="sxs-lookup"><span data-stu-id="df0a4-113">**2**</span></span> | <span data-ttu-id="df0a4-114">En förlängning av en konsekvenskontroll efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="df0a4-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="df0a4-115">Det här värdet får inte kombineras med andra värden.</span><span class="sxs-lookup"><span data-stu-id="df0a4-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="df0a4-116">**4**</span><span class="sxs-lookup"><span data-stu-id="df0a4-116">**4**</span></span> | <span data-ttu-id="df0a4-117">Konfigurationen ska hämtas från hämtningsservern som anges i metaconfiguration för noden.</span><span class="sxs-lookup"><span data-stu-id="df0a4-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="df0a4-118">Det här värdet alltid att kombineras med **1**, för ett värde för **5**.</span><span class="sxs-lookup"><span data-stu-id="df0a4-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="df0a4-119">**8**</span><span class="sxs-lookup"><span data-stu-id="df0a4-119">**8**</span></span> | <span data-ttu-id="df0a4-120">Skicka status till rapportservern.</span><span class="sxs-lookup"><span data-stu-id="df0a4-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="df0a4-121">Returvärde</span><span class="sxs-lookup"><span data-stu-id="df0a4-121">Return value</span></span>

<span data-ttu-id="df0a4-122">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="df0a4-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="df0a4-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="df0a4-123">Remarks</span></span>

<span data-ttu-id="df0a4-124">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="df0a4-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="df0a4-125">Krav</span><span class="sxs-lookup"><span data-stu-id="df0a4-125">Requirements</span></span>

<span data-ttu-id="df0a4-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="df0a4-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="df0a4-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="df0a4-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="df0a4-128">Se även</span><span class="sxs-lookup"><span data-stu-id="df0a4-128">See also</span></span>

[<span data-ttu-id="df0a4-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="df0a4-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)