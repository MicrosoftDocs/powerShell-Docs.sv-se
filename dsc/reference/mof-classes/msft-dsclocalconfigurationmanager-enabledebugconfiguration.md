---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: EnableDebugConfiguration-metoden
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727147"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="e7d91-103">EnableDebugConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="e7d91-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="e7d91-104">Aktiverar felsökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="e7d91-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7d91-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7d91-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="e7d91-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e7d91-106">Parameters</span></span>

<span data-ttu-id="e7d91-107">*BreakAll* \[i\] anger en brytpunkt på varje rad i resurs-skriptet.</span><span class="sxs-lookup"><span data-stu-id="e7d91-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7d91-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="e7d91-108">Return value</span></span>

<span data-ttu-id="e7d91-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="e7d91-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7d91-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e7d91-110">Remarks</span></span>

<span data-ttu-id="e7d91-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="e7d91-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7d91-112">Krav</span><span class="sxs-lookup"><span data-stu-id="e7d91-112">Requirements</span></span>

<span data-ttu-id="e7d91-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e7d91-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e7d91-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7d91-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e7d91-115">Se även</span><span class="sxs-lookup"><span data-stu-id="e7d91-115">See also</span></span>

[<span data-ttu-id="e7d91-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e7d91-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
