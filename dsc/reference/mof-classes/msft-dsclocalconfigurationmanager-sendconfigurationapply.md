---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727017"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="2f562-103">SendConfigurationApply-metoden</span><span class="sxs-lookup"><span data-stu-id="2f562-103">SendConfigurationApply method</span></span>

<span data-ttu-id="2f562-104">Skickar konfigurationsdokumentet till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2f562-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="2f562-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f562-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="2f562-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2f562-106">Parameters</span></span>

<span data-ttu-id="2f562-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2f562-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="2f562-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="2f562-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2f562-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="2f562-109">Return value</span></span>

<span data-ttu-id="2f562-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="2f562-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f562-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2f562-111">Remarks</span></span>

<span data-ttu-id="2f562-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="2f562-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f562-113">Krav</span><span class="sxs-lookup"><span data-stu-id="2f562-113">Requirements</span></span>

<span data-ttu-id="2f562-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2f562-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2f562-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f562-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2f562-116">Se även</span><span class="sxs-lookup"><span data-stu-id="2f562-116">See also</span></span>

[<span data-ttu-id="2f562-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2f562-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
