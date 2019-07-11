---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734296"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="f5363-103">SendConfigurationApplyAsync-metoden</span><span class="sxs-lookup"><span data-stu-id="f5363-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="f5363-104">Skickar konfigurationsdokumentet asynkront till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f5363-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5363-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5363-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="f5363-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f5363-106">Parameters</span></span>

<span data-ttu-id="f5363-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f5363-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="f5363-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="f5363-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="f5363-109">*jobId* \[i\] ID för jobbet för att skicka konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f5363-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f5363-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="f5363-110">Return value</span></span>

<span data-ttu-id="f5363-111">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="f5363-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5363-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f5363-112">Remarks</span></span>

<span data-ttu-id="f5363-113">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="f5363-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5363-114">Krav</span><span class="sxs-lookup"><span data-stu-id="f5363-114">Requirements</span></span>

<span data-ttu-id="f5363-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f5363-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f5363-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f5363-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f5363-117">Se även</span><span class="sxs-lookup"><span data-stu-id="f5363-117">See also</span></span>

[<span data-ttu-id="f5363-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f5363-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
