---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: installera pswawebapplication
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="b527b-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="b527b-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="b527b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b527b-104">SYNOPSIS</span></span>

<span data-ttu-id="b527b-105">Konfigurerar Windows PowerShell® Web Access-webbprogrammet i IIS.</span><span class="sxs-lookup"><span data-stu-id="b527b-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="b527b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b527b-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="b527b-107">Standard</span><span class="sxs-lookup"><span data-stu-id="b527b-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b527b-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b527b-108">DESCRIPTION</span></span>

<span data-ttu-id="b527b-109">Den **Install-PswaWebApplication** cmdlet konfigurerar Windows PowerShell Web Access-webbprogram.</span><span class="sxs-lookup"><span data-stu-id="b527b-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="b527b-110">Denna cmdlet installerar cmdleten webbprogrammet, kopplas till en webbplats och du kan även skapa en test SSL certifikat med hjälp av den **useTestCertificate** parameter.</span><span class="sxs-lookup"><span data-stu-id="b527b-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="b527b-111">Av säkerhetsskäl bör orsaker webbadministratörer inte använda ett testcertifikat för produktionsmiljöer.</span><span class="sxs-lookup"><span data-stu-id="b527b-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="b527b-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b527b-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="b527b-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="b527b-113">-UseTestCertificate</span></span>

<span data-ttu-id="b527b-114">Anger att ett testcertifikat skapas.</span><span class="sxs-lookup"><span data-stu-id="b527b-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="b527b-115">Om den här parametern anges till true, och sedan denna cmdlet skapar ett testcertifikat och konfigurerar Windows PowerShell Web Access webbprogram att använda certifikat för HTTPS-begäranden.</span><span class="sxs-lookup"><span data-stu-id="b527b-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="b527b-116">Om den här parametern är inställd på false, skapas inga certifikat eller bindning.</span><span class="sxs-lookup"><span data-stu-id="b527b-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="b527b-117">Ange värdet till false om ett annat certifikat används för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b527b-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||  
|-|-|
| <span data-ttu-id="b527b-118">Alias</span><span class="sxs-lookup"><span data-stu-id="b527b-118">Aliases</span></span>                              | <span data-ttu-id="b527b-119">inget</span><span class="sxs-lookup"><span data-stu-id="b527b-119">none</span></span>                                 |
| <span data-ttu-id="b527b-120">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b527b-120">Required?</span></span>                            | <span data-ttu-id="b527b-121">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-121">false</span></span>                                |
| <span data-ttu-id="b527b-122">Placering?</span><span class="sxs-lookup"><span data-stu-id="b527b-122">Position?</span></span>                            | <span data-ttu-id="b527b-123">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b527b-123">named</span></span>                                |
| <span data-ttu-id="b527b-124">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b527b-124">Default Value</span></span>                        | <span data-ttu-id="b527b-125">SANT</span><span class="sxs-lookup"><span data-stu-id="b527b-125">true</span></span>                                 |
| <span data-ttu-id="b527b-126">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b527b-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b527b-127">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-127">false</span></span>                                |
| <span data-ttu-id="b527b-128">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b527b-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b527b-129">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="b527b-130">-WebApplicationName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="b527b-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="b527b-131">Anger namnet för ditt webbprogram.</span><span class="sxs-lookup"><span data-stu-id="b527b-131">Specifies the name for your web application.</span></span> <span data-ttu-id="b527b-132">Detta visas som den sista delen av URL: en Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b527b-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||  
|-|-|
| <span data-ttu-id="b527b-133">Alias</span><span class="sxs-lookup"><span data-stu-id="b527b-133">Aliases</span></span>                              | <span data-ttu-id="b527b-134">inget</span><span class="sxs-lookup"><span data-stu-id="b527b-134">none</span></span>                                 |
| <span data-ttu-id="b527b-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b527b-135">Required?</span></span>                            | <span data-ttu-id="b527b-136">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-136">false</span></span>                                |
| <span data-ttu-id="b527b-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="b527b-137">Position?</span></span>                            | <span data-ttu-id="b527b-138">1</span><span class="sxs-lookup"><span data-stu-id="b527b-138">1</span></span>                                    |
| <span data-ttu-id="b527b-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b527b-139">Default Value</span></span>                        | <span data-ttu-id="b527b-140">pswa</span><span class="sxs-lookup"><span data-stu-id="b527b-140">pswa</span></span>                                 |
| <span data-ttu-id="b527b-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b527b-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b527b-142">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-142">false</span></span>                                |
| <span data-ttu-id="b527b-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b527b-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b527b-144">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="b527b-145">-WebSiteName&lt;sträng&gt;</span><span class="sxs-lookup"><span data-stu-id="b527b-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="b527b-146">Anger namnet på webbplatsen webbserver (IIS) som du vill installera det här webbprogrammet för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b527b-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||  
|-|-|
| <span data-ttu-id="b527b-147">Alias</span><span class="sxs-lookup"><span data-stu-id="b527b-147">Aliases</span></span>                              | <span data-ttu-id="b527b-148">inget</span><span class="sxs-lookup"><span data-stu-id="b527b-148">none</span></span>                                 |
| <span data-ttu-id="b527b-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b527b-149">Required?</span></span>                            | <span data-ttu-id="b527b-150">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-150">false</span></span>                                |
| <span data-ttu-id="b527b-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="b527b-151">Position?</span></span>                            | <span data-ttu-id="b527b-152">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b527b-152">named</span></span>                                |
| <span data-ttu-id="b527b-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b527b-153">Default Value</span></span>                        | <span data-ttu-id="b527b-154">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="b527b-154">Default Web Site</span></span>                     |
| <span data-ttu-id="b527b-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b527b-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b527b-156">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-156">false</span></span>                                |
| <span data-ttu-id="b527b-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b527b-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b527b-158">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="b527b-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b527b-159">-Confirm</span></span>

<span data-ttu-id="b527b-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b527b-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="b527b-161">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b527b-161">Required?</span></span>                            | <span data-ttu-id="b527b-162">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-162">false</span></span>                                |
| <span data-ttu-id="b527b-163">Placering?</span><span class="sxs-lookup"><span data-stu-id="b527b-163">Position?</span></span>                            | <span data-ttu-id="b527b-164">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b527b-164">named</span></span>                                |
| <span data-ttu-id="b527b-165">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b527b-165">Default Value</span></span>                        | <span data-ttu-id="b527b-166">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-166">false</span></span>                                |
| <span data-ttu-id="b527b-167">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b527b-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b527b-168">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-168">false</span></span>                                |
| <span data-ttu-id="b527b-169">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b527b-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b527b-170">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="b527b-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b527b-171">-WhatIf</span></span>

<span data-ttu-id="b527b-172">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b527b-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b527b-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b527b-173">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="b527b-174">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="b527b-174">Required?</span></span>                            | <span data-ttu-id="b527b-175">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-175">false</span></span>                                |
| <span data-ttu-id="b527b-176">Placering?</span><span class="sxs-lookup"><span data-stu-id="b527b-176">Position?</span></span>                            | <span data-ttu-id="b527b-177">Med namnet</span><span class="sxs-lookup"><span data-stu-id="b527b-177">named</span></span>                                |
| <span data-ttu-id="b527b-178">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="b527b-178">Default Value</span></span>                        | <span data-ttu-id="b527b-179">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-179">false</span></span>                                |
| <span data-ttu-id="b527b-180">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="b527b-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b527b-181">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-181">false</span></span>                                |
| <span data-ttu-id="b527b-182">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="b527b-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b527b-183">falskt</span><span class="sxs-lookup"><span data-stu-id="b527b-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="b527b-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="b527b-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="b527b-185">Denna cmdlet stöder de gemensamma parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b527b-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b527b-186">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b527b-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="b527b-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="b527b-187">INPUTS</span></span>

<span data-ttu-id="b527b-188">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="b527b-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="b527b-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b527b-189">OUTPUTS</span></span>

<span data-ttu-id="b527b-190">Denna cmdlet ger inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b527b-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="b527b-191">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b527b-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b527b-192">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="b527b-192">EXAMPLE 1</span></span>

<span data-ttu-id="b527b-193">Det här exemplet installerar PSWA webbprogrammet med standardvärden för de **WebApplicationName** (*pswa*) och **WebSiteName** (*Default Web Site* ) parametrar.</span><span class="sxs-lookup"><span data-stu-id="b527b-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="b527b-194">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="b527b-194">EXAMPLE 2</span></span>

<span data-ttu-id="b527b-195">Det här exemplet installerar PSWA webbprogrammet med ett testcertifikat, och använder standardvärden för de **WebApplicationName** och **WebSiteName** parametrar.</span><span class="sxs-lookup"><span data-stu-id="b527b-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="b527b-196">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="b527b-196">Related topics</span></span>

- [<span data-ttu-id="b527b-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b527b-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="b527b-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b527b-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="b527b-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b527b-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="b527b-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b527b-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
