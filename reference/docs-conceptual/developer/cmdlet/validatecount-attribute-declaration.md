---
title: ValidateCount-Attribute-deklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692371"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="e154c-102">Deklaration av attributet ValidateCount</span><span class="sxs-lookup"><span data-stu-id="e154c-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="e154c-103">Attributet ValidateCount anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="e154c-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="e154c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e154c-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="e154c-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e154c-105">Parameters</span></span>

<span data-ttu-id="e154c-106">`MinLength`([System. Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="e154c-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="e154c-107">Anger det minsta antalet argument.</span><span class="sxs-lookup"><span data-stu-id="e154c-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="e154c-108">`MaxLength`([System. Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="e154c-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="e154c-109">Anger det maximala antalet argument.</span><span class="sxs-lookup"><span data-stu-id="e154c-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="e154c-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e154c-110">Remarks</span></span>

- <span data-ttu-id="e154c-111">Mer information om hur du deklarerar det här attributet finns i [så här verifierar du ett argument antal][].</span><span class="sxs-lookup"><span data-stu-id="e154c-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="e154c-112">När det här attributet inte anropas kan motsvarande cmdlet-parameter ha valfritt antal argument.</span><span class="sxs-lookup"><span data-stu-id="e154c-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="e154c-113">Windows PowerShell-körningsmiljön genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="e154c-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="e154c-114">`MinLength`Parametrarna och `MaxLength` är inte av typen [system. Int32][].</span><span class="sxs-lookup"><span data-stu-id="e154c-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="e154c-115">Värdet för `MaxLength` attributet Attribute är mindre än värdet för `MinLength` parametern Attribute.</span><span class="sxs-lookup"><span data-stu-id="e154c-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="e154c-116">Attributet ValidateCount definieras av klassen [system. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="e154c-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e154c-117">Se även</span><span class="sxs-lookup"><span data-stu-id="e154c-117">See Also</span></span>

<span data-ttu-id="e154c-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="e154c-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="e154c-119">[Verifiera argumentantal][]</span><span class="sxs-lookup"><span data-stu-id="e154c-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="e154c-120">[Skriva en Windows PowerShell-cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="e154c-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Verifiera argumentantal]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
