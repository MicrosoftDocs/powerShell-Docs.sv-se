---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceGet-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: df90cb6859413c94be992c8cbc30171e9bd3d6de
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d6a53-103">ResourceGet-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d6a53-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d6a53-104">Direkt anropar den **hämta** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="d6a53-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="d6a53-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d6a53-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="d6a53-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d6a53-106">Parameters</span></span>
----------

<span data-ttu-id="d6a53-107">*ResourceType* \[i\]</span><span class="sxs-lookup"><span data-stu-id="d6a53-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="d6a53-108">Namnet på resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="d6a53-108">The name of the resource to call.</span></span>

<span data-ttu-id="d6a53-109">*Modulnamn* \[i\]</span><span class="sxs-lookup"><span data-stu-id="d6a53-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="d6a53-110">Namnet på den modul som innehåller resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="d6a53-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="d6a53-111">*resourceProperty* \[i\]</span><span class="sxs-lookup"><span data-stu-id="d6a53-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="d6a53-112">Anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="d6a53-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="d6a53-113">Använd den [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.</span><span class="sxs-lookup"><span data-stu-id="d6a53-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="d6a53-114">*konfigurationer* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="d6a53-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="d6a53-115">Innehåller en inbäddad instans av konfigurationerna på return.</span><span class="sxs-lookup"><span data-stu-id="d6a53-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6a53-116">Returvärde</span><span class="sxs-lookup"><span data-stu-id="d6a53-116">Return value</span></span>
------------

<span data-ttu-id="d6a53-117">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="d6a53-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6a53-118">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d6a53-118">Remarks</span></span>

<span data-ttu-id="d6a53-119">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="d6a53-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6a53-120">Krav</span><span class="sxs-lookup"><span data-stu-id="d6a53-120">Requirements</span></span>
------------
><span data-ttu-id="d6a53-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d6a53-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d6a53-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6a53-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d6a53-123">Se även</span><span class="sxs-lookup"><span data-stu-id="d6a53-123">See also</span></span>


[<span data-ttu-id="d6a53-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6a53-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



