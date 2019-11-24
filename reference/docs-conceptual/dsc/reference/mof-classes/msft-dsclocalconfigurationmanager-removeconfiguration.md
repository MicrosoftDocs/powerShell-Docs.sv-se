---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: RemoveConfiguration-metoden
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941560"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="490b1-103">RemoveConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="490b1-103">RemoveConfiguration method</span></span>

<span data-ttu-id="490b1-104">Tar bort konfigurationsfilerna.</span><span class="sxs-lookup"><span data-stu-id="490b1-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="490b1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="490b1-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="490b1-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="490b1-106">Parameters</span></span>

<span data-ttu-id="490b1-107">*Steg* \[i\] anger vilket konfigurations dokument som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="490b1-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="490b1-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="490b1-108">The following values are valid:</span></span>

|<span data-ttu-id="490b1-109">Värde</span><span class="sxs-lookup"><span data-stu-id="490b1-109">Value</span></span> |<span data-ttu-id="490b1-110">Description</span><span class="sxs-lookup"><span data-stu-id="490b1-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="490b1-111">**1**</span><span class="sxs-lookup"><span data-stu-id="490b1-111">**1**</span></span> | <span data-ttu-id="490b1-112">**Aktuellt** konfigurations dokument (aktuell. MOF).</span><span class="sxs-lookup"><span data-stu-id="490b1-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="490b1-113">**2**</span><span class="sxs-lookup"><span data-stu-id="490b1-113">**2**</span></span> | <span data-ttu-id="490b1-114">**Väntande** konfigurations dokument (väntar. MOF).</span><span class="sxs-lookup"><span data-stu-id="490b1-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="490b1-115">**4**</span><span class="sxs-lookup"><span data-stu-id="490b1-115">**4**</span></span> | <span data-ttu-id="490b1-116">**Föregående** konfigurations dokument (föregående. MOF).</span><span class="sxs-lookup"><span data-stu-id="490b1-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="490b1-117">*Tvinga* \[i\] **True** att framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="490b1-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="490b1-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="490b1-118">Return value</span></span>

<span data-ttu-id="490b1-119">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="490b1-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="490b1-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="490b1-120">Remarks</span></span>

<span data-ttu-id="490b1-121">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="490b1-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="490b1-122">Krav</span><span class="sxs-lookup"><span data-stu-id="490b1-122">Requirements</span></span>

<span data-ttu-id="490b1-123">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="490b1-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="490b1-124">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="490b1-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="490b1-125">Se också</span><span class="sxs-lookup"><span data-stu-id="490b1-125">See also</span></span>

[<span data-ttu-id="490b1-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="490b1-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
