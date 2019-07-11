---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727101"
---
# <a name="resourceset-method"></a><span data-ttu-id="905b1-103">ResourceSet-metoden</span><span class="sxs-lookup"><span data-stu-id="905b1-103">ResourceSet method</span></span>

<span data-ttu-id="905b1-104">Direkt anropar den **ange** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="905b1-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="905b1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="905b1-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="905b1-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="905b1-106">Parameters</span></span>

<span data-ttu-id="905b1-107">*ResourceType* \[i\] namnet på resursen att anropa.</span><span class="sxs-lookup"><span data-stu-id="905b1-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="905b1-108">*ModuleName* \[i\] namnet på den modul som innehåller resursen som ska anropa.</span><span class="sxs-lookup"><span data-stu-id="905b1-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="905b1-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="905b1-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="905b1-110">Använd den [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet för att identifiera resursegenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="905b1-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="905b1-111">*RebootRequired* \[ut\] på RETUR, den här egenskapen anges **SANT** om målnoden måste startas.</span><span class="sxs-lookup"><span data-stu-id="905b1-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="905b1-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="905b1-112">Return value</span></span>

<span data-ttu-id="905b1-113">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="905b1-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="905b1-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="905b1-114">Remarks</span></span>

<span data-ttu-id="905b1-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="905b1-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="905b1-116">Krav</span><span class="sxs-lookup"><span data-stu-id="905b1-116">Requirements</span></span>

<span data-ttu-id="905b1-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="905b1-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="905b1-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="905b1-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="905b1-119">Se även</span><span class="sxs-lookup"><span data-stu-id="905b1-119">See also</span></span>

[<span data-ttu-id="905b1-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="905b1-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
