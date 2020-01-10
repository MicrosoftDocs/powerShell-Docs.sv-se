---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Ta bort objekt från pipelinen där objektet
ms.openlocfilehash: 370e7745341b70c0794352a690d5750d21f53ac2
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737193"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="031ba-103">Ta bort objekt från pipelinen (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="031ba-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="031ba-104">I PowerShell genererar och passerar du ofta fler objekt till en pipeline än du vill.</span><span class="sxs-lookup"><span data-stu-id="031ba-104">In PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="031ba-105">Du kan ange egenskaperna för specifika objekt som ska visas med hjälp av `Format-*`-cmdletar, men det hjälper inte till med problemet med att ta bort hela objekt från skärmen.</span><span class="sxs-lookup"><span data-stu-id="031ba-105">You can specify the properties of particular objects to display by using the `Format-*` cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="031ba-106">Du kanske vill filtrera objekt före slutet av en pipeline, så att du kan utföra åtgärder på endast en delmängd av de ursprungligen genererade objekten.</span><span class="sxs-lookup"><span data-stu-id="031ba-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="031ba-107">PowerShell innehåller en `Where-Object`-cmdlet som gör att du kan testa varje objekt i pipelinen och bara skicka det längs pipelinen om det uppfyller ett visst test villkor.</span><span class="sxs-lookup"><span data-stu-id="031ba-107">PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="031ba-108">Objekt som inte klarar testet tas bort från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="031ba-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="031ba-109">Du anger test villkoret som värdet för parametern **FilterScript** .</span><span class="sxs-lookup"><span data-stu-id="031ba-109">You supply the test condition as the value of the **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="031ba-110">Utföra enkla tester med Where-Object</span><span class="sxs-lookup"><span data-stu-id="031ba-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="031ba-111">Värdet för **FilterScript** är ett *skript block* – ett eller flera PowerShell-kommandon som omges av klammerparenteser (`{}`) – som utvärderas till true eller false.</span><span class="sxs-lookup"><span data-stu-id="031ba-111">The value of **FilterScript** is a *script block* - one or more PowerShell commands surrounded by braces (`{}`) - that evaluates to true or false.</span></span> <span data-ttu-id="031ba-112">Dessa skript block kan vara väldigt enkla, men att skapa dem kräver att du känner till ett annat PowerShell-begrepp, jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="031ba-112">These script blocks can be very simple, but creating them requires knowing about another PowerShell concept, comparison operators.</span></span> <span data-ttu-id="031ba-113">En jämförelse operator jämför objekten som visas på varje sida av den.</span><span class="sxs-lookup"><span data-stu-id="031ba-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="031ba-114">Jämförelse operatorer börjar med ett bindestreck (`-`) och följt av ett namn.</span><span class="sxs-lookup"><span data-stu-id="031ba-114">Comparison operators begin with a hyphen character (`-`) and are followed by a name.</span></span> <span data-ttu-id="031ba-115">Grundläggande jämförelse operatorer fungerar på nästan alla typer av objekt.</span><span class="sxs-lookup"><span data-stu-id="031ba-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="031ba-116">De mer avancerade jämförelse operatörerna kanske bara arbetar med text eller matriser.</span><span class="sxs-lookup"><span data-stu-id="031ba-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="031ba-117">När du arbetar med text är PowerShell-jämförelsen som standard Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="031ba-117">By default, when working with text, PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="031ba-118">På grund av tolknings överväganden används symboler som `<`,`>`och `=` inte som jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="031ba-118">Due to parsing considerations, symbols such as `<`,`>`, and `=` are not used as comparison operators.</span></span> <span data-ttu-id="031ba-119">Jämförelse operatorer består i stället av bokstäver.</span><span class="sxs-lookup"><span data-stu-id="031ba-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="031ba-120">De grundläggande jämförelse operatorerna visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="031ba-120">The basic comparison operators are listed in the following table.</span></span>

| <span data-ttu-id="031ba-121">Jämförelseoperator</span><span class="sxs-lookup"><span data-stu-id="031ba-121">Comparison Operator</span></span> |                  <span data-ttu-id="031ba-122">Innebörd</span><span class="sxs-lookup"><span data-stu-id="031ba-122">Meaning</span></span>                   |    <span data-ttu-id="031ba-123">Exempel (returnerar true)</span><span class="sxs-lookup"><span data-stu-id="031ba-123">Example (returns true)</span></span>    |
| ------------------- | ------------------------------------------ | ---------------------------- |
| <span data-ttu-id="031ba-124">-EQ</span><span class="sxs-lookup"><span data-stu-id="031ba-124">-eq</span></span>                 | <span data-ttu-id="031ba-125">är lika med</span><span class="sxs-lookup"><span data-stu-id="031ba-125">is equal to</span></span>                                | <span data-ttu-id="031ba-126">1 – EQ 1</span><span class="sxs-lookup"><span data-stu-id="031ba-126">1 -eq 1</span></span>                      |
| <span data-ttu-id="031ba-127">-Ne</span><span class="sxs-lookup"><span data-stu-id="031ba-127">-ne</span></span>                 | <span data-ttu-id="031ba-128">Är inte lika med</span><span class="sxs-lookup"><span data-stu-id="031ba-128">Is not equal to</span></span>                            | <span data-ttu-id="031ba-129">1 – Ne 2</span><span class="sxs-lookup"><span data-stu-id="031ba-129">1 -ne 2</span></span>                      |
| <span data-ttu-id="031ba-130">-lt</span><span class="sxs-lookup"><span data-stu-id="031ba-130">-lt</span></span>                 | <span data-ttu-id="031ba-131">Är mindre än</span><span class="sxs-lookup"><span data-stu-id="031ba-131">Is less than</span></span>                               | <span data-ttu-id="031ba-132">1 – lt 2</span><span class="sxs-lookup"><span data-stu-id="031ba-132">1 -lt 2</span></span>                      |
| <span data-ttu-id="031ba-133">-Le</span><span class="sxs-lookup"><span data-stu-id="031ba-133">-le</span></span>                 | <span data-ttu-id="031ba-134">är mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="031ba-134">Is less than or equal to</span></span>                   | <span data-ttu-id="031ba-135">1 – Le 2</span><span class="sxs-lookup"><span data-stu-id="031ba-135">1 -le 2</span></span>                      |
| <span data-ttu-id="031ba-136">-gt</span><span class="sxs-lookup"><span data-stu-id="031ba-136">-gt</span></span>                 | <span data-ttu-id="031ba-137">Är större än</span><span class="sxs-lookup"><span data-stu-id="031ba-137">Is greater than</span></span>                            | <span data-ttu-id="031ba-138">2 – gt 1</span><span class="sxs-lookup"><span data-stu-id="031ba-138">2 -gt 1</span></span>                      |
| <span data-ttu-id="031ba-139">-ge</span><span class="sxs-lookup"><span data-stu-id="031ba-139">-ge</span></span>                 | <span data-ttu-id="031ba-140">är större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="031ba-140">Is greater than or equal to</span></span>                | <span data-ttu-id="031ba-141">2-ge 1</span><span class="sxs-lookup"><span data-stu-id="031ba-141">2 -ge 1</span></span>                      |
| <span data-ttu-id="031ba-142">– som</span><span class="sxs-lookup"><span data-stu-id="031ba-142">-like</span></span>               | <span data-ttu-id="031ba-143">Liknar (jämförelse av jokertecken för text)</span><span class="sxs-lookup"><span data-stu-id="031ba-143">Is like (wildcard comparison for text)</span></span>     | <span data-ttu-id="031ba-144">"File. doc" – som "f \*. gör?"</span><span class="sxs-lookup"><span data-stu-id="031ba-144">"file.doc" -like "f\*.do?"</span></span>    |
| <span data-ttu-id="031ba-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="031ba-145">-notlike</span></span>            | <span data-ttu-id="031ba-146">Liknar inte (jämförelse av jokertecken för text)</span><span class="sxs-lookup"><span data-stu-id="031ba-146">Is not like (wildcard comparison for text)</span></span> | <span data-ttu-id="031ba-147">"File. doc"-notlike "p\*. doc"</span><span class="sxs-lookup"><span data-stu-id="031ba-147">"file.doc" -notlike "p\*.doc"</span></span> |
| <span data-ttu-id="031ba-148">– innehåller</span><span class="sxs-lookup"><span data-stu-id="031ba-148">-contains</span></span>           | <span data-ttu-id="031ba-149">Innehåller</span><span class="sxs-lookup"><span data-stu-id="031ba-149">Contains</span></span>                                   | <span data-ttu-id="031ba-150">1, 2, 3 – innehåller 1</span><span class="sxs-lookup"><span data-stu-id="031ba-150">1,2,3 -contains 1</span></span>            |
| <span data-ttu-id="031ba-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="031ba-151">-notcontains</span></span>        | <span data-ttu-id="031ba-152">Innehåller inte</span><span class="sxs-lookup"><span data-stu-id="031ba-152">Does not contain</span></span>                           | <span data-ttu-id="031ba-153">1, 2, 3-notcontains 4</span><span class="sxs-lookup"><span data-stu-id="031ba-153">1,2,3 -notcontains 4</span></span>         |

<span data-ttu-id="031ba-154">`Where-Object` skript block använder den speciella variabeln `$_` för att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="031ba-154">`Where-Object` script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="031ba-155">Här är ett exempel på hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="031ba-155">Here is an example of how it works.</span></span> <span data-ttu-id="031ba-156">Om du har en lista med tal och bara vill returnera de som är mindre än 3 kan du använda `Where-Object` för att filtrera talen genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="031ba-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use `Where-Object` to filter the numbers by typing:</span></span>

```
1,2,3,4 | Where-Object {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="031ba-157">Filtrering baserat på objekt egenskaper</span><span class="sxs-lookup"><span data-stu-id="031ba-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="031ba-158">Eftersom `$_` refererar till det aktuella pipeline-objektet kan vi komma åt dess egenskaper för våra tester.</span><span class="sxs-lookup"><span data-stu-id="031ba-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="031ba-159">Vi kan till exempel titta på **Win32_SystemDriver** -klassen i WMI.</span><span class="sxs-lookup"><span data-stu-id="031ba-159">As an example, we can look at the **Win32_SystemDriver** class in WMI.</span></span> <span data-ttu-id="031ba-160">Det kan finnas hundratals system driv rutiner i ett visst system, men du kanske bara är intresse rad av en viss uppsättning system driv rutiner, till exempel de som för närvarande körs.</span><span class="sxs-lookup"><span data-stu-id="031ba-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="031ba-161">För den **Win32_SystemDriver** klassen är relevant egenskap är **State**.</span><span class="sxs-lookup"><span data-stu-id="031ba-161">For the **Win32_SystemDriver** class the relevant property is **State**.</span></span> <span data-ttu-id="031ba-162">Du kan filtrera system driv rutinerna, välja enbart de som körs genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="031ba-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq 'Running'}
```

<span data-ttu-id="031ba-163">Detta skapar fortfarande en lång lista.</span><span class="sxs-lookup"><span data-stu-id="031ba-163">This still produces a long list.</span></span> <span data-ttu-id="031ba-164">Du kanske vill filtrera för att endast välja de driv rutiner som ska starta automatiskt genom att testa **Start mode** -värdet också:</span><span class="sxs-lookup"><span data-stu-id="031ba-164">You may want to filter to only select the drivers set to start automatically by testing the **StartMode** value as well:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Auto"}
```

```Output
DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
...
```

<span data-ttu-id="031ba-165">Detta ger oss mycket information som vi inte längre behöver eftersom vi vet att driv rutinerna körs.</span><span class="sxs-lookup"><span data-stu-id="031ba-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span>
<span data-ttu-id="031ba-166">Den enda information som vi förmodligen behöver i det här läget är i själva verket namnet och visnings namnet.</span><span class="sxs-lookup"><span data-stu-id="031ba-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="031ba-167">Följande kommando innehåller bara de två egenskaperna, vilket resulterar i mycket enklare utdata:</span><span class="sxs-lookup"><span data-stu-id="031ba-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {$_.State -eq "Running"} |
    Where-Object {$_.StartMode -eq "Manual"} |
      Format-Table -Property Name,DisplayName
```

```Output
Name              DisplayName
----              -----------
AsyncMac               RAS Asynchronous Media Driver
bindflt                Windows Bind Filter Driver
bowser                 Browser
CompositeBus           Composite Bus Enumerator Driver
condrv                 Console Driver
HdAudAddService        Microsoft 1.1 UAA Function Driver for High Definition Audio Service
HDAudBus               Microsoft UAA Bus Driver for High Definition Audio
HidUsb                 Microsoft HID Class Driver
HTTP                   HTTP Service
igfx                   igfx
IntcDAud               Intel(R) Display Audio
intelppm               Intel Processor Driver
...
```

<span data-ttu-id="031ba-168">Det finns två `Where-Object` element i ovanstående kommando, men de kan uttryckas i ett enda `Where-Object`-element med hjälp av den logiska operatorn för `-and`, så här:</span><span class="sxs-lookup"><span data-stu-id="031ba-168">There are two `Where-Object` elements in the above command, but they can be expressed in a single `Where-Object` element by using the `-and` logical operator, like this:</span></span>

```powershell
Get-CimInstance -Class Win32_SystemDriver |
  Where-Object {($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual')} |
    Format-Table -Property Name,DisplayName
```

<span data-ttu-id="031ba-169">De logiska standard operatörerna visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="031ba-169">The standard logical operators are listed in the following table.</span></span>

| <span data-ttu-id="031ba-170">Logisk operator</span><span class="sxs-lookup"><span data-stu-id="031ba-170">Logical Operator</span></span> |                 <span data-ttu-id="031ba-171">Innebörd</span><span class="sxs-lookup"><span data-stu-id="031ba-171">Meaning</span></span>                  |  <span data-ttu-id="031ba-172">Exempel (returnerar true)</span><span class="sxs-lookup"><span data-stu-id="031ba-172">Example (returns true)</span></span>  |
| ---------------- | ---------------------------------------- | ------------------------ |
| <span data-ttu-id="031ba-173">-och</span><span class="sxs-lookup"><span data-stu-id="031ba-173">-and</span></span>             | <span data-ttu-id="031ba-174">Logisk och; sant om båda sidorna är sanna</span><span class="sxs-lookup"><span data-stu-id="031ba-174">Logical and; true if both sides are true</span></span> | <span data-ttu-id="031ba-175">(1 – EQ 1)-och (2-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="031ba-175">(1 -eq 1) -and (2 -eq 2)</span></span> |
| <span data-ttu-id="031ba-176">-eller</span><span class="sxs-lookup"><span data-stu-id="031ba-176">-or</span></span>              | <span data-ttu-id="031ba-177">Logiskt eller; sant om endera sidan är sann</span><span class="sxs-lookup"><span data-stu-id="031ba-177">Logical or; true if either side is true</span></span>  | <span data-ttu-id="031ba-178">(1 – EQ 1)-eller (1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="031ba-178">(1 -eq 1) -or (1 -eq 2)</span></span>  |
| <span data-ttu-id="031ba-179">– inte</span><span class="sxs-lookup"><span data-stu-id="031ba-179">-not</span></span>             | <span data-ttu-id="031ba-180">Logiskt not; ångrar sant och falskt</span><span class="sxs-lookup"><span data-stu-id="031ba-180">Logical not; reverses true and false</span></span>     | <span data-ttu-id="031ba-181">– inte (1 – EQ 2)</span><span class="sxs-lookup"><span data-stu-id="031ba-181">-not (1 -eq 2)</span></span>           |
| \!               | <span data-ttu-id="031ba-182">Logiskt not; ångrar sant och falskt</span><span class="sxs-lookup"><span data-stu-id="031ba-182">Logical not; reverses true and false</span></span>     | <span data-ttu-id="031ba-183">\!(1 – EQ 2)</span><span class="sxs-lookup"><span data-stu-id="031ba-183">\!(1 -eq 2)</span></span>              |
