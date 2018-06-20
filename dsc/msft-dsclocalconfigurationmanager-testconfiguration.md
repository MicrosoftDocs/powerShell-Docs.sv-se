---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219019"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a16d2-103">TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="a16d2-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a16d2-104">Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="a16d2-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="a16d2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a16d2-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="a16d2-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a16d2-106">Parameters</span></span>
----------

<span data-ttu-id="a16d2-107">*configurationData* \[i\] miljödata för confuguration.</span><span class="sxs-lookup"><span data-stu-id="a16d2-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="a16d2-108">*InDesiredState* \[ut\] på RETUR, anger om hanterad nod är i tillståndet anges i configuration-dokumentet.</span><span class="sxs-lookup"><span data-stu-id="a16d2-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="a16d2-109">*ResourcesInDesiredState* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_ResourceInDesiredState** klass som anger resurser som ingår i tillståndet.</span><span class="sxs-lookup"><span data-stu-id="a16d2-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="a16d2-110">*ResourcesNotInDesiredState* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte är i tillståndet önskade.</span><span class="sxs-lookup"><span data-stu-id="a16d2-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="a16d2-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a16d2-111">Return value</span></span>
------------

<span data-ttu-id="a16d2-112">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a16d2-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a16d2-113">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a16d2-113">Remarks</span></span>

<span data-ttu-id="a16d2-114">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a16d2-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a16d2-115">Krav</span><span class="sxs-lookup"><span data-stu-id="a16d2-115">Requirements</span></span>
------------
><span data-ttu-id="a16d2-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a16d2-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a16d2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16d2-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a16d2-118">Se även</span><span class="sxs-lookup"><span data-stu-id="a16d2-118">See also</span></span>


[<span data-ttu-id="a16d2-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a16d2-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)