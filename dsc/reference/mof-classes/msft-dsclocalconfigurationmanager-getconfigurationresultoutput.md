---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078661"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fcc93-103">GetConfigurationResultOutput-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="fcc93-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fcc93-104">Hämtar Configuration-agenten utdata som är associerade med ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="fcc93-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcc93-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fcc93-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="fcc93-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="fcc93-106">Parameters</span></span>

<span data-ttu-id="fcc93-107">*jobId* \[i\] ID för jobbet som du vill hämta utdata.</span><span class="sxs-lookup"><span data-stu-id="fcc93-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="fcc93-108">*resumeOutputBookmark* \[i\] anger att utdata ska vara en fortsättning från en föregående bokmärke.</span><span class="sxs-lookup"><span data-stu-id="fcc93-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="fcc93-109">*utdata* \[ut\] utdata för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="fcc93-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="fcc93-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="fcc93-110">Return value</span></span>

<span data-ttu-id="fcc93-111">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="fcc93-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcc93-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fcc93-112">Remarks</span></span>

<span data-ttu-id="fcc93-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="fcc93-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcc93-114">Krav</span><span class="sxs-lookup"><span data-stu-id="fcc93-114">Requirements</span></span>

<span data-ttu-id="fcc93-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fcc93-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fcc93-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fcc93-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fcc93-117">Se även</span><span class="sxs-lookup"><span data-stu-id="fcc93-117">See also</span></span>

[<span data-ttu-id="fcc93-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fcc93-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)