---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ba7fe-103">EnableDebugConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ba7fe-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ba7fe-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="ba7fe-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="ba7fe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ba7fe-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="ba7fe-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ba7fe-106">Parameters</span></span>
----------

<span data-ttu-id="ba7fe-107">*BreakAll* \[i\]</span><span class="sxs-lookup"><span data-stu-id="ba7fe-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="ba7fe-108">Anger en brytpunkt på varje rad i skriptet resurs.</span><span class="sxs-lookup"><span data-stu-id="ba7fe-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba7fe-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ba7fe-109">Return value</span></span>
------------

<span data-ttu-id="ba7fe-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="ba7fe-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba7fe-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ba7fe-111">Remarks</span></span>

<span data-ttu-id="ba7fe-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ba7fe-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba7fe-113">Krav</span><span class="sxs-lookup"><span data-stu-id="ba7fe-113">Requirements</span></span>
------------
><span data-ttu-id="ba7fe-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ba7fe-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ba7fe-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ba7fe-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ba7fe-116">Se även</span><span class="sxs-lookup"><span data-stu-id="ba7fe-116">See also</span></span>


[<span data-ttu-id="ba7fe-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ba7fe-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



