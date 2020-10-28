---
ms.date: 09/12/2016
ms.topic: reference
title: Namnge hjälpfiler
description: Namnge hjälpfiler
ms.openlocfilehash: b77af8f9b9510785a4198fed9da1263184a27b99
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667597"
---
# <a name="naming-help-files"></a><span data-ttu-id="ff68a-103">Namnge hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="ff68a-103">Naming Help Files</span></span>

<span data-ttu-id="ff68a-104">I det här avsnittet beskrivs hur du namnger en XML-baserad hjälpfil så att cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) kan hitta den.</span><span class="sxs-lookup"><span data-stu-id="ff68a-104">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="ff68a-105">Namn kraven varierar för varje kommando typ.</span><span class="sxs-lookup"><span data-stu-id="ff68a-105">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="ff68a-106">Cmdlet-hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="ff68a-106">Cmdlet Help Files</span></span>

<span data-ttu-id="ff68a-107">Hjälp filen för en C#-cmdlet måste namnges för sammansättningen där cmdleten definieras.</span><span class="sxs-lookup"><span data-stu-id="ff68a-107">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="ff68a-108">Använd följande fil namns format:</span><span class="sxs-lookup"><span data-stu-id="ff68a-108">Use the following filename format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ff68a-109">Sammansättnings namnets format måste anges även om sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="ff68a-109">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ff68a-110">Till exempel definieras cmdleten [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) i Microsoft.PowerShell.Diagnostics.dll sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-110">For example, the [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="ff68a-111">`Get-Help`Cmdleten söker efter ett hjälp avsnitt för `Get-WinEvent` cmdleten endast i `Microsoft.PowerShell.Diagnostics.dll-help.xml` filen i modul-katalogen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-111">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the `Microsoft.PowerShell.Diagnostics.dll-help.xml` file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="ff68a-112">Hjälp filer för Provider</span><span class="sxs-lookup"><span data-stu-id="ff68a-112">Provider Help files</span></span>

<span data-ttu-id="ff68a-113">Hjälp filen för en PowerShell-Provider måste namnges för sammansättningen där providern definieras.</span><span class="sxs-lookup"><span data-stu-id="ff68a-113">The help file for a PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="ff68a-114">Använd följande fil namns format:</span><span class="sxs-lookup"><span data-stu-id="ff68a-114">Use the following filename format:</span></span>

`<AssemblyName>.dll-help.xml`

<span data-ttu-id="ff68a-115">Sammansättnings namnets format måste anges även om sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="ff68a-115">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ff68a-116">Till exempel definieras certifikat leverantören i `Microsoft.PowerShell.Security.dll` sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-116">For example, the Certificate provider is defined in the `Microsoft.PowerShell.Security.dll` assembly.</span></span> <span data-ttu-id="ff68a-117">`Get-Help`Cmdleten söker efter ett hjälp avsnitt för certifikat leverantören enbart i `Microsoft.PowerShell.Security.dll-help.xml` filen i modul-katalogen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-117">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the `Microsoft.PowerShell.Security.dll-help.xml` file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="ff68a-118">Funktions hjälp filer</span><span class="sxs-lookup"><span data-stu-id="ff68a-118">Function Help Files</span></span>

<span data-ttu-id="ff68a-119">Funktioner kan dokumenteras med hjälp av en [kommenterad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenteras i en XML-hjälpfil.</span><span class="sxs-lookup"><span data-stu-id="ff68a-119">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="ff68a-120">När funktionen dokumenteras i en XML-fil måste funktionen ha ett `.ExternalHelp` kommentar nyckelord som associerar funktionen med XML-filen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-120">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="ff68a-121">Annars `Get-Help` kan inte cmdlet: en hitta hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-121">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="ff68a-122">Det finns inga tekniska krav för namnet på en funktions hjälp fil.</span><span class="sxs-lookup"><span data-stu-id="ff68a-122">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="ff68a-123">Vi rekommenderar dock att du namnger hjälp filen för den skript-modul där funktionen definieras.</span><span class="sxs-lookup"><span data-stu-id="ff68a-123">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="ff68a-124">Till exempel definieras följande funktion i `MyModule.psm1` filen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-124">For example, the following function is defined in the `MyModule.psm1` file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="ff68a-125">Hjälp filer för CIM-kommando</span><span class="sxs-lookup"><span data-stu-id="ff68a-125">CIM Command Help Files</span></span>

<span data-ttu-id="ff68a-126">Hjälp filen för ett CIM-kommando måste namnges för den CDXLM-fil där CIM-kommandot definieras.</span><span class="sxs-lookup"><span data-stu-id="ff68a-126">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="ff68a-127">Använd följande fil namns format:</span><span class="sxs-lookup"><span data-stu-id="ff68a-127">Use the following filename format:</span></span>

`<FileName>.cdxml-help.xml`

<span data-ttu-id="ff68a-128">CIM-kommandon definieras i CDXLM-filer som kan inkluderas i moduler som kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="ff68a-128">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="ff68a-129">När CIM-kommandot importeras till sessionen som en funktion lägger PowerShell `.ExternalHelp` till ett kommentar nyckelord till funktions definitionen som associerar funktionen med en XML-hjälpfil som heter för cdxlm-filen där CIM-kommandot definieras.</span><span class="sxs-lookup"><span data-stu-id="ff68a-129">When the CIM command is imported into the session as a function, PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="ff68a-130">Hjälpfiler för skript arbets flöde</span><span class="sxs-lookup"><span data-stu-id="ff68a-130">Script Workflow Help Files</span></span>

<span data-ttu-id="ff68a-131">Skript arbets flöden som ingår i moduler kan dokumenteras i XML-baserade hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="ff68a-131">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="ff68a-132">Det finns inga tekniska krav för namnet på hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="ff68a-132">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="ff68a-133">Vi rekommenderar dock att du namnger hjälp filen för den skript-modul där skript arbets flödet har definierats.</span><span class="sxs-lookup"><span data-stu-id="ff68a-133">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="ff68a-134">Exempel:</span><span class="sxs-lookup"><span data-stu-id="ff68a-134">For example:</span></span>

`<ScriptModule>.psm1-help.xml`

<span data-ttu-id="ff68a-135">Till skillnad från andra skriptbaserade kommandon behöver inte skript arbets flöden ett `.ExternalHelp` kommentars nyckelord för att koppla dem till en hjälp fil.</span><span class="sxs-lookup"><span data-stu-id="ff68a-135">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="ff68a-136">I stället söker PowerShell i den UI-kulturbaserade under kataloger i modul katalogen för XML-baserade hjälpfiler och söker efter hjälp för skript arbets flödet i alla filer.</span><span class="sxs-lookup"><span data-stu-id="ff68a-136">Instead, PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="ff68a-137">`.ExternalHelp` nyckelordet comment ignoreras.</span><span class="sxs-lookup"><span data-stu-id="ff68a-137">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="ff68a-138">Eftersom `.ExternalHelp` nyckelordet comment ignoreras, `Get-Help` kan cmdleten bara hitta hjälp för skript arbets flöden när de ingår i moduler.</span><span class="sxs-lookup"><span data-stu-id="ff68a-138">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
