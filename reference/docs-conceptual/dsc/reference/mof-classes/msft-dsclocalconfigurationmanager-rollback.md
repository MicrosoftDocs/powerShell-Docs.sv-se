---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: RollBack-metoden
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942638"
---
# <a name="rollback-method"></a><span data-ttu-id="b0786-103">RollBack-metoden</span><span class="sxs-lookup"><span data-stu-id="b0786-103">RollBack method</span></span>

<span data-ttu-id="b0786-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="b0786-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0786-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0786-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="b0786-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b0786-106">Parameters</span></span>

<span data-ttu-id="b0786-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b0786-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0786-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b0786-108">Return value</span></span>

<span data-ttu-id="b0786-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="b0786-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0786-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b0786-110">Remarks</span></span>

<span data-ttu-id="b0786-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b0786-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0786-112">Krav</span><span class="sxs-lookup"><span data-stu-id="b0786-112">Requirements</span></span>

<span data-ttu-id="b0786-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="b0786-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b0786-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0786-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b0786-115">Se också</span><span class="sxs-lookup"><span data-stu-id="b0786-115">See also</span></span>

[<span data-ttu-id="b0786-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0786-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
