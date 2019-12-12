---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: PowerShell-skript
ms.openlocfilehash: 281f2e798b3d3fa1c150b079d633cb7e8490dcec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "62058496"
---
# <a name="powershell"></a><span data-ttu-id="3fbae-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fbae-103">PowerShell</span></span>

<span data-ttu-id="3fbae-104">PowerShell är ett uppgifts baserat kommando rads gränssnitt och skript språk som bygger på .NET.</span><span class="sxs-lookup"><span data-stu-id="3fbae-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="3fbae-105">Med PowerShell kan system administratörer och avancerade användare snabbt automatisera uppgifter som hanterar operativ system (Linux, macOS och Windows) och processer.</span><span class="sxs-lookup"><span data-stu-id="3fbae-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="3fbae-106">Med PowerShell-kommandon kan du hantera datorer från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="3fbae-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="3fbae-107">Med PowerShell-providers kan du komma åt data lager, till exempel registret och certifikat arkivet, så enkelt som du har åtkomst till fil systemet.</span><span class="sxs-lookup"><span data-stu-id="3fbae-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="3fbae-108">PowerShell innehåller en omfattande uttrycks parser och ett fullständigt utvecklat skript språk.</span><span class="sxs-lookup"><span data-stu-id="3fbae-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="3fbae-109">PowerShell är öppen källkod</span><span class="sxs-lookup"><span data-stu-id="3fbae-109">PowerShell is open-source</span></span>

<span data-ttu-id="3fbae-110">PowerShell-källkoden är nu tillgänglig i GitHub och är öppen för community-bidrag.</span><span class="sxs-lookup"><span data-stu-id="3fbae-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="3fbae-111">Se [PowerShell-källan på GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="3fbae-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="3fbae-112">Du kan börja med de bitar du behöver med [hjälp av PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span><span class="sxs-lookup"><span data-stu-id="3fbae-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="3fbae-113">Eller så kanske du får en snabb genom gång på [komma igång](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="3fbae-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="3fbae-114">Design mål för PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fbae-114">PowerShell design goals</span></span>

<span data-ttu-id="3fbae-115">PowerShell är utformat för att förbättra kommando rads-och skript miljön genom att eliminera problem med lång sikt och lägga till nya funktioner.</span><span class="sxs-lookup"><span data-stu-id="3fbae-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="3fbae-116">Identifierings möjligheten</span><span class="sxs-lookup"><span data-stu-id="3fbae-116">Discoverability</span></span>

<span data-ttu-id="3fbae-117">Med PowerShell är det enkelt att upptäcka dess funktioner.</span><span class="sxs-lookup"><span data-stu-id="3fbae-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="3fbae-118">Om du till exempel vill hitta en lista över cmdletar som visar och ändrar Windows-tjänster skriver du:</span><span class="sxs-lookup"><span data-stu-id="3fbae-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="3fbae-119">När du har identifierat vilken cmdlet som utför en aktivitet kan du läsa mer om cmdleten med hjälp av `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fbae-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3fbae-120">Om du till exempel vill visa hjälp om cmdleten `Get-Service` skriver du:</span><span class="sxs-lookup"><span data-stu-id="3fbae-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="3fbae-121">De flesta cmdletar returnerar objekt som kan manipuleras och sedan återges som text för visning.</span><span class="sxs-lookup"><span data-stu-id="3fbae-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="3fbae-122">För att fullständigt förstå utdata från en cmdlet skickar du utdata till `Get-Member`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fbae-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="3fbae-123">Följande kommando visar till exempel information om medlemmar i objektets utdata från `Get-Service`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fbae-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="3fbae-124">Konsekvens</span><span class="sxs-lookup"><span data-stu-id="3fbae-124">Consistency</span></span>

<span data-ttu-id="3fbae-125">Hantering av system kan vara en komplicerad uppgift.</span><span class="sxs-lookup"><span data-stu-id="3fbae-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="3fbae-126">Verktyg som har ett konsekvent gränssnitt hjälper dig att styra den komplicerade komplexiteten.</span><span class="sxs-lookup"><span data-stu-id="3fbae-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="3fbae-127">Kommando rads verktyg och COM-objekt (Scriptable Component Object Model) är inte kända för deras konsekvens.</span><span class="sxs-lookup"><span data-stu-id="3fbae-127">Unfortunately, command-line tools and scriptable Component Object Model (COM) objects aren't known for their consistency.</span></span>

<span data-ttu-id="3fbae-128">Konsekvensen av PowerShell är en av dess primära till gångar.</span><span class="sxs-lookup"><span data-stu-id="3fbae-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="3fbae-129">Om du till exempel lär dig hur du använder `Sort-Object`-cmdleten kan du använda den informationen för att sortera utdata från alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="3fbae-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="3fbae-130">Du behöver inte lära dig de olika sorterings rutinerna för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3fbae-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="3fbae-131">Dessutom behöver inte cmdlet-utvecklare utforma sorterings funktioner för sina cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3fbae-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="3fbae-132">PowerShell ger ett ramverk med de grundläggande funktioner som tvingar konsekvens.</span><span class="sxs-lookup"><span data-stu-id="3fbae-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="3fbae-133">Ramverket eliminerar några val som finns kvar i utvecklaren.</span><span class="sxs-lookup"><span data-stu-id="3fbae-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="3fbae-134">Men i retur gör det mycket enklare att utveckla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="3fbae-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="3fbae-135">Interaktiva miljöer och skript miljöer</span><span class="sxs-lookup"><span data-stu-id="3fbae-135">Interactive and scripting environments</span></span>

<span data-ttu-id="3fbae-136">Kommando tolken i Windows innehåller ett interaktivt gränssnitt med åtkomst till kommando rads verktyg och grundläggande skript.</span><span class="sxs-lookup"><span data-stu-id="3fbae-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="3fbae-137">Windows Script Host (WSH) har skript bara kommando rads verktyg och COM Automation-objekt, men ger inte ett interaktivt gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="3fbae-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="3fbae-138">PowerShell kombinerar ett interaktivt gränssnitt och en skript miljö.</span><span class="sxs-lookup"><span data-stu-id="3fbae-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="3fbae-139">PowerShell kan komma åt kommando rads verktyg, COM-objekt och .NET-klass bibliotek.</span><span class="sxs-lookup"><span data-stu-id="3fbae-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="3fbae-140">Den här kombinationen av funktioner utökar funktionerna i den interaktiva användaren, skript skrivaren och system administratören.</span><span class="sxs-lookup"><span data-stu-id="3fbae-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="3fbae-141">Objekt orientering</span><span class="sxs-lookup"><span data-stu-id="3fbae-141">Object orientation</span></span>

<span data-ttu-id="3fbae-142">PowerShell baseras på objekt som inte är text.</span><span class="sxs-lookup"><span data-stu-id="3fbae-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="3fbae-143">Utdata från ett kommando är ett objekt.</span><span class="sxs-lookup"><span data-stu-id="3fbae-143">The output of a command is an object.</span></span> <span data-ttu-id="3fbae-144">Du kan skicka objektet utdata via pipelinen till ett annat kommando som indata.</span><span class="sxs-lookup"><span data-stu-id="3fbae-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="3fbae-145">Den här pipelinen ger ett välbekant gränssnitt för personer som har erfarenhet av andra gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="3fbae-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="3fbae-146">PowerShell utökar det här konceptet genom att skicka objekt i stället för text.</span><span class="sxs-lookup"><span data-stu-id="3fbae-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="3fbae-147">Enkel över gång till skript</span><span class="sxs-lookup"><span data-stu-id="3fbae-147">Easy transition to scripting</span></span>

<span data-ttu-id="3fbae-148">PowerShell-kommandots identifiering gör det enkelt att gå över från att skriva kommandon interaktivt för att skapa och köra skript.</span><span class="sxs-lookup"><span data-stu-id="3fbae-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="3fbae-149">Med PowerShell-avskrifter och historik kan du enkelt kopiera kommandon till en fil för användning som ett skript.</span><span class="sxs-lookup"><span data-stu-id="3fbae-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
