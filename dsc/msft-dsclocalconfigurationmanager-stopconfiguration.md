---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893883"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9ef55-103">StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="9ef55-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9ef55-104">Stoppar konfigurationsändring som håller på att skapas.</span><span class="sxs-lookup"><span data-stu-id="9ef55-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ef55-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ef55-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9ef55-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9ef55-106">Parameters</span></span>

<span data-ttu-id="9ef55-107">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="9ef55-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ef55-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="9ef55-108">Return value</span></span>

<span data-ttu-id="9ef55-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="9ef55-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ef55-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9ef55-110">Remarks</span></span>

<span data-ttu-id="9ef55-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="9ef55-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ef55-112">Krav</span><span class="sxs-lookup"><span data-stu-id="9ef55-112">Requirements</span></span>

<span data-ttu-id="9ef55-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9ef55-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9ef55-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9ef55-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9ef55-115">Se även</span><span class="sxs-lookup"><span data-stu-id="9ef55-115">See also</span></span>

[<span data-ttu-id="9ef55-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9ef55-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)