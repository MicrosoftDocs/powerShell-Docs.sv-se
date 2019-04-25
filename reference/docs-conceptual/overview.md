---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: PowerShell Scripting
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058496"
---
# <a name="powershell"></a><span data-ttu-id="d7057-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d7057-103">PowerShell</span></span>

<span data-ttu-id="d7057-104">PowerShell är ett uppgiftsbaserat kommandoradsgränssnitt och skriptspråk som bygger på .NET.</span><span class="sxs-lookup"><span data-stu-id="d7057-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="d7057-105">PowerShell hjälper administratörer och Privilegierade användare automatisera snabbt uppgifter som hanterar operativsystem (Linux, macOS och Windows) och processer.</span><span class="sxs-lookup"><span data-stu-id="d7057-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="d7057-106">PowerShell-kommandon kan du hantera datorer från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="d7057-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="d7057-107">PowerShell-providers kan du få åtkomst till datalager, till exempel registret och certifikatarkivet, lika enkelt som du har åtkomst till filsystemet.</span><span class="sxs-lookup"><span data-stu-id="d7057-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="d7057-108">PowerShell innehåller en omfattande uttrycksparser och ett fullständigt utvecklat skriptspråk.</span><span class="sxs-lookup"><span data-stu-id="d7057-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="d7057-109">PowerShell är öppen källkod</span><span class="sxs-lookup"><span data-stu-id="d7057-109">PowerShell is open-source</span></span>

<span data-ttu-id="d7057-110">PowerShell grundläggande källkoden är nu tillgängligt i GitHub och öppna community-bidrag.</span><span class="sxs-lookup"><span data-stu-id="d7057-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="d7057-111">Se [PowerShell källkod på GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="d7057-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="d7057-112">Du kan börja med bits på [hämta PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="d7057-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="d7057-113">Eller kanske, med en snabb genomgång på [komma igång](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="d7057-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="d7057-114">PowerShell-designmålen</span><span class="sxs-lookup"><span data-stu-id="d7057-114">PowerShell design goals</span></span>

<span data-ttu-id="d7057-115">PowerShell har utformats för att förbättra miljön kommandorad och skript genom att långsiktigt problem och lägga till nya funktioner.</span><span class="sxs-lookup"><span data-stu-id="d7057-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="d7057-116">För att göra</span><span class="sxs-lookup"><span data-stu-id="d7057-116">Discoverability</span></span>

<span data-ttu-id="d7057-117">PowerShell gör det enkelt att identifiera dess funktioner.</span><span class="sxs-lookup"><span data-stu-id="d7057-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="d7057-118">Till exempel för att hitta en lista över cmdlets som Visa och ändra Windows-tjänster, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d7057-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="d7057-119">Efter identifiering av vilka cmdlet uppnår en uppgift, kan du läsa mer om cmdlet: en med hjälp av den `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7057-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="d7057-120">Till exempel vill visa hjälp om den `Get-Service` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="d7057-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="d7057-121">De flesta cmdletar returnerar objekt som kan ändras och sedan renderas som text som ska visas.</span><span class="sxs-lookup"><span data-stu-id="d7057-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="d7057-122">För att helt förstå resultatet av en cmdlet, skicka utdata till den `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7057-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="d7057-123">Till exempel följande kommando visar information om medlemmarna i objektutdata av den `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7057-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="d7057-124">Konsekvens</span><span class="sxs-lookup"><span data-stu-id="d7057-124">Consistency</span></span>

<span data-ttu-id="d7057-125">Hantera system kan vara en komplicerad uppgift.</span><span class="sxs-lookup"><span data-stu-id="d7057-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="d7057-126">Verktyg som har ett konsekvent gränssnitt hjälpa till att styra den inbyggda komplexiteten.</span><span class="sxs-lookup"><span data-stu-id="d7057-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="d7057-127">Tyvärr är inte kommandoradsverktyg och skriptbara COM Component Object Model ()-objekt känt för sin konsekvens.</span><span class="sxs-lookup"><span data-stu-id="d7057-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="d7057-128">Konsekvenskontroll av PowerShell är en av dess primära tillgångar.</span><span class="sxs-lookup"><span data-stu-id="d7057-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="d7057-129">Exempel: Om du lära dig hur du använder den `Sort-Object` cmdlet, du kan använda denna kunskap för att ordna resultatet av en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7057-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="d7057-130">Du behöver att lära dig de olika sortering rutinerna för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7057-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="d7057-131">Dessutom inte cmdlet-utvecklare att utforma sortering funktioner för deras cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d7057-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="d7057-132">PowerShell ger ett ramverk med grundläggande funktioner som tvingar konsekvens.</span><span class="sxs-lookup"><span data-stu-id="d7057-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="d7057-133">Ramverket eliminerar vissa alternativ som är kvar att utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="d7057-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="d7057-134">Men, i utbyte kan det gör utvecklingen av cmdlet: ar mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="d7057-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="d7057-135">Interaktiva och skript miljöer</span><span class="sxs-lookup"><span data-stu-id="d7057-135">Interactive and scripting environments</span></span>

<span data-ttu-id="d7057-136">Windows-kommandotolk innehåller ett interaktivt gränssnitt med åtkomst till kommandoradsverktyg och basic-skript.</span><span class="sxs-lookup"><span data-stu-id="d7057-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="d7057-137">Windows Script Host (WSH) har skriptbara kommandoradsverktyg och COM automation-objekt, men tillhandahåller inte ett interaktivt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="d7057-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="d7057-138">PowerShell kombinerar ett interaktivt gränssnitt och en skriptmiljö.</span><span class="sxs-lookup"><span data-stu-id="d7057-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="d7057-139">PowerShell kan komma åt kommandoradsverktyg, COM-objekt och .NET-klassbibliotek.</span><span class="sxs-lookup"><span data-stu-id="d7057-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="d7057-140">Kombinationen av funktioner utökar funktionerna i den interaktiva användaren skrivar-skript och systemadministratören.</span><span class="sxs-lookup"><span data-stu-id="d7057-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="d7057-141">Objektorientering</span><span class="sxs-lookup"><span data-stu-id="d7057-141">Object orientation</span></span>

<span data-ttu-id="d7057-142">PowerShell är baserad på objekt inte text.</span><span class="sxs-lookup"><span data-stu-id="d7057-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="d7057-143">Utdata från ett kommando är ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d7057-143">The output of a command is an object.</span></span> <span data-ttu-id="d7057-144">Du kan skicka objektet, genom pipelinen och till ett annat kommando som indata.</span><span class="sxs-lookup"><span data-stu-id="d7057-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="d7057-145">Denna pipeline finns det ett välbekanta gränssnitt för personer med andra gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="d7057-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="d7057-146">PowerShell utvidgar detta begrepp genom att skicka objekt i stället för text.</span><span class="sxs-lookup"><span data-stu-id="d7057-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="d7057-147">Lätt att skript</span><span class="sxs-lookup"><span data-stu-id="d7057-147">Easy transition to scripting</span></span>

<span data-ttu-id="d7057-148">PowerShell-kommando för att göra blir det enkelt att övergången från att skriva in kommandon interaktivt till skapa och köra skript.</span><span class="sxs-lookup"><span data-stu-id="d7057-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="d7057-149">PowerShell betyg och historik gör det enkelt att kopiera kommandon till en fil för användning som ett skript.</span><span class="sxs-lookup"><span data-stu-id="d7057-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
