---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceTest-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="477ac-103">ResourceTest-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="477ac-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="477ac-104">Direkt anropar den **Test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="477ac-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="477ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="477ac-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="477ac-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="477ac-106">Parameters</span></span>
----------

<span data-ttu-id="477ac-107">*ResourceType* \[i\]</span><span class="sxs-lookup"><span data-stu-id="477ac-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="477ac-108">Namnet på resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="477ac-108">The name of the resource to call.</span></span>

<span data-ttu-id="477ac-109">*Modulnamn* \[i\]</span><span class="sxs-lookup"><span data-stu-id="477ac-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="477ac-110">Namnet på den modul som innehåller resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="477ac-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="477ac-111">*resourceProperty* \[i\]</span><span class="sxs-lookup"><span data-stu-id="477ac-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="477ac-112">Anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="477ac-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="477ac-113">Använd den [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.</span><span class="sxs-lookup"><span data-stu-id="477ac-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="477ac-114">*InDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="477ac-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="477ac-115">På RETUR, ange den här egenskapen är **SANT** om Målnoden är i tillståndet önskade.</span><span class="sxs-lookup"><span data-stu-id="477ac-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="477ac-116">Returvärde</span><span class="sxs-lookup"><span data-stu-id="477ac-116">Return value</span></span>
------------

<span data-ttu-id="477ac-117">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="477ac-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="477ac-118">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="477ac-118">Remarks</span></span>

<span data-ttu-id="477ac-119">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="477ac-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="477ac-120">Krav</span><span class="sxs-lookup"><span data-stu-id="477ac-120">Requirements</span></span>
------------
><span data-ttu-id="477ac-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="477ac-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="477ac-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="477ac-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="477ac-123">Se även</span><span class="sxs-lookup"><span data-stu-id="477ac-123">See also</span></span>


[<span data-ttu-id="477ac-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="477ac-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



