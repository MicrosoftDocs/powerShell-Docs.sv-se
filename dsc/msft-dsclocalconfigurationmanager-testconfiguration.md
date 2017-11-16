---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="85cb3-103">TestConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="85cb3-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="85cb3-104">Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="85cb3-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="85cb3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="85cb3-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="85cb3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="85cb3-106">Parameters</span></span>
----------

<span data-ttu-id="85cb3-107">*configurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="85cb3-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="85cb3-108">Miljödata för confuguration.</span><span class="sxs-lookup"><span data-stu-id="85cb3-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="85cb3-109">*InDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="85cb3-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="85cb3-110">Anger om hanterad nod är i tillståndet anges i konfigurationen dokumentet på return.</span><span class="sxs-lookup"><span data-stu-id="85cb3-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="85cb3-111">*ResourcesInDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="85cb3-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="85cb3-112">På RETUR, innehåller en inbäddad instans av den **MSFT_ResourceInDesiredState** klass som anger resurser som ingår i tillståndet.</span><span class="sxs-lookup"><span data-stu-id="85cb3-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="85cb3-113">*ResourcesNotInDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="85cb3-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="85cb3-114">På RETUR, innehåller en inbäddad instans av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte är i tillståndet önskade.</span><span class="sxs-lookup"><span data-stu-id="85cb3-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="85cb3-115">Returvärde</span><span class="sxs-lookup"><span data-stu-id="85cb3-115">Return value</span></span>
------------

<span data-ttu-id="85cb3-116">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="85cb3-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="85cb3-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="85cb3-117">Remarks</span></span>

<span data-ttu-id="85cb3-118">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="85cb3-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="85cb3-119">Krav</span><span class="sxs-lookup"><span data-stu-id="85cb3-119">Requirements</span></span>
------------
><span data-ttu-id="85cb3-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="85cb3-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="85cb3-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="85cb3-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="85cb3-122">Se även</span><span class="sxs-lookup"><span data-stu-id="85cb3-122">See also</span></span>


[<span data-ttu-id="85cb3-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="85cb3-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



