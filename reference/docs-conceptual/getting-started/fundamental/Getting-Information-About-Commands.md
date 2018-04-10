---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Få information om kommandon
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 1426c171d74afc87751f7d31d46571b9c98fa47e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="5f9d3-103">Få information om kommandon</span><span class="sxs-lookup"><span data-stu-id="5f9d3-103">Getting Information About Commands</span></span>
<span data-ttu-id="5f9d3-104">Windows PowerShell **Get-Command** cmdlet hämtar alla kommandon som är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="5f9d3-105">När du skriver **Get-Command** i Windows PowerShell-kommandotolken visas utdata som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="5f9d3-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="5f9d3-106">Detta utdata mycket ser ut som hjälp utdata från Cmd.exe: en tabell sammanfattning av interna kommandon.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="5f9d3-107">I utdrag ur den **Get-Command** kommandot utdata visas alla kommandon som visas ovan, har en CommandType Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="5f9d3-108">En cmdlet är Windows PowerShell inre kommandotypen - en typ som motsvarar ungefär till den **dir** och **cd** kommandon cmd.exe och built-ins i UNIX-gränssnitt, till exempel BASH.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="5f9d3-109">I utdata från den **Get-Command** kommandot alla definitioner avslutas med ellipserna (...) för att indikera att PowerShell inte kan visa allt innehåll i det tillgängliga utrymmet.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="5f9d3-110">När Windows PowerShell visar utdata, formaterar resultatet som text och ordnar det som gör att data korrekt passar i fönstret.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="5f9d3-111">Vi ska tala om det senare i avsnittet på formaterare.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="5f9d3-112">Den **Get-Command** cmdlet har en **Syntax** parameter som hämtar syntaxen för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="5f9d3-113">För att få syntaxen för cmdleten Get-Help, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="5f9d3-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="5f9d3-114">**Get-kommandot Get-Help-Syntax**</span><span class="sxs-lookup"><span data-stu-id="5f9d3-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="5f9d3-115">Visa tillgängliga kommandon</span><span class="sxs-lookup"><span data-stu-id="5f9d3-115">Displaying Available Command Types</span></span>
<span data-ttu-id="5f9d3-116">Den **Get-Command** kommando inte innehåller alla kommandon som är tillgängliga i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="5f9d3-117">I stället den **Get-Command** kommando visar bara cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="5f9d3-118">Windows PowerShell verkligen har stöd för flera typer av kommandon.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="5f9d3-119">Alias, funktioner och skript är också Windows PowerShell-kommandon, även om de inte beskrivs i detalj i Windows PowerShell användarhandboken.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="5f9d3-120">Externa filer som är körbara eller har en registrerad typ hanterare också klassificeras som kommandon.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="5f9d3-121">Om du vill hämta alla kommandon i sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="5f9d3-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="5f9d3-122">Eftersom den här listan innehåller de externa filerna i sökvägen, kan den innehålla tusentals objekt.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="5f9d3-123">Det är bättre att titta på en uppsättning kommandon.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="5f9d3-124">Inbyggda kommandon av andra typer får använda den **CommandType** parameter för den **Get-Command** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="5f9d3-125">En asterisk (\*) används för matchning i Windows PowerShell kommandoargumenten med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="5f9d3-126">Den \* ”matchar en eller flera tecken”.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="5f9d3-127">Du kan skriva **Get-Command en\&#42;** att hitta alla kommandon som börjar med bokstaven ”a”.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="5f9d3-128">Till skillnad från matchning med jokertecken i Cmd.exe, kommer Windows PowerShell med jokertecken också under en period.</span><span class="sxs-lookup"><span data-stu-id="5f9d3-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="5f9d3-129">Om du vill ha kommandot alias som är tilldelade smeknamn kommandon, skriver du:</span><span class="sxs-lookup"><span data-stu-id="5f9d3-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="5f9d3-130">För att få funktionerna i den aktuella sessionen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="5f9d3-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="5f9d3-131">Om du vill visa skript i Windows PowerShell-sökvägen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="5f9d3-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```