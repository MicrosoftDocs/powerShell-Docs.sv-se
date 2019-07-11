---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727125"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="1aa5d-103">GetConfigurationResultOutput-metoden</span><span class="sxs-lookup"><span data-stu-id="1aa5d-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="1aa5d-104">Hämtar Configuration-agenten utdata som är associerade med ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="1aa5d-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="1aa5d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1aa5d-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="1aa5d-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="1aa5d-106">Parameters</span></span>

<span data-ttu-id="1aa5d-107">*jobId* \[i\] ID för jobbet som du vill hämta utdata.</span><span class="sxs-lookup"><span data-stu-id="1aa5d-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="1aa5d-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från en föregående bokmärke.</span><span class="sxs-lookup"><span data-stu-id="1aa5d-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="1aa5d-109">*utdata* \[ut\] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="1aa5d-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="1aa5d-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="1aa5d-110">Return value</span></span>

<span data-ttu-id="1aa5d-111">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="1aa5d-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1aa5d-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="1aa5d-112">Remarks</span></span>

<span data-ttu-id="1aa5d-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="1aa5d-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1aa5d-114">Krav</span><span class="sxs-lookup"><span data-stu-id="1aa5d-114">Requirements</span></span>

<span data-ttu-id="1aa5d-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1aa5d-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1aa5d-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1aa5d-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1aa5d-117">Se även</span><span class="sxs-lookup"><span data-stu-id="1aa5d-117">See also</span></span>

[<span data-ttu-id="1aa5d-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1aa5d-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
