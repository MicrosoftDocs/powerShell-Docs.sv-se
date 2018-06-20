---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Omdirigera data med Out-cmdletar
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 3ca7984e831a995e80cbd8a4d83ae9225c2a4f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952128"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="204f2-103">Omdirigera Data med Out-\* Cmdlets</span><span class="sxs-lookup"><span data-stu-id="204f2-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="204f2-104">Windows PowerShell innehåller flera cmdlets som låter dig styra data utdata direkt.</span><span class="sxs-lookup"><span data-stu-id="204f2-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="204f2-105">Dessa cmdletar har två viktiga egenskaper.</span><span class="sxs-lookup"><span data-stu-id="204f2-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="204f2-106">Först transformera de vanligtvis data till någon form av text.</span><span class="sxs-lookup"><span data-stu-id="204f2-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="204f2-107">Det gör de eftersom de utdata för systemkomponenter i som kräver indata från text.</span><span class="sxs-lookup"><span data-stu-id="204f2-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="204f2-108">Det innebär att de behöver för att representera objekt som text.</span><span class="sxs-lookup"><span data-stu-id="204f2-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="204f2-109">Texten är därför formaterad som det visas i fönstret Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="204f2-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="204f2-110">Sedan använder dessa cmdlets i Windows PowerShell-verb **ut** eftersom de skicka information från Windows PowerShell till någon annanstans.</span><span class="sxs-lookup"><span data-stu-id="204f2-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="204f2-111">Den **ut värd** cmdlet är inget undantag: visningen värden som ligger utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="204f2-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="204f2-112">Detta är viktigt eftersom när data skickas utanför Windows PowerShell, den tas bort.</span><span class="sxs-lookup"><span data-stu-id="204f2-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="204f2-113">Du kan se dessa om du försöker skapa en pipeline sidor data till fönstret värden och försök sedan att formatera som en lista som visas här:</span><span class="sxs-lookup"><span data-stu-id="204f2-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="204f2-114">Du kan förvänta sig kommandot för att visa sidor i processinformation i listformat.</span><span class="sxs-lookup"><span data-stu-id="204f2-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="204f2-115">I stället visas listan över tabeller som standard:</span><span class="sxs-lookup"><span data-stu-id="204f2-115">Instead, it displays the default tabular list:</span></span>

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

<span data-ttu-id="204f2-116">Den **ut värd** cmdlet skickar data direkt till konsolen så **Format-List** kommandot får aldrig något format.</span><span class="sxs-lookup"><span data-stu-id="204f2-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="204f2-117">Det korrekta sättet att struktur det här kommandot är att placera den **ut värd** cmdlet i slutet av pipeline enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="204f2-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="204f2-118">Detta medför processdata ska formateras i en lista före som växlingsbart och visas.</span><span class="sxs-lookup"><span data-stu-id="204f2-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="204f2-119">Detta gäller för alla de **ut** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="204f2-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="204f2-120">En **ut** cmdlet alltid ska visas i slutet av pipeline.</span><span class="sxs-lookup"><span data-stu-id="204f2-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="204f2-121">Alla de **ut** cmdlets återge resultatet som text med den formatering som tillämpas för konsolfönstret, inklusive rad längd gränser.</span><span class="sxs-lookup"><span data-stu-id="204f2-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="204f2-122">Växling konsolens utdata (routningsserver värd)</span><span class="sxs-lookup"><span data-stu-id="204f2-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="204f2-123">Som standard, Windows PowerShell skickar data till fönstret värden som är exakt vad den ut värd för cmdlet har.</span><span class="sxs-lookup"><span data-stu-id="204f2-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="204f2-124">Primär användning för den inkommande värd cmdlet är sidindelning data som har beskrivits tidigare.</span><span class="sxs-lookup"><span data-stu-id="204f2-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="204f2-125">Till exempel värdar följande kommando använder ut till sidan utdata från cmdleten Get-Command:</span><span class="sxs-lookup"><span data-stu-id="204f2-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="204f2-126">Du kan också använda den **mer** siddata av funktionen.</span><span class="sxs-lookup"><span data-stu-id="204f2-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="204f2-127">I Windows PowerShell **mer** är en funktion som anropar **ut värd-växling**.</span><span class="sxs-lookup"><span data-stu-id="204f2-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="204f2-128">Följande kommando visas hur du använder den **mer** funktion på sidan Get-kommandot:</span><span class="sxs-lookup"><span data-stu-id="204f2-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="204f2-129">Om du inkluderar ett eller flera filnamn som argument till funktionen mer funktionen läsa de angivna filerna och sidan innehållet till värden:</span><span class="sxs-lookup"><span data-stu-id="204f2-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="204f2-130">Ignorera utdata (routningsserver Null)</span><span class="sxs-lookup"><span data-stu-id="204f2-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="204f2-131">Den **ut Null** cmdlet är utformat för att direkt ta bort alla indata som tas emot.</span><span class="sxs-lookup"><span data-stu-id="204f2-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="204f2-132">Detta är användbart för att ta bort onödiga data som är tillgängliga som en sidoeffekt av ett kommando körs.</span><span class="sxs-lookup"><span data-stu-id="204f2-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="204f2-133">När skriver du följande kommando, du får inte något tillbaka från kommandot:</span><span class="sxs-lookup"><span data-stu-id="204f2-133">When type the following command, you do not get anything back from the command:</span></span>

```powreshell
Get-Command | Out-Null
```

<span data-ttu-id="204f2-134">Den **ut Null** cmdlet tar inte bort Felutdata.</span><span class="sxs-lookup"><span data-stu-id="204f2-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="204f2-135">Till exempel om du anger följande kommando, visas ett meddelande informerar dig om att Windows PowerShell inte känner igen 'Är NotACommand':</span><span class="sxs-lookup"><span data-stu-id="204f2-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="204f2-136">Data för utskrift (Out-skrivare)</span><span class="sxs-lookup"><span data-stu-id="204f2-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="204f2-137">Du kan skriva ut data med hjälp av den **Out-skrivare** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="204f2-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="204f2-138">Den **Out-skrivare** cmdlet använder standardskrivaren om du inte anger namnet på en skrivare.</span><span class="sxs-lookup"><span data-stu-id="204f2-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="204f2-139">Du kan använda alla Windows-baserade skrivare genom att ange dess namn.</span><span class="sxs-lookup"><span data-stu-id="204f2-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="204f2-140">Det behövs ingen för alla typer av skrivare portmappning eller även verkliga fysiska skrivare.</span><span class="sxs-lookup"><span data-stu-id="204f2-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="204f2-141">Om du har Microsoft Office-dokument avbildning verktygen som installeras kan kan du till exempel skicka data till en bildfil genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="204f2-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="204f2-142">Spara Data (out-File)</span><span class="sxs-lookup"><span data-stu-id="204f2-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="204f2-143">Du kan skicka utdata till en fil i stället för konsolfönstret med hjälp av den **out-File** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="204f2-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="204f2-144">Följande kommandorad skickar en lista över processer till filen **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="204f2-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="204f2-145">Resultatet av att använda den **out-File** cmdlet kanske inte som du förväntar dig om du för omdirigering av traditionella utdata.</span><span class="sxs-lookup"><span data-stu-id="204f2-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="204f2-146">För att förstå sitt beteende, måste du vara medveten om kontexten där den **out-File** cmdlet fungerar.</span><span class="sxs-lookup"><span data-stu-id="204f2-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="204f2-147">Som standard den **out-File** cmdlet skapar en Unicode-fil.</span><span class="sxs-lookup"><span data-stu-id="204f2-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="204f2-148">Detta är den bästa standardvärdet på lång sikt, men innebär det att verktyg som ASCII-filer ska fungera korrekt med standardformatet för utdata.</span><span class="sxs-lookup"><span data-stu-id="204f2-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="204f2-149">Du kan ändra standardformatet för utdata till ASCII med hjälp av den **kodning** parameter:</span><span class="sxs-lookup"><span data-stu-id="204f2-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="204f2-150">**Out-File** format filinnehåll ska se ut som konsolens utdata.</span><span class="sxs-lookup"><span data-stu-id="204f2-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="204f2-151">Detta leder till utdata till trunkeras precis som i ett konsolfönster i de flesta fall.</span><span class="sxs-lookup"><span data-stu-id="204f2-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="204f2-152">Till exempel om du kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="204f2-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="204f2-153">Resultatet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="204f2-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="204f2-154">Du kan använda för att hämta utdata som inte tvingar rad radbryter att matcha skärmbredden på **bredd** parametern för att ange linjebredd.</span><span class="sxs-lookup"><span data-stu-id="204f2-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="204f2-155">Eftersom **bredd** är en 32-bitars heltal-parameter kan ha maxvärdet är 2147483647.</span><span class="sxs-lookup"><span data-stu-id="204f2-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="204f2-156">Skriv följande för att ange bredden för den här högsta värdet:</span><span class="sxs-lookup"><span data-stu-id="204f2-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="204f2-157">Den **out-File** cmdlet är användbar när du vill spara utdata som den skulle ha visas på konsolen.</span><span class="sxs-lookup"><span data-stu-id="204f2-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="204f2-158">Du behöver mer avancerade verktyg får bättre kontroll över utdataformat.</span><span class="sxs-lookup"><span data-stu-id="204f2-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="204f2-159">Vi ska titta på de i nästa kapitel, tillsammans med information om objektet manipulation.</span><span class="sxs-lookup"><span data-stu-id="204f2-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>