---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ff14a-103">GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="ff14a-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ff14a-104">Hämtar Configuration Agent utdata som är associerade med ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="ff14a-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="ff14a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff14a-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="ff14a-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ff14a-106">Parameters</span></span>
----------

<span data-ttu-id="ff14a-107">*jobId* \[i\] ID för jobbet som du vill hämta utdata.</span><span class="sxs-lookup"><span data-stu-id="ff14a-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="ff14a-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från föregående bokmärke.</span><span class="sxs-lookup"><span data-stu-id="ff14a-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="ff14a-109">*utdata* \[ut\] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="ff14a-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff14a-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ff14a-110">Return value</span></span>
------------

<span data-ttu-id="ff14a-111">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="ff14a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff14a-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ff14a-112">Remarks</span></span>

<span data-ttu-id="ff14a-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ff14a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff14a-114">Krav</span><span class="sxs-lookup"><span data-stu-id="ff14a-114">Requirements</span></span>
------------
><span data-ttu-id="ff14a-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ff14a-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ff14a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ff14a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ff14a-117">Se även</span><span class="sxs-lookup"><span data-stu-id="ff14a-117">See also</span></span>


[<span data-ttu-id="ff14a-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ff14a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)