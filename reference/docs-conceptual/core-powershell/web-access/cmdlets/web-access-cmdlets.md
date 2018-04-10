---
description: ''
ms.topic: article
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 12/12/2016
title: -cmdletar för Webbåtkomst
ms.technology: powershell
ms.openlocfilehash: 6930fd6a08de69078576fb0d0fbabb04e05d0814
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="8e5cd-103">Windows PowerShell-cmdletar för webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="8e5cd-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="8e5cd-104">Den här referensen innehåller beskrivningar av cmdlet och syntax för alla Windows PowerShell® Web Access-specifika cmdletar.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="8e5cd-105">Den visar cmdlet: ar i alfabetisk ordning baserat på verb i början av cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="8e5cd-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e5cd-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="8e5cd-107">Lägger till en ny auktoriseringsregel regeluppsättningen för auktorisering av Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="8e5cd-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e5cd-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="8e5cd-109">Returnerar en uppsättning auktoriseringsregler för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="8e5cd-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8e5cd-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="8e5cd-111">Konfigurerar Windows PowerShell Web Access-webbprogrammet i IIS.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="8e5cd-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e5cd-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="8e5cd-113">Tar bort en angiven auktoriseringsregel från Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="8e5cd-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="8e5cd-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="8e5cd-115">Testar auktoriseringsregler Kontrollera att en viss användare, dator, endpoint åtkomstbegäran auktoriseras.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="8e5cd-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="8e5cd-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="8e5cd-117">Avinstallerar Windows PowerShell-webbprogrammet från IIS.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="8e5cd-118">**Obs**:</span><span class="sxs-lookup"><span data-stu-id="8e5cd-118">**Note**:</span></span>
>
><span data-ttu-id="8e5cd-119">Om du vill visa en lista över alla cmdlets som är tillgängliga, använda den:</span><span class="sxs-lookup"><span data-stu-id="8e5cd-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="8e5cd-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="8e5cd-121">Mer information om, eller syntaxen för någon av cmdletar, använda: `Get-Help ` *&lt;cmdlet-namn&gt;* där *&lt;cmdlet-namn&gt;* är namnet på den cmdlet som du vill undersöka.</span><span class="sxs-lookup"><span data-stu-id="8e5cd-121">For more information about, or for the syntax of, any of the cmdlets, use: `Get-Help `*&lt;cmdlet name&gt;* where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="8e5cd-122">Du kan köra någon av följande cmdletar för att få mer detaljerad information:</span><span class="sxs-lookup"><span data-stu-id="8e5cd-122">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="8e5cd-123">`Get-Help `*&lt;Cmdlet-namn&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="8e5cd-123">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="8e5cd-124">`Get-Help `*&lt;Cmdlet-namn&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="8e5cd-124">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="8e5cd-125">`Get-Help `*&lt;Cmdlet-namn&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="8e5cd-125">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="8e5cd-126">Mer Information</span><span class="sxs-lookup"><span data-stu-id="8e5cd-126">More Information</span></span>

<span data-ttu-id="8e5cd-127">Mer information om PowerShell-webbåtkomst finns:</span><span class="sxs-lookup"><span data-stu-id="8e5cd-127">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="8e5cd-128">Installera och använda Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="8e5cd-128">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)