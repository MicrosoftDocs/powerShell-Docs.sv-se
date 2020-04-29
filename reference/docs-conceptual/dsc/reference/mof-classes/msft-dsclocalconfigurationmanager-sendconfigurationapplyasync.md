---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941546"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="f90a4-103">SendConfigurationApplyAsync-metoden</span><span class="sxs-lookup"><span data-stu-id="f90a4-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="f90a4-104">Skickar konfigurations dokumentet asynkront till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f90a4-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="f90a4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f90a4-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="f90a4-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f90a4-106">Parameters</span></span>

<span data-ttu-id="f90a4-107">*ConfigurationData* \[i\] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f90a4-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="f90a4-108">*tvinga* \[i\] **uppfyllelse** att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="f90a4-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="f90a4-109">*jobId* \[i\] ID: t för det jobb som konfigurationen ska skickas till.</span><span class="sxs-lookup"><span data-stu-id="f90a4-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f90a4-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="f90a4-110">Return value</span></span>

<span data-ttu-id="f90a4-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="f90a4-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f90a4-112">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f90a4-112">Remarks</span></span>

<span data-ttu-id="f90a4-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="f90a4-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f90a4-114">Krav</span><span class="sxs-lookup"><span data-stu-id="f90a4-114">Requirements</span></span>

<span data-ttu-id="f90a4-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="f90a4-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f90a4-116">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f90a4-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f90a4-117">Se även</span><span class="sxs-lookup"><span data-stu-id="f90a4-117">See also</span></span>

[<span data-ttu-id="f90a4-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f90a4-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
