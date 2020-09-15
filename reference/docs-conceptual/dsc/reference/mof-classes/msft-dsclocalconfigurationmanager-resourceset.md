---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceSet-metoden
ms.openlocfilehash: c015960b2a5ffca0d28b714d571aa616400555bd
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464067"
---
# <a name="resourceset-method"></a><span data-ttu-id="6bc29-103">ResourceSet-metoden</span><span class="sxs-lookup"><span data-stu-id="6bc29-103">ResourceSet method</span></span>

<span data-ttu-id="6bc29-104">Anropar **set** -metoden för en DSC-resurs direkt.</span><span class="sxs-lookup"><span data-stu-id="6bc29-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bc29-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6bc29-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="6bc29-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="6bc29-106">Parameters</span></span>

<span data-ttu-id="6bc29-107">**Resourcetype** \[ i \] namnet på resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="6bc29-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="6bc29-108">**Modulnamn** \[ i \] namnet på den modul som innehåller resursen som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="6bc29-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="6bc29-109">**resourceProperty** \[ i \] anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel och värde respektive.</span><span class="sxs-lookup"><span data-stu-id="6bc29-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="6bc29-110">Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.</span><span class="sxs-lookup"><span data-stu-id="6bc29-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="6bc29-111">**RebootRequired** \[ ut \] vid retur anges den här egenskapen till **Sant** om målnoden måste startas om.</span><span class="sxs-lookup"><span data-stu-id="6bc29-111">**RebootRequired** \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="6bc29-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="6bc29-112">Return value</span></span>

<span data-ttu-id="6bc29-113">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="6bc29-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6bc29-114">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6bc29-114">Remarks</span></span>

<span data-ttu-id="6bc29-115">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="6bc29-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bc29-116">Krav</span><span class="sxs-lookup"><span data-stu-id="6bc29-116">Requirements</span></span>

<span data-ttu-id="6bc29-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="6bc29-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6bc29-118">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6bc29-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6bc29-119">Se även</span><span class="sxs-lookup"><span data-stu-id="6bc29-119">See also</span></span>

[<span data-ttu-id="6bc29-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6bc29-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
