---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-help?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Help
ms.openlocfilehash: 82721b3d079c795e0ce6fcae1fba0eab93344b52
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709181"
---
# <span data-ttu-id="0eae8-102">Get-Help</span><span class="sxs-lookup"><span data-stu-id="0eae8-102">Get-Help</span></span>

## <span data-ttu-id="0eae8-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0eae8-103">SYNOPSIS</span></span>
<span data-ttu-id="0eae8-104">Visar information om PowerShell-kommandon och-koncept.</span><span class="sxs-lookup"><span data-stu-id="0eae8-104">Displays information about PowerShell commands and concepts.</span></span>

## <span data-ttu-id="0eae8-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0eae8-105">SYNTAX</span></span>

### <span data-ttu-id="0eae8-106">AllUsersView (standard)</span><span class="sxs-lookup"><span data-stu-id="0eae8-106">AllUsersView (Default)</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Full] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0eae8-107">DetailedView</span><span class="sxs-lookup"><span data-stu-id="0eae8-107">DetailedView</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Detailed
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0eae8-108">Exempel</span><span class="sxs-lookup"><span data-stu-id="0eae8-108">Examples</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Examples
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0eae8-109">Parameters (Parametrar)</span><span class="sxs-lookup"><span data-stu-id="0eae8-109">Parameters</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] -Parameter <String[]>
 [-Component <String[]>] [-Functionality <String[]>] [-Role <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="0eae8-110">Online</span><span class="sxs-lookup"><span data-stu-id="0eae8-110">Online</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -Online [<CommonParameters>]
```

### <span data-ttu-id="0eae8-111">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="0eae8-111">ShowWindow</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>]
 [-Functionality <String[]>] [-Role <String[]>] -ShowWindow [<CommonParameters>]
```

## <span data-ttu-id="0eae8-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0eae8-112">DESCRIPTION</span></span>

<span data-ttu-id="0eae8-113">`Get-Help`Cmdleten visar information om PowerShell-begrepp och kommandon, inklusive cmdlets, functions, Common Information Model (CIM), arbets flöden, providers, alias och skript.</span><span class="sxs-lookup"><span data-stu-id="0eae8-113">The `Get-Help` cmdlet displays information about PowerShell concepts and commands, including cmdlets, functions, Common Information Model (CIM) commands, workflows, providers, aliases, and scripts.</span></span>

<span data-ttu-id="0eae8-114">Om du vill ha hjälp med en PowerShell-cmdlet skriver du `Get-Help` följt av cmdlet-namnet, t `Get-Help Get-Process` . ex.:.</span><span class="sxs-lookup"><span data-stu-id="0eae8-114">To get help for a PowerShell cmdlet, type `Get-Help` followed by the cmdlet name, such as: `Get-Help Get-Process`.</span></span>

<span data-ttu-id="0eae8-115">Konceptuell hjälp artiklar i PowerShell börjar med **about_**, till exempel **about_Comparison_Operators**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-115">Conceptual help articles in PowerShell begin with **about_**, such as **about_Comparison_Operators**.</span></span> <span data-ttu-id="0eae8-116">Om du vill se alla **about_** artiklar skriver du `Get-Help about_*` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-116">To see all **about_** articles, type `Get-Help about_*`.</span></span> <span data-ttu-id="0eae8-117">Om du vill se en viss artikel skriver du `Get-Help about_<article-name>` , till exempel `Get-Help about_Comparison_Operators` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-117">To see a particular article, type `Get-Help about_<article-name>`, such as `Get-Help about_Comparison_Operators`.</span></span>

<span data-ttu-id="0eae8-118">Om du vill ha hjälp med en PowerShell-Provider skriver du `Get-Help` följt av namnet på providern.</span><span class="sxs-lookup"><span data-stu-id="0eae8-118">To get help for a PowerShell provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="0eae8-119">Om du till exempel vill få hjälp med certifikat leverantören skriver du `Get-Help Certificate` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-119">For example, to get help for the Certificate provider, type `Get-Help Certificate`.</span></span>

<span data-ttu-id="0eae8-120">Du kan också skriva `help` eller `man` , som visar en skärm med text i taget.</span><span class="sxs-lookup"><span data-stu-id="0eae8-120">You can also type `help` or `man`, which displays one screen of text at a time.</span></span> <span data-ttu-id="0eae8-121">Eller, `<cmdlet-name> -?` som är identisk med `Get-Help` , men endast fungerar för-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-121">Or, `<cmdlet-name> -?`, that is identical to `Get-Help`, but only works for cmdlets.</span></span>

<span data-ttu-id="0eae8-122">`Get-Help` hämtar hjälp innehållet som det visar från hjälp filer på din dator.</span><span class="sxs-lookup"><span data-stu-id="0eae8-122">`Get-Help` gets the help content that it displays from help files on your computer.</span></span> <span data-ttu-id="0eae8-123">Utan hjälpfilerna `Get-Help` visar endast grundläggande information om cmdletar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-123">Without the help files, `Get-Help` displays only basic information about cmdlets.</span></span> <span data-ttu-id="0eae8-124">Några PowerShell-moduler innehåller hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="0eae8-124">Some PowerShell modules include help files.</span></span> <span data-ttu-id="0eae8-125">Från och med PowerShell 3,0 innehåller modulerna som medföljer operativ systemet Windows inte hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-125">Beginning in PowerShell 3.0, the modules that come with the Windows operating system don't include help files.</span></span> <span data-ttu-id="0eae8-126">Om du vill hämta eller uppdatera hjälpfilerna för en modul i PowerShell 3,0 använder du `Update-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0eae8-126">To download or update the help files for a module in PowerShell 3.0, use the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="0eae8-127">Du kan också Visa PowerShell-hjälp dokument online i Microsoft Docs. Om du vill hämta online-versionen av en hjälpfil använder du parametern **online** , t. ex `Get-Help Get-Process -Online` .:.</span><span class="sxs-lookup"><span data-stu-id="0eae8-127">You can also view the PowerShell help documents online in the Microsoft Docs. To get the online version of a help file, use the **Online** parameter, such as: `Get-Help Get-Process -Online`.</span></span> <span data-ttu-id="0eae8-128">Läs mer om PowerShell-dokumentationen i Microsoft Docs PowerShell- [dokumentationen](/powershell).</span><span class="sxs-lookup"><span data-stu-id="0eae8-128">To read all the PowerShell documentation, see the Microsoft Docs [PowerShell Documentation](/powershell).</span></span>

<span data-ttu-id="0eae8-129">Om du skriver `Get-Help` följt av det exakta namnet på en hjälp artikel, eller ett ord som är unikt för en hjälp artikel, `Get-Help` visar artikelns innehåll.</span><span class="sxs-lookup"><span data-stu-id="0eae8-129">If you type `Get-Help` followed by the exact name of a help article, or by a word unique to a help article, `Get-Help` displays the article's content.</span></span> <span data-ttu-id="0eae8-130">Om du anger det exakta namnet på ett kommando alias `Get-Help` visar hjälpen för det ursprungliga kommandot.</span><span class="sxs-lookup"><span data-stu-id="0eae8-130">If you specify the exact name of a command alias, `Get-Help` displays the help for the original command.</span></span> <span data-ttu-id="0eae8-131">Om du anger ett ord-eller ord mönster som visas i flera hjälp artikel rubriker `Get-Help` visas en lista över matchande rubriker.</span><span class="sxs-lookup"><span data-stu-id="0eae8-131">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span> <span data-ttu-id="0eae8-132">Om du anger text som inte visas i någon hjälp artikel titlar, `Get-Help` visar en lista över artiklar som innehåller texten i innehållet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-132">If you enter any text that doesn't appear in any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="0eae8-133">`Get-Help` kan få hjälp artiklar för alla språk som stöds och nationella inställningar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-133">`Get-Help` can get help articles for all supported languages and locales.</span></span> <span data-ttu-id="0eae8-134">`Get-Help` börja med att leta efter hjälpfiler i språk uppsättningen för Windows och sedan i det överordnade språket, till exempel **PT** för **pt-br**, och sedan i ett återställnings språk.</span><span class="sxs-lookup"><span data-stu-id="0eae8-134">`Get-Help` first looks for help files in the locale set for Windows, then in the parent locale, such as **pt** for **pt-BR**, and then in a fallback locale.</span></span> <span data-ttu-id="0eae8-135">Från och med PowerShell 3,0, om det `Get-Help` inte finns hjälp i reserv språket, söker det efter hjälp artiklar på engelska, **en-US**, innan det returnerar ett fel meddelande eller visar automatiskt genererad hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-135">Beginning in PowerShell 3.0, if `Get-Help` doesn't find help in the fallback locale, it looks for help articles in English, **en-US**, before it returns an error message or displaying autogenerated help.</span></span>

<span data-ttu-id="0eae8-136">Information om symbolerna som `Get-Help` visas i syntaxen för kommandosyntaxen finns [about_Command_Syntax](./About/about_Command_Syntax.md).</span><span class="sxs-lookup"><span data-stu-id="0eae8-136">For information about the symbols that `Get-Help` displays in the command syntax diagram, see [about_Command_Syntax](./About/about_Command_Syntax.md).</span></span>
<span data-ttu-id="0eae8-137">Information om attributvärden, till exempel **obligatorisk** och **Position**, finns [about_Parameters](./About/about_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0eae8-137">For information about parameter attributes, such as **Required** and **Position**, see [about_Parameters](./About/about_Parameters.md).</span></span>

>[!NOTE]
> <span data-ttu-id="0eae8-138">I PowerShell 3,0 och PowerShell 4,0 `Get-Help` går det inte  att hitta artiklar i moduler om modulen inte har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-138">In PowerShell 3.0 and PowerShell 4.0, `Get-Help` can't find **About** articles in modules unless the module is imported into the current session.</span></span> <span data-ttu-id="0eae8-139">Detta är ett känt problem.</span><span class="sxs-lookup"><span data-stu-id="0eae8-139">This is a known issue.</span></span> <span data-ttu-id="0eae8-140">**Om** du vill hämta artiklar i en modul importerar du modulen antingen med hjälp av `Import-Module` cmdleten eller genom att köra en cmdlet som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-140">To get **About** articles in a module, import the module, either by using the `Import-Module` cmdlet or by running a cmdlet that's included in the module.</span></span>

## <span data-ttu-id="0eae8-141">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0eae8-141">EXAMPLES</span></span>

### <span data-ttu-id="0eae8-142">Exempel 1: Visa grundläggande hjälp information om en cmdlet</span><span class="sxs-lookup"><span data-stu-id="0eae8-142">Example 1: Display basic help information about a cmdlet</span></span>

<span data-ttu-id="0eae8-143">I de här exemplen visas grundläggande hjälp information om `Format-Table` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0eae8-143">These examples display basic help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table
Get-Help -Name Format-Table
Format-Table -?
```

<span data-ttu-id="0eae8-144">`Get-Help <cmdlet-name>` är den enklaste och standardsyntaxen för `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-144">`Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet.</span></span> <span data-ttu-id="0eae8-145">Du kan utelämna parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="0eae8-145">You can omit the **Name** parameter.</span></span>

<span data-ttu-id="0eae8-146">Syntaxen `<cmdlet-name> -?` fungerar bara för-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-146">The syntax `<cmdlet-name> -?` works only for cmdlets.</span></span>

### <span data-ttu-id="0eae8-147">Exempel 2: Visa grundläggande information en sida i taget</span><span class="sxs-lookup"><span data-stu-id="0eae8-147">Example 2: Display basic information one page at a time</span></span>

<span data-ttu-id="0eae8-148">I de här exemplen visas grundläggande hjälp information om `Format-Table` cmdleten en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="0eae8-148">These examples display basic help information about the `Format-Table` cmdlet one page at a time.</span></span>

```powershell
help Format-Table
man Format-Table
Get-Help Format-Table | Out-Host -Paging
```

<span data-ttu-id="0eae8-149">`help` är en funktion som kör `Get-Help` cmdlet internt och visar resultatet en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="0eae8-149">`help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.</span></span>

<span data-ttu-id="0eae8-150">`man` är ett alias för `help` funktionen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-150">`man` is an alias for the `help` function.</span></span>

<span data-ttu-id="0eae8-151">`Get-Help Format-Table` skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-151">`Get-Help Format-Table` sends the object down the pipeline.</span></span> <span data-ttu-id="0eae8-152">`Out-Host -Paging` tar emot utdata från pipelinen och visar en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="0eae8-152">`Out-Host -Paging` receives the output from the pipeline and displays it one page at a time.</span></span> <span data-ttu-id="0eae8-153">Mer information finns i [out-Host](Out-Host.md).</span><span class="sxs-lookup"><span data-stu-id="0eae8-153">For more information, see [Out-Host](Out-Host.md).</span></span>

### <span data-ttu-id="0eae8-154">Exempel 3: Visa mer information om en cmdlet</span><span class="sxs-lookup"><span data-stu-id="0eae8-154">Example 3: Display more information for a cmdlet</span></span>

<span data-ttu-id="0eae8-155">I de här exemplen visas mer detaljerad hjälp information om `Format-Table` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0eae8-155">These examples display more detailed help information about the `Format-Table` cmdlet.</span></span>

```powershell
Get-Help Format-Table -Detailed
Get-Help Format-Table -Full
```

<span data-ttu-id="0eae8-156">Den **detaljerade** parametern visar hjälp artikelns detaljerade vy som innehåller parameter beskrivningar och exempel.</span><span class="sxs-lookup"><span data-stu-id="0eae8-156">The **Detailed** parameter displays the help article's detailed view that includes parameter descriptions and examples.</span></span>

<span data-ttu-id="0eae8-157">Den **fullständiga** parametern visar hjälp artikelns fullständiga vy som innehåller parameter beskrivningar, exempel, indata och utdata för objekt och ytterligare anteckningar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-157">The **Full** parameter displays the help article's full view that includes parameter descriptions, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="0eae8-158">De **detaljerade** och **fullständiga** parametrarna gäller endast för kommandon som har hjälpfiler installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-158">The **Detailed** and **Full** parameters are effective only for the commands that have help files installed on the computer.</span></span> <span data-ttu-id="0eae8-159">Parametrarna gäller inte för de konceptuella (**about_**) hjälp artiklarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-159">The parameters aren't effective for the conceptual (**about_**) help articles.</span></span>

### <span data-ttu-id="0eae8-160">Exempel 4: Visa valda delar av en cmdlet med hjälp av parametrar</span><span class="sxs-lookup"><span data-stu-id="0eae8-160">Example 4: Display selected parts of a cmdlet by using parameters</span></span>

<span data-ttu-id="0eae8-161">I de här exemplen visas valda delar av `Format-Table` cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-161">These examples display selected portions of the `Format-Table` cmdlet help.</span></span>

```powershell
Get-Help Format-Table -Examples
Get-Help Format-Table -Parameter *
Get-Help Format-Table -Parameter GroupBy
```

<span data-ttu-id="0eae8-162">I **exempel** parametern visas hjälp filens **namn** och **sammanfattnings** avsnitt och alla exempel.</span><span class="sxs-lookup"><span data-stu-id="0eae8-162">The **Examples** parameter displays the help file's **NAME** and **SYNOPSIS** sections, and all the Examples.</span></span> <span data-ttu-id="0eae8-163">Du kan inte ange ett exempel nummer eftersom **exempel** parametern är en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="0eae8-163">You can't specify an Example number because the **Examples** parameter is a switch parameter.</span></span>

<span data-ttu-id="0eae8-164">**Parametern parameter** visar bara beskrivningarna av de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-164">The **Parameter** parameter displays only the descriptions of the specified parameters.</span></span> <span data-ttu-id="0eae8-165">Om du bara anger jokertecknet asterisk ( `*` ) visas beskrivningarna för alla parametrar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-165">If you specify only the asterisk (`*`) wildcard character, it displays the descriptions of all parameters.</span></span>
<span data-ttu-id="0eae8-166">När **parametern** anger ett parameter namn, till exempel **groupby**, visas information om den parametern.</span><span class="sxs-lookup"><span data-stu-id="0eae8-166">When **Parameter** specifies a parameter name such as **GroupBy**, information about that parameter is shown.</span></span>

<span data-ttu-id="0eae8-167">Dessa parametrar är inte effektiva för de konceptuella (**about_**) hjälp artiklarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-167">These parameters aren't effective for the conceptual (**about_**) help articles.</span></span>

### <span data-ttu-id="0eae8-168">Exempel 5: Visa onlineversionen av hjälp</span><span class="sxs-lookup"><span data-stu-id="0eae8-168">Example 5: Display online version of help</span></span>

<span data-ttu-id="0eae8-169">I det här exemplet visas onlineversionen av hjälp artikeln för `Format-Table` cmdleten i din standard webbläsare.</span><span class="sxs-lookup"><span data-stu-id="0eae8-169">This example displays the online version of the help article for the `Format-Table` cmdlet in your default web browser.</span></span>

```powershell
Get-Help Format-Table -Online
```

### <span data-ttu-id="0eae8-170">Exempel 6: Visa hjälp om hjälp systemet</span><span class="sxs-lookup"><span data-stu-id="0eae8-170">Example 6: Display help about the help system</span></span>

<span data-ttu-id="0eae8-171">`Get-Help`Cmdlet utan parametrar visar information om PowerShell-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-171">The `Get-Help` cmdlet without parameters displays information about the PowerShell help system.</span></span>

```powershell
Get-Help
```

### <span data-ttu-id="0eae8-172">Exempel 7: Visa tillgängliga hjälp artiklar</span><span class="sxs-lookup"><span data-stu-id="0eae8-172">Example 7: Display available help articles</span></span>

<span data-ttu-id="0eae8-173">I det här exemplet visas en lista över alla hjälp artiklar som är tillgängliga på din dator.</span><span class="sxs-lookup"><span data-stu-id="0eae8-173">This example displays a list of all help articles available on your computer.</span></span>

```powershell
Get-Help *
```

### <span data-ttu-id="0eae8-174">Exempel 8: Visa en lista med konceptuella artiklar</span><span class="sxs-lookup"><span data-stu-id="0eae8-174">Example 8: Display a list of conceptual articles</span></span>

<span data-ttu-id="0eae8-175">I det här exemplet visas en lista över de konceptuella artiklarna som ingår i PowerShell-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-175">This example displays a list of the conceptual articles included in PowerShell help.</span></span> <span data-ttu-id="0eae8-176">Alla dessa artiklar börjar med de tecken som **about_**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-176">All these articles begin with the characters **about_**.</span></span> <span data-ttu-id="0eae8-177">Om du vill visa en viss hjälp fil skriver du till `Get-Help \<about_article-name\>` exempel `Get-Help about_Signing` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-177">To display a particular help file, type `Get-Help \<about_article-name\>`, for example, `Get-Help about_Signing`.</span></span>

<span data-ttu-id="0eae8-178">Endast de konceptuella artiklarna som innehåller hjälpfiler som är installerade på datorn visas.</span><span class="sxs-lookup"><span data-stu-id="0eae8-178">Only the conceptual articles that have help files installed on your computer are displayed.</span></span> <span data-ttu-id="0eae8-179">Information om hur du hämtar och installerar hjälpfiler i PowerShell 3,0 finns i [Update-Help](Update-Help.md).</span><span class="sxs-lookup"><span data-stu-id="0eae8-179">For information about downloading and installing help files in PowerShell 3.0, see [Update-Help](Update-Help.md).</span></span>

```powershell
Get-Help about_*
```

### <span data-ttu-id="0eae8-180">Exempel 9: Sök efter ett ord i cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="0eae8-180">Example 9: Search for a word in cmdlet help</span></span>

<span data-ttu-id="0eae8-181">Det här exemplet visar hur du söker efter ett ord i en hjälp artikel för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-181">This example shows how to search for a word in a cmdlet help article.</span></span>

```powershell
Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml
```

```Output
the Export-Clixml cmdlet to save the instance of the object, including the additional members...
can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
Export-Clixml
Import-Clixml
```

<span data-ttu-id="0eae8-182">`Get-Help` använder den **fullständiga** parametern för att få hjälp information för `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-182">`Get-Help` uses the **Full** parameter to get help information for `Add-Member`.</span></span> <span data-ttu-id="0eae8-183">**MamlCommandHelpInfo** -objektet skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-183">The **MamlCommandHelpInfo** object is sent down the pipeline.</span></span> <span data-ttu-id="0eae8-184">`Out-String` använder **Stream** -parametern för att konvertera objektet till en sträng.</span><span class="sxs-lookup"><span data-stu-id="0eae8-184">`Out-String` uses the **Stream** parameter to convert the object into a string.</span></span> <span data-ttu-id="0eae8-185">`Select-String` använder **mönster** parametern för att söka i strängen efter **CliXml**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-185">`Select-String` uses the **Pattern** parameter to search the string for **Clixml**.</span></span>

### <span data-ttu-id="0eae8-186">Exempel 10: Visa en lista över artiklar som innehåller ett ord</span><span class="sxs-lookup"><span data-stu-id="0eae8-186">Example 10: Display a list of articles that include a word</span></span>

<span data-ttu-id="0eae8-187">I det här exemplet visas en lista över artiklar som innehåller Word- **fjärrkommunikation**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-187">This example displays a list of articles that include the word **remoting**.</span></span>

<span data-ttu-id="0eae8-188">När du anger ett ord som inte visas i någon artikel rubrik, `Get-Help` visar en lista över artiklar som innehåller ordet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-188">When you enter a word that doesn't appear in any article title, `Get-Help` displays a list of articles that include that word.</span></span>

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

### <span data-ttu-id="0eae8-189">Exempel 11: Visa leverantörsspecifik hjälp</span><span class="sxs-lookup"><span data-stu-id="0eae8-189">Example 11: Display provider-specific help</span></span>

<span data-ttu-id="0eae8-190">I det här exemplet visas två sätt att hämta den providerspecifika hjälpen för `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-190">This example shows two ways of getting the provider-specific help for `Get-Item`.</span></span> <span data-ttu-id="0eae8-191">De här kommandona får hjälp som förklarar hur du använder `Get-Item` cmdleten i PowerShell-SQL Server-providerns **DataCollection** -nod.</span><span class="sxs-lookup"><span data-stu-id="0eae8-191">These commands get help that explains how to use the `Get-Item` cmdlet in the PowerShell SQL Server provider's **DataCollection** node.</span></span>

<span data-ttu-id="0eae8-192">I det första exemplet används `Get-Help` parametern **Path** för att ange SQL Server providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="0eae8-192">The first example uses the `Get-Help` **Path** parameter to specify the SQL Server provider's path.</span></span>
<span data-ttu-id="0eae8-193">Eftersom providerns sökväg har angetts kan du köra kommandot från alla Sök vägs platser.</span><span class="sxs-lookup"><span data-stu-id="0eae8-193">Because the provider's path is specified, you can run the command from any path location.</span></span>

<span data-ttu-id="0eae8-194">Det andra exemplet använder `Set-Location` för att navigera till SQL Server leverantörs sökväg.</span><span class="sxs-lookup"><span data-stu-id="0eae8-194">The second example uses `Set-Location` to navigate to the SQL Server provider's path.</span></span> <span data-ttu-id="0eae8-195">Från den platsen behövs inte **Sök vägs** parametern för `Get-Help` att hämta den providerspecifika hjälpen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-195">From that location, the **Path** parameter isn't needed for `Get-Help` to get the provider-specific help.</span></span>

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

### <span data-ttu-id="0eae8-196">Exempel 12: Visa hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="0eae8-196">Example 12: Display help for a script</span></span>

<span data-ttu-id="0eae8-197">I det här exemplet får du hjälp med `MyScript.ps1 script` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-197">This example gets help for the `MyScript.ps1 script`.</span></span> <span data-ttu-id="0eae8-198">Information om hur du skriver hjälp för dina funktioner och skript finns [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="0eae8-198">For information about how to write help for your functions and scripts, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md).</span></span>

```powershell
Get-Help -Name C:\PS-Test\MyScript.ps1
```

## <span data-ttu-id="0eae8-199">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0eae8-199">PARAMETERS</span></span>

### <span data-ttu-id="0eae8-200">– Kategori</span><span class="sxs-lookup"><span data-stu-id="0eae8-200">-Category</span></span>

<span data-ttu-id="0eae8-201">Visar hjälp endast för objekt i den angivna kategorin och deras alias.</span><span class="sxs-lookup"><span data-stu-id="0eae8-201">Displays help only for items in the specified category and their aliases.</span></span> <span data-ttu-id="0eae8-202">Konceptuella artiklar finns i kategorin **Hjälpfil** .</span><span class="sxs-lookup"><span data-stu-id="0eae8-202">Conceptual articles are in the **HelpFile** category.</span></span>

<span data-ttu-id="0eae8-203">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="0eae8-203">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="0eae8-204">Alias</span><span class="sxs-lookup"><span data-stu-id="0eae8-204">Alias</span></span>
- <span data-ttu-id="0eae8-205">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0eae8-205">Cmdlet</span></span>
- <span data-ttu-id="0eae8-206">Leverantör</span><span class="sxs-lookup"><span data-stu-id="0eae8-206">Provider</span></span>
- <span data-ttu-id="0eae8-207">Allmänt</span><span class="sxs-lookup"><span data-stu-id="0eae8-207">General</span></span>
- <span data-ttu-id="0eae8-208">VANLIGA FRÅGOR OCH SVAR</span><span class="sxs-lookup"><span data-stu-id="0eae8-208">FAQ</span></span>
- <span data-ttu-id="0eae8-209">Ordlista</span><span class="sxs-lookup"><span data-stu-id="0eae8-209">Glossary</span></span>
- <span data-ttu-id="0eae8-210">Hjälpfil</span><span class="sxs-lookup"><span data-stu-id="0eae8-210">HelpFile</span></span>
- <span data-ttu-id="0eae8-211">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="0eae8-211">ScriptCommand</span></span>
- <span data-ttu-id="0eae8-212">Funktion</span><span class="sxs-lookup"><span data-stu-id="0eae8-212">Function</span></span>
- <span data-ttu-id="0eae8-213">Filtrera</span><span class="sxs-lookup"><span data-stu-id="0eae8-213">Filter</span></span>
- <span data-ttu-id="0eae8-214">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="0eae8-214">ExternalScript</span></span>
- <span data-ttu-id="0eae8-215">Alla</span><span class="sxs-lookup"><span data-stu-id="0eae8-215">All</span></span>
- <span data-ttu-id="0eae8-216">DefaultHelp</span><span class="sxs-lookup"><span data-stu-id="0eae8-216">DefaultHelp</span></span>
- <span data-ttu-id="0eae8-217">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="0eae8-217">Workflow</span></span>
- <span data-ttu-id="0eae8-218">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="0eae8-218">DscResource</span></span>
- <span data-ttu-id="0eae8-219">Klass</span><span class="sxs-lookup"><span data-stu-id="0eae8-219">Class</span></span>
- <span data-ttu-id="0eae8-220">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="0eae8-220">Configuration</span></span>

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

### <span data-ttu-id="0eae8-221">– Komponent</span><span class="sxs-lookup"><span data-stu-id="0eae8-221">-Component</span></span>

<span data-ttu-id="0eae8-222">Visar kommandon med det angivna komponent svärdet, till exempel **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-222">Displays commands with the specified component value, such as **Exchange**.</span></span> <span data-ttu-id="0eae8-223">Ange ett komponent namn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-223">Enter a component name.</span></span>
<span data-ttu-id="0eae8-224">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-224">Wildcard characters are permitted.</span></span> <span data-ttu-id="0eae8-225">Den här parametern har ingen påverkan på skärmar med konceptuell (**About_**) hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-225">This parameter has no effect on displays of conceptual (**About_**) help.</span></span>

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

### <span data-ttu-id="0eae8-226">-Detaljerad</span><span class="sxs-lookup"><span data-stu-id="0eae8-226">-Detailed</span></span>

<span data-ttu-id="0eae8-227">Lägger till parameter beskrivningar och exempel i den grundläggande hjälp visningen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-227">Adds parameter descriptions and examples to the basic help display.</span></span> <span data-ttu-id="0eae8-228">Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-228">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="0eae8-229">Den har ingen påverkan på skärmar med konceptuell (**About_**) hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-229">It has no effect on displays of conceptual (**About_**) help.</span></span>

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

### <span data-ttu-id="0eae8-230">– Exempel</span><span class="sxs-lookup"><span data-stu-id="0eae8-230">-Examples</span></span>

<span data-ttu-id="0eae8-231">Visar endast namn, Sammanfattning och exempel.</span><span class="sxs-lookup"><span data-stu-id="0eae8-231">Displays only the name, synopsis, and examples.</span></span> <span data-ttu-id="0eae8-232">Om du bara vill visa exemplen skriver du `(Get-Help \<cmdlet-name\>).Examples` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-232">To display only the examples, type `(Get-Help \<cmdlet-name\>).Examples`.</span></span>

<span data-ttu-id="0eae8-233">Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-233">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="0eae8-234">Den har ingen påverkan på skärmar med konceptuell (**About_**) hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-234">It has no effect on displays of conceptual (**About_**) help.</span></span>

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

### <span data-ttu-id="0eae8-235">– Fullständig</span><span class="sxs-lookup"><span data-stu-id="0eae8-235">-Full</span></span>

<span data-ttu-id="0eae8-236">Visar hela hjälp artikeln för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-236">Displays the entire help article for a cmdlet.</span></span> <span data-ttu-id="0eae8-237">**Fullständig** innehåller parameter beskrivningar och attribut, exempel, indata och utdata och ytterligare anteckningar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-237">**Full** includes parameter descriptions and attributes, examples, input and output object types, and additional notes.</span></span>

<span data-ttu-id="0eae8-238">Den här parametern är endast effektiv när hjälpfilerna är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-238">This parameter is effective only when the help files are installed on the computer.</span></span> <span data-ttu-id="0eae8-239">Den har ingen påverkan på skärmar med konceptuell (**About_**) hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-239">It has no effect on displays of conceptual (**About_**) help.</span></span>

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

### <span data-ttu-id="0eae8-240">– Funktioner</span><span class="sxs-lookup"><span data-stu-id="0eae8-240">-Functionality</span></span>

<span data-ttu-id="0eae8-241">Visar hjälp för objekt med de angivna funktionerna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-241">Displays help for items with the specified functionality.</span></span> <span data-ttu-id="0eae8-242">Ange funktionerna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-242">Enter the functionality.</span></span> <span data-ttu-id="0eae8-243">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-243">Wildcard characters are permitted.</span></span> <span data-ttu-id="0eae8-244">Den här parametern har ingen påverkan på skärmar med konceptuell (**About_**) hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-244">This parameter has no effect on displays of conceptual (**About_**) help.</span></span>

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

### <span data-ttu-id="0eae8-245">-Name</span><span class="sxs-lookup"><span data-stu-id="0eae8-245">-Name</span></span>

<span data-ttu-id="0eae8-246">Hämtar hjälp om det angivna kommandot eller konceptet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-246">Gets help about the specified command or concept.</span></span> <span data-ttu-id="0eae8-247">Ange namnet på en cmdlet, funktion, Provider, skript eller ett arbets flöde, till exempel `Get-Member` ett konceptuellt artikel namn, till exempel `about_Objects` eller ett alias, till exempel `ls` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-247">Enter the name of a cmdlet, function, provider, script, or workflow, such as `Get-Member`, a conceptual article name, such as `about_Objects`, or an alias, such as `ls`.</span></span> <span data-ttu-id="0eae8-248">Jokertecken tillåts i cmdlet-och Provider-namn, men du kan inte använda jokertecken för att hitta namnen på hjälp artiklar om funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="0eae8-248">Wildcard characters are permitted in cmdlet and provider names, but you can't use wildcard characters to find the names of function help and script help articles.</span></span>

<span data-ttu-id="0eae8-249">Om du vill ha hjälp med ett skript som inte finns i en sökväg som anges i `$env:Path` miljövariabeln, anger du Skriptets sökväg och fil namn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-249">To get help for a script that isn't located in a path that's listed in the `$env:Path` environment variable, type the script's path and file name.</span></span>

<span data-ttu-id="0eae8-250">Om du anger det exakta namnet på en hjälp artikel, `Get-Help` visar innehållet i artikeln.</span><span class="sxs-lookup"><span data-stu-id="0eae8-250">If you enter the exact name of a help article, `Get-Help` displays the article contents.</span></span>

<span data-ttu-id="0eae8-251">Om du anger ett ord-eller ord mönster som visas i flera hjälp artikel rubriker `Get-Help` visas en lista över matchande rubriker.</span><span class="sxs-lookup"><span data-stu-id="0eae8-251">If you enter a word or word pattern that appears in several help article titles, `Get-Help` displays a list of the matching titles.</span></span>

<span data-ttu-id="0eae8-252">Om du anger text som inte matchar någon rubrik för hjälp artiklar, `Get-Help` visar en lista över artiklar som innehåller texten i innehållet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-252">If you enter any text that doesn't match any help article titles, `Get-Help` displays a list of articles that include that text in their contents.</span></span>

<span data-ttu-id="0eae8-253">Namn på konceptuella artiklar, till exempel `about_Objects` , måste anges på engelska, även i icke-engelska versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0eae8-253">The names of conceptual articles, such as `about_Objects`, must be entered in English, even in non-English versions of PowerShell.</span></span>

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

### <span data-ttu-id="0eae8-254">– Online</span><span class="sxs-lookup"><span data-stu-id="0eae8-254">-Online</span></span>

<span data-ttu-id="0eae8-255">Visar onlineversionen av en hjälp artikel i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="0eae8-255">Displays the online version of a help article in the default browser.</span></span> <span data-ttu-id="0eae8-256">Den här parametern är endast giltig för hjälp artiklar för cmdlet, Function, Workflow och script.</span><span class="sxs-lookup"><span data-stu-id="0eae8-256">This parameter is valid only for cmdlet, function, workflow, and script help articles.</span></span> <span data-ttu-id="0eae8-257">Du kan inte använda parametern **online** med `Get-Help` i en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="0eae8-257">You can't use the **Online** parameter with `Get-Help` in a remote session.</span></span>

<span data-ttu-id="0eae8-258">Information om hur du får stöd för den här funktionen i hjälp artiklar som du skriver, finns [about_Comment_Based_Help](./About/about_Comment_Based_Help.md)och [stöder onlinehjälp](/powershell/scripting/developer/module/supporting-online-help)och [Skriv hjälp för PowerShell-cmdletar](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="0eae8-258">For information about supporting this feature in help articles that you write, see [about_Comment_Based_Help](./About/about_Comment_Based_Help.md), and [Supporting Online Help](/powershell/scripting/developer/module/supporting-online-help), and [Writing Help for PowerShell Cmdlets](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

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

### <span data-ttu-id="0eae8-259">-Parameter</span><span class="sxs-lookup"><span data-stu-id="0eae8-259">-Parameter</span></span>

<span data-ttu-id="0eae8-260">Visar endast de detaljerade beskrivningarna av de angivna parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-260">Displays only the detailed descriptions of the specified parameters.</span></span> <span data-ttu-id="0eae8-261">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-261">Wildcards are permitted.</span></span> <span data-ttu-id="0eae8-262">Den här parametern har ingen påverkan på skärmar med konceptuell (**About_**) hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-262">This parameter has no effect on displays of conceptual (**About_**) help.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Parameters
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0eae8-263">-Path</span><span class="sxs-lookup"><span data-stu-id="0eae8-263">-Path</span></span>

<span data-ttu-id="0eae8-264">Hämtar hjälp som förklarar hur cmdleten fungerar i den angivna providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="0eae8-264">Gets help that explains how the cmdlet works in the specified provider path.</span></span> <span data-ttu-id="0eae8-265">Ange en sökväg till PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="0eae8-265">Enter a PowerShell provider path.</span></span>

<span data-ttu-id="0eae8-266">Den här parametern hämtar en anpassad version av en cmdlets hjälp artikel som förklarar hur cmdleten fungerar i den angivna PowerShell-providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="0eae8-266">This parameter gets a customized version of a cmdlet help article that explains how the cmdlet works in the specified PowerShell provider path.</span></span> <span data-ttu-id="0eae8-267">Den här parametern är endast effektiv för hjälp om en provider-cmdlet och bara när providern innehåller en anpassad version av hjälp artikeln Provider-cmdlet i Hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-267">This parameter is effective only for help about a provider cmdlet and only when the provider includes a custom version of the provider cmdlet help article in its help file.</span></span> <span data-ttu-id="0eae8-268">Om du vill använda den här parametern installerar du hjälp filen för modulen som innehåller providern.</span><span class="sxs-lookup"><span data-stu-id="0eae8-268">To use this parameter, install the help file for the module that includes the provider.</span></span>

<span data-ttu-id="0eae8-269">Om du vill se en anpassad cmdlet-hjälp för en sökväg för en provider går du till platsen för providerns sökväg och anger ett `Get-Help` kommando eller, från valfri sökväg, använder du parametern **Path** för `Get-Help` att ange providerns sökväg.</span><span class="sxs-lookup"><span data-stu-id="0eae8-269">To see the custom cmdlet help for a provider path, go to the provider path location and enter a `Get-Help` command or, from any path location, use the **Path** parameter of `Get-Help` to specify the provider path.</span></span> <span data-ttu-id="0eae8-270">Du kan också hitta anpassad cmdlet-hjälp online i hjälp avsnitten för providern i hjälp artiklarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-270">You can also find custom cmdlet help online in the provider help section of the help articles.</span></span>

<span data-ttu-id="0eae8-271">Mer information om PowerShell-leverantörer finns [about_Providers](./About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0eae8-271">For more information about PowerShell providers, see [about_Providers](./About/about_Providers.md).</span></span>

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

### <span data-ttu-id="0eae8-272">-Roll</span><span class="sxs-lookup"><span data-stu-id="0eae8-272">-Role</span></span>

<span data-ttu-id="0eae8-273">Visar anpassad hjälp för den angivna användar rollen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-273">Displays help customized for the specified user role.</span></span> <span data-ttu-id="0eae8-274">Ange en roll.</span><span class="sxs-lookup"><span data-stu-id="0eae8-274">Enter a role.</span></span> <span data-ttu-id="0eae8-275">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="0eae8-276">Ange den roll som användaren spelar i en organisation.</span><span class="sxs-lookup"><span data-stu-id="0eae8-276">Enter the role that the user plays in an organization.</span></span> <span data-ttu-id="0eae8-277">Vissa cmdletar visar annan text i sina hjälpfiler baserat på värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="0eae8-277">Some cmdlets display different text in their help files based on the value of this parameter.</span></span> <span data-ttu-id="0eae8-278">Den här parametern har ingen inverkan på hjälpen för Core-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-278">This parameter has no effect on help for the core cmdlets.</span></span>

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

### <span data-ttu-id="0eae8-279">-ShowWindow</span><span class="sxs-lookup"><span data-stu-id="0eae8-279">-ShowWindow</span></span>

<span data-ttu-id="0eae8-280">Visar hjälp avsnittet i ett fönster för enklare läsning.</span><span class="sxs-lookup"><span data-stu-id="0eae8-280">Displays the help topic in a window for easier reading.</span></span> <span data-ttu-id="0eae8-281">I fönstret **finns en Sök funktion och en** **inställnings** ruta där du kan ange alternativ för visning, inklusive alternativ för att endast Visa valda avsnitt i ett hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="0eae8-281">The window includes a **Find** search feature and a **Settings** box that lets you set options for the display, including options to display only selected sections of a help topic.</span></span>

<span data-ttu-id="0eae8-282">**ShowWindow** -parametern stöder hjälp avsnitt för kommandon (cmdlets, functions, CIM-kommandon, skript) och konceptuella **om** artiklar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-282">The **ShowWindow** parameter supports help topics for commands (cmdlets, functions, CIM commands, scripts) and conceptual **About** articles.</span></span> <span data-ttu-id="0eae8-283">Den har inte stöd för leverantörs hjälp.</span><span class="sxs-lookup"><span data-stu-id="0eae8-283">It does not support provider help.</span></span>

<span data-ttu-id="0eae8-284">Den här parametern introducerades i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="0eae8-284">This parameter was reintroduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="0eae8-285">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0eae8-285">CommonParameters</span></span>

<span data-ttu-id="0eae8-286">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0eae8-286">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0eae8-287">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0eae8-287">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0eae8-288">INDATA</span><span class="sxs-lookup"><span data-stu-id="0eae8-288">INPUTS</span></span>

### <span data-ttu-id="0eae8-289">Inga</span><span class="sxs-lookup"><span data-stu-id="0eae8-289">None</span></span>

<span data-ttu-id="0eae8-290">Du kan inte skicka objekt nedåt i pipelinen till `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-290">You can't send objects down the pipeline to `Get-Help`.</span></span>

## <span data-ttu-id="0eae8-291">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0eae8-291">OUTPUTS</span></span>

### <span data-ttu-id="0eae8-292">ExtendedCmdletHelpInfo</span><span class="sxs-lookup"><span data-stu-id="0eae8-292">ExtendedCmdletHelpInfo</span></span>

<span data-ttu-id="0eae8-293">Om du kör `Get-Help` på ett kommando som inte har en hjälp fil `Get-Help` returnerar ett **ExtendedCmdletHelpInfo** -objekt som representerar den automatiskt genererade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="0eae8-293">If you run `Get-Help` on a command that doesn't have a help file, `Get-Help` returns an **ExtendedCmdletHelpInfo** object that represents autogenerated help.</span></span>

### <span data-ttu-id="0eae8-294">System. String</span><span class="sxs-lookup"><span data-stu-id="0eae8-294">System.String</span></span>

<span data-ttu-id="0eae8-295">Om du får en konceptuell hjälp artikel `Get-Help` returneras den som en sträng.</span><span class="sxs-lookup"><span data-stu-id="0eae8-295">If you get a conceptual help article, `Get-Help` returns it as a string.</span></span>

### <span data-ttu-id="0eae8-296">MamlCommandHelpInfo</span><span class="sxs-lookup"><span data-stu-id="0eae8-296">MamlCommandHelpInfo</span></span>

<span data-ttu-id="0eae8-297">Om du får ett kommando som har en hjälp fil `Get-Help` returnerar ett **MamlCommandHelpInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0eae8-297">If you get a command that has a help file, `Get-Help` returns a **MamlCommandHelpInfo** object.</span></span>

## <span data-ttu-id="0eae8-298">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0eae8-298">NOTES</span></span>

<span data-ttu-id="0eae8-299">PowerShell 3,0 innehåller inte hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-299">PowerShell 3.0 doesn't include help files.</span></span> <span data-ttu-id="0eae8-300">Använd cmdleten för att ladda ned och installera hjälpfilerna som `Get-Help` läser `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="0eae8-300">To download and install the help files that `Get-Help` reads, use the `Update-Help` cmdlet.</span></span> <span data-ttu-id="0eae8-301">Du kan använda `Update-Help` cmdleten för att hämta och installera hjälpfiler för de kärn kommandon som ingår i PowerShell och för alla moduler som du installerar.</span><span class="sxs-lookup"><span data-stu-id="0eae8-301">You can use the `Update-Help` cmdlet to download and install help files for the core commands that come with PowerShell and for any modules that you install.</span></span> <span data-ttu-id="0eae8-302">Du kan också använda den för att uppdatera hjälpfilerna så att hjälpen på datorn aldrig är inaktuell.</span><span class="sxs-lookup"><span data-stu-id="0eae8-302">You can also use it to update the help files so that the help on your computer is never outdated.</span></span>

<span data-ttu-id="0eae8-303">Du kan också läsa hjälp artiklarna om de kommandon som levereras med PowerShell online från [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="0eae8-303">You can also read the help articles about the commands that come with PowerShell online starting at [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

<span data-ttu-id="0eae8-304">`Get-Help` Visar hjälp i språk uppsättningen för Windows-operativsystemet eller på reserv språket för det aktuella språket.</span><span class="sxs-lookup"><span data-stu-id="0eae8-304">`Get-Help` displays help in the locale set for the Windows operating system or in the fallback language for that locale.</span></span> <span data-ttu-id="0eae8-305">Om du inte har hjälpfilerna för primär-eller fallback-språkvarianten `Get-Help` fungerar det som om det inte finns några hjälpfiler på datorn.</span><span class="sxs-lookup"><span data-stu-id="0eae8-305">If you don't have help files for the primary or fallback locale, `Get-Help` behaves as if there are no help files on the computer.</span></span> <span data-ttu-id="0eae8-306">Om du vill ha hjälp med ett annat språk kan du använda **region** och **språk** på kontroll panelen för att ändra inställningarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-306">To get help for a different locale, use **Region** and **Language** in Control Panel to change the settings.</span></span> <span data-ttu-id="0eae8-307">På Windows 10, **Inställningar**, **tid & språk**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-307">On Windows 10, **Settings**, **Time & Language**.</span></span>

<span data-ttu-id="0eae8-308">En fullständig vy över hjälpen innehåller en tabell med information om parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0eae8-308">The full view of help includes a table of information about the parameters.</span></span> <span data-ttu-id="0eae8-309">Tabellen innehåller följande fält:</span><span class="sxs-lookup"><span data-stu-id="0eae8-309">The table includes the following fields:</span></span>

- <span data-ttu-id="0eae8-310">**Krävs**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-310">**Required**.</span></span> <span data-ttu-id="0eae8-311">Anger om parametern är obligatorisk (sant) eller valfri (falskt).</span><span class="sxs-lookup"><span data-stu-id="0eae8-311">Indicates whether the parameter is required (true) or optional (false).</span></span>

- <span data-ttu-id="0eae8-312">**Position**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-312">**Position**.</span></span> <span data-ttu-id="0eae8-313">Anger om parametern är namngiven eller position (numerisk).</span><span class="sxs-lookup"><span data-stu-id="0eae8-313">Indicates whether the parameter is named or positional (numeric).</span></span> <span data-ttu-id="0eae8-314">Positions parametrar måste finnas på en angiven plats i kommandot.</span><span class="sxs-lookup"><span data-stu-id="0eae8-314">Positional parameters must appear in a specified place in the command.</span></span>

- <span data-ttu-id="0eae8-315">**Namngiven** anger att parameter namnet är obligatoriskt, men att parametern kan visas var som helst i kommandot.</span><span class="sxs-lookup"><span data-stu-id="0eae8-315">**Named** indicates that the parameter name is required, but that the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="0eae8-316">**Numeriskt** anger att parameter namnet är valfritt, men när namnet utelämnas måste parametern vara på den plats som anges i numret.</span><span class="sxs-lookup"><span data-stu-id="0eae8-316">**Numeric** indicates that the parameter name is optional, but when the name is omitted, the parameter must be in the place specified by the number.</span></span> <span data-ttu-id="0eae8-317">Anger till exempel `2` att om parameter namnet utelämnas måste parametern vara den andra eller enda namnlös parameter i kommandot.</span><span class="sxs-lookup"><span data-stu-id="0eae8-317">For example, `2` indicates that when the parameter name is omitted, the parameter must be the second or only unnamed parameter in the command.</span></span> <span data-ttu-id="0eae8-318">När parameter namnet används kan parametern visas var som helst i kommandot.</span><span class="sxs-lookup"><span data-stu-id="0eae8-318">When the parameter name is used, the parameter can appear anywhere in the command.</span></span>

- <span data-ttu-id="0eae8-319">**Standardvärde**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-319">**Default value**.</span></span> <span data-ttu-id="0eae8-320">Parametervärdet eller standard beteendet som används i PowerShell om du inte inkluderar parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="0eae8-320">The parameter value or default behavior that PowerShell uses if you don't include the parameter in the command.</span></span>

- <span data-ttu-id="0eae8-321">Accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="0eae8-321">Accepts pipeline input.</span></span> <span data-ttu-id="0eae8-322">Anger om du kan (sant) eller inte (falskt) skicka objekt till parametern via en pipeline.</span><span class="sxs-lookup"><span data-stu-id="0eae8-322">Indicates whether you can (true) or can't (false) send objects to the parameter through a pipeline.</span></span> <span data-ttu-id="0eae8-323">**Efter egenskaps namn** betyder det att det pipelinade objektet måste ha en egenskap som har samma namn som parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="0eae8-323">**By Property Name** means that the pipelined object must have a property that has the same name as the parameter name.</span></span>

- <span data-ttu-id="0eae8-324">**Accepterar jokertecken**.</span><span class="sxs-lookup"><span data-stu-id="0eae8-324">**Accepts wildcard characters**.</span></span> <span data-ttu-id="0eae8-325">Anger om värdet för en parameter kan innehålla jokertecken, till exempel en asterisk ( `*` ) eller frågetecken ( `?` ).</span><span class="sxs-lookup"><span data-stu-id="0eae8-325">Indicates whether the value of a parameter can include wildcard characters, such as an asterisk (`*`) or question mark (`?`).</span></span>

## <span data-ttu-id="0eae8-326">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0eae8-326">RELATED LINKS</span></span>

[<span data-ttu-id="0eae8-327">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="0eae8-327">about_Command_Syntax</span></span>](About/about_Command_Syntax.md)

[<span data-ttu-id="0eae8-328">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="0eae8-328">about_Comment_Based_Help</span></span>](./About/about_Comment_Based_Help.md)

[<span data-ttu-id="0eae8-329">Get-Command</span><span class="sxs-lookup"><span data-stu-id="0eae8-329">Get-Command</span></span>](Get-Command.md)

[<span data-ttu-id="0eae8-330">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="0eae8-330">Supporting Updatable Help</span></span>](/powershell/scripting/developer/module/supporting-updatable-help)

[<span data-ttu-id="0eae8-331">Uppdatera – hjälp</span><span class="sxs-lookup"><span data-stu-id="0eae8-331">Update-Help</span></span>](Update-Help.md)

[<span data-ttu-id="0eae8-332">Skriva kommentarsbaserade hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="0eae8-332">Writing Comment-Based Help Topics</span></span>](/powershell/scripting/developer/help/writing-comment-based-help-topics)

[<span data-ttu-id="0eae8-333">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="0eae8-333">Writing Help for PowerShell Cmdlets</span></span>](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)

