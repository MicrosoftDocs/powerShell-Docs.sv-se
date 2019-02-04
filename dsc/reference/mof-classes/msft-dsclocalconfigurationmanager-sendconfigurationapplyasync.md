---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688835"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a7fcd-103">SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="a7fcd-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a7fcd-104">Skickar konfigurationsdokumentet asynkront till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a7fcd-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7fcd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7fcd-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="a7fcd-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a7fcd-106">Parameters</span></span>

<span data-ttu-id="a7fcd-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a7fcd-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a7fcd-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="a7fcd-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="a7fcd-109">*jobId* \[i\] ID för jobbet för att skicka konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a7fcd-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a7fcd-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a7fcd-110">Return value</span></span>

<span data-ttu-id="a7fcd-111">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a7fcd-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7fcd-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a7fcd-112">Remarks</span></span>

<span data-ttu-id="a7fcd-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a7fcd-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7fcd-114">Krav</span><span class="sxs-lookup"><span data-stu-id="a7fcd-114">Requirements</span></span>

<span data-ttu-id="a7fcd-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a7fcd-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a7fcd-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7fcd-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a7fcd-117">Se även</span><span class="sxs-lookup"><span data-stu-id="a7fcd-117">See also</span></span>

[<span data-ttu-id="a7fcd-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a7fcd-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)