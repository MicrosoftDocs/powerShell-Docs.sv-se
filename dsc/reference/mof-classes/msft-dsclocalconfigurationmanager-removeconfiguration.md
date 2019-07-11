---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734396"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="4a113-103">RemoveConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="4a113-103">RemoveConfiguration method</span></span>

<span data-ttu-id="4a113-104">Tar bort filerna.</span><span class="sxs-lookup"><span data-stu-id="4a113-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a113-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a113-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="4a113-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="4a113-106">Parameters</span></span>

<span data-ttu-id="4a113-107">*Steg* \[i\] anger vilka konfigurationsdokumentet att ta bort.</span><span class="sxs-lookup"><span data-stu-id="4a113-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="4a113-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="4a113-108">The following values are valid:</span></span>

|<span data-ttu-id="4a113-109">Värde</span><span class="sxs-lookup"><span data-stu-id="4a113-109">Value</span></span> |<span data-ttu-id="4a113-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4a113-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="4a113-111">**1**</span><span class="sxs-lookup"><span data-stu-id="4a113-111">**1**</span></span> | <span data-ttu-id="4a113-112">Den **aktuella** konfigurationsdokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="4a113-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="4a113-113">**2**</span><span class="sxs-lookup"><span data-stu-id="4a113-113">**2**</span></span> | <span data-ttu-id="4a113-114">Den **väntande** konfigurationsdokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="4a113-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="4a113-115">**4**</span><span class="sxs-lookup"><span data-stu-id="4a113-115">**4**</span></span> | <span data-ttu-id="4a113-116">Den **föregående** konfigurationsdokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="4a113-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="4a113-117">*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4a113-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a113-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="4a113-118">Return value</span></span>

<span data-ttu-id="4a113-119">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="4a113-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4a113-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4a113-120">Remarks</span></span>

<span data-ttu-id="4a113-121">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="4a113-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4a113-122">Krav</span><span class="sxs-lookup"><span data-stu-id="4a113-122">Requirements</span></span>

<span data-ttu-id="4a113-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4a113-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4a113-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a113-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4a113-125">Se även</span><span class="sxs-lookup"><span data-stu-id="4a113-125">See also</span></span>

[<span data-ttu-id="4a113-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4a113-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
