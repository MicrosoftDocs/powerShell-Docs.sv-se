---
ms.date: 09/13/2016
ms.topic: reference
title: Attributtyper
description: Attributtyper
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667121"
---
# <a name="attribute-types"></a><span data-ttu-id="5ee2c-103">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="5ee2c-103">Attribute Types</span></span>

<span data-ttu-id="5ee2c-104">Cmdlet-attribut kan grupperas efter funktionalitet.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-104">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="5ee2c-105">I följande avsnitt beskrivs tillgängliga attribut och hur du kan beskriva vad körningen gör när attributet anropas.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-105">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="5ee2c-106">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="5ee2c-106">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="5ee2c-107">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5ee2c-107">Cmdlet</span></span>

<span data-ttu-id="5ee2c-108">Identifierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-108">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="5ee2c-109">Detta är det grundläggande attributet som krävs.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-109">This is the required base attribute.</span></span>
<span data-ttu-id="5ee2c-110">Mer information finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-110">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="5ee2c-111">Parameter-attribut</span><span class="sxs-lookup"><span data-stu-id="5ee2c-111">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="5ee2c-112">Parameter</span><span class="sxs-lookup"><span data-stu-id="5ee2c-112">Parameter</span></span>

<span data-ttu-id="5ee2c-113">Identifierar en offentlig egenskap i cmdlet-klassen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-113">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="5ee2c-114">Mer information finns i [deklaration av parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-114">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="5ee2c-115">Alias</span><span class="sxs-lookup"><span data-stu-id="5ee2c-115">Alias</span></span>

<span data-ttu-id="5ee2c-116">Anger ett eller flera alias för en parameter.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-116">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="5ee2c-117">Mer information finns i [deklaration för alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-117">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="5ee2c-118">Attribut för argument verifiering</span><span class="sxs-lookup"><span data-stu-id="5ee2c-118">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="5ee2c-119">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="5ee2c-119">ValidateCount</span></span>

<span data-ttu-id="5ee2c-120">Anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-120">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="5ee2c-121">Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-121">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="5ee2c-122">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="5ee2c-122">ValidateLength</span></span>

<span data-ttu-id="5ee2c-123">Anger ett minsta och högsta antal tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-123">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="5ee2c-124">Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-124">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="5ee2c-125">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="5ee2c-125">ValidatePattern</span></span>

<span data-ttu-id="5ee2c-126">Anger ett mönster för reguljära uttryck som argumentet cmdlet-parameter måste matcha.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-126">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="5ee2c-127">Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-127">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="5ee2c-128">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="5ee2c-128">ValidateRange</span></span>

<span data-ttu-id="5ee2c-129">Anger det lägsta och högsta värdet för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-129">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="5ee2c-130">Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-130">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="5ee2c-131">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="5ee2c-131">ValidateSet</span></span>

<span data-ttu-id="5ee2c-132">Anger en uppsättning giltiga värden för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="5ee2c-132">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="5ee2c-133">Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="5ee2c-133">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ee2c-134">Se även</span><span class="sxs-lookup"><span data-stu-id="5ee2c-134">See Also</span></span>

[<span data-ttu-id="5ee2c-135">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5ee2c-135">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
