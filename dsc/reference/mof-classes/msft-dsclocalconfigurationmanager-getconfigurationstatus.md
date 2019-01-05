---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048733"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d668c-103">GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="d668c-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d668c-104">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="d668c-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="d668c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d668c-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="d668c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d668c-106">Parameters</span></span>

<span data-ttu-id="d668c-107">*Alla* \[i\] **SANT** om den här metoden ska returnera information om alla konfigurationen körs på datorn, inklusive av konfigurationsprogrammet och konsekvenskontrollen.</span><span class="sxs-lookup"><span data-stu-id="d668c-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d668c-108">*configurationStatus* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_DSCConfigurationStatus** klass som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="d668c-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d668c-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d668c-109">Return value</span></span>

<span data-ttu-id="d668c-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d668c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d668c-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d668c-111">Remarks</span></span>

<span data-ttu-id="d668c-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d668c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d668c-113">Krav</span><span class="sxs-lookup"><span data-stu-id="d668c-113">Requirements</span></span>

<span data-ttu-id="d668c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d668c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d668c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d668c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d668c-116">Se även</span><span class="sxs-lookup"><span data-stu-id="d668c-116">See also</span></span>

[<span data-ttu-id="d668c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d668c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)