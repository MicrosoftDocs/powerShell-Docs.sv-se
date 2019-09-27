---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Få detaljerad hjälpinformation
ms.openlocfilehash: 033a8962ca438b49c10fafa2852c87d19868b4d9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325196"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="4fc12-103">Få detaljerad hjälpinformation</span><span class="sxs-lookup"><span data-stu-id="4fc12-103">Getting detailed help information</span></span>

<span data-ttu-id="4fc12-104">PowerShell innehåller detaljerade hjälp artiklar som förklarar PowerShell-koncept och PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="4fc12-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="4fc12-105">Det finns också hjälp artiklar för varje cmdlet och Provider och för många funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="4fc12-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="4fc12-106">Du kan visa dessa hjälp artiklar i kommando tolken eller Visa de senaste uppdaterade versionerna av de här artiklarna i [PowerShell](/powershell/scripting/overview) -dokumentationen online.</span><span class="sxs-lookup"><span data-stu-id="4fc12-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="4fc12-107">Få hjälp med cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fc12-107">Getting help for cmdlets</span></span>

<span data-ttu-id="4fc12-108">Använd cmdleten [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) för att få hjälp om PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="4fc12-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="4fc12-109">Om du till exempel vill få hjälp med `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="4fc12-110">eller</span><span class="sxs-lookup"><span data-stu-id="4fc12-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="4fc12-111">Du kan även få hjälp med cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="4fc12-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="4fc12-112">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4fc12-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="4fc12-113">Om du vill hämta en lista över alla hjälp artiklar för cmdlet i sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="4fc12-114">Om du vill visa en sida i varje hjälp artikel i taget använder du `help` funktionen eller dess alias `man`.</span><span class="sxs-lookup"><span data-stu-id="4fc12-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="4fc12-115">Om du till exempel vill visa hjälp för `Get-ChildItem` cmdleten skriver du</span><span class="sxs-lookup"><span data-stu-id="4fc12-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="4fc12-116">eller</span><span class="sxs-lookup"><span data-stu-id="4fc12-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="4fc12-117">Om du vill visa detaljerad information använder du den **detaljerade** parametern `Get-Help` för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4fc12-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4fc12-118">Om du till exempel vill få detaljerad information om `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="4fc12-119">Om du vill visa allt innehåll i hjälp artikeln använder du en **fullständig** parameter för `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4fc12-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4fc12-120">Om du till exempel vill visa allt innehåll i hjälp artikeln för `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="4fc12-121">Om du vill ha mer information om parametrarna för en cmdlet använder du **parametern parameter** för `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4fc12-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4fc12-122">Om du till exempel vill få detaljerad hjälp för alla parametrar för `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="4fc12-123">Om du bara vill visa exemplen i en hjälp artikel använder du parametern `Get-Help`exempel i.</span><span class="sxs-lookup"><span data-stu-id="4fc12-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="4fc12-124">Om du till exempel vill visa bara exemplen i hjälp artikeln för `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="4fc12-125">Information om hur du skriver hjälp artiklar för de cmdlet: ar som du skriver in finns i [så här skriver du cmdlet-hjälpen](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="4fc12-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="4fc12-126">Få konceptuell hjälp</span><span class="sxs-lookup"><span data-stu-id="4fc12-126">Getting conceptual help</span></span>

<span data-ttu-id="4fc12-127">`Get-Help` Cmdleten visar också information om konceptuella artiklar i PowerShell, inklusive artiklar om PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="4fc12-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="4fc12-128">Konceptuell hjälp artiklar börjar med prefixet "about_", till exempel about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="4fc12-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="4fc12-129">(Namnet på den konceptuella artikeln måste anges på engelska även på icke-engelska versioner av PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="4fc12-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="4fc12-130">Om du vill visa en lista med konceptuella artiklar skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="4fc12-131">Om du vill visa en viss hjälp artikel skriver du artikel namnet, till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fc12-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="4fc12-132">Parametrarna `Get-Help`för, till exempel **detaljerad**, **parameter**och **exempel**, har ingen påverkan på visningen av konceptuella hjälp artiklar.</span><span class="sxs-lookup"><span data-stu-id="4fc12-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="4fc12-133">Få hjälp om leverantörer</span><span class="sxs-lookup"><span data-stu-id="4fc12-133">Getting help about providers</span></span>

<span data-ttu-id="4fc12-134">`Get-Help` Cmdleten visar information om PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="4fc12-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="4fc12-135">Om du vill ha hjälp med en provider `Get-Help` skriver du följt av namnet på providern.</span><span class="sxs-lookup"><span data-stu-id="4fc12-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="4fc12-136">Om du till exempel vill få hjälp med register leverantören skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="4fc12-137">Om du vill hämta en lista över alla hjälp artiklar om providern i din session skriver du</span><span class="sxs-lookup"><span data-stu-id="4fc12-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="4fc12-138">Parametrarna `Get-Help`för, till exempel **detaljerad**, **parameter**och **exempel**, har ingen påverkan på visningen av leverantörs hjälp artiklar.</span><span class="sxs-lookup"><span data-stu-id="4fc12-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="4fc12-139">Få hjälp om skript och funktioner</span><span class="sxs-lookup"><span data-stu-id="4fc12-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="4fc12-140">Många skript och funktioner i PowerShell har hjälp artiklar.</span><span class="sxs-lookup"><span data-stu-id="4fc12-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="4fc12-141">`Get-Help` Använd cmdleten för att visa hjälp artiklarna för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="4fc12-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="4fc12-142">Om du vill visa hjälpen för en funktion skriver `Get-Help` du följt av funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="4fc12-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="4fc12-143">Om du till exempel vill få hjälp med `Disable-PSRemoting` funktionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="4fc12-144">Om du vill visa hjälpen för ett skript anger du sökvägen till skript filen.</span><span class="sxs-lookup"><span data-stu-id="4fc12-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="4fc12-145">Om skriptet inte finns i en sökväg som anges i miljövariabeln PATH måste du använda den fullständigt kvalificerade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="4fc12-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="4fc12-146">Om du till exempel har ett skript som heter "TestScript. ps1" i katalogen C:\\PS-test för att visa hjälp artikeln för skriptet, skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="4fc12-147">De parametrar som är utformade för att Visa cmdlet-hjälp fungerar även för skript-och funktions hjälp.</span><span class="sxs-lookup"><span data-stu-id="4fc12-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="4fc12-148">Hjälp för funktioner och skript visas dock inte när du kör `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="4fc12-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="4fc12-149">Information om hur du skriver hjälp artiklar för dina funktioner och skript finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="4fc12-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="4fc12-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="4fc12-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="4fc12-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="4fc12-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="4fc12-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="4fc12-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="4fc12-153">Få hjälp online</span><span class="sxs-lookup"><span data-stu-id="4fc12-153">Getting help online</span></span>

<span data-ttu-id="4fc12-154">Visa hjälp artiklar online är ett av de bästa sätten att få hjälp.</span><span class="sxs-lookup"><span data-stu-id="4fc12-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="4fc12-155">Online-artiklar är enklare att uppdatera och tillhandahålla det mest aktuella innehållet.</span><span class="sxs-lookup"><span data-stu-id="4fc12-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="4fc12-156">Använd `Get-Help` cmdleten **online** för att få hjälp online.</span><span class="sxs-lookup"><span data-stu-id="4fc12-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4fc12-157">Alla hjälp artiklar som ingår i PowerShell, inklusive leverantörs hjälp och begreppsmässig (om) hjälp artiklar finns tillgängliga online i [PowerShell](/powershell/scripting/powershell-scripting) -dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="4fc12-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="4fc12-158">Du kan inte använda **online** -parametern med konceptuell (\*about_) eller leverantörs hjälp artiklar.</span><span class="sxs-lookup"><span data-stu-id="4fc12-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="4fc12-159">Direkt hjälpen är valfri, så den fungerar inte för varje cmdlet, funktion eller skript.</span><span class="sxs-lookup"><span data-stu-id="4fc12-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="4fc12-160">Om du till exempel vill hämta online-versionen av hjälp artikeln om `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="4fc12-161">PowerShell öppnar artikeln i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="4fc12-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="4fc12-162">Om onlinehjälpen stöds för en hjälp artikel kan du också Visa webb adressen till hjälp artikeln.</span><span class="sxs-lookup"><span data-stu-id="4fc12-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="4fc12-163">URL: en visas i avsnittet relaterade länkar i en hjälp artikel.</span><span class="sxs-lookup"><span data-stu-id="4fc12-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="4fc12-164">Om du till exempel vill visa URL: en för online-versionen av cmdleten Add-Computer skriver du:</span><span class="sxs-lookup"><span data-stu-id="4fc12-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="4fc12-165">Den första raden i avsnittet relaterade länkar i artikeln visas nedan.</span><span class="sxs-lookup"><span data-stu-id="4fc12-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="4fc12-166">Information om hur du ger support online för dina hjälp artiklar finns i [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="4fc12-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="4fc12-167">Se även</span><span class="sxs-lookup"><span data-stu-id="4fc12-167">See also</span></span>

- [<span data-ttu-id="4fc12-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="4fc12-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="4fc12-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="4fc12-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="4fc12-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="4fc12-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="4fc12-171">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="4fc12-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
