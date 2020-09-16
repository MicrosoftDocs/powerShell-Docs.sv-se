---
title: Nyckelord för kommentarsbaserad hjälp
ms.date: 06/09/2020
ms.openlocfilehash: fb737c19d7b7f4d003af3ba36bb396bac52d94e7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893160"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="b45b3-102">Nyckelord för kommentarsbaserad hjälp</span><span class="sxs-lookup"><span data-stu-id="b45b3-102">Comment-Based Help Keywords</span></span>

<span data-ttu-id="b45b3-103">Det här avsnittet innehåller information om nyckelorden i kommenterad hjälp.</span><span class="sxs-lookup"><span data-stu-id="b45b3-103">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="b45b3-104">Nyckelord i kommenterings-baserad hjälp</span><span class="sxs-lookup"><span data-stu-id="b45b3-104">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="b45b3-105">Följande är giltiga kommentarer baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="b45b3-105">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="b45b3-106">De visas i den ordning som de normalt visas i ett hjälp avsnitt, tillsammans med deras avsedda användning.</span><span class="sxs-lookup"><span data-stu-id="b45b3-106">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="b45b3-107">Dessa nyckelord kan visas i vilken ordning som helst i den kommenterade hjälpen, och de är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="b45b3-107">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="b45b3-108">Observera att `.EXTERNALHELP` nyckelordet har företräde framför alla andra kommenterings-baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="b45b3-108">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="b45b3-109">När `.EXTERNALHELP` finns, visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-109">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b45b3-110">. Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="b45b3-110">.SYNOPSIS</span></span>

<span data-ttu-id="b45b3-111">En kort beskrivning av funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-111">A brief description of the function or script.</span></span> <span data-ttu-id="b45b3-112">Det här nyckelordet kan bara användas en gång i varje ämne.</span><span class="sxs-lookup"><span data-stu-id="b45b3-112">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="b45b3-113">. BETECKNING</span><span class="sxs-lookup"><span data-stu-id="b45b3-113">.DESCRIPTION</span></span>

<span data-ttu-id="b45b3-114">En detaljerad beskrivning av funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-114">A detailed description of the function or script.</span></span> <span data-ttu-id="b45b3-115">Det här nyckelordet kan bara användas en gång i varje ämne.</span><span class="sxs-lookup"><span data-stu-id="b45b3-115">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="b45b3-116">. PROFILESERVICEAPPLICATIONPROXY \<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="b45b3-116">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="b45b3-117">Beskrivningen av en parameter.</span><span class="sxs-lookup"><span data-stu-id="b45b3-117">The description of a parameter.</span></span> <span data-ttu-id="b45b3-118">Du kan inkludera ett `.PARAMETER` nyckelord för varje parameter i funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-118">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="b45b3-119">`.PARAMETER`Nyckelorden kan visas i vilken ordning som helst i kommentars blocket, men i vilken ordning parametrarna visas i `Param` instruktions-eller funktions deklarationen fastställs i vilken ordning parametrarna visas i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-119">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="b45b3-120">Ändra ordningen på parametrarna i `Param` instruktions-eller funktions deklarationen om du vill ändra ordningen på parametrarna i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-120">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="b45b3-121">Du kan också ange en parameter beskrivning genom att placera en kommentar i `Param` instruktionen omedelbart före parameterns variabel namn.</span><span class="sxs-lookup"><span data-stu-id="b45b3-121">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="b45b3-122">Om du använder både en `Param` instruktions kommentar och ett `.PARAMETER` nyckelord, används beskrivningen som är associerad med `.PARAMETER` nyckelordet och `Param` instruktions kommentaren ignoreras.</span><span class="sxs-lookup"><span data-stu-id="b45b3-122">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="b45b3-123">. EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b45b3-123">.EXAMPLE</span></span>

<span data-ttu-id="b45b3-124">Ett exempel kommando som använder funktionen eller skriptet, eventuellt följt av exempel på utdata och en beskrivning.</span><span class="sxs-lookup"><span data-stu-id="b45b3-124">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="b45b3-125">Upprepa det här nyckelordet för varje exempel.</span><span class="sxs-lookup"><span data-stu-id="b45b3-125">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="b45b3-126">. TILLFÖR</span><span class="sxs-lookup"><span data-stu-id="b45b3-126">.INPUTS</span></span>

<span data-ttu-id="b45b3-127">De Microsoft .NET Ramverks typerna av objekt som kan skickas till funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-127">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="b45b3-128">Du kan också inkludera en beskrivning av inobjekten.</span><span class="sxs-lookup"><span data-stu-id="b45b3-128">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="b45b3-129">. UTDATA</span><span class="sxs-lookup"><span data-stu-id="b45b3-129">.OUTPUTS</span></span>

<span data-ttu-id="b45b3-130">Den .NET Framework typ av objekt som cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="b45b3-130">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="b45b3-131">Du kan också inkludera en beskrivning av de returnerade objekten.</span><span class="sxs-lookup"><span data-stu-id="b45b3-131">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="b45b3-132">. NOTER</span><span class="sxs-lookup"><span data-stu-id="b45b3-132">.NOTES</span></span>

<span data-ttu-id="b45b3-133">Ytterligare information om funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-133">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="b45b3-134">. OPERATIONSFÖLJDSLÄNKKOD</span><span class="sxs-lookup"><span data-stu-id="b45b3-134">.LINK</span></span>

<span data-ttu-id="b45b3-135">Namnet på ett relaterat ämne.</span><span class="sxs-lookup"><span data-stu-id="b45b3-135">The name of a related topic.</span></span> <span data-ttu-id="b45b3-136">Upprepa det här nyckelordet för varje relaterat ämne.</span><span class="sxs-lookup"><span data-stu-id="b45b3-136">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="b45b3-137">Det här innehållet visas i avsnittet relaterade länkar i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-137">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="b45b3-138">`.LINK`Nyckelords innehållet kan också innehålla en Uniform Resource Identifier (URI) till en online-version av samma hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="b45b3-138">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="b45b3-139">Online-versionen öppnas när du använder- `Online` parametern för `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b45b3-139">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="b45b3-140">URI: n måste börja med http eller https.</span><span class="sxs-lookup"><span data-stu-id="b45b3-140">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="b45b3-141">. KOMPONENTFILERNA</span><span class="sxs-lookup"><span data-stu-id="b45b3-141">.COMPONENT</span></span>

<span data-ttu-id="b45b3-142">Namnet på tekniken eller funktionen som funktionen eller skriptet använder, eller som den är relaterad till.</span><span class="sxs-lookup"><span data-stu-id="b45b3-142">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="b45b3-143">**Komponent** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b45b3-143">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="b45b3-144">. Rollinnehavaren</span><span class="sxs-lookup"><span data-stu-id="b45b3-144">.Role</span></span>

<span data-ttu-id="b45b3-145">Namnet på användar rollen för hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-145">The name of the user role for the help topic.</span></span> <span data-ttu-id="b45b3-146">**Roll** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b45b3-146">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="b45b3-147">. FUNKTIONS</span><span class="sxs-lookup"><span data-stu-id="b45b3-147">.FUNCTIONALITY</span></span>

<span data-ttu-id="b45b3-148">Nyckelord som beskriver den avsedda användningen av funktionen.</span><span class="sxs-lookup"><span data-stu-id="b45b3-148">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="b45b3-149">**Funktions** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b45b3-149">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="b45b3-150">. FORWARDHELPTARGETNAME \<Command-Name></span><span class="sxs-lookup"><span data-stu-id="b45b3-150">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="b45b3-151">Omdirigerar till hjälp avsnittet för det angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="b45b3-151">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="b45b3-152">Du kan omdirigera användare till valfritt hjälp avsnitt, inklusive hjälp avsnitt för en funktion, ett skript, en cmdlet eller en provider.</span><span class="sxs-lookup"><span data-stu-id="b45b3-152">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="b45b3-153">. FORWARDHELPCATEGORY \<Category></span><span class="sxs-lookup"><span data-stu-id="b45b3-153">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="b45b3-154">Anger hjälp kategorin för objektet i `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="b45b3-154">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="b45b3-155">Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.</span><span class="sxs-lookup"><span data-stu-id="b45b3-155">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="b45b3-156">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="b45b3-156">Valid values are:</span></span>

- <span data-ttu-id="b45b3-157">Alias</span><span class="sxs-lookup"><span data-stu-id="b45b3-157">Alias</span></span>
- <span data-ttu-id="b45b3-158">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b45b3-158">Cmdlet</span></span>
- <span data-ttu-id="b45b3-159">Hjälpfil</span><span class="sxs-lookup"><span data-stu-id="b45b3-159">HelpFile</span></span>
- <span data-ttu-id="b45b3-160">Funktion</span><span class="sxs-lookup"><span data-stu-id="b45b3-160">Function</span></span>
- <span data-ttu-id="b45b3-161">Leverantör</span><span class="sxs-lookup"><span data-stu-id="b45b3-161">Provider</span></span>
- <span data-ttu-id="b45b3-162">Allmänt</span><span class="sxs-lookup"><span data-stu-id="b45b3-162">General</span></span>
- <span data-ttu-id="b45b3-163">Vanliga frågor</span><span class="sxs-lookup"><span data-stu-id="b45b3-163">FAQ</span></span>
- <span data-ttu-id="b45b3-164">Ordlista</span><span class="sxs-lookup"><span data-stu-id="b45b3-164">Glossary</span></span>
- <span data-ttu-id="b45b3-165">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="b45b3-165">ScriptCommand</span></span>
- <span data-ttu-id="b45b3-166">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="b45b3-166">ExternalScript</span></span>
- <span data-ttu-id="b45b3-167">Filtrera</span><span class="sxs-lookup"><span data-stu-id="b45b3-167">Filter</span></span>
- <span data-ttu-id="b45b3-168">Alla</span><span class="sxs-lookup"><span data-stu-id="b45b3-168">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="b45b3-169">. REMOTEHELPRUNSPACE \<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="b45b3-169">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="b45b3-170">Anger en session som innehåller hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-170">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="b45b3-171">Ange en variabel som innehåller en PSSession.</span><span class="sxs-lookup"><span data-stu-id="b45b3-171">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="b45b3-172">Det här nyckelordet används av `Export-PSSession` cmdleten för att hitta hjälp avsnitten för de exporterade kommandona.</span><span class="sxs-lookup"><span data-stu-id="b45b3-172">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="b45b3-173">. EXTERNALHELP \<XML Help File></span><span class="sxs-lookup"><span data-stu-id="b45b3-173">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="b45b3-174">Anger sökvägen och/eller namnet på en XML-baserad hjälpfil för skriptet eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="b45b3-174">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="b45b3-175">`.EXTERNALHELP`Nyckelordet instruerar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) för att få hjälp med skriptet eller funktionen i en XML-baserad fil.</span><span class="sxs-lookup"><span data-stu-id="b45b3-175">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="b45b3-176">`.EXTERNALHELP`Nyckelordet krävs när du använder en XML-baserad hjälp fil för ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="b45b3-176">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="b45b3-177">Utan det `Get-Help` kommer inte att hitta någon hjälp fil för funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-177">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="b45b3-178">`.EXTERNALHELP`Nyckelordet har företräde framför alla andra kommenterings-baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="b45b3-178">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="b45b3-179">När `.EXTERNALHELP` finns, visar cmdleten [Microsoft. PowerShell. commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) inte någon kommenterad hjälp, även om det inte går att hitta en hjälp fil som matchar värdet för nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-179">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="b45b3-180">När funktionen exporteras av en-skript-modul `.EXTERNALHELP` ska värdet vara ett fil namn utan sökväg.</span><span class="sxs-lookup"><span data-stu-id="b45b3-180">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="b45b3-181">`Get-Help` söker efter filen i en språkspecifik under katalog i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="b45b3-181">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="b45b3-182">Det finns inga krav på fil namnet, men det är en bra idé att använda följande fil namns format: `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="b45b3-182">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="b45b3-183">Om funktionen inte är associerad med en modul inkluderar du en sökväg och ett fil namn i värdet för `.EXTERNALHELP` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="b45b3-183">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="b45b3-184">Om den angivna sökvägen till XML-filen innehåller UI-kultur-specifika under kataloger, `Get-Help` söker igenom under katalogerna rekursivt efter en XML-fil med namnet på skriptet eller funktionen i enlighet med de språk reserv standarder som är etablerade för Windows, precis som för alla XML-baserade hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="b45b3-184">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="b45b3-185">Mer information om cmdlet Help XML-baserade hjälp fils format finns i [skriva Windows PowerShell-cmdlet-hjälpen](./writing-help-for-windows-powershell-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="b45b3-185">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
