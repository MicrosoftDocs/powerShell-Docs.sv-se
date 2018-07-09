---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceGet-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893213"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="62cac-103">ResourceGet-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="62cac-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="62cac-104">Direkt anropar den **hämta** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="62cac-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="62cac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="62cac-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="62cac-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="62cac-106">Parameters</span></span>

<span data-ttu-id="62cac-107">*ResourceType* \[i\] namnet på resursen att anropa.</span><span class="sxs-lookup"><span data-stu-id="62cac-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="62cac-108">*ModuleName* \[i\] namnet på den modul som innehåller resursen som ska anropa.</span><span class="sxs-lookup"><span data-stu-id="62cac-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="62cac-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="62cac-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="62cac-110">Använd den [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet för att identifiera resursegenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="62cac-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="62cac-111">*konfigurationer* \[ut\] på return innehåller en inbäddad förekomst av konfigurationerna.</span><span class="sxs-lookup"><span data-stu-id="62cac-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="62cac-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="62cac-112">Return value</span></span>

<span data-ttu-id="62cac-113">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="62cac-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="62cac-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="62cac-114">Remarks</span></span>

<span data-ttu-id="62cac-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="62cac-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="62cac-116">Krav</span><span class="sxs-lookup"><span data-stu-id="62cac-116">Requirements</span></span>

<span data-ttu-id="62cac-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="62cac-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="62cac-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="62cac-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="62cac-119">Se även</span><span class="sxs-lookup"><span data-stu-id="62cac-119">See also</span></span>

[<span data-ttu-id="62cac-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="62cac-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)