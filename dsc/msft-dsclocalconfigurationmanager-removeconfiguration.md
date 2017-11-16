---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5dbcb-103">RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5dbcb-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5dbcb-104">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="5dbcb-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="5dbcb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5dbcb-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="5dbcb-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="5dbcb-106">Parameters</span></span>
----------

<span data-ttu-id="5dbcb-107">*Steget* \[i\]</span><span class="sxs-lookup"><span data-stu-id="5dbcb-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="5dbcb-108">Anger vilken konfiguration dokumentet ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="5dbcb-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="5dbcb-109">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="5dbcb-109">The following values are valid:</span></span>

|<span data-ttu-id="5dbcb-110">Värde</span><span class="sxs-lookup"><span data-stu-id="5dbcb-110">Value</span></span> |<span data-ttu-id="5dbcb-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5dbcb-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5dbcb-112">**1**</span><span class="sxs-lookup"><span data-stu-id="5dbcb-112">**1**</span></span> | <span data-ttu-id="5dbcb-113">Den **aktuella** configuration dokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="5dbcb-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="5dbcb-114">**2**</span><span class="sxs-lookup"><span data-stu-id="5dbcb-114">**2**</span></span> | <span data-ttu-id="5dbcb-115">Den **väntande** configuration dokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="5dbcb-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="5dbcb-116">**4**</span><span class="sxs-lookup"><span data-stu-id="5dbcb-116">**4**</span></span> | <span data-ttu-id="5dbcb-117">Den **föregående** configuration dokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="5dbcb-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="5dbcb-118">*Framtvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="5dbcb-118">*Force* \[in\]</span></span>  
<span data-ttu-id="5dbcb-119">**SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5dbcb-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5dbcb-120">Returvärde</span><span class="sxs-lookup"><span data-stu-id="5dbcb-120">Return value</span></span>
------------

<span data-ttu-id="5dbcb-121">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="5dbcb-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5dbcb-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5dbcb-122">Remarks</span></span>

<span data-ttu-id="5dbcb-123">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="5dbcb-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5dbcb-124">Krav</span><span class="sxs-lookup"><span data-stu-id="5dbcb-124">Requirements</span></span>
------------
><span data-ttu-id="5dbcb-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5dbcb-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5dbcb-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5dbcb-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5dbcb-127">Se även</span><span class="sxs-lookup"><span data-stu-id="5dbcb-127">See also</span></span>


[<span data-ttu-id="5dbcb-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5dbcb-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



