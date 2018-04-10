---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="24c71-103">ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass</span><span class="sxs-lookup"><span data-stu-id="24c71-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="24c71-104">Använder Configuration Agent för att använda den konfiguration som är i vänteläge.</span><span class="sxs-lookup"><span data-stu-id="24c71-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="24c71-105">Om det finns ingen konfiguration väntande, återställer den här metoden den aktuella konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="24c71-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="24c71-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="24c71-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="24c71-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="24c71-107">Parameters</span></span>
----------

<span data-ttu-id="24c71-108">*Tvinga* \[i\] om det här är **SANT**, den aktuella konfigurationen används igen, även om det finns en konfiguration väntande.</span><span class="sxs-lookup"><span data-stu-id="24c71-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="24c71-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="24c71-109">Return value</span></span>
------------

<span data-ttu-id="24c71-110">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="24c71-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24c71-111">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="24c71-111">Remarks</span></span>

<span data-ttu-id="24c71-112">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="24c71-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24c71-113">Krav</span><span class="sxs-lookup"><span data-stu-id="24c71-113">Requirements</span></span>
------------
><span data-ttu-id="24c71-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24c71-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="24c71-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24c71-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="24c71-116">Se även</span><span class="sxs-lookup"><span data-stu-id="24c71-116">See also</span></span>


[<span data-ttu-id="24c71-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="24c71-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)