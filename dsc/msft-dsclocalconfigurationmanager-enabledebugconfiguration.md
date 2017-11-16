---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7b399-103">EnableDebugConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7b399-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7b399-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="7b399-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="7b399-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b399-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="7b399-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7b399-106">Parameters</span></span>
----------

<span data-ttu-id="7b399-107">*BreakAll* \[i\]</span><span class="sxs-lookup"><span data-stu-id="7b399-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="7b399-108">Anger en brytpunkt på varje rad i skriptet resurs.</span><span class="sxs-lookup"><span data-stu-id="7b399-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b399-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="7b399-109">Return value</span></span>
------------

<span data-ttu-id="7b399-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="7b399-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b399-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7b399-111">Remarks</span></span>

<span data-ttu-id="7b399-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="7b399-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b399-113">Krav</span><span class="sxs-lookup"><span data-stu-id="7b399-113">Requirements</span></span>
------------
><span data-ttu-id="7b399-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7b399-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7b399-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7b399-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7b399-116">Se även</span><span class="sxs-lookup"><span data-stu-id="7b399-116">See also</span></span>


[<span data-ttu-id="7b399-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7b399-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



