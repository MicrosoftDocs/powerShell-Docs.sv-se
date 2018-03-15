---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceTest-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 799b1cd91dfacf25c0e5e734ca96d20a776103f0
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="34ccd-103">ResourceTest-metoden i klassen MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="34ccd-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="34ccd-104">Direkt anropar den **Test** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="34ccd-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="34ccd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="34ccd-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="34ccd-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="34ccd-106">Parameters</span></span>
----------

<span data-ttu-id="34ccd-107">*ResourceType* \[i\]</span><span class="sxs-lookup"><span data-stu-id="34ccd-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="34ccd-108">Namnet på resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="34ccd-108">The name of the resource to call.</span></span>

<span data-ttu-id="34ccd-109">*Modulnamn* \[i\]</span><span class="sxs-lookup"><span data-stu-id="34ccd-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="34ccd-110">Namnet på den modul som innehåller resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="34ccd-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="34ccd-111">*resourceProperty* \[i\]</span><span class="sxs-lookup"><span data-stu-id="34ccd-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="34ccd-112">Anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="34ccd-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="34ccd-113">Använd den [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.</span><span class="sxs-lookup"><span data-stu-id="34ccd-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="34ccd-114">*InDesiredState* \[ut\]</span><span class="sxs-lookup"><span data-stu-id="34ccd-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="34ccd-115">På RETUR, ange den här egenskapen är **SANT** om Målnoden är i tillståndet önskade.</span><span class="sxs-lookup"><span data-stu-id="34ccd-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="34ccd-116">Returvärde</span><span class="sxs-lookup"><span data-stu-id="34ccd-116">Return value</span></span>
------------

<span data-ttu-id="34ccd-117">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="34ccd-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="34ccd-118">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="34ccd-118">Remarks</span></span>

<span data-ttu-id="34ccd-119">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="34ccd-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="34ccd-120">Krav</span><span class="sxs-lookup"><span data-stu-id="34ccd-120">Requirements</span></span>
------------
><span data-ttu-id="34ccd-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="34ccd-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="34ccd-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="34ccd-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="34ccd-123">Se även</span><span class="sxs-lookup"><span data-stu-id="34ccd-123">See also</span></span>


[<span data-ttu-id="34ccd-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="34ccd-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



