---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: ta bort pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 28dbfe84827d6ccb99dce1ebb520cae66dc8c50e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="2cbb3-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2cbb3-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="2cbb3-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="2cbb3-104">SYNOPSIS</span></span>

<span data-ttu-id="2cbb3-105">Tar bort en angiven auktoriseringsregel från Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="2cbb3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2cbb3-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="2cbb3-107">Id</span><span class="sxs-lookup"><span data-stu-id="2cbb3-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="2cbb3-108">Regeln</span><span class="sxs-lookup"><span data-stu-id="2cbb3-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2cbb3-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2cbb3-109">DESCRIPTION</span></span>

<span data-ttu-id="2cbb3-110">Tar bort en angiven auktoriseringsregel från Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="2cbb3-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2cbb3-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="2cbb3-112">-Force</span><span class="sxs-lookup"><span data-stu-id="2cbb3-112">-Force</span></span>

<span data-ttu-id="2cbb3-113">Kör cmdleten utan att fråga efter bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="2cbb3-114">Som standard begär cmdlet bekräftelse innan du fortsätter.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="2cbb3-115">Alias</span><span class="sxs-lookup"><span data-stu-id="2cbb3-115">Aliases</span></span>                              | <span data-ttu-id="2cbb3-116">inget</span><span class="sxs-lookup"><span data-stu-id="2cbb3-116">none</span></span>                                 |
| <span data-ttu-id="2cbb3-117">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-117">Required?</span></span>                            | <span data-ttu-id="2cbb3-118">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-118">false</span></span>                                |
| <span data-ttu-id="2cbb3-119">Placering?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-119">Position?</span></span>                            | <span data-ttu-id="2cbb3-120">Med namnet</span><span class="sxs-lookup"><span data-stu-id="2cbb3-120">named</span></span>                                |
| <span data-ttu-id="2cbb3-121">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2cbb3-121">Default Value</span></span>                        | <span data-ttu-id="2cbb3-122">inget</span><span class="sxs-lookup"><span data-stu-id="2cbb3-122">none</span></span>                                 |
| <span data-ttu-id="2cbb3-123">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2cbb3-124">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-124">false</span></span>                                |
| <span data-ttu-id="2cbb3-125">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2cbb3-126">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="2cbb3-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2cbb3-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="2cbb3-128">Anger identifierare (ID) av en eller flera regler för att ta bort.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="2cbb3-129">Alias</span><span class="sxs-lookup"><span data-stu-id="2cbb3-129">Aliases</span></span>                              | <span data-ttu-id="2cbb3-130">inget</span><span class="sxs-lookup"><span data-stu-id="2cbb3-130">none</span></span>                                 |
| <span data-ttu-id="2cbb3-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-131">Required?</span></span>                            | <span data-ttu-id="2cbb3-132">true</span><span class="sxs-lookup"><span data-stu-id="2cbb3-132">true</span></span>                                 |
| <span data-ttu-id="2cbb3-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-133">Position?</span></span>                            | <span data-ttu-id="2cbb3-134">2</span><span class="sxs-lookup"><span data-stu-id="2cbb3-134">2</span></span>                                    |
| <span data-ttu-id="2cbb3-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2cbb3-135">Default Value</span></span>                        | <span data-ttu-id="2cbb3-136">inget</span><span class="sxs-lookup"><span data-stu-id="2cbb3-136">none</span></span>                                 |
| <span data-ttu-id="2cbb3-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2cbb3-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2cbb3-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="2cbb3-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2cbb3-140">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="2cbb3-141">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2cbb3-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="2cbb3-142">Anger regler för att ta bort.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="2cbb3-143">Alias</span><span class="sxs-lookup"><span data-stu-id="2cbb3-143">Aliases</span></span>                              | <span data-ttu-id="2cbb3-144">inget</span><span class="sxs-lookup"><span data-stu-id="2cbb3-144">none</span></span>                                 |
| <span data-ttu-id="2cbb3-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-145">Required?</span></span>                            | <span data-ttu-id="2cbb3-146">true</span><span class="sxs-lookup"><span data-stu-id="2cbb3-146">true</span></span>                                 |
| <span data-ttu-id="2cbb3-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-147">Position?</span></span>                            | <span data-ttu-id="2cbb3-148">2</span><span class="sxs-lookup"><span data-stu-id="2cbb3-148">2</span></span>                                    |
| <span data-ttu-id="2cbb3-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2cbb3-149">Default Value</span></span>                        | <span data-ttu-id="2cbb3-150">inget</span><span class="sxs-lookup"><span data-stu-id="2cbb3-150">none</span></span>                                 |
| <span data-ttu-id="2cbb3-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2cbb3-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="2cbb3-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="2cbb3-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2cbb3-154">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="2cbb3-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2cbb3-155">-Confirm</span></span>

<span data-ttu-id="2cbb3-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="2cbb3-157">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-157">Required?</span></span>                            | <span data-ttu-id="2cbb3-158">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-158">false</span></span>                                |
| <span data-ttu-id="2cbb3-159">Placering?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-159">Position?</span></span>                            | <span data-ttu-id="2cbb3-160">Med namnet</span><span class="sxs-lookup"><span data-stu-id="2cbb3-160">named</span></span>                                |
| <span data-ttu-id="2cbb3-161">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2cbb3-161">Default Value</span></span>                        | <span data-ttu-id="2cbb3-162">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-162">false</span></span>                                |
| <span data-ttu-id="2cbb3-163">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2cbb3-164">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-164">false</span></span>                                |
| <span data-ttu-id="2cbb3-165">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2cbb3-166">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="2cbb3-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2cbb3-167">-WhatIf</span></span>

<span data-ttu-id="2cbb3-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2cbb3-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="2cbb3-170">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-170">Required?</span></span>                            | <span data-ttu-id="2cbb3-171">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-171">false</span></span>                                |
| <span data-ttu-id="2cbb3-172">Placering?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-172">Position?</span></span>                            | <span data-ttu-id="2cbb3-173">Med namnet</span><span class="sxs-lookup"><span data-stu-id="2cbb3-173">named</span></span>                                |
| <span data-ttu-id="2cbb3-174">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="2cbb3-174">Default Value</span></span>                        | <span data-ttu-id="2cbb3-175">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-175">false</span></span>                                |
| <span data-ttu-id="2cbb3-176">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2cbb3-177">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-177">false</span></span>                                |
| <span data-ttu-id="2cbb3-178">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="2cbb3-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2cbb3-179">falskt</span><span class="sxs-lookup"><span data-stu-id="2cbb3-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2cbb3-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2cbb3-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2cbb3-181">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2cbb3-182">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2cbb3-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="2cbb3-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="2cbb3-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="2cbb3-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="2cbb3-184">int\[\]</span></span>

<span data-ttu-id="2cbb3-185">Denna cmdlet accepterar en heltalsmatris eller en matris med PswaAuthorizationRule-objekt.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="2cbb3-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="2cbb3-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="2cbb3-187">Denna cmdlet accepterar en heltalsmatris eller en matris med PswaAuthorizationRule-objekt.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="2cbb3-188">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2cbb3-188">OUTPUTS</span></span>

<span data-ttu-id="2cbb3-189">Denna cmdlet ger inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="2cbb3-190">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2cbb3-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2cbb3-191">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="2cbb3-191">EXAMPLE 1</span></span>

<span data-ttu-id="2cbb3-192">Det här exemplet tar bort auktoriseringsregeln med ID *2*.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="2cbb3-193">EXEMPEL 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2cbb3-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="2cbb3-194">Det här exemplet tar bort alla auktoriseringsregler och kräver bekräftelse av användaren.</span><span class="sxs-lookup"><span data-stu-id="2cbb3-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="2cbb3-195">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="2cbb3-195">Related topics</span></span>

- [<span data-ttu-id="2cbb3-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2cbb3-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="2cbb3-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2cbb3-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="2cbb3-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="2cbb3-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="2cbb3-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2cbb3-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)