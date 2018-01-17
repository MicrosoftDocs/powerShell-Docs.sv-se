---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c901f-103">TestConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c901f-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c901f-104">Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="c901f-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="c901f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c901f-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="c901f-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="c901f-106">Parameters</span></span>
----------

<span data-ttu-id="c901f-107">*configurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="c901f-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="c901f-108">Miljödata för confuguration.</span><span class="sxs-lookup"><span data-stu-id="c901f-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="c901f-109">*InDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="c901f-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="c901f-110">Anger om hanterad nod är i tillståndet anges i konfigurationen dokumentet på return.</span><span class="sxs-lookup"><span data-stu-id="c901f-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="c901f-111">*ResourcesInDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="c901f-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="c901f-112">På RETUR, innehåller en inbäddad instans av den **MSFT_ResourceInDesiredState** klass som anger resurser som ingår i tillståndet.</span><span class="sxs-lookup"><span data-stu-id="c901f-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="c901f-113">*ResourcesNotInDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="c901f-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="c901f-114">På RETUR, innehåller en inbäddad instans av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte är i tillståndet önskade.</span><span class="sxs-lookup"><span data-stu-id="c901f-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="c901f-115">Returvärde</span><span class="sxs-lookup"><span data-stu-id="c901f-115">Return value</span></span>
------------

<span data-ttu-id="c901f-116">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="c901f-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c901f-117">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c901f-117">Remarks</span></span>

<span data-ttu-id="c901f-118">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="c901f-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c901f-119">Krav</span><span class="sxs-lookup"><span data-stu-id="c901f-119">Requirements</span></span>
------------
><span data-ttu-id="c901f-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c901f-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c901f-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c901f-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c901f-122">Se även</span><span class="sxs-lookup"><span data-stu-id="c901f-122">See also</span></span>


[<span data-ttu-id="c901f-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c901f-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



