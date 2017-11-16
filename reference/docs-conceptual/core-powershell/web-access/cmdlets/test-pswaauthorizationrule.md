---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: test-pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="4d93c-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4d93c-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="4d93c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4d93c-104">SYNOPSIS</span></span>

<span data-ttu-id="4d93c-105">Kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="4d93c-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d93c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4d93c-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="4d93c-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="4d93c-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="4d93c-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="4d93c-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="4d93c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4d93c-109">DESCRIPTION</span></span>

<span data-ttu-id="4d93c-110">Den **Test-PswaAuthorizationRule** cmdlet kontrollerar om det finns en regel för en specifik användare, dator eller slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="4d93c-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="4d93c-111">Denna cmdlet kan också användas för att testa auktoriseringsregler för att verifiera att en viss användare, dator eller slutpunkt åtkomst-begäran är auktoriserad.</span><span class="sxs-lookup"><span data-stu-id="4d93c-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="4d93c-112">Som standard utvärderar den här cmdleten alla regler i auktoriseringsfilen.</span><span class="sxs-lookup"><span data-stu-id="4d93c-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="4d93c-113">Du kan dock ange en delmängd av regler som ska testas.</span><span class="sxs-lookup"><span data-stu-id="4d93c-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="4d93c-114">Du kan använda denna cmdlet för att felsöka autentiseringsfel.</span><span class="sxs-lookup"><span data-stu-id="4d93c-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="4d93c-115">Parametrarna för denna cmdlet motsvarar fälten på sidan Windows PowerShell® Web Access inloggning.</span><span class="sxs-lookup"><span data-stu-id="4d93c-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="4d93c-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4d93c-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="4d93c-117">-ComputerName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="4d93c-118">Anger namnet på datorn för att testa.</span><span class="sxs-lookup"><span data-stu-id="4d93c-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4d93c-119">Alias</span><span class="sxs-lookup"><span data-stu-id="4d93c-119">Aliases</span></span>                              | <span data-ttu-id="4d93c-120">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-120">none</span></span>                                 |
| <span data-ttu-id="4d93c-121">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="4d93c-121">Required?</span></span>                            | <span data-ttu-id="4d93c-122">SANT</span><span class="sxs-lookup"><span data-stu-id="4d93c-122">true</span></span>                                 |
| <span data-ttu-id="4d93c-123">Placering?</span><span class="sxs-lookup"><span data-stu-id="4d93c-123">Position?</span></span>                            | <span data-ttu-id="4d93c-124">2</span><span class="sxs-lookup"><span data-stu-id="4d93c-124">2</span></span>                                    |
| <span data-ttu-id="4d93c-125">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4d93c-125">Default Value</span></span>                        | <span data-ttu-id="4d93c-126">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-126">none</span></span>                                 |
| <span data-ttu-id="4d93c-127">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="4d93c-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4d93c-128">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-128">false</span></span>                                |
| <span data-ttu-id="4d93c-129">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="4d93c-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4d93c-130">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="4d93c-131">-ConfigurationName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="4d93c-132">Anger namnet på sessionskonfigurationen Windows PowerShell, även kallat endpoint eller runspace, om du vill testa.</span><span class="sxs-lookup"><span data-stu-id="4d93c-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4d93c-133">Alias</span><span class="sxs-lookup"><span data-stu-id="4d93c-133">Aliases</span></span>                              | <span data-ttu-id="4d93c-134">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-134">none</span></span>                                 |
| <span data-ttu-id="4d93c-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="4d93c-135">Required?</span></span>                            | <span data-ttu-id="4d93c-136">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-136">false</span></span>                                |
| <span data-ttu-id="4d93c-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="4d93c-137">Position?</span></span>                            | <span data-ttu-id="4d93c-138">3</span><span class="sxs-lookup"><span data-stu-id="4d93c-138">3</span></span>                                    |
| <span data-ttu-id="4d93c-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4d93c-139">Default Value</span></span>                        | <span data-ttu-id="4d93c-140">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-140">none</span></span>                                 |
| <span data-ttu-id="4d93c-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="4d93c-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4d93c-142">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-142">false</span></span>                                |
| <span data-ttu-id="4d93c-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="4d93c-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4d93c-144">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="4d93c-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="4d93c-146">Anger URI för att testa anslutningen.</span><span class="sxs-lookup"><span data-stu-id="4d93c-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4d93c-147">Alias</span><span class="sxs-lookup"><span data-stu-id="4d93c-147">Aliases</span></span>                              | <span data-ttu-id="4d93c-148">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-148">none</span></span>                                 |
| <span data-ttu-id="4d93c-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="4d93c-149">Required?</span></span>                            | <span data-ttu-id="4d93c-150">SANT</span><span class="sxs-lookup"><span data-stu-id="4d93c-150">true</span></span>                                 |
| <span data-ttu-id="4d93c-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="4d93c-151">Position?</span></span>                            | <span data-ttu-id="4d93c-152">2</span><span class="sxs-lookup"><span data-stu-id="4d93c-152">2</span></span>                                    |
| <span data-ttu-id="4d93c-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4d93c-153">Default Value</span></span>                        | <span data-ttu-id="4d93c-154">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-154">none</span></span>                                 |
| <span data-ttu-id="4d93c-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="4d93c-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4d93c-156">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-156">false</span></span>                                |
| <span data-ttu-id="4d93c-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="4d93c-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4d93c-158">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="4d93c-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="4d93c-160">Anger en **PSCredential** objekt för ett användarkonto som du vill använda för att testa Windows PowerShell Web Access auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="4d93c-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="4d93c-161">Om du inte lägga till den här parametern används cmdlet det inloggade användarkontot.</span><span class="sxs-lookup"><span data-stu-id="4d93c-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="4d93c-162">Få en **PSCredential** -objektet, vilket krävs för att testa auktoriseringsregler från en fjärrdator, kör den [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d93c-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="4d93c-163">Alias</span><span class="sxs-lookup"><span data-stu-id="4d93c-163">Aliases</span></span>                              | <span data-ttu-id="4d93c-164">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-164">none</span></span>                                 |
| <span data-ttu-id="4d93c-165">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="4d93c-165">Required?</span></span>                            | <span data-ttu-id="4d93c-166">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-166">false</span></span>                                |
| <span data-ttu-id="4d93c-167">Placering?</span><span class="sxs-lookup"><span data-stu-id="4d93c-167">Position?</span></span>                            | <span data-ttu-id="4d93c-168">Med namnet</span><span class="sxs-lookup"><span data-stu-id="4d93c-168">named</span></span>                                |
| <span data-ttu-id="4d93c-169">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4d93c-169">Default Value</span></span>                        | <span data-ttu-id="4d93c-170">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-170">none</span></span>                                 |
| <span data-ttu-id="4d93c-171">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="4d93c-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4d93c-172">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-172">false</span></span>                                |
| <span data-ttu-id="4d93c-173">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="4d93c-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4d93c-174">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="4d93c-175">-Regel &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="4d93c-176">Anger en delmängd av regler som ska testas.</span><span class="sxs-lookup"><span data-stu-id="4d93c-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="4d93c-177">Om den här parametern anges, testar denna cmdlet mot alla auktoriseringsregler.</span><span class="sxs-lookup"><span data-stu-id="4d93c-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="4d93c-178">Alias</span><span class="sxs-lookup"><span data-stu-id="4d93c-178">Aliases</span></span>                              | <span data-ttu-id="4d93c-179">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-179">none</span></span>                                 |
| <span data-ttu-id="4d93c-180">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="4d93c-180">Required?</span></span>                            | <span data-ttu-id="4d93c-181">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-181">false</span></span>                                |
| <span data-ttu-id="4d93c-182">Placering?</span><span class="sxs-lookup"><span data-stu-id="4d93c-182">Position?</span></span>                            | <span data-ttu-id="4d93c-183">Med namnet</span><span class="sxs-lookup"><span data-stu-id="4d93c-183">named</span></span>                                |
| <span data-ttu-id="4d93c-184">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4d93c-184">Default Value</span></span>                        | <span data-ttu-id="4d93c-185">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-185">none</span></span>                                 |
| <span data-ttu-id="4d93c-186">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="4d93c-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4d93c-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="4d93c-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="4d93c-188">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="4d93c-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4d93c-189">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="4d93c-190">-UserName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="4d93c-191">Anger namnet på användaren att testa.</span><span class="sxs-lookup"><span data-stu-id="4d93c-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="4d93c-192">Alias</span><span class="sxs-lookup"><span data-stu-id="4d93c-192">Aliases</span></span>                              | <span data-ttu-id="4d93c-193">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-193">none</span></span>                                 |
| <span data-ttu-id="4d93c-194">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="4d93c-194">Required?</span></span>                            | <span data-ttu-id="4d93c-195">SANT</span><span class="sxs-lookup"><span data-stu-id="4d93c-195">true</span></span>                                 |
| <span data-ttu-id="4d93c-196">Placering?</span><span class="sxs-lookup"><span data-stu-id="4d93c-196">Position?</span></span>                            | <span data-ttu-id="4d93c-197">1</span><span class="sxs-lookup"><span data-stu-id="4d93c-197">1</span></span>                                    |
| <span data-ttu-id="4d93c-198">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4d93c-198">Default Value</span></span>                        | <span data-ttu-id="4d93c-199">inget</span><span class="sxs-lookup"><span data-stu-id="4d93c-199">none</span></span>                                 |
| <span data-ttu-id="4d93c-200">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="4d93c-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="4d93c-201">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-201">false</span></span>                                |
| <span data-ttu-id="4d93c-202">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="4d93c-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="4d93c-203">falskt</span><span class="sxs-lookup"><span data-stu-id="4d93c-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="4d93c-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="4d93c-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="4d93c-205">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="4d93c-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="4d93c-206">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4d93c-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="4d93c-207">INDATA</span><span class="sxs-lookup"><span data-stu-id="4d93c-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4d93c-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4d93c-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4d93c-209">Denna cmdlet accepterar en matris med PswaAuthorizationRule-objekt som indata.</span><span class="sxs-lookup"><span data-stu-id="4d93c-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="4d93c-210">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4d93c-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="4d93c-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="4d93c-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="4d93c-212">Denna cmdlet ger en matris med PswaAuthorizationRule objekt som utdata.</span><span class="sxs-lookup"><span data-stu-id="4d93c-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="4d93c-213">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4d93c-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="4d93c-214">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="4d93c-214">EXAMPLE 1</span></span>

<span data-ttu-id="4d93c-215">Det här exemplet testar alla auktoriseringsregler för att visa alla regler som tillåter att användaren *contoso\\mhanson* att ansluta till datorn *srv2* och använda Windows PowerShell-sessionen konfiguration med namnet *testa*.</span><span class="sxs-lookup"><span data-stu-id="4d93c-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="4d93c-216">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="4d93c-216">EXAMPLE 2</span></span>

<span data-ttu-id="4d93c-217">Det här exemplet testerna alla auktoriseringsregler för att kontrollera vilka auktoriseringsregler som gäller för användaren *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="4d93c-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="4d93c-218">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="4d93c-218">Related topics</span></span>

- [<span data-ttu-id="4d93c-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4d93c-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="4d93c-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4d93c-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="4d93c-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="4d93c-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="4d93c-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="4d93c-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
