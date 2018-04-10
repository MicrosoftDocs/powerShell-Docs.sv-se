---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: ed6d56b2f3c4ee4ac410cdaadda312bffe506ee9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="9b167-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b167-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="9b167-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="9b167-104">SYNOPSIS</span></span>

<span data-ttu-id="9b167-105">Kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="9b167-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b167-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b167-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="9b167-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="9b167-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="9b167-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="9b167-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9b167-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9b167-109">DESCRIPTION</span></span>

<span data-ttu-id="9b167-110">Den **Test-PswaAuthorizationRule** cmdlet kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="9b167-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="9b167-111">Denna cmdlet kan också användas för att testa auktoriseringsregler för att verifiera att en viss användare, dator eller slutpunkt åtkomst-begäran är auktoriserad.</span><span class="sxs-lookup"><span data-stu-id="9b167-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="9b167-112">Som standard utvärderar den här cmdleten alla regler i auktoriseringsfilen.</span><span class="sxs-lookup"><span data-stu-id="9b167-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="9b167-113">Du kan dock ange en delmängd av regler som ska testas.</span><span class="sxs-lookup"><span data-stu-id="9b167-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="9b167-114">Du kan använda denna cmdlet för att felsöka autentiseringsfel.</span><span class="sxs-lookup"><span data-stu-id="9b167-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="9b167-115">Parametrarna för denna cmdlet motsvarar fälten på sidan Windows PowerShell® Web Access inloggning.</span><span class="sxs-lookup"><span data-stu-id="9b167-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="9b167-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9b167-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="9b167-117">-ComputerName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="9b167-118">Anger namnet på datorn för att testa.</span><span class="sxs-lookup"><span data-stu-id="9b167-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9b167-119">Alias</span><span class="sxs-lookup"><span data-stu-id="9b167-119">Aliases</span></span>                              | <span data-ttu-id="9b167-120">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-120">none</span></span>                                 |
| <span data-ttu-id="9b167-121">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="9b167-121">Required?</span></span>                            | <span data-ttu-id="9b167-122">true</span><span class="sxs-lookup"><span data-stu-id="9b167-122">true</span></span>                                 |
| <span data-ttu-id="9b167-123">Placering?</span><span class="sxs-lookup"><span data-stu-id="9b167-123">Position?</span></span>                            | <span data-ttu-id="9b167-124">2</span><span class="sxs-lookup"><span data-stu-id="9b167-124">2</span></span>                                    |
| <span data-ttu-id="9b167-125">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9b167-125">Default Value</span></span>                        | <span data-ttu-id="9b167-126">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-126">none</span></span>                                 |
| <span data-ttu-id="9b167-127">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="9b167-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9b167-128">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-128">false</span></span>                                |
| <span data-ttu-id="9b167-129">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="9b167-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9b167-130">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="9b167-131">-ConfigurationName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="9b167-132">Anger namnet på sessionskonfigurationen Windows PowerShell, även kallat endpoint eller runspace, om du vill testa.</span><span class="sxs-lookup"><span data-stu-id="9b167-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9b167-133">Alias</span><span class="sxs-lookup"><span data-stu-id="9b167-133">Aliases</span></span>                              | <span data-ttu-id="9b167-134">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-134">none</span></span>                                 |
| <span data-ttu-id="9b167-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="9b167-135">Required?</span></span>                            | <span data-ttu-id="9b167-136">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-136">false</span></span>                                |
| <span data-ttu-id="9b167-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="9b167-137">Position?</span></span>                            | <span data-ttu-id="9b167-138">3</span><span class="sxs-lookup"><span data-stu-id="9b167-138">3</span></span>                                    |
| <span data-ttu-id="9b167-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9b167-139">Default Value</span></span>                        | <span data-ttu-id="9b167-140">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-140">none</span></span>                                 |
| <span data-ttu-id="9b167-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="9b167-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9b167-142">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-142">false</span></span>                                |
| <span data-ttu-id="9b167-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="9b167-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9b167-144">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="9b167-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="9b167-146">Anger URI för att testa anslutningen.</span><span class="sxs-lookup"><span data-stu-id="9b167-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9b167-147">Alias</span><span class="sxs-lookup"><span data-stu-id="9b167-147">Aliases</span></span>                              | <span data-ttu-id="9b167-148">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-148">none</span></span>                                 |
| <span data-ttu-id="9b167-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="9b167-149">Required?</span></span>                            | <span data-ttu-id="9b167-150">true</span><span class="sxs-lookup"><span data-stu-id="9b167-150">true</span></span>                                 |
| <span data-ttu-id="9b167-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="9b167-151">Position?</span></span>                            | <span data-ttu-id="9b167-152">2</span><span class="sxs-lookup"><span data-stu-id="9b167-152">2</span></span>                                    |
| <span data-ttu-id="9b167-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9b167-153">Default Value</span></span>                        | <span data-ttu-id="9b167-154">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-154">none</span></span>                                 |
| <span data-ttu-id="9b167-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="9b167-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9b167-156">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-156">false</span></span>                                |
| <span data-ttu-id="9b167-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="9b167-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9b167-158">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="9b167-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="9b167-160">Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att testa Windows PowerShell Web Access auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="9b167-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="9b167-161">Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot.</span><span class="sxs-lookup"><span data-stu-id="9b167-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="9b167-162">Få en **PSCredential** -objektet, vilket krävs för att testa auktoriseringsregler från en fjärrdator, kör den [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b167-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="9b167-163">Alias</span><span class="sxs-lookup"><span data-stu-id="9b167-163">Aliases</span></span>                              | <span data-ttu-id="9b167-164">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-164">none</span></span>                                 |
| <span data-ttu-id="9b167-165">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="9b167-165">Required?</span></span>                            | <span data-ttu-id="9b167-166">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-166">false</span></span>                                |
| <span data-ttu-id="9b167-167">Placering?</span><span class="sxs-lookup"><span data-stu-id="9b167-167">Position?</span></span>                            | <span data-ttu-id="9b167-168">Med namnet</span><span class="sxs-lookup"><span data-stu-id="9b167-168">named</span></span>                                |
| <span data-ttu-id="9b167-169">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9b167-169">Default Value</span></span>                        | <span data-ttu-id="9b167-170">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-170">none</span></span>                                 |
| <span data-ttu-id="9b167-171">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="9b167-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9b167-172">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-172">false</span></span>                                |
| <span data-ttu-id="9b167-173">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="9b167-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9b167-174">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="9b167-175">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="9b167-176">Anger en delmängd av regler som ska testas.</span><span class="sxs-lookup"><span data-stu-id="9b167-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="9b167-177">Om den här parametern anges, testar denna cmdlet mot alla auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="9b167-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="9b167-178">Alias</span><span class="sxs-lookup"><span data-stu-id="9b167-178">Aliases</span></span>                              | <span data-ttu-id="9b167-179">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-179">none</span></span>                                 |
| <span data-ttu-id="9b167-180">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="9b167-180">Required?</span></span>                            | <span data-ttu-id="9b167-181">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-181">false</span></span>                                |
| <span data-ttu-id="9b167-182">Placering?</span><span class="sxs-lookup"><span data-stu-id="9b167-182">Position?</span></span>                            | <span data-ttu-id="9b167-183">Med namnet</span><span class="sxs-lookup"><span data-stu-id="9b167-183">named</span></span>                                |
| <span data-ttu-id="9b167-184">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9b167-184">Default Value</span></span>                        | <span data-ttu-id="9b167-185">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-185">none</span></span>                                 |
| <span data-ttu-id="9b167-186">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="9b167-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9b167-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="9b167-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="9b167-188">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="9b167-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9b167-189">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="9b167-190">-UserName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="9b167-191">Anger namnet på användaren att testa.</span><span class="sxs-lookup"><span data-stu-id="9b167-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9b167-192">Alias</span><span class="sxs-lookup"><span data-stu-id="9b167-192">Aliases</span></span>                              | <span data-ttu-id="9b167-193">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-193">none</span></span>                                 |
| <span data-ttu-id="9b167-194">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="9b167-194">Required?</span></span>                            | <span data-ttu-id="9b167-195">true</span><span class="sxs-lookup"><span data-stu-id="9b167-195">true</span></span>                                 |
| <span data-ttu-id="9b167-196">Placering?</span><span class="sxs-lookup"><span data-stu-id="9b167-196">Position?</span></span>                            | <span data-ttu-id="9b167-197">1</span><span class="sxs-lookup"><span data-stu-id="9b167-197">1</span></span>                                    |
| <span data-ttu-id="9b167-198">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="9b167-198">Default Value</span></span>                        | <span data-ttu-id="9b167-199">inget</span><span class="sxs-lookup"><span data-stu-id="9b167-199">none</span></span>                                 |
| <span data-ttu-id="9b167-200">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="9b167-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9b167-201">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-201">false</span></span>                                |
| <span data-ttu-id="9b167-202">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="9b167-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9b167-203">falskt</span><span class="sxs-lookup"><span data-stu-id="9b167-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9b167-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="9b167-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9b167-205">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="9b167-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9b167-206">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b167-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="9b167-207">INDATA</span><span class="sxs-lookup"><span data-stu-id="9b167-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="9b167-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="9b167-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="9b167-209">Denna cmdlet accepterar en matris med PswaAuthorizationRule-objekt som indata.</span><span class="sxs-lookup"><span data-stu-id="9b167-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9b167-210">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9b167-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="9b167-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="9b167-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="9b167-212">Denna cmdlet ger en matris med PswaAuthorizationRule objekt som utdata.</span><span class="sxs-lookup"><span data-stu-id="9b167-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="9b167-213">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9b167-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9b167-214">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="9b167-214">EXAMPLE 1</span></span>

<span data-ttu-id="9b167-215">Det här exemplet testar alla auktoriseringsregler för att visa alla regler som tillåter att användaren *contoso\\mhanson* att ansluta till datorn *srv2* och använda Windows PowerShell-sessionen konfiguration med namnet *testa*.</span><span class="sxs-lookup"><span data-stu-id="9b167-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="9b167-216">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="9b167-216">EXAMPLE 2</span></span>

<span data-ttu-id="9b167-217">Det här exemplet testerna alla auktoriseringsregler för att kontrollera vilka auktoriseringsregler som gäller för användaren *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="9b167-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="9b167-218">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="9b167-218">Related topics</span></span>

- [<span data-ttu-id="9b167-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b167-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="9b167-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b167-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="9b167-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9b167-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="9b167-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b167-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)