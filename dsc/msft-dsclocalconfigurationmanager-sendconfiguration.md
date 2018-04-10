---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0a0f6-103">SendConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="0a0f6-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0a0f6-104">Skickar konfiguration dokumentet till noden hanterade och sparar den som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="0a0f6-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="0a0f6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0a0f6-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="0a0f6-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0a0f6-106">Parameters</span></span>
----------

<span data-ttu-id="0a0f6-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0a0f6-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0a0f6-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="0a0f6-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0a0f6-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="0a0f6-109">Return value</span></span>
------------

<span data-ttu-id="0a0f6-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="0a0f6-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a0f6-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0a0f6-111">Remarks</span></span>

<span data-ttu-id="0a0f6-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="0a0f6-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a0f6-113">Krav</span><span class="sxs-lookup"><span data-stu-id="0a0f6-113">Requirements</span></span>
------------
><span data-ttu-id="0a0f6-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0a0f6-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="0a0f6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0a0f6-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="0a0f6-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0a0f6-116">See also</span></span>


[<span data-ttu-id="0a0f6-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0a0f6-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)