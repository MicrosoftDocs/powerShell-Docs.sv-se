---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="fb80c-103">ResourceSet-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="fb80c-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="fb80c-104">Direkt anropar den **ange** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="fb80c-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="fb80c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fb80c-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="fb80c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="fb80c-106">Parameters</span></span>
----------

<span data-ttu-id="fb80c-107">*ResourceType* \[i\]</span><span class="sxs-lookup"><span data-stu-id="fb80c-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="fb80c-108">Namnet på resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="fb80c-108">The name of the resource to call.</span></span>

<span data-ttu-id="fb80c-109">*Modulnamn* \[i\]</span><span class="sxs-lookup"><span data-stu-id="fb80c-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="fb80c-110">Namnet på den modul som innehåller resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="fb80c-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="fb80c-111">*resourceProperty* \[i\]</span><span class="sxs-lookup"><span data-stu-id="fb80c-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="fb80c-112">Anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="fb80c-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="fb80c-113">Använd den [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.</span><span class="sxs-lookup"><span data-stu-id="fb80c-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="fb80c-114">*RebootRequired* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="fb80c-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="fb80c-115">På RETUR, ange den här egenskapen är **SANT** om målnoden måste startas om.</span><span class="sxs-lookup"><span data-stu-id="fb80c-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb80c-116">Returvärde</span><span class="sxs-lookup"><span data-stu-id="fb80c-116">Return value</span></span>
------------

<span data-ttu-id="fb80c-117">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="fb80c-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb80c-118">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="fb80c-118">Remarks</span></span>

<span data-ttu-id="fb80c-119">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="fb80c-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb80c-120">Krav</span><span class="sxs-lookup"><span data-stu-id="fb80c-120">Requirements</span></span>
------------
><span data-ttu-id="fb80c-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fb80c-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="fb80c-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fb80c-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="fb80c-123">Se även</span><span class="sxs-lookup"><span data-stu-id="fb80c-123">See also</span></span>


[<span data-ttu-id="fb80c-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fb80c-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



