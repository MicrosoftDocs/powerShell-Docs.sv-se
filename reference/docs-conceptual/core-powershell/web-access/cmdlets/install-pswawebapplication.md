---
ms.topic: reference
keywords: PowerShell cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 29e074b75eeb387640831229c63142e6dd5e991a
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268307"
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="aff6a-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="aff6a-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="aff6a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aff6a-104">SYNOPSIS</span></span>

<span data-ttu-id="aff6a-105">Konfigurerar Windows PowerShell Web Access-webbprogram i IIS.</span><span class="sxs-lookup"><span data-stu-id="aff6a-105">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="aff6a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aff6a-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="aff6a-107">Standard</span><span class="sxs-lookup"><span data-stu-id="aff6a-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="aff6a-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aff6a-108">DESCRIPTION</span></span>

<span data-ttu-id="aff6a-109">Den **Install-PswaWebApplication** cmdlet konfigurerar Windows PowerShell Web Access-webbprogram.</span><span class="sxs-lookup"><span data-stu-id="aff6a-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span>
<span data-ttu-id="aff6a-110">Denna cmdlet installerar webbprogrammet, kopplar det till en webbplats och kan även skapa en test SSL certifikatet med den **useTestCertificate** parametern.</span><span class="sxs-lookup"><span data-stu-id="aff6a-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="aff6a-111">För säkerhet orsaker webbadministratörer bör inte använda ett testcertifikat för produktionsmiljöer.</span><span class="sxs-lookup"><span data-stu-id="aff6a-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="aff6a-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aff6a-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="aff6a-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="aff6a-113">-UseTestCertificate</span></span>

<span data-ttu-id="aff6a-114">Anger att ett testcertifikat skapas.</span><span class="sxs-lookup"><span data-stu-id="aff6a-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="aff6a-115">Om den här parametern anges till true, och sedan denna cmdlet skapar ett testcertifikat och konfigurerar det webbaserade programmet i Windows PowerShell-webbåtkomst och använda certifikat för HTTPS-begäranden.</span><span class="sxs-lookup"><span data-stu-id="aff6a-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="aff6a-116">Om den här parametern är inställd på false, skapas ingen certifikat eller en bindning.</span><span class="sxs-lookup"><span data-stu-id="aff6a-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="aff6a-117">Ange värdet till false om ett annat certifikat används för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="aff6a-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="aff6a-118">Alias</span><span class="sxs-lookup"><span data-stu-id="aff6a-118">Aliases</span></span>                              | <span data-ttu-id="aff6a-119">inget</span><span class="sxs-lookup"><span data-stu-id="aff6a-119">none</span></span>                                 |
| <span data-ttu-id="aff6a-120">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="aff6a-120">Required?</span></span>                            | <span data-ttu-id="aff6a-121">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-121">false</span></span>                                |
| <span data-ttu-id="aff6a-122">Placering?</span><span class="sxs-lookup"><span data-stu-id="aff6a-122">Position?</span></span>                            | <span data-ttu-id="aff6a-123">med namnet</span><span class="sxs-lookup"><span data-stu-id="aff6a-123">named</span></span>                                |
| <span data-ttu-id="aff6a-124">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="aff6a-124">Default Value</span></span>                        | <span data-ttu-id="aff6a-125">SANT</span><span class="sxs-lookup"><span data-stu-id="aff6a-125">true</span></span>                                 |
| <span data-ttu-id="aff6a-126">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="aff6a-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="aff6a-127">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-127">false</span></span>                                |
| <span data-ttu-id="aff6a-128">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="aff6a-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="aff6a-129">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-129">false</span></span>                                |

### <a name="-webapplicationname"></a><span data-ttu-id="aff6a-130">-WebApplicationName</span><span class="sxs-lookup"><span data-stu-id="aff6a-130">-WebApplicationName</span></span>

<span data-ttu-id="aff6a-131">Anger namnet för ditt webbprogram.</span><span class="sxs-lookup"><span data-stu-id="aff6a-131">Specifies the name for your web application.</span></span> <span data-ttu-id="aff6a-132">Detta visas som den sista delen av URL: en Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="aff6a-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="aff6a-133">Alias</span><span class="sxs-lookup"><span data-stu-id="aff6a-133">Aliases</span></span>                              | <span data-ttu-id="aff6a-134">inget</span><span class="sxs-lookup"><span data-stu-id="aff6a-134">none</span></span>                                 |
| <span data-ttu-id="aff6a-135">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="aff6a-135">Required?</span></span>                            | <span data-ttu-id="aff6a-136">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-136">false</span></span>                                |
| <span data-ttu-id="aff6a-137">Placering?</span><span class="sxs-lookup"><span data-stu-id="aff6a-137">Position?</span></span>                            | <span data-ttu-id="aff6a-138">1</span><span class="sxs-lookup"><span data-stu-id="aff6a-138">1</span></span>                                    |
| <span data-ttu-id="aff6a-139">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="aff6a-139">Default Value</span></span>                        | <span data-ttu-id="aff6a-140">pswa</span><span class="sxs-lookup"><span data-stu-id="aff6a-140">pswa</span></span>                                 |
| <span data-ttu-id="aff6a-141">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="aff6a-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="aff6a-142">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-142">false</span></span>                                |
| <span data-ttu-id="aff6a-143">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="aff6a-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="aff6a-144">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-144">false</span></span>                                |

### <a name="-websitename"></a><span data-ttu-id="aff6a-145">-WebbPlatsensNamn</span><span class="sxs-lookup"><span data-stu-id="aff6a-145">-WebSiteName</span></span>

<span data-ttu-id="aff6a-146">Anger namnet på Web Server (IIS)-webbplats som du vill installera den här Windows PowerShell Web Access-webbprogram.</span><span class="sxs-lookup"><span data-stu-id="aff6a-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="aff6a-147">Alias</span><span class="sxs-lookup"><span data-stu-id="aff6a-147">Aliases</span></span>                              | <span data-ttu-id="aff6a-148">inget</span><span class="sxs-lookup"><span data-stu-id="aff6a-148">none</span></span>                                 |
| <span data-ttu-id="aff6a-149">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="aff6a-149">Required?</span></span>                            | <span data-ttu-id="aff6a-150">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-150">false</span></span>                                |
| <span data-ttu-id="aff6a-151">Placering?</span><span class="sxs-lookup"><span data-stu-id="aff6a-151">Position?</span></span>                            | <span data-ttu-id="aff6a-152">med namnet</span><span class="sxs-lookup"><span data-stu-id="aff6a-152">named</span></span>                                |
| <span data-ttu-id="aff6a-153">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="aff6a-153">Default Value</span></span>                        | <span data-ttu-id="aff6a-154">Default Web Site</span><span class="sxs-lookup"><span data-stu-id="aff6a-154">Default Web Site</span></span>                     |
| <span data-ttu-id="aff6a-155">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="aff6a-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="aff6a-156">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-156">false</span></span>                                |
| <span data-ttu-id="aff6a-157">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="aff6a-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="aff6a-158">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="aff6a-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aff6a-159">-Confirm</span></span>

<span data-ttu-id="aff6a-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aff6a-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="aff6a-161">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="aff6a-161">Required?</span></span>                            | <span data-ttu-id="aff6a-162">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-162">false</span></span>                                |
| <span data-ttu-id="aff6a-163">Placering?</span><span class="sxs-lookup"><span data-stu-id="aff6a-163">Position?</span></span>                            | <span data-ttu-id="aff6a-164">med namnet</span><span class="sxs-lookup"><span data-stu-id="aff6a-164">named</span></span>                                |
| <span data-ttu-id="aff6a-165">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="aff6a-165">Default Value</span></span>                        | <span data-ttu-id="aff6a-166">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-166">false</span></span>                                |
| <span data-ttu-id="aff6a-167">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="aff6a-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="aff6a-168">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-168">false</span></span>                                |
| <span data-ttu-id="aff6a-169">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="aff6a-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="aff6a-170">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="aff6a-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aff6a-171">-WhatIf</span></span>

<span data-ttu-id="aff6a-172">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="aff6a-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="aff6a-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="aff6a-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="aff6a-174">Obligatorisk?</span><span class="sxs-lookup"><span data-stu-id="aff6a-174">Required?</span></span>                            | <span data-ttu-id="aff6a-175">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-175">false</span></span>                                |
| <span data-ttu-id="aff6a-176">Placering?</span><span class="sxs-lookup"><span data-stu-id="aff6a-176">Position?</span></span>                            | <span data-ttu-id="aff6a-177">med namnet</span><span class="sxs-lookup"><span data-stu-id="aff6a-177">named</span></span>                                |
| <span data-ttu-id="aff6a-178">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="aff6a-178">Default Value</span></span>                        | <span data-ttu-id="aff6a-179">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-179">false</span></span>                                |
| <span data-ttu-id="aff6a-180">Acceptera pipelineindata?</span><span class="sxs-lookup"><span data-stu-id="aff6a-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="aff6a-181">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-181">false</span></span>                                |
| <span data-ttu-id="aff6a-182">Acceptera jokertecken?</span><span class="sxs-lookup"><span data-stu-id="aff6a-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="aff6a-183">falskt</span><span class="sxs-lookup"><span data-stu-id="aff6a-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="aff6a-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="aff6a-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="aff6a-185">Denna cmdlet har stöd för parametrarna:-Verbose,-Debug, - ErrorAction, -ErrorVariable,-OutBuffer och - OutVariable.</span><span class="sxs-lookup"><span data-stu-id="aff6a-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span> <span data-ttu-id="aff6a-186">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aff6a-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="aff6a-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="aff6a-187">INPUTS</span></span>

<span data-ttu-id="aff6a-188">Den här cmdleten tar inga indata.</span><span class="sxs-lookup"><span data-stu-id="aff6a-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="aff6a-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aff6a-189">OUTPUTS</span></span>

<span data-ttu-id="aff6a-190">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="aff6a-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="aff6a-191">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aff6a-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="aff6a-192">EXEMPEL 1</span><span class="sxs-lookup"><span data-stu-id="aff6a-192">EXAMPLE 1</span></span>

<span data-ttu-id="aff6a-193">Det här exemplet installerar PSWA webbprogrammet med standardvärden för de **WebApplicationName** (*pswa*) och **WebbPlatsensNamn** (*Default Web Site* ) parametrar.</span><span class="sxs-lookup"><span data-stu-id="aff6a-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="aff6a-194">EXEMPEL 2</span><span class="sxs-lookup"><span data-stu-id="aff6a-194">EXAMPLE 2</span></span>

<span data-ttu-id="aff6a-195">Det här exemplet installerar PSWA webbprogrammet med ett testcertifikat och använder standardvärden för de **WebApplicationName** och **WebbPlatsensNamn** parametrar.</span><span class="sxs-lookup"><span data-stu-id="aff6a-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="aff6a-196">Närliggande information</span><span class="sxs-lookup"><span data-stu-id="aff6a-196">Related topics</span></span>

- [<span data-ttu-id="aff6a-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="aff6a-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="aff6a-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="aff6a-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="aff6a-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="aff6a-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="aff6a-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="aff6a-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)