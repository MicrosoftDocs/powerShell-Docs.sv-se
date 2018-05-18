---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceGet-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bc5a7-103">ResourceGet-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="bc5a7-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bc5a7-104">Direkt anropar den **hämta** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="bc5a7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc5a7-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="bc5a7-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="bc5a7-106">Parameters</span></span>
----------

<span data-ttu-id="bc5a7-107">*ResourceType* \[i\] namnet på resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="bc5a7-108">*Modulnamn* \[i\] namnet på den modul som innehåller resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="bc5a7-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="bc5a7-110">Använd den [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="bc5a7-111">*konfigurationer* \[ut\] på RETUR, innehåller en inbäddad instans av konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc5a7-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="bc5a7-112">Return value</span></span>
------------

<span data-ttu-id="bc5a7-113">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bc5a7-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bc5a7-114">Remarks</span></span>

<span data-ttu-id="bc5a7-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="bc5a7-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc5a7-116">Krav</span><span class="sxs-lookup"><span data-stu-id="bc5a7-116">Requirements</span></span>
------------
><span data-ttu-id="bc5a7-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bc5a7-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bc5a7-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bc5a7-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bc5a7-119">Se även</span><span class="sxs-lookup"><span data-stu-id="bc5a7-119">See also</span></span>


[<span data-ttu-id="bc5a7-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bc5a7-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)