---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218883"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="94d00-103">StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="94d00-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="94d00-104">Stoppar konfigurationsändringen som pågår.</span><span class="sxs-lookup"><span data-stu-id="94d00-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="94d00-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="94d00-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="94d00-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="94d00-106">Parameters</span></span>
----------

<span data-ttu-id="94d00-107">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="94d00-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="94d00-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="94d00-108">Return value</span></span>
------------

<span data-ttu-id="94d00-109">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="94d00-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="94d00-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="94d00-110">Remarks</span></span>

<span data-ttu-id="94d00-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="94d00-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94d00-112">Krav</span><span class="sxs-lookup"><span data-stu-id="94d00-112">Requirements</span></span>
------------
><span data-ttu-id="94d00-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="94d00-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="94d00-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="94d00-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="94d00-115">Se även</span><span class="sxs-lookup"><span data-stu-id="94d00-115">See also</span></span>


[<span data-ttu-id="94d00-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="94d00-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)