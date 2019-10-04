---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetConfigurationStatus-metoden
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942694"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="3e997-103">GetConfigurationStatus-metoden</span><span class="sxs-lookup"><span data-stu-id="3e997-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="3e997-104">Hämta konfigurations status historik.</span><span class="sxs-lookup"><span data-stu-id="3e997-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e997-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e997-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="3e997-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="3e997-106">Parameters</span></span>

<span data-ttu-id="3e997-107">*Alla* \[in @ no__t-2 **True** om den här metoden ska returnera information om all konfiguration som körs på datorn, inklusive konfigurations programmet och konsekvens kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3e997-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="3e997-108">*configurationStatus* \[out @ no__t-2 vid retur innehåller en inbäddad instans av **MSFT_DSCConfigurationStatus** -klassen som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="3e997-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e997-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="3e997-109">Return value</span></span>

<span data-ttu-id="3e997-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="3e997-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e997-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3e997-111">Remarks</span></span>

<span data-ttu-id="3e997-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="3e997-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e997-113">Krav</span><span class="sxs-lookup"><span data-stu-id="3e997-113">Requirements</span></span>

<span data-ttu-id="3e997-114">**-** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3e997-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3e997-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3e997-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3e997-116">Se även</span><span class="sxs-lookup"><span data-stu-id="3e997-116">See also</span></span>

[<span data-ttu-id="3e997-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3e997-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
