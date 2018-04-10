---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Hämta pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="2de42-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2de42-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="2de42-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2de42-104">SYNOPSIS</span></span>

<span data-ttu-id="2de42-105">Returnerar en uppsättning auktoriseringsregler för Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="2de42-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="2de42-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2de42-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="2de42-107">ID</span><span class="sxs-lookup"><span data-stu-id="2de42-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="2de42-108">Namn</span><span class="sxs-lookup"><span data-stu-id="2de42-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2de42-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2de42-109">DESCRIPTION</span></span>

<span data-ttu-id="2de42-110">Den **Get-PswaAuthorizationRule** cmdlet returnerar en uppsättning auktoriseringsregler för Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="2de42-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="2de42-111">Om varken den **Id** parametern eller **RuleName** parametern anges, och den här cmdleten visar alla regler.</span><span class="sxs-lookup"><span data-stu-id="2de42-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="2de42-112">Den **Id** parametern kan användas för att filtrera resultaten.</span><span class="sxs-lookup"><span data-stu-id="2de42-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="2de42-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2de42-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="2de42-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2de42-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="2de42-115">Anger identifierare (ID) av regler som denna cmdlet ska få.</span><span class="sxs-lookup"><span data-stu-id="2de42-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="2de42-116">Om inga-ID har angetts returnerar den här cmdleten alla auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="2de42-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="2de42-117">Alias</span><span class="sxs-lookup"><span data-stu-id="2de42-117">Aliases</span></span>                              | <span data-ttu-id="2de42-118">inget</span><span class="sxs-lookup"><span data-stu-id="2de42-118">none</span></span>                                 |
| <span data-ttu-id="2de42-119">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2de42-119">Required?</span></span>                            | <span data-ttu-id="2de42-120">falskt</span><span class="sxs-lookup"><span data-stu-id="2de42-120">false</span></span>                                |
| <span data-ttu-id="2de42-121">Placering?</span><span class="sxs-lookup"><span data-stu-id="2de42-121">Position?</span></span>                            | <span data-ttu-id="2de42-122">2</span><span class="sxs-lookup"><span data-stu-id="2de42-122">2</span></span>                                    |
| <span data-ttu-id="2de42-123">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2de42-123">Default Value</span></span>                        | <span data-ttu-id="2de42-124">inget</span><span class="sxs-lookup"><span data-stu-id="2de42-124">none</span></span>                                 |
| <span data-ttu-id="2de42-125">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2de42-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2de42-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2de42-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="2de42-127">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2de42-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2de42-128">falskt</span><span class="sxs-lookup"><span data-stu-id="2de42-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="2de42-129">-RuleName&lt;sträng\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2de42-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="2de42-130">Anger namn på auktoriseringsregler för att hämta.</span><span class="sxs-lookup"><span data-stu-id="2de42-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="2de42-131">Den här parametern returnerar de regler som matchar exakt Regelnamn strängar i denna matris.</span><span class="sxs-lookup"><span data-stu-id="2de42-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="2de42-132">Alias</span><span class="sxs-lookup"><span data-stu-id="2de42-132">Aliases</span></span>                              | <span data-ttu-id="2de42-133">inget</span><span class="sxs-lookup"><span data-stu-id="2de42-133">none</span></span>                                 |
| <span data-ttu-id="2de42-134">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2de42-134">Required?</span></span>                            | <span data-ttu-id="2de42-135">true</span><span class="sxs-lookup"><span data-stu-id="2de42-135">true</span></span>                                 |
| <span data-ttu-id="2de42-136">Placering?</span><span class="sxs-lookup"><span data-stu-id="2de42-136">Position?</span></span>                            | <span data-ttu-id="2de42-137">2</span><span class="sxs-lookup"><span data-stu-id="2de42-137">2</span></span>                                    |
| <span data-ttu-id="2de42-138">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2de42-138">Default Value</span></span>                        | <span data-ttu-id="2de42-139">inget</span><span class="sxs-lookup"><span data-stu-id="2de42-139">none</span></span>                                 |
| <span data-ttu-id="2de42-140">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2de42-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2de42-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2de42-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="2de42-142">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2de42-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2de42-143">falskt</span><span class="sxs-lookup"><span data-stu-id="2de42-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2de42-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2de42-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2de42-145">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="2de42-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2de42-146">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2de42-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2de42-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="2de42-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="2de42-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="2de42-148">int\[\]</span></span>

<span data-ttu-id="2de42-149">Denna cmdlet accepterar en heltalsmatris eller en matris med strängvärden som indata.</span><span class="sxs-lookup"><span data-stu-id="2de42-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="2de42-150">Sträng\[\]</span><span class="sxs-lookup"><span data-stu-id="2de42-150">String\[\]</span></span>

<span data-ttu-id="2de42-151">Denna cmdlet accepterar en heltalsmatris eller en matris med strängvärden som indata.</span><span class="sxs-lookup"><span data-stu-id="2de42-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="2de42-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2de42-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="2de42-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="2de42-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="2de42-154">Denna cmdlet ger ett PswaAuthorizationRule-objekt som utdata.</span><span class="sxs-lookup"><span data-stu-id="2de42-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="2de42-155">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2de42-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2de42-156">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="2de42-156">EXAMPLE 1</span></span>

<span data-ttu-id="2de42-157">Det här exemplet hämtar alla regler.</span><span class="sxs-lookup"><span data-stu-id="2de42-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="2de42-158">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="2de42-158">EXAMPLE 2</span></span>

<span data-ttu-id="2de42-159">Det här exemplet hämtar en regel med ID *2*.</span><span class="sxs-lookup"><span data-stu-id="2de42-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="2de42-160">EXEMPEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2de42-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="2de42-161">Det här exemplet illustrerar hur cmdlet accepterar ett värde från pipeline.</span><span class="sxs-lookup"><span data-stu-id="2de42-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="2de42-162">Regel-id och ett namn för regeln skickas i denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2de42-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="2de42-163">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="2de42-163">Related topics</span></span>

- [<span data-ttu-id="2de42-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2de42-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2de42-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2de42-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="2de42-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2de42-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="2de42-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2de42-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)