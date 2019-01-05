---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048650"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ee471-103">GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="ee471-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ee471-104">Hämtar Configuration-agenten utdata som är associerade med ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="ee471-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee471-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee471-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="ee471-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ee471-106">Parameters</span></span>

<span data-ttu-id="ee471-107">*jobId* \[i\] ID för jobbet som du vill hämta utdata.</span><span class="sxs-lookup"><span data-stu-id="ee471-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="ee471-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från en föregående bokmärke.</span><span class="sxs-lookup"><span data-stu-id="ee471-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="ee471-109">*utdata* \[ut\] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="ee471-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee471-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ee471-110">Return value</span></span>

<span data-ttu-id="ee471-111">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="ee471-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee471-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ee471-112">Remarks</span></span>

<span data-ttu-id="ee471-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ee471-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee471-114">Krav</span><span class="sxs-lookup"><span data-stu-id="ee471-114">Requirements</span></span>

<span data-ttu-id="ee471-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ee471-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ee471-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee471-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ee471-117">Se även</span><span class="sxs-lookup"><span data-stu-id="ee471-117">See also</span></span>

[<span data-ttu-id="ee471-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ee471-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)