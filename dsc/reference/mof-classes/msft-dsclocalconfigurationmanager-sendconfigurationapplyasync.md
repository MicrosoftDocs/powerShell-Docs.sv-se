---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048698"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9d754-103">SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="9d754-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9d754-104">Skickar konfigurationsdokumentet asynkront till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9d754-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d754-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d754-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="9d754-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9d754-106">Parameters</span></span>

<span data-ttu-id="9d754-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9d754-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9d754-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="9d754-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="9d754-109">*jobId* \[i\] ID för jobbet för att skicka konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9d754-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d754-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="9d754-110">Return value</span></span>

<span data-ttu-id="9d754-111">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="9d754-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d754-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="9d754-112">Remarks</span></span>

<span data-ttu-id="9d754-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="9d754-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d754-114">Krav</span><span class="sxs-lookup"><span data-stu-id="9d754-114">Requirements</span></span>

<span data-ttu-id="9d754-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9d754-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9d754-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9d754-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9d754-117">Se även</span><span class="sxs-lookup"><span data-stu-id="9d754-117">See also</span></span>

[<span data-ttu-id="9d754-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9d754-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)