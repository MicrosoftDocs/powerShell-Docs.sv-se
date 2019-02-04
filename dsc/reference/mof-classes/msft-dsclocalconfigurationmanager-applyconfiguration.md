---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683914"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b269f-103">ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass</span><span class="sxs-lookup"><span data-stu-id="b269f-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b269f-104">Använder Configuration-agenten för att tillämpa konfigurationen som väntar.</span><span class="sxs-lookup"><span data-stu-id="b269f-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="b269f-105">Om det finns ingen konfiguration väntande, lägger den här metoden den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b269f-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="b269f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b269f-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b269f-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b269f-107">Parameters</span></span>

<span data-ttu-id="b269f-108">*Tvinga* \[i\] om det här är **SANT**, den aktuella konfigurationen används igen, även om det finns en konfiguration väntande.</span><span class="sxs-lookup"><span data-stu-id="b269f-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="b269f-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b269f-109">Return value</span></span>

<span data-ttu-id="b269f-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b269f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b269f-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b269f-111">Remarks</span></span>

<span data-ttu-id="b269f-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b269f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b269f-113">Krav</span><span class="sxs-lookup"><span data-stu-id="b269f-113">Requirements</span></span>

<span data-ttu-id="b269f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b269f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b269f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b269f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b269f-116">Se även</span><span class="sxs-lookup"><span data-stu-id="b269f-116">See also</span></span>

[<span data-ttu-id="b269f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b269f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)