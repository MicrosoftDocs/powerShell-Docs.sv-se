---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048729"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7a558-103">RollBack-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="7a558-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7a558-104">Återställer konfigurationen till en tidigare version.</span><span class="sxs-lookup"><span data-stu-id="7a558-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a558-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a558-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="7a558-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7a558-106">Parameters</span></span>

<span data-ttu-id="7a558-107">*configurationNumber* \[i\] anger den begärda konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="7a558-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a558-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="7a558-108">Return value</span></span>

<span data-ttu-id="7a558-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="7a558-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a558-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7a558-110">Remarks</span></span>

<span data-ttu-id="7a558-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="7a558-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a558-112">Krav</span><span class="sxs-lookup"><span data-stu-id="7a558-112">Requirements</span></span>

<span data-ttu-id="7a558-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a558-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7a558-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a558-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7a558-115">Se även</span><span class="sxs-lookup"><span data-stu-id="7a558-115">See also</span></span>

[<span data-ttu-id="7a558-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7a558-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)