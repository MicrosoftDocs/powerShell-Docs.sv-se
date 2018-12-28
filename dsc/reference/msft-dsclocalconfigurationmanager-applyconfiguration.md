---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405146"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a07d5-103">ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass</span><span class="sxs-lookup"><span data-stu-id="a07d5-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a07d5-104">Använder Configuration-agenten för att tillämpa konfigurationen som väntar.</span><span class="sxs-lookup"><span data-stu-id="a07d5-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="a07d5-105">Om det finns ingen konfiguration väntande, lägger den här metoden den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a07d5-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="a07d5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a07d5-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a07d5-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a07d5-107">Parameters</span></span>

<span data-ttu-id="a07d5-108">*Tvinga* \[i\] om det här är **SANT**, den aktuella konfigurationen används igen, även om det finns en konfiguration väntande.</span><span class="sxs-lookup"><span data-stu-id="a07d5-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="a07d5-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a07d5-109">Return value</span></span>

<span data-ttu-id="a07d5-110">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a07d5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a07d5-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a07d5-111">Remarks</span></span>

<span data-ttu-id="a07d5-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a07d5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a07d5-113">Krav</span><span class="sxs-lookup"><span data-stu-id="a07d5-113">Requirements</span></span>

<span data-ttu-id="a07d5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a07d5-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a07d5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a07d5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a07d5-116">Se även</span><span class="sxs-lookup"><span data-stu-id="a07d5-116">See also</span></span>

[<span data-ttu-id="a07d5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a07d5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)