---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fa0c3-103">RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fa0c3-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fa0c3-104">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="fa0c3-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="fa0c3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fa0c3-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="fa0c3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="fa0c3-106">Parameters</span></span>
----------

<span data-ttu-id="fa0c3-107">*Steget* \[i\]</span><span class="sxs-lookup"><span data-stu-id="fa0c3-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="fa0c3-108">Anger vilken konfiguration dokumentet ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="fa0c3-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="fa0c3-109">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="fa0c3-109">The following values are valid:</span></span>

|<span data-ttu-id="fa0c3-110">Värde</span><span class="sxs-lookup"><span data-stu-id="fa0c3-110">Value</span></span> |<span data-ttu-id="fa0c3-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fa0c3-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="fa0c3-112">**1**</span><span class="sxs-lookup"><span data-stu-id="fa0c3-112">**1**</span></span> | <span data-ttu-id="fa0c3-113">Den **aktuella** configuration dokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="fa0c3-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="fa0c3-114">**2**</span><span class="sxs-lookup"><span data-stu-id="fa0c3-114">**2**</span></span> | <span data-ttu-id="fa0c3-115">Den **väntande** configuration dokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="fa0c3-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="fa0c3-116">**4**</span><span class="sxs-lookup"><span data-stu-id="fa0c3-116">**4**</span></span> | <span data-ttu-id="fa0c3-117">Den **föregående** configuration dokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="fa0c3-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="fa0c3-118">*Framtvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="fa0c3-118">*Force* \[in\]</span></span>  
<span data-ttu-id="fa0c3-119">**SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fa0c3-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fa0c3-120">Returvärde</span><span class="sxs-lookup"><span data-stu-id="fa0c3-120">Return value</span></span>
------------

<span data-ttu-id="fa0c3-121">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="fa0c3-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa0c3-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fa0c3-122">Remarks</span></span>

<span data-ttu-id="fa0c3-123">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="fa0c3-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fa0c3-124">Krav</span><span class="sxs-lookup"><span data-stu-id="fa0c3-124">Requirements</span></span>
------------
><span data-ttu-id="fa0c3-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fa0c3-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fa0c3-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa0c3-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fa0c3-127">Se även</span><span class="sxs-lookup"><span data-stu-id="fa0c3-127">See also</span></span>


[<span data-ttu-id="fa0c3-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fa0c3-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



