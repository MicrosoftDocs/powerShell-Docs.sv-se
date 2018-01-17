---
description: 
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: avinstallera pswawebapplication
ms.technology: powershell
ms.openlocfilehash: cc54c94426d754ff2d3bf658e3e92083f02cd6c7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="241db-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="241db-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="241db-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="241db-104">SYNOPSIS</span></span>

<span data-ttu-id="241db-105">Avinstallerar Windows PowerShell® webbprogrammet.</span><span class="sxs-lookup"><span data-stu-id="241db-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="241db-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="241db-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="241db-107">Standard</span><span class="sxs-lookup"><span data-stu-id="241db-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="241db-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="241db-108">DESCRIPTION</span></span>

<span data-ttu-id="241db-109">Den **Uninstall-PswaWebApplication** cmdlet avinstallerar Windows PowerShell-webbprogram och tar bort webbplatsen från IIS.</span><span class="sxs-lookup"><span data-stu-id="241db-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="241db-110">Cmdlet avinstallerar inte IIS eller andra funktioner som installeras eftersom de var krävs för Windows PowerShell för att köra.</span><span class="sxs-lookup"><span data-stu-id="241db-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="241db-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="241db-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="241db-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="241db-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="241db-113">Anger att testcertifikat som skapats av den **installera\_PswaWebApplication** cmdlet (med den **UseTestCertificate** parametern) tas bort.</span><span class="sxs-lookup"><span data-stu-id="241db-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="241db-114">Endast Testcertifikatet med samma namn som skapas av den **Install-PswaWebApplication** cmdlet tas bort.</span><span class="sxs-lookup"><span data-stu-id="241db-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="241db-115">Alias</span><span class="sxs-lookup"><span data-stu-id="241db-115">Aliases</span></span>                              | <span data-ttu-id="241db-116">inget</span><span class="sxs-lookup"><span data-stu-id="241db-116">none</span></span>                                 |
| <span data-ttu-id="241db-117">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="241db-117">Required?</span></span>                            | <span data-ttu-id="241db-118">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-118">false</span></span>                                |
| <span data-ttu-id="241db-119">Placering?</span><span class="sxs-lookup"><span data-stu-id="241db-119">Position?</span></span>                            | <span data-ttu-id="241db-120">Med namnet</span><span class="sxs-lookup"><span data-stu-id="241db-120">named</span></span>                                |
| <span data-ttu-id="241db-121">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="241db-121">Default Value</span></span>                        | <span data-ttu-id="241db-122">true</span><span class="sxs-lookup"><span data-stu-id="241db-122">true</span></span>                                 |
| <span data-ttu-id="241db-123">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="241db-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="241db-124">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-124">false</span></span>                                |
| <span data-ttu-id="241db-125">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="241db-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="241db-126">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="241db-127">-WebApplicationName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="241db-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="241db-128">Anger namnet på webbprogrammet för att avinstallera.</span><span class="sxs-lookup"><span data-stu-id="241db-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="241db-129">Alias</span><span class="sxs-lookup"><span data-stu-id="241db-129">Aliases</span></span>                              | <span data-ttu-id="241db-130">inget</span><span class="sxs-lookup"><span data-stu-id="241db-130">none</span></span>                                 |
| <span data-ttu-id="241db-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="241db-131">Required?</span></span>                            | <span data-ttu-id="241db-132">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-132">false</span></span>                                |
| <span data-ttu-id="241db-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="241db-133">Position?</span></span>                            | <span data-ttu-id="241db-134">1</span><span class="sxs-lookup"><span data-stu-id="241db-134">1</span></span>                                    |
| <span data-ttu-id="241db-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="241db-135">Default Value</span></span>                        | <span data-ttu-id="241db-136">pswa</span><span class="sxs-lookup"><span data-stu-id="241db-136">pswa</span></span>                                 |
| <span data-ttu-id="241db-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="241db-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="241db-138">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-138">false</span></span>                                |
| <span data-ttu-id="241db-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="241db-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="241db-140">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="241db-141">-WebSiteName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="241db-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="241db-142">Anger namnet på webbplatsen där webbprogrammet är installerat.</span><span class="sxs-lookup"><span data-stu-id="241db-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="241db-143">Alias</span><span class="sxs-lookup"><span data-stu-id="241db-143">Aliases</span></span>                              | <span data-ttu-id="241db-144">inget</span><span class="sxs-lookup"><span data-stu-id="241db-144">none</span></span>                                 |
| <span data-ttu-id="241db-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="241db-145">Required?</span></span>                            | <span data-ttu-id="241db-146">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-146">false</span></span>                                |
| <span data-ttu-id="241db-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="241db-147">Position?</span></span>                            | <span data-ttu-id="241db-148">Med namnet</span><span class="sxs-lookup"><span data-stu-id="241db-148">named</span></span>                                |
| <span data-ttu-id="241db-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="241db-149">Default Value</span></span>                        | <span data-ttu-id="241db-150">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="241db-150">Default Web Site</span></span>                     |
| <span data-ttu-id="241db-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="241db-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="241db-152">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-152">false</span></span>                                |
| <span data-ttu-id="241db-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="241db-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="241db-154">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="241db-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="241db-155">-Confirm</span></span>

<span data-ttu-id="241db-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="241db-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="241db-157">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="241db-157">Required?</span></span>                            | <span data-ttu-id="241db-158">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-158">false</span></span>                                |
| <span data-ttu-id="241db-159">Placering?</span><span class="sxs-lookup"><span data-stu-id="241db-159">Position?</span></span>                            | <span data-ttu-id="241db-160">Med namnet</span><span class="sxs-lookup"><span data-stu-id="241db-160">named</span></span>                                |
| <span data-ttu-id="241db-161">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="241db-161">Default Value</span></span>                        | <span data-ttu-id="241db-162">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-162">false</span></span>                                |
| <span data-ttu-id="241db-163">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="241db-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="241db-164">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-164">false</span></span>                                |
| <span data-ttu-id="241db-165">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="241db-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="241db-166">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="241db-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="241db-167">-WhatIf</span></span>

<span data-ttu-id="241db-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="241db-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="241db-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="241db-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="241db-170">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="241db-170">Required?</span></span>                            | <span data-ttu-id="241db-171">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-171">false</span></span>                                |
| <span data-ttu-id="241db-172">Placering?</span><span class="sxs-lookup"><span data-stu-id="241db-172">Position?</span></span>                            | <span data-ttu-id="241db-173">Med namnet</span><span class="sxs-lookup"><span data-stu-id="241db-173">named</span></span>                                |
| <span data-ttu-id="241db-174">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="241db-174">Default Value</span></span>                        | <span data-ttu-id="241db-175">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-175">false</span></span>                                |
| <span data-ttu-id="241db-176">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="241db-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="241db-177">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-177">false</span></span>                                |
| <span data-ttu-id="241db-178">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="241db-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="241db-179">falskt</span><span class="sxs-lookup"><span data-stu-id="241db-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="241db-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="241db-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="241db-181">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="241db-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="241db-182">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="241db-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="241db-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="241db-183">INPUTS</span></span>

<span data-ttu-id="241db-184">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="241db-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="241db-185">UTDATA</span><span class="sxs-lookup"><span data-stu-id="241db-185">OUTPUTS</span></span>

<span data-ttu-id="241db-186">Den här cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="241db-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="241db-187">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="241db-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="241db-188">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="241db-188">EXAMPLE 1</span></span>

<span data-ttu-id="241db-189">Det här kommandot avinstallerar webbprogrammet för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="241db-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="241db-190">Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med standardvärden.</span><span class="sxs-lookup"><span data-stu-id="241db-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="241db-191">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="241db-191">EXAMPLE 2</span></span>

<span data-ttu-id="241db-192">Det här kommandot avinstallerar Windows PowerShell-webbprogram och tar bort testcertifikat som är associerade med applikationen.</span><span class="sxs-lookup"><span data-stu-id="241db-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="241db-193">Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med hjälp av standardinställningarna och skapa ett testcertifikat.</span><span class="sxs-lookup"><span data-stu-id="241db-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="241db-194">EXEMPEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="241db-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="241db-195">Det här kommandot avinstallerar webbprogrammet för Windows PowerShell när en anpassad webbplats och program som angavs under installationen.</span><span class="sxs-lookup"><span data-stu-id="241db-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="241db-196">Kommandot tar bort den webbplats med namnet *webbplats* och program med namnet *testprogram* och anger att testcertifikat som är associerade med applikationen också tas bort.</span><span class="sxs-lookup"><span data-stu-id="241db-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="241db-197">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="241db-197">Related topics</span></span>

- [<span data-ttu-id="241db-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="241db-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="241db-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="241db-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="241db-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="241db-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="241db-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="241db-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="241db-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="241db-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
