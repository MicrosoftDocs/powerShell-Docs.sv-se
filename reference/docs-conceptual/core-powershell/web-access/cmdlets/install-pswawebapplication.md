---
ms.topic: reference
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="e992c-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e992c-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="e992c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e992c-104">SYNOPSIS</span></span>

<span data-ttu-id="e992c-105">Konfigurerar Windows PowerShell® Web Access-webbprogrammet i IIS.</span><span class="sxs-lookup"><span data-stu-id="e992c-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="e992c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e992c-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="e992c-107">Standard</span><span class="sxs-lookup"><span data-stu-id="e992c-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="e992c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e992c-108">DESCRIPTION</span></span>

<span data-ttu-id="e992c-109">Den **Install-PswaWebApplication** cmdlet konfigurerar Windows PowerShell Web Access-webbprogram.</span><span class="sxs-lookup"><span data-stu-id="e992c-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="e992c-110">Denna cmdlet installerar cmdleten webbprogrammet, kopplas till en webbplats och du kan även skapa en test SSL certifikat med hjälp av den **useTestCertificate** parameter.</span><span class="sxs-lookup"><span data-stu-id="e992c-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="e992c-111">Av säkerhetsskäl bör orsaker webbadministratörer inte använda ett testcertifikat för produktionsmiljöer.</span><span class="sxs-lookup"><span data-stu-id="e992c-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="e992c-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e992c-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="e992c-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="e992c-113">-UseTestCertificate</span></span>

<span data-ttu-id="e992c-114">Anger att ett testcertifikat skapas.</span><span class="sxs-lookup"><span data-stu-id="e992c-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="e992c-115">Om den här parametern anges till true, och sedan denna cmdlet skapar ett testcertifikat och konfigurerar Windows PowerShell Web Access webbprogram att använda certifikat för HTTPS-begäranden.</span><span class="sxs-lookup"><span data-stu-id="e992c-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="e992c-116">Om den här parametern är inställd på false, skapas inga certifikat eller bindning.</span><span class="sxs-lookup"><span data-stu-id="e992c-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="e992c-117">Ange värdet till false om ett annat certifikat används för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="e992c-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="e992c-118">Alias</span><span class="sxs-lookup"><span data-stu-id="e992c-118">Aliases</span></span>                              | <span data-ttu-id="e992c-119">inget</span><span class="sxs-lookup"><span data-stu-id="e992c-119">none</span></span>                                 |
| <span data-ttu-id="e992c-120">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="e992c-120">Required?</span></span>                            | <span data-ttu-id="e992c-121">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-121">false</span></span>                                |
| <span data-ttu-id="e992c-122">Placering?</span><span class="sxs-lookup"><span data-stu-id="e992c-122">Position?</span></span>                            | <span data-ttu-id="e992c-123">Med namnet</span><span class="sxs-lookup"><span data-stu-id="e992c-123">named</span></span>                                |
| <span data-ttu-id="e992c-124">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="e992c-124">Default Value</span></span>                        | <span data-ttu-id="e992c-125">SANT</span><span class="sxs-lookup"><span data-stu-id="e992c-125">true</span></span>                                 |
| <span data-ttu-id="e992c-126">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="e992c-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e992c-127">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-127">false</span></span>                                |
| <span data-ttu-id="e992c-128">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="e992c-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e992c-129">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="e992c-130">-WebApplicationName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="e992c-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="e992c-131">Anger namnet för ditt webbprogram.</span><span class="sxs-lookup"><span data-stu-id="e992c-131">Specifies the name for your web application.</span></span> <span data-ttu-id="e992c-132">Detta visas som den sista delen av URL: en Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="e992c-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="e992c-133">Alias</span><span class="sxs-lookup"><span data-stu-id="e992c-133">Aliases</span></span>                              | <span data-ttu-id="e992c-134">inget</span><span class="sxs-lookup"><span data-stu-id="e992c-134">none</span></span>                                 |
| <span data-ttu-id="e992c-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="e992c-135">Required?</span></span>                            | <span data-ttu-id="e992c-136">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-136">false</span></span>                                |
| <span data-ttu-id="e992c-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="e992c-137">Position?</span></span>                            | <span data-ttu-id="e992c-138">1</span><span class="sxs-lookup"><span data-stu-id="e992c-138">1</span></span>                                    |
| <span data-ttu-id="e992c-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="e992c-139">Default Value</span></span>                        | <span data-ttu-id="e992c-140">pswa</span><span class="sxs-lookup"><span data-stu-id="e992c-140">pswa</span></span>                                 |
| <span data-ttu-id="e992c-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="e992c-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e992c-142">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-142">false</span></span>                                |
| <span data-ttu-id="e992c-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="e992c-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e992c-144">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="e992c-145">-WebSiteName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="e992c-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="e992c-146">Anger namnet på webbplatsen webbserver (IIS) som du vill installera det här webbprogrammet för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="e992c-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="e992c-147">Alias</span><span class="sxs-lookup"><span data-stu-id="e992c-147">Aliases</span></span>                              | <span data-ttu-id="e992c-148">inget</span><span class="sxs-lookup"><span data-stu-id="e992c-148">none</span></span>                                 |
| <span data-ttu-id="e992c-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="e992c-149">Required?</span></span>                            | <span data-ttu-id="e992c-150">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-150">false</span></span>                                |
| <span data-ttu-id="e992c-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="e992c-151">Position?</span></span>                            | <span data-ttu-id="e992c-152">Med namnet</span><span class="sxs-lookup"><span data-stu-id="e992c-152">named</span></span>                                |
| <span data-ttu-id="e992c-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="e992c-153">Default Value</span></span>                        | <span data-ttu-id="e992c-154">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="e992c-154">Default Web Site</span></span>                     |
| <span data-ttu-id="e992c-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="e992c-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e992c-156">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-156">false</span></span>                                |
| <span data-ttu-id="e992c-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="e992c-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e992c-158">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="e992c-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e992c-159">-Confirm</span></span>

<span data-ttu-id="e992c-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e992c-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="e992c-161">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="e992c-161">Required?</span></span>                            | <span data-ttu-id="e992c-162">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-162">false</span></span>                                |
| <span data-ttu-id="e992c-163">Placering?</span><span class="sxs-lookup"><span data-stu-id="e992c-163">Position?</span></span>                            | <span data-ttu-id="e992c-164">Med namnet</span><span class="sxs-lookup"><span data-stu-id="e992c-164">named</span></span>                                |
| <span data-ttu-id="e992c-165">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="e992c-165">Default Value</span></span>                        | <span data-ttu-id="e992c-166">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-166">false</span></span>                                |
| <span data-ttu-id="e992c-167">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="e992c-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e992c-168">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-168">false</span></span>                                |
| <span data-ttu-id="e992c-169">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="e992c-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e992c-170">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="e992c-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e992c-171">-WhatIf</span></span>

<span data-ttu-id="e992c-172">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e992c-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e992c-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e992c-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="e992c-174">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="e992c-174">Required?</span></span>                            | <span data-ttu-id="e992c-175">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-175">false</span></span>                                |
| <span data-ttu-id="e992c-176">Placering?</span><span class="sxs-lookup"><span data-stu-id="e992c-176">Position?</span></span>                            | <span data-ttu-id="e992c-177">Med namnet</span><span class="sxs-lookup"><span data-stu-id="e992c-177">named</span></span>                                |
| <span data-ttu-id="e992c-178">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="e992c-178">Default Value</span></span>                        | <span data-ttu-id="e992c-179">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-179">false</span></span>                                |
| <span data-ttu-id="e992c-180">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="e992c-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e992c-181">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-181">false</span></span>                                |
| <span data-ttu-id="e992c-182">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="e992c-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e992c-183">falskt</span><span class="sxs-lookup"><span data-stu-id="e992c-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="e992c-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="e992c-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="e992c-185">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="e992c-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="e992c-186">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e992c-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="e992c-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="e992c-187">INPUTS</span></span>

<span data-ttu-id="e992c-188">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="e992c-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="e992c-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e992c-189">OUTPUTS</span></span>

<span data-ttu-id="e992c-190">Denna cmdlet ger inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e992c-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="e992c-191">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e992c-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="e992c-192">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="e992c-192">EXAMPLE 1</span></span>

<span data-ttu-id="e992c-193">Det här exemplet installerar PSWA webbprogrammet med standardvärden för de **WebApplicationName** (*pswa*) och **WebSiteName** (*Default Web Site* ) parametrar.</span><span class="sxs-lookup"><span data-stu-id="e992c-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="e992c-194">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="e992c-194">EXAMPLE 2</span></span>

<span data-ttu-id="e992c-195">Det här exemplet installerar PSWA webbprogrammet med ett testcertifikat, och använder standardvärden för de **WebApplicationName** och **WebSiteName** parametrar.</span><span class="sxs-lookup"><span data-stu-id="e992c-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="e992c-196">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="e992c-196">Related topics</span></span>

- [<span data-ttu-id="e992c-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e992c-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="e992c-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e992c-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="e992c-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e992c-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="e992c-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e992c-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)