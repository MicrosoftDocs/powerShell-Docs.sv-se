---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: RollBack-metoden
ms.openlocfilehash: 301b8926d2ebf1ebe524f52a67928d34e26d860e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464340"
---
# <a name="rollback-method"></a><span data-ttu-id="9d104-103">RollBack-metoden</span><span class="sxs-lookup"><span data-stu-id="9d104-103">RollBack method</span></span>

<span data-ttu-id="9d104-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="9d104-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="9d104-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9d104-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="9d104-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="9d104-106">Parameters</span></span>

<span data-ttu-id="9d104-107">**configurationNumber** \[ i \] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="9d104-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d104-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="9d104-108">Return value</span></span>

<span data-ttu-id="9d104-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="9d104-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d104-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="9d104-110">Remarks</span></span>

<span data-ttu-id="9d104-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="9d104-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d104-112">Krav</span><span class="sxs-lookup"><span data-stu-id="9d104-112">Requirements</span></span>

<span data-ttu-id="9d104-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="9d104-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9d104-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9d104-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9d104-115">Se även</span><span class="sxs-lookup"><span data-stu-id="9d104-115">See also</span></span>

[<span data-ttu-id="9d104-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9d104-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
