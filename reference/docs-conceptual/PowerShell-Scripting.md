---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: PowerShell-skript
ms.openlocfilehash: c6ba3abc2544834e2cbec16a524f79399a1d2599
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094059"
---
# <a name="powershell"></a><span data-ttu-id="0ead8-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0ead8-103">PowerShell</span></span>

<span data-ttu-id="0ead8-104">Bygger på .NET Framework och är PowerShell ett uppgiftsbaserat kommandoradsgränssnitt och skriptspråk; Det är utformat särskilt för administratörer och Privilegierade användare, att automatisera snabbt administrationen av flera operativsystem (Linux, macOS, Unix- och Windows) och processer som är relaterade till de program som körs på dessa operativsystem.</span><span class="sxs-lookup"><span data-stu-id="0ead8-104">Built on the .NET Framework, PowerShell is a task-based command-line shell and scripting language; it is designed specifically for system administrators and power-users, to rapidly automate the administration of multiple operating systems (Linux, macOS, Unix, and Windows) and the processes related to the applications that run on those operating systems.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="0ead8-105">PowerShell är öppen källkod</span><span class="sxs-lookup"><span data-stu-id="0ead8-105">PowerShell is open source</span></span>

<span data-ttu-id="0ead8-106">PowerShell grundläggande källkoden är nu tillgängligt i GitHub och öppna community-bidrag.</span><span class="sxs-lookup"><span data-stu-id="0ead8-106">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="0ead8-107">Se [PowerShell källkod på GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="0ead8-107">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="0ead8-108">Du kan börja med bits på [hämta PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="0ead8-108">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="0ead8-109">Eller kanske, med en snabb genomgång på [komma igång](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span><span class="sxs-lookup"><span data-stu-id="0ead8-109">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell)</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="0ead8-110">PowerShell-designmålen</span><span class="sxs-lookup"><span data-stu-id="0ead8-110">PowerShell design goals</span></span>
<span data-ttu-id="0ead8-111">PowerShell har utformats för att förbättra miljön kommandorad och skript genom att långsiktigt problem och lägga till nya funktioner.</span><span class="sxs-lookup"><span data-stu-id="0ead8-111">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="0ead8-112">För att göra</span><span class="sxs-lookup"><span data-stu-id="0ead8-112">Discoverability</span></span>
<span data-ttu-id="0ead8-113">PowerShell gör det enkelt att identifiera dess funktioner.</span><span class="sxs-lookup"><span data-stu-id="0ead8-113">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="0ead8-114">Till exempel för att hitta en lista över cmdlets som Visa och ändra Windows-tjänster, skriver du:</span><span class="sxs-lookup"><span data-stu-id="0ead8-114">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="0ead8-115">Efter identifiering av vilka cmdlet uppnår en uppgift, kan du läsa mer om cmdlet: en med hjälp av den `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ead8-115">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span>
<span data-ttu-id="0ead8-116">Till exempel vill visa hjälp om den `Get-Service` cmdlet, typ:</span><span class="sxs-lookup"><span data-stu-id="0ead8-116">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```
<span data-ttu-id="0ead8-117">De flesta cmdletar sända objekt som kan ändras och sedan återges i text som ska visas.</span><span class="sxs-lookup"><span data-stu-id="0ead8-117">Most cmdlets emit objects which can be manipulated and then rendered into text for display.</span></span>
<span data-ttu-id="0ead8-118">För att helt förstå utdata från denna cmdlet kan skicka utdata till den `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ead8-118">To fully understand the output of that cmdlet, pipe its output to the `Get-Member` cmdlet.</span></span>
<span data-ttu-id="0ead8-119">Till exempel följande kommando visar information om medlemmarna i objektutdata av den `Get-Service` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ead8-119">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="0ead8-120">Konsekvens</span><span class="sxs-lookup"><span data-stu-id="0ead8-120">Consistency</span></span>
<span data-ttu-id="0ead8-121">Hantera system kan vara en komplex åtagande och verktyg som har ett konsekvent gränssnitt bidra till att styra den inbyggda komplexiteten.</span><span class="sxs-lookup"><span data-stu-id="0ead8-121">Managing systems can be a complex endeavor and tools that have a consistent interface help to control the inherent complexity.</span></span>
<span data-ttu-id="0ead8-122">Varken kommandoradsverktyg eller skriptbara COM-objekt har tyvärr rapporterats för sina konsekvens.</span><span class="sxs-lookup"><span data-stu-id="0ead8-122">Unfortunately, neither command-line tools nor scriptable COM objects have been known for their consistency.</span></span>

<span data-ttu-id="0ead8-123">Konsekvenskontroll av PowerShell är en av dess primära tillgångar.</span><span class="sxs-lookup"><span data-stu-id="0ead8-123">The consistency of PowerShell is one of its primary assets.</span></span>
<span data-ttu-id="0ead8-124">Exempel: Om du lära dig hur du använder den `Sort-Object` cmdlet, du kan använda denna kunskap för att ordna resultatet av en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ead8-124">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span>
<span data-ttu-id="0ead8-125">Du behöver inte lära dig de olika sortering rutinerna för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0ead8-125">You do not have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="0ead8-126">Dessutom behöver inte cmdlet-utvecklare utforma sortering funktioner för deras cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0ead8-126">In addition, cmdlet developers do not have to design sorting features for their cmdlets.</span></span>
<span data-ttu-id="0ead8-127">PowerShell ger dem ett ramverk som tillhandahåller grundläggande funktioner och tvingar dem att vara konsekvent många aspekter av gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="0ead8-127">PowerShell gives them a framework that provides the basic features and forces them to be consistent about many aspects of the interface.</span></span>
<span data-ttu-id="0ead8-128">Ramverket eliminerar några av de alternativ som vanligtvis lämnas till utvecklaren, men i utbyte blir utvecklingen av robust och enkel att använda cmdlet: ar mycket enklare.</span><span class="sxs-lookup"><span data-stu-id="0ead8-128">The framework eliminates some of the choices that are typically left to the developer, but, in return, it makes the development of robust and easy-to-use cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="0ead8-129">Interaktiva och skript miljöer</span><span class="sxs-lookup"><span data-stu-id="0ead8-129">Interactive and Scripting Environments</span></span>
<span data-ttu-id="0ead8-130">PowerShell är en kombinerad interaktiva och skript som ger dig tillgång till kommandoradsverktyg och COM-objekt och även aktiverar du kan använda kraften i .NET Framework Class Library (FCL).</span><span class="sxs-lookup"><span data-stu-id="0ead8-130">PowerShell is a combined interactive and scripting environment that gives you access to command-line tools and COM objects, and also enables you to use the power of the .NET Framework Class Library (FCL).</span></span>

<span data-ttu-id="0ead8-131">Den här miljön förbättrar vid Windows Kommandotolken, vilket ger en interaktiv miljö med flera kommandoradsverktyg.</span><span class="sxs-lookup"><span data-stu-id="0ead8-131">This environment improves upon the Windows Command Prompt, which provides an interactive environment with multiple command-line tools.</span></span>
<span data-ttu-id="0ead8-132">Det förbättrar också vid skript för Windows Script Host (WSH), som gör att du använder flera kommandoradsverktyg och COM automation-objekt, men inte anger en interaktiv miljö.</span><span class="sxs-lookup"><span data-stu-id="0ead8-132">It also improves upon Windows Script Host (WSH) scripts, which let you use multiple command-line tools and COM automation objects, but do not provide an interactive environment.</span></span>

<span data-ttu-id="0ead8-133">Genom att kombinera åtkomst till alla dessa funktioner kan PowerShell utökar möjligheten för den interaktiva användaren och skrivar-skriptet och gör systemadministration mer hanterbara.</span><span class="sxs-lookup"><span data-stu-id="0ead8-133">By combining access to all of these features, PowerShell extends the ability of the interactive user and the script writer, and makes system administration more manageable.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="0ead8-134">Objektorientering</span><span class="sxs-lookup"><span data-stu-id="0ead8-134">Object Orientation</span></span>
<span data-ttu-id="0ead8-135">Även om du interagerar med PowerShell genom att skriva kommandon i texten, är PowerShell baserad på objekt, inte text.</span><span class="sxs-lookup"><span data-stu-id="0ead8-135">Although you interact with PowerShell by typing commands in text, PowerShell is based on objects, not text.</span></span>
<span data-ttu-id="0ead8-136">Utdata från ett kommando är ett objekt.</span><span class="sxs-lookup"><span data-stu-id="0ead8-136">The output of a command is an object.</span></span>
<span data-ttu-id="0ead8-137">Du kan skicka objektet till ett annat kommando som indata.</span><span class="sxs-lookup"><span data-stu-id="0ead8-137">You can send the output object to another command as its input.</span></span>
<span data-ttu-id="0ead8-138">Därför innehåller PowerShell en välbekanta gränssnittet till personer som har erfarenhet av andra gränssnitt, samtidigt som introducerar nya, kraftfulla kommandoradsverktyget paradigm.</span><span class="sxs-lookup"><span data-stu-id="0ead8-138">As a result, PowerShell provides a familiar interface to people experienced with other shells, while introducing a new and powerful command-line paradigm.</span></span>
<span data-ttu-id="0ead8-139">Det är en utökad variant för att skicka data mellan kommandon genom att skicka objekt i stället för text.</span><span class="sxs-lookup"><span data-stu-id="0ead8-139">It extends the concept of sending data between commands by enabling you to send objects, rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="0ead8-140">Lätt att skript</span><span class="sxs-lookup"><span data-stu-id="0ead8-140">Easy Transition to Scripting</span></span>
<span data-ttu-id="0ead8-141">PowerShell gör det enkelt att övergången från att skriva in kommandon interaktivt till skapa och köra skript.</span><span class="sxs-lookup"><span data-stu-id="0ead8-141">PowerShell makes it easy to transition from typing commands interactively to creating and running scripts.</span></span>
<span data-ttu-id="0ead8-142">Du kan skriva kommandon i Kommandotolken för PowerShell för att identifiera de kommandon som utför en uppgift.</span><span class="sxs-lookup"><span data-stu-id="0ead8-142">You can type commands at the PowerShell command prompt to discover the commands that perform a task.</span></span>
<span data-ttu-id="0ead8-143">Sedan kan du spara dessa kommandon i en avskrift eller en historik innan kopiera dem till en fil för användning som ett skript.</span><span class="sxs-lookup"><span data-stu-id="0ead8-143">Then, you can save those commands in a transcript or a history before copying them to a file for use as a script.</span></span>
