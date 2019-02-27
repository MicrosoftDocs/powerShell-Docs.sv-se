---
title: Namnge hjälpfiler | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847280"
---
# <a name="naming-help-files"></a><span data-ttu-id="6cf61-102">Namnge hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="6cf61-102">Naming Help Files</span></span>

<span data-ttu-id="6cf61-103">Det här avsnittet beskriver hur du namnger en XML-baserade hjälpfil så att den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kan hitta den.</span><span class="sxs-lookup"><span data-stu-id="6cf61-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="6cf61-104">Krav för namnet skiljer sig åt för varje kommando.</span><span class="sxs-lookup"><span data-stu-id="6cf61-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="6cf61-105">Det här avsnittet beskriver hur du namnger en XML-baserade hjälpfil så att den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kan hitta den.</span><span class="sxs-lookup"><span data-stu-id="6cf61-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="6cf61-106">Krav för namnet skiljer sig åt för varje kommando.</span><span class="sxs-lookup"><span data-stu-id="6cf61-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="6cf61-107">Cmdlet-hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="6cf61-107">Cmdlet Help Files</span></span>

<span data-ttu-id="6cf61-108">I hjälpfilen en C# cmdlet måste ha namnet för sammansättningen där cmdleten har definierats.</span><span class="sxs-lookup"><span data-stu-id="6cf61-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="6cf61-109">Använd formatet följande namn:</span><span class="sxs-lookup"><span data-stu-id="6cf61-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="6cf61-110">Sammansättningen namnformat krävs även när sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="6cf61-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="6cf61-111">Till exempel den [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet har definierats i sammansättningen Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="6cf61-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="6cf61-112">Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för de `Get-WinEvent` cmdlet endast i filen Microsoft.PowerShell.Diagnostics.dll help.xml i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="6cf61-113">Till exempel den [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet har definierats i sammansättningen Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="6cf61-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="6cf61-114">Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för de `Get-WinEvent` cmdlet endast i filen Microsoft.PowerShell.Diagnostics.dll help.xml i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="6cf61-115">Providern hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="6cf61-115">Provider Help files</span></span>

<span data-ttu-id="6cf61-116">I hjälpfilen för en Windows PowerShell-provider måste ha namnet för sammansättningen som providern definieras.</span><span class="sxs-lookup"><span data-stu-id="6cf61-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="6cf61-117">Använd formatet följande namn:</span><span class="sxs-lookup"><span data-stu-id="6cf61-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="6cf61-118">Sammansättningen namnformat krävs även när sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="6cf61-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="6cf61-119">Till exempel har certifikatleverantör definierats i sammansättningen Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="6cf61-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="6cf61-120">Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för certifikatleverantör endast i filen Microsoft.PowerShell.Security.dll help.xml i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="6cf61-121">Funktionen hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="6cf61-121">Function Help Files</span></span>

<span data-ttu-id="6cf61-122">Functions kan dokumenteras med hjälp av [kommentarbaserad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenterade i en XML-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="6cf61-123">När funktionen dokumenteras i en XML-fil, funktionen måste ha en `.ExternalHelp` kommentera nyckelord som associerar funktionen med XML-filen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="6cf61-124">I annat fall den `Get-Help` cmdlet kan inte hitta hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="6cf61-125">Functions kan dokumenteras med hjälp av [kommentarbaserad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenterade i en XML-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="6cf61-126">När funktionen dokumenteras i en XML-fil, funktionen måste ha en `.ExternalHelp` kommentera nyckelord som associerar funktionen med XML-filen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="6cf61-127">I annat fall den `Get-Help` cmdlet kan inte hitta hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="6cf61-128">Det finns inga tekniska krav för namnet för en funktion hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="6cf61-129">Ett bra tips är dock att namnge i hjälpfilen för modulen skriptet där funktionen har definierats.</span><span class="sxs-lookup"><span data-stu-id="6cf61-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="6cf61-130">Till exempel har följande funktion definierats i filen Minmodul.psm1.</span><span class="sxs-lookup"><span data-stu-id="6cf61-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="6cf61-131">CIM-kommandot hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="6cf61-131">CIM Command Help Files</span></span>

<span data-ttu-id="6cf61-132">I hjälpfilen för en CIM-kommandot måste ha namnet för filen CDXLM som CIM-kommandot har definierats.</span><span class="sxs-lookup"><span data-stu-id="6cf61-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="6cf61-133">Använd formatet följande namn:</span><span class="sxs-lookup"><span data-stu-id="6cf61-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="6cf61-134">CIM-kommandon har definierats i CDXLM-filer som kan tas med i moduler som kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="6cf61-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="6cf61-135">När kommandot CIM har importerats till sessionen som en funktion, Windows PowerShell lägger till en `.ExternalHelp` kommentar nyckelord till funktionsdefinitionen som associerar funktionen med hjälp ett XML-fil som heter för CDXLM-filen som CIM-kommandot har definierats.</span><span class="sxs-lookup"><span data-stu-id="6cf61-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="6cf61-136">Skript-arbetsflöde hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="6cf61-136">Script Workflow Help Files</span></span>

<span data-ttu-id="6cf61-137">Arbetsflöden för skript som ingår i moduler kan dokumenteras i XML-baserade hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="6cf61-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="6cf61-138">Det finns inga tekniska krav för namn på hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="6cf61-139">Ett bra tips är dock att namnge i hjälpfilen för modulen skript som skriptarbetsflödet definieras.</span><span class="sxs-lookup"><span data-stu-id="6cf61-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="6cf61-140">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="6cf61-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="6cf61-141">Till skillnad från andra skriptkommandon skriptarbetsflöden kräver inte en `.ExternalHelp` kommentera nyckelord för att associera dem med en hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="6cf61-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="6cf61-142">I stället Windows PowerShell söker UI-kultur-specifika underkataloger i modulkatalogen för XML-baserade hjälpfiler och söker efter hjälp för skriptarbetsflödet i alla filer.</span><span class="sxs-lookup"><span data-stu-id="6cf61-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="6cf61-143">`.ExternalHelp` kommentera nyckelordet ignoreras.</span><span class="sxs-lookup"><span data-stu-id="6cf61-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="6cf61-144">Eftersom den `.ExternalHelp` kommentar nyckelordet ignoreras den `Get-Help` cmdlet kan få hjälp med att skriptarbetsflöden endast när de ingår i moduler.</span><span class="sxs-lookup"><span data-stu-id="6cf61-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>