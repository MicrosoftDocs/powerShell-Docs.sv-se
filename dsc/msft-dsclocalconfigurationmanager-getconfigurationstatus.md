---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221773"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="095c3-103">GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="095c3-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="095c3-104">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="095c3-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="095c3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="095c3-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="095c3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="095c3-106">Parameters</span></span>
----------

<span data-ttu-id="095c3-107">*Alla* \[i\] **SANT** om den här metoden ska returnera information om alla konfigurationen som körs på datorn, inklusive program för konfiguration och konsekvenskontrollen.</span><span class="sxs-lookup"><span data-stu-id="095c3-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="095c3-108">*configurationStatus* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_DSCConfigurationStatus** klass som definierar inställningar.</span><span class="sxs-lookup"><span data-stu-id="095c3-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="095c3-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="095c3-109">Return value</span></span>
------------

<span data-ttu-id="095c3-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="095c3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="095c3-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="095c3-111">Remarks</span></span>

<span data-ttu-id="095c3-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="095c3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="095c3-113">Krav</span><span class="sxs-lookup"><span data-stu-id="095c3-113">Requirements</span></span>
------------
><span data-ttu-id="095c3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="095c3-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="095c3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="095c3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="095c3-116">Se även</span><span class="sxs-lookup"><span data-stu-id="095c3-116">See also</span></span>


[<span data-ttu-id="095c3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="095c3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)