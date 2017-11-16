---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="33799-103">SendConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="33799-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="33799-104">Skickar konfiguration dokumentet till noden hanterade och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="33799-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="33799-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="33799-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="33799-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="33799-106">Parameters</span></span>
----------

<span data-ttu-id="33799-107">*ConfigurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="33799-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="33799-108">Miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="33799-108">The environment data for the configuration.</span></span>

<span data-ttu-id="33799-109">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="33799-109">*force* \[in\]</span></span>  
<span data-ttu-id="33799-110">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="33799-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="33799-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="33799-111">Return value</span></span>
------------

<span data-ttu-id="33799-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="33799-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="33799-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="33799-113">Remarks</span></span>

<span data-ttu-id="33799-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="33799-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="33799-115">Krav</span><span class="sxs-lookup"><span data-stu-id="33799-115">Requirements</span></span>
------------
><span data-ttu-id="33799-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="33799-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="33799-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="33799-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="33799-118">Se även</span><span class="sxs-lookup"><span data-stu-id="33799-118">See also</span></span>


[<span data-ttu-id="33799-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="33799-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



