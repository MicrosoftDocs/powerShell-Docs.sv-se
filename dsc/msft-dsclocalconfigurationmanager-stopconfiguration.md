---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d0e44-103">StopConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="d0e44-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d0e44-104">Stoppar konfigurationsändringen som pågår.</span><span class="sxs-lookup"><span data-stu-id="d0e44-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="d0e44-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0e44-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d0e44-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d0e44-106">Parameters</span></span>
----------

<span data-ttu-id="d0e44-107">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="d0e44-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d0e44-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d0e44-108">Return value</span></span>
------------

<span data-ttu-id="d0e44-109">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d0e44-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0e44-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d0e44-110">Remarks</span></span>

<span data-ttu-id="d0e44-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d0e44-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0e44-112">Krav</span><span class="sxs-lookup"><span data-stu-id="d0e44-112">Requirements</span></span>
------------
><span data-ttu-id="d0e44-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d0e44-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d0e44-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d0e44-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d0e44-115">Se även</span><span class="sxs-lookup"><span data-stu-id="d0e44-115">See also</span></span>


[<span data-ttu-id="d0e44-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d0e44-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)