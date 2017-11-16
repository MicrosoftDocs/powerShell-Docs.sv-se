---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9552fd5b5feb862fbe8ef95a7746776e7fe2f5c8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="15a98-103">SendConfigurationApply-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="15a98-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="15a98-104">Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="15a98-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="15a98-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="15a98-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="15a98-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="15a98-106">Parameters</span></span>
----------

<span data-ttu-id="15a98-107">*ConfigurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="15a98-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="15a98-108">Miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="15a98-108">The environment data for the configuration.</span></span>

<span data-ttu-id="15a98-109">*Tvinga* \[i\]</span><span class="sxs-lookup"><span data-stu-id="15a98-109">*force* \[in\]</span></span>  
<span data-ttu-id="15a98-110">**SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="15a98-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="15a98-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="15a98-111">Return value</span></span>
------------

<span data-ttu-id="15a98-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="15a98-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="15a98-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="15a98-113">Remarks</span></span>

<span data-ttu-id="15a98-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="15a98-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="15a98-115">Krav</span><span class="sxs-lookup"><span data-stu-id="15a98-115">Requirements</span></span>
------------
><span data-ttu-id="15a98-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="15a98-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="15a98-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="15a98-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="15a98-118">Se även</span><span class="sxs-lookup"><span data-stu-id="15a98-118">See also</span></span>


[<span data-ttu-id="15a98-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="15a98-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



