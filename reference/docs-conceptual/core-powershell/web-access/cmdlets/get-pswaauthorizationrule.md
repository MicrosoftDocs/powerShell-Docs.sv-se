---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: "Hämta pswaauthorizationrule"
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="08346-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08346-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="08346-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="08346-104">SYNOPSIS</span></span>

<span data-ttu-id="08346-105">Returnerar en uppsättning auktoriseringsregler för Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="08346-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="08346-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="08346-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="08346-107">ID</span><span class="sxs-lookup"><span data-stu-id="08346-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="08346-108">Namn</span><span class="sxs-lookup"><span data-stu-id="08346-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="08346-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="08346-109">DESCRIPTION</span></span>

<span data-ttu-id="08346-110">Den **Get-PswaAuthorizationRule** cmdlet returnerar en uppsättning auktoriseringsregler för Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="08346-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="08346-111">Om varken den **Id** parametern eller **RuleName** parametern anges, och den här cmdleten visar alla regler.</span><span class="sxs-lookup"><span data-stu-id="08346-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="08346-112">Den **Id** parametern kan användas för att filtrera resultaten.</span><span class="sxs-lookup"><span data-stu-id="08346-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="08346-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="08346-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="08346-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="08346-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="08346-115">Anger identifierare (ID) av regler som denna cmdlet ska få.</span><span class="sxs-lookup"><span data-stu-id="08346-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="08346-116">Om inga-ID har angetts returnerar den här cmdleten alla auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="08346-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="08346-117">Alias</span><span class="sxs-lookup"><span data-stu-id="08346-117">Aliases</span></span>                              | <span data-ttu-id="08346-118">inget</span><span class="sxs-lookup"><span data-stu-id="08346-118">none</span></span>                                 |
| <span data-ttu-id="08346-119">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="08346-119">Required?</span></span>                            | <span data-ttu-id="08346-120">falskt</span><span class="sxs-lookup"><span data-stu-id="08346-120">false</span></span>                                |
| <span data-ttu-id="08346-121">Placering?</span><span class="sxs-lookup"><span data-stu-id="08346-121">Position?</span></span>                            | <span data-ttu-id="08346-122">2</span><span class="sxs-lookup"><span data-stu-id="08346-122">2</span></span>                                    |
| <span data-ttu-id="08346-123">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="08346-123">Default Value</span></span>                        | <span data-ttu-id="08346-124">inget</span><span class="sxs-lookup"><span data-stu-id="08346-124">none</span></span>                                 |
| <span data-ttu-id="08346-125">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="08346-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08346-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="08346-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="08346-127">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="08346-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08346-128">falskt</span><span class="sxs-lookup"><span data-stu-id="08346-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="08346-129">-RuleName&lt;sträng\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="08346-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="08346-130">Anger namn på auktoriseringsregler för att hämta.</span><span class="sxs-lookup"><span data-stu-id="08346-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="08346-131">Den här parametern returnerar de regler som matchar exakt Regelnamn strängar i denna matris.</span><span class="sxs-lookup"><span data-stu-id="08346-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="08346-132">Alias</span><span class="sxs-lookup"><span data-stu-id="08346-132">Aliases</span></span>                              | <span data-ttu-id="08346-133">inget</span><span class="sxs-lookup"><span data-stu-id="08346-133">none</span></span>                                 |
| <span data-ttu-id="08346-134">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="08346-134">Required?</span></span>                            | <span data-ttu-id="08346-135">SANT</span><span class="sxs-lookup"><span data-stu-id="08346-135">true</span></span>                                 |
| <span data-ttu-id="08346-136">Placering?</span><span class="sxs-lookup"><span data-stu-id="08346-136">Position?</span></span>                            | <span data-ttu-id="08346-137">2</span><span class="sxs-lookup"><span data-stu-id="08346-137">2</span></span>                                    |
| <span data-ttu-id="08346-138">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="08346-138">Default Value</span></span>                        | <span data-ttu-id="08346-139">inget</span><span class="sxs-lookup"><span data-stu-id="08346-139">none</span></span>                                 |
| <span data-ttu-id="08346-140">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="08346-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="08346-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="08346-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="08346-142">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="08346-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="08346-143">falskt</span><span class="sxs-lookup"><span data-stu-id="08346-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="08346-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="08346-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="08346-145">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="08346-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="08346-146">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="08346-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="08346-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="08346-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="08346-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="08346-148">int\[\]</span></span>

<span data-ttu-id="08346-149">Denna cmdlet accepterar en heltalsmatris eller en matris med strängvärden som indata.</span><span class="sxs-lookup"><span data-stu-id="08346-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="08346-150">Sträng\[\]</span><span class="sxs-lookup"><span data-stu-id="08346-150">String\[\]</span></span>

<span data-ttu-id="08346-151">Denna cmdlet accepterar en heltalsmatris eller en matris med strängvärden som indata.</span><span class="sxs-lookup"><span data-stu-id="08346-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="08346-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="08346-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="08346-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="08346-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="08346-154">Denna cmdlet ger ett PswaAuthorizationRule-objekt som utdata.</span><span class="sxs-lookup"><span data-stu-id="08346-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="08346-155">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="08346-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="08346-156">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="08346-156">EXAMPLE 1</span></span>

<span data-ttu-id="08346-157">Det här exemplet hämtar alla regler.</span><span class="sxs-lookup"><span data-stu-id="08346-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="08346-158">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="08346-158">EXAMPLE 2</span></span>

<span data-ttu-id="08346-159">Det här exemplet hämtar en regel med ID *2*.</span><span class="sxs-lookup"><span data-stu-id="08346-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="08346-160">EXEMPEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="08346-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="08346-161">Det här exemplet illustrerar hur cmdlet accepterar ett värde från pipeline.</span><span class="sxs-lookup"><span data-stu-id="08346-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="08346-162">Regel-id och ett namn för regeln skickas i denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="08346-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="08346-163">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="08346-163">Related topics</span></span>

- [<span data-ttu-id="08346-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08346-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="08346-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08346-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="08346-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="08346-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="08346-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="08346-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
