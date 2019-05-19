---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Använd variabler för att lagra objekt
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 16e82b83df967674da11193c8ac60d637687a01b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854325"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="4471c-103">Använd variabler för att lagra objekt</span><span class="sxs-lookup"><span data-stu-id="4471c-103">Using variables to store objects</span></span>

<span data-ttu-id="4471c-104">PowerShell fungerar med objekt.</span><span class="sxs-lookup"><span data-stu-id="4471c-104">PowerShell works with objects.</span></span> <span data-ttu-id="4471c-105">PowerShell kan du skapa objekt som kallas variabler.</span><span class="sxs-lookup"><span data-stu-id="4471c-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="4471c-106">Variabelnamn kan innehålla understreck och alfanumeriska tecken.</span><span class="sxs-lookup"><span data-stu-id="4471c-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="4471c-107">När den används i PowerShell, en variabel alltid anges med hjälp av den \$ tecken följt av namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="4471c-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="4471c-108">Skapa en variabel</span><span class="sxs-lookup"><span data-stu-id="4471c-108">Creating a variable</span></span>

<span data-ttu-id="4471c-109">Du kan skapa en variabel genom att skriva ett giltigt variabelnamn:</span><span class="sxs-lookup"><span data-stu-id="4471c-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="4471c-110">Det här exemplet returnerar inga resultat eftersom `$loc` saknar ett värde.</span><span class="sxs-lookup"><span data-stu-id="4471c-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="4471c-111">Du kan skapa en variabel och tilldela den ett värde i samma steg.</span><span class="sxs-lookup"><span data-stu-id="4471c-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="4471c-112">PowerShell skapar endast variabeln om det inte finns.</span><span class="sxs-lookup"><span data-stu-id="4471c-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="4471c-113">Annars tilldelar det angivna värdet till en befintlig variabel.</span><span class="sxs-lookup"><span data-stu-id="4471c-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="4471c-114">I följande exempel lagrar den aktuella platsen i variabeln `$loc`:</span><span class="sxs-lookup"><span data-stu-id="4471c-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="4471c-115">PowerShell visar inga utdata när du skriver in det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="4471c-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="4471c-116">PowerShell skickar utdata från Get-plats till `$loc`.</span><span class="sxs-lookup"><span data-stu-id="4471c-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="4471c-117">I PowerShell skickas data som inte är tilldelade eller omdirigeras till skärmen.</span><span class="sxs-lookup"><span data-stu-id="4471c-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="4471c-118">Att skriva `$loc` visar din aktuella plats:</span><span class="sxs-lookup"><span data-stu-id="4471c-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="4471c-119">Du kan använda `Get-Member` att visa information om innehållet för variabler.</span><span class="sxs-lookup"><span data-stu-id="4471c-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="4471c-120">`Get-Member` Visar att `$loc` är en **PathInfo** objekt, precis som utdata från `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="4471c-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="4471c-121">Ändra variabler</span><span class="sxs-lookup"><span data-stu-id="4471c-121">Manipulating variables</span></span>

<span data-ttu-id="4471c-122">PowerShell innehåller flera kommandon för att ändra variabler.</span><span class="sxs-lookup"><span data-stu-id="4471c-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="4471c-123">Du kan se en fullständig lista i form av en läsbar genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="4471c-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="4471c-124">PowerShell skapar även flera systemdefinierade variabler.</span><span class="sxs-lookup"><span data-stu-id="4471c-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="4471c-125">Du kan använda den `Remove-Variable` cmdlet för att ta bort variabler som inte kontrolleras av PowerShell, från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4471c-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="4471c-126">Skriv följande kommando för att rensa alla variabler:</span><span class="sxs-lookup"><span data-stu-id="4471c-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="4471c-127">När du har kört kommandot föregående den `Get-Variable` cmdlet visar systemvariabler PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4471c-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="4471c-128">PowerShell skapar även en variabel enhet.</span><span class="sxs-lookup"><span data-stu-id="4471c-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="4471c-129">Använd följande exempel för att visa alla PowerShell-variabler med hjälp av variabeln drive:</span><span class="sxs-lookup"><span data-stu-id="4471c-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="4471c-130">Använda cmd.exe variabler</span><span class="sxs-lookup"><span data-stu-id="4471c-130">Using cmd.exe variables</span></span>

<span data-ttu-id="4471c-131">PowerShell kan använda de samma miljövariablerna som är tillgängliga för alla Windows-processen, inklusive **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="4471c-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="4471c-132">Dessa variabler är tillgängliga via en enhet med namnet `env:`.</span><span class="sxs-lookup"><span data-stu-id="4471c-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="4471c-133">Du kan visa dessa variabler genom att skriva följande kommando:</span><span class="sxs-lookup"><span data-stu-id="4471c-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="4471c-134">Standard `*-Variable` cmdletar är inte avsett att fungera med miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="4471c-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="4471c-135">Miljövariabler kan nås med hjälp av den `env:` enhetsprefix.</span><span class="sxs-lookup"><span data-stu-id="4471c-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="4471c-136">Till exempel den **% SystemRoot %** variabel i **cmd.exe** innehåller katalognamnet för operativsystemets rot.</span><span class="sxs-lookup"><span data-stu-id="4471c-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="4471c-137">I PowerShell kan du använda `$env:SystemRoot` att få åtkomst till samma värde.</span><span class="sxs-lookup"><span data-stu-id="4471c-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="4471c-138">Du kan också skapa och ändra miljövariabler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4471c-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="4471c-139">Miljövariabler i PowerShell följer samma regler för miljövariabler används någon annanstans i operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="4471c-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="4471c-140">I följande exempel skapas en ny miljövariabel:</span><span class="sxs-lookup"><span data-stu-id="4471c-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="4471c-141">Även om inte krävs, är det vanligt att miljövariabelnamn att använda enbart versaler.</span><span class="sxs-lookup"><span data-stu-id="4471c-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
