---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: StopConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a8aaf-103">StopConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a8aaf-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a8aaf-104">Stoppar konfigurationsändringen som pågår.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="a8aaf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8aaf-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="a8aaf-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a8aaf-106">Parameters</span></span>
----------

<span data-ttu-id="a8aaf-107">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="a8aaf-107">*force* \[in\]</span></span>  
<span data-ttu-id="a8aaf-108">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a8aaf-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a8aaf-109">Return value</span></span>
------------

<span data-ttu-id="a8aaf-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8aaf-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a8aaf-111">Remarks</span></span>

<span data-ttu-id="a8aaf-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a8aaf-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a8aaf-113">Krav</span><span class="sxs-lookup"><span data-stu-id="a8aaf-113">Requirements</span></span>
------------
><span data-ttu-id="a8aaf-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a8aaf-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a8aaf-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a8aaf-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a8aaf-116">Se även</span><span class="sxs-lookup"><span data-stu-id="a8aaf-116">See also</span></span>


[<span data-ttu-id="a8aaf-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a8aaf-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



