---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186685"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2ef5e-103">SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="2ef5e-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2ef5e-104">Skickar konfiguration dokumentet asynkront till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="2ef5e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ef5e-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="2ef5e-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2ef5e-106">Parameters</span></span>
----------

<span data-ttu-id="2ef5e-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="2ef5e-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="2ef5e-109">*jobId* \[i\] ID för jobbet för att skicka konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ef5e-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="2ef5e-110">Return value</span></span>
------------

<span data-ttu-id="2ef5e-111">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ef5e-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2ef5e-112">Remarks</span></span>

<span data-ttu-id="2ef5e-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ef5e-114">Krav</span><span class="sxs-lookup"><span data-stu-id="2ef5e-114">Requirements</span></span>
------------
><span data-ttu-id="2ef5e-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2ef5e-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2ef5e-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2ef5e-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2ef5e-117">Se även</span><span class="sxs-lookup"><span data-stu-id="2ef5e-117">See also</span></span>


[<span data-ttu-id="2ef5e-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2ef5e-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)