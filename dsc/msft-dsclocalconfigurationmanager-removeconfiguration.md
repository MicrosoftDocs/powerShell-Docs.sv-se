---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892692"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="93c0e-103">RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="93c0e-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="93c0e-104">Tar bort filerna.</span><span class="sxs-lookup"><span data-stu-id="93c0e-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="93c0e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="93c0e-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="93c0e-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="93c0e-106">Parameters</span></span>

<span data-ttu-id="93c0e-107">*Steg* \[i\] anger vilka konfigurationsdokumentet att ta bort.</span><span class="sxs-lookup"><span data-stu-id="93c0e-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="93c0e-108">Följande värden är giltiga:</span><span class="sxs-lookup"><span data-stu-id="93c0e-108">The following values are valid:</span></span>

|<span data-ttu-id="93c0e-109">Värde</span><span class="sxs-lookup"><span data-stu-id="93c0e-109">Value</span></span> |<span data-ttu-id="93c0e-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="93c0e-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="93c0e-111">**1**</span><span class="sxs-lookup"><span data-stu-id="93c0e-111">**1**</span></span> | <span data-ttu-id="93c0e-112">Den **aktuella** konfigurationsdokumentet (current.mof).</span><span class="sxs-lookup"><span data-stu-id="93c0e-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="93c0e-113">**2**</span><span class="sxs-lookup"><span data-stu-id="93c0e-113">**2**</span></span> | <span data-ttu-id="93c0e-114">Den **väntande** konfigurationsdokumentet (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="93c0e-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="93c0e-115">**4**</span><span class="sxs-lookup"><span data-stu-id="93c0e-115">**4**</span></span> | <span data-ttu-id="93c0e-116">Den **föregående** konfigurationsdokumentet (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="93c0e-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="93c0e-117">*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="93c0e-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="93c0e-118">Returvärde</span><span class="sxs-lookup"><span data-stu-id="93c0e-118">Return value</span></span>

<span data-ttu-id="93c0e-119">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="93c0e-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="93c0e-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="93c0e-120">Remarks</span></span>

<span data-ttu-id="93c0e-121">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="93c0e-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="93c0e-122">Krav</span><span class="sxs-lookup"><span data-stu-id="93c0e-122">Requirements</span></span>

<span data-ttu-id="93c0e-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="93c0e-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="93c0e-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="93c0e-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="93c0e-125">Se även</span><span class="sxs-lookup"><span data-stu-id="93c0e-125">See also</span></span>

[<span data-ttu-id="93c0e-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="93c0e-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)