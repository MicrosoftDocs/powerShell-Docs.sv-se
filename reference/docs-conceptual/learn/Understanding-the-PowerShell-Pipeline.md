---
ms.date: 08/23/2018
keywords: PowerShell, cmdlet
title: Förstå PowerShell-pipeliner
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030388"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="3733c-103">Förstå pipelines</span><span class="sxs-lookup"><span data-stu-id="3733c-103">Understanding pipelines</span></span>

<span data-ttu-id="3733c-104">Pipelines fungerar som en serie anslutna segment av en pipe.</span><span class="sxs-lookup"><span data-stu-id="3733c-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="3733c-105">Objekt som flyttas utmed pipelinen passerar varje segment.</span><span class="sxs-lookup"><span data-stu-id="3733c-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="3733c-106">Om du vill skapa en pipeline i PowerShell ansluter du kommandon tillsammans med pipe-operatorn "|".</span><span class="sxs-lookup"><span data-stu-id="3733c-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="3733c-107">Utdata från varje kommando används som indata till nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="3733c-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="3733c-108">Den notation som används för pipelines liknar den notation som används i andra gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="3733c-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="3733c-109">I första hand kan det vara inte uppenbart hur pipelines skiljer sig i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3733c-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="3733c-110">Även om du ser text på skärmen, PowerShell pipe-objekt, inte text, mellan kommandon.</span><span class="sxs-lookup"><span data-stu-id="3733c-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="3733c-111">PowerShell-pipeline</span><span class="sxs-lookup"><span data-stu-id="3733c-111">The PowerShell pipeline</span></span>

<span data-ttu-id="3733c-112">Pipelines är utan tvekan det mest värdefulla konceptet som används i kommando rads gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="3733c-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="3733c-113">När pipelinen används korrekt minskar pipelinen arbetet med att använda komplexa kommandon och gör det lättare att se arbets flödet för kommandona.</span><span class="sxs-lookup"><span data-stu-id="3733c-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="3733c-114">Varje kommando i en pipeline (kallas ett pipeline-element) skickar utdata till nästa-kommando i pipelinen, item-by-Item.</span><span class="sxs-lookup"><span data-stu-id="3733c-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="3733c-115">Kommandon behöver inte hantera mer än ett objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="3733c-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="3733c-116">Resultatet är minskad resursförbrukning och möjligheten att börja få utdata direkt.</span><span class="sxs-lookup"><span data-stu-id="3733c-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="3733c-117">Om du till exempel använder `Out-Host` cmdleten för att tvinga fram visning av utdata från ett annat kommando, ser utdata ut precis som den normala texten som visas på skärmen, och delas upp i sidor:</span><span class="sxs-lookup"><span data-stu-id="3733c-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="3733c-118">Växlingen minskar också processor användningen eftersom bearbetningen överförs till `Out-Host` cmdleten när en hel sida är klar att visas.</span><span class="sxs-lookup"><span data-stu-id="3733c-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="3733c-119">Cmdletarna som föregår den i pipelinen pausar körningen tills nästa sida med utdata är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="3733c-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="3733c-120">Du kan se hur rörledning påverkar processor-och minnes användning i aktivitets hanteraren genom att jämföra följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="3733c-120">You can see how piping impacts CPU and memory usage in the Windows Task Manager by comparing the following commands:</span></span>

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> <span data-ttu-id="3733c-121">**Växlings** parametern stöds inte av alla PowerShell-värdar.</span><span class="sxs-lookup"><span data-stu-id="3733c-121">The **Paging** parameter is not supported by all PowerShell hosts.</span></span> <span data-ttu-id="3733c-122">När du till exempel försöker använda **växlings** parametern i PowerShell ISE visas följande fel:</span><span class="sxs-lookup"><span data-stu-id="3733c-122">For example, when you try to use the **Paging** parameter in the PowerShell ISE, you see the following error:</span></span>
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="3733c-123">Objekt i pipelinen</span><span class="sxs-lookup"><span data-stu-id="3733c-123">Objects in the pipeline</span></span>

<span data-ttu-id="3733c-124">När du kör en cmdlet i PowerShell visas text utdata eftersom det är nödvändigt att representera objekt som text i ett konsol fönster.</span><span class="sxs-lookup"><span data-stu-id="3733c-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="3733c-125">Text utmatningen kanske inte visar alla egenskaper för objektet som ska skrivas ut.</span><span class="sxs-lookup"><span data-stu-id="3733c-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="3733c-126">Överväg till exempel `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3733c-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="3733c-127">Om du kör `Get-Location` medan din aktuella plats är roten på C-enheten visas följande utdata:</span><span class="sxs-lookup"><span data-stu-id="3733c-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="3733c-128">Text utmatningen är en sammanfattning av informationen, inte en fullständig representation av det objekt som `Get-Location`returnerades av.</span><span class="sxs-lookup"><span data-stu-id="3733c-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="3733c-129">Rubriken i utdata läggs till av processen som formaterar data för skärm visning.</span><span class="sxs-lookup"><span data-stu-id="3733c-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="3733c-130">När du skickar utdata till `Get-Member` cmdleten får du information om det objekt som returnerades `Get-Location`av.</span><span class="sxs-lookup"><span data-stu-id="3733c-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="3733c-131">`Get-Location`Returnerar ett **PathInfo** -objekt som innehåller den aktuella sökvägen och annan information.</span><span class="sxs-lookup"><span data-stu-id="3733c-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
