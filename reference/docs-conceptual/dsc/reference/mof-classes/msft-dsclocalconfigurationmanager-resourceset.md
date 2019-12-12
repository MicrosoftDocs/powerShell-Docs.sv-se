---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceSet-metoden
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942652"
---
# <a name="resourceset-method"></a><span data-ttu-id="20d30-103">ResourceSet-metoden</span><span class="sxs-lookup"><span data-stu-id="20d30-103">ResourceSet method</span></span>

<span data-ttu-id="20d30-104">Anropar **set** -metoden för en DSC-resurs direkt.</span><span class="sxs-lookup"><span data-stu-id="20d30-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="20d30-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="20d30-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="20d30-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="20d30-106">Parameters</span></span>

<span data-ttu-id="20d30-107">*Resurs-\[i*\] namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="20d30-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="20d30-108">*Modulnamn* \[i\] namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="20d30-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="20d30-109">*resourceProperty* \[i\] anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde.</span><span class="sxs-lookup"><span data-stu-id="20d30-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="20d30-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="20d30-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="20d30-111">*RebootRequired* \[ut\] vid retur anges den här egenskapen till **Sant** om målnoden måste startas om.</span><span class="sxs-lookup"><span data-stu-id="20d30-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="20d30-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="20d30-112">Return value</span></span>

<span data-ttu-id="20d30-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="20d30-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="20d30-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="20d30-114">Remarks</span></span>

<span data-ttu-id="20d30-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="20d30-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="20d30-116">Krav</span><span class="sxs-lookup"><span data-stu-id="20d30-116">Requirements</span></span>

<span data-ttu-id="20d30-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="20d30-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="20d30-118">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="20d30-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="20d30-119">Se även</span><span class="sxs-lookup"><span data-stu-id="20d30-119">See also</span></span>

[<span data-ttu-id="20d30-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="20d30-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
