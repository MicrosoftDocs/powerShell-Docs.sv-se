---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceGet-metoden
ms.openlocfilehash: aa7671989db6f4a98d879fd449d09503eddbeda3
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463966"
---
# <a name="resourceget-method"></a><span data-ttu-id="199fc-103">ResourceGet-metoden</span><span class="sxs-lookup"><span data-stu-id="199fc-103">ResourceGet method</span></span>

<span data-ttu-id="199fc-104">Anropar direkt **Get** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="199fc-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="199fc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="199fc-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="199fc-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="199fc-106">Parameters</span></span>

<span data-ttu-id="199fc-107">**Resourcetype** \[ i \] namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="199fc-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="199fc-108">**Modulnamn** \[ i \] namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="199fc-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="199fc-109">**resourceProperty** \[ i \] anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel och värde respektive.</span><span class="sxs-lookup"><span data-stu-id="199fc-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="199fc-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="199fc-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="199fc-111">**konfigurationer** \[ ut \] vid retur innehåller en inbäddad instans av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="199fc-111">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="199fc-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="199fc-112">Return value</span></span>

<span data-ttu-id="199fc-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="199fc-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="199fc-114">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="199fc-114">Remarks</span></span>

<span data-ttu-id="199fc-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="199fc-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="199fc-116">Krav</span><span class="sxs-lookup"><span data-stu-id="199fc-116">Requirements</span></span>

<span data-ttu-id="199fc-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="199fc-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="199fc-118">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="199fc-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="199fc-119">Se även</span><span class="sxs-lookup"><span data-stu-id="199fc-119">See also</span></span>

[<span data-ttu-id="199fc-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="199fc-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
