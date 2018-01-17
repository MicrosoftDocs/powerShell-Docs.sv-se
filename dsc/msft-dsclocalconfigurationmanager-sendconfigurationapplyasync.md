---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="99fff-103">SendConfigurationApplyAsync-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="99fff-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="99fff-104">Skickar konfiguration dokumentet asynkront till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="99fff-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="99fff-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="99fff-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="99fff-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="99fff-106">Parameters</span></span>
----------

<span data-ttu-id="99fff-107">*ConfigurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="99fff-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="99fff-108">Miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="99fff-108">The environment data for the configuration.</span></span>

<span data-ttu-id="99fff-109">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="99fff-109">*force* \[in\]</span></span>  
<span data-ttu-id="99fff-110">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="99fff-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="99fff-111">*jobId* \[i\]</span><span class="sxs-lookup"><span data-stu-id="99fff-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="99fff-112">ID för jobbet för att skicka konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="99fff-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="99fff-113">Returvärde</span><span class="sxs-lookup"><span data-stu-id="99fff-113">Return value</span></span>
------------

<span data-ttu-id="99fff-114">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="99fff-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="99fff-115">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="99fff-115">Remarks</span></span>

<span data-ttu-id="99fff-116">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="99fff-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="99fff-117">Krav</span><span class="sxs-lookup"><span data-stu-id="99fff-117">Requirements</span></span>
------------
><span data-ttu-id="99fff-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="99fff-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="99fff-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="99fff-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="99fff-120">Se även</span><span class="sxs-lookup"><span data-stu-id="99fff-120">See also</span></span>


[<span data-ttu-id="99fff-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="99fff-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



