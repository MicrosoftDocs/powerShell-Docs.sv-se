---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: EnableDebugConfiguration-metoden
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941588"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="23183-103">EnableDebugConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="23183-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="23183-104">Aktiverar fel sökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="23183-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="23183-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23183-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="23183-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="23183-106">Parameters</span></span>

<span data-ttu-id="23183-107">*BreakAll* \[i\] anger en Bryt punkt på varje rad i resurs skriptet.</span><span class="sxs-lookup"><span data-stu-id="23183-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="23183-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="23183-108">Return value</span></span>

<span data-ttu-id="23183-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="23183-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="23183-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="23183-110">Remarks</span></span>

<span data-ttu-id="23183-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="23183-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="23183-112">Krav</span><span class="sxs-lookup"><span data-stu-id="23183-112">Requirements</span></span>

<span data-ttu-id="23183-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="23183-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="23183-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="23183-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="23183-115">Se också</span><span class="sxs-lookup"><span data-stu-id="23183-115">See also</span></span>

[<span data-ttu-id="23183-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="23183-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
