---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: avinstallera pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 5fe608b3bfbb90f842f16c1f5a8c51879589cf6d
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="429e2-103">Avinstallera-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="429e2-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="429e2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="429e2-104">SYNOPSIS</span></span>

<span data-ttu-id="429e2-105">Avinstallerar Windows PowerShell® webbprogrammet.</span><span class="sxs-lookup"><span data-stu-id="429e2-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="429e2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="429e2-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="429e2-107">Standard</span><span class="sxs-lookup"><span data-stu-id="429e2-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="429e2-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="429e2-108">DESCRIPTION</span></span>

<span data-ttu-id="429e2-109">Den **Uninstall-PswaWebApplication** cmdlet avinstallerar Windows PowerShell-webbprogram och tar bort webbplatsen från IIS.</span><span class="sxs-lookup"><span data-stu-id="429e2-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="429e2-110">Cmdlet avinstallerar inte IIS eller andra funktioner som installeras eftersom de var krävs för Windows PowerShell för att köra.</span><span class="sxs-lookup"><span data-stu-id="429e2-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="429e2-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="429e2-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="429e2-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="429e2-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="429e2-113">Anger att testcertifikat som skapats av den **installera\_PswaWebApplication** cmdlet (med den **UseTestCertificate** parametern) tas bort.</span><span class="sxs-lookup"><span data-stu-id="429e2-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="429e2-114">Endast Testcertifikatet med samma namn som skapas av den **Install-PswaWebApplication** cmdlet tas bort.</span><span class="sxs-lookup"><span data-stu-id="429e2-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="429e2-115">Alias</span><span class="sxs-lookup"><span data-stu-id="429e2-115">Aliases</span></span>                              | <span data-ttu-id="429e2-116">inget</span><span class="sxs-lookup"><span data-stu-id="429e2-116">none</span></span>                                 |
| <span data-ttu-id="429e2-117">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="429e2-117">Required?</span></span>                            | <span data-ttu-id="429e2-118">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-118">false</span></span>                                |
| <span data-ttu-id="429e2-119">Placering?</span><span class="sxs-lookup"><span data-stu-id="429e2-119">Position?</span></span>                            | <span data-ttu-id="429e2-120">Med namnet</span><span class="sxs-lookup"><span data-stu-id="429e2-120">named</span></span>                                |
| <span data-ttu-id="429e2-121">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="429e2-121">Default Value</span></span>                        | <span data-ttu-id="429e2-122">SANT</span><span class="sxs-lookup"><span data-stu-id="429e2-122">true</span></span>                                 |
| <span data-ttu-id="429e2-123">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="429e2-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="429e2-124">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-124">false</span></span>                                |
| <span data-ttu-id="429e2-125">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="429e2-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="429e2-126">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="429e2-127">-WebApplicationName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="429e2-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="429e2-128">Anger namnet på webbprogrammet för att avinstallera.</span><span class="sxs-lookup"><span data-stu-id="429e2-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="429e2-129">Alias</span><span class="sxs-lookup"><span data-stu-id="429e2-129">Aliases</span></span>                              | <span data-ttu-id="429e2-130">inget</span><span class="sxs-lookup"><span data-stu-id="429e2-130">none</span></span>                                 |
| <span data-ttu-id="429e2-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="429e2-131">Required?</span></span>                            | <span data-ttu-id="429e2-132">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-132">false</span></span>                                |
| <span data-ttu-id="429e2-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="429e2-133">Position?</span></span>                            | <span data-ttu-id="429e2-134">1</span><span class="sxs-lookup"><span data-stu-id="429e2-134">1</span></span>                                    |
| <span data-ttu-id="429e2-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="429e2-135">Default Value</span></span>                        | <span data-ttu-id="429e2-136">pswa</span><span class="sxs-lookup"><span data-stu-id="429e2-136">pswa</span></span>                                 |
| <span data-ttu-id="429e2-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="429e2-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="429e2-138">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-138">false</span></span>                                |
| <span data-ttu-id="429e2-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="429e2-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="429e2-140">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="429e2-141">-WebSiteName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="429e2-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="429e2-142">Anger namnet på webbplatsen där webbprogrammet är installerat.</span><span class="sxs-lookup"><span data-stu-id="429e2-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="429e2-143">Alias</span><span class="sxs-lookup"><span data-stu-id="429e2-143">Aliases</span></span>                              | <span data-ttu-id="429e2-144">inget</span><span class="sxs-lookup"><span data-stu-id="429e2-144">none</span></span>                                 |
| <span data-ttu-id="429e2-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="429e2-145">Required?</span></span>                            | <span data-ttu-id="429e2-146">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-146">false</span></span>                                |
| <span data-ttu-id="429e2-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="429e2-147">Position?</span></span>                            | <span data-ttu-id="429e2-148">Med namnet</span><span class="sxs-lookup"><span data-stu-id="429e2-148">named</span></span>                                |
| <span data-ttu-id="429e2-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="429e2-149">Default Value</span></span>                        | <span data-ttu-id="429e2-150">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="429e2-150">Default Web Site</span></span>                     |
| <span data-ttu-id="429e2-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="429e2-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="429e2-152">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-152">false</span></span>                                |
| <span data-ttu-id="429e2-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="429e2-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="429e2-154">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="429e2-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="429e2-155">-Confirm</span></span>

<span data-ttu-id="429e2-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="429e2-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="429e2-157">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="429e2-157">Required?</span></span>                            | <span data-ttu-id="429e2-158">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-158">false</span></span>                                |
| <span data-ttu-id="429e2-159">Placering?</span><span class="sxs-lookup"><span data-stu-id="429e2-159">Position?</span></span>                            | <span data-ttu-id="429e2-160">Med namnet</span><span class="sxs-lookup"><span data-stu-id="429e2-160">named</span></span>                                |
| <span data-ttu-id="429e2-161">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="429e2-161">Default Value</span></span>                        | <span data-ttu-id="429e2-162">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-162">false</span></span>                                |
| <span data-ttu-id="429e2-163">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="429e2-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="429e2-164">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-164">false</span></span>                                |
| <span data-ttu-id="429e2-165">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="429e2-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="429e2-166">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="429e2-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="429e2-167">-WhatIf</span></span>

<span data-ttu-id="429e2-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="429e2-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="429e2-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="429e2-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="429e2-170">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="429e2-170">Required?</span></span>                            | <span data-ttu-id="429e2-171">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-171">false</span></span>                                |
| <span data-ttu-id="429e2-172">Placering?</span><span class="sxs-lookup"><span data-stu-id="429e2-172">Position?</span></span>                            | <span data-ttu-id="429e2-173">Med namnet</span><span class="sxs-lookup"><span data-stu-id="429e2-173">named</span></span>                                |
| <span data-ttu-id="429e2-174">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="429e2-174">Default Value</span></span>                        | <span data-ttu-id="429e2-175">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-175">false</span></span>                                |
| <span data-ttu-id="429e2-176">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="429e2-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="429e2-177">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-177">false</span></span>                                |
| <span data-ttu-id="429e2-178">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="429e2-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="429e2-179">falskt</span><span class="sxs-lookup"><span data-stu-id="429e2-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="429e2-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="429e2-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="429e2-181">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="429e2-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="429e2-182">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="429e2-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="429e2-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="429e2-183">INPUTS</span></span>

<span data-ttu-id="429e2-184">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="429e2-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="429e2-185">UTDATA</span><span class="sxs-lookup"><span data-stu-id="429e2-185">OUTPUTS</span></span>

<span data-ttu-id="429e2-186">Den här cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="429e2-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="429e2-187">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="429e2-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="429e2-188">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="429e2-188">EXAMPLE 1</span></span>

<span data-ttu-id="429e2-189">Det här kommandot avinstallerar webbprogrammet för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="429e2-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="429e2-190">Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med standardvärden.</span><span class="sxs-lookup"><span data-stu-id="429e2-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="429e2-191">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="429e2-191">EXAMPLE 2</span></span>

<span data-ttu-id="429e2-192">Det här kommandot avinstallerar Windows PowerShell-webbprogram och tar bort testcertifikat som är associerade med applikationen.</span><span class="sxs-lookup"><span data-stu-id="429e2-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="429e2-193">Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med hjälp av standardinställningarna och skapa ett testcertifikat.</span><span class="sxs-lookup"><span data-stu-id="429e2-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="429e2-194">EXEMPEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="429e2-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="429e2-195">Det här kommandot avinstallerar webbprogrammet för Windows PowerShell när en anpassad webbplats och program som angavs under installationen.</span><span class="sxs-lookup"><span data-stu-id="429e2-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="429e2-196">Kommandot tar bort den webbplats med namnet *webbplats* och program med namnet *testprogram* och anger att testcertifikat som är associerade med applikationen också tas bort.</span><span class="sxs-lookup"><span data-stu-id="429e2-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="429e2-197">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="429e2-197">Related topics</span></span>

- [<span data-ttu-id="429e2-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="429e2-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="429e2-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="429e2-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="429e2-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="429e2-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="429e2-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="429e2-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="429e2-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="429e2-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
