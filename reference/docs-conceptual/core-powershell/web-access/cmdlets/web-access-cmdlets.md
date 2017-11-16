---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell-cmdlet
ms.date: 2016-12-12
title: "-cmdletar för Webbåtkomst"
ms.technology: powershell
ms.openlocfilehash: daebe2fe2cbccaf8d3f41d265d23dc45d3bb99b6
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="c85fa-103">Windows PowerShell-cmdletar för webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="c85fa-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="c85fa-104">Den här referensen innehåller beskrivningar av cmdlet och syntax för alla Windows PowerShell® Web Access-specifika cmdletar.</span><span class="sxs-lookup"><span data-stu-id="c85fa-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="c85fa-105">Den visar cmdlet: ar i alfabetisk ordning baserat på verb i början av cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c85fa-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="c85fa-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c85fa-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="c85fa-107">Lägger till en ny auktoriseringsregel regeluppsättningen för auktorisering av Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c85fa-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="c85fa-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c85fa-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="c85fa-109">Returnerar en uppsättning auktoriseringsregler för Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="c85fa-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="c85fa-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="c85fa-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="c85fa-111">Konfigurerar Windows PowerShell Web Access-webbprogrammet i IIS.</span><span class="sxs-lookup"><span data-stu-id="c85fa-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="c85fa-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c85fa-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="c85fa-113">Tar bort en angiven auktoriseringsregel från Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="c85fa-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="c85fa-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c85fa-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="c85fa-115">Testar auktoriseringsregler Kontrollera att en viss användare, dator, endpoint åtkomstbegäran auktoriseras.</span><span class="sxs-lookup"><span data-stu-id="c85fa-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="c85fa-116">Avinstallera-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="c85fa-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="c85fa-117">Avinstallerar Windows PowerShell-webbprogrammet från IIS.</span><span class="sxs-lookup"><span data-stu-id="c85fa-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="c85fa-118">**Obs**:</span><span class="sxs-lookup"><span data-stu-id="c85fa-118">**Note**:</span></span>
>
><span data-ttu-id="c85fa-119">Om du vill visa en lista över alla cmdlets som är tillgängliga, använda den:</span><span class="sxs-lookup"><span data-stu-id="c85fa-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="c85fa-120">`Get-Command –Module PowerShellWebAccess`cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c85fa-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="c85fa-121">Mer information om, eller syntaxen för någon av cmdletar, Använd:</span><span class="sxs-lookup"><span data-stu-id="c85fa-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="c85fa-122">`Get-Help `*&lt;cmdlet-namn&gt;*</span><span class="sxs-lookup"><span data-stu-id="c85fa-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="c85fa-123">där  *&lt;cmdlet-namn&gt;*  är namnet på den cmdlet som du vill undersöka.</span><span class="sxs-lookup"><span data-stu-id="c85fa-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="c85fa-124">Du kan köra någon av följande cmdletar för att få mer detaljerad information:</span><span class="sxs-lookup"><span data-stu-id="c85fa-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="c85fa-125">`Get-Help `*&lt;cmdlet-namn&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="c85fa-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="c85fa-126">`Get-Help `*&lt;cmdlet-namn&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="c85fa-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="c85fa-127">`Get-Help `*&lt;cmdlet-namn&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="c85fa-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="c85fa-128">Mer Information</span><span class="sxs-lookup"><span data-stu-id="c85fa-128">More Information</span></span>

<span data-ttu-id="c85fa-129">Mer information om PowerShell-webbåtkomst finns:</span><span class="sxs-lookup"><span data-stu-id="c85fa-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="c85fa-130">Installera och använda Windows PowerShell-webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="c85fa-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

