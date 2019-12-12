---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Ta bort objekt från pipelinen där objektet
ms.openlocfilehash: c47efd38e2ff40ce3b7bf50b161cc38de922c5da
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030879"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="f8373-103">Ta bort objekt från pipelinen (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="f8373-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="f8373-104">I Windows PowerShell genererar och passerar du ofta fler objekt till en pipeline än du vill.</span><span class="sxs-lookup"><span data-stu-id="f8373-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="f8373-105">Du kan ange egenskaperna för specifika objekt som ska visas med hjälp av **format** -cmdletar, men det hjälper inte till med problemet med att ta bort hela objekt från skärmen.</span><span class="sxs-lookup"><span data-stu-id="f8373-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="f8373-106">Du kanske vill filtrera objekt före slutet av en pipeline, så att du kan utföra åtgärder på endast en delmängd av de ursprungligen genererade objekten.</span><span class="sxs-lookup"><span data-stu-id="f8373-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="f8373-107">Windows PowerShell innehåller en `Where-Object`-cmdlet som gör att du kan testa varje objekt i pipelinen och bara skicka det längs pipelinen om det uppfyller ett visst test villkor.</span><span class="sxs-lookup"><span data-stu-id="f8373-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="f8373-108">Objekt som inte klarar testet tas bort från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="f8373-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="f8373-109">Du anger test villkoret som värdet för parametern `Where-Object` **FilterScript** .</span><span class="sxs-lookup"><span data-stu-id="f8373-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

## <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="f8373-110">Utföra enkla tester med Where-Object</span><span class="sxs-lookup"><span data-stu-id="f8373-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="f8373-111">Värdet för **FilterScript** är ett *skript block* – ett eller flera Windows PowerShell-kommandon som omges av klammerparenteser {} – som utvärderas till true eller false.</span><span class="sxs-lookup"><span data-stu-id="f8373-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="f8373-112">Dessa skript block kan vara väldigt enkla, men att skapa dem kräver att du känner till ett annat Windows PowerShell-begrepp, jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="f8373-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="f8373-113">En jämförelse operator jämför objekten som visas på varje sida av den.</span><span class="sxs-lookup"><span data-stu-id="f8373-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="f8373-114">Jämförelse operatorer börjar med ett-och följt av ett namn.</span><span class="sxs-lookup"><span data-stu-id="f8373-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="f8373-115">Grundläggande jämförelse operatorer fungerar på nästan alla typer av objekt.</span><span class="sxs-lookup"><span data-stu-id="f8373-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="f8373-116">De mer avancerade jämförelse operatörerna kanske bara arbetar med text eller matriser.</span><span class="sxs-lookup"><span data-stu-id="f8373-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="f8373-117">När du arbetar med text är Windows PowerShell-jämförelsen som standard Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="f8373-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="f8373-118">På grund av tolknings överväganden används symboler som <, > och = inte som jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="f8373-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="f8373-119">Jämförelse operatorer består i stället av bokstäver.</span><span class="sxs-lookup"><span data-stu-id="f8373-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="f8373-120">De grundläggande jämförelse operatorerna visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="f8373-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="f8373-121">Jämförelseoperator</span><span class="sxs-lookup"><span data-stu-id="f8373-121">Comparison Operator</span></span>|<span data-ttu-id="f8373-122">Innebörd</span><span class="sxs-lookup"><span data-stu-id="f8373-122">Meaning</span></span>|<span data-ttu-id="f8373-123">Exempel (returnerar true)</span><span class="sxs-lookup"><span data-stu-id="f8373-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="f8373-124">-EQ</span><span class="sxs-lookup"><span data-stu-id="f8373-124">-eq</span></span>|<span data-ttu-id="f8373-125">är lika med</span><span class="sxs-lookup"><span data-stu-id="f8373-125">is equal to</span></span>|<span data-ttu-id="f8373-126">1 – EQ 1</span><span class="sxs-lookup"><span data-stu-id="f8373-126">1 -eq 1</span></span>|
|<span data-ttu-id="f8373-127">-Ne</span><span class="sxs-lookup"><span data-stu-id="f8373-127">-ne</span></span>|<span data-ttu-id="f8373-128">Är inte lika med</span><span class="sxs-lookup"><span data-stu-id="f8373-128">Is not equal to</span></span>|<span data-ttu-id="f8373-129">1 – Ne 2</span><span class="sxs-lookup"><span data-stu-id="f8373-129">1 -ne 2</span></span>|
|<span data-ttu-id="f8373-130">-lt</span><span class="sxs-lookup"><span data-stu-id="f8373-130">-lt</span></span>|<span data-ttu-id="f8373-131">Är mindre än</span><span class="sxs-lookup"><span data-stu-id="f8373-131">Is less than</span></span>|<span data-ttu-id="f8373-132">1 – lt 2</span><span class="sxs-lookup"><span data-stu-id="f8373-132">1 -lt 2</span></span>|
|<span data-ttu-id="f8373-133">-Le</span><span class="sxs-lookup"><span data-stu-id="f8373-133">-le</span></span>|<span data-ttu-id="f8373-134">är mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="f8373-134">Is less than or equal to</span></span>|<span data-ttu-id="f8373-135">1 – Le 2</span><span class="sxs-lookup"><span data-stu-id="f8373-135">1 -le 2</span></span>|
|<span data-ttu-id="f8373-136">-gt</span><span class="sxs-lookup"><span data-stu-id="f8373-136">-gt</span></span>|<span data-ttu-id="f8373-137">Är större än</span><span class="sxs-lookup"><span data-stu-id="f8373-137">Is greater than</span></span>|<span data-ttu-id="f8373-138">2 – gt 1</span><span class="sxs-lookup"><span data-stu-id="f8373-138">2 -gt 1</span></span>|
|<span data-ttu-id="f8373-139">-ge</span><span class="sxs-lookup"><span data-stu-id="f8373-139">-ge</span></span>|<span data-ttu-id="f8373-140">är större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="f8373-140">Is greater than or equal to</span></span>|<span data-ttu-id="f8373-141">2-ge 1</span><span class="sxs-lookup"><span data-stu-id="f8373-141">2 -ge 1</span></span>|
|<span data-ttu-id="f8373-142">– som</span><span class="sxs-lookup"><span data-stu-id="f8373-142">-like</span></span>|<span data-ttu-id="f8373-143">Liknar (jämförelse av jokertecken för text)</span><span class="sxs-lookup"><span data-stu-id="f8373-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="f8373-144">"File. doc" – som "f\*. gör?"</span><span class="sxs-lookup"><span data-stu-id="f8373-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="f8373-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="f8373-145">-notlike</span></span>|<span data-ttu-id="f8373-146">Liknar inte (jämförelse av jokertecken för text)</span><span class="sxs-lookup"><span data-stu-id="f8373-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="f8373-147">"File. doc"-notlike "p\*. doc"</span><span class="sxs-lookup"><span data-stu-id="f8373-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="f8373-148">– innehåller</span><span class="sxs-lookup"><span data-stu-id="f8373-148">-contains</span></span>|<span data-ttu-id="f8373-149">innehåller</span><span class="sxs-lookup"><span data-stu-id="f8373-149">Contains</span></span>|<span data-ttu-id="f8373-150">1, 2, 3 – innehåller 1</span><span class="sxs-lookup"><span data-stu-id="f8373-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="f8373-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="f8373-151">-notcontains</span></span>|<span data-ttu-id="f8373-152">Innehåller inte</span><span class="sxs-lookup"><span data-stu-id="f8373-152">Does not contain</span></span>|<span data-ttu-id="f8373-153">1, 2, 3-notcontains 4</span><span class="sxs-lookup"><span data-stu-id="f8373-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="f8373-154">Where-Object skript block använder den särskilda variabeln `$_` för att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="f8373-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="f8373-155">Här är ett exempel på hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="f8373-155">Here is an example of how it works.</span></span> <span data-ttu-id="f8373-156">Om du har en lista med tal, och bara vill returnera de som är mindre än 3, kan du använda Where-Object för att filtrera talen genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="f8373-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

## <a name="filtering-based-on-object-properties"></a><span data-ttu-id="f8373-157">Filtrering baserat på objekt egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8373-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="f8373-158">Eftersom `$_` refererar till det aktuella pipeline-objektet kan vi komma åt dess egenskaper för våra tester.</span><span class="sxs-lookup"><span data-stu-id="f8373-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="f8373-159">Vi kan till exempel titta på Win32_SystemDriver-klassen i WMI.</span><span class="sxs-lookup"><span data-stu-id="f8373-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="f8373-160">Det kan finnas hundratals system driv rutiner i ett visst system, men du kanske bara är intresse rad av en viss uppsättning system driv rutiner, till exempel de som för närvarande körs.</span><span class="sxs-lookup"><span data-stu-id="f8373-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="f8373-161">Om du använder Get-Member för att Visa Win32_SystemDriver medlemmar (**Get-WmiObject-Class Win32_SystemDriver | Get-Member-MemberType-egenskap**) ser du att relevant egenskap är State och att den har värdet "körs" när driv rutinen körs.</span><span class="sxs-lookup"><span data-stu-id="f8373-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="f8373-162">Du kan filtrera system driv rutinerna, välja enbart de som körs genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="f8373-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="f8373-163">Detta skapar fortfarande en lång lista.</span><span class="sxs-lookup"><span data-stu-id="f8373-163">This still produces a long list.</span></span> <span data-ttu-id="f8373-164">Du kanske vill filtrera för att endast välja de driv rutiner som ska starta automatiskt genom att testa start mode-värdet också:</span><span class="sxs-lookup"><span data-stu-id="f8373-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

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
```

<span data-ttu-id="f8373-165">Detta ger oss mycket information som vi inte längre behöver eftersom vi vet att driv rutinerna körs.</span><span class="sxs-lookup"><span data-stu-id="f8373-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="f8373-166">Den enda information som vi förmodligen behöver i det här läget är i själva verket namnet och visnings namnet.</span><span class="sxs-lookup"><span data-stu-id="f8373-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="f8373-167">Följande kommando innehåller bara de två egenskaperna, vilket resulterar i mycket enklare utdata:</span><span class="sxs-lookup"><span data-stu-id="f8373-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="f8373-168">Det finns två element i WHERE-objekt i ovanstående kommando, men de kan uttryckas i ett enda WHERE-objekt-element med hjälp av operatorn-och logiska operatorn, så här:</span><span class="sxs-lookup"><span data-stu-id="f8373-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="f8373-169">De logiska standard operatörerna visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="f8373-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="f8373-170">Logisk operator</span><span class="sxs-lookup"><span data-stu-id="f8373-170">Logical Operator</span></span>|<span data-ttu-id="f8373-171">Innebörd</span><span class="sxs-lookup"><span data-stu-id="f8373-171">Meaning</span></span>|<span data-ttu-id="f8373-172">Exempel (returnerar true)</span><span class="sxs-lookup"><span data-stu-id="f8373-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="f8373-173">-och</span><span class="sxs-lookup"><span data-stu-id="f8373-173">-and</span></span>|<span data-ttu-id="f8373-174">Logisk och; sant om båda sidorna är sanna</span><span class="sxs-lookup"><span data-stu-id="f8373-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="f8373-175">(1 – EQ 1)-och (2-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="f8373-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="f8373-176">-eller</span><span class="sxs-lookup"><span data-stu-id="f8373-176">-or</span></span>|<span data-ttu-id="f8373-177">Logiskt eller; sant om endera sidan är sann</span><span class="sxs-lookup"><span data-stu-id="f8373-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="f8373-178">(1 – EQ 1)-eller (1-EQ 2)</span><span class="sxs-lookup"><span data-stu-id="f8373-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="f8373-179">– inte</span><span class="sxs-lookup"><span data-stu-id="f8373-179">-not</span></span>|<span data-ttu-id="f8373-180">Logiskt not; ångrar sant och falskt</span><span class="sxs-lookup"><span data-stu-id="f8373-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="f8373-181">– inte (1 – EQ 2)</span><span class="sxs-lookup"><span data-stu-id="f8373-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="f8373-182">Logiskt not; ångrar sant och falskt</span><span class="sxs-lookup"><span data-stu-id="f8373-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="f8373-183">\!(1 – EQ 2)</span><span class="sxs-lookup"><span data-stu-id="f8373-183">\!(1 -eq 2)</span></span>|
