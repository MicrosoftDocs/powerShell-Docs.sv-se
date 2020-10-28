---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceTest-metoden
description: ResourceTest-metoden
ms.openlocfilehash: cbac53ea96a59ec92fa840f75cd264a3125b965a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650672"
---
# <a name="resourcetest-method"></a><span data-ttu-id="d9646-103">ResourceTest-metoden</span><span class="sxs-lookup"><span data-stu-id="d9646-103">ResourceTest method</span></span>

<span data-ttu-id="d9646-104">Anropar direkt **test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d9646-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9646-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9646-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="d9646-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d9646-106">Parameters</span></span>

<span data-ttu-id="d9646-107">**Resourcetype** \[ i \] namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="d9646-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="d9646-108">**Modulnamn** \[ i \] namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="d9646-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="d9646-109">\**_resourceProperty_* \[ i \] anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel och värde respektive.</span><span class="sxs-lookup"><span data-stu-id="d9646-109">\**_resourceProperty_* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="d9646-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="d9646-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="d9646-111">*InDesiredState* \*  InDesiredState \[ ut \] vid retur anges den här egenskapen till **Sant** om målnoden är i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="d9646-111">*InDesiredState*\* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="d9646-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d9646-112">Return value</span></span>

<span data-ttu-id="d9646-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="d9646-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9646-114">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d9646-114">Remarks</span></span>

<span data-ttu-id="d9646-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d9646-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9646-116">Krav</span><span class="sxs-lookup"><span data-stu-id="d9646-116">Requirements</span></span>

<span data-ttu-id="d9646-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="d9646-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d9646-118">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d9646-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d9646-119">Se även</span><span class="sxs-lookup"><span data-stu-id="d9646-119">See also</span></span>

[<span data-ttu-id="d9646-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d9646-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
