---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="78083-103">GetConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="78083-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="78083-104">Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="78083-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="78083-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="78083-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="78083-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="78083-106">Parameters</span></span>
----------

<span data-ttu-id="78083-107">*configurationData* \[i\]</span><span class="sxs-lookup"><span data-stu-id="78083-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="78083-108">Anger att skicka konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="78083-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="78083-109">*konfigurationer* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="78083-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="78083-110">Innehåller en inbäddad instans av konfigurationerna på return.</span><span class="sxs-lookup"><span data-stu-id="78083-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="78083-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="78083-111">Return value</span></span>
------------

<span data-ttu-id="78083-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="78083-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78083-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="78083-113">Remarks</span></span>

<span data-ttu-id="78083-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="78083-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78083-115">Krav</span><span class="sxs-lookup"><span data-stu-id="78083-115">Requirements</span></span>
------------
><span data-ttu-id="78083-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78083-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="78083-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78083-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="78083-118">Se även</span><span class="sxs-lookup"><span data-stu-id="78083-118">See also</span></span>


[<span data-ttu-id="78083-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="78083-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



