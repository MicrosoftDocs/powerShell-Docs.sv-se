---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: SendMetaConfigurationApply-metoden
ms.openlocfilehash: 896afe2f3370e108b48583aafb33ee7b0eb1301b
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463728"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="ad93a-103">SendMetaConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="ad93a-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="ad93a-104">Anger de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="ad93a-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="ad93a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ad93a-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ad93a-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ad93a-106">Parameters</span></span>

<span data-ttu-id="ad93a-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ad93a-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ad93a-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="ad93a-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ad93a-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ad93a-109">Return value</span></span>

<span data-ttu-id="ad93a-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="ad93a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ad93a-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ad93a-111">Remarks</span></span>

<span data-ttu-id="ad93a-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ad93a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ad93a-113">Krav</span><span class="sxs-lookup"><span data-stu-id="ad93a-113">Requirements</span></span>

<span data-ttu-id="ad93a-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ad93a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ad93a-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ad93a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ad93a-116">Se även</span><span class="sxs-lookup"><span data-stu-id="ad93a-116">See also</span></span>

[<span data-ttu-id="ad93a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ad93a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
