---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceGet-metoden
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727111"
---
# <a name="resourceget-method"></a><span data-ttu-id="a9450-103">ResourceGet-metoden</span><span class="sxs-lookup"><span data-stu-id="a9450-103">ResourceGet method</span></span>

<span data-ttu-id="a9450-104">Direkt anropar den **hämta** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="a9450-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9450-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a9450-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="a9450-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="a9450-106">Parameters</span></span>

<span data-ttu-id="a9450-107">*ResourceType* \[i\] namnet på resursen att anropa.</span><span class="sxs-lookup"><span data-stu-id="a9450-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="a9450-108">*ModuleName* \[i\] namnet på den modul som innehåller resursen som ska anropa.</span><span class="sxs-lookup"><span data-stu-id="a9450-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="a9450-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="a9450-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="a9450-110">Använd den [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet för att identifiera resursegenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="a9450-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="a9450-111">*konfigurationer* \[ut\] på return innehåller en inbäddad förekomst av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="a9450-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9450-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="a9450-112">Return value</span></span>

<span data-ttu-id="a9450-113">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="a9450-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9450-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a9450-114">Remarks</span></span>

<span data-ttu-id="a9450-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="a9450-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9450-116">Krav</span><span class="sxs-lookup"><span data-stu-id="a9450-116">Requirements</span></span>

<span data-ttu-id="a9450-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9450-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a9450-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9450-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a9450-119">Se även</span><span class="sxs-lookup"><span data-stu-id="a9450-119">See also</span></span>

[<span data-ttu-id="a9450-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a9450-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
