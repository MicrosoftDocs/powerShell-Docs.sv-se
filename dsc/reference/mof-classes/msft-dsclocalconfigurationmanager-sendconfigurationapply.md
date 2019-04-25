---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078268"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="0362f-103">SendConfigurationApply-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="0362f-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="0362f-104">Skickar konfigurationsdokumentet till hanterad nod och använder konfigurationen agenten för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0362f-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0362f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0362f-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0362f-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0362f-106">Parameters</span></span>

<span data-ttu-id="0362f-107">*ConfigurationData* \[i\] miljödata om konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0362f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0362f-108">*Tvinga* \[i\] **SANT** att tvinga konfigurationen att stoppa.</span><span class="sxs-lookup"><span data-stu-id="0362f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0362f-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="0362f-109">Return value</span></span>

<span data-ttu-id="0362f-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="0362f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0362f-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0362f-111">Remarks</span></span>

<span data-ttu-id="0362f-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="0362f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0362f-113">Krav</span><span class="sxs-lookup"><span data-stu-id="0362f-113">Requirements</span></span>

<span data-ttu-id="0362f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0362f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0362f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0362f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0362f-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0362f-116">See also</span></span>

[<span data-ttu-id="0362f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0362f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)