---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: 4cfac5edb5fed94ee69deb98d7aa6be56b51c5b3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463745"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="ff548-103">SendConfigurationApplyAsync-metoden</span><span class="sxs-lookup"><span data-stu-id="ff548-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="ff548-104">Skickar konfigurations dokumentet asynkront till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ff548-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff548-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff548-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="ff548-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ff548-106">Parameters</span></span>

<span data-ttu-id="ff548-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ff548-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ff548-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="ff548-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="ff548-109">**jobId** \[ i \] ID: t för det jobb som du vill skicka konfigurationen för.</span><span class="sxs-lookup"><span data-stu-id="ff548-109">**jobId** \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ff548-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ff548-110">Return value</span></span>

<span data-ttu-id="ff548-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="ff548-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff548-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ff548-112">Remarks</span></span>

<span data-ttu-id="ff548-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ff548-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ff548-114">Krav</span><span class="sxs-lookup"><span data-stu-id="ff548-114">Requirements</span></span>

<span data-ttu-id="ff548-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ff548-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ff548-116">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ff548-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ff548-117">Se även</span><span class="sxs-lookup"><span data-stu-id="ff548-117">See also</span></span>

[<span data-ttu-id="ff548-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ff548-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
