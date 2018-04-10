---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="093c0-103">EnableDebugConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="093c0-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="093c0-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="093c0-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="093c0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="093c0-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="093c0-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="093c0-106">Parameters</span></span>
----------

<span data-ttu-id="093c0-107">*BreakAll* \[i\] anger en brytpunkt på varje rad i skriptet resurs.</span><span class="sxs-lookup"><span data-stu-id="093c0-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="093c0-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="093c0-108">Return value</span></span>
------------

<span data-ttu-id="093c0-109">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="093c0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="093c0-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="093c0-110">Remarks</span></span>

<span data-ttu-id="093c0-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="093c0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="093c0-112">Krav</span><span class="sxs-lookup"><span data-stu-id="093c0-112">Requirements</span></span>
------------
><span data-ttu-id="093c0-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="093c0-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="093c0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="093c0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="093c0-115">Se även</span><span class="sxs-lookup"><span data-stu-id="093c0-115">See also</span></span>


[<span data-ttu-id="093c0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="093c0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)