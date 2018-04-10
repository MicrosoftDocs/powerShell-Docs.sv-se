---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79dd2-103">RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="79dd2-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79dd2-104">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="79dd2-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="79dd2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="79dd2-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="79dd2-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="79dd2-106">Parameters</span></span>
----------

<span data-ttu-id="79dd2-107">*Steget* \[i\] anger vilken konfiguration dokumentet ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="79dd2-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="79dd2-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="79dd2-108">The following values are valid:</span></span>

|<span data-ttu-id="79dd2-109">Värde</span><span class="sxs-lookup"><span data-stu-id="79dd2-109">Value</span></span> |<span data-ttu-id="79dd2-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="79dd2-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="79dd2-111">**1**</span><span class="sxs-lookup"><span data-stu-id="79dd2-111">**1**</span></span> | <span data-ttu-id="79dd2-112">Den **aktuella** configuration dokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="79dd2-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="79dd2-113">**2**</span><span class="sxs-lookup"><span data-stu-id="79dd2-113">**2**</span></span> | <span data-ttu-id="79dd2-114">Den **väntande** configuration dokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="79dd2-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="79dd2-115">**4**</span><span class="sxs-lookup"><span data-stu-id="79dd2-115">**4**</span></span> | <span data-ttu-id="79dd2-116">Den **föregående** configuration dokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="79dd2-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="79dd2-117">*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="79dd2-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="79dd2-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="79dd2-118">Return value</span></span>
------------

<span data-ttu-id="79dd2-119">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="79dd2-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="79dd2-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="79dd2-120">Remarks</span></span>

<span data-ttu-id="79dd2-121">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="79dd2-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79dd2-122">Krav</span><span class="sxs-lookup"><span data-stu-id="79dd2-122">Requirements</span></span>
------------
><span data-ttu-id="79dd2-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79dd2-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="79dd2-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79dd2-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="79dd2-125">Se även</span><span class="sxs-lookup"><span data-stu-id="79dd2-125">See also</span></span>


[<span data-ttu-id="79dd2-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="79dd2-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)