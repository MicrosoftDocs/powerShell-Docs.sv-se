---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6373a-103">GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="6373a-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6373a-104">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6373a-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="6373a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6373a-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="6373a-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="6373a-106">Parameters</span></span>
----------

<span data-ttu-id="6373a-107">*Alla* \[i\] **SANT** om den här metoden ska returnera information om alla konfigurationen som körs på datorn, inklusive program för konfiguration och konsekvenskontrollen.</span><span class="sxs-lookup"><span data-stu-id="6373a-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="6373a-108">*configurationStatus* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_DSCConfigurationStatus** klass som definierar inställningar.</span><span class="sxs-lookup"><span data-stu-id="6373a-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="6373a-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="6373a-109">Return value</span></span>
------------

<span data-ttu-id="6373a-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="6373a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6373a-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="6373a-111">Remarks</span></span>

<span data-ttu-id="6373a-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="6373a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6373a-113">Krav</span><span class="sxs-lookup"><span data-stu-id="6373a-113">Requirements</span></span>
------------
><span data-ttu-id="6373a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6373a-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6373a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6373a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6373a-116">Se även</span><span class="sxs-lookup"><span data-stu-id="6373a-116">See also</span></span>


[<span data-ttu-id="6373a-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6373a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)