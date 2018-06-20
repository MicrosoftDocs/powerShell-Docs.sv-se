---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190153"
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="8c603-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8c603-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="8c603-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8c603-104">SYNOPSIS</span></span>

<span data-ttu-id="8c603-105">Kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="8c603-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c603-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c603-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="8c603-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="8c603-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="8c603-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="8c603-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="8c603-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8c603-109">DESCRIPTION</span></span>

<span data-ttu-id="8c603-110">Den **Test-PswaAuthorizationRule** cmdlet kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="8c603-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="8c603-111">Denna cmdlet kan också användas för att testa auktoriseringsregler för att verifiera att en viss användare, dator eller slutpunkt åtkomst-begäran är auktoriserad.</span><span class="sxs-lookup"><span data-stu-id="8c603-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="8c603-112">Som standard utvärderar den här cmdleten alla regler i auktoriseringsfilen.</span><span class="sxs-lookup"><span data-stu-id="8c603-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="8c603-113">Du kan dock ange en delmängd av regler som ska testas.</span><span class="sxs-lookup"><span data-stu-id="8c603-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="8c603-114">Du kan använda denna cmdlet för att felsöka autentiseringsfel.</span><span class="sxs-lookup"><span data-stu-id="8c603-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="8c603-115">Parametrarna för denna cmdlet motsvarar fälten på sidan Windows PowerShell® Web Access inloggning.</span><span class="sxs-lookup"><span data-stu-id="8c603-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="8c603-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8c603-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="8c603-117">-ComputerName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="8c603-118">Anger namnet på datorn för att testa.</span><span class="sxs-lookup"><span data-stu-id="8c603-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8c603-119">Alias</span><span class="sxs-lookup"><span data-stu-id="8c603-119">Aliases</span></span>                              | <span data-ttu-id="8c603-120">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-120">none</span></span>                                 |
| <span data-ttu-id="8c603-121">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="8c603-121">Required?</span></span>                            | <span data-ttu-id="8c603-122">SANT</span><span class="sxs-lookup"><span data-stu-id="8c603-122">true</span></span>                                 |
| <span data-ttu-id="8c603-123">Placering?</span><span class="sxs-lookup"><span data-stu-id="8c603-123">Position?</span></span>                            | <span data-ttu-id="8c603-124">2</span><span class="sxs-lookup"><span data-stu-id="8c603-124">2</span></span>                                    |
| <span data-ttu-id="8c603-125">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="8c603-125">Default Value</span></span>                        | <span data-ttu-id="8c603-126">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-126">none</span></span>                                 |
| <span data-ttu-id="8c603-127">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="8c603-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8c603-128">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-128">false</span></span>                                |
| <span data-ttu-id="8c603-129">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="8c603-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8c603-130">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="8c603-131">-ConfigurationName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="8c603-132">Anger namnet på sessionskonfigurationen Windows PowerShell, även kallat endpoint eller runspace, om du vill testa.</span><span class="sxs-lookup"><span data-stu-id="8c603-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8c603-133">Alias</span><span class="sxs-lookup"><span data-stu-id="8c603-133">Aliases</span></span>                              | <span data-ttu-id="8c603-134">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-134">none</span></span>                                 |
| <span data-ttu-id="8c603-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="8c603-135">Required?</span></span>                            | <span data-ttu-id="8c603-136">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-136">false</span></span>                                |
| <span data-ttu-id="8c603-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="8c603-137">Position?</span></span>                            | <span data-ttu-id="8c603-138">3</span><span class="sxs-lookup"><span data-stu-id="8c603-138">3</span></span>                                    |
| <span data-ttu-id="8c603-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="8c603-139">Default Value</span></span>                        | <span data-ttu-id="8c603-140">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-140">none</span></span>                                 |
| <span data-ttu-id="8c603-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="8c603-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8c603-142">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-142">false</span></span>                                |
| <span data-ttu-id="8c603-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="8c603-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8c603-144">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="8c603-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="8c603-146">Anger URI för att testa anslutningen.</span><span class="sxs-lookup"><span data-stu-id="8c603-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8c603-147">Alias</span><span class="sxs-lookup"><span data-stu-id="8c603-147">Aliases</span></span>                              | <span data-ttu-id="8c603-148">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-148">none</span></span>                                 |
| <span data-ttu-id="8c603-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="8c603-149">Required?</span></span>                            | <span data-ttu-id="8c603-150">SANT</span><span class="sxs-lookup"><span data-stu-id="8c603-150">true</span></span>                                 |
| <span data-ttu-id="8c603-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="8c603-151">Position?</span></span>                            | <span data-ttu-id="8c603-152">2</span><span class="sxs-lookup"><span data-stu-id="8c603-152">2</span></span>                                    |
| <span data-ttu-id="8c603-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="8c603-153">Default Value</span></span>                        | <span data-ttu-id="8c603-154">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-154">none</span></span>                                 |
| <span data-ttu-id="8c603-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="8c603-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8c603-156">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-156">false</span></span>                                |
| <span data-ttu-id="8c603-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="8c603-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8c603-158">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="8c603-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="8c603-160">Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att testa Windows PowerShell Web Access auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="8c603-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="8c603-161">Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot.</span><span class="sxs-lookup"><span data-stu-id="8c603-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="8c603-162">Få en **PSCredential** -objektet, vilket krävs för att testa auktoriseringsregler från en fjärrdator, kör den [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c603-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="8c603-163">Alias</span><span class="sxs-lookup"><span data-stu-id="8c603-163">Aliases</span></span>                              | <span data-ttu-id="8c603-164">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-164">none</span></span>                                 |
| <span data-ttu-id="8c603-165">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="8c603-165">Required?</span></span>                            | <span data-ttu-id="8c603-166">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-166">false</span></span>                                |
| <span data-ttu-id="8c603-167">Placering?</span><span class="sxs-lookup"><span data-stu-id="8c603-167">Position?</span></span>                            | <span data-ttu-id="8c603-168">Med namnet</span><span class="sxs-lookup"><span data-stu-id="8c603-168">named</span></span>                                |
| <span data-ttu-id="8c603-169">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="8c603-169">Default Value</span></span>                        | <span data-ttu-id="8c603-170">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-170">none</span></span>                                 |
| <span data-ttu-id="8c603-171">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="8c603-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8c603-172">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-172">false</span></span>                                |
| <span data-ttu-id="8c603-173">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="8c603-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8c603-174">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="8c603-175">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="8c603-176">Anger en delmängd av regler som ska testas.</span><span class="sxs-lookup"><span data-stu-id="8c603-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="8c603-177">Om den här parametern anges, testar denna cmdlet mot alla auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="8c603-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="8c603-178">Alias</span><span class="sxs-lookup"><span data-stu-id="8c603-178">Aliases</span></span>                              | <span data-ttu-id="8c603-179">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-179">none</span></span>                                 |
| <span data-ttu-id="8c603-180">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="8c603-180">Required?</span></span>                            | <span data-ttu-id="8c603-181">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-181">false</span></span>                                |
| <span data-ttu-id="8c603-182">Placering?</span><span class="sxs-lookup"><span data-stu-id="8c603-182">Position?</span></span>                            | <span data-ttu-id="8c603-183">Med namnet</span><span class="sxs-lookup"><span data-stu-id="8c603-183">named</span></span>                                |
| <span data-ttu-id="8c603-184">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="8c603-184">Default Value</span></span>                        | <span data-ttu-id="8c603-185">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-185">none</span></span>                                 |
| <span data-ttu-id="8c603-186">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="8c603-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8c603-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="8c603-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="8c603-188">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="8c603-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8c603-189">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="8c603-190">-UserName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="8c603-191">Anger namnet på användaren att testa.</span><span class="sxs-lookup"><span data-stu-id="8c603-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="8c603-192">Alias</span><span class="sxs-lookup"><span data-stu-id="8c603-192">Aliases</span></span>                              | <span data-ttu-id="8c603-193">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-193">none</span></span>                                 |
| <span data-ttu-id="8c603-194">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="8c603-194">Required?</span></span>                            | <span data-ttu-id="8c603-195">SANT</span><span class="sxs-lookup"><span data-stu-id="8c603-195">true</span></span>                                 |
| <span data-ttu-id="8c603-196">Placering?</span><span class="sxs-lookup"><span data-stu-id="8c603-196">Position?</span></span>                            | <span data-ttu-id="8c603-197">1</span><span class="sxs-lookup"><span data-stu-id="8c603-197">1</span></span>                                    |
| <span data-ttu-id="8c603-198">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="8c603-198">Default Value</span></span>                        | <span data-ttu-id="8c603-199">inget</span><span class="sxs-lookup"><span data-stu-id="8c603-199">none</span></span>                                 |
| <span data-ttu-id="8c603-200">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="8c603-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="8c603-201">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-201">false</span></span>                                |
| <span data-ttu-id="8c603-202">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="8c603-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="8c603-203">falskt</span><span class="sxs-lookup"><span data-stu-id="8c603-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="8c603-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="8c603-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="8c603-205">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="8c603-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="8c603-206">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c603-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="8c603-207">INDATA</span><span class="sxs-lookup"><span data-stu-id="8c603-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8c603-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8c603-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8c603-209">Denna cmdlet accepterar en matris med PswaAuthorizationRule-objekt som indata.</span><span class="sxs-lookup"><span data-stu-id="8c603-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="8c603-210">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8c603-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="8c603-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="8c603-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="8c603-212">Denna cmdlet ger en matris med PswaAuthorizationRule objekt som utdata.</span><span class="sxs-lookup"><span data-stu-id="8c603-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="8c603-213">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8c603-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="8c603-214">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="8c603-214">EXAMPLE 1</span></span>

<span data-ttu-id="8c603-215">Det här exemplet testar alla auktoriseringsregler för att visa alla regler som tillåter att användaren *contoso\\mhanson* att ansluta till datorn *srv2* och använda Windows PowerShell-sessionen konfiguration med namnet *testa*.</span><span class="sxs-lookup"><span data-stu-id="8c603-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="8c603-216">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="8c603-216">EXAMPLE 2</span></span>

<span data-ttu-id="8c603-217">Det här exemplet testerna alla auktoriseringsregler för att kontrollera vilka auktoriseringsregler som gäller för användaren *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="8c603-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="8c603-218">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="8c603-218">Related topics</span></span>

- [<span data-ttu-id="8c603-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8c603-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="8c603-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8c603-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="8c603-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8c603-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="8c603-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8c603-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)