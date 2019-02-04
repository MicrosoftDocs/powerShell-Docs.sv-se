---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Ta bort objekt från pipelinen Where-Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: c060b93a3823be26ad6c7757acc633bb4fc2fcfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685727"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="a59ad-103">Ta bort objekt från pipelinen (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="a59ad-103">Removing Objects from the Pipeline (Where-Object)</span></span>

<span data-ttu-id="a59ad-104">I Windows PowerShell kan du ofta generera och skicka längs flera objekt till en pipeline än vad du vill.</span><span class="sxs-lookup"><span data-stu-id="a59ad-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="a59ad-105">Du kan ange egenskaperna för specifika objekt som ska visas med hjälp av den **Format** cmdlet: ar, men detta inte hjälper med problemet med att ta bort hela objekt från visningen.</span><span class="sxs-lookup"><span data-stu-id="a59ad-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="a59ad-106">Du kanske vill filtrera objekten innan slutet av en pipeline, så att du kan utföra åtgärder på endast en delmängd av objekt som ursprungligen genererades.</span><span class="sxs-lookup"><span data-stu-id="a59ad-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="a59ad-107">Windows PowerShell innehåller en `Where-Object` cmdlet som gör att du kan testa varje objekt i pipelinen och endast skicka dem längsmed pipelinen om den uppfyller ett visst test-villkor.</span><span class="sxs-lookup"><span data-stu-id="a59ad-107">Windows PowerShell includes a `Where-Object` cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="a59ad-108">Objekt som inte klarar testet tas bort från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a59ad-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="a59ad-109">Du kan ange testvillkoret som värde för den `Where-Object` **FilterScript** parametern.</span><span class="sxs-lookup"><span data-stu-id="a59ad-109">You supply the test condition as the value of the `Where-Object` **FilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="a59ad-110">Utför enkla tester med Where-Object</span><span class="sxs-lookup"><span data-stu-id="a59ad-110">Performing Simple Tests with Where-Object</span></span>

<span data-ttu-id="a59ad-111">Värdet för **FilterScript** är en *skriptblock* -en eller flera Windows PowerShell-kommandon som omges av klammerparenteser {} -som utvärderas SANT eller FALSKT.</span><span class="sxs-lookup"><span data-stu-id="a59ad-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="a59ad-112">Dessa skriptblocken kan vara väldigt enkelt skapa dem kräver dock att känna till om en annan Windows PowerShell-koncept jämförelseoperatorer.</span><span class="sxs-lookup"><span data-stu-id="a59ad-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="a59ad-113">Jämförelseoperator jämför de objekt som visas på varje sida.</span><span class="sxs-lookup"><span data-stu-id="a59ad-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="a59ad-114">Jämförelseoperatorer börjar med en '-' tecken och följas av ett namn.</span><span class="sxs-lookup"><span data-stu-id="a59ad-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="a59ad-115">Grundläggande jämförelseoperatorer fungerar på nästan vilken typ av objekt.</span><span class="sxs-lookup"><span data-stu-id="a59ad-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="a59ad-116">Mer avancerade jämförelseoperatorer kanske bara fungerar på text eller matriser.</span><span class="sxs-lookup"><span data-stu-id="a59ad-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="a59ad-117">Som standard när du arbetar med text, är Windows PowerShell-jämförelseoperatorer skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="a59ad-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="a59ad-118">På grund av parsning överväganden symboler till exempel <>, och = inte används som jämförelseoperatorer.</span><span class="sxs-lookup"><span data-stu-id="a59ad-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="a59ad-119">I stället består jämförelseoperatorer av bokstäver.</span><span class="sxs-lookup"><span data-stu-id="a59ad-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="a59ad-120">Grundläggande jämförelseoperatorer visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="a59ad-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="a59ad-121">Jämförelseoperator</span><span class="sxs-lookup"><span data-stu-id="a59ad-121">Comparison Operator</span></span>|<span data-ttu-id="a59ad-122">Innebörd</span><span class="sxs-lookup"><span data-stu-id="a59ad-122">Meaning</span></span>|<span data-ttu-id="a59ad-123">Exempel (returnerar true)</span><span class="sxs-lookup"><span data-stu-id="a59ad-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="a59ad-124">-eq</span><span class="sxs-lookup"><span data-stu-id="a59ad-124">-eq</span></span>|<span data-ttu-id="a59ad-125">är lika med</span><span class="sxs-lookup"><span data-stu-id="a59ad-125">is equal to</span></span>|<span data-ttu-id="a59ad-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="a59ad-126">1 -eq 1</span></span>|
|<span data-ttu-id="a59ad-127">-ne</span><span class="sxs-lookup"><span data-stu-id="a59ad-127">-ne</span></span>|<span data-ttu-id="a59ad-128">Är inte lika med</span><span class="sxs-lookup"><span data-stu-id="a59ad-128">Is not equal to</span></span>|<span data-ttu-id="a59ad-129">1 - ne 2</span><span class="sxs-lookup"><span data-stu-id="a59ad-129">1 -ne 2</span></span>|
|<span data-ttu-id="a59ad-130">-lt</span><span class="sxs-lookup"><span data-stu-id="a59ad-130">-lt</span></span>|<span data-ttu-id="a59ad-131">är mindre än</span><span class="sxs-lookup"><span data-stu-id="a59ad-131">Is less than</span></span>|<span data-ttu-id="a59ad-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="a59ad-132">1 -lt 2</span></span>|
|<span data-ttu-id="a59ad-133">-le</span><span class="sxs-lookup"><span data-stu-id="a59ad-133">-le</span></span>|<span data-ttu-id="a59ad-134">Är mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="a59ad-134">Is less than or equal to</span></span>|<span data-ttu-id="a59ad-135">1 - le 2</span><span class="sxs-lookup"><span data-stu-id="a59ad-135">1 -le 2</span></span>|
|<span data-ttu-id="a59ad-136">-gt</span><span class="sxs-lookup"><span data-stu-id="a59ad-136">-gt</span></span>|<span data-ttu-id="a59ad-137">är större än</span><span class="sxs-lookup"><span data-stu-id="a59ad-137">Is greater than</span></span>|<span data-ttu-id="a59ad-138">2 - gt 1</span><span class="sxs-lookup"><span data-stu-id="a59ad-138">2 -gt 1</span></span>|
|<span data-ttu-id="a59ad-139">-ge</span><span class="sxs-lookup"><span data-stu-id="a59ad-139">-ge</span></span>|<span data-ttu-id="a59ad-140">Är större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="a59ad-140">Is greater than or equal to</span></span>|<span data-ttu-id="a59ad-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="a59ad-141">2 -ge 1</span></span>|
|<span data-ttu-id="a59ad-142">– t.ex.</span><span class="sxs-lookup"><span data-stu-id="a59ad-142">-like</span></span>|<span data-ttu-id="a59ad-143">Liknar (jokertecken jämförelse för text)</span><span class="sxs-lookup"><span data-stu-id="a59ad-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="a59ad-144">”file.doc”-som ”f\*.skicka”?</span><span class="sxs-lookup"><span data-stu-id="a59ad-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="a59ad-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="a59ad-145">-notlike</span></span>|<span data-ttu-id="a59ad-146">Liknar inte (jokertecken jämförelse för text)</span><span class="sxs-lookup"><span data-stu-id="a59ad-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="a59ad-147">”file.doc”-notlike ”p\*.doc”</span><span class="sxs-lookup"><span data-stu-id="a59ad-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="a59ad-148">-innehåller</span><span class="sxs-lookup"><span data-stu-id="a59ad-148">-contains</span></span>|<span data-ttu-id="a59ad-149">innehåller</span><span class="sxs-lookup"><span data-stu-id="a59ad-149">Contains</span></span>|<span data-ttu-id="a59ad-150">1,2,3 - innehåller 1</span><span class="sxs-lookup"><span data-stu-id="a59ad-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="a59ad-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="a59ad-151">-notcontains</span></span>|<span data-ttu-id="a59ad-152">innehåller inte</span><span class="sxs-lookup"><span data-stu-id="a59ad-152">Does not contain</span></span>|<span data-ttu-id="a59ad-153">1,2,3 - notcontains 4</span><span class="sxs-lookup"><span data-stu-id="a59ad-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="a59ad-154">WHERE-Object-skriptblock använder variabeln särskilda `$_` att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a59ad-154">Where-Object script blocks use the special variable `$_` to refer to the current object in the pipeline.</span></span> <span data-ttu-id="a59ad-155">Här är ett exempel på hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="a59ad-155">Here is an example of how it works.</span></span> <span data-ttu-id="a59ad-156">Om du har en lista med tal och bara vill returnera de som är mindre än 3, kan du använda Where-Object för att filtrera talen genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="a59ad-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="a59ad-157">Filtrering baserat på objektegenskaper</span><span class="sxs-lookup"><span data-stu-id="a59ad-157">Filtering Based on Object Properties</span></span>

<span data-ttu-id="a59ad-158">Eftersom `$_` refererar till det aktuella pipeline-objektet kan vi komma åt egenskaperna för våra tester.</span><span class="sxs-lookup"><span data-stu-id="a59ad-158">Since `$_` refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="a59ad-159">Exempelvis kan vi titta på klassen Win32_SystemDriver i WMI.</span><span class="sxs-lookup"><span data-stu-id="a59ad-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="a59ad-160">Det kan finnas hundratals systemdrivrutiner på ett visst system, men kanske du bara är intresserad av en viss uppsättning systemdrivrutiner, till exempel de som för närvarande körs.</span><span class="sxs-lookup"><span data-stu-id="a59ad-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="a59ad-161">Om du använder Get-Member för att visa Win32_SystemDriver medlemmar (**Get-WmiObject-klassen Win32_SystemDriver | Get-Member - MemberType egenskapen**) visas att egenskapen relevanta är tillstånd och att den har ett värde ”körs” när drivrutinen körs.</span><span class="sxs-lookup"><span data-stu-id="a59ad-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="a59ad-162">Du kan filtrera systemdrivrutiner, att välja endast de som körs som genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="a59ad-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

<span data-ttu-id="a59ad-163">Detta ger ändå en lång lista.</span><span class="sxs-lookup"><span data-stu-id="a59ad-163">This still produces a long list.</span></span> <span data-ttu-id="a59ad-164">Du kanske vill filtrera för att välja endast de drivrutiner som är konfigurerad att starta automatiskt genom att testa värdet StartMode:</span><span class="sxs-lookup"><span data-stu-id="a59ad-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

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

<span data-ttu-id="a59ad-165">Det ger oss en mängd information som vi behöver inte längre eftersom vi vet att drivrutinerna som körs.</span><span class="sxs-lookup"><span data-stu-id="a59ad-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="a59ad-166">I själva verket är den enda information som vi behöver förmodligen nu namn och visningsnamn.</span><span class="sxs-lookup"><span data-stu-id="a59ad-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="a59ad-167">Följande kommando innehåller endast de två egenskaper, vilket resulterar i mycket enklare utdata:</span><span class="sxs-lookup"><span data-stu-id="a59ad-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

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

<span data-ttu-id="a59ad-168">Det finns två Where-Object-element i kommandot ovan, men de kan uttryckas i ett enda Where-Object-element med hjälp av- och den logiska operatorn så här:</span><span class="sxs-lookup"><span data-stu-id="a59ad-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="a59ad-169">De logiska operatorerna som standard visas i följande tabell.</span><span class="sxs-lookup"><span data-stu-id="a59ad-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="a59ad-170">Logisk Operator</span><span class="sxs-lookup"><span data-stu-id="a59ad-170">Logical Operator</span></span>|<span data-ttu-id="a59ad-171">Innebörd</span><span class="sxs-lookup"><span data-stu-id="a59ad-171">Meaning</span></span>|<span data-ttu-id="a59ad-172">Exempel (returnerar true)</span><span class="sxs-lookup"><span data-stu-id="a59ad-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="a59ad-173">- och</span><span class="sxs-lookup"><span data-stu-id="a59ad-173">-and</span></span>|<span data-ttu-id="a59ad-174">Logiska och; TRUE om båda sidorna utvärderas som true</span><span class="sxs-lookup"><span data-stu-id="a59ad-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="a59ad-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a59ad-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="a59ad-176">- eller</span><span class="sxs-lookup"><span data-stu-id="a59ad-176">-or</span></span>|<span data-ttu-id="a59ad-177">Logiska eller; SANT om endera sida är true</span><span class="sxs-lookup"><span data-stu-id="a59ad-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="a59ad-178">(1 - eq 1) - eller (1 - eq 2).</span><span class="sxs-lookup"><span data-stu-id="a59ad-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="a59ad-179">-inte</span><span class="sxs-lookup"><span data-stu-id="a59ad-179">-not</span></span>|<span data-ttu-id="a59ad-180">Logiskt not; omvänd true och false</span><span class="sxs-lookup"><span data-stu-id="a59ad-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="a59ad-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a59ad-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="a59ad-182">Logiskt not; omvänd true och false</span><span class="sxs-lookup"><span data-stu-id="a59ad-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="a59ad-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="a59ad-183">\!(1 -eq 2)</span></span>|
