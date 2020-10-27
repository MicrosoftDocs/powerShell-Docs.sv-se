---
ms.date: 07/17/2020
ms.topic: reference
title: GetMetaConfiguration-metoden
description: GetMetaConfiguration-metoden
ms.openlocfilehash: deca6b8ec342a34543bbe0e1fabbc2a740a88feb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644720"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="9bd4b-103">GetMetaConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="9bd4b-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="9bd4b-104">Hämtar de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bd4b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bd4b-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="9bd4b-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9bd4b-106">Parameters</span></span>

<span data-ttu-id="9bd4b-107">**MetaConfiguration** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_DSCMetaConfiguration** som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="9bd4b-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="9bd4b-108">Return value</span></span>

<span data-ttu-id="9bd4b-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9bd4b-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9bd4b-110">Remarks</span></span>

<span data-ttu-id="9bd4b-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="9bd4b-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9bd4b-112">Krav</span><span class="sxs-lookup"><span data-stu-id="9bd4b-112">Requirements</span></span>

<span data-ttu-id="9bd4b-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="9bd4b-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9bd4b-114">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9bd4b-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9bd4b-115">Se även</span><span class="sxs-lookup"><span data-stu-id="9bd4b-115">See also</span></span>

[<span data-ttu-id="9bd4b-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9bd4b-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
