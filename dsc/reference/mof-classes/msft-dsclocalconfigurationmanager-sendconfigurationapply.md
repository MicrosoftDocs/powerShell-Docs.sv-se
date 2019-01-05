---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048621"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="09db7-103">SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="09db7-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="09db7-104">Skickar konfigurationsdokumentet till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="09db7-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="09db7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="09db7-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="09db7-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="09db7-106">Parameters</span></span>

<span data-ttu-id="09db7-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="09db7-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="09db7-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="09db7-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="09db7-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="09db7-109">Return value</span></span>

<span data-ttu-id="09db7-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="09db7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="09db7-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="09db7-111">Remarks</span></span>

<span data-ttu-id="09db7-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="09db7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="09db7-113">Krav</span><span class="sxs-lookup"><span data-stu-id="09db7-113">Requirements</span></span>

<span data-ttu-id="09db7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="09db7-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="09db7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="09db7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="09db7-116">Se även</span><span class="sxs-lookup"><span data-stu-id="09db7-116">See also</span></span>

[<span data-ttu-id="09db7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="09db7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)