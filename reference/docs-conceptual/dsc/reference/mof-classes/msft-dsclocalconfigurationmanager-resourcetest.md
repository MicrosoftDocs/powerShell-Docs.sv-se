---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceTest-metoden
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942645"
---
# <a name="resourcetest-method"></a><span data-ttu-id="599fd-103">ResourceTest-metoden</span><span class="sxs-lookup"><span data-stu-id="599fd-103">ResourceTest method</span></span>

<span data-ttu-id="599fd-104">Anropar direkt **test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="599fd-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="599fd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="599fd-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="599fd-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="599fd-106">Parameters</span></span>

<span data-ttu-id="599fd-107">*Resurs-\[i*\] namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="599fd-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="599fd-108">*Modulnamn* \[i\] namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="599fd-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="599fd-109">*resourceProperty* \[i\] anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="599fd-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="599fd-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="599fd-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="599fd-111">*InDesiredState* \[ut\] vid retur anges den här egenskapen till **Sant** om målnoden är i önskat tillstånd.</span><span class="sxs-lookup"><span data-stu-id="599fd-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="599fd-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="599fd-112">Return value</span></span>

<span data-ttu-id="599fd-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="599fd-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="599fd-114">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="599fd-114">Remarks</span></span>

<span data-ttu-id="599fd-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="599fd-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="599fd-116">Krav</span><span class="sxs-lookup"><span data-stu-id="599fd-116">Requirements</span></span>

<span data-ttu-id="599fd-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="599fd-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="599fd-118">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="599fd-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="599fd-119">Se också</span><span class="sxs-lookup"><span data-stu-id="599fd-119">See also</span></span>

[<span data-ttu-id="599fd-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="599fd-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
