---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: GetMetaConfiguration-metoden
ms.openlocfilehash: 5111cb3b15e0fba0bf71b412580efdd3cd95b2dc
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463983"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="a7059-103">GetMetaConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="a7059-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="a7059-104">Hämtar de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="a7059-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="a7059-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7059-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="a7059-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a7059-106">Parameters</span></span>

<span data-ttu-id="a7059-107">**MetaConfiguration** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_DSCMetaConfiguration** som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="a7059-107">**MetaConfiguration** \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="a7059-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a7059-108">Return value</span></span>

<span data-ttu-id="a7059-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="a7059-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7059-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a7059-110">Remarks</span></span>

<span data-ttu-id="a7059-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a7059-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7059-112">Krav</span><span class="sxs-lookup"><span data-stu-id="a7059-112">Requirements</span></span>

<span data-ttu-id="a7059-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="a7059-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a7059-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7059-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a7059-115">Se även</span><span class="sxs-lookup"><span data-stu-id="a7059-115">See also</span></span>

[<span data-ttu-id="a7059-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a7059-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
