---
ms.date: 09/13/2016
ms.topic: reference
title: Attributtyper
description: Attributtyper
ms.openlocfilehash: 65640f2f8449887dedb9fae137eb16b6252f1d57
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667121"
---
# <a name="attribute-types"></a><span data-ttu-id="293d9-103">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="293d9-103">Attribute Types</span></span>

<span data-ttu-id="293d9-104">Cmdlet-attribut kan grupperas efter funktionalitet.</span><span class="sxs-lookup"><span data-stu-id="293d9-104">Cmdlet attributes can be grouped by functionality.</span></span>
<span data-ttu-id="293d9-105">I följande avsnitt beskrivs tillgängliga attribut och hur du kan beskriva vad körningen gör när attributet anropas.</span><span class="sxs-lookup"><span data-stu-id="293d9-105">The following sections describe the available attributes and describe what the runtime does when the attribute is invoked.</span></span>

## <a name="cmdlet-attributes"></a><span data-ttu-id="293d9-106">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="293d9-106">Cmdlet Attributes</span></span>

### <a name="cmdlet"></a><span data-ttu-id="293d9-107">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="293d9-107">Cmdlet</span></span>

<span data-ttu-id="293d9-108">Identifierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="293d9-108">Identifies a .NET Framework class as a cmdlet.</span></span>
<span data-ttu-id="293d9-109">Detta är det grundläggande attributet som krävs.</span><span class="sxs-lookup"><span data-stu-id="293d9-109">This is the required base attribute.</span></span>
<span data-ttu-id="293d9-110">Mer information finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-110">For more information, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="parameter-attributes"></a><span data-ttu-id="293d9-111">Parameter-attribut</span><span class="sxs-lookup"><span data-stu-id="293d9-111">Parameter Attributes</span></span>

### <a name="parameter"></a><span data-ttu-id="293d9-112">Parameter</span><span class="sxs-lookup"><span data-stu-id="293d9-112">Parameter</span></span>

<span data-ttu-id="293d9-113">Identifierar en offentlig egenskap i cmdlet-klassen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="293d9-113">Identifies a public property in the cmdlet class as a cmdlet parameter.</span></span>
<span data-ttu-id="293d9-114">Mer information finns i [deklaration av parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-114">For more information, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

### <a name="alias"></a><span data-ttu-id="293d9-115">Alias</span><span class="sxs-lookup"><span data-stu-id="293d9-115">Alias</span></span>

<span data-ttu-id="293d9-116">Anger ett eller flera alias för en parameter.</span><span class="sxs-lookup"><span data-stu-id="293d9-116">Specifies one or more aliases for a parameter.</span></span>
<span data-ttu-id="293d9-117">Mer information finns i [deklaration för alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-117">For more information, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="argument-validation-attributes"></a><span data-ttu-id="293d9-118">Attribut för argument verifiering</span><span class="sxs-lookup"><span data-stu-id="293d9-118">Argument Validation Attributes</span></span>

### <a name="validatecount"></a><span data-ttu-id="293d9-119">ValidateCount</span><span class="sxs-lookup"><span data-stu-id="293d9-119">ValidateCount</span></span>

<span data-ttu-id="293d9-120">Anger det lägsta och högsta antalet argument som tillåts för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="293d9-120">Specifies the minimum and maximum number of arguments that are allowed for a cmdlet parameter.</span></span>
<span data-ttu-id="293d9-121">Mer information finns i [ValidateCount Attribute-deklaration](./validatecount-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-121">For more information, see [ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md).</span></span>

### <a name="validatelength"></a><span data-ttu-id="293d9-122">ValidateLength</span><span class="sxs-lookup"><span data-stu-id="293d9-122">ValidateLength</span></span>

<span data-ttu-id="293d9-123">Anger ett minsta och högsta antal tecken för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="293d9-123">Specifies a minimum and maximum number of characters for a cmdlet parameter argument.</span></span>
<span data-ttu-id="293d9-124">Mer information finns i [ValidateLength Attribute-deklaration](./validatelength-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-124">For more information, see [ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md).</span></span>

### <a name="validatepattern"></a><span data-ttu-id="293d9-125">ValidatePattern</span><span class="sxs-lookup"><span data-stu-id="293d9-125">ValidatePattern</span></span>

<span data-ttu-id="293d9-126">Anger ett mönster för reguljära uttryck som argumentet cmdlet-parameter måste matcha.</span><span class="sxs-lookup"><span data-stu-id="293d9-126">Specifies a regular expression pattern that the cmdlet parameter argument must match.</span></span>
<span data-ttu-id="293d9-127">Mer information finns i [ValidatePattern Attribute-deklaration](./validatepattern-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-127">For more information, see [ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md).</span></span>

### <a name="validaterange"></a><span data-ttu-id="293d9-128">ValidateRange</span><span class="sxs-lookup"><span data-stu-id="293d9-128">ValidateRange</span></span>

<span data-ttu-id="293d9-129">Anger det lägsta och högsta värdet för ett cmdlet parameter argument.</span><span class="sxs-lookup"><span data-stu-id="293d9-129">Specifies the minimum and maximum values for a cmdlet parameter argument.</span></span>
<span data-ttu-id="293d9-130">Mer information finns i [ValidateRange Attribute-deklaration](./validaterange-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-130">For more information, see [ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md).</span></span>

### <a name="validateset"></a><span data-ttu-id="293d9-131">ValidateSet</span><span class="sxs-lookup"><span data-stu-id="293d9-131">ValidateSet</span></span>

<span data-ttu-id="293d9-132">Anger en uppsättning giltiga värden för argumentet cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="293d9-132">Specifies a set of valid values for the cmdlet parameter argument.</span></span>
<span data-ttu-id="293d9-133">Mer information finns i [ValidateSet Attribute-deklaration](./validateset-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="293d9-133">For more information, see [ValidateSet Attribute Declaration](./validateset-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="293d9-134">Se även</span><span class="sxs-lookup"><span data-stu-id="293d9-134">See Also</span></span>

[<span data-ttu-id="293d9-135">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="293d9-135">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
