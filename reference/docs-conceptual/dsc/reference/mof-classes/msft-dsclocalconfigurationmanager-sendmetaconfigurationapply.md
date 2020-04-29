---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: SendMetaConfigurationApply-metoden
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942596"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="f77e0-103">SendMetaConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="f77e0-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="f77e0-104">Anger de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="f77e0-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="f77e0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f77e0-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f77e0-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f77e0-106">Parameters</span></span>

<span data-ttu-id="f77e0-107">*ConfigurationData* \[i\] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f77e0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="f77e0-108">*tvinga* \[i\] **uppfyllelse** att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="f77e0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="f77e0-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="f77e0-109">Return value</span></span>

<span data-ttu-id="f77e0-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="f77e0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f77e0-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f77e0-111">Remarks</span></span>

<span data-ttu-id="f77e0-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="f77e0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f77e0-113">Krav</span><span class="sxs-lookup"><span data-stu-id="f77e0-113">Requirements</span></span>

<span data-ttu-id="f77e0-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="f77e0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f77e0-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f77e0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f77e0-116">Se även</span><span class="sxs-lookup"><span data-stu-id="f77e0-116">See also</span></span>

[<span data-ttu-id="f77e0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f77e0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
