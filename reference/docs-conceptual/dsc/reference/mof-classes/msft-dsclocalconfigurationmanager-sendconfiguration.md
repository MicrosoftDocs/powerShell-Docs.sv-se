---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration-metoden
description: SendConfiguration-metoden
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650551"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="81bd9-103">SendConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="81bd9-103">SendConfiguration method</span></span>

<span data-ttu-id="81bd9-104">Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.</span><span class="sxs-lookup"><span data-stu-id="81bd9-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="81bd9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="81bd9-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="81bd9-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="81bd9-106">Parameters</span></span>

<span data-ttu-id="81bd9-107">**ConfigurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81bd9-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="81bd9-108">**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.</span><span class="sxs-lookup"><span data-stu-id="81bd9-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="81bd9-109">Returvärde</span><span class="sxs-lookup"><span data-stu-id="81bd9-109">Return value</span></span>

<span data-ttu-id="81bd9-110">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="81bd9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="81bd9-111">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="81bd9-111">Remarks</span></span>

<span data-ttu-id="81bd9-112">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="81bd9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="81bd9-113">Krav</span><span class="sxs-lookup"><span data-stu-id="81bd9-113">Requirements</span></span>

<span data-ttu-id="81bd9-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="81bd9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="81bd9-115">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="81bd9-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="81bd9-116">Se även</span><span class="sxs-lookup"><span data-stu-id="81bd9-116">See also</span></span>

[<span data-ttu-id="81bd9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="81bd9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
