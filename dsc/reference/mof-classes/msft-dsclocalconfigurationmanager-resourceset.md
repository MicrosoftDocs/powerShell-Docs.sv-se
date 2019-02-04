---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685468"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="af92f-103">ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="af92f-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="af92f-104">Direkt anropar den **ange** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="af92f-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="af92f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="af92f-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="af92f-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="af92f-106">Parameters</span></span>

<span data-ttu-id="af92f-107">*ResourceType* \[i\] namnet på resursen att anropa.</span><span class="sxs-lookup"><span data-stu-id="af92f-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="af92f-108">*ModuleName* \[i\] namnet på den modul som innehåller resursen som ska anropa.</span><span class="sxs-lookup"><span data-stu-id="af92f-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="af92f-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="af92f-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="af92f-110">Använd den [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet för att identifiera resursegenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="af92f-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="af92f-111">*RebootRequired* \[ut\] på RETUR, den här egenskapen anges **SANT** om målnoden måste startas.</span><span class="sxs-lookup"><span data-stu-id="af92f-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="af92f-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="af92f-112">Return value</span></span>

<span data-ttu-id="af92f-113">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="af92f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="af92f-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="af92f-114">Remarks</span></span>

<span data-ttu-id="af92f-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="af92f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="af92f-116">Krav</span><span class="sxs-lookup"><span data-stu-id="af92f-116">Requirements</span></span>

<span data-ttu-id="af92f-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="af92f-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="af92f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="af92f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="af92f-119">Se även</span><span class="sxs-lookup"><span data-stu-id="af92f-119">See also</span></span>

[<span data-ttu-id="af92f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="af92f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)