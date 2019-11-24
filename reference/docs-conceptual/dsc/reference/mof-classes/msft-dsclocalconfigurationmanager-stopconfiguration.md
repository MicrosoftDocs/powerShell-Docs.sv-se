---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: StopConfiguration-metoden
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941532"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="41633-103">StopConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="41633-103">StopConfiguration method</span></span>

<span data-ttu-id="41633-104">Stoppar den konfigurations ändring som pågår.</span><span class="sxs-lookup"><span data-stu-id="41633-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="41633-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="41633-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="41633-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="41633-106">Parameters</span></span>

<span data-ttu-id="41633-107">*tvinga* \[i\] **Sant** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="41633-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="41633-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="41633-108">Return value</span></span>

<span data-ttu-id="41633-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="41633-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="41633-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="41633-110">Remarks</span></span>

<span data-ttu-id="41633-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="41633-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="41633-112">Krav</span><span class="sxs-lookup"><span data-stu-id="41633-112">Requirements</span></span>

<span data-ttu-id="41633-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="41633-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="41633-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="41633-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="41633-115">Se också</span><span class="sxs-lookup"><span data-stu-id="41633-115">See also</span></span>

[<span data-ttu-id="41633-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="41633-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
