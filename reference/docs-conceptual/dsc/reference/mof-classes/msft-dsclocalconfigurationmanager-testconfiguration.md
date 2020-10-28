---
ms.date: 07/17/2020
ms.topic: reference
title: TestConfiguration-metoden
description: TestConfiguration-metoden
ms.openlocfilehash: ed26fcad2286ca753fb4b1845b8c6ad0741d491b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648920"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="81df3-103">TestConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="81df3-103">TestConfiguration method</span></span>

<span data-ttu-id="81df3-104">Skickar konfigurations dokumentet till den hanterade noden och verifierar den aktuella konfigurationen mot dokumentet.</span><span class="sxs-lookup"><span data-stu-id="81df3-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="81df3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="81df3-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="81df3-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="81df3-106">Parameters</span></span>

<span data-ttu-id="81df3-107">**configurationData** \[ i \] miljö data för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81df3-107">**configurationData** \[in\] Environment data for the configuration.</span></span>

<span data-ttu-id="81df3-108">**InDesiredState** \[ ut \] vid retur anger om den hanterade noden är i det tillstånd som anges av konfigurations dokumentet.</span><span class="sxs-lookup"><span data-stu-id="81df3-108">**InDesiredState** \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="81df3-109">**ResourcesInDesiredState** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_ResourceInDesiredState** som anger vilka resurser som är i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="81df3-109">**ResourcesInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="81df3-110">**ResourcesNotInDesiredState** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_ResourceNotInDesiredState** som anger resurser som inte är i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="81df3-110">**ResourcesNotInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="81df3-111">Returvärde</span><span class="sxs-lookup"><span data-stu-id="81df3-111">Return value</span></span>

<span data-ttu-id="81df3-112">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="81df3-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="81df3-113">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="81df3-113">Remarks</span></span>

<span data-ttu-id="81df3-114">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="81df3-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="81df3-115">Krav</span><span class="sxs-lookup"><span data-stu-id="81df3-115">Requirements</span></span>

<span data-ttu-id="81df3-116">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="81df3-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="81df3-117">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="81df3-117">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="81df3-118">Se även</span><span class="sxs-lookup"><span data-stu-id="81df3-118">See also</span></span>

[<span data-ttu-id="81df3-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="81df3-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
