---
description: Beskriver hur du skriver kommentarer baserade hjälp avsnitt för funktioner och skript.
keywords: powershell,cmdlet
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: eaf1ea3eaacf944e9489292ea46822d655f2068b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271622"
---
# <a name="about-comment-based-help"></a><span data-ttu-id="a5917-104">Om kommenterings-baserad hjälp</span><span class="sxs-lookup"><span data-stu-id="a5917-104">About Comment-based Help</span></span>

## <a name="short-description"></a><span data-ttu-id="a5917-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a5917-105">Short description</span></span>
<span data-ttu-id="a5917-106">Beskriver hur du skriver kommentarer baserade hjälp avsnitt för funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-106">Describes how to write comment-based help topics for functions and scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="a5917-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="a5917-107">Long description</span></span>

<span data-ttu-id="a5917-108">Du kan skriva kommentarer baserade hjälp avsnitt för funktioner och skript genom att använda särskilda nyckelord för hjälp kommentarer.</span><span class="sxs-lookup"><span data-stu-id="a5917-108">You can write comment-based help topics for functions and scripts by using special help comment keywords.</span></span>

<span data-ttu-id="a5917-109">Cmdleten [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) visar kommenterad hjälp i samma format som den visar cmdlet-hjälpen som genereras från XML-filer.</span><span class="sxs-lookup"><span data-stu-id="a5917-109">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) cmdlet displays comment-based help in the same format in which it displays the cmdlet help topics that are generated from XML files.</span></span> <span data-ttu-id="a5917-110">Användarna kan använda alla parametrar i `Get-Help` , till exempel **detaljerade** , **fullständiga** , **exempel** och **online** , för att visa innehållet i den kommenterade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="a5917-110">Users can use all of the parameters of `Get-Help`, such as **Detailed** , **Full** , **Examples** , and **Online** , to display the contents of comment-based help.</span></span>

<span data-ttu-id="a5917-111">Du kan också skriva XML-baserade hjälpfiler för funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-111">You can also write XML-based help files for functions and scripts.</span></span> <span data-ttu-id="a5917-112">Om du vill aktivera `Get-Help` cmdleten för att hitta den XML-baserade hjälp filen för en funktion eller ett skript, använder du `.ExternalHelp` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-112">To enable the `Get-Help` cmdlet to find the XML-based help file for a function or script, use the `.ExternalHelp` keyword.</span></span> <span data-ttu-id="a5917-113">Utan det här nyckelordet kan du `Get-Help` inte hitta XML-baserade hjälp avsnitt för funktioner eller skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-113">Without this keyword, `Get-Help` cannot find XML-based help topics for functions or scripts.</span></span>

<span data-ttu-id="a5917-114">I det här avsnittet beskrivs hur du skriver hjälp ämnen för funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-114">This topic explains how to write help topics for functions and scripts.</span></span> <span data-ttu-id="a5917-115">Information om hur du visar hjälp avsnitt för funktioner och skript finns i [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).</span><span class="sxs-lookup"><span data-stu-id="a5917-115">For information about how to display help topics for functions and scripts, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).</span></span>

<span data-ttu-id="a5917-116">Cmdletarna [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) och [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) fungerar bara på XML-filer.</span><span class="sxs-lookup"><span data-stu-id="a5917-116">The [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) and [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) cmdlets work only on XML files.</span></span> <span data-ttu-id="a5917-117">Uppdaterings bara hjälp har inte stöd för kommentarer baserade hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="a5917-117">Updatable Help does not support comment-based help topics.</span></span>

## <a name="syntax-for-comment-based-help"></a><span data-ttu-id="a5917-118">Syntax för kommenterings-baserad hjälp</span><span class="sxs-lookup"><span data-stu-id="a5917-118">Syntax for comment-based help</span></span>

<span data-ttu-id="a5917-119">Syntaxen för kommenterings-baserad hjälp är följande:</span><span class="sxs-lookup"><span data-stu-id="a5917-119">The syntax for comment-based help is as follows:</span></span>

```
# .<help keyword>
# <help content>
```

<span data-ttu-id="a5917-120">eller</span><span class="sxs-lookup"><span data-stu-id="a5917-120">or</span></span>

```
<#
.<help keyword>
<help content>
#>
```

<span data-ttu-id="a5917-121">Kommenterad hjälp skrivs som en rad kommentarer.</span><span class="sxs-lookup"><span data-stu-id="a5917-121">Comment-based help is written as a series of comments.</span></span> <span data-ttu-id="a5917-122">Du kan skriva en kommentars symbol `#` före varje rad med kommentarer, eller så kan du använda- `<#` och- `#>` symbolerna för att skapa ett kommentar block.</span><span class="sxs-lookup"><span data-stu-id="a5917-122">You can type a comment symbol `#` before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="a5917-123">Alla rader i kommentars blocket tolkas som kommentarer.</span><span class="sxs-lookup"><span data-stu-id="a5917-123">All the lines within the comment block are interpreted as comments.</span></span>

<span data-ttu-id="a5917-124">Alla rader i ett kommenterat hjälp avsnitt måste vara sammanhängande.</span><span class="sxs-lookup"><span data-stu-id="a5917-124">All of the lines in a comment-based help topic must be contiguous.</span></span> <span data-ttu-id="a5917-125">Om ett kommenterat hjälp avsnitt följer en kommentar som inte är en del av hjälp avsnittet, måste det finnas minst en tom rad mellan den sista raden för icke-hjälp-kommentarer och början av den kommenterade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="a5917-125">If a comment-based help topic follows a comment that is not part of the help topic, there must be at least one blank line between the last non-help comment line and the beginning of the comment-based help.</span></span>

<span data-ttu-id="a5917-126">Nyckelord definierar varje avsnitt i en kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="a5917-126">Keywords define each section of comment-based help.</span></span> <span data-ttu-id="a5917-127">Varje comment-baserat hjälp nyckelord föregås av en punkt `.` .</span><span class="sxs-lookup"><span data-stu-id="a5917-127">Each comment-based help keyword is preceded by a dot `.`.</span></span> <span data-ttu-id="a5917-128">Nyckelorden kan visas i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="a5917-128">The keywords can appear in any order.</span></span> <span data-ttu-id="a5917-129">Nyckelords namnen är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="a5917-129">The keyword names are not case-sensitive.</span></span>

<span data-ttu-id="a5917-130">Nyckelordet kan till exempel `.Description` föregå en beskrivning av en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-130">For example, the `.Description` keyword precedes a description of a function or script.</span></span>

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

<span data-ttu-id="a5917-131">Kommentar blocket måste innehålla minst ett nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a5917-131">The comment block must contain at least one keyword.</span></span> <span data-ttu-id="a5917-132">Några av nyckelorden, till exempel `.EXAMPLE` , kan visas många gånger i samma kommentars block.</span><span class="sxs-lookup"><span data-stu-id="a5917-132">Some of the keywords, such as `.EXAMPLE`, can appear many times in the same comment block.</span></span> <span data-ttu-id="a5917-133">Hjälp innehållet för varje nyckelord börjar på raden efter nyckelordet och kan omfatta flera rader.</span><span class="sxs-lookup"><span data-stu-id="a5917-133">The help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

## <a name="syntax-for-comment-based-help-in-functions"></a><span data-ttu-id="a5917-134">Syntax för kommenterings-baserad hjälp i functions</span><span class="sxs-lookup"><span data-stu-id="a5917-134">Syntax for comment-based help in functions</span></span>

<span data-ttu-id="a5917-135">Den kommenterade hjälpen för en funktion kan visas på tre platser:</span><span class="sxs-lookup"><span data-stu-id="a5917-135">Comment-based help for a function can appear in one of three locations:</span></span>

- <span data-ttu-id="a5917-136">I början av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="a5917-136">At the beginning of the function body.</span></span>
- <span data-ttu-id="a5917-137">I slutet av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="a5917-137">At the end of the function body.</span></span>
- <span data-ttu-id="a5917-138">Före `function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-138">Before the `function` keyword.</span></span> <span data-ttu-id="a5917-139">Det får inte finnas mer än en tom rad mellan den sista raden i funktions hjälpen och `function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-139">There cannot be more than one blank line between the last line of the function help and the `function` keyword.</span></span>

<span data-ttu-id="a5917-140">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="a5917-140">For example:</span></span>

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

<span data-ttu-id="a5917-141">eller</span><span class="sxs-lookup"><span data-stu-id="a5917-141">or</span></span>

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

<span data-ttu-id="a5917-142">eller</span><span class="sxs-lookup"><span data-stu-id="a5917-142">or</span></span>

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a><span data-ttu-id="a5917-143">Syntax för kommenterings-baserad hjälp i skript</span><span class="sxs-lookup"><span data-stu-id="a5917-143">Syntax for comment-based help in scripts</span></span>

<span data-ttu-id="a5917-144">Kommentera-baserad hjälp för ett skript kan visas på någon av följande två platser i skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-144">Comment-based help for a script can appear in one of the following two locations in the script.</span></span>

- <span data-ttu-id="a5917-145">I början av skript filen.</span><span class="sxs-lookup"><span data-stu-id="a5917-145">At the beginning of the script file.</span></span> <span data-ttu-id="a5917-146">Skript hjälpen kan bara föregås av kommentarer och tomma rader.</span><span class="sxs-lookup"><span data-stu-id="a5917-146">Script help can be preceded in the script only by comments and blank lines.</span></span>

  <span data-ttu-id="a5917-147">Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen.</span><span class="sxs-lookup"><span data-stu-id="a5917-147">If the first item in the script body (after the help) is a function declaration, there must be at least two blank lines between the end of the script help and the function declaration.</span></span> <span data-ttu-id="a5917-148">Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-148">Otherwise, the help is interpreted as being help for the function, not help for the script.</span></span>

- <span data-ttu-id="a5917-149">I slutet av skript filen.</span><span class="sxs-lookup"><span data-stu-id="a5917-149">At the end of the script file.</span></span> <span data-ttu-id="a5917-150">Men om skriptet är signerat placerar du en kommenterings-baserad hjälp i början av skript filen.</span><span class="sxs-lookup"><span data-stu-id="a5917-150">However, if the script is signed, place Comment-based help at the beginning of the script file.</span></span> <span data-ttu-id="a5917-151">Slutet på skriptet används av signerings blocket.</span><span class="sxs-lookup"><span data-stu-id="a5917-151">The end of the script is occupied by the signature block.</span></span>

<span data-ttu-id="a5917-152">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="a5917-152">For example:</span></span>

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

<span data-ttu-id="a5917-153">eller</span><span class="sxs-lookup"><span data-stu-id="a5917-153">or</span></span>

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a><span data-ttu-id="a5917-154">Syntax för kommenterings-baserad hjälp i skript moduler</span><span class="sxs-lookup"><span data-stu-id="a5917-154">Syntax for comment-based help in script modules</span></span>

<span data-ttu-id="a5917-155">I en skript `.psm1` -modul använder den kommenterade hjälpen syntaxen för functions, inte syntaxen för skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-155">In a script module `.psm1`, comment-based help uses the syntax for functions, not the syntax for scripts.</span></span> <span data-ttu-id="a5917-156">Du kan inte använda kommandosyntaxen för att ge hjälp för alla funktioner som definierats i en-modul.</span><span class="sxs-lookup"><span data-stu-id="a5917-156">You cannot use the script syntax to provide help for all functions defined in a script module.</span></span>

<span data-ttu-id="a5917-157">Om du till exempel använder `.ExternalHelp` nyckelordet för att identifiera de XML-baserade hjälpfilerna för funktionerna i en-modul, måste du lägga till en `.ExternalHelp` kommentar till varje funktion.</span><span class="sxs-lookup"><span data-stu-id="a5917-157">For example, if you are using the `.ExternalHelp` keyword to identify the XML-based help files for the functions in a script module, you must add an `.ExternalHelp` comment to each function.</span></span>

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a><span data-ttu-id="a5917-158">Kommentera-baserade hjälp nyckelord</span><span class="sxs-lookup"><span data-stu-id="a5917-158">Comment-based help keywords</span></span>

<span data-ttu-id="a5917-159">Följande är giltiga kommentarer baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a5917-159">The following are valid comment-based help keywords.</span></span> <span data-ttu-id="a5917-160">De visas i den ordning som de normalt visas i ett hjälp avsnitt, tillsammans med deras avsedda användning.</span><span class="sxs-lookup"><span data-stu-id="a5917-160">They are listed in the order in which they typically appear in a help topic along with their intended use.</span></span> <span data-ttu-id="a5917-161">Dessa nyckelord kan visas i vilken ordning som helst i den kommenterade hjälpen, och de är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="a5917-161">These keywords can appear in any order in the comment-based help, and they are not case-sensitive.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a5917-162">. Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="a5917-162">.SYNOPSIS</span></span>

<span data-ttu-id="a5917-163">En kort beskrivning av funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-163">A brief description of the function or script.</span></span> <span data-ttu-id="a5917-164">Det här nyckelordet kan bara användas en gång i varje ämne.</span><span class="sxs-lookup"><span data-stu-id="a5917-164">This keyword can be used only once in each topic.</span></span>

### <a name="description"></a><span data-ttu-id="a5917-165">. BETECKNING</span><span class="sxs-lookup"><span data-stu-id="a5917-165">.DESCRIPTION</span></span>

<span data-ttu-id="a5917-166">En detaljerad beskrivning av funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-166">A detailed description of the function or script.</span></span> <span data-ttu-id="a5917-167">Det här nyckelordet kan bara användas en gång i varje ämne.</span><span class="sxs-lookup"><span data-stu-id="a5917-167">This keyword can be used only once in each topic.</span></span>

### <a name="parameter"></a><span data-ttu-id="a5917-168">. PROFILESERVICEAPPLICATIONPROXY</span><span class="sxs-lookup"><span data-stu-id="a5917-168">.PARAMETER</span></span>

<span data-ttu-id="a5917-169">Beskrivningen av en parameter.</span><span class="sxs-lookup"><span data-stu-id="a5917-169">The description of a parameter.</span></span> <span data-ttu-id="a5917-170">Lägg till ett `.PARAMETER` nyckelord för varje parameter i syntaxen Function och script.</span><span class="sxs-lookup"><span data-stu-id="a5917-170">Add a `.PARAMETER` keyword for each parameter in the function or script syntax.</span></span>

<span data-ttu-id="a5917-171">Skriv parameter namnet på samma rad som `.PARAMETER` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-171">Type the parameter name on the same line as the `.PARAMETER` keyword.</span></span> <span data-ttu-id="a5917-172">Ange parameter beskrivningen på raderna som följer `.PARAMETER` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-172">Type the parameter description on the lines following the `.PARAMETER` keyword.</span></span> <span data-ttu-id="a5917-173">Windows PowerShell tolkar all text mellan `.PARAMETER` raden och nästa nyckelord eller slutet av kommentars blocket som en del av parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="a5917-173">Windows PowerShell interprets all text between the `.PARAMETER` line and the next keyword or the end of the comment block as part of the parameter description.</span></span>
<span data-ttu-id="a5917-174">Beskrivningen kan innehålla stycke brytningar.</span><span class="sxs-lookup"><span data-stu-id="a5917-174">The description can include paragraph breaks.</span></span>

```
.PARAMETER  <Parameter-Name>
```

<span data-ttu-id="a5917-175">Parameter nyckelorden kan visas i vilken ordning som helst i kommentars blocket, men funktionen eller skript-syntaxen avgör i vilken ordning parametrarna (och deras beskrivningar) visas i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a5917-175">The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters (and their descriptions) appear in help topic.</span></span> <span data-ttu-id="a5917-176">Om du vill ändra ordningen ändrar du syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a5917-176">To change the order, change the syntax.</span></span>

<span data-ttu-id="a5917-177">Du kan också ange en parameter beskrivning genom att placera en kommentar i funktionen eller syntaxen för skriptet omedelbart före parameterns variabel namn.</span><span class="sxs-lookup"><span data-stu-id="a5917-177">You can also specify a parameter description by placing a comment in the function or script syntax immediately before the parameter variable name.</span></span> <span data-ttu-id="a5917-178">För att detta ska fungera måste du också ha ett kommentar block med minst ett nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a5917-178">For this to work, you must also have a comment block with at least one keyword.</span></span>

<span data-ttu-id="a5917-179">Om du använder både en syntax-kommentar och ett `.PARAMETER` nyckelord, används beskrivningen som är associerad med `.PARAMETER` nyckelordet och syntax-kommentaren ignoreras.</span><span class="sxs-lookup"><span data-stu-id="a5917-179">If you use both a syntax comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the syntax comment is ignored.</span></span>

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a><span data-ttu-id="a5917-180">. EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a5917-180">.EXAMPLE</span></span>

<span data-ttu-id="a5917-181">Ett exempel kommando som använder funktionen eller skriptet, eventuellt följt av exempel på utdata och en beskrivning.</span><span class="sxs-lookup"><span data-stu-id="a5917-181">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="a5917-182">Upprepa det här nyckelordet för varje exempel.</span><span class="sxs-lookup"><span data-stu-id="a5917-182">Repeat this keyword for each example.</span></span>

### <a name="inputs"></a><span data-ttu-id="a5917-183">. TILLFÖR</span><span class="sxs-lookup"><span data-stu-id="a5917-183">.INPUTS</span></span>

<span data-ttu-id="a5917-184">.NET-typerna av objekt som kan skickas till funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-184">The .NET types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="a5917-185">Du kan också inkludera en beskrivning av inobjekten.</span><span class="sxs-lookup"><span data-stu-id="a5917-185">You can also include a description of the input objects.</span></span>

### <a name="outputs"></a><span data-ttu-id="a5917-186">. UTDATA</span><span class="sxs-lookup"><span data-stu-id="a5917-186">.OUTPUTS</span></span>

<span data-ttu-id="a5917-187">.NET-typen av objekt som cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="a5917-187">The .NET type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="a5917-188">Du kan också inkludera en beskrivning av de returnerade objekten.</span><span class="sxs-lookup"><span data-stu-id="a5917-188">You can also include a description of the returned objects.</span></span>

### <a name="notes"></a><span data-ttu-id="a5917-189">. NOTER</span><span class="sxs-lookup"><span data-stu-id="a5917-189">.NOTES</span></span>

<span data-ttu-id="a5917-190">Ytterligare information om funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-190">Additional information about the function or script.</span></span>

### <a name="link"></a><span data-ttu-id="a5917-191">. OPERATIONSFÖLJDSLÄNKKOD</span><span class="sxs-lookup"><span data-stu-id="a5917-191">.LINK</span></span>

<span data-ttu-id="a5917-192">Namnet på ett relaterat ämne.</span><span class="sxs-lookup"><span data-stu-id="a5917-192">The name of a related topic.</span></span> <span data-ttu-id="a5917-193">Värdet visas på raden under ". LINK "nyckelordet och måste föregås av en kommentar symbol `#` eller ingå i kommentars blocket.</span><span class="sxs-lookup"><span data-stu-id="a5917-193">The value appears on the line below the ".LINK" keyword and must be preceded by a comment symbol `#` or included in the comment block.</span></span>

<span data-ttu-id="a5917-194">Upprepa `.LINK` nyckelordet för varje relaterat ämne.</span><span class="sxs-lookup"><span data-stu-id="a5917-194">Repeat the `.LINK` keyword for each related topic.</span></span>

<span data-ttu-id="a5917-195">Det här innehållet visas i avsnittet relaterade länkar i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a5917-195">This content appears in the Related Links section of the help topic.</span></span>

<span data-ttu-id="a5917-196">`.Link`Nyckelords innehållet kan också innehålla en Uniform Resource Identifier (URI) till en online-version av samma hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="a5917-196">The `.Link` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same help topic.</span></span> <span data-ttu-id="a5917-197">Online-versionen öppnas när du använder **online** -parametern för `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="a5917-197">The online version opens when you use the **Online** parameter of `Get-Help`.</span></span> <span data-ttu-id="a5917-198">URI: n måste börja med http eller https.</span><span class="sxs-lookup"><span data-stu-id="a5917-198">The URI must begin with "http" or "https".</span></span>

### <a name="component"></a><span data-ttu-id="a5917-199">. KOMPONENTFILERNA</span><span class="sxs-lookup"><span data-stu-id="a5917-199">.COMPONENT</span></span>

<span data-ttu-id="a5917-200">Namnet på tekniken eller funktionen som funktionen eller skriptet använder, eller som den är relaterad till.</span><span class="sxs-lookup"><span data-stu-id="a5917-200">The name of the technology or feature that the function or script uses, or to which it is related.</span></span> <span data-ttu-id="a5917-201">**Komponent** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="a5917-201">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="role"></a><span data-ttu-id="a5917-202">. ROLLINNEHAVAREN</span><span class="sxs-lookup"><span data-stu-id="a5917-202">.ROLE</span></span>

<span data-ttu-id="a5917-203">Namnet på användar rollen för hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a5917-203">The name of the user role for the help topic.</span></span> <span data-ttu-id="a5917-204">**Roll** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="a5917-204">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="functionality"></a><span data-ttu-id="a5917-205">. FUNKTIONS</span><span class="sxs-lookup"><span data-stu-id="a5917-205">.FUNCTIONALITY</span></span>

<span data-ttu-id="a5917-206">Nyckelord som beskriver den avsedda användningen av funktionen.</span><span class="sxs-lookup"><span data-stu-id="a5917-206">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="a5917-207">**Funktions** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="a5917-207">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="forwardhelptargetname"></a><span data-ttu-id="a5917-208">. FORWARDHELPTARGETNAME</span><span class="sxs-lookup"><span data-stu-id="a5917-208">.FORWARDHELPTARGETNAME</span></span>

<span data-ttu-id="a5917-209">Omdirigerar till hjälp avsnittet för det angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="a5917-209">Redirects to the help topic for the specified command.</span></span> <span data-ttu-id="a5917-210">Du kan omdirigera användare till valfritt hjälp avsnitt, inklusive hjälp avsnitt för en funktion, ett skript, en cmdlet eller en provider.</span><span class="sxs-lookup"><span data-stu-id="a5917-210">You can redirect users to any help topic, including help topics for a function, script, cmdlet, or provider.</span></span>

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a><span data-ttu-id="a5917-211">. FORWARDHELPCATEGORY</span><span class="sxs-lookup"><span data-stu-id="a5917-211">.FORWARDHELPCATEGORY</span></span>

<span data-ttu-id="a5917-212">Anger hjälp kategorin för objektet i `.ForwardHelpTargetName` .</span><span class="sxs-lookup"><span data-stu-id="a5917-212">Specifies the help category of the item in `.ForwardHelpTargetName`.</span></span> <span data-ttu-id="a5917-213">Giltiga värden är,,,,,,,,,, `Alias` `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` eller `All` .</span><span class="sxs-lookup"><span data-stu-id="a5917-213">Valid values are `Alias`, `Cmdlet`, `HelpFile`, `Function`, `Provider`, `General`, `FAQ`, `Glossary`, `ScriptCommand`, `ExternalScript`, `Filter`, or `All`.</span></span> <span data-ttu-id="a5917-214">Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.</span><span class="sxs-lookup"><span data-stu-id="a5917-214">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a><span data-ttu-id="a5917-215">. REMOTEHELPRUNSPACE</span><span class="sxs-lookup"><span data-stu-id="a5917-215">.REMOTEHELPRUNSPACE</span></span>

<span data-ttu-id="a5917-216">Anger en session som innehåller hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a5917-216">Specifies a session that contains the help topic.</span></span> <span data-ttu-id="a5917-217">Ange en variabel som innehåller ett **PSSession** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a5917-217">Enter a variable that contains a **PSSession** object.</span></span> <span data-ttu-id="a5917-218">Det här nyckelordet används av cmdleten [export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) för att hitta hjälp avsnitten för de exporterade kommandona.</span><span class="sxs-lookup"><span data-stu-id="a5917-218">This keyword is used by the [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet to find the help topics for the exported commands.</span></span>

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a><span data-ttu-id="a5917-219">. EXTERNALHELP</span><span class="sxs-lookup"><span data-stu-id="a5917-219">.EXTERNALHELP</span></span>

<span data-ttu-id="a5917-220">Anger en XML-baserad hjälpfil för skriptet eller funktionen.</span><span class="sxs-lookup"><span data-stu-id="a5917-220">Specifies an XML-based help file for the script or function.</span></span>

```powershell
# .EXTERNALHELP <XML Help File>
```

<span data-ttu-id="a5917-221">`.ExternalHelp`Nyckelordet krävs när en funktion eller ett skript dokumenteras i XML-filer.</span><span class="sxs-lookup"><span data-stu-id="a5917-221">The `.ExternalHelp` keyword is required when a function or script is documented in XML files.</span></span> <span data-ttu-id="a5917-222">Utan det här nyckelordet `Get-Help` kan inte hitta den XML-baserade hjälp filen för funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-222">Without this keyword, `Get-Help` cannot find the XML-based help file for the function or script.</span></span>

<span data-ttu-id="a5917-223">`.ExternalHelp`Nyckelordet har företräde framför andra kommenterings-baserade hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a5917-223">The `.ExternalHelp` keyword takes precedence over other comment-based help keywords.</span></span> <span data-ttu-id="a5917-224">Om `.ExternalHelp` finns visas `Get-Help` inte kommenterad hjälp, även om det inte går att hitta ett hjälp avsnitt som matchar värdet för `.ExternalHelp` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-224">If `.ExternalHelp` is present, `Get-Help` does not display comment-based help, even if it cannot find a help topic that matches the value of the `.ExternalHelp` keyword.</span></span>

<span data-ttu-id="a5917-225">Om funktionen exporteras av en modul ställer du in värdet för `.ExternalHelp` nyckelordet till ett fil namn utan sökväg.</span><span class="sxs-lookup"><span data-stu-id="a5917-225">If the function is exported by a module, set the value of the `.ExternalHelp` keyword to a filename without a path.</span></span> <span data-ttu-id="a5917-226">`Get-Help` söker efter det angivna fil namnet i en språkspecifik under katalog i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="a5917-226">`Get-Help` looks for the specified file name in a language-specific subdirectory of the module directory.</span></span> <span data-ttu-id="a5917-227">Det finns inga krav på namnet på den XML-baserade hjälp filen för en funktion, men det är en bra idé att använda följande format:</span><span class="sxs-lookup"><span data-stu-id="a5917-227">There are no requirements for the name of the XML-based help file for a function, but a best practice is to use the following format:</span></span>

```
<ScriptModule.psm1>-help.xml
```

<span data-ttu-id="a5917-228">Om funktionen inte ingår i en modul inkluderar du en sökväg till den XML-baserade hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="a5917-228">If the function is not included in a module, include a path to the XML-based help file.</span></span> <span data-ttu-id="a5917-229">Om värdet innehåller en sökväg och sökvägen innehåller UI-kultur-specifika under kataloger, `Get-Help` söker igenom under katalogerna rekursivt efter en XML-fil med namnet på skriptet eller funktionen i enlighet med de språk reserv standarder som är etablerade för Windows, precis som i en modul katalog.</span><span class="sxs-lookup"><span data-stu-id="a5917-229">If the value includes a path and the path contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does in a module directory.</span></span>

<span data-ttu-id="a5917-230">Mer information om cmdlet Help XML-baserade hjälp fils format finns i [så här skriver du cmdlet-hjälpen](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="a5917-230">For more information about the cmdlet help XML-based help file format, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="autogenerated-content"></a><span data-ttu-id="a5917-231">Automatiskt genererat innehåll</span><span class="sxs-lookup"><span data-stu-id="a5917-231">Autogenerated content</span></span>

<span data-ttu-id="a5917-232">Namn, syntax, parameter lista, parameter-Attribute tabell, vanliga parametrar och anmärkningar genereras automatiskt av `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a5917-232">The name, syntax, parameter list, parameter attribute table, common parameters, and remarks are automatically generated by the `Get-Help` cmdlet.</span></span>

### <a name="name"></a><span data-ttu-id="a5917-233">Name</span><span class="sxs-lookup"><span data-stu-id="a5917-233">Name</span></span>

<span data-ttu-id="a5917-234">Avsnittet **Name** i ett funktions hjälp avsnitt tas från funktions namnet i Function-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a5917-234">The **Name** section of a function help topic is taken from the function name in the function syntax.</span></span> <span data-ttu-id="a5917-235">**Namnet** på ett skript hjälp avsnitt tas från skript fil namnet.</span><span class="sxs-lookup"><span data-stu-id="a5917-235">The **Name** of a script help topic is taken from the script filename.</span></span> <span data-ttu-id="a5917-236">Om du vill ändra namnet eller dess versaler ändrar du syntaxen för funktionen eller skript fil namnet.</span><span class="sxs-lookup"><span data-stu-id="a5917-236">To change the name or its capitalization, change the function syntax or the script filename.</span></span>

### <a name="syntax"></a><span data-ttu-id="a5917-237">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5917-237">Syntax</span></span>

<span data-ttu-id="a5917-238">Avsnittet **syntax** i hjälp avsnittet genereras från funktionen eller syntaxen i skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-238">The **Syntax** section of the help topic is generated from the function or script syntax.</span></span> <span data-ttu-id="a5917-239">Om du vill lägga till information i syntaxen för hjälp ämnet, till exempel .NET-typen för en parameter, lägger du till informationen i syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a5917-239">To add detail to the help topic syntax, such as the .NET type of a parameter, add the detail to the syntax.</span></span> <span data-ttu-id="a5917-240">Om du inte anger en parameter typ infogas **objekt** typen som standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="a5917-240">If you do not specify a parameter type, the **Object** type is inserted as the default value.</span></span>

### <a name="parameter-list"></a><span data-ttu-id="a5917-241">Parameter lista</span><span class="sxs-lookup"><span data-stu-id="a5917-241">Parameter List</span></span>

<span data-ttu-id="a5917-242">Parameter listan i hjälp avsnittet genereras från funktionen eller syntaxen för skriptet och från de beskrivningar som du lägger till med hjälp av `.Parameter` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-242">The parameter list in the help topic is generated from the function or script syntax and from the descriptions that you add by using the `.Parameter` keyword.</span></span> <span data-ttu-id="a5917-243">Funktions parametrarna visas i avsnittet **parametrar** i hjälp avsnittet i samma ordning som de visas i funktionen eller syntaxen för skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-243">The function parameters appear in the **Parameters** section of the help topic in the same order that they appear in the function or script syntax.</span></span> <span data-ttu-id="a5917-244">Stavning och Skift läge för parameter namn tas också med i syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a5917-244">The spelling and capitalization of parameter names is also taken from the syntax.</span></span> <span data-ttu-id="a5917-245">Det påverkas inte av det parameter namn som anges av `.Parameter` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-245">It is not affected by the parameter name specified by the `.Parameter` keyword.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="a5917-246">Vanliga parametrar</span><span class="sxs-lookup"><span data-stu-id="a5917-246">Common Parameters</span></span>

<span data-ttu-id="a5917-247">De **gemensamma parametrarna** läggs till i syntax och parameter listan i hjälp avsnittet, även om de inte har någon påverkan.</span><span class="sxs-lookup"><span data-stu-id="a5917-247">The **Common parameters** are added to the syntax and parameter list of the help topic, even if they have no effect.</span></span> <span data-ttu-id="a5917-248">Mer information om de gemensamma parametrarna finns [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a5917-248">For more information about the common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="a5917-249">Parameter egenskaps tabell</span><span class="sxs-lookup"><span data-stu-id="a5917-249">Parameter Attribute Table</span></span>

<span data-ttu-id="a5917-250">`Get-Help` genererar tabellen med parameter-attribut som visas när du använder parametern **fullständig** eller **parameter** i `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="a5917-250">`Get-Help` generates the table of parameter attributes that appears when you use the **Full** or **Parameter** parameter of `Get-Help`.</span></span> <span data-ttu-id="a5917-251">Värdet för attributen **required** , **position** och **Standardvärde** tas från funktionen eller syntaxen i skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-251">The value of the **Required** , **Position** , and **Default** value attributes is taken from the function or script syntax.</span></span>

<span data-ttu-id="a5917-252">Standardvärden och ett värde för **acceptera jokertecken** visas inte i tabellen parameter attribut, även om de definieras i funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-252">Default values and a value for **Accept Wildcard characters** do not appear in the parameter attribute table even when they are defined in the function or script.</span></span> <span data-ttu-id="a5917-253">För att hjälpa användarna att ange den här informationen i parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="a5917-253">To help users, provide this information in the parameter description.</span></span>

### <a name="remarks"></a><span data-ttu-id="a5917-254">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a5917-254">Remarks</span></span>

<span data-ttu-id="a5917-255">Avsnittet **anmärkningar** i hjälp avsnittet genereras automatiskt från funktionen eller skript namnet.</span><span class="sxs-lookup"><span data-stu-id="a5917-255">The **Remarks** section of the help topic is automatically generated from the function or script name.</span></span> <span data-ttu-id="a5917-256">Du kan inte ändra eller påverka dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="a5917-256">You cannot change or affect its content.</span></span>

## <a name="examples"></a><span data-ttu-id="a5917-257">Exempel</span><span class="sxs-lookup"><span data-stu-id="a5917-257">Examples</span></span>

### <a name="comment-based-help-for-a-function"></a><span data-ttu-id="a5917-258">Kommenterings-baserad hjälp för en funktion</span><span class="sxs-lookup"><span data-stu-id="a5917-258">Comment-based Help for a Function</span></span>

<span data-ttu-id="a5917-259">Följande exempel funktion innehåller kommenterings-baserad hjälp:</span><span class="sxs-lookup"><span data-stu-id="a5917-259">The following sample function includes comment-based help:</span></span>

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

<span data-ttu-id="a5917-260">Resultatet är följande:</span><span class="sxs-lookup"><span data-stu-id="a5917-260">The results are as follows:</span></span>

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a><span data-ttu-id="a5917-261">Parameter beskrivningar i Function-syntax</span><span class="sxs-lookup"><span data-stu-id="a5917-261">Parameter Descriptions in Function Syntax</span></span>

<span data-ttu-id="a5917-262">Det här exemplet är detsamma som föregående, förutom att parameter beskrivningarna infogas i Function-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a5917-262">This example is the same as the previous one, except that the parameter descriptions are inserted in the function syntax.</span></span> <span data-ttu-id="a5917-263">Det här formatet är mest användbart när beskrivningarna är korta.</span><span class="sxs-lookup"><span data-stu-id="a5917-263">This format is most useful when the descriptions are brief.</span></span>

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a><span data-ttu-id="a5917-264">Kommenterings-baserad hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="a5917-264">Comment-based Help for a Script</span></span>

<span data-ttu-id="a5917-265">Följande exempel skript innehåller kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="a5917-265">The following sample script includes comment-based help.</span></span> <span data-ttu-id="a5917-266">Lägg märke till de tomma raderna mellan stängningen `#>` och `Param` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="a5917-266">Notice the blank lines between the closing `#>` and the `Param` statement.</span></span> <span data-ttu-id="a5917-267">I ett skript som saknar `Param` instruktion måste det finnas minst två tomma rader mellan den sista kommentaren i hjälp avsnittet och den första funktions deklarationen.</span><span class="sxs-lookup"><span data-stu-id="a5917-267">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the help topic and the first function declaration.</span></span> <span data-ttu-id="a5917-268">Utan dessa tomma rader `Get-Help` associeras hjälp avsnittet med funktionen, inte skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-268">Without these blank lines, `Get-Help` associates the help topic with the function, not the script.</span></span>

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

<span data-ttu-id="a5917-269">Följande kommando hämtar skript hjälpen.</span><span class="sxs-lookup"><span data-stu-id="a5917-269">The following command gets the script help.</span></span> <span data-ttu-id="a5917-270">Eftersom skriptet inte finns i en katalog som anges i `$env:Path` miljövariabeln, `Get-Help` måste kommandot som hämtar skript-hjälpen ange skript Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="a5917-270">Because the script is not in a directory that is listed in the `$env:Path` environment variable, the `Get-Help` command that gets the script help must specify the script path.</span></span>

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a><span data-ttu-id="a5917-271">Omdirigerar till en XML-fil</span><span class="sxs-lookup"><span data-stu-id="a5917-271">Redirecting to an XML File</span></span>

<span data-ttu-id="a5917-272">Du kan skriva XML-baserade hjälp avsnitt för funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="a5917-272">You can write XML-based help topics for functions and scripts.</span></span> <span data-ttu-id="a5917-273">Även om det är enklare att implementera en kommenterad hjälp, krävs det en XML-baserad hjälp för uppdaterings bara hjälp och för att tillhandahålla hjälp avsnitt på flera språk.</span><span class="sxs-lookup"><span data-stu-id="a5917-273">Although comment-based help is easier to implement, XML-based help is required for Updatable Help and to provide help topics in multiple languages.</span></span>

<span data-ttu-id="a5917-274">I följande exempel visas de första raderna i Update-Month.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-274">The following example shows the first few lines of the Update-Month.ps1 script.</span></span>
<span data-ttu-id="a5917-275">Skriptet använder `.ExternalHelp` nyckelordet för att ange sökvägen till ett XML-baserat hjälp avsnitt för skriptet.</span><span class="sxs-lookup"><span data-stu-id="a5917-275">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based help topic for the script.</span></span>

<span data-ttu-id="a5917-276">Observera att `.ExternalHelp` nyckelordets värde visas på samma rad som nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a5917-276">Note that the value of the `.ExternalHelp` keyword appears on the same line as the keyword.</span></span> <span data-ttu-id="a5917-277">Andra placeringar är ineffektiva.</span><span class="sxs-lookup"><span data-stu-id="a5917-277">Any other placement is ineffective.</span></span>

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

<span data-ttu-id="a5917-278">I följande exempel visas tre giltiga placeringar av `.ExternalHelp` nyckelordet i en funktion.</span><span class="sxs-lookup"><span data-stu-id="a5917-278">The following examples show three valid placements of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a><span data-ttu-id="a5917-279">Omdirigera till ett annat hjälp avsnitt</span><span class="sxs-lookup"><span data-stu-id="a5917-279">Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="a5917-280">Följande kod är ett utdrag från början av den inbyggda hjälp funktionen i PowerShell, som visar en skärm med hjälp text i taget.</span><span class="sxs-lookup"><span data-stu-id="a5917-280">The following code is an excerpt from the beginning of the built-in help function in PowerShell, which displays one screen of help text at a time.</span></span>
<span data-ttu-id="a5917-281">Eftersom hjälp avsnittet för `Get-Help` cmdlet: en beskriver hjälp funktionen, använder funktionen och för att `.ForwardHelpTargetName` `.ForwardHelpCategory` omdirigera användaren till `Get-Help` cmdlet-hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a5917-281">Because the help topic for the `Get-Help` cmdlet describes the help function, the help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the `Get-Help` cmdlet help topic.</span></span>

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

<span data-ttu-id="a5917-282">Följande kommando använder den här funktionen:</span><span class="sxs-lookup"><span data-stu-id="a5917-282">The following command uses this feature:</span></span>

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a><span data-ttu-id="a5917-283">Se även</span><span class="sxs-lookup"><span data-stu-id="a5917-283">See also</span></span>

[<span data-ttu-id="a5917-284">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a5917-284">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="a5917-285">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="a5917-285">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="a5917-286">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="a5917-286">about_Scripts</span></span>](about_Scripts.md)

[<span data-ttu-id="a5917-287">Så här skriver du cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="a5917-287">How to Write Cmdlet Help</span></span>](https://go.microsoft.com/fwlink/?LinkID=123415)
