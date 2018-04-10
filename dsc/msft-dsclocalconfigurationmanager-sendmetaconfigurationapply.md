---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cdb94-103">SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="cdb94-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cdb94-104">Anger Local Configuration Manager-inställningar som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="cdb94-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="cdb94-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cdb94-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="cdb94-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="cdb94-106">Parameters</span></span>
----------

<span data-ttu-id="cdb94-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="cdb94-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="cdb94-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="cdb94-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cdb94-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="cdb94-109">Return value</span></span>
------------

<span data-ttu-id="cdb94-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="cdb94-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdb94-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cdb94-111">Remarks</span></span>

<span data-ttu-id="cdb94-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="cdb94-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdb94-113">Krav</span><span class="sxs-lookup"><span data-stu-id="cdb94-113">Requirements</span></span>
------------
><span data-ttu-id="cdb94-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cdb94-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cdb94-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cdb94-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cdb94-116">Se även</span><span class="sxs-lookup"><span data-stu-id="cdb94-116">See also</span></span>


[<span data-ttu-id="cdb94-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cdb94-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)