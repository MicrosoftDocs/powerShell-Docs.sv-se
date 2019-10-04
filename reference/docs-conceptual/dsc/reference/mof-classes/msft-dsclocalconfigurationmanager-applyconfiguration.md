---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ApplyConfiguration-metoden
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941602"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="f2cfa-103">ApplyConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="f2cfa-103">ApplyConfiguration method</span></span>

<span data-ttu-id="f2cfa-104">Använder konfigurations agenten för att tillämpa den konfiguration som väntar.</span><span class="sxs-lookup"><span data-stu-id="f2cfa-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="f2cfa-105">Om det inte finns någon väntande konfiguration, tillämpar den här metoden den aktuella konfigurationen igen.</span><span class="sxs-lookup"><span data-stu-id="f2cfa-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2cfa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f2cfa-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f2cfa-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f2cfa-107">Parameters</span></span>

<span data-ttu-id="f2cfa-108">*tvinga* \[in @ no__t-2 om detta är **Sant**tillämpas den aktuella konfigurationen igen, även om det finns en väntande konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f2cfa-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2cfa-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="f2cfa-109">Return value</span></span>

<span data-ttu-id="f2cfa-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="f2cfa-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2cfa-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f2cfa-111">Remarks</span></span>

<span data-ttu-id="f2cfa-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="f2cfa-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2cfa-113">Krav</span><span class="sxs-lookup"><span data-stu-id="f2cfa-113">Requirements</span></span>

<span data-ttu-id="f2cfa-114">**-** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="f2cfa-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f2cfa-115">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2cfa-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f2cfa-116">Se även</span><span class="sxs-lookup"><span data-stu-id="f2cfa-116">See also</span></span>

[<span data-ttu-id="f2cfa-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f2cfa-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
