---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a0331-103">GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="a0331-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a0331-104">Hämtar Configuration Agent utdata som är associerade med ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="a0331-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="a0331-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a0331-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="a0331-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a0331-106">Parameters</span></span>
----------

<span data-ttu-id="a0331-107">*jobId* \[i\] ID för jobbet som du vill hämta utdata.</span><span class="sxs-lookup"><span data-stu-id="a0331-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="a0331-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från föregående bokmärke.</span><span class="sxs-lookup"><span data-stu-id="a0331-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="a0331-109">*utdata* \[ut\] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="a0331-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="a0331-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a0331-110">Return value</span></span>
------------

<span data-ttu-id="a0331-111">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a0331-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0331-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a0331-112">Remarks</span></span>

<span data-ttu-id="a0331-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a0331-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0331-114">Krav</span><span class="sxs-lookup"><span data-stu-id="a0331-114">Requirements</span></span>
------------
><span data-ttu-id="a0331-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a0331-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a0331-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a0331-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a0331-117">Se även</span><span class="sxs-lookup"><span data-stu-id="a0331-117">See also</span></span>


[<span data-ttu-id="a0331-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a0331-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)