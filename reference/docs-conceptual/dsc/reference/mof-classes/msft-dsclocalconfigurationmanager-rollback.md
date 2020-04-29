---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: RollBack-metoden
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942638"
---
# <a name="rollback-method"></a><span data-ttu-id="2c63a-103">RollBack-metoden</span><span class="sxs-lookup"><span data-stu-id="2c63a-103">RollBack method</span></span>

<span data-ttu-id="2c63a-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="2c63a-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c63a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c63a-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="2c63a-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2c63a-106">Parameters</span></span>

<span data-ttu-id="2c63a-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2c63a-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="2c63a-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="2c63a-108">Return value</span></span>

<span data-ttu-id="2c63a-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="2c63a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c63a-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2c63a-110">Remarks</span></span>

<span data-ttu-id="2c63a-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="2c63a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c63a-112">Krav</span><span class="sxs-lookup"><span data-stu-id="2c63a-112">Requirements</span></span>

<span data-ttu-id="2c63a-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="2c63a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2c63a-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c63a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2c63a-115">Se även</span><span class="sxs-lookup"><span data-stu-id="2c63a-115">See also</span></span>

[<span data-ttu-id="2c63a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2c63a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
