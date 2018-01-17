---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 72c59b5aad293fa561146e5ad6822f27f40f321f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ff7ce-103">SendConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="ff7ce-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ff7ce-104">Skickar konfiguration dokumentet till noden hanterade och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="ff7ce-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="ff7ce-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff7ce-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="ff7ce-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ff7ce-106">Parameters</span></span>
----------

<span data-ttu-id="ff7ce-107">*ConfigurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="ff7ce-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="ff7ce-108">Miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ff7ce-108">The environment data for the configuration.</span></span>

<span data-ttu-id="ff7ce-109">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="ff7ce-109">*force* \[in\]</span></span>  
<span data-ttu-id="ff7ce-110">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="ff7ce-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff7ce-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ff7ce-111">Return value</span></span>
------------

<span data-ttu-id="ff7ce-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="ff7ce-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff7ce-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ff7ce-113">Remarks</span></span>

<span data-ttu-id="ff7ce-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ff7ce-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff7ce-115">Krav</span><span class="sxs-lookup"><span data-stu-id="ff7ce-115">Requirements</span></span>
------------
><span data-ttu-id="ff7ce-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ff7ce-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="ff7ce-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ff7ce-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="ff7ce-118">Se även</span><span class="sxs-lookup"><span data-stu-id="ff7ce-118">See also</span></span>


[<span data-ttu-id="ff7ce-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ff7ce-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



