---
title: Namngivnings hjälp filer | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: d13324871bac7ba21c0e042e8674c5996e5dba85
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810815"
---
# <a name="naming-help-files"></a><span data-ttu-id="ac868-102">Namnge hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="ac868-102">Naming Help Files</span></span>

<span data-ttu-id="ac868-103">I det här avsnittet beskrivs hur du namnger en XML-baserad hjälpfil så att cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) kan hitta den.</span><span class="sxs-lookup"><span data-stu-id="ac868-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="ac868-104">Namn kraven varierar för varje kommando typ.</span><span class="sxs-lookup"><span data-stu-id="ac868-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="ac868-105">Cmdlet-hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="ac868-105">Cmdlet Help Files</span></span>

<span data-ttu-id="ac868-106">Hjälp filen för en C#-cmdlet måste namnges för sammansättningen där cmdleten definieras.</span><span class="sxs-lookup"><span data-stu-id="ac868-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="ac868-107">Använd följande fil namns format:</span><span class="sxs-lookup"><span data-stu-id="ac868-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ac868-108">Sammansättnings namnets format måste anges även om sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="ac868-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ac868-109">Till exempel [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdleten definieras i sammansättningen Microsoft. PowerShell. Diagnostics. dll.</span><span class="sxs-lookup"><span data-stu-id="ac868-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="ac868-110">`Get-Help`Cmdleten söker efter ett hjälp avsnitt för `Get-WinEvent` cmdleten endast i filen Microsoft. PowerShell. Diagnostics. dll-Help. xml i modul-katalogen.</span><span class="sxs-lookup"><span data-stu-id="ac868-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="ac868-111">Hjälp filer för Provider</span><span class="sxs-lookup"><span data-stu-id="ac868-111">Provider Help files</span></span>

<span data-ttu-id="ac868-112">Hjälp filen för en Windows PowerShell-Provider måste namnges för sammansättningen där providern definieras.</span><span class="sxs-lookup"><span data-stu-id="ac868-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="ac868-113">Använd följande fil namns format:</span><span class="sxs-lookup"><span data-stu-id="ac868-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ac868-114">Sammansättnings namnets format måste anges även om sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="ac868-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ac868-115">Till exempel definieras certifikat leverantören i sammansättningen Microsoft. PowerShell. Security. dll.</span><span class="sxs-lookup"><span data-stu-id="ac868-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="ac868-116">`Get-Help`Cmdleten söker bara efter ett hjälp avsnitt för certifikat leverantören i filen Microsoft. PowerShell. Security. dll-Help. xml i modul-katalogen.</span><span class="sxs-lookup"><span data-stu-id="ac868-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="ac868-117">Funktions hjälp filer</span><span class="sxs-lookup"><span data-stu-id="ac868-117">Function Help Files</span></span>

<span data-ttu-id="ac868-118">Funktioner kan dokumenteras med hjälp av en [kommenterad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenteras i en XML-hjälpfil.</span><span class="sxs-lookup"><span data-stu-id="ac868-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="ac868-119">När funktionen dokumenteras i en XML-fil måste funktionen ha ett `.ExternalHelp` kommentar nyckelord som associerar funktionen med XML-filen.</span><span class="sxs-lookup"><span data-stu-id="ac868-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="ac868-120">Annars `Get-Help` kan inte cmdlet: en hitta hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="ac868-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="ac868-121">Det finns inga tekniska krav för namnet på en funktions hjälp fil.</span><span class="sxs-lookup"><span data-stu-id="ac868-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="ac868-122">Vi rekommenderar dock att du namnger hjälp filen för den skript-modul där funktionen definieras.</span><span class="sxs-lookup"><span data-stu-id="ac868-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="ac868-123">Till exempel definieras följande funktion i filen psm1..</span><span class="sxs-lookup"><span data-stu-id="ac868-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="ac868-124">Hjälp filer för CIM-kommando</span><span class="sxs-lookup"><span data-stu-id="ac868-124">CIM Command Help Files</span></span>

<span data-ttu-id="ac868-125">Hjälp filen för ett CIM-kommando måste namnges för den CDXLM-fil där CIM-kommandot definieras.</span><span class="sxs-lookup"><span data-stu-id="ac868-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="ac868-126">Använd följande fil namns format:</span><span class="sxs-lookup"><span data-stu-id="ac868-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="ac868-127">CIM-kommandon definieras i CDXLM-filer som kan inkluderas i moduler som kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="ac868-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="ac868-128">När CIM-kommandot importeras till sessionen som en funktion lägger Windows PowerShell `.ExternalHelp` till ett kommentar nyckelord till funktions definitionen som associerar funktionen med en XML-hjälpfil som heter för cdxlm-filen där CIM-kommandot definieras.</span><span class="sxs-lookup"><span data-stu-id="ac868-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="ac868-129">Hjälpfiler för skript arbets flöde</span><span class="sxs-lookup"><span data-stu-id="ac868-129">Script Workflow Help Files</span></span>

<span data-ttu-id="ac868-130">Skript arbets flöden som ingår i moduler kan dokumenteras i XML-baserade hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="ac868-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="ac868-131">Det finns inga tekniska krav för namnet på hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="ac868-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="ac868-132">Vi rekommenderar dock att du namnger hjälp filen för den skript-modul där skript arbets flödet har definierats.</span><span class="sxs-lookup"><span data-stu-id="ac868-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="ac868-133">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ac868-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="ac868-134">Till skillnad från andra skriptbaserade kommandon behöver inte skript arbets flöden ett `.ExternalHelp` kommentars nyckelord för att koppla dem till en hjälp fil.</span><span class="sxs-lookup"><span data-stu-id="ac868-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="ac868-135">I stället söker Windows PowerShell efter den UI-kulturbaserade under kataloger i modul katalogen för XML-baserade hjälpfiler och söker efter hjälp för skript arbets flödet i alla filer.</span><span class="sxs-lookup"><span data-stu-id="ac868-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="ac868-136">`.ExternalHelp`nyckelordet comment ignoreras.</span><span class="sxs-lookup"><span data-stu-id="ac868-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="ac868-137">Eftersom `.ExternalHelp` nyckelordet comment ignoreras, `Get-Help` kan cmdleten bara hitta hjälp för skript arbets flöden när de ingår i moduler.</span><span class="sxs-lookup"><span data-stu-id="ac868-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
