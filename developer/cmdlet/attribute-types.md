---
title: Attributet typer | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852278"
---
# <a name="attribute-types"></a><span data-ttu-id="c3cca-102">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="c3cca-102">Attribute Types</span></span>

<span data-ttu-id="c3cca-103">Cmdlet-attribut kan grupperas per funktion.</span><span class="sxs-lookup"><span data-stu-id="c3cca-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="c3cca-104">I följande avsnitt beskrivs tillgängliga attribut och Beskriv vad körningen gör när attributet anropas.</span><span class="sxs-lookup"><span data-stu-id="c3cca-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="c3cca-105">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="c3cca-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="c3cca-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c3cca-106">Cmdlet</span></span>

<span data-ttu-id="c3cca-107">Identifierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3cca-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="c3cca-108">Det här är nödvändig basattributet.</span><span class="sxs-lookup"><span data-stu-id="c3cca-108">This is the required base attribute.</span></span>
<span data-ttu-id="c3cca-109">Mer information finns i [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="c3cca-110">Parameterattribut</span><span class="sxs-lookup"><span data-stu-id="c3cca-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="c3cca-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="c3cca-111">Parameter</span></span>

<span data-ttu-id="c3cca-112">Identifierar en offentlig egenskap i klassen cmdlet som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c3cca-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="c3cca-113">Mer information finns i [parameterdeklaration för attributet](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="c3cca-114">Alias</span><span class="sxs-lookup"><span data-stu-id="c3cca-114">Alias</span></span>

<span data-ttu-id="c3cca-115">Anger en eller flera alias för en parameter.</span><span class="sxs-lookup"><span data-stu-id="c3cca-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="c3cca-116">Mer information finns i [Alias attributet deklarationen](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="c3cca-117">Argumentet verifiering attribut</span><span class="sxs-lookup"><span data-stu-id="c3cca-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="c3cca-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="c3cca-118">ValidateCount</span></span>

<span data-ttu-id="c3cca-119">Anger minsta och största antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c3cca-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="c3cca-120">Mer information finns i [ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="c3cca-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="c3cca-121">ValidateLength</span></span>

<span data-ttu-id="c3cca-122">Anger en lägsta och högsta antalet tillåtna tecken för en cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="c3cca-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c3cca-123">Mer information finns i [ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="c3cca-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="c3cca-124">ValidatePattern</span></span>

<span data-ttu-id="c3cca-125">Anger ett mönster för reguljärt uttryck som cmdlet-argument för parametern måste matcha.</span><span class="sxs-lookup"><span data-stu-id="c3cca-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="c3cca-126">Mer information finns i [ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="c3cca-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="c3cca-127">ValidateRange</span></span>

<span data-ttu-id="c3cca-128">Anger minsta och högsta värden för en cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="c3cca-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c3cca-129">Mer information finns i [ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="c3cca-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="c3cca-130">ValidateSet</span></span>

<span data-ttu-id="c3cca-131">Anger en uppsättning med giltiga värden för cmdlet-argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="c3cca-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="c3cca-132">Mer information finns i [ValidateSet attributet deklarationen](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c3cca-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3cca-133">Se även</span><span class="sxs-lookup"><span data-stu-id="c3cca-133">See Also</span></span>

[<span data-ttu-id="c3cca-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c3cca-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
