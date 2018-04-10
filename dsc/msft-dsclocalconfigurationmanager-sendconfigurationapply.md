---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 8edf8c55089e767394ba21b42fe74072777a45c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0d215-103">SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="0d215-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0d215-104">Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0d215-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="0d215-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d215-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="0d215-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0d215-106">Parameters</span></span>
----------

<span data-ttu-id="0d215-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0d215-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0d215-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="0d215-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d215-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="0d215-109">Return value</span></span>
------------

<span data-ttu-id="0d215-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="0d215-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d215-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0d215-111">Remarks</span></span>

<span data-ttu-id="0d215-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="0d215-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d215-113">Krav</span><span class="sxs-lookup"><span data-stu-id="0d215-113">Requirements</span></span>
------------
><span data-ttu-id="0d215-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0d215-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0d215-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d215-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0d215-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0d215-116">See also</span></span>


[<span data-ttu-id="0d215-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0d215-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)