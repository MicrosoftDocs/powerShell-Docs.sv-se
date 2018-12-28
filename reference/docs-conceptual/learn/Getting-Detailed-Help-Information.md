---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Få detaljerad hjälpinformation
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 8b56f003fdef38b0f126cfe82eefcc145cc54783
ms.sourcegitcommit: 3402a478cf118c11a5642038eb117bc76553e3ab
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53411607"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="a0b2a-103">Få detaljerad hjälpinformation</span><span class="sxs-lookup"><span data-stu-id="a0b2a-103">Getting detailed help information</span></span>

<span data-ttu-id="a0b2a-104">PowerShell innehåller detaljerade hjälpartiklar som förklarar PowerShell-koncept och PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="a0b2a-105">Det finns även hjälpartiklar för varje cmdlet och providern och för många funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="a0b2a-106">Du kan visa dessa hjälpartiklar i Kommandotolken eller visa den senast uppdaterade versioner av de här artiklarna i den [PowerShell](/powershell/scripting/overview) dokumentationen online.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="a0b2a-107">Få hjälp om cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="a0b2a-107">Getting help for cmdlets</span></span>

<span data-ttu-id="a0b2a-108">Om du behöver hjälp om PowerShell-cmdletar, använda den [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="a0b2a-109">Till exempel för att få hjälp med den `Get-ChildItem` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="a0b2a-110">eller</span><span class="sxs-lookup"><span data-stu-id="a0b2a-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="a0b2a-111">Du kan även få hjälp om cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="a0b2a-112">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="a0b2a-113">Om du vill hämta en lista över alla cmdlet hjälpartiklar i sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="a0b2a-114">Använd för att visa en sida med varje hjälpartikeln i taget, den `help` funktion eller dess alias `man`.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="a0b2a-115">Till exempel vill visa hjälp för den `Get-ChildItem` cmdlet, typ</span><span class="sxs-lookup"><span data-stu-id="a0b2a-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="a0b2a-116">eller</span><span class="sxs-lookup"><span data-stu-id="a0b2a-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="a0b2a-117">Använd för att visa detaljerad information i **detaljerat** -parametern för den `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="a0b2a-118">Till exempel för att få detaljerad information den `Get-ChildItem` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="a0b2a-119">Använd för att visa allt innehåll i hjälpartikeln den **fullständig** -parametern för den `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="a0b2a-120">Till exempel för att visa allt innehåll i hjälpartikeln för den `Get-ChildItem` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="a0b2a-121">Få ytterligare hjälp om parametrarna för en cmdlet, Använd den **parametern** -parametern för den `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="a0b2a-122">Till exempel utförlig information för alla parametrar för att hämta den `Get-ChildItem` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="a0b2a-123">Använd för att visa endast i exemplen i en hjälpartikeln den **exempel** -parametern för den `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="a0b2a-124">Till exempel för att visa endast i exemplen i hjälpartikeln för den `Get-ChildItem `cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-124">For example, to display only the examples in the Help article for the `Get-ChildItem `cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="a0b2a-125">Information om hur du skriver hjälpartiklar för de cmdletar som du skriver finns i [hur du skriver hjälp för cmdleten](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="a0b2a-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="a0b2a-126">Konceptuell hjälp</span><span class="sxs-lookup"><span data-stu-id="a0b2a-126">Getting conceptual help</span></span>

<span data-ttu-id="a0b2a-127">Den `Get-Help` cmdleten visar också information om konceptuella artiklar i PowerShell, bland annat artiklar om PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="a0b2a-128">Konceptuell hjälp artiklar som börjar med prefixet ”about_”, till exempel about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="a0b2a-129">(Namnet på den konceptuella artikeln måste anges på engelska även på icke-engelska versioner av PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="a0b2a-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="a0b2a-130">Om du vill visa en lista över konceptuella artiklar, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="a0b2a-131">Om du vill visa en viss hjälpartikeln, skriver du artikelnamnet på till exempel:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="a0b2a-132">Parametrarna för `Get-Help`, till exempel **detaljerat**, **parametern**, och **exempel**, har ingen effekt på visning av konceptuell hjälpartiklar.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="a0b2a-133">Få hjälp om leverantörer</span><span class="sxs-lookup"><span data-stu-id="a0b2a-133">Getting help about providers</span></span>

<span data-ttu-id="a0b2a-134">Den `Get-Help` cmdlet visar information om PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="a0b2a-135">Om du vill få hjälp med en provider, skriver `Get-Help` följt av providernamn.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="a0b2a-136">Till exempel om du behöver hjälp för register-provider, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="a0b2a-137">Om du vill hämta en lista över alla providern hjälpartiklar i sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="a0b2a-138">Parametrarna för `Get-Help`, till exempel **detaljerat**, **parametern**, och **exempel**, har ingen effekt på visning av providern hjälpartiklar.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="a0b2a-139">Få hjälp om skript och funktioner</span><span class="sxs-lookup"><span data-stu-id="a0b2a-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="a0b2a-140">Många skript och funktioner i PowerShell har hjälpartiklar.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="a0b2a-141">Använd den `Get-Help` cmdleten för att visa hjälpartiklar för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="a0b2a-142">Om du vill visa hjälpen för en funktion, skriver `Get-Help` följt av namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="a0b2a-143">Till exempel för att få hjälp med den `Disable-PSRemoting` skriver:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="a0b2a-144">Om du vill visa hjälp för ett skript, ange sökvägen till skriptfilen.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="a0b2a-145">Om skriptet inte är i en sökväg som anges i miljövariabeln Path måste du använda den fullständiga sökvägen.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="a0b2a-146">Exempel: Om du har ett skript som heter ”TestScript.ps1” i din C:\\PS-Test directory för att visa hjälpartikeln för skriptet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="a0b2a-147">De parametrar som är utformade för att visa cmdlet Help arbete för skriptet och funktionen hjälper för.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="a0b2a-148">Hjälp för funktioner och skript är dock inte visas när du kör `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="a0b2a-149">Information om hur du skriver hjälpartiklar för dina funktioner och skript finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="a0b2a-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a0b2a-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="a0b2a-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="a0b2a-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="a0b2a-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="a0b2a-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="a0b2a-153">Få hjälp online</span><span class="sxs-lookup"><span data-stu-id="a0b2a-153">Getting help online</span></span>

<span data-ttu-id="a0b2a-154">Visa hjälpartiklar online är en av de bästa sätten att få hjälp.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="a0b2a-155">Online artiklar är lättare att uppdatera och ger det mest aktuella innehållet.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="a0b2a-156">Om du vill få hjälp online, använda den **Online** -parametern för den `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="a0b2a-157">Alla hjälpartiklar som levereras med PowerShell, inklusive providern hjälp och konceptuella (om) hjälpartiklar, är tillgängliga online i den [PowerShell](/powershell/scripting/powershell-scripting) dokumentation.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="a0b2a-158">Du kan inte använda den **Online** parameter med konceptuella (about_\*) eller hjälpartiklar för providern.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="a0b2a-159">Onlinehjälp är valfritt, så inte fungerar för varje cmdlet, en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="a0b2a-160">Till exempel för att få onlineversionen av hjälpavsnittet om den `Get-ChildItem` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="a0b2a-161">PowerShell öppnas artikeln i din standardwebbläsare.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="a0b2a-162">Du kan också visa Webbadressen till hjälpartikeln om onlinehjälp stöds för en hjälpartikeln.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="a0b2a-163">Webbadressen visas i avsnittet med länkar i en hjälpartikeln.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="a0b2a-164">Till exempel om du vill se URL-Adressen för online-versionen av cmdleten Lägg till dator skriver du:</span><span class="sxs-lookup"><span data-stu-id="a0b2a-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="a0b2a-165">Den första raden i avsnittet med länkar i artikeln visas nedan.</span><span class="sxs-lookup"><span data-stu-id="a0b2a-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="a0b2a-166">Information om hur du ger online support för dina hjälpartiklar finns i [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="a0b2a-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0b2a-167">Se även</span><span class="sxs-lookup"><span data-stu-id="a0b2a-167">See also</span></span>

- [<span data-ttu-id="a0b2a-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="a0b2a-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="a0b2a-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="a0b2a-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="a0b2a-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="a0b2a-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="a0b2a-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="a0b2a-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
