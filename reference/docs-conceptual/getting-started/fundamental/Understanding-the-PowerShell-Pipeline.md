---
ms.date: 08/23/2018
keywords: PowerShell cmdlet
title: Förstå PowerShell-förlopp
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: fc7c7f57bdce458185a0f5bdb8bc1fbbd81d0d61
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002863"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="7167d-103">Förstå pipelines</span><span class="sxs-lookup"><span data-stu-id="7167d-103">Understanding pipelines</span></span>

<span data-ttu-id="7167d-104">Pipelines fungerar som en serie med anslutna pipe-segment.</span><span class="sxs-lookup"><span data-stu-id="7167d-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="7167d-105">Artiklar som flyttas längsmed pipelinen släpper igenom varje segment.</span><span class="sxs-lookup"><span data-stu-id="7167d-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="7167d-106">Om du vill skapa en pipeline i PowerShell som du ansluter kommandon tillsammans med operatorn ”|”.</span><span class="sxs-lookup"><span data-stu-id="7167d-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="7167d-107">Utdata för varje kommando används som indata till nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="7167d-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="7167d-108">Notation används för pipelines liknar beteckningen används i andra gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7167d-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="7167d-109">Vid en första titt kanske det inte tydligt hur skiljer sig pipelines i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7167d-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="7167d-110">Även om du ser text på skärmen, kommer objekt inte text mellan kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7167d-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="7167d-111">PowerShell-pipelinen</span><span class="sxs-lookup"><span data-stu-id="7167d-111">The PowerShell pipeline</span></span>

<span data-ttu-id="7167d-112">Pipeliner är utan tvekan den mest värdefulla begrepp som används i kommandoradsverktyget gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7167d-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="7167d-113">När detta används korrekt kan minska arbetet med att använda komplexa kommandon pipelines och gör det lättare att se arbetsflödet för kommandon.</span><span class="sxs-lookup"><span data-stu-id="7167d-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="7167d-114">Varje kommando i en pipeline (kallas en pipeline-elementet) skickar sina utdata till nästa kommando i pipeline-post.</span><span class="sxs-lookup"><span data-stu-id="7167d-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="7167d-115">Kommandon har inte kan hantera mer än ett objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="7167d-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="7167d-116">Resultatet är lägre resursförbrukning och möjligheten att börja hämta utdata direkt.</span><span class="sxs-lookup"><span data-stu-id="7167d-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="7167d-117">Exempel: Om du använder den `Out-Host` cmdlet för att framtvinga en sida för sida visning av utdata från ett annat kommando, de utdata ser ut precis som den normala texten som visas på skärmen som delats upp i sidor:</span><span class="sxs-lookup"><span data-stu-id="7167d-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

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

<span data-ttu-id="7167d-118">Växling också minskar CPU-belastningen eftersom bearbetning överförs till den `Out-Host` cmdlet när den har en hel sida som är redo att visa.</span><span class="sxs-lookup"><span data-stu-id="7167d-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="7167d-119">De cmdletar som redan har infogats i pipelinen Pausa körning tills nästa sida i utdata är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="7167d-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="7167d-120">Du kan se skillnaden Windows Aktivitetshanteraren för att övervaka CPU och minne som används av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7167d-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="7167d-121">Kör följande kommando: `Get-ChildItem C:\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="7167d-121">Run the following command: `Get-ChildItem C:\Windows -Recurse`.</span></span> <span data-ttu-id="7167d-122">Jämför användningen av processor och minne det här kommandot: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="7167d-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`.</span></span>

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="7167d-123">Objekt i pipelinen</span><span class="sxs-lookup"><span data-stu-id="7167d-123">Objects in the pipeline</span></span>

<span data-ttu-id="7167d-124">När du kör en cmdlet i PowerShell, se textutdata eftersom det är nödvändigt att representera objekt som text i ett konsolfönster.</span><span class="sxs-lookup"><span data-stu-id="7167d-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="7167d-125">Text-utdata visas inte alla egenskaper i objektet som utdata.</span><span class="sxs-lookup"><span data-stu-id="7167d-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="7167d-126">Anta exempelvis att den `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7167d-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="7167d-127">Om du kör `Get-Location` din aktuella plats är roten på C-enheten, finns i följande utdata:</span><span class="sxs-lookup"><span data-stu-id="7167d-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="7167d-128">Textutdata är en sammanfattning av informationen, inte en fullständig återgivning av objektet som returnerades av `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="7167d-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="7167d-129">Rubriken i utdata har lagts till via processen som formaterar data för visning på skärmen.</span><span class="sxs-lookup"><span data-stu-id="7167d-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="7167d-130">När du skicka utdata till den `Get-Member` cmdlet du få information om objektet som returnerades av `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="7167d-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
PS> Get-Location | Get-Member
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

<span data-ttu-id="7167d-131">`Get-Location` Returnerar en **PathInfo** objekt som innehåller den aktuella sökvägen och annan information.</span><span class="sxs-lookup"><span data-stu-id="7167d-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>
