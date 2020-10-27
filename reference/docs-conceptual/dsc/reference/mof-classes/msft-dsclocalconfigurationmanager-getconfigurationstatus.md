---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationStatus-metoden
description: GetConfigurationStatus-metoden
ms.openlocfilehash: fe25d17069d9011e931ac50fec27cb9ebafba365
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650869"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="95eda-103">GetConfigurationStatus-metoden</span><span class="sxs-lookup"><span data-stu-id="95eda-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="95eda-104">Hämta konfigurations status historik.</span><span class="sxs-lookup"><span data-stu-id="95eda-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="95eda-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="95eda-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="95eda-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="95eda-106">Parameters</span></span>

<span data-ttu-id="95eda-107">**Alla** \[ i \] **True** om den här metoden ska returnera information om all konfiguration som körs på datorn, inklusive konfigurations programmet och konsekvens kontrollen.</span><span class="sxs-lookup"><span data-stu-id="95eda-107">**All** \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="95eda-108">**configurationStatus** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_DSCConfigurationStatus** som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="95eda-108">**configurationStatus** \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="95eda-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="95eda-109">Return value</span></span>

<span data-ttu-id="95eda-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="95eda-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="95eda-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="95eda-111">Remarks</span></span>

<span data-ttu-id="95eda-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="95eda-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="95eda-113">Krav</span><span class="sxs-lookup"><span data-stu-id="95eda-113">Requirements</span></span>

<span data-ttu-id="95eda-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="95eda-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="95eda-115">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="95eda-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="95eda-116">Se även</span><span class="sxs-lookup"><span data-stu-id="95eda-116">See also</span></span>

[<span data-ttu-id="95eda-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="95eda-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
