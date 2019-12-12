---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Använd variabler för att lagra objekt
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030366"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="99ea5-103">Använd variabler för att lagra objekt</span><span class="sxs-lookup"><span data-stu-id="99ea5-103">Using variables to store objects</span></span>

<span data-ttu-id="99ea5-104">PowerShell fungerar med objekt.</span><span class="sxs-lookup"><span data-stu-id="99ea5-104">PowerShell works with objects.</span></span> <span data-ttu-id="99ea5-105">Med PowerShell kan du skapa namngivna objekt som kallas variabler.</span><span class="sxs-lookup"><span data-stu-id="99ea5-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="99ea5-106">Variabel namn kan innehålla under streck och alfanumeriska tecken.</span><span class="sxs-lookup"><span data-stu-id="99ea5-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="99ea5-107">När det används i PowerShell anges alltid en variabel med hjälp av \$-tecknen följt av variabel namnet.</span><span class="sxs-lookup"><span data-stu-id="99ea5-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="99ea5-108">Skapa en variabel</span><span class="sxs-lookup"><span data-stu-id="99ea5-108">Creating a variable</span></span>

<span data-ttu-id="99ea5-109">Du kan skapa en variabel genom att skriva ett giltigt variabel namn:</span><span class="sxs-lookup"><span data-stu-id="99ea5-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="99ea5-110">Det här exemplet returnerar inget resultat eftersom `$loc` inte har något värde.</span><span class="sxs-lookup"><span data-stu-id="99ea5-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="99ea5-111">Du kan skapa en variabel och tilldela den ett värde i samma steg.</span><span class="sxs-lookup"><span data-stu-id="99ea5-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="99ea5-112">PowerShell skapar bara variabeln om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="99ea5-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="99ea5-113">Annars tilldelar den den befintliga variabeln det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="99ea5-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="99ea5-114">I följande exempel lagras den aktuella platsen i variabeln `$loc`:</span><span class="sxs-lookup"><span data-stu-id="99ea5-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="99ea5-115">PowerShell visar inga utdata när du skriver det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="99ea5-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="99ea5-116">PowerShell skickar utdata från get-location till `$loc`.</span><span class="sxs-lookup"><span data-stu-id="99ea5-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="99ea5-117">I PowerShell skickas data som inte är tilldelade eller omdirigerade till skärmen.</span><span class="sxs-lookup"><span data-stu-id="99ea5-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="99ea5-118">När du skriver `$loc` visas din aktuella plats:</span><span class="sxs-lookup"><span data-stu-id="99ea5-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="99ea5-119">Du kan använda `Get-Member` för att visa information om innehållet i variabler.</span><span class="sxs-lookup"><span data-stu-id="99ea5-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="99ea5-120">`Get-Member` visar att `$loc` är ett **PathInfo** -objekt, precis som utdata från `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="99ea5-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

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

## <a name="manipulating-variables"></a><span data-ttu-id="99ea5-121">Manipulera variabler</span><span class="sxs-lookup"><span data-stu-id="99ea5-121">Manipulating variables</span></span>

<span data-ttu-id="99ea5-122">PowerShell innehåller flera kommandon för att manipulera variabler.</span><span class="sxs-lookup"><span data-stu-id="99ea5-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="99ea5-123">Du kan se en fullständig lista i läsbart format genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="99ea5-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="99ea5-124">PowerShell skapar också flera systemdefinierade variabler.</span><span class="sxs-lookup"><span data-stu-id="99ea5-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="99ea5-125">Du kan använda `Remove-Variable`-cmdlet för att ta bort variabler, som inte styrs av PowerShell, från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="99ea5-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="99ea5-126">Skriv följande kommando för att rensa alla variabler:</span><span class="sxs-lookup"><span data-stu-id="99ea5-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="99ea5-127">När du har kört föregående kommando visar `Get-Variable`-cmdleten PowerShell-systemvariablerna.</span><span class="sxs-lookup"><span data-stu-id="99ea5-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="99ea5-128">PowerShell skapar också en variabel enhet.</span><span class="sxs-lookup"><span data-stu-id="99ea5-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="99ea5-129">Använd följande exempel för att visa alla PowerShell-variabler med variabeln drive:</span><span class="sxs-lookup"><span data-stu-id="99ea5-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="99ea5-130">Använda CMD. exe-variabler</span><span class="sxs-lookup"><span data-stu-id="99ea5-130">Using cmd.exe variables</span></span>

<span data-ttu-id="99ea5-131">PowerShell kan använda samma miljövariabler som är tillgängliga för alla Windows-processer, inklusive **cmd. exe**.</span><span class="sxs-lookup"><span data-stu-id="99ea5-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="99ea5-132">Dessa variabler exponeras via en enhet med namnet `env:`.</span><span class="sxs-lookup"><span data-stu-id="99ea5-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="99ea5-133">Du kan visa dessa variabler genom att skriva följande kommando:</span><span class="sxs-lookup"><span data-stu-id="99ea5-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="99ea5-134">Standard-`*-Variable`-cmdletarna är inte utformade för att fungera med miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="99ea5-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="99ea5-135">Miljövariabler nås med hjälp av `env:`-enhetens prefix.</span><span class="sxs-lookup"><span data-stu-id="99ea5-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="99ea5-136">Variabeln **% systemroot%** i **cmd. exe** innehåller till exempel operativ systemets rot Katalog namn.</span><span class="sxs-lookup"><span data-stu-id="99ea5-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="99ea5-137">I PowerShell använder du `$env:SystemRoot` för att få åtkomst till samma värde.</span><span class="sxs-lookup"><span data-stu-id="99ea5-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="99ea5-138">Du kan också skapa och ändra miljövariabler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99ea5-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="99ea5-139">Miljövariabler i PowerShell följer samma regler för miljövariabler som används någon annan stans i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="99ea5-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="99ea5-140">I följande exempel skapas en ny miljö variabel:</span><span class="sxs-lookup"><span data-stu-id="99ea5-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="99ea5-141">Även om detta inte krävs är det vanligt att namn på miljö variabel används för alla versaler.</span><span class="sxs-lookup"><span data-stu-id="99ea5-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
