---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Omdirigera data med Out-cmdletar
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030073"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="750a8-103">Omdirigera data med out-\*-cmdletar</span><span class="sxs-lookup"><span data-stu-id="750a8-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="750a8-104">Windows PowerShell innehåller flera cmdlets som låter dig styra data utdata direkt.</span><span class="sxs-lookup"><span data-stu-id="750a8-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="750a8-105">Dessa cmdletar delar två viktiga egenskaper.</span><span class="sxs-lookup"><span data-stu-id="750a8-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="750a8-106">Först omvandlar de ofta data till någon form av text.</span><span class="sxs-lookup"><span data-stu-id="750a8-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="750a8-107">De gör detta eftersom de skickar data till system komponenter som kräver text inmatning.</span><span class="sxs-lookup"><span data-stu-id="750a8-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="750a8-108">Det innebär att de måste representera objekten som text.</span><span class="sxs-lookup"><span data-stu-id="750a8-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="750a8-109">Därför formateras texten som du ser i fönstret Windows PowerShell-konsol.</span><span class="sxs-lookup"><span data-stu-id="750a8-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="750a8-110">För det andra använder dessa cmdlets för Windows PowerShell **-verbet** eftersom de skickar ut information från Windows PowerShell till någon annan stans.</span><span class="sxs-lookup"><span data-stu-id="750a8-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="750a8-111">Cmdleten **out-Host** är inget undantag: värd fönstrets visning är utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="750a8-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="750a8-112">Detta är viktigt eftersom när data skickas ut från Windows PowerShell tas de faktiskt bort.</span><span class="sxs-lookup"><span data-stu-id="750a8-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="750a8-113">Du kan se detta om du försöker skapa en pipeline som Page-data till värd fönstret och sedan försöka formatera den som en lista, som du ser här:</span><span class="sxs-lookup"><span data-stu-id="750a8-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="750a8-114">Du kan vänta på att kommandot visar sidor i process information i list format.</span><span class="sxs-lookup"><span data-stu-id="750a8-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="750a8-115">I stället visas standard tabell listan:</span><span class="sxs-lookup"><span data-stu-id="750a8-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="750a8-116">Cmdleten **out-Host** skickar data direkt till-konsolen så att kommandot **format-lista** aldrig får något att formatera.</span><span class="sxs-lookup"><span data-stu-id="750a8-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="750a8-117">Det korrekta sättet att strukturera det här kommandot är att placera cmdleten **out-Host** i slutet av pipelinen som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="750a8-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="750a8-118">Detta gör att process data formateras i en lista innan de växlas och visas.</span><span class="sxs-lookup"><span data-stu-id="750a8-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="750a8-119">Detta gäller för alla **out** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="750a8-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="750a8-120">En **out** -cmdlet ska alltid visas i slutet av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="750a8-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="750a8-121">Alla **utgångs** kommandon återger utdata som text med hjälp av formatering som gäller för konsol fönstret, inklusive gränser för linje längd.</span><span class="sxs-lookup"><span data-stu-id="750a8-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

## <a name="paging-console-output-out-host"></a><span data-ttu-id="750a8-122">Utdata för växlings konsolen (out-Host)</span><span class="sxs-lookup"><span data-stu-id="750a8-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="750a8-123">Som standard skickar Windows PowerShell data till värd fönstret, vilket är exakt vad out-Host-cmdleten gör.</span><span class="sxs-lookup"><span data-stu-id="750a8-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="750a8-124">Den primära användningen för out-Host-cmdleten är växlings data som vi beskrivit tidigare.</span><span class="sxs-lookup"><span data-stu-id="750a8-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="750a8-125">Följande kommando använder till exempel out-Host för att visa utdata från cmdleten Get-Command:</span><span class="sxs-lookup"><span data-stu-id="750a8-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="750a8-126">Du kan också använda funktionen **more** för att ange data på sidan.</span><span class="sxs-lookup"><span data-stu-id="750a8-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="750a8-127">I Windows **PowerShell är en** funktion som anropar **out-Host-sid indelning**.</span><span class="sxs-lookup"><span data-stu-id="750a8-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="750a8-128">Följande kommando visar hur du använder funktionen **more** för att visa utdata från Get-Command:</span><span class="sxs-lookup"><span data-stu-id="750a8-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="750a8-129">Om du inkluderar ett eller flera fil namn som argument för funktionen More, kommer funktionen att läsa de angivna filerna och sidans innehåll till värden:</span><span class="sxs-lookup"><span data-stu-id="750a8-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a><span data-ttu-id="750a8-130">Tar bort utdata (out-null)</span><span class="sxs-lookup"><span data-stu-id="750a8-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="750a8-131">Cmdleten out-null är utformad för att omedelbart ta bort de **inloggade inaktuella inaktuella** .</span><span class="sxs-lookup"><span data-stu-id="750a8-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="750a8-132">Detta är användbart för att ta bort onödiga data som du får som en sido effekt av att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="750a8-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="750a8-133">När du skriver följande kommando får du inte tillbaka något från kommandot:</span><span class="sxs-lookup"><span data-stu-id="750a8-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="750a8-134">Cmdleten **out-null** ignorerar inte fel utdata.</span><span class="sxs-lookup"><span data-stu-id="750a8-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="750a8-135">Om du till exempel anger följande kommando visas ett meddelande som talar om att Windows PowerShell inte känner igen "NotACommand":</span><span class="sxs-lookup"><span data-stu-id="750a8-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a><span data-ttu-id="750a8-136">Skriva ut data (ut-skrivare)</span><span class="sxs-lookup"><span data-stu-id="750a8-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="750a8-137">Du kan skriva ut data med hjälp av cmdleten **out-Printer** .</span><span class="sxs-lookup"><span data-stu-id="750a8-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="750a8-138">Cmdleten **out-Printer** använder standard skrivaren om du inte anger något skrivar namn.</span><span class="sxs-lookup"><span data-stu-id="750a8-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="750a8-139">Du kan använda valfri Windows-baserad skrivare genom att ange dess visnings namn.</span><span class="sxs-lookup"><span data-stu-id="750a8-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="750a8-140">Det finns inget behov av någon typ av skrivar port mappning eller till och med en riktig fysisk skrivare.</span><span class="sxs-lookup"><span data-stu-id="750a8-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="750a8-141">Om du till exempel har installerat Microsoft Office Document Imaging Tools kan du skicka data till en bildfil genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="750a8-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a><span data-ttu-id="750a8-142">Spara data (Out-File)</span><span class="sxs-lookup"><span data-stu-id="750a8-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="750a8-143">Du kan skicka utdata till en fil i stället för konsol fönstret genom att använda cmdleten **Out-File** .</span><span class="sxs-lookup"><span data-stu-id="750a8-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="750a8-144">Följande kommando rad skickar en lista över processer till filen **C:\\Temp\\processlist. txt**:</span><span class="sxs-lookup"><span data-stu-id="750a8-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="750a8-145">Resultatet av att använda cmdleten **Out-File** är kanske inte det du förväntar dig om du använder traditionell omdirigering av utdata.</span><span class="sxs-lookup"><span data-stu-id="750a8-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="750a8-146">För att förstå dess beteende måste du vara medveten om kontexten där cmdleten **Out-File** fungerar.</span><span class="sxs-lookup"><span data-stu-id="750a8-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="750a8-147">Som standard skapar cmdleten **Out-File** en Unicode-fil.</span><span class="sxs-lookup"><span data-stu-id="750a8-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="750a8-148">Detta är det bästa standardvärdet för lång körning, men det innebär att verktyg som förväntar sig att ASCII-filer inte fungerar korrekt med standardformatet för utdata.</span><span class="sxs-lookup"><span data-stu-id="750a8-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="750a8-149">Du kan ändra standardformatet för utdata till ASCII med hjälp av parametern **encoding** :</span><span class="sxs-lookup"><span data-stu-id="750a8-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="750a8-150">Fil innehåll i **fil** format är fil innehåll som ser ut som konsol utdata.</span><span class="sxs-lookup"><span data-stu-id="750a8-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="750a8-151">Detta gör att utdata trunkeras precis som i ett konsol fönster i de flesta fall.</span><span class="sxs-lookup"><span data-stu-id="750a8-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="750a8-152">Om du till exempel kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="750a8-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="750a8-153">Utdata kommer att se ut så här:</span><span class="sxs-lookup"><span data-stu-id="750a8-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="750a8-154">Om du vill hämta utdata som inte tvingar rad brytningar att matcha skärm bredden kan du använda parametern **width** för att ange linje bredd.</span><span class="sxs-lookup"><span data-stu-id="750a8-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="750a8-155">Eftersom **width** är en 32-bitars heltals parameter kan det högsta värdet vara 2147483647.</span><span class="sxs-lookup"><span data-stu-id="750a8-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="750a8-156">Skriv följande för att ställa in linje bredden på det maximala värdet:</span><span class="sxs-lookup"><span data-stu-id="750a8-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="750a8-157">Cmdleten **Out-File** är mest användbar när du vill spara utdata som den skulle ha visat i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="750a8-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="750a8-158">Du behöver mer avancerade verktyg för bättre kontroll över utdataformatet.</span><span class="sxs-lookup"><span data-stu-id="750a8-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="750a8-159">Vi ska titta på dem i nästa kapitel, tillsammans med information om objekt manipulation.</span><span class="sxs-lookup"><span data-stu-id="750a8-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>
