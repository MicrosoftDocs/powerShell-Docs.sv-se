---
ms.date: 07/17/2020
ms.topic: reference
title: RollBack-metoden
description: RollBack-metoden
ms.openlocfilehash: 82ca54ed23a3a892b785f603be3b423def5ee636
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650618"
---
# <a name="rollback-method"></a><span data-ttu-id="0cd81-103">RollBack-metoden</span><span class="sxs-lookup"><span data-stu-id="0cd81-103">RollBack method</span></span>

<span data-ttu-id="0cd81-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="0cd81-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="0cd81-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0cd81-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="0cd81-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="0cd81-106">Parameters</span></span>

<span data-ttu-id="0cd81-107">**configurationNumber** \[ i \] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0cd81-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="0cd81-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="0cd81-108">Return value</span></span>

<span data-ttu-id="0cd81-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="0cd81-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0cd81-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0cd81-110">Remarks</span></span>

<span data-ttu-id="0cd81-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="0cd81-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0cd81-112">Krav</span><span class="sxs-lookup"><span data-stu-id="0cd81-112">Requirements</span></span>

<span data-ttu-id="0cd81-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="0cd81-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0cd81-114">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0cd81-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0cd81-115">Se även</span><span class="sxs-lookup"><span data-stu-id="0cd81-115">See also</span></span>

[<span data-ttu-id="0cd81-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0cd81-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
