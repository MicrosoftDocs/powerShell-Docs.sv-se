---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="430b5-103">StopConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="430b5-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="430b5-104">Stoppar konfigurationsändringen som pågår.</span><span class="sxs-lookup"><span data-stu-id="430b5-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="430b5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="430b5-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="430b5-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="430b5-106">Parameters</span></span>
----------

<span data-ttu-id="430b5-107">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="430b5-107">*force* \[in\]</span></span>  
<span data-ttu-id="430b5-108">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="430b5-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="430b5-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="430b5-109">Return value</span></span>
------------

<span data-ttu-id="430b5-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="430b5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="430b5-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="430b5-111">Remarks</span></span>

<span data-ttu-id="430b5-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="430b5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="430b5-113">Krav</span><span class="sxs-lookup"><span data-stu-id="430b5-113">Requirements</span></span>
------------
><span data-ttu-id="430b5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="430b5-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="430b5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="430b5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="430b5-116">Se även</span><span class="sxs-lookup"><span data-stu-id="430b5-116">See also</span></span>


[<span data-ttu-id="430b5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="430b5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



