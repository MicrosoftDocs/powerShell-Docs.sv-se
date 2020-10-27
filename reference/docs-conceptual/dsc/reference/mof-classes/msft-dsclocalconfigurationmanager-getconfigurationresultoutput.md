---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput-metoden
description: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644703"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="b9804-103">GetConfigurationResultOutput-metoden</span><span class="sxs-lookup"><span data-stu-id="b9804-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="b9804-104">Hämtar konfigurations agentens utdata som är associerad med ett speciellt jobb.</span><span class="sxs-lookup"><span data-stu-id="b9804-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9804-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9804-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="b9804-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b9804-106">Parameters</span></span>

<span data-ttu-id="b9804-107">**jobId** \[ i \] ID: t för det jobb för vilket utdata ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="b9804-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="b9804-108">**resumeOutputBookmark** \[ i \] anger att utdata ska vara en fortsättning från ett tidigare bok märke.</span><span class="sxs-lookup"><span data-stu-id="b9804-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="b9804-109">**utdata** \[ ut \] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="b9804-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9804-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b9804-110">Return value</span></span>

<span data-ttu-id="b9804-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="b9804-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9804-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b9804-112">Remarks</span></span>

<span data-ttu-id="b9804-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b9804-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9804-114">Krav</span><span class="sxs-lookup"><span data-stu-id="b9804-114">Requirements</span></span>

<span data-ttu-id="b9804-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="b9804-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b9804-116">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b9804-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b9804-117">Se även</span><span class="sxs-lookup"><span data-stu-id="b9804-117">See also</span></span>

[<span data-ttu-id="b9804-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b9804-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
