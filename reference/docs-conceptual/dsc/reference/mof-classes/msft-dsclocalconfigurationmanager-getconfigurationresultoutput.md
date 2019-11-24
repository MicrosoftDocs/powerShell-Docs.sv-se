---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941574"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="2fc68-103">GetConfigurationResultOutput-metoden</span><span class="sxs-lookup"><span data-stu-id="2fc68-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="2fc68-104">Hämtar konfigurations agentens utdata som är associerad med ett speciellt jobb.</span><span class="sxs-lookup"><span data-stu-id="2fc68-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fc68-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fc68-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="2fc68-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2fc68-106">Parameters</span></span>

<span data-ttu-id="2fc68-107">*jobId* \[i\] ID: t för det jobb som utdata ska hämtas till.</span><span class="sxs-lookup"><span data-stu-id="2fc68-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="2fc68-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från ett tidigare bok märke.</span><span class="sxs-lookup"><span data-stu-id="2fc68-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="2fc68-109">*utdata* \[ut\] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="2fc68-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="2fc68-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="2fc68-110">Return value</span></span>

<span data-ttu-id="2fc68-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="2fc68-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fc68-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2fc68-112">Remarks</span></span>

<span data-ttu-id="2fc68-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="2fc68-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2fc68-114">Krav</span><span class="sxs-lookup"><span data-stu-id="2fc68-114">Requirements</span></span>

<span data-ttu-id="2fc68-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="2fc68-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2fc68-116">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2fc68-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2fc68-117">Se också</span><span class="sxs-lookup"><span data-stu-id="2fc68-117">See also</span></span>

[<span data-ttu-id="2fc68-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2fc68-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
