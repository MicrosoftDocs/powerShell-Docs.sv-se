---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendMetaConfigurationApply-metoden
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727038"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="7687c-103">SendMetaConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="7687c-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="7687c-104">Anger de Local Configuration Manager-inställningar som används för att styra agenten Configuration.</span><span class="sxs-lookup"><span data-stu-id="7687c-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7687c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7687c-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7687c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7687c-106">Parameters</span></span>

<span data-ttu-id="7687c-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="7687c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7687c-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="7687c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7687c-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="7687c-109">Return value</span></span>

<span data-ttu-id="7687c-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="7687c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7687c-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7687c-111">Remarks</span></span>

<span data-ttu-id="7687c-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="7687c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7687c-113">Krav</span><span class="sxs-lookup"><span data-stu-id="7687c-113">Requirements</span></span>

<span data-ttu-id="7687c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7687c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7687c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7687c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7687c-116">Se även</span><span class="sxs-lookup"><span data-stu-id="7687c-116">See also</span></span>

[<span data-ttu-id="7687c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7687c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
