---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceTest-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404702"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b1e34-103">ResourceTest-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="b1e34-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b1e34-104">Direkt anropar den **Test** -metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="b1e34-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1e34-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b1e34-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="b1e34-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="b1e34-106">Parameters</span></span>

<span data-ttu-id="b1e34-107">*ResourceType* \[i\] namnet på resursen att anropa.</span><span class="sxs-lookup"><span data-stu-id="b1e34-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="b1e34-108">*ModuleName* \[i\] namnet på den modul som innehåller resursen som ska anropa.</span><span class="sxs-lookup"><span data-stu-id="b1e34-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b1e34-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="b1e34-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b1e34-110">Använd den [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet för att identifiera resursegenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="b1e34-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b1e34-111">*InDesiredState* \[ut\] på RETUR, den här egenskapen anges **SANT** om Målnoden är i önskat läge.</span><span class="sxs-lookup"><span data-stu-id="b1e34-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="b1e34-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="b1e34-112">Return value</span></span>

<span data-ttu-id="b1e34-113">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="b1e34-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1e34-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b1e34-114">Remarks</span></span>

<span data-ttu-id="b1e34-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="b1e34-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1e34-116">Krav</span><span class="sxs-lookup"><span data-stu-id="b1e34-116">Requirements</span></span>

<span data-ttu-id="b1e34-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b1e34-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b1e34-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1e34-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b1e34-119">Se även</span><span class="sxs-lookup"><span data-stu-id="b1e34-119">See also</span></span>

[<span data-ttu-id="b1e34-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b1e34-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)