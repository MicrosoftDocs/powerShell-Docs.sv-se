---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceGet-metoden
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942680"
---
# <a name="resourceget-method"></a><span data-ttu-id="37ea4-103">ResourceGet-metoden</span><span class="sxs-lookup"><span data-stu-id="37ea4-103">ResourceGet method</span></span>

<span data-ttu-id="37ea4-104">Anropar direkt **Get** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="37ea4-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="37ea4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="37ea4-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="37ea4-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="37ea4-106">Parameters</span></span>

<span data-ttu-id="37ea4-107">*ResourceType* \[in @ no__t-2 namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="37ea4-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="37ea4-108">*Modulnamn* \[in @ no__t-2 namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="37ea4-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="37ea4-109">*resourceProperty* \[in @ no__t-2 anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="37ea4-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="37ea4-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="37ea4-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="37ea4-111">*konfigurationer* \[out @ no__t-2 vid retur, innehåller en inbäddad instans av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="37ea4-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="37ea4-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="37ea4-112">Return value</span></span>

<span data-ttu-id="37ea4-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="37ea4-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="37ea4-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="37ea4-114">Remarks</span></span>

<span data-ttu-id="37ea4-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="37ea4-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="37ea4-116">Krav</span><span class="sxs-lookup"><span data-stu-id="37ea4-116">Requirements</span></span>

<span data-ttu-id="37ea4-117">**-** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="37ea4-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="37ea4-118">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="37ea4-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="37ea4-119">Se även</span><span class="sxs-lookup"><span data-stu-id="37ea4-119">See also</span></span>

[<span data-ttu-id="37ea4-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="37ea4-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
