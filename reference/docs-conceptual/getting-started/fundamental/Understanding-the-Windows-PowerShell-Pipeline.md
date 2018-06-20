---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Förstå PowerShell-pipelinen
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: c3f1d17432cf3a77c0f5ecae137a4233a28a19d7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951077"
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="b422f-103">Förstå PowerShell-pipelinen</span><span class="sxs-lookup"><span data-stu-id="b422f-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="b422f-104">Rörnät fungerar praktiskt taget överallt i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b422f-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="b422f-105">Även om du ser texten på skärmen, Windows PowerShell inte att skicka text mellan kommandon.</span><span class="sxs-lookup"><span data-stu-id="b422f-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="b422f-106">Den kommer i stället objekt.</span><span class="sxs-lookup"><span data-stu-id="b422f-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="b422f-107">Det format som används för pipelines är liknande som används i andra så vid en första titt, kanske inte tydligt att Windows PowerShell innehåller något nytt.</span><span class="sxs-lookup"><span data-stu-id="b422f-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="b422f-108">Till exempel om du använder den **ut värd** att framtvinga en varje sida visning av utdata från ett annat kommando, utdata söker precis som den normala texten som visas på skärmen, uppdelade sidor:</span><span class="sxs-lookup"><span data-stu-id="b422f-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="b422f-109">Out-Host-sidindelning kommandot är en användbar pipeline-elementet när du har långa utdata som du vill visa långsamt.</span><span class="sxs-lookup"><span data-stu-id="b422f-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="b422f-110">Det är särskilt användbart om åtgärden är mycket processorintensiva.</span><span class="sxs-lookup"><span data-stu-id="b422f-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="b422f-111">Eftersom bearbetning överförs till den inkommande värd cmdlet när den har en hel sida som är redo att visa cmdlets som föregår i pipelinen stoppa åtgärden tills nästa sida i utdata är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="b422f-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="b422f-112">Du kan se dessa om du använder Aktivitetshanteraren för att övervaka CPU och minne används av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b422f-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="b422f-113">Kör följande kommando: **Get-ChildItem C:\\Windows-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="b422f-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="b422f-114">Jämför processor- och minnesanvändning för det här kommandot: **Get-ChildItem C:\\Windows-Recurse | Routningsserver Host-växling**.</span><span class="sxs-lookup"><span data-stu-id="b422f-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="b422f-115">Vad som visas på skärmen är text, men det beror på att det är nödvändigt för att representera objekt som text i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="b422f-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="b422f-116">Detta är bara en representation av vad är verkligen pågår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b422f-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="b422f-117">Anta till exempel att cmdleten Get-plats.</span><span class="sxs-lookup"><span data-stu-id="b422f-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="b422f-118">Om du anger **Get-plats** din aktuella plats är roten på enhet C, visas följande utdata:</span><span class="sxs-lookup"><span data-stu-id="b422f-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="b422f-119">Om Windows PowerShell pipeline text, utfärda ett kommando som **Get-plats | Värd för inkommande**, skulle skickas från **Get-plats** till **ut värd** en uppsättning tecken i den ordning de visas på skärmen.</span><span class="sxs-lookup"><span data-stu-id="b422f-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="b422f-120">Med andra ord, om du ignorerar rubrikinformationen, **ut värd** kommer först att ta emot tecknet '**C'**, sedan tecknet '**:'**, sedan tecknet ' **\\'**.</span><span class="sxs-lookup"><span data-stu-id="b422f-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="b422f-121">Den **ut värd** cmdlet kunde inte avgöra vilka vilket innebär att associera med tecken resultatet av den **Get-plats** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b422f-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="b422f-122">I stället för text för att kommandon i en pipeline kommunicera Windows PowerShell använder objekt.</span><span class="sxs-lookup"><span data-stu-id="b422f-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="b422f-123">När gäller för en användare objekt paketet relaterad information i ett formulär som gör det enklare att manipulera informationen som en enhet och extrahera specifika objekt som du behöver.</span><span class="sxs-lookup"><span data-stu-id="b422f-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="b422f-124">Den **Get-plats** inte returnerar text som innehåller den aktuella sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b422f-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="b422f-125">Den returnerar ett paket med information som kallas en **PathInfo** objekt som innehåller den aktuella sökvägen tillsammans med annan information.</span><span class="sxs-lookup"><span data-stu-id="b422f-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="b422f-126">Den **ut värd** cmdlet skickar sedan detta **PathInfo** objekt till skärmen och Windows PowerShell bestämmer vad information som ska visas och hur det ska visas baserat på dess formateringsregler.</span><span class="sxs-lookup"><span data-stu-id="b422f-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="b422f-127">I själva verket rubrikinformationen utdata genom att den **Get-plats** cmdlet läggs endast i slutet av processen, som en del av processen för att formatera data för visning på skärmen.</span><span class="sxs-lookup"><span data-stu-id="b422f-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="b422f-128">Vad som visas på skärmen är en sammanfattning av information och inte en fullständig representation av utdata-objektet.</span><span class="sxs-lookup"><span data-stu-id="b422f-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="b422f-129">Med hänsyn till att det kan finnas mer information utdata från en Windows PowerShell kommando än vad vi se visas i konsolfönstret, hur kan du hämta icke-synliga element?</span><span class="sxs-lookup"><span data-stu-id="b422f-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="b422f-130">Hur visar du extra data?</span><span class="sxs-lookup"><span data-stu-id="b422f-130">How do you view the extra data?</span></span> <span data-ttu-id="b422f-131">Och om du vill visa data i ett format som skiljer sig en Windows PowerShell normalt använder?</span><span class="sxs-lookup"><span data-stu-id="b422f-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="b422f-132">Resten av det här kapitlet beskrivs hur du kan identifiera strukturen för specifika objekt i Windows PowerShell, välja specifika objekt och formatera dem för enklare visning och hur du skickar informationen till alternativa utdatafilerna som filer och skrivare.</span><span class="sxs-lookup"><span data-stu-id="b422f-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>