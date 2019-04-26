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
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082189"
---
# <a name="naming-help-files"></a><span data-ttu-id="c5588-102">Namnge hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c5588-102">Naming Help Files</span></span>

<span data-ttu-id="c5588-103">Det här avsnittet beskriver hur du namnger en XML-baserade hjälpfil så att den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet kan hitta den.</span><span class="sxs-lookup"><span data-stu-id="c5588-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="c5588-104">Krav för namnet skiljer sig åt för varje kommando.</span><span class="sxs-lookup"><span data-stu-id="c5588-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="c5588-105">Cmdlet-hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c5588-105">Cmdlet Help Files</span></span>

<span data-ttu-id="c5588-106">I hjälpfilen en C# cmdlet måste ha namnet för sammansättningen där cmdleten har definierats.</span><span class="sxs-lookup"><span data-stu-id="c5588-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="c5588-107">Använd formatet följande namn:</span><span class="sxs-lookup"><span data-stu-id="c5588-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="c5588-108">Sammansättningen namnformat krävs även när sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="c5588-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="c5588-109">Till exempel den [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet har definierats i sammansättningen Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="c5588-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="c5588-110">Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för de `Get-WinEvent` cmdlet endast i filen Microsoft.PowerShell.Diagnostics.dll help.xml i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="c5588-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="c5588-111">Providern hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c5588-111">Provider Help files</span></span>

<span data-ttu-id="c5588-112">I hjälpfilen för en Windows PowerShell-provider måste ha namnet för sammansättningen som providern definieras.</span><span class="sxs-lookup"><span data-stu-id="c5588-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="c5588-113">Använd formatet följande namn:</span><span class="sxs-lookup"><span data-stu-id="c5588-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="c5588-114">Sammansättningen namnformat krävs även när sammansättningen är en kapslad modul.</span><span class="sxs-lookup"><span data-stu-id="c5588-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="c5588-115">Till exempel har certifikatleverantör definierats i sammansättningen Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="c5588-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="c5588-116">Den `Get-Help` cmdleten söker efter ett hjälpavsnitt för certifikatleverantör endast i filen Microsoft.PowerShell.Security.dll help.xml i modulkatalogen.</span><span class="sxs-lookup"><span data-stu-id="c5588-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="c5588-117">Funktionen hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c5588-117">Function Help Files</span></span>

<span data-ttu-id="c5588-118">Functions kan dokumenteras med hjälp av [kommentarbaserad hjälp](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) eller dokumenterade i en XML-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="c5588-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="c5588-119">När funktionen dokumenteras i en XML-fil, funktionen måste ha en `.ExternalHelp` kommentera nyckelord som associerar funktionen med XML-filen.</span><span class="sxs-lookup"><span data-stu-id="c5588-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="c5588-120">I annat fall den `Get-Help` cmdlet kan inte hitta hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="c5588-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="c5588-121">Det finns inga tekniska krav för namnet för en funktion hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="c5588-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="c5588-122">Ett bra tips är dock att namnge i hjälpfilen för modulen skriptet där funktionen har definierats.</span><span class="sxs-lookup"><span data-stu-id="c5588-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="c5588-123">Till exempel har följande funktion definierats i filen Minmodul.psm1.</span><span class="sxs-lookup"><span data-stu-id="c5588-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="c5588-124">CIM-kommandot hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c5588-124">CIM Command Help Files</span></span>

<span data-ttu-id="c5588-125">I hjälpfilen för en CIM-kommandot måste ha namnet för filen CDXLM som CIM-kommandot har definierats.</span><span class="sxs-lookup"><span data-stu-id="c5588-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="c5588-126">Använd formatet följande namn:</span><span class="sxs-lookup"><span data-stu-id="c5588-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="c5588-127">CIM-kommandon har definierats i CDXLM-filer som kan tas med i moduler som kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="c5588-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="c5588-128">När kommandot CIM har importerats till sessionen som en funktion, Windows PowerShell lägger till en `.ExternalHelp` kommentar nyckelord till funktionsdefinitionen som associerar funktionen med hjälp ett XML-fil som heter för CDXLM-filen som CIM-kommandot har definierats.</span><span class="sxs-lookup"><span data-stu-id="c5588-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="c5588-129">Skript-arbetsflöde hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c5588-129">Script Workflow Help Files</span></span>

<span data-ttu-id="c5588-130">Arbetsflöden för skript som ingår i moduler kan dokumenteras i XML-baserade hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="c5588-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="c5588-131">Det finns inga tekniska krav för namn på hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="c5588-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="c5588-132">Ett bra tips är dock att namnge i hjälpfilen för modulen skript som skriptarbetsflödet definieras.</span><span class="sxs-lookup"><span data-stu-id="c5588-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="c5588-133">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="c5588-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="c5588-134">Till skillnad från andra skriptkommandon skriptarbetsflöden kräver inte en `.ExternalHelp` kommentera nyckelord för att associera dem med en hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="c5588-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="c5588-135">I stället Windows PowerShell söker UI-kultur-specifika underkataloger i modulkatalogen för XML-baserade hjälpfiler och söker efter hjälp för skriptarbetsflödet i alla filer.</span><span class="sxs-lookup"><span data-stu-id="c5588-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="c5588-136">`.ExternalHelp` kommentera nyckelordet ignoreras.</span><span class="sxs-lookup"><span data-stu-id="c5588-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="c5588-137">Eftersom den `.ExternalHelp` kommentar nyckelordet ignoreras den `Get-Help` cmdlet kan få hjälp med att skriptarbetsflöden endast när de ingår i moduler.</span><span class="sxs-lookup"><span data-stu-id="c5588-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>