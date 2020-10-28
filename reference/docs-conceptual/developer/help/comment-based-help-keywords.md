---
ms.date: 06/09/2020
ms.topic: reference
title: Nyckelord för kommentarsbaserad hjälp
description: Nyckelord för kommentarsbaserad hjälp
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645472"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="282e8-103">Nyckelord för kommentarsbaserad hjälp</span><span class="sxs-lookup"><span data-stu-id="282e8-103">Comment-Based Help Keywords</span></span>

<span data-ttu-id="282e8-104">Det här avsnittet innehåller information om nyckelorden i kommenterad hjälp.</span><span class="sxs-lookup"><span data-stu-id="282e8-104">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="282e8-105">Nyckelord i Comment-Based hjälp</span><span class="sxs-lookup"><span data-stu-id="282e8-105">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="282e8-106">Följande är giltiga kommentarer baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="282e8-106">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="282e8-107">De visas i den ordning som de normalt visas i ett hjälp avsnitt, tillsammans med deras avsedda användning.</span><span class="sxs-lookup"><span data-stu-id="282e8-107">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="282e8-108">Dessa nyckelord kan visas i vilken ordning som helst i den kommenterade hjälpen, och de är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="282e8-108">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="282e8-109">Observera att `.EXTERNALHELP` nyckelordet har företräde framför alla andra kommenterings-baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="282e8-109">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="282e8-110">När `.EXTERNALHELP` finns, visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="282e8-110">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="282e8-111">. Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="282e8-111">.SYNOPSIS</span></span>

<span data-ttu-id="282e8-112">En kort beskrivning av funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="282e8-112">A brief description of the function or script.</span></span> <span data-ttu-id="282e8-113">Det här nyckelordet kan bara användas en gång i varje ämne.</span><span class="sxs-lookup"><span data-stu-id="282e8-113">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="282e8-114">. BETECKNING</span><span class="sxs-lookup"><span data-stu-id="282e8-114">.DESCRIPTION</span></span>

<span data-ttu-id="282e8-115">En detaljerad beskrivning av funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="282e8-115">A detailed description of the function or script.</span></span> <span data-ttu-id="282e8-116">Det här nyckelordet kan bara användas en gång i varje ämne.</span><span class="sxs-lookup"><span data-stu-id="282e8-116">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="282e8-117">. PROFILESERVICEAPPLICATIONPROXY \<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="282e8-117">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="282e8-118">Beskrivningen av en parameter.</span><span class="sxs-lookup"><span data-stu-id="282e8-118">The description of a parameter.</span></span> <span data-ttu-id="282e8-119">Du kan inkludera ett `.PARAMETER` nyckelord för varje parameter i funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="282e8-119">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="282e8-120">`.PARAMETER`Nyckelorden kan visas i vilken ordning som helst i kommentars blocket, men i vilken ordning parametrarna visas i `Param` instruktions-eller funktions deklarationen fastställs i vilken ordning parametrarna visas i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="282e8-120">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="282e8-121">Ändra ordningen på parametrarna i `Param` instruktions-eller funktions deklarationen om du vill ändra ordningen på parametrarna i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="282e8-121">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="282e8-122">Du kan också ange en parameter beskrivning genom att placera en kommentar i `Param` instruktionen omedelbart före parameterns variabel namn.</span><span class="sxs-lookup"><span data-stu-id="282e8-122">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="282e8-123">Om du använder både en `Param` instruktions kommentar och ett `.PARAMETER` nyckelord, används beskrivningen som är associerad med `.PARAMETER` nyckelordet och `Param` instruktions kommentaren ignoreras.</span><span class="sxs-lookup"><span data-stu-id="282e8-123">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="282e8-124">. EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="282e8-124">.EXAMPLE</span></span>

<span data-ttu-id="282e8-125">Ett exempel kommando som använder funktionen eller skriptet, eventuellt följt av exempel på utdata och en beskrivning.</span><span class="sxs-lookup"><span data-stu-id="282e8-125">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="282e8-126">Upprepa det här nyckelordet för varje exempel.</span><span class="sxs-lookup"><span data-stu-id="282e8-126">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="282e8-127">. TILLFÖR</span><span class="sxs-lookup"><span data-stu-id="282e8-127">.INPUTS</span></span>

<span data-ttu-id="282e8-128">De Microsoft .NET Ramverks typerna av objekt som kan skickas till funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="282e8-128">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="282e8-129">Du kan också inkludera en beskrivning av inobjekten.</span><span class="sxs-lookup"><span data-stu-id="282e8-129">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="282e8-130">. UTDATA</span><span class="sxs-lookup"><span data-stu-id="282e8-130">.OUTPUTS</span></span>

<span data-ttu-id="282e8-131">Den .NET Framework typ av objekt som cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="282e8-131">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="282e8-132">Du kan också inkludera en beskrivning av de returnerade objekten.</span><span class="sxs-lookup"><span data-stu-id="282e8-132">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="282e8-133">. NOTER</span><span class="sxs-lookup"><span data-stu-id="282e8-133">.NOTES</span></span>

<span data-ttu-id="282e8-134">Ytterligare information om funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="282e8-134">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="282e8-135">. OPERATIONSFÖLJDSLÄNKKOD</span><span class="sxs-lookup"><span data-stu-id="282e8-135">.LINK</span></span>

<span data-ttu-id="282e8-136">Namnet på ett relaterat ämne.</span><span class="sxs-lookup"><span data-stu-id="282e8-136">The name of a related topic.</span></span> <span data-ttu-id="282e8-137">Upprepa det här nyckelordet för varje relaterat ämne.</span><span class="sxs-lookup"><span data-stu-id="282e8-137">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="282e8-138">Det här innehållet visas i avsnittet relaterade länkar i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="282e8-138">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="282e8-139">`.LINK`Nyckelords innehållet kan också innehålla en Uniform Resource Identifier (URI) till en online-version av samma hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="282e8-139">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="282e8-140">Online-versionen öppnas när du använder- `Online` parametern för `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="282e8-140">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="282e8-141">URI: n måste börja med http eller https.</span><span class="sxs-lookup"><span data-stu-id="282e8-141">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="282e8-142">. KOMPONENTFILERNA</span><span class="sxs-lookup"><span data-stu-id="282e8-142">.COMPONENT</span></span>

<span data-ttu-id="282e8-143">Namnet på tekniken eller funktionen som funktionen eller skriptet använder, eller som den är relaterad till.</span><span class="sxs-lookup"><span data-stu-id="282e8-143">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="282e8-144">**Komponent** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="282e8-144">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="282e8-145">. Rollinnehavaren</span><span class="sxs-lookup"><span data-stu-id="282e8-145">.Role</span></span>

<span data-ttu-id="282e8-146">Namnet på användar rollen för hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="282e8-146">The name of the user role for the help topic.</span></span> <span data-ttu-id="282e8-147">**Roll** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="282e8-147">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="282e8-148">. FUNKTIONS</span><span class="sxs-lookup"><span data-stu-id="282e8-148">.FUNCTIONALITY</span></span>

<span data-ttu-id="282e8-149">Nyckelord som beskriver den avsedda användningen av funktionen.</span><span class="sxs-lookup"><span data-stu-id="282e8-149">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="282e8-150">**Funktions** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="282e8-150">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="282e8-151">. FORWARDHELPTARGETNAME \<Command-Name></span><span class="sxs-lookup"><span data-stu-id="282e8-151">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="282e8-152">Omdirigerar till hjälp avsnittet för det angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="282e8-152">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="282e8-153">Du kan omdirigera användare till valfritt hjälp avsnitt, inklusive hjälp avsnitt för en funktion, ett skript, en cmdlet eller en provider.</span><span class="sxs-lookup"><span data-stu-id="282e8-153">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="282e8-154">. FORWARDHELPCATEGORY \<Category></span><span class="sxs-lookup"><span data-stu-id="282e8-154">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="282e8-155">Anger hjälp kategorin för objektet i `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="282e8-155">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="282e8-156">Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.</span><span class="sxs-lookup"><span data-stu-id="282e8-156">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="282e8-157">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="282e8-157">Valid values are:</span></span>

- <span data-ttu-id="282e8-158">Alias</span><span class="sxs-lookup"><span data-stu-id="282e8-158">Alias</span></span>
- <span data-ttu-id="282e8-159">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="282e8-159">Cmdlet</span></span>
- <span data-ttu-id="282e8-160">Hjälpfil</span><span class="sxs-lookup"><span data-stu-id="282e8-160">HelpFile</span></span>
- <span data-ttu-id="282e8-161">Funktion</span><span class="sxs-lookup"><span data-stu-id="282e8-161">Function</span></span>
- <span data-ttu-id="282e8-162">Leverantör</span><span class="sxs-lookup"><span data-stu-id="282e8-162">Provider</span></span>
- <span data-ttu-id="282e8-163">Allmänt</span><span class="sxs-lookup"><span data-stu-id="282e8-163">General</span></span>
- <span data-ttu-id="282e8-164">Vanliga frågor</span><span class="sxs-lookup"><span data-stu-id="282e8-164">FAQ</span></span>
- <span data-ttu-id="282e8-165">Ordlista</span><span class="sxs-lookup"><span data-stu-id="282e8-165">Glossary</span></span>
- <span data-ttu-id="282e8-166">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="282e8-166">ScriptCommand</span></span>
- <span data-ttu-id="282e8-167">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="282e8-167">ExternalScript</span></span>
- <span data-ttu-id="282e8-168">Filtrera</span><span class="sxs-lookup"><span data-stu-id="282e8-168">Filter</span></span>
- <span data-ttu-id="282e8-169">Alla</span><span class="sxs-lookup"><span data-stu-id="282e8-169">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="282e8-170">. REMOTEHELPRUNSPACE \<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="282e8-170">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="282e8-171">Anger en session som innehåller hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="282e8-171">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="282e8-172">Ange en variabel som innehåller en PSSession.</span><span class="sxs-lookup"><span data-stu-id="282e8-172">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="282e8-173">Det här nyckelordet används av `Export-PSSession` cmdleten för att hitta hjälp avsnitten för de exporterade kommandona.</span><span class="sxs-lookup"><span data-stu-id="282e8-173">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="282e8-174">. EXTERNALHELP \<XML Help File></span><span class="sxs-lookup"><span data-stu-id="282e8-174">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="282e8-175">Anger sökvägen och/eller namnet på en XML-baserad hjälpfil för skriptet eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="282e8-175">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="282e8-176">`.EXTERNALHELP`Nyckelordet instruerar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) för att få hjälp med skriptet eller funktionen i en XML-baserad fil.</span><span class="sxs-lookup"><span data-stu-id="282e8-176">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="282e8-177">`.EXTERNALHELP`Nyckelordet krävs när du använder en XML-baserad hjälp fil för ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="282e8-177">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="282e8-178">Utan det `Get-Help` kommer inte att hitta någon hjälp fil för funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="282e8-178">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="282e8-179">`.EXTERNALHELP`Nyckelordet har företräde framför alla andra kommenterings-baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="282e8-179">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="282e8-180">När `.EXTERNALHELP` finns, visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="282e8-180">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="282e8-181">När funktionen exporteras av en-skript-modul `.EXTERNALHELP` ska värdet vara ett fil namn utan sökväg.</span><span class="sxs-lookup"><span data-stu-id="282e8-181">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="282e8-182">`Get-Help` söker efter filen i en språkspecifik under katalog i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="282e8-182">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="282e8-183">Det finns inga krav på fil namnet, men det är en bra idé att använda följande fil namns format: `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="282e8-183">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="282e8-184">Om funktionen inte är associerad med en modul inkluderar du en sökväg och ett fil namn i värdet för `.EXTERNALHELP` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="282e8-184">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="282e8-185">Om den angivna sökvägen till XML-filen innehåller UI-kultur-specifika under kataloger, `Get-Help` söker igenom under katalogerna rekursivt efter en XML-fil med namnet på skriptet eller funktionen i enlighet med de språk reserv standarder som är etablerade för Windows, precis som för alla XML-baserade hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="282e8-185">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="282e8-186">Mer information om cmdlet Help XML-baserade hjälp fils format finns i [skriva Windows PowerShell-cmdlet-hjälpen](./writing-help-for-windows-powershell-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="282e8-186">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
