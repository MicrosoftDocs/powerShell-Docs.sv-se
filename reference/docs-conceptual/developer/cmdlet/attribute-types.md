---
title: Attributtyper | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 96fdd38ba10eb748ab0762f0c910463dd472494d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782386"
---
# <a name="attribute-types"></a><span data-ttu-id="c5adf-102">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="c5adf-102">Attribute Types</span></span>

<span data-ttu-id="c5adf-103">Cmdlet-attribut kan grupperas efter funktionalitet.</span><span class="sxs-lookup"><span data-stu-id="c5adf-103">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="c5adf-104">I följande avsnitt beskrivs tillgängliga attribut och hur du kan beskriva vad körningen gör när attributet anropas.</span><span class="sxs-lookup"><span data-stu-id="c5adf-104">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="c5adf-105">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="c5adf-105">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="c5adf-106">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c5adf-106">Cmdlet</span></span>

<span data-ttu-id="c5adf-107">Identifierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5adf-107">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="c5adf-108">Detta är det grundläggande attributet som krävs.</span><span class="sxs-lookup"><span data-stu-id="c5adf-108">This is the required base attribute.</span></span>
<span data-ttu-id="c5adf-109">Mer information finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-109">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="c5adf-110">Parameter-attribut</span><span class="sxs-lookup"><span data-stu-id="c5adf-110">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="c5adf-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="c5adf-111">Parameter</span></span>

<span data-ttu-id="c5adf-112">Identifierar en offentlig egenskap i cmdlet-klassen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c5adf-112">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="c5adf-113">Mer information finns i [deklaration av parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-113">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="c5adf-114">Alias</span><span class="sxs-lookup"><span data-stu-id="c5adf-114">Alias</span></span>

<span data-ttu-id="c5adf-115">Anger ett eller flera alias för en parameter.</span><span class="sxs-lookup"><span data-stu-id="c5adf-115">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="c5adf-116">Mer information finns i [deklaration för alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-116">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="c5adf-117">Attribut för argument verifiering</span><span class="sxs-lookup"><span data-stu-id="c5adf-117">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="c5adf-118">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="c5adf-118">ValidateCount</span></span>

<span data-ttu-id="c5adf-119">Anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c5adf-119">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="c5adf-120">Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-120">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="c5adf-121">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="c5adf-121">ValidateLength</span></span>

<span data-ttu-id="c5adf-122">Anger ett minsta och högsta antal tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="c5adf-122">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c5adf-123">Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-123">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="c5adf-124">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="c5adf-124">ValidatePattern</span></span>

<span data-ttu-id="c5adf-125">Anger ett mönster för reguljära uttryck som argumentet cmdlet-parameter måste matcha.</span><span class="sxs-lookup"><span data-stu-id="c5adf-125">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="c5adf-126">Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-126">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="c5adf-127">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="c5adf-127">ValidateRange</span></span>

<span data-ttu-id="c5adf-128">Anger det lägsta och högsta värdet för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="c5adf-128">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="c5adf-129">Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-129">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="c5adf-130">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="c5adf-130">ValidateSet</span></span>

<span data-ttu-id="c5adf-131">Anger en uppsättning giltiga värden för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="c5adf-131">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="c5adf-132">Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="c5adf-132">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5adf-133">Se även</span><span class="sxs-lookup"><span data-stu-id="c5adf-133">See Also</span></span>

[<span data-ttu-id="c5adf-134">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c5adf-134">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
