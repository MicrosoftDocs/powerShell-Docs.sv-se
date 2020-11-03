---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: a9a7aa7730d920bb78e0ae64daa50e5a28921163
ms.sourcegitcommit: b7ff031a12afd04910aeb98345ebee92f5845b0c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "93268790"
---
# <span data-ttu-id="e076c-103">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e076c-103">Get-Help</span></span>

## <span data-ttu-id="e076c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e076c-104">SYNOPSIS</span></span>
<span data-ttu-id="e076c-105">Visar information om PowerShell-kommandon och-koncept.</span><span class="sxs-lookup"><span data-stu-id="e076c-105">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="e076c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e076c-106">SYNTAX</span></span>

### <span data-ttu-id="e076c-107">AllUsersView (standard)</span><span class="sxs-lookup"><span data-stu-id="e076c-107">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [-Full] [<CommonParameters>]
```

### <span data-ttu-id="e076c-108">DetailedView</span><span class="sxs-lookup"><span data-stu-id="e076c-108">DetailedView</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Detailed [<CommonParameters>]
```

### <span data-ttu-id="e076c-109">Exempel</span><span class="sxs-lookup"><span data-stu-id="e076c-109">Examples</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Examples [<CommonParameters>]
```

### <span data-ttu-id="e076c-110">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e076c-110">Parameters</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Parameter <String> [<CommonParameters>]
```

### <span data-ttu-id="e076c-111">Online</span><span class="sxs-lookup"><span data-stu-id="e076c-111">Online</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### <span data-ttu-id="e076c-112">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="e076c-112">ShowWindow</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## <span data-ttu-id="e076c-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e076c-113">DESCRIPTION</span></span>

<span data-ttu-id="e076c-114">`Get-Help`Cmdleten visar information om PowerShell-begrepp och kommandon, inklusive cmdlets, functions, Common Information Model (CIM), arbets flöden, providers, alias och skript.</span><span class="sxs-lookup"><span data-stu-id="e076c-114">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="e076c-115">Om du vill ha hjälp med en PowerShell-cmdlet skriver du `Get-Help` följt av cmdlet-namnet, t `Get-Help Get-Process` . ex.:.</span><span class="sxs-lookup"><span data-stu-id="e076c-115">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="e076c-116">Konceptuell hjälp artiklar i PowerShell börjar med **about_** , till exempel **about_Comparison_Operators**.</span><span class="sxs-lookup"><span data-stu-id="e076c-116">Conceptual help articles in PowerShell begin with **about_** , such as **about_Comparison_Operators**.</span></span> <span data-ttu-id="e076c-117">Om du vill se alla **about_** artiklar skriver du `Get-Help about_*` .</span><span class="sxs-lookup"><span data-stu-id="e076c-117">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="e076c-118">Om du vill se en viss artikel skriver du `Get-Help about_<article-name>` , till exempel `Get-Help about_Comparison_Operators` .</span><span class="sxs-lookup"><span data-stu-id="e076c-118">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="e076c-119">Om du vill ha hjälp med en PowerShell-Provider skriver du `Get-Help` följt av namnet på providern.</span><span class="sxs-lookup"><span data-stu-id="e076c-119">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="e076c-120">Om du till exempel vill få hjälp med certifikat leverantören skriver du `Get-Help Certificate` .</span><span class="sxs-lookup"><span data-stu-id="e076c-120">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="e076c-121">Du kan också skriva `help` eller `man` , som visar en skärm med text i taget.</span><span class="sxs-lookup"><span data-stu-id="e076c-121">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="e076c-122">Eller, `<cmdlet-name> -?` som är identisk med `Get-Help` , men endast fungerar för-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e076c-122">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="e076c-123">`Get-Help` hämtar hjälp innehållet som det visar från hjälp filer på din dator.</span><span class="sxs-lookup"><span data-stu-id="e076c-123">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="e076c-124">Utan hjälpfilerna `Get-Help` visar endast grundläggande information om cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e076c-124">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="e076c-125">Några PowerShell-moduler innehåller hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="e076c-125">Some PowerShell modules include help files.</span></span> <span data-ttu-id="e076c-126">Från och med PowerShell 3,0 innehåller modulerna som medföljer operativ systemet Windows inte hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="e076c-126">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="e076c-127">Om du vill hämta eller uppdatera hjälpfilerna för en modul i PowerShell 3,0 använder du `Update-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e076c-127">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="e076c-128">Du kan också Visa PowerShell-hjälp dokument online i Microsoft Docs. Om du vill hämta online-versionen av en hjälpfil använder du parametern **online** , t. ex `Get-Help Get-Process -Online` .:.</span><span class="sxs-lookup"><span data-stu-id="e076c-128">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="e076c-129">Läs mer om PowerShell-dokumentationen i Microsoft Docs PowerShell- [dokumentationen](/powershell).</span><span class="sxs-lookup"><span data-stu-id="e076c-129">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="e076c-130">Om du skriver `Get-Help` följt av det exakta namnet på en hjälp artikel, eller ett ord som är unikt för en hjälp artikel, `Get-Help` visar artikelns innehåll.</span><span class="sxs-lookup"><span data-stu-id="e076c-130">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="e076c-131">Om du anger det exakta namnet på ett kommando alias `Get-Help` visar hjälpen för det ursprungliga kommandot.</span><span class="sxs-lookup"><span data-stu-id="e076c-131">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="e076c-132">Om du anger ett ord-eller ord mönster som visas i flera hjälp artikel rubriker `Get-Help` visas en lista över matchande rubriker.</span><span class="sxs-lookup"><span data-stu-id="e076c-132">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="e076c-133">Om du anger text som inte visas i någon hjälp artikel titlar, `Get-Help` visar en lista över artiklar som innehåller texten i innehållet.</span><span class="sxs-lookup"><span data-stu-id="e076c-133">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="e076c-134">`Get-Help` kan få hjälp artiklar för alla språk som stöds och nationella inställningar.</span><span class="sxs-lookup"><span data-stu-id="e076c-134">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="e076c-135">`Get-Help` börja med att leta efter hjälpfiler i språk uppsättningen för Windows och sedan i det överordnade språket, till exempel **PT** för **pt-br** , och sedan i ett återställnings språk.</span><span class="sxs-lookup"><span data-stu-id="e076c-135">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR** , and then in a fallback locale.</span></span> <span data-ttu-id="e076c-136">Från och med PowerShell 3,0, om det `Get-Help` inte finns hjälp i reserv språket, söker det efter hjälp artiklar på engelska, **en-US** , innan det returnerar ett fel meddelande eller visar automatiskt genererad hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-136">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US** , before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="e076c-137">Information om symbolerna som `Get-Help` visas i syntaxen för kommandosyntaxen finns [about_Command_Syntax](./About/about_Command_Syntax.md).</span><span class="sxs-lookup"><span data-stu-id="e076c-137">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="e076c-138">Information om attributvärden, till exempel **obligatorisk** och **Position** , finns [about_Parameters](./About/about_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e076c-138">For information about parameter attributes, such as **Required** and **Position** , see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="e076c-139">I PowerShell 3,0 och PowerShell 4,0 `Get-Help` går det inte **About** att hitta artiklar i moduler om modulen inte har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e076c-139">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="e076c-140">Detta är ett känt fel.</span><span class="sxs-lookup"><span data-stu-id="e076c-140">This is a known issue.</span></span> <span data-ttu-id="e076c-141">**Om** du vill hämta artiklar i en modul importerar du modulen antingen med hjälp av `Import-Module` cmdleten eller genom att köra en cmdlet som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="e076c-141">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="e076c-142">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e076c-142">EXAMPLES</span></span>

### <span data-ttu-id="e076c-143">Exempel 1: Visa grundläggande hjälp information om en cmdlet</span><span class="sxs-lookup"><span data-stu-id="e076c-143">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="e076c-144">I de här exemplen visas grundläggande hjälp information om `Format-Table` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e076c-144">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="e076c-145">`Get-Help <cmdlet-name>` är den enklaste och standardsyntaxen för `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e076c-145">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="e076c-146">Du kan utelämna parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="e076c-146">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="e076c-147">Syntaxen `<cmdlet-name> -?` fungerar bara för-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e076c-147">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="e076c-148">Exempel 2: Visa grundläggande information en sida i taget</span><span class="sxs-lookup"><span data-stu-id="e076c-148">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="e076c-149">I de här exemplen visas grundläggande hjälp information om `Format-Table` cmdleten en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="e076c-149">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="e076c-150">`help` är en funktion som kör `Get-Help` cmdlet internt och visar resultatet en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="e076c-150">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="e076c-151">`man` är ett alias för `help` funktionen.</span><span class="sxs-lookup"><span data-stu-id="e076c-151">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="e076c-152">`Get-Help Format-Table` skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e076c-152">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="e076c-153">`Out-Host -Paging` tar emot utdata från pipelinen och visar en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="e076c-153">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="e076c-154">Mer information finns i [out-Host](Out-Host.md).</span><span class="sxs-lookup"><span data-stu-id="e076c-154">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="e076c-155">Exempel 3: Visa mer information om en cmdlet</span><span class="sxs-lookup"><span data-stu-id="e076c-155">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="e076c-156">I de här exemplen visas mer detaljerad hjälp information om `Format-Table` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e076c-156">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="e076c-157">Den **detaljerade** parametern visar hjälp artikelns detaljerade vy som innehåller parameter beskrivningar och exempel.</span><span class="sxs-lookup"><span data-stu-id="e076c-157">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="e076c-158">Den **fullständiga** parametern visar hjälp artikelns fullständiga vy som innehåller parameter beskrivningar, exempel, indata och utdata för objekt och ytterligare anteckningar.</span><span class="sxs-lookup"><span data-stu-id="e076c-158">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="e076c-159">De **detaljerade** och **fullständiga** parametrarna gäller endast för kommandon som har hjälpfiler installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="e076c-159">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="e076c-160">Parametrarna gäller inte för de konceptuella ( **about_** ) hjälp artiklarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-160">The parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="e076c-161">Exempel 4: Visa valda delar av en cmdlet med hjälp av parametrar</span><span class="sxs-lookup"><span data-stu-id="e076c-161">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="e076c-162">I de här exemplen visas valda delar av `Format-Table` cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e076c-162">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="e076c-163">I **exempel** parametern visas hjälp filens **namn** och **sammanfattnings** avsnitt och alla exempel.</span><span class="sxs-lookup"><span data-stu-id="e076c-163">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="e076c-164">Du kan inte ange ett exempel nummer eftersom **exempel** parametern är en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="e076c-164">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="e076c-165">**Parametern parameter** visar bara beskrivningarna av de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-165">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="e076c-166">Om du bara anger jokertecknet asterisk ( `*` ) visas beskrivningarna för alla parametrar.</span><span class="sxs-lookup"><span data-stu-id="e076c-166">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="e076c-167">När **parametern** anger ett parameter namn, till exempel **groupby** , visas information om den parametern.</span><span class="sxs-lookup"><span data-stu-id="e076c-167">When **Parameter** specifies a parameter name such as **GroupBy** , information about that parameter is shown.</span></span>

<span data-ttu-id="e076c-168">Dessa parametrar är inte effektiva för de konceptuella ( **about_** ) hjälp artiklarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-168">These parameters aren't effective for the conceptual ( **about_** ) help articles.</span></span>

### <span data-ttu-id="e076c-169">Exempel 5: Visa onlineversionen av hjälp</span><span class="sxs-lookup"><span data-stu-id="e076c-169">Example 5: Display online version of help</span></span>

<span data-ttu-id="e076c-170">I det här exemplet visas onlineversionen av hjälp artikeln för `Format-Table` cmdleten i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="e076c-170">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="e076c-171">Exempel 6: Visa hjälp om hjälp systemet</span><span class="sxs-lookup"><span data-stu-id="e076c-171">Example 6: Display help about the help system</span></span>

<span data-ttu-id="e076c-172">`Get-Help`Cmdlet utan parametrar visar information om PowerShell-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e076c-172">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="e076c-173">Exempel 7: Visa tillgängliga hjälp artiklar</span><span class="sxs-lookup"><span data-stu-id="e076c-173">Example 7: Display available help articles</span></span>

<span data-ttu-id="e076c-174">I det här exemplet visas en lista över alla hjälp artiklar som är tillgängliga på din dator.</span><span class="sxs-lookup"><span data-stu-id="e076c-174">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="e076c-175">Exempel 8: Visa en lista med konceptuella artiklar</span><span class="sxs-lookup"><span data-stu-id="e076c-175">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="e076c-176">I det här exemplet visas en lista över de konceptuella artiklarna som ingår i PowerShell-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e076c-176">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="e076c-177">Alla dessa artiklar börjar med de tecken som **about_**.</span><span class="sxs-lookup"><span data-stu-id="e076c-177">All these articles begin with the characters **about_**.</span></span> <span data-ttu-id="e076c-178">Om du vill visa en viss hjälp fil skriver du till `Get-Help \<about_article-name\>` exempel `Get-Help about_Signing` .</span><span class="sxs-lookup"><span data-stu-id="e076c-178">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="e076c-179">Endast de konceptuella artiklarna som innehåller hjälpfiler som är installerade på datorn visas.</span><span class="sxs-lookup"><span data-stu-id="e076c-179">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="e076c-180">Information om hur du hämtar och installerar hjälpfiler i PowerShell 3,0 finns i [Update-Help](Update-Help.md).</span><span class="sxs-lookup"><span data-stu-id="e076c-180">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="e076c-181">Exempel 9: Sök efter ett ord i cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="e076c-181">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="e076c-182">Det här exemplet visar hur du söker efter ett ord i en hjälp artikel för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e076c-182">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="e076c-183">`Get-Help` använder den **fullständiga** parametern för att få hjälp information för `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="e076c-183">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="e076c-184">**MamlCommandHelpInfo** -objektet skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e076c-184">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="e076c-185">`Out-String` använder **Stream** -parametern för att konvertera objektet till en sträng.</span><span class="sxs-lookup"><span data-stu-id="e076c-185">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="e076c-186">`Select-String` använder **mönster** parametern för att söka i strängen efter **CliXml**.</span><span class="sxs-lookup"><span data-stu-id="e076c-186">`Select-String` uses the **Pattern** parameter to search the string for **Clixml**.</span></span>

### <span data-ttu-id="e076c-187">Exempel 10: Visa en lista över artiklar som innehåller ett ord</span><span class="sxs-lookup"><span data-stu-id="e076c-187">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="e076c-188">I det här exemplet visas en lista över artiklar som innehåller Word- **fjärrkommunikation**.</span><span class="sxs-lookup"><span data-stu-id="e076c-188">This example displays a list of articles that include the word **remoting**.</span></span>

<span data-ttu-id="e076c-189">När du anger ett ord som inte visas i någon artikel rubrik, `Get-Help` visar en lista över artiklar som innehåller ordet.</span><span class="sxs-lookup"><span data-stu-id="e076c-189">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

```powershell
Get-Help -Name remoting
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...
```

### <span data-ttu-id="e076c-190">Exempel 11: Visa leverantörsspecifik hjälp</span><span class="sxs-lookup"><span data-stu-id="e076c-190">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="e076c-191">I det här exemplet visas två sätt att hämta den providerspecifika hjälpen för `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="e076c-191">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="e076c-192">De här kommandona får hjälp som förklarar hur du använder `Get-Item` cmdleten i PowerShell-SQL Server-providerns **DataCollection** -nod.</span><span class="sxs-lookup"><span data-stu-id="e076c-192">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="e076c-193">I det första exemplet används `Get-Help` parametern **Path** för att ange SQL Server providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="e076c-193">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="e076c-194">Eftersom providerns sökväg har angetts kan du köra kommandot från alla Sök vägs platser.</span><span class="sxs-lookup"><span data-stu-id="e076c-194">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="e076c-195">Det andra exemplet använder `Set-Location` för att navigera till SQL Server leverantörs sökväg.</span><span class="sxs-lookup"><span data-stu-id="e076c-195">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="e076c-196">Från den platsen behövs inte **Sök vägs** parametern för `Get-Help` att hämta den providerspecifika hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e076c-196">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

```powershell
Get-Help Get-Item -Path SQLSERVER:\DataCollection
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

```powershell
Set-Location SQLSERVER:\DataCollection
SQLSERVER:\DataCollection> Get-Help Get-Item
```

```Output
NAME

    Get-Item

SYNOPSIS

    Gets a collection of Server objects for the local computer and any computers

    to which you have made a SQL Server PowerShell connection.
    ...
```

### <span data-ttu-id="e076c-197">Exempel 12: Visa hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="e076c-197">Example 12: Display help for a script</span></span>

<span data-ttu-id="e076c-198">I det här exemplet får du hjälp med `MyScript.ps1 script` .</span><span class="sxs-lookup"><span data-stu-id="e076c-198">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="e076c-199">Information om hur du skriver hjälp för dina funktioner och skript finns [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="e076c-199">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="e076c-200">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e076c-200">PARAMETERS</span></span>

### <span data-ttu-id="e076c-201">– Kategori</span><span class="sxs-lookup"><span data-stu-id="e076c-201">-Category</span></span>

<span data-ttu-id="e076c-202">Visar hjälp endast för objekt i den angivna kategorin och deras alias.</span><span class="sxs-lookup"><span data-stu-id="e076c-202">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="e076c-203">Konceptuella artiklar finns i kategorin **Hjälpfil** .</span><span class="sxs-lookup"><span data-stu-id="e076c-203">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="e076c-204">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="e076c-204">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e076c-205">Alias</span><span class="sxs-lookup"><span data-stu-id="e076c-205">Alias</span></span>
- <span data-ttu-id="e076c-206">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e076c-206">Cmdlet</span></span>
- <span data-ttu-id="e076c-207">Leverantör</span><span class="sxs-lookup"><span data-stu-id="e076c-207">Provider</span></span>
- <span data-ttu-id="e076c-208">Allmänt</span><span class="sxs-lookup"><span data-stu-id="e076c-208">General</span></span>
- <span data-ttu-id="e076c-209">VANLIGA FRÅGOR OCH SVAR</span><span class="sxs-lookup"><span data-stu-id="e076c-209">FAQ</span></span>
- <span data-ttu-id="e076c-210">Ordlista</span><span class="sxs-lookup"><span data-stu-id="e076c-210">Glossary</span></span>
- <span data-ttu-id="e076c-211">Hjälpfil</span><span class="sxs-lookup"><span data-stu-id="e076c-211">HelpFile</span></span>
- <span data-ttu-id="e076c-212">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="e076c-212">ScriptCommand</span></span>
- <span data-ttu-id="e076c-213">Funktion</span><span class="sxs-lookup"><span data-stu-id="e076c-213">Function</span></span>
- <span data-ttu-id="e076c-214">Filtrera</span><span class="sxs-lookup"><span data-stu-id="e076c-214">Filter</span></span>
- <span data-ttu-id="e076c-215">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="e076c-215">ExternalScript</span></span>
- <span data-ttu-id="e076c-216">Alla</span><span class="sxs-lookup"><span data-stu-id="e076c-216">All</span></span>
- <span data-ttu-id="e076c-217">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="e076c-217">DefaultHelp</span></span>
- <span data-ttu-id="e076c-218">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="e076c-218">Workflow</span></span>
- <span data-ttu-id="e076c-219">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="e076c-219">DscResource</span></span>
- <span data-ttu-id="e076c-220">Klass</span><span class="sxs-lookup"><span data-stu-id="e076c-220">Class</span></span>
- <span data-ttu-id="e076c-221">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="e076c-221">Configuration</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Alias, Cmdlet, Provider, General, FAQ, Glossary, HelpFile, ScriptCommand, Function, Filter, ExternalScript, All, DefaultHelp, Workflow, DscResource, Class, Configuration

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e076c-222">– Komponent</span><span class="sxs-lookup"><span data-stu-id="e076c-222">-Component</span></span>

<span data-ttu-id="e076c-223">Visar kommandon med det angivna komponent svärdet, till exempel **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="e076c-223">Displays commands with the specified component value, such as **Exchange**.</span></span> <span data-ttu-id="e076c-224">Ange ett komponent namn.</span><span class="sxs-lookup"><span data-stu-id="e076c-224">Enter a component name.</span></span>
<span data-ttu-id="e076c-225">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e076c-225">Wildcard characters are permitted.</span></span> <span data-ttu-id="e076c-226">Den här parametern har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-226">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e076c-227">-Detaljerad</span><span class="sxs-lookup"><span data-stu-id="e076c-227">-Detailed</span></span>

<span data-ttu-id="e076c-228">Lägger till parameter beskrivningar och exempel i den grundläggande hjälp visningen.</span><span class="sxs-lookup"><span data-stu-id="e076c-228">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="e076c-229">Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="e076c-229">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="e076c-230">Den har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-230">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetailedView
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e076c-231">– Exempel</span><span class="sxs-lookup"><span data-stu-id="e076c-231">-Examples</span></span>

<span data-ttu-id="e076c-232">Visar endast namn, Sammanfattning och exempel.</span><span class="sxs-lookup"><span data-stu-id="e076c-232">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="e076c-233">Om du bara vill visa exemplen skriver du `(Get-Help \<cmdlet-name\>).Examples` .</span><span class="sxs-lookup"><span data-stu-id="e076c-233">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="e076c-234">Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="e076c-234">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="e076c-235">Den har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-235">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Examples
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e076c-236">– Fullständig</span><span class="sxs-lookup"><span data-stu-id="e076c-236">-Full</span></span>

<span data-ttu-id="e076c-237">Visar hela hjälp artikeln för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e076c-237">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="e076c-238">**Fullständig** innehåller parameter beskrivningar och attribut, exempel, indata och utdata och ytterligare anteckningar.</span><span class="sxs-lookup"><span data-stu-id="e076c-238">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="e076c-239">Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="e076c-239">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="e076c-240">Den har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-240">It has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllUsersView
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e076c-241">– Funktioner</span><span class="sxs-lookup"><span data-stu-id="e076c-241">-Functionality</span></span>

<span data-ttu-id="e076c-242">Visar hjälp för objekt med de angivna funktionerna.</span><span class="sxs-lookup"><span data-stu-id="e076c-242">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="e076c-243">Ange funktionerna.</span><span class="sxs-lookup"><span data-stu-id="e076c-243">Enter the functionality.</span></span> <span data-ttu-id="e076c-244">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e076c-244">Wildcard characters are permitted.</span></span> <span data-ttu-id="e076c-245">Den här parametern har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-245">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e076c-246">-Name</span><span class="sxs-lookup"><span data-stu-id="e076c-246">-Name</span></span>

<span data-ttu-id="e076c-247">Hämtar hjälp om det angivna kommandot eller konceptet.</span><span class="sxs-lookup"><span data-stu-id="e076c-247">Gets help about the specified command or concept.</span></span> <span data-ttu-id="e076c-248">Ange namnet på en cmdlet, funktion, Provider, skript eller ett arbets flöde, till exempel `Get-Member` ett konceptuellt artikel namn, till exempel `about_Objects` eller ett alias, till exempel `ls` .</span><span class="sxs-lookup"><span data-stu-id="e076c-248">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="e076c-249">Jokertecken tillåts i cmdlet-och Provider-namn, men du kan inte använda jokertecken för att hitta namnen på hjälp artiklar om funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="e076c-249">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="e076c-250">Om du vill ha hjälp med ett skript som inte finns i en sökväg som anges i `$env:Path` miljövariabeln, anger du Skriptets sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="e076c-250">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="e076c-251">Om du anger det exakta namnet på en hjälp artikel, `Get-Help` visar innehållet i artikeln.</span><span class="sxs-lookup"><span data-stu-id="e076c-251">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="e076c-252">Om du anger ett ord-eller ord mönster som visas i flera hjälp artikel rubriker `Get-Help` visas en lista över matchande rubriker.</span><span class="sxs-lookup"><span data-stu-id="e076c-252">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="e076c-253">Om du anger text som inte matchar någon rubrik för hjälp artiklar, `Get-Help` visar en lista över artiklar som innehåller texten i innehållet.</span><span class="sxs-lookup"><span data-stu-id="e076c-253">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="e076c-254">Namn på konceptuella artiklar, till exempel `about_Objects` , måste anges på engelska, även i icke-engelska versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e076c-254">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e076c-255">– Online</span><span class="sxs-lookup"><span data-stu-id="e076c-255">-Online</span></span>

<span data-ttu-id="e076c-256">Visar onlineversionen av en hjälp artikel i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="e076c-256">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="e076c-257">Den här parametern är endast giltig för hjälp artiklar för cmdlet, Function, Workflow och script.</span><span class="sxs-lookup"><span data-stu-id="e076c-257">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="e076c-258">Du kan inte använda parametern **online** med `Get-Help` i en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="e076c-258">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="e076c-259">Information om hur du får stöd för den här funktionen i hjälp artiklar som du skriver, finns [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)och [stöder onlinehjälp](/powershell/scripting/developer/module/supporting-online-help)och [Skriv hjälp för PowerShell-cmdletar](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="e076c-259">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Online
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e076c-260">-Parameter</span><span class="sxs-lookup"><span data-stu-id="e076c-260">-Parameter</span></span>

<span data-ttu-id="e076c-261">Visar endast de detaljerade beskrivningarna av de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-261">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="e076c-262">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e076c-262">Wildcards are permitted.</span></span> <span data-ttu-id="e076c-263">Den här parametern har ingen påverkan på skärmar med konceptuell ( **About_** ) hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-263">This parameter has no effect on displays of conceptual ( **About_** ) help.</span></span>

```yaml
Type: System.String
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e076c-264">-Path</span><span class="sxs-lookup"><span data-stu-id="e076c-264">-Path</span></span>

<span data-ttu-id="e076c-265">Hämtar hjälp som förklarar hur cmdleten fungerar i den angivna providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="e076c-265">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="e076c-266">Ange en sökväg till PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="e076c-266">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="e076c-267">Den här parametern hämtar en anpassad version av en cmdlets hjälp artikel som förklarar hur cmdleten fungerar i den angivna PowerShell-providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="e076c-267">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="e076c-268">Den här parametern är endast effektiv för hjälp om en provider-cmdlet och bara när providern innehåller en anpassad version av hjälp artikeln Provider-cmdlet i Hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="e076c-268">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="e076c-269">Om du vill använda den här parametern installerar du hjälp filen för modulen som innehåller providern.</span><span class="sxs-lookup"><span data-stu-id="e076c-269">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="e076c-270">Om du vill se en anpassad cmdlet-hjälp för en sökväg för en provider går du till platsen för providerns sökväg och anger ett `Get-Help` kommando eller, från valfri sökväg, använder du parametern **Path** för `Get-Help` att ange providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="e076c-270">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="e076c-271">Du kan också hitta anpassad cmdlet-hjälp online i hjälp avsnitten för providern i hjälp artiklarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-271">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="e076c-272">Mer information om PowerShell-leverantörer finns [about_Providers](./About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="e076c-272">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e076c-273">-Roll</span><span class="sxs-lookup"><span data-stu-id="e076c-273">-Role</span></span>

<span data-ttu-id="e076c-274">Visar anpassad hjälp för den angivna användar rollen.</span><span class="sxs-lookup"><span data-stu-id="e076c-274">Displays help customized for the specified user role.</span></span> <span data-ttu-id="e076c-275">Ange en roll.</span><span class="sxs-lookup"><span data-stu-id="e076c-275">Enter a role.</span></span> <span data-ttu-id="e076c-276">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e076c-276">Wildcard characters are permitted.</span></span>

<span data-ttu-id="e076c-277">Ange den roll som användaren spelar i en organisation.</span><span class="sxs-lookup"><span data-stu-id="e076c-277">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="e076c-278">Vissa cmdletar visar annan text i sina hjälpfiler baserat på värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="e076c-278">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="e076c-279">Den här parametern har ingen inverkan på hjälpen för Core-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e076c-279">This parameter has no effect on help for the core cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e076c-280">-ShowWindow</span><span class="sxs-lookup"><span data-stu-id="e076c-280">-ShowWindow</span></span>

<span data-ttu-id="e076c-281">Visar hjälp avsnittet i ett fönster för enklare läsning.</span><span class="sxs-lookup"><span data-stu-id="e076c-281">Displays the help topic in a window for easier reading.</span></span> <span data-ttu-id="e076c-282">I fönstret **finns en Sök funktion och en** **inställnings** ruta där du kan ange alternativ för visning, inklusive alternativ för att endast Visa valda avsnitt i ett hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="e076c-282">The window includes a **Find** search feature and a **Settings** box that lets you set options for the display, including options to display only selected sections of a help topic.</span></span>

<span data-ttu-id="e076c-283">Parametern **ShowWindow** stöder hjälp avsnitt för kommandon (cmdlets, functions, CIM-kommandon, arbets flöden, skript) och konceptuella **om** artiklar.</span><span class="sxs-lookup"><span data-stu-id="e076c-283">The **ShowWindow** parameter supports help topics for commands (cmdlets, functions, CIM commands, workflows, scripts) and conceptual **About** articles.</span></span> <span data-ttu-id="e076c-284">Den har inte stöd för leverantörs hjälp.</span><span class="sxs-lookup"><span data-stu-id="e076c-284">It does not support provider help.</span></span>

<span data-ttu-id="e076c-285">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e076c-285">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShowWindow
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e076c-286">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e076c-286">CommonParameters</span></span>

<span data-ttu-id="e076c-287">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e076c-287">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e076c-288">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e076c-288">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e076c-289">INDATA</span><span class="sxs-lookup"><span data-stu-id="e076c-289">INPUTS</span></span>

### <span data-ttu-id="e076c-290">Inget</span><span class="sxs-lookup"><span data-stu-id="e076c-290">None</span></span>

<span data-ttu-id="e076c-291">Du kan inte skicka objekt nedåt i pipelinen till `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="e076c-291">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="e076c-292">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e076c-292">OUTPUTS</span></span>

### <span data-ttu-id="e076c-293">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="e076c-293">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="e076c-294">Om du kör `Get-Help` på ett kommando som inte har en hjälp fil `Get-Help` returnerar ett **ExtendedCmdletHelpInfo** -objekt som representerar den automatiskt genererade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e076c-294">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="e076c-295">System. String</span><span class="sxs-lookup"><span data-stu-id="e076c-295">System.String</span></span>

<span data-ttu-id="e076c-296">Om du får en konceptuell hjälp artikel `Get-Help` returneras den som en sträng.</span><span class="sxs-lookup"><span data-stu-id="e076c-296">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="e076c-297">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="e076c-297">MamlCommandHelpInfo</span></span>

<span data-ttu-id="e076c-298">Om du får ett kommando som har en hjälp fil `Get-Help` returnerar ett **MamlCommandHelpInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="e076c-298">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="e076c-299">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e076c-299">NOTES</span></span>

<span data-ttu-id="e076c-300">PowerShell 3,0 innehåller inte hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="e076c-300">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="e076c-301">Använd cmdleten för att ladda ned och installera hjälpfilerna som `Get-Help` läser `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="e076c-301">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="e076c-302">Du kan använda `Update-Help` cmdleten för att hämta och installera hjälpfiler för de kärn kommandon som ingår i PowerShell och för alla moduler som du installerar.</span><span class="sxs-lookup"><span data-stu-id="e076c-302">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="e076c-303">Du kan också använda den för att uppdatera hjälpfilerna så att hjälpen på datorn aldrig är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="e076c-303">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="e076c-304">Du kan också läsa hjälp artiklarna om de kommandon som levereras med PowerShell online från [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e076c-304">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="e076c-305">`Get-Help` Visar hjälp i språk uppsättningen för Windows-operativsystemet eller på reserv språket för det aktuella språket.</span><span class="sxs-lookup"><span data-stu-id="e076c-305">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="e076c-306">Om du inte har hjälpfilerna för primär-eller fallback-språkvarianten `Get-Help` fungerar det som om det inte finns några hjälpfiler på datorn.</span><span class="sxs-lookup"><span data-stu-id="e076c-306">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="e076c-307">Om du vill ha hjälp med ett annat språk kan du använda **region** och **språk** på kontroll panelen för att ändra inställningarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-307">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="e076c-308">På Windows 10, **Inställningar** , **tid & språk**.</span><span class="sxs-lookup"><span data-stu-id="e076c-308">On Windows 10, **Settings** , **Time & Language**.</span></span>

<span data-ttu-id="e076c-309">En fullständig vy över hjälpen innehåller en tabell med information om parametrarna.</span><span class="sxs-lookup"><span data-stu-id="e076c-309">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="e076c-310">Tabellen innehåller följande fält:</span><span class="sxs-lookup"><span data-stu-id="e076c-310">The table includes the following fields:</span></span>

- <span data-ttu-id="e076c-311">**Krävs**.</span><span class="sxs-lookup"><span data-stu-id="e076c-311">**Required**.</span></span> <span data-ttu-id="e076c-312">Anger om parametern är obligatorisk (sant) eller valfri (falskt).</span><span class="sxs-lookup"><span data-stu-id="e076c-312">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="e076c-313">**Position**.</span><span class="sxs-lookup"><span data-stu-id="e076c-313">**Position**.</span></span> <span data-ttu-id="e076c-314">Anger om parametern är namngiven eller position (numerisk).</span><span class="sxs-lookup"><span data-stu-id="e076c-314">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="e076c-315">Positions parametrar måste finnas på en angiven plats i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e076c-315">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="e076c-316">**Namngiven** anger att parameter namnet är obligatoriskt, men att parametern kan visas var som helst i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e076c-316">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="e076c-317">**Numeriskt** anger att parameter namnet är valfritt, men när namnet utelämnas måste parametern vara på den plats som anges i numret.</span><span class="sxs-lookup"><span data-stu-id="e076c-317">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="e076c-318">Anger till exempel `2` att om parameter namnet utelämnas måste parametern vara den andra eller enda namnlös parameter i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e076c-318">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="e076c-319">När parameter namnet används kan parametern visas var som helst i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e076c-319">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="e076c-320">**Standardvärde**.</span><span class="sxs-lookup"><span data-stu-id="e076c-320">**Default value**.</span></span> <span data-ttu-id="e076c-321">Parametervärdet eller standard beteendet som används i PowerShell om du inte inkluderar parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="e076c-321">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="e076c-322">Accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="e076c-322">Accepts pipeline input.</span></span> <span data-ttu-id="e076c-323">Anger om du kan (sant) eller inte (falskt) skicka objekt till parametern via en pipeline.</span><span class="sxs-lookup"><span data-stu-id="e076c-323">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="e076c-324">**Efter egenskaps namn** betyder det att det pipelinade objektet måste ha en egenskap som har samma namn som parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="e076c-324">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="e076c-325">**Accepterar jokertecken**.</span><span class="sxs-lookup"><span data-stu-id="e076c-325">**Accepts wildcard characters**.</span></span> <span data-ttu-id="e076c-326">Anger om värdet för en parameter kan innehålla jokertecken, till exempel en asterisk ( `*` ) eller frågetecken ( `?` ).</span><span class="sxs-lookup"><span data-stu-id="e076c-326">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="e076c-327">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e076c-327">RELATED LINKS</span></span>

[<span data-ttu-id="e076c-328">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="e076c-328">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="e076c-329">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="e076c-329">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="e076c-330">Get-Command</span><span class="sxs-lookup"><span data-stu-id="e076c-330">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="e076c-331">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="e076c-331">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="e076c-332">Uppdatera – hjälp</span><span class="sxs-lookup"><span data-stu-id="e076c-332">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="e076c-333">Skriva kommentarsbaserade hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="e076c-333">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="e076c-334">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="e076c-334">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)
