---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b9520-103">SendConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b9520-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b9520-104">Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b9520-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="b9520-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b9520-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="b9520-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b9520-106">Parameters</span></span>
----------

<span data-ttu-id="b9520-107">*ConfigurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="b9520-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="b9520-108">Miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b9520-108">The environment data for the configuration.</span></span>

<span data-ttu-id="b9520-109">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="b9520-109">*force* \[in\]</span></span>  
<span data-ttu-id="b9520-110">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="b9520-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9520-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b9520-111">Return value</span></span>
------------

<span data-ttu-id="b9520-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b9520-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9520-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b9520-113">Remarks</span></span>

<span data-ttu-id="b9520-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b9520-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b9520-115">Krav</span><span class="sxs-lookup"><span data-stu-id="b9520-115">Requirements</span></span>
------------
><span data-ttu-id="b9520-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b9520-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b9520-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b9520-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b9520-118">Se även</span><span class="sxs-lookup"><span data-stu-id="b9520-118">See also</span></span>


[<span data-ttu-id="b9520-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b9520-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



