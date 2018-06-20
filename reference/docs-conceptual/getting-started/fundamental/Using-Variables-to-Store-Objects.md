---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd variabler för att lagra objekt
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: e52f0a344d0ad13db42b34bed912d584c99b0e30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953335"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="63588-103">Använd variabler för att lagra objekt</span><span class="sxs-lookup"><span data-stu-id="63588-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="63588-104">PowerShell fungerar med objekt.</span><span class="sxs-lookup"><span data-stu-id="63588-104">PowerShell works with objects.</span></span> <span data-ttu-id="63588-105">PowerShell kan du skapa variabler som i stort sett heter objekt att bevara utdata för senare användning.</span><span class="sxs-lookup"><span data-stu-id="63588-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="63588-106">Om du har använt för att arbeta med variabler i andra tankar Kom ihåg att PowerShell variabler objekt, inte text.</span><span class="sxs-lookup"><span data-stu-id="63588-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="63588-107">Variabler anges alltid med det första tecknet $ och kan innehålla alfanumeriska tecken eller understreck i sina namn.</span><span class="sxs-lookup"><span data-stu-id="63588-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="63588-108">Skapa en variabel</span><span class="sxs-lookup"><span data-stu-id="63588-108">Creating a Variable</span></span>
<span data-ttu-id="63588-109">Du kan skapa en variabel genom att ange ett giltigt namn på variabel:</span><span class="sxs-lookup"><span data-stu-id="63588-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="63588-110">Inga resultat returneras eftersom **$loc** saknar ett värde.</span><span class="sxs-lookup"><span data-stu-id="63588-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="63588-111">Du kan skapa en variabel och tilldela den ett värde i samma steg.</span><span class="sxs-lookup"><span data-stu-id="63588-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="63588-112">PowerShell skapar endast variabeln om det inte finns; Annars tilldelar det angivna värdet till en befintlig variabel.</span><span class="sxs-lookup"><span data-stu-id="63588-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="63588-113">Att lagra din aktuella plats i variabeln **$loc**, typ:</span><span class="sxs-lookup"><span data-stu-id="63588-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="63588-114">Det finns inga utdata som visas när du anger det här kommandot eftersom utdata skickas till $ lagerst.</span><span class="sxs-lookup"><span data-stu-id="63588-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="63588-115">I PowerShell är visas utdata en sidoeffekt av det faktum att informationen som inte annars dirigeras, skickas alltid till skärmen.</span><span class="sxs-lookup"><span data-stu-id="63588-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="63588-116">Att skriva $loc visar din aktuella plats:</span><span class="sxs-lookup"><span data-stu-id="63588-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="63588-117">Du kan använda **Get-medlemmen** att visa information om innehållet för variabler.</span><span class="sxs-lookup"><span data-stu-id="63588-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="63588-118">Skicka $loc till Get-medlemmen visar att det är en **PathInfo** objektet, precis som utdata från Get-plats:</span><span class="sxs-lookup"><span data-stu-id="63588-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="63588-119">Ändra variabler</span><span class="sxs-lookup"><span data-stu-id="63588-119">Manipulating Variables</span></span>
<span data-ttu-id="63588-120">PowerShell innehåller flera kommandon för att ändra variabler.</span><span class="sxs-lookup"><span data-stu-id="63588-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="63588-121">Du kan se en fullständig lista i ett läsbart formulär genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63588-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="63588-122">Förutom de variabler som du skapar i den aktuella PowerShell-sessionen finns flera systemdefinierade variabler.</span><span class="sxs-lookup"><span data-stu-id="63588-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="63588-123">Du kan använda den **ta bort variabeln** cmdlet för att rensa alla variabler som inte kontrolleras av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63588-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="63588-124">Skriv följande kommando för att rensa alla variabler:</span><span class="sxs-lookup"><span data-stu-id="63588-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="63588-125">Detta genererar tillfrågas om du ser nedan.</span><span class="sxs-lookup"><span data-stu-id="63588-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="63588-126">Om du kör den **Get-Variable** cmdlet, visas de återstående PowerShell-variablerna.</span><span class="sxs-lookup"><span data-stu-id="63588-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="63588-127">Eftersom det inte finns en variabel PowerShell-enhet, kan du också visa alla PowerShell variabler genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63588-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="63588-128">Använda Cmd.exe variabler</span><span class="sxs-lookup"><span data-stu-id="63588-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="63588-129">Även om PowerShell inte är Cmd.exe körs i en miljö med kommandot shell och kan använda samma variabler som är tillgängliga i alla miljöer i Windows.</span><span class="sxs-lookup"><span data-stu-id="63588-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="63588-130">Dessa variabler är tillgängliga via en enhet med namnet **env**:.</span><span class="sxs-lookup"><span data-stu-id="63588-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="63588-131">Du kan visa dessa variabler genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63588-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="63588-132">Även om standard variabel cmdlets inte är avsedda att fungera med **env:** variabler, du kan fortfarande använda dem genom att ange den **env:** prefix.</span><span class="sxs-lookup"><span data-stu-id="63588-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="63588-133">Till exempel om du vill se rotkatalogen operativsystem du kan använda kommandotolken- **% SystemRoot %** variabel från i PowerShell genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63588-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="63588-134">Du kan också skapa och ändra miljövariabler i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63588-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="63588-135">Miljövariabler som nås från Windows PowerShell stämmer överens med de vanliga reglerna för miljövariabler någon annanstans i Windows.</span><span class="sxs-lookup"><span data-stu-id="63588-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>