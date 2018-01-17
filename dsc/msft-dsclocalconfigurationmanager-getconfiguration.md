---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e2ce8-103">GetConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e2ce8-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e2ce8-104">Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="e2ce8-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="e2ce8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2ce8-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="e2ce8-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e2ce8-106">Parameters</span></span>
----------

<span data-ttu-id="e2ce8-107">*configurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="e2ce8-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="e2ce8-108">Anger att skicka konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="e2ce8-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="e2ce8-109">*konfigurationer* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="e2ce8-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="e2ce8-110">Innehåller en inbäddad instans av konfigurationerna på return.</span><span class="sxs-lookup"><span data-stu-id="e2ce8-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="e2ce8-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="e2ce8-111">Return value</span></span>
------------

<span data-ttu-id="e2ce8-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="e2ce8-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2ce8-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e2ce8-113">Remarks</span></span>

<span data-ttu-id="e2ce8-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="e2ce8-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2ce8-115">Krav</span><span class="sxs-lookup"><span data-stu-id="e2ce8-115">Requirements</span></span>
------------
><span data-ttu-id="e2ce8-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e2ce8-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e2ce8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e2ce8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e2ce8-118">Se även</span><span class="sxs-lookup"><span data-stu-id="e2ce8-118">See also</span></span>


[<span data-ttu-id="e2ce8-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e2ce8-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



