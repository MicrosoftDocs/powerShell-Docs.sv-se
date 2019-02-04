---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688583"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="22910-103">RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="22910-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="22910-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="22910-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="22910-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="22910-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="22910-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="22910-106">Parameters</span></span>

<span data-ttu-id="22910-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="22910-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="22910-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="22910-108">Return value</span></span>

<span data-ttu-id="22910-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="22910-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="22910-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="22910-110">Remarks</span></span>

<span data-ttu-id="22910-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="22910-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="22910-112">Krav</span><span class="sxs-lookup"><span data-stu-id="22910-112">Requirements</span></span>

<span data-ttu-id="22910-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="22910-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="22910-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="22910-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="22910-115">Se även</span><span class="sxs-lookup"><span data-stu-id="22910-115">See also</span></span>

[<span data-ttu-id="22910-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="22910-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)