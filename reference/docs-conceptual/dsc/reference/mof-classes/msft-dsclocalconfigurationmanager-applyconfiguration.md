---
ms.date: 07/14/2020
keywords: DSC, PowerShell, konfiguration, installation
title: ApplyConfiguration-metoden
ms.openlocfilehash: bec74ccd6f75448484adfd26bf8a4af4e224eb3f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463847"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="5d418-103">ApplyConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="5d418-103">ApplyConfiguration method</span></span>

<span data-ttu-id="5d418-104">Använder konfigurations agenten för att tillämpa den konfiguration som väntar.</span><span class="sxs-lookup"><span data-stu-id="5d418-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="5d418-105">Om det inte finns någon väntande konfiguration, tillämpar den här metoden den aktuella konfigurationen igen.</span><span class="sxs-lookup"><span data-stu-id="5d418-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d418-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d418-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5d418-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="5d418-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="5d418-108">inför</span><span class="sxs-lookup"><span data-stu-id="5d418-108">force</span></span>

<span data-ttu-id="5d418-109">Om detta är **Sant**tillämpas den aktuella konfigurationen igen, även om det finns en väntande konfiguration.</span><span class="sxs-lookup"><span data-stu-id="5d418-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d418-110">Returvärde</span><span class="sxs-lookup"><span data-stu-id="5d418-110">Return value</span></span>

<span data-ttu-id="5d418-111">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="5d418-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d418-112">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5d418-112">Remarks</span></span>

<span data-ttu-id="5d418-113">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="5d418-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d418-114">Krav</span><span class="sxs-lookup"><span data-stu-id="5d418-114">Requirements</span></span>

<span data-ttu-id="5d418-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="5d418-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5d418-116">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d418-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5d418-117">Se även</span><span class="sxs-lookup"><span data-stu-id="5d418-117">See also</span></span>

[<span data-ttu-id="5d418-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5d418-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
