---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Få information om kommandon
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030941"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="bcc73-103">Få information om kommandon</span><span class="sxs-lookup"><span data-stu-id="bcc73-103">Getting information about commands</span></span>

<span data-ttu-id="bcc73-104">PowerShell-`Get-Command` visar kommandon som är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="bcc73-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="bcc73-105">När du kör `Get-Command`-cmdlet ser du något som liknar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="bcc73-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

<span data-ttu-id="bcc73-106">Det här resultatet ser ut ungefär som hjälp resultatet av **cmd. exe**: en tabell Sammanfattning av interna kommandon.</span><span class="sxs-lookup"><span data-stu-id="bcc73-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="bcc73-107">I utdraget av `Get-Command` kommandot utdata som visas ovan, har varje kommando som visas en cmdlet-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcc73-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="bcc73-108">En cmdlet är PowerShell: s inbyggda kommando typ.</span><span class="sxs-lookup"><span data-stu-id="bcc73-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="bcc73-109">Den här typen motsvarar ungefär samma som för kommandon som `dir` och `cd` i **cmd. exe** eller inbyggda kommandon i UNIX-gränssnitt som bash.</span><span class="sxs-lookup"><span data-stu-id="bcc73-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="bcc73-110">`Get-Command`-cmdleten har en **syntax** -parameter som returnerar syntaxen för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcc73-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="bcc73-111">I följande exempel visas hur du hämtar syntaxen för `Get-Help`-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="bcc73-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="bcc73-112">Visar tillgängligt kommando efter typ</span><span class="sxs-lookup"><span data-stu-id="bcc73-112">Displaying available command by type</span></span>

<span data-ttu-id="bcc73-113">Kommandot `Get-Command` visar bara cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="bcc73-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="bcc73-114">PowerShell stöder faktiskt flera andra typer av kommandon:</span><span class="sxs-lookup"><span data-stu-id="bcc73-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="bcc73-115">Alias</span><span class="sxs-lookup"><span data-stu-id="bcc73-115">Aliases</span></span>
- <span data-ttu-id="bcc73-116">Funktioner</span><span class="sxs-lookup"><span data-stu-id="bcc73-116">Functions</span></span>
- <span data-ttu-id="bcc73-117">Skript</span><span class="sxs-lookup"><span data-stu-id="bcc73-117">Scripts</span></span>

<span data-ttu-id="bcc73-118">Externa körbara filer eller filer som har en registrerad fil typs hanterare klassificeras också som kommandon.</span><span class="sxs-lookup"><span data-stu-id="bcc73-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="bcc73-119">Om du vill hämta alla kommandon i sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="bcc73-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="bcc73-120">Den här listan innehåller externa kommandon i din Sök väg så att den kan innehålla tusentals objekt.</span><span class="sxs-lookup"><span data-stu-id="bcc73-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="bcc73-121">Det är mer användbart att titta på en reducerad uppsättning kommandon.</span><span class="sxs-lookup"><span data-stu-id="bcc73-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="bcc73-122">Asterisken (\*) används för matchning av jokertecken i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="bcc73-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="bcc73-123">\* betyder "matcha ett eller flera tecken".</span><span class="sxs-lookup"><span data-stu-id="bcc73-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="bcc73-124">Du kan skriva `Get-Command a*` för att hitta alla kommandon som börjar med bokstaven "a".</span><span class="sxs-lookup"><span data-stu-id="bcc73-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="bcc73-125">Till skillnad från matchning av jokertecken i **cmd. exe**kommer PowerShell-jokertecknet också att matcha en punkt.</span><span class="sxs-lookup"><span data-stu-id="bcc73-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="bcc73-126">Använd parametern **CommandType** för `Get-Command` för att hämta interna kommandon av andra typer.</span><span class="sxs-lookup"><span data-stu-id="bcc73-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="bcc73-127">.</span><span class="sxs-lookup"><span data-stu-id="bcc73-127">cmdlet.</span></span>

<span data-ttu-id="bcc73-128">Om du vill hämta kommando Ali Aset, som är tilldelade smek namn för kommandon, skriver du:</span><span class="sxs-lookup"><span data-stu-id="bcc73-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="bcc73-129">Om du vill hämta funktionerna i den aktuella sessionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="bcc73-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="bcc73-130">Om du vill visa skript i PowerShell: s Sök väg skriver du:</span><span class="sxs-lookup"><span data-stu-id="bcc73-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
