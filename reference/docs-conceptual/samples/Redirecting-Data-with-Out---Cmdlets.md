---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Omdirigera data med Out-cmdletar
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: f08879f436ce751b176af020aba21e90f09aa61f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687141"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="e7e15-103">Omdirigera Data med Out-\* cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="e7e15-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="e7e15-104">Windows PowerShell innehåller flera cmdletar som låter dig styra data utdata direkt.</span><span class="sxs-lookup"><span data-stu-id="e7e15-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="e7e15-105">Dessa cmdletar har två viktiga egenskaper.</span><span class="sxs-lookup"><span data-stu-id="e7e15-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="e7e15-106">Först måste omvandla de vanligtvis data till någon form av text.</span><span class="sxs-lookup"><span data-stu-id="e7e15-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="e7e15-107">De göra det eftersom de mata ut data till systemkomponenter som behöver mata in text.</span><span class="sxs-lookup"><span data-stu-id="e7e15-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="e7e15-108">Det innebär att de behöver för att representera objekt som text.</span><span class="sxs-lookup"><span data-stu-id="e7e15-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="e7e15-109">Därför formateras texten som syns i Windows PowerShell-konsolfönster.</span><span class="sxs-lookup"><span data-stu-id="e7e15-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="e7e15-110">Sedan dessa cmdletar använder Windows PowerShell-verb **ut** eftersom de skicka information från Windows PowerShell till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="e7e15-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="e7e15-111">Den **ut värd** cmdlet är inget undantag: visningen värden som ligger utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7e15-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="e7e15-112">Detta är viktigt eftersom när data skickas ut från Windows PowerShell, den tas bort.</span><span class="sxs-lookup"><span data-stu-id="e7e15-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="e7e15-113">Du kan se om du försöker skapa en pipeline som sidor-data till fönstret värden och försök sedan att formatera den som en lista som visas här:</span><span class="sxs-lookup"><span data-stu-id="e7e15-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="e7e15-114">Du kan förvänta dig kommandot för att visa sidor i processinformation i listformat.</span><span class="sxs-lookup"><span data-stu-id="e7e15-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="e7e15-115">I stället visas listan över tabular:</span><span class="sxs-lookup"><span data-stu-id="e7e15-115">Instead, it displays the default tabular list:</span></span>

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

<span data-ttu-id="e7e15-116">Den **ut värd** cmdleten skickar data direkt till konsolen så **Format-List** kommando får aldrig något ska formateras.</span><span class="sxs-lookup"><span data-stu-id="e7e15-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="e7e15-117">Det korrekta sättet att strukturera det här kommandot är att placera den **ut värd** cmdlet i slutet av pipelinen enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="e7e15-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="e7e15-118">Detta leder till processdata ska vara formaterad i en lista innan du kan växlat minne och visas.</span><span class="sxs-lookup"><span data-stu-id="e7e15-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="e7e15-119">Detta gäller för alla de **ut** cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e7e15-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="e7e15-120">En **ut** cmdlet alltid ska visas i slutet av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e7e15-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="e7e15-121">Alla de **ut** cmdletar återges resultatet som text med formateringen gäller för konsolfönstret, inklusive rad längd gränser.</span><span class="sxs-lookup"><span data-stu-id="e7e15-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="e7e15-122">Växling konsolens utdata (ut värd)</span><span class="sxs-lookup"><span data-stu-id="e7e15-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="e7e15-123">Som standard, Windows PowerShell skickar data till fönstret värd, vilket är exakt vad de ut värd cmdlet gör.</span><span class="sxs-lookup"><span data-stu-id="e7e15-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="e7e15-124">Primär användning för den värd ut cmdlet är sidindelning data som har beskrivits tidigare.</span><span class="sxs-lookup"><span data-stu-id="e7e15-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="e7e15-125">Till exempel följande kommando använder ut att ha till sidan utdata från Get-Command-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e7e15-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="e7e15-126">Du kan också använda den **mer** att siddata.</span><span class="sxs-lookup"><span data-stu-id="e7e15-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="e7e15-127">I Windows PowerShell **mer** är en funktion som anropar **ut värd-växling**.</span><span class="sxs-lookup"><span data-stu-id="e7e15-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="e7e15-128">Följande kommando visar hur du använder den **mer** att sidan utdata från Get-kommandot:</span><span class="sxs-lookup"><span data-stu-id="e7e15-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="e7e15-129">Om du anger ett eller flera filnamn som argument till funktionen mer funktionen läser de angivna filerna och sidan innehållet till värden:</span><span class="sxs-lookup"><span data-stu-id="e7e15-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="e7e15-130">Tar bort utdata (ut Null)</span><span class="sxs-lookup"><span data-stu-id="e7e15-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="e7e15-131">Den **ut Null** cmdlet har utformats för att omedelbart ta bort några indata som tas emot.</span><span class="sxs-lookup"><span data-stu-id="e7e15-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="e7e15-132">Detta är användbart för att ta bort onödiga data som är tillgängliga som en sidoeffekt av som kör ett kommando.</span><span class="sxs-lookup"><span data-stu-id="e7e15-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="e7e15-133">När skriver du följande kommando, du får inte något tillbaka från kommandot:</span><span class="sxs-lookup"><span data-stu-id="e7e15-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="e7e15-134">Den **ut Null** cmdlet tar inte bort utdata om felet.</span><span class="sxs-lookup"><span data-stu-id="e7e15-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="e7e15-135">Till exempel om du anger du följande kommando, meddelande ett informerar dig om att Windows PowerShell inte känner igen ”är NotACommand':</span><span class="sxs-lookup"><span data-stu-id="e7e15-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="e7e15-136">Data för utskrift (Out-skrivare)</span><span class="sxs-lookup"><span data-stu-id="e7e15-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="e7e15-137">Du kan skriva ut data med hjälp av den **Out-skrivare** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e7e15-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="e7e15-138">Den **Out-skrivare** cmdlet använder standardskrivaren om du inte anger namnet på en skrivare.</span><span class="sxs-lookup"><span data-stu-id="e7e15-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="e7e15-139">Du kan använda valfri Windows-baserade skrivare genom att ange dess namn.</span><span class="sxs-lookup"><span data-stu-id="e7e15-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="e7e15-140">Det finns inget behov av alla slags skrivare portmappning och även en riktig fysisk skrivare.</span><span class="sxs-lookup"><span data-stu-id="e7e15-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="e7e15-141">Om du har Microsoft Office-dokument avbildning verktygen som installeras kan kan du till exempel skicka data till en bildfil genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="e7e15-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="e7e15-142">Sparar Data (out-File)</span><span class="sxs-lookup"><span data-stu-id="e7e15-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="e7e15-143">Du kan skicka utdata till en fil i stället för konsolfönstret genom att använda den **out-File** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e7e15-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="e7e15-144">Följande kommandorad skickar en lista över processer till filen **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="e7e15-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="e7e15-145">Resultatet av att använda den **out-File** cmdlet kanske inte vad du förväntar dig om du är van att omdirigering av traditionella utdata.</span><span class="sxs-lookup"><span data-stu-id="e7e15-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="e7e15-146">För att förstå dess beteende, måste du vara medveten om kontexten där den **out-File** cmdlet fungerar.</span><span class="sxs-lookup"><span data-stu-id="e7e15-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="e7e15-147">Som standard den **out-File** cmdlet skapar en Unicode-fil.</span><span class="sxs-lookup"><span data-stu-id="e7e15-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="e7e15-148">Det här är den bästa standarden på lång sikt, men det innebär att verktyg som räknar ASCII-filer inte fungerar korrekt med format för standardutdata.</span><span class="sxs-lookup"><span data-stu-id="e7e15-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="e7e15-149">Du kan ändra format för standardutdata till ASCII med hjälp av den **Encoding** parameter:</span><span class="sxs-lookup"><span data-stu-id="e7e15-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="e7e15-150">**Out-File** format filinnehåll ska se ut som konsolens utdata.</span><span class="sxs-lookup"><span data-stu-id="e7e15-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="e7e15-151">Detta leder till utdata till trunkeras precis som i ett konsolfönster i de flesta fall.</span><span class="sxs-lookup"><span data-stu-id="e7e15-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="e7e15-152">Exempel: Om du kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="e7e15-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="e7e15-153">Utdata ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="e7e15-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="e7e15-154">Du kan använda för att få utdata som inte tvingar rad radbryter så att den matchar skärmbredden kan den **bredd** parametern för att ange bredden.</span><span class="sxs-lookup"><span data-stu-id="e7e15-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="e7e15-155">Eftersom **bredd** är en 32-bitars heltal-parameter, det högsta värdet som den kan ha är 2147483647.</span><span class="sxs-lookup"><span data-stu-id="e7e15-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="e7e15-156">Skriv följande för att ange bredden för den här högsta värdet:</span><span class="sxs-lookup"><span data-stu-id="e7e15-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="e7e15-157">Den **out-File** cmdlet är mest användbara när du vill spara utdata som det skulle ha visas på konsolen.</span><span class="sxs-lookup"><span data-stu-id="e7e15-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="e7e15-158">För mer detaljerad kontroll över utdataformat behöver du mer avancerade verktyg.</span><span class="sxs-lookup"><span data-stu-id="e7e15-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="e7e15-159">Vi ska titta på dem i nästa kapitel, tillsammans med viss information om manipulering av objekt.</span><span class="sxs-lookup"><span data-stu-id="e7e15-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>