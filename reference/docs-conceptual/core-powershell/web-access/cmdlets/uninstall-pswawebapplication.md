---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Avinstallera-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221926"
---
# <a name="uninstall-pswawebapplication"></a><span data-ttu-id="b0c4c-103">Avinstallera-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b0c4c-103">Uninstall-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="b0c4c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b0c4c-104">SYNOPSIS</span></span>

<span data-ttu-id="b0c4c-105">Avinstallerar Windows PowerShell® webbprogrammet.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0c4c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0c4c-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="b0c4c-107">Standard</span><span class="sxs-lookup"><span data-stu-id="b0c4c-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b0c4c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b0c4c-108">DESCRIPTION</span></span>

<span data-ttu-id="b0c4c-109">Den **Uninstall-PswaWebApplication** cmdlet avinstallerar Windows PowerShell-webbprogram och tar bort webbplatsen från IIS.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="b0c4c-110">Cmdlet avinstallerar inte IIS eller andra funktioner som installeras eftersom de var krävs för Windows PowerShell för att köra.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="b0c4c-111">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b0c4c-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="b0c4c-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="b0c4c-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="b0c4c-113">Anger att testcertifikat som skapats av den **installera\_PswaWebApplication** cmdlet (med den **UseTestCertificate** parametern) tas bort.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="b0c4c-114">Endast Testcertifikatet med samma namn som skapas av den **Install-PswaWebApplication** cmdlet tas bort.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||
|-|-|
| <span data-ttu-id="b0c4c-115">Alias</span><span class="sxs-lookup"><span data-stu-id="b0c4c-115">Aliases</span></span>                              | <span data-ttu-id="b0c4c-116">inget</span><span class="sxs-lookup"><span data-stu-id="b0c4c-116">none</span></span>                                 |
| <span data-ttu-id="b0c4c-117">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-117">Required?</span></span>                            | <span data-ttu-id="b0c4c-118">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-118">false</span></span>                                |
| <span data-ttu-id="b0c4c-119">Placering?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-119">Position?</span></span>                            | <span data-ttu-id="b0c4c-120">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b0c4c-120">named</span></span>                                |
| <span data-ttu-id="b0c4c-121">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b0c4c-121">Default Value</span></span>                        | <span data-ttu-id="b0c4c-122">SANT</span><span class="sxs-lookup"><span data-stu-id="b0c4c-122">true</span></span>                                 |
| <span data-ttu-id="b0c4c-123">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0c4c-124">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-124">false</span></span>                                |
| <span data-ttu-id="b0c4c-125">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0c4c-126">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="b0c4c-127">-WebApplicationName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="b0c4c-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="b0c4c-128">Anger namnet på webbprogrammet för att avinstallera.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-128">Specifies the name of the web application to uninstall.</span></span>

|||
|-|-|
| <span data-ttu-id="b0c4c-129">Alias</span><span class="sxs-lookup"><span data-stu-id="b0c4c-129">Aliases</span></span>                              | <span data-ttu-id="b0c4c-130">inget</span><span class="sxs-lookup"><span data-stu-id="b0c4c-130">none</span></span>                                 |
| <span data-ttu-id="b0c4c-131">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-131">Required?</span></span>                            | <span data-ttu-id="b0c4c-132">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-132">false</span></span>                                |
| <span data-ttu-id="b0c4c-133">Placering?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-133">Position?</span></span>                            | <span data-ttu-id="b0c4c-134">1</span><span class="sxs-lookup"><span data-stu-id="b0c4c-134">1</span></span>                                    |
| <span data-ttu-id="b0c4c-135">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b0c4c-135">Default Value</span></span>                        | <span data-ttu-id="b0c4c-136">pswa</span><span class="sxs-lookup"><span data-stu-id="b0c4c-136">pswa</span></span>                                 |
| <span data-ttu-id="b0c4c-137">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0c4c-138">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-138">false</span></span>                                |
| <span data-ttu-id="b0c4c-139">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0c4c-140">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="b0c4c-141">-WebSiteName &lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="b0c4c-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="b0c4c-142">Anger namnet på webbplatsen där webbprogrammet är installerat.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-142">Specifies the name of the web site where the web application is installed.</span></span>

|||
|-|-|
| <span data-ttu-id="b0c4c-143">Alias</span><span class="sxs-lookup"><span data-stu-id="b0c4c-143">Aliases</span></span>                              | <span data-ttu-id="b0c4c-144">inget</span><span class="sxs-lookup"><span data-stu-id="b0c4c-144">none</span></span>                                 |
| <span data-ttu-id="b0c4c-145">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-145">Required?</span></span>                            | <span data-ttu-id="b0c4c-146">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-146">false</span></span>                                |
| <span data-ttu-id="b0c4c-147">Placering?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-147">Position?</span></span>                            | <span data-ttu-id="b0c4c-148">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b0c4c-148">named</span></span>                                |
| <span data-ttu-id="b0c4c-149">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b0c4c-149">Default Value</span></span>                        | <span data-ttu-id="b0c4c-150">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="b0c4c-150">Default Web Site</span></span>                     |
| <span data-ttu-id="b0c4c-151">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0c4c-152">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-152">false</span></span>                                |
| <span data-ttu-id="b0c4c-153">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0c4c-154">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="b0c4c-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b0c4c-155">-Confirm</span></span>

<span data-ttu-id="b0c4c-156">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="b0c4c-157">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-157">Required?</span></span>                            | <span data-ttu-id="b0c4c-158">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-158">false</span></span>                                |
| <span data-ttu-id="b0c4c-159">Placering?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-159">Position?</span></span>                            | <span data-ttu-id="b0c4c-160">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b0c4c-160">named</span></span>                                |
| <span data-ttu-id="b0c4c-161">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b0c4c-161">Default Value</span></span>                        | <span data-ttu-id="b0c4c-162">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-162">false</span></span>                                |
| <span data-ttu-id="b0c4c-163">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0c4c-164">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-164">false</span></span>                                |
| <span data-ttu-id="b0c4c-165">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0c4c-166">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="b0c4c-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b0c4c-167">-WhatIf</span></span>

<span data-ttu-id="b0c4c-168">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b0c4c-169">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-169">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="b0c4c-170">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-170">Required?</span></span>                            | <span data-ttu-id="b0c4c-171">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-171">false</span></span>                                |
| <span data-ttu-id="b0c4c-172">Placering?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-172">Position?</span></span>                            | <span data-ttu-id="b0c4c-173">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b0c4c-173">named</span></span>                                |
| <span data-ttu-id="b0c4c-174">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b0c4c-174">Default Value</span></span>                        | <span data-ttu-id="b0c4c-175">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-175">false</span></span>                                |
| <span data-ttu-id="b0c4c-176">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b0c4c-177">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-177">false</span></span>                                |
| <span data-ttu-id="b0c4c-178">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b0c4c-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b0c4c-179">falskt</span><span class="sxs-lookup"><span data-stu-id="b0c4c-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b0c4c-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b0c4c-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b0c4c-181">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b0c4c-182">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b0c4c-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b0c4c-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="b0c4c-183">INPUTS</span></span>

<span data-ttu-id="b0c4c-184">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="b0c4c-185">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b0c4c-185">OUTPUTS</span></span>

<span data-ttu-id="b0c4c-186">Den här cmdleten returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="b0c4c-187">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b0c4c-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b0c4c-188">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="b0c4c-188">EXAMPLE 1</span></span>

<span data-ttu-id="b0c4c-189">Det här kommandot avinstallerar webbprogrammet för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="b0c4c-190">Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med standardvärden.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="b0c4c-191">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="b0c4c-191">EXAMPLE 2</span></span>

<span data-ttu-id="b0c4c-192">Det här kommandot avinstallerar Windows PowerShell-webbprogram och tar bort testcertifikat som är associerade med applikationen.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="b0c4c-193">Du kan använda denna cmdlet för att avinstallera Windows PowerShell-webbprogrammet om du har installerat den med hjälp av standardinställningarna och skapa ett testcertifikat.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="b0c4c-194">EXEMPEL 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="b0c4c-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="b0c4c-195">Det här kommandot avinstallerar webbprogrammet för Windows PowerShell när en anpassad webbplats och program som angavs under installationen.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="b0c4c-196">Kommandot tar bort den webbplats med namnet *webbplats* och program med namnet *testprogram* och anger att testcertifikat som är associerade med applikationen också tas bort.</span><span class="sxs-lookup"><span data-stu-id="b0c4c-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="b0c4c-197">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="b0c4c-197">Related topics</span></span>

- [<span data-ttu-id="b0c4c-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0c4c-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b0c4c-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0c4c-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b0c4c-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b0c4c-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="b0c4c-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0c4c-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="b0c4c-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b0c4c-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)