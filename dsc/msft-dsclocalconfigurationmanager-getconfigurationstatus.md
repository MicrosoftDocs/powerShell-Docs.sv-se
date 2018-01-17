---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b63f3-103">GetConfigurationStatus-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b63f3-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b63f3-104">Hämta statushistorik konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b63f3-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="b63f3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b63f3-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="b63f3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b63f3-106">Parameters</span></span>
----------

<span data-ttu-id="b63f3-107">*Alla* \[i\]</span><span class="sxs-lookup"><span data-stu-id="b63f3-107">*All* \[in\]</span></span>  
<span data-ttu-id="b63f3-108">**SANT** om den här metoden ska returnera information om alla konfigurationen som körs på datorn, inklusive program för konfiguration och konsekvenskontrollen.</span><span class="sxs-lookup"><span data-stu-id="b63f3-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="b63f3-109">*configurationStatus* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="b63f3-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="b63f3-110">På RETUR, innehåller en inbäddad instans av den **MSFT_DSCConfigurationStatus** klass som definierar inställningar.</span><span class="sxs-lookup"><span data-stu-id="b63f3-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="b63f3-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b63f3-111">Return value</span></span>
------------

<span data-ttu-id="b63f3-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b63f3-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b63f3-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b63f3-113">Remarks</span></span>

<span data-ttu-id="b63f3-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b63f3-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b63f3-115">Krav</span><span class="sxs-lookup"><span data-stu-id="b63f3-115">Requirements</span></span>
------------
><span data-ttu-id="b63f3-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b63f3-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b63f3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b63f3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b63f3-118">Se även</span><span class="sxs-lookup"><span data-stu-id="b63f3-118">See also</span></span>


[<span data-ttu-id="b63f3-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b63f3-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



