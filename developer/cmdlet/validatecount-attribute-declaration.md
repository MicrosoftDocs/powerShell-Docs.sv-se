---
title: Deklaration av ValidateCount attribut | Microsoft Docs
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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983906"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="2fab3-102">Deklaration av attributet ValidateCount</span><span class="sxs-lookup"><span data-stu-id="2fab3-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="2fab3-103">Attributet ValidateCount anger minsta och största antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="2fab3-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fab3-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fab3-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="2fab3-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2fab3-105">Parameters</span></span>

<span data-ttu-id="2fab3-106">`MinLength` ([System.Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="2fab3-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="2fab3-107">Anger det minsta antalet argument.</span><span class="sxs-lookup"><span data-stu-id="2fab3-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="2fab3-108">`MaxLength`([System.Int32][]) krävs.</span><span class="sxs-lookup"><span data-stu-id="2fab3-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="2fab3-109">Anger det maximala antalet argument.</span><span class="sxs-lookup"><span data-stu-id="2fab3-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fab3-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2fab3-110">Remarks</span></span>

- <span data-ttu-id="2fab3-111">Läs mer om hur du deklarera det här attributet [hur du validerar en argumentantal][].</span><span class="sxs-lookup"><span data-stu-id="2fab3-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="2fab3-112">När det här attributet inte har anropats kan motsvarande cmdlet-parameter ha valfritt antal argument.</span><span class="sxs-lookup"><span data-stu-id="2fab3-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="2fab3-113">Windows PowerShell-runtime genererar ett fel under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="2fab3-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="2fab3-114">Den `MinLength` och `MaxLength` attributet parametrar inte är av typen [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="2fab3-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="2fab3-115">Värdet för den `MaxLength` attribut parameter är mindre än värdet för den `MinLength` attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="2fab3-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="2fab3-116">Attributet ValidateCount definieras av den [System.Management.Automation.ValidateCountAttribute][] klass.</span><span class="sxs-lookup"><span data-stu-id="2fab3-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fab3-117">Se även</span><span class="sxs-lookup"><span data-stu-id="2fab3-117">See Also</span></span>

<span data-ttu-id="2fab3-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="2fab3-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="2fab3-119">[Hur du validerar en argumentantal][]</span><span class="sxs-lookup"><span data-stu-id="2fab3-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="2fab3-120">[Skriva en Windows PowerShell-Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="2fab3-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Hur du validerar en argumentantal]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Skriva en Windows PowerShell-Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
