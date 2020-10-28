---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceSet-metoden
description: ResourceSet-metoden
ms.openlocfilehash: 2554ff5805d7ed9518bd283565dc879a0fdfdfd0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650693"
---
# <a name="resourceset-method"></a><span data-ttu-id="f477d-103">ResourceSet-metoden</span><span class="sxs-lookup"><span data-stu-id="f477d-103">ResourceSet method</span></span>

<span data-ttu-id="f477d-104">Anropar **set** -metoden för en DSC-resurs direkt.</span><span class="sxs-lookup"><span data-stu-id="f477d-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="f477d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f477d-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="f477d-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f477d-106">Parameters</span></span>

<span data-ttu-id="f477d-107">**Resourcetype** \[ i \] namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="f477d-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f477d-108">**Modulnamn** \[ i \] namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="f477d-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f477d-109">**resourceProperty** \[ i \] anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel och värde respektive.</span><span class="sxs-lookup"><span data-stu-id="f477d-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f477d-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="f477d-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f477d-111">**RebootRequired** \[ ut \] vid retur anges den här egenskapen till **Sant** om målnoden måste startas om.</span><span class="sxs-lookup"><span data-stu-id="f477d-111">**RebootRequired** \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="f477d-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="f477d-112">Return value</span></span>

<span data-ttu-id="f477d-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="f477d-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f477d-114">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f477d-114">Remarks</span></span>

<span data-ttu-id="f477d-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="f477d-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f477d-116">Krav</span><span class="sxs-lookup"><span data-stu-id="f477d-116">Requirements</span></span>

<span data-ttu-id="f477d-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="f477d-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f477d-118">**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f477d-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f477d-119">Se även</span><span class="sxs-lookup"><span data-stu-id="f477d-119">See also</span></span>

[<span data-ttu-id="f477d-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f477d-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
