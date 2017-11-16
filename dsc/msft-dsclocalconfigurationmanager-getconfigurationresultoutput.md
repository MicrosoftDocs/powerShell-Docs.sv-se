---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationResultOutput-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="94fba-103">GetConfigurationResultOutput-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="94fba-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="94fba-104">Hämtar Configuration Agent utdata som är associerade med ett specifikt jobb.</span><span class="sxs-lookup"><span data-stu-id="94fba-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="94fba-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="94fba-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="94fba-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="94fba-106">Parameters</span></span>
----------

<span data-ttu-id="94fba-107">*jobId* \[i\]</span><span class="sxs-lookup"><span data-stu-id="94fba-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="94fba-108">ID för jobbet som du vill hämta utdata.</span><span class="sxs-lookup"><span data-stu-id="94fba-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="94fba-109">*resumeOutputBookmark* \[i\]</span><span class="sxs-lookup"><span data-stu-id="94fba-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="94fba-110">Anger att utdata ska vara en fortsättning från föregående bokmärke.</span><span class="sxs-lookup"><span data-stu-id="94fba-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="94fba-111">*utdata* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="94fba-111">*output* \[out\]</span></span>  
<span data-ttu-id="94fba-112">Utdata för jobbet.</span><span class="sxs-lookup"><span data-stu-id="94fba-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="94fba-113">Returvärde</span><span class="sxs-lookup"><span data-stu-id="94fba-113">Return value</span></span>
------------

<span data-ttu-id="94fba-114">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="94fba-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="94fba-115">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="94fba-115">Remarks</span></span>

<span data-ttu-id="94fba-116">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="94fba-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94fba-117">Krav</span><span class="sxs-lookup"><span data-stu-id="94fba-117">Requirements</span></span>
------------
><span data-ttu-id="94fba-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="94fba-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="94fba-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="94fba-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="94fba-120">Se även</span><span class="sxs-lookup"><span data-stu-id="94fba-120">See also</span></span>


[<span data-ttu-id="94fba-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="94fba-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



