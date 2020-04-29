---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941574"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="a72b0-103">GetConfigurationResultOutput-metoden</span><span class="sxs-lookup"><span data-stu-id="a72b0-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="a72b0-104">Hämtar konfigurations agentens utdata som är associerad med ett speciellt jobb.</span><span class="sxs-lookup"><span data-stu-id="a72b0-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="a72b0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a72b0-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="a72b0-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a72b0-106">Parameters</span></span>

<span data-ttu-id="a72b0-107">*jobId* \[i\] ID: t för det jobb som utdata ska hämtas för.</span><span class="sxs-lookup"><span data-stu-id="a72b0-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="a72b0-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från ett tidigare bok märke.</span><span class="sxs-lookup"><span data-stu-id="a72b0-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="a72b0-109">utvärderar utdata för det angivna jobbet. *output* \[\]</span><span class="sxs-lookup"><span data-stu-id="a72b0-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="a72b0-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a72b0-110">Return value</span></span>

<span data-ttu-id="a72b0-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="a72b0-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a72b0-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a72b0-112">Remarks</span></span>

<span data-ttu-id="a72b0-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a72b0-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a72b0-114">Krav</span><span class="sxs-lookup"><span data-stu-id="a72b0-114">Requirements</span></span>

<span data-ttu-id="a72b0-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="a72b0-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a72b0-116">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a72b0-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a72b0-117">Se även</span><span class="sxs-lookup"><span data-stu-id="a72b0-117">See also</span></span>

[<span data-ttu-id="a72b0-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a72b0-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
