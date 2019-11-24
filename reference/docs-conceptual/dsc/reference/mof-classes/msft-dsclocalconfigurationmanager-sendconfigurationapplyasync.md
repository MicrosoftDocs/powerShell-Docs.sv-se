---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941546"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="24c20-103">SendConfigurationApplyAsync-metoden</span><span class="sxs-lookup"><span data-stu-id="24c20-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="24c20-104">Skickar konfigurations dokumentet asynkront till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="24c20-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="24c20-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="24c20-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="24c20-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="24c20-106">Parameters</span></span>

<span data-ttu-id="24c20-107">*ConfigurationData* \[i\] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="24c20-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="24c20-108">*tvinga* \[i\] **Sant** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="24c20-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="24c20-109">*jobId* \[i\] ID: t för det jobb som konfigurationen ska skickas till.</span><span class="sxs-lookup"><span data-stu-id="24c20-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="24c20-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="24c20-110">Return value</span></span>

<span data-ttu-id="24c20-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="24c20-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24c20-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="24c20-112">Remarks</span></span>

<span data-ttu-id="24c20-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="24c20-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24c20-114">Krav</span><span class="sxs-lookup"><span data-stu-id="24c20-114">Requirements</span></span>

<span data-ttu-id="24c20-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="24c20-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="24c20-116">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24c20-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="24c20-117">Se också</span><span class="sxs-lookup"><span data-stu-id="24c20-117">See also</span></span>

[<span data-ttu-id="24c20-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24c20-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
