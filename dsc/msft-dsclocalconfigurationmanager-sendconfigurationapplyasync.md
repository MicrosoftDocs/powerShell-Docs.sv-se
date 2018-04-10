---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fca6b-103">SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="fca6b-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fca6b-104">Skickar konfiguration dokumentet asynkront till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fca6b-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="fca6b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fca6b-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="fca6b-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="fca6b-106">Parameters</span></span>
----------

<span data-ttu-id="fca6b-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fca6b-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fca6b-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="fca6b-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="fca6b-109">*jobId* \[i\] ID för jobbet för att skicka konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="fca6b-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="fca6b-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="fca6b-110">Return value</span></span>
------------

<span data-ttu-id="fca6b-111">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="fca6b-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fca6b-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fca6b-112">Remarks</span></span>

<span data-ttu-id="fca6b-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="fca6b-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fca6b-114">Krav</span><span class="sxs-lookup"><span data-stu-id="fca6b-114">Requirements</span></span>
------------
><span data-ttu-id="fca6b-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fca6b-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fca6b-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fca6b-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fca6b-117">Se även</span><span class="sxs-lookup"><span data-stu-id="fca6b-117">See also</span></span>


[<span data-ttu-id="fca6b-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fca6b-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)