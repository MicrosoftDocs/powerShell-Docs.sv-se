---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727019"
---
# <a name="rollback-method"></a><span data-ttu-id="b2d5d-103">RollBack-metoden</span><span class="sxs-lookup"><span data-stu-id="b2d5d-103">RollBack method</span></span>

<span data-ttu-id="b2d5d-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="b2d5d-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2d5d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2d5d-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="b2d5d-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b2d5d-106">Parameters</span></span>

<span data-ttu-id="b2d5d-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b2d5d-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b2d5d-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b2d5d-108">Return value</span></span>

<span data-ttu-id="b2d5d-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b2d5d-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2d5d-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b2d5d-110">Remarks</span></span>

<span data-ttu-id="b2d5d-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b2d5d-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2d5d-112">Krav</span><span class="sxs-lookup"><span data-stu-id="b2d5d-112">Requirements</span></span>

<span data-ttu-id="b2d5d-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b2d5d-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b2d5d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2d5d-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b2d5d-115">Se även</span><span class="sxs-lookup"><span data-stu-id="b2d5d-115">See also</span></span>

[<span data-ttu-id="b2d5d-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b2d5d-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
