---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationStatus-metoden
ms.openlocfilehash: c2c478151428052d656832fb4079f12d666a910d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464066"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="dc23a-103">GetConfigurationStatus-metoden</span><span class="sxs-lookup"><span data-stu-id="dc23a-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="dc23a-104">Hämta konfigurations status historik.</span><span class="sxs-lookup"><span data-stu-id="dc23a-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="dc23a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dc23a-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="dc23a-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="dc23a-106">Parameters</span></span>

<span data-ttu-id="dc23a-107">**Alla** \[ i \] **True** om den här metoden ska returnera information om all konfiguration som körs på datorn, inklusive konfigurations programmet och konsekvens kontrollen.</span><span class="sxs-lookup"><span data-stu-id="dc23a-107">**All** \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="dc23a-108">**configurationStatus** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_DSCConfigurationStatus** som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="dc23a-108">**configurationStatus** \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="dc23a-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="dc23a-109">Return value</span></span>

<span data-ttu-id="dc23a-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="dc23a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc23a-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="dc23a-111">Remarks</span></span>

<span data-ttu-id="dc23a-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="dc23a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="dc23a-113">Krav</span><span class="sxs-lookup"><span data-stu-id="dc23a-113">Requirements</span></span>

<span data-ttu-id="dc23a-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="dc23a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="dc23a-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc23a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="dc23a-116">Se även</span><span class="sxs-lookup"><span data-stu-id="dc23a-116">See also</span></span>

[<span data-ttu-id="dc23a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="dc23a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
