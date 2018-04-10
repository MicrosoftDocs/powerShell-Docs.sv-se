---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: installera pswawebapplication
ms.technology: powershell
ms.openlocfilehash: c7f7768a41b6784d8c29afa1fccf0b855160b777
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="74bc7-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="74bc7-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="74bc7-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="74bc7-104">SYNOPSIS</span></span>

<span data-ttu-id="74bc7-105">Konfigurerar Windows PowerShell® Web Access-webbprogrammet i IIS.</span><span class="sxs-lookup"><span data-stu-id="74bc7-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="74bc7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74bc7-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="74bc7-107">Standard</span><span class="sxs-lookup"><span data-stu-id="74bc7-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="74bc7-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="74bc7-108">DESCRIPTION</span></span>

<span data-ttu-id="74bc7-109">Den **Install-PswaWebApplication** cmdlet konfigurerar Windows PowerShell Web Access-webbprogram.</span><span class="sxs-lookup"><span data-stu-id="74bc7-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="74bc7-110">Denna cmdlet installerar cmdleten webbprogrammet, kopplas till en webbplats och du kan även skapa en test SSL certifikat med hjälp av den **useTestCertificate** parameter.</span><span class="sxs-lookup"><span data-stu-id="74bc7-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="74bc7-111">Av säkerhetsskäl bör orsaker webbadministratörer inte använda ett testcertifikat för produktionsmiljöer.</span><span class="sxs-lookup"><span data-stu-id="74bc7-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="74bc7-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="74bc7-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="74bc7-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="74bc7-113">-UseTestCertificate</span></span>

<span data-ttu-id="74bc7-114">Anger att ett testcertifikat skapas.</span><span class="sxs-lookup"><span data-stu-id="74bc7-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="74bc7-115">Om den här parametern anges till true, och sedan denna cmdlet skapar ett testcertifikat och konfigurerar Windows PowerShell Web Access webbprogram att använda certifikat för HTTPS-begäranden.</span><span class="sxs-lookup"><span data-stu-id="74bc7-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="74bc7-116">Om den här parametern är inställd på false, skapas inga certifikat eller bindning.</span><span class="sxs-lookup"><span data-stu-id="74bc7-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="74bc7-117">Ange värdet till false om ett annat certifikat används för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="74bc7-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="74bc7-118">Alias</span><span class="sxs-lookup"><span data-stu-id="74bc7-118">Aliases</span></span>                              | <span data-ttu-id="74bc7-119">inget</span><span class="sxs-lookup"><span data-stu-id="74bc7-119">none</span></span>                                 |
| <span data-ttu-id="74bc7-120">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="74bc7-120">Required?</span></span>                            | <span data-ttu-id="74bc7-121">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-121">false</span></span>                                |
| <span data-ttu-id="74bc7-122">Placering?</span><span class="sxs-lookup"><span data-stu-id="74bc7-122">Position?</span></span>                            | <span data-ttu-id="74bc7-123">Med namnet</span><span class="sxs-lookup"><span data-stu-id="74bc7-123">named</span></span>                                |
| <span data-ttu-id="74bc7-124">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="74bc7-124">Default Value</span></span>                        | <span data-ttu-id="74bc7-125">true</span><span class="sxs-lookup"><span data-stu-id="74bc7-125">true</span></span>                                 |
| <span data-ttu-id="74bc7-126">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="74bc7-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="74bc7-127">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-127">false</span></span>                                |
| <span data-ttu-id="74bc7-128">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="74bc7-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="74bc7-129">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="74bc7-130">-WebApplicationName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="74bc7-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="74bc7-131">Anger namnet för ditt webbprogram.</span><span class="sxs-lookup"><span data-stu-id="74bc7-131">Specifies the name for your web application.</span></span> <span data-ttu-id="74bc7-132">Detta visas som den sista delen av URL: en Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="74bc7-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="74bc7-133">Alias</span><span class="sxs-lookup"><span data-stu-id="74bc7-133">Aliases</span></span>                              | <span data-ttu-id="74bc7-134">inget</span><span class="sxs-lookup"><span data-stu-id="74bc7-134">none</span></span>                                 |
| <span data-ttu-id="74bc7-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="74bc7-135">Required?</span></span>                            | <span data-ttu-id="74bc7-136">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-136">false</span></span>                                |
| <span data-ttu-id="74bc7-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="74bc7-137">Position?</span></span>                            | <span data-ttu-id="74bc7-138">1</span><span class="sxs-lookup"><span data-stu-id="74bc7-138">1</span></span>                                    |
| <span data-ttu-id="74bc7-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="74bc7-139">Default Value</span></span>                        | <span data-ttu-id="74bc7-140">pswa</span><span class="sxs-lookup"><span data-stu-id="74bc7-140">pswa</span></span>                                 |
| <span data-ttu-id="74bc7-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="74bc7-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="74bc7-142">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-142">false</span></span>                                |
| <span data-ttu-id="74bc7-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="74bc7-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="74bc7-144">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="74bc7-145">-WebSiteName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="74bc7-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="74bc7-146">Anger namnet på webbplatsen webbserver (IIS) som du vill installera det här webbprogrammet för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="74bc7-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="74bc7-147">Alias</span><span class="sxs-lookup"><span data-stu-id="74bc7-147">Aliases</span></span>                              | <span data-ttu-id="74bc7-148">inget</span><span class="sxs-lookup"><span data-stu-id="74bc7-148">none</span></span>                                 |
| <span data-ttu-id="74bc7-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="74bc7-149">Required?</span></span>                            | <span data-ttu-id="74bc7-150">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-150">false</span></span>                                |
| <span data-ttu-id="74bc7-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="74bc7-151">Position?</span></span>                            | <span data-ttu-id="74bc7-152">Med namnet</span><span class="sxs-lookup"><span data-stu-id="74bc7-152">named</span></span>                                |
| <span data-ttu-id="74bc7-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="74bc7-153">Default Value</span></span>                        | <span data-ttu-id="74bc7-154">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="74bc7-154">Default Web Site</span></span>                     |
| <span data-ttu-id="74bc7-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="74bc7-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="74bc7-156">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-156">false</span></span>                                |
| <span data-ttu-id="74bc7-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="74bc7-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="74bc7-158">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="74bc7-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="74bc7-159">-Confirm</span></span>

<span data-ttu-id="74bc7-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74bc7-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="74bc7-161">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="74bc7-161">Required?</span></span>                            | <span data-ttu-id="74bc7-162">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-162">false</span></span>                                |
| <span data-ttu-id="74bc7-163">Placering?</span><span class="sxs-lookup"><span data-stu-id="74bc7-163">Position?</span></span>                            | <span data-ttu-id="74bc7-164">Med namnet</span><span class="sxs-lookup"><span data-stu-id="74bc7-164">named</span></span>                                |
| <span data-ttu-id="74bc7-165">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="74bc7-165">Default Value</span></span>                        | <span data-ttu-id="74bc7-166">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-166">false</span></span>                                |
| <span data-ttu-id="74bc7-167">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="74bc7-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="74bc7-168">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-168">false</span></span>                                |
| <span data-ttu-id="74bc7-169">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="74bc7-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="74bc7-170">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="74bc7-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="74bc7-171">-WhatIf</span></span>

<span data-ttu-id="74bc7-172">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="74bc7-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="74bc7-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="74bc7-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="74bc7-174">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="74bc7-174">Required?</span></span>                            | <span data-ttu-id="74bc7-175">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-175">false</span></span>                                |
| <span data-ttu-id="74bc7-176">Placering?</span><span class="sxs-lookup"><span data-stu-id="74bc7-176">Position?</span></span>                            | <span data-ttu-id="74bc7-177">Med namnet</span><span class="sxs-lookup"><span data-stu-id="74bc7-177">named</span></span>                                |
| <span data-ttu-id="74bc7-178">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="74bc7-178">Default Value</span></span>                        | <span data-ttu-id="74bc7-179">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-179">false</span></span>                                |
| <span data-ttu-id="74bc7-180">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="74bc7-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="74bc7-181">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-181">false</span></span>                                |
| <span data-ttu-id="74bc7-182">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="74bc7-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="74bc7-183">falskt</span><span class="sxs-lookup"><span data-stu-id="74bc7-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="74bc7-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="74bc7-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="74bc7-185">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="74bc7-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="74bc7-186">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="74bc7-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="74bc7-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="74bc7-187">INPUTS</span></span>

<span data-ttu-id="74bc7-188">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="74bc7-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="74bc7-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="74bc7-189">OUTPUTS</span></span>

<span data-ttu-id="74bc7-190">Denna cmdlet ger inga utdata.</span><span class="sxs-lookup"><span data-stu-id="74bc7-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="74bc7-191">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="74bc7-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="74bc7-192">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="74bc7-192">EXAMPLE 1</span></span>

<span data-ttu-id="74bc7-193">Det här exemplet installerar PSWA webbprogrammet med standardvärden för de **WebApplicationName** (*pswa*) och **WebSiteName** (*Default Web Site* ) parametrar.</span><span class="sxs-lookup"><span data-stu-id="74bc7-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="74bc7-194">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="74bc7-194">EXAMPLE 2</span></span>

<span data-ttu-id="74bc7-195">Det här exemplet installerar PSWA webbprogrammet med ett testcertifikat, och använder standardvärden för de **WebApplicationName** och **WebSiteName** parametrar.</span><span class="sxs-lookup"><span data-stu-id="74bc7-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="74bc7-196">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="74bc7-196">Related topics</span></span>

- [<span data-ttu-id="74bc7-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="74bc7-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="74bc7-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="74bc7-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="74bc7-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="74bc7-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="74bc7-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="74bc7-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)