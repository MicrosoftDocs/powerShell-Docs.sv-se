---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: EnableDebugConfiguration-metoden
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464102"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="3ab55-103">EnableDebugConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="3ab55-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="3ab55-104">Aktiverar fel sökning av DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="3ab55-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ab55-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ab55-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="3ab55-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3ab55-106">Parameters</span></span>

<span data-ttu-id="3ab55-107">**BreakAll** \[ i \] anger en Bryt punkt på varje rad i resurs skriptet.</span><span class="sxs-lookup"><span data-stu-id="3ab55-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ab55-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="3ab55-108">Return value</span></span>

<span data-ttu-id="3ab55-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="3ab55-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ab55-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3ab55-110">Remarks</span></span>

<span data-ttu-id="3ab55-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="3ab55-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ab55-112">Krav</span><span class="sxs-lookup"><span data-stu-id="3ab55-112">Requirements</span></span>

<span data-ttu-id="3ab55-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3ab55-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3ab55-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ab55-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3ab55-115">Se även</span><span class="sxs-lookup"><span data-stu-id="3ab55-115">See also</span></span>

[<span data-ttu-id="3ab55-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ab55-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
