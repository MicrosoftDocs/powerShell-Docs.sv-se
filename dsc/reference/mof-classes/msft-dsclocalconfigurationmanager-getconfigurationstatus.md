---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734507"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="07415-103">GetConfigurationStatus-metoden</span><span class="sxs-lookup"><span data-stu-id="07415-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="07415-104">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="07415-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="07415-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="07415-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="07415-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="07415-106">Parameters</span></span>

<span data-ttu-id="07415-107">*Alla* \[i\] **SANT** om den här metoden ska returnera information om alla konfigurationen körs på datorn, inklusive av konfigurationsprogrammet och konsekvenskontrollen.</span><span class="sxs-lookup"><span data-stu-id="07415-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="07415-108">*configurationStatus* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_DSCConfigurationStatus** klass som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="07415-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="07415-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="07415-109">Return value</span></span>

<span data-ttu-id="07415-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="07415-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07415-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="07415-111">Remarks</span></span>

<span data-ttu-id="07415-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="07415-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07415-113">Krav</span><span class="sxs-lookup"><span data-stu-id="07415-113">Requirements</span></span>

<span data-ttu-id="07415-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07415-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="07415-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07415-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="07415-116">Se även</span><span class="sxs-lookup"><span data-stu-id="07415-116">See also</span></span>

[<span data-ttu-id="07415-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07415-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
