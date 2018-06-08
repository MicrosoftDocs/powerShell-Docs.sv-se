---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Få detaljerad hjälpinformation
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 29c24af3f688f9388893044952442910e793842d
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483040"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="cb4eb-103">Få detaljerad hjälpinformation</span><span class="sxs-lookup"><span data-stu-id="cb4eb-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="cb4eb-104">Windows PowerShell innehåller detaljerade hjälpavsnitt som beskriver begrepp för Windows PowerShell och Windows PowerShell-språk.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="cb4eb-105">Det finns även hjälpavsnitt för varje cmdlet och providern och hjälpavsnitt för många funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="cb4eb-106">Du kan visa de här hjälpavsnitten i Kommandotolken eller visa senast uppdaterade versioner av dessa avsnitt i Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="cb4eb-107">Många program som är värdar för Windows PowerShell, till exempel Windows PowerShell Integrated Scripting Environment, ange ytterligare hjälp-funktioner, till exempel sammanhangsberoende hjälp och kompilerade hjälpfilen (.chm).</span><span class="sxs-lookup"><span data-stu-id="cb4eb-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="cb4eb-108">Få hjälp med cmdletar</span><span class="sxs-lookup"><span data-stu-id="cb4eb-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="cb4eb-109">För att få hjälp om Windows PowerShell-cmdlets kan använda den [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="cb4eb-110">Till exempel för att få hjälp med den [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, skriv:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="cb4eb-111">eller</span><span class="sxs-lookup"><span data-stu-id="cb4eb-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="cb4eb-112">Du kan även få hjälp om cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="cb4eb-113">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="cb4eb-114">Om du vill hämta en lista över alla skriver cmdlet-hjälpavsnitten i sessionen, du:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="cb4eb-115">Använd för att visa en sida i varje hjälpavsnitt samtidigt i **hjälp** funktion eller dess alias **man**.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="cb4eb-116">Skriv till exempel om du vill visa hjälpen för cmdleten Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="cb4eb-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="cb4eb-117">eller</span><span class="sxs-lookup"><span data-stu-id="cb4eb-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="cb4eb-118">Använd för att visa detaljerad information om en cmdlet-, function- eller skript, inklusive beskrivningar av dess parametrar och exempel på dess användning av *detaljerad* parametern för cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="cb4eb-119">Om du vill hämta detaljerad information om cmdlet Get-ChildItem, exempelvis:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="cb4eb-120">Använd för att visa allt innehåll i hjälpavsnittet den *fullständig* parametern för cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="cb4eb-121">Om du vill visa allt innehåll i hjälpavsnittet för cmdleten Get-ChildItem, exempelvis:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="cb4eb-122">Få detaljerad hjälp om parametrarna för en cmdlet, Använd den *parametern* parametern för cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="cb4eb-123">Till exempel få detaljerad hjälp för alla parametrar för cmdleten Get-ChildItem typ:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="cb4eb-124">Använd för att visa endast exemplen i ett hjälpavsnitt den *exempel* parametern för Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="cb4eb-125">Om du vill visa endast exemplen i hjälpavsnittet för cmdleten Get-ChildItem, exempelvis:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="cb4eb-126">Information om hur du skriver hjälpavsnitt för de cmdlets som du skriver finns [så att skriva Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN library.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="cb4eb-127">Konceptuell hjälp</span><span class="sxs-lookup"><span data-stu-id="cb4eb-127">Getting Conceptual Help</span></span>
<span data-ttu-id="cb4eb-128">Cmdleten Get-Help visar även information om konceptuella avsnitt i Windows PowerShell, inklusive information om Windows PowerShell-språk.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="cb4eb-129">Konceptuell hjälpavsnitt som börjar med prefixet ”about_”, till exempel about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="cb4eb-130">(Namnet på konceptuellt avsnitt måste anges på engelska även på icke-engelska versioner av Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="cb4eb-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="cb4eb-131">Om du vill visa en lista över grundläggande information skriver du:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="cb4eb-132">Om du vill visa ett hjälpavsnitt, skriver du avsnittsnamnet på till exempel:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="cb4eb-133">Parametrarna för Get-Help som *detaljerad*, *parametern*, och *exempel*, har ingen effekt på visning av konceptuella hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="cb4eb-134">Få hjälp om leverantörer</span><span class="sxs-lookup"><span data-stu-id="cb4eb-134">Getting Help About Providers</span></span>
<span data-ttu-id="cb4eb-135">Cmdleten Get-Help visar information om Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="cb4eb-136">För att få hjälp för en provider, Skriv ”Get-Help” följt av providernamn.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="cb4eb-137">Skriv till exempel för att få hjälp för register-provider:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="cb4eb-138">Om du vill hämta en lista över alla hjälpavsnitt för providern i sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="cb4eb-139">Parametrarna för Get-Help som *detaljerad*, *parametern*, och *exempel*, har ingen effekt på visning av hjälpavsnitt för providern.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="cb4eb-140">Få hjälp om skript och funktioner</span><span class="sxs-lookup"><span data-stu-id="cb4eb-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="cb4eb-141">Många skript och funktioner i Windows PowerShell har hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="cb4eb-142">Använd cmdleten Get-Help om du vill visa hjälpavsnitt för skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="cb4eb-143">Om du vill visa hjälp för en funktion, Skriv ”get-help” följt av namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="cb4eb-144">Om du vill få hjälp med funktionen inaktivera PSRemoting, exempelvis:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="cb4eb-145">Visa hjälp för ett skript, skriva den fullständiga sökvägen till skriptfilen.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="cb4eb-146">Om skriptet finns på en sökväg som anges i miljövariabeln Path, kan du utelämna sökvägen från kommandot.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="cb4eb-147">Till exempel om du har ett skript som heter ”TestScript.ps1” i din C:\\PS-Test directory vill visa hjälpavsnitt för skriptet, typ:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="cb4eb-148">De parametrar som utformats för att visa cmdlet hjälp som *detaljerad*, *fullständig*, *exempel*, och *parametern*arbetar för skriptet hjälp och funktionen hjälp, för.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="cb4eb-149">Men när du visar alla hjälp genom att skriva ”get-help \*”, för funktioner och skript inte visas.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="cb4eb-150">Information om hur du skriver hjälpavsnitt för funktioner och skript finns i [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af), och [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="cb4eb-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="cb4eb-151">Få hjälp Online</span><span class="sxs-lookup"><span data-stu-id="cb4eb-151">Getting Help Online</span></span>
<span data-ttu-id="cb4eb-152">Om du är ansluten till Internet, är ett bra sätt att få hjälp att visa hjälpavsnitt online.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="cb4eb-153">Eftersom det är enkelt att uppdatera online avsnitt, är det troligt att ange det mest aktuella innehållet.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="cb4eb-154">För att få hjälp online försök den *Online* parametern för cmdleten Get-Help.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="cb4eb-155">Den *Online* parametern för Get-Help cmdleten fungerar endast för cmdlet hjälp fungera hjälp och skript för hjälp.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="cb4eb-156">Du kan inte använda den *Online* parameter med konceptuella (om) avsnitt eller hjälpavsnitt för providern.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="cb4eb-157">Dessutom eftersom den här funktionen är valfritt, fungerar det inte för varje cmdlet-, function- eller skript hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="cb4eb-158">Men alla hjälpavsnitt som levereras med Windows PowerShell, inklusive providern hjälp och konceptuella (hjälpavsnitt), är tillgänglig online i den [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) avsnitt i Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="cb4eb-159">Att använda den *Online* parametern för cmdleten Get-Help använder du följande kommandoformat.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="cb4eb-160">Till exempel för att få onlineversionen av hjälpavsnittet om cmdlet Get-ChildItem, skriver du:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="cb4eb-161">Om det finns en onlineversionen av hjälpavsnittet öppnas i standardwebbläsaren.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="cb4eb-162">Du kan också visa Internet-adress (URL) i hjälpavsnittet om hjälp online har stöd för ett hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="cb4eb-163">Internet-adressen visas i avsnittet med länkar i ett hjälpavsnitt.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="cb4eb-164">Till exempel vill se URL: en för online-versionen av cmdlet Add-Computer skriver du:</span><span class="sxs-lookup"><span data-stu-id="cb4eb-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="cb4eb-165">Den första raden i avsnittet länkarna i avsnittet visas nedan.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="cb4eb-166">Information om hur du ska ge support online för dina hjälpavsnitt finns [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), och se [så att skriva Cmdlet](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN library.</span><span class="sxs-lookup"><span data-stu-id="cb4eb-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb4eb-167">Se även</span><span class="sxs-lookup"><span data-stu-id="cb4eb-167">See Also</span></span>
- <span data-ttu-id="cb4eb-168">[about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="cb4eb-168">[about_Functions [m2]](https://technet.microsoft.com/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="cb4eb-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="cb4eb-169">about_Scripts</span></span>](https://technet.microsoft.com/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="cb4eb-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="cb4eb-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="cb4eb-171">[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="cb4eb-171">[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>