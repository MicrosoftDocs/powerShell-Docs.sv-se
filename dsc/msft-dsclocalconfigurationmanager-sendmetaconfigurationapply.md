---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d9b49-103">SendMetaConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="d9b49-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d9b49-104">Anger Local Configuration Manager-inställningar som används för att styra Configuration Agent.</span><span class="sxs-lookup"><span data-stu-id="d9b49-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="d9b49-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9b49-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="d9b49-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d9b49-106">Parameters</span></span>
----------

<span data-ttu-id="d9b49-107">*ConfigurationData* \[i\] miljödata för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d9b49-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d9b49-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.</span><span class="sxs-lookup"><span data-stu-id="d9b49-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d9b49-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d9b49-109">Return value</span></span>
------------

<span data-ttu-id="d9b49-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d9b49-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9b49-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d9b49-111">Remarks</span></span>

<span data-ttu-id="d9b49-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d9b49-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9b49-113">Krav</span><span class="sxs-lookup"><span data-stu-id="d9b49-113">Requirements</span></span>
------------
><span data-ttu-id="d9b49-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d9b49-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d9b49-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9b49-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d9b49-116">Se även</span><span class="sxs-lookup"><span data-stu-id="d9b49-116">See also</span></span>


[<span data-ttu-id="d9b49-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d9b49-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)