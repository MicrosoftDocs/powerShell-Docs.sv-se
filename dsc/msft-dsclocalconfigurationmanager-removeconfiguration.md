---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189745"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="303b5-103">RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="303b5-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="303b5-104">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="303b5-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="303b5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="303b5-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="303b5-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="303b5-106">Parameters</span></span>
----------

<span data-ttu-id="303b5-107">*Steget* \[i\] anger vilken konfiguration dokumentet ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="303b5-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="303b5-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="303b5-108">The following values are valid:</span></span>

|<span data-ttu-id="303b5-109">Värde</span><span class="sxs-lookup"><span data-stu-id="303b5-109">Value</span></span> |<span data-ttu-id="303b5-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="303b5-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="303b5-111">**1**</span><span class="sxs-lookup"><span data-stu-id="303b5-111">**1**</span></span> | <span data-ttu-id="303b5-112">Den **aktuella** configuration dokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="303b5-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="303b5-113">**2**</span><span class="sxs-lookup"><span data-stu-id="303b5-113">**2**</span></span> | <span data-ttu-id="303b5-114">Den **väntande** configuration dokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="303b5-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="303b5-115">**4**</span><span class="sxs-lookup"><span data-stu-id="303b5-115">**4**</span></span> | <span data-ttu-id="303b5-116">Den **föregående** configuration dokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="303b5-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="303b5-117">*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="303b5-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="303b5-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="303b5-118">Return value</span></span>
------------

<span data-ttu-id="303b5-119">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="303b5-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="303b5-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="303b5-120">Remarks</span></span>

<span data-ttu-id="303b5-121">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="303b5-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="303b5-122">Krav</span><span class="sxs-lookup"><span data-stu-id="303b5-122">Requirements</span></span>
------------
><span data-ttu-id="303b5-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="303b5-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="303b5-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="303b5-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="303b5-125">Se även</span><span class="sxs-lookup"><span data-stu-id="303b5-125">See also</span></span>


[<span data-ttu-id="303b5-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="303b5-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)