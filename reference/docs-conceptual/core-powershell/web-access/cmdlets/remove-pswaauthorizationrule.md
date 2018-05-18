---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Remove-PswaAuthorizationRule
ms.openlocfilehash: 6a3720bb9b8df3e1c6bb9f4a6196c9868b85b67d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="3ff20-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3ff20-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="3ff20-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3ff20-104">SYNOPSIS</span></span>

<span data-ttu-id="3ff20-105">Tar bort en angiven auktoriseringsregel från Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="3ff20-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ff20-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ff20-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="3ff20-107">Id</span><span class="sxs-lookup"><span data-stu-id="3ff20-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="3ff20-108">Regeln</span><span class="sxs-lookup"><span data-stu-id="3ff20-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="3ff20-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3ff20-109">DESCRIPTION</span></span>

<span data-ttu-id="3ff20-110">Tar bort en angiven auktoriseringsregel från Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="3ff20-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="3ff20-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3ff20-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="3ff20-112">-Force</span><span class="sxs-lookup"><span data-stu-id="3ff20-112">-Force</span></span>

<span data-ttu-id="3ff20-113">Kör cmdleten utan att fråga efter bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="3ff20-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="3ff20-114">Som standard begär cmdlet bekräftelse innan du fortsätter.</span><span class="sxs-lookup"><span data-stu-id="3ff20-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||
|-|-|
| <span data-ttu-id="3ff20-115">Alias</span><span class="sxs-lookup"><span data-stu-id="3ff20-115">Aliases</span></span>                              | <span data-ttu-id="3ff20-116">inget</span><span class="sxs-lookup"><span data-stu-id="3ff20-116">none</span></span>                                 |
| <span data-ttu-id="3ff20-117">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="3ff20-117">Required?</span></span>                            | <span data-ttu-id="3ff20-118">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-118">false</span></span>                                |
| <span data-ttu-id="3ff20-119">Placering?</span><span class="sxs-lookup"><span data-stu-id="3ff20-119">Position?</span></span>                            | <span data-ttu-id="3ff20-120">Med namnet</span><span class="sxs-lookup"><span data-stu-id="3ff20-120">named</span></span>                                |
| <span data-ttu-id="3ff20-121">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="3ff20-121">Default Value</span></span>                        | <span data-ttu-id="3ff20-122">inget</span><span class="sxs-lookup"><span data-stu-id="3ff20-122">none</span></span>                                 |
| <span data-ttu-id="3ff20-123">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="3ff20-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3ff20-124">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-124">false</span></span>                                |
| <span data-ttu-id="3ff20-125">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="3ff20-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3ff20-126">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="3ff20-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="3ff20-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="3ff20-128">Anger identifierare (ID) av en eller flera regler för att ta bort.</span><span class="sxs-lookup"><span data-stu-id="3ff20-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="3ff20-129">Alias</span><span class="sxs-lookup"><span data-stu-id="3ff20-129">Aliases</span></span>                              | <span data-ttu-id="3ff20-130">inget</span><span class="sxs-lookup"><span data-stu-id="3ff20-130">none</span></span>                                 |
| <span data-ttu-id="3ff20-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="3ff20-131">Required?</span></span>                            | <span data-ttu-id="3ff20-132">SANT</span><span class="sxs-lookup"><span data-stu-id="3ff20-132">true</span></span>                                 |
| <span data-ttu-id="3ff20-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="3ff20-133">Position?</span></span>                            | <span data-ttu-id="3ff20-134">2</span><span class="sxs-lookup"><span data-stu-id="3ff20-134">2</span></span>                                    |
| <span data-ttu-id="3ff20-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="3ff20-135">Default Value</span></span>                        | <span data-ttu-id="3ff20-136">inget</span><span class="sxs-lookup"><span data-stu-id="3ff20-136">none</span></span>                                 |
| <span data-ttu-id="3ff20-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="3ff20-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3ff20-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="3ff20-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="3ff20-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="3ff20-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3ff20-140">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="3ff20-141">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="3ff20-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="3ff20-142">Anger regler för att ta bort.</span><span class="sxs-lookup"><span data-stu-id="3ff20-142">Specifies the rules to remove.</span></span>

|||
|-|-|
| <span data-ttu-id="3ff20-143">Alias</span><span class="sxs-lookup"><span data-stu-id="3ff20-143">Aliases</span></span>                              | <span data-ttu-id="3ff20-144">inget</span><span class="sxs-lookup"><span data-stu-id="3ff20-144">none</span></span>                                 |
| <span data-ttu-id="3ff20-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="3ff20-145">Required?</span></span>                            | <span data-ttu-id="3ff20-146">SANT</span><span class="sxs-lookup"><span data-stu-id="3ff20-146">true</span></span>                                 |
| <span data-ttu-id="3ff20-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="3ff20-147">Position?</span></span>                            | <span data-ttu-id="3ff20-148">2</span><span class="sxs-lookup"><span data-stu-id="3ff20-148">2</span></span>                                    |
| <span data-ttu-id="3ff20-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="3ff20-149">Default Value</span></span>                        | <span data-ttu-id="3ff20-150">inget</span><span class="sxs-lookup"><span data-stu-id="3ff20-150">none</span></span>                                 |
| <span data-ttu-id="3ff20-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="3ff20-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3ff20-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="3ff20-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="3ff20-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="3ff20-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3ff20-154">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="3ff20-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3ff20-155">-Confirm</span></span>

<span data-ttu-id="3ff20-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ff20-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="3ff20-157">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="3ff20-157">Required?</span></span>                            | <span data-ttu-id="3ff20-158">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-158">false</span></span>                                |
| <span data-ttu-id="3ff20-159">Placering?</span><span class="sxs-lookup"><span data-stu-id="3ff20-159">Position?</span></span>                            | <span data-ttu-id="3ff20-160">Med namnet</span><span class="sxs-lookup"><span data-stu-id="3ff20-160">named</span></span>                                |
| <span data-ttu-id="3ff20-161">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="3ff20-161">Default Value</span></span>                        | <span data-ttu-id="3ff20-162">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-162">false</span></span>                                |
| <span data-ttu-id="3ff20-163">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="3ff20-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3ff20-164">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-164">false</span></span>                                |
| <span data-ttu-id="3ff20-165">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="3ff20-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3ff20-166">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="3ff20-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3ff20-167">-WhatIf</span></span>

<span data-ttu-id="3ff20-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="3ff20-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3ff20-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3ff20-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="3ff20-170">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="3ff20-170">Required?</span></span>                            | <span data-ttu-id="3ff20-171">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-171">false</span></span>                                |
| <span data-ttu-id="3ff20-172">Placering?</span><span class="sxs-lookup"><span data-stu-id="3ff20-172">Position?</span></span>                            | <span data-ttu-id="3ff20-173">Med namnet</span><span class="sxs-lookup"><span data-stu-id="3ff20-173">named</span></span>                                |
| <span data-ttu-id="3ff20-174">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="3ff20-174">Default Value</span></span>                        | <span data-ttu-id="3ff20-175">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-175">false</span></span>                                |
| <span data-ttu-id="3ff20-176">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="3ff20-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3ff20-177">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-177">false</span></span>                                |
| <span data-ttu-id="3ff20-178">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="3ff20-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3ff20-179">falskt</span><span class="sxs-lookup"><span data-stu-id="3ff20-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="3ff20-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="3ff20-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="3ff20-181">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="3ff20-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="3ff20-182">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3ff20-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="3ff20-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="3ff20-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="3ff20-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="3ff20-184">int\[\]</span></span>

<span data-ttu-id="3ff20-185">Denna cmdlet accepterar en heltalsmatris eller en matris med PswaAuthorizationRule-objekt.</span><span class="sxs-lookup"><span data-stu-id="3ff20-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="3ff20-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="3ff20-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="3ff20-187">Denna cmdlet accepterar en heltalsmatris eller en matris med PswaAuthorizationRule-objekt.</span><span class="sxs-lookup"><span data-stu-id="3ff20-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="3ff20-188">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3ff20-188">OUTPUTS</span></span>

<span data-ttu-id="3ff20-189">Denna cmdlet ger inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3ff20-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="3ff20-190">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3ff20-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="3ff20-191">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="3ff20-191">EXAMPLE 1</span></span>

<span data-ttu-id="3ff20-192">Det här exemplet tar bort auktoriseringsregeln med ID *2*.</span><span class="sxs-lookup"><span data-stu-id="3ff20-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="3ff20-193">EXEMPEL 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="3ff20-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="3ff20-194">Det här exemplet tar bort alla auktoriseringsregler och kräver bekräftelse av användaren.</span><span class="sxs-lookup"><span data-stu-id="3ff20-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="3ff20-195">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="3ff20-195">Related topics</span></span>

- [<span data-ttu-id="3ff20-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3ff20-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="3ff20-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3ff20-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="3ff20-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="3ff20-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="3ff20-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3ff20-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)