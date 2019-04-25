---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078698"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ad705-103">RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="ad705-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ad705-104">Tar bort filerna.</span><span class="sxs-lookup"><span data-stu-id="ad705-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad705-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad705-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="ad705-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ad705-106">Parameters</span></span>

<span data-ttu-id="ad705-107">*Steg* \[i\] anger vilka konfigurationsdokumentet att ta bort.</span><span class="sxs-lookup"><span data-stu-id="ad705-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="ad705-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="ad705-108">The following values are valid:</span></span>

|<span data-ttu-id="ad705-109">Värde</span><span class="sxs-lookup"><span data-stu-id="ad705-109">Value</span></span> |<span data-ttu-id="ad705-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ad705-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="ad705-111">**1**</span><span class="sxs-lookup"><span data-stu-id="ad705-111">**1**</span></span> | <span data-ttu-id="ad705-112">Den **aktuella** konfigurationsdokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="ad705-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="ad705-113">**2**</span><span class="sxs-lookup"><span data-stu-id="ad705-113">**2**</span></span> | <span data-ttu-id="ad705-114">Den **väntande** konfigurationsdokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="ad705-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="ad705-115">**4**</span><span class="sxs-lookup"><span data-stu-id="ad705-115">**4**</span></span> | <span data-ttu-id="ad705-116">Den **föregående** konfigurationsdokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="ad705-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="ad705-117">*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ad705-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad705-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ad705-118">Return value</span></span>

<span data-ttu-id="ad705-119">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="ad705-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad705-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ad705-120">Remarks</span></span>

<span data-ttu-id="ad705-121">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ad705-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad705-122">Krav</span><span class="sxs-lookup"><span data-stu-id="ad705-122">Requirements</span></span>

<span data-ttu-id="ad705-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ad705-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ad705-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ad705-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ad705-125">Se även</span><span class="sxs-lookup"><span data-stu-id="ad705-125">See also</span></span>

[<span data-ttu-id="ad705-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ad705-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)