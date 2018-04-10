---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: b5f437a123bd38df21f30d11e71d2c3b36bc9f3a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7595c-103">ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="7595c-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7595c-104">Direkt anropar den **ange** metoden för en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="7595c-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="7595c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7595c-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="7595c-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="7595c-106">Parameters</span></span>
----------

<span data-ttu-id="7595c-107">*ResourceType* \[i\] namnet på resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="7595c-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="7595c-108">*Modulnamn* \[i\] namnet på den modul som innehåller resursen ska anropa.</span><span class="sxs-lookup"><span data-stu-id="7595c-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7595c-109">*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive.</span><span class="sxs-lookup"><span data-stu-id="7595c-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7595c-110">Använd den [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) för att identifiera egenskaper för resursen och deras typer.</span><span class="sxs-lookup"><span data-stu-id="7595c-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7595c-111">*RebootRequired* \[ut\] på RETUR, ange den här egenskapen är **SANT** om målnoden måste startas om.</span><span class="sxs-lookup"><span data-stu-id="7595c-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="7595c-112">Returvärde</span><span class="sxs-lookup"><span data-stu-id="7595c-112">Return value</span></span>
------------

<span data-ttu-id="7595c-113">Returnerar noll på lyckade; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="7595c-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7595c-114">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7595c-114">Remarks</span></span>

<span data-ttu-id="7595c-115">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="7595c-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7595c-116">Krav</span><span class="sxs-lookup"><span data-stu-id="7595c-116">Requirements</span></span>
------------
><span data-ttu-id="7595c-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7595c-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7595c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7595c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7595c-119">Se även</span><span class="sxs-lookup"><span data-stu-id="7595c-119">See also</span></span>


[<span data-ttu-id="7595c-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7595c-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)