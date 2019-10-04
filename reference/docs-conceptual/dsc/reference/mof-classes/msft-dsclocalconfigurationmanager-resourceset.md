---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceSet-metoden
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942652"
---
# <a name="resourceset-method"></a><span data-ttu-id="ace17-103">ResourceSet-metoden</span><span class="sxs-lookup"><span data-stu-id="ace17-103">ResourceSet method</span></span>

<span data-ttu-id="ace17-104">Anropar **set** -metoden för en DSC-resurs direkt.</span><span class="sxs-lookup"><span data-stu-id="ace17-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="ace17-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ace17-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="ace17-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="ace17-106">Parameters</span></span>

<span data-ttu-id="ace17-107">*ResourceType* \[in @ no__t-2 namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="ace17-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="ace17-108">*Modulnamn* \[in @ no__t-2 namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="ace17-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="ace17-109">*resourceProperty* \[in @ no__t-2 anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="ace17-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="ace17-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="ace17-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="ace17-111">*RebootRequired* \[out @ no__t-2 vid retur anges den här egenskapen till **Sant** om målnoden måste startas om.</span><span class="sxs-lookup"><span data-stu-id="ace17-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="ace17-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="ace17-112">Return value</span></span>

<span data-ttu-id="ace17-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="ace17-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ace17-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ace17-114">Remarks</span></span>

<span data-ttu-id="ace17-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="ace17-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ace17-116">Krav</span><span class="sxs-lookup"><span data-stu-id="ace17-116">Requirements</span></span>

<span data-ttu-id="ace17-117">**-** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ace17-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ace17-118">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ace17-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ace17-119">Se även</span><span class="sxs-lookup"><span data-stu-id="ace17-119">See also</span></span>

[<span data-ttu-id="ace17-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ace17-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
