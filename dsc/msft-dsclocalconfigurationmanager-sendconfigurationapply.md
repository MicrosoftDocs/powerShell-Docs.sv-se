---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d7a3f-103">SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="d7a3f-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d7a3f-104">Skickar konfiguration dokumentet till noden hanterade används Configuration Agent för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d7a3f-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="d7a3f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d7a3f-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d7a3f-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d7a3f-106">Parameters</span></span>
----------

<span data-ttu-id="d7a3f-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d7a3f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d7a3f-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="d7a3f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d7a3f-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d7a3f-109">Return value</span></span>
------------

<span data-ttu-id="d7a3f-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d7a3f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7a3f-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d7a3f-111">Remarks</span></span>

<span data-ttu-id="d7a3f-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d7a3f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d7a3f-113">Krav</span><span class="sxs-lookup"><span data-stu-id="d7a3f-113">Requirements</span></span>
------------
><span data-ttu-id="d7a3f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d7a3f-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d7a3f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d7a3f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d7a3f-116">Se även</span><span class="sxs-lookup"><span data-stu-id="d7a3f-116">See also</span></span>


[<span data-ttu-id="d7a3f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d7a3f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)