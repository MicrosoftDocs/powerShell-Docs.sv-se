---
description: Beskriver hur du använder metoder för att utföra åtgärder på objekt i PowerShell.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Methods
ms.openlocfilehash: 35eaafcec5d645be6fe88f506bc0971344406273
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710219"
---
# <a name="about-methods"></a><span data-ttu-id="9e517-103">Om metoder</span><span class="sxs-lookup"><span data-stu-id="9e517-103">About methods</span></span>

## <a name="short-description"></a><span data-ttu-id="9e517-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="9e517-104">Short description</span></span>
<span data-ttu-id="9e517-105">Beskriver hur du använder metoder för att utföra åtgärder på objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e517-105">Describes how to use methods to perform actions on objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="9e517-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="9e517-106">Long description</span></span>

<span data-ttu-id="9e517-107">PowerShell använder objekt för att representera objekten i data lager eller datorns tillstånd.</span><span class="sxs-lookup"><span data-stu-id="9e517-107">PowerShell uses objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="9e517-108">FileInfo-objekt representerar till exempel filerna i fil system enheter och ProcessInfo-objekt representerar processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="9e517-108">For example, FileInfo objects represent the files in file system drives and ProcessInfo objects represent the processes on the computer.</span></span>

<span data-ttu-id="9e517-109">Objekt har egenskaper, som lagrar data om objektet och metoder som gör att du kan ändra objektet.</span><span class="sxs-lookup"><span data-stu-id="9e517-109">Objects have properties, which store data about the object, and methods that let you change the object.</span></span>

<span data-ttu-id="9e517-110">En "metod" är en uppsättning instruktioner som anger en åtgärd som du kan utföra på objektet.</span><span class="sxs-lookup"><span data-stu-id="9e517-110">A "method" is a set of instructions that specify an action you can perform on the object.</span></span> <span data-ttu-id="9e517-111">Objektet innehåller till exempel `FileInfo` `CopyTo` metoden som kopierar filen som `FileInfo` objektet representerar.</span><span class="sxs-lookup"><span data-stu-id="9e517-111">For example, the `FileInfo` object includes the `CopyTo` method that copies the file that the `FileInfo` object represents.</span></span>

<span data-ttu-id="9e517-112">Använd cmdleten för att hämta metoder för ett objekt `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="9e517-112">To get the methods of any object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="9e517-113">Använd dess **MemberType** -egenskap med värdet "Method".</span><span class="sxs-lookup"><span data-stu-id="9e517-113">Use its **MemberType** property with a value of "Method".</span></span> <span data-ttu-id="9e517-114">Följande kommando hämtar metoderna för process-objekt.</span><span class="sxs-lookup"><span data-stu-id="9e517-114">The following command gets the methods of process objects.</span></span>

```powershell
Get-Process | Get-Member -MemberType Method
```

```Output
TypeName: System.Diagnostics.Process

Name                      MemberType Definition
----                      ---------- ----------
BeginErrorReadLine        Method     System.Void BeginErrorReadLine()
BeginOutputReadLine       Method     System.Void BeginOutputReadLine()
...
Kill                      Method     System.Void Kill()
Refresh                   Method     System.Void Refresh()
Start                     Method     bool Start()
ToString                  Method     string ToString()
WaitForExit               Method     bool WaitForExit(int milliseconds), ...
WaitForInputIdle          Method     bool WaitForInputIdle(int millisecon...
```

<span data-ttu-id="9e517-115">Om du vill utföra eller "anropa" en metod för ett objekt skriver du en punkt (.), metod namnet och en uppsättning parenteser ().</span><span class="sxs-lookup"><span data-stu-id="9e517-115">To perform or "invoke" a method of an object, type a dot (.), the method name, and a set of parentheses "()".</span></span> <span data-ttu-id="9e517-116">Om metoden har argument, placerar du argument värden innanför parenteserna.</span><span class="sxs-lookup"><span data-stu-id="9e517-116">If the method has arguments, place the argument values inside the parentheses.</span></span> <span data-ttu-id="9e517-117">Parenteserna krävs för varje metod anrop, även om det inte finns några argument.</span><span class="sxs-lookup"><span data-stu-id="9e517-117">The parentheses are required for every method call, even when there are no arguments.</span></span> <span data-ttu-id="9e517-118">Om metoden tar flera argument ska de avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="9e517-118">If the method takes multiple arguments, they should be separated by commas.</span></span>

<span data-ttu-id="9e517-119">Till exempel anropar följande kommando metoden Kill of processs för att avsluta Anteckningar-processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="9e517-119">For example, the following command invokes the Kill method of processes to end the Notepad process on the computer.</span></span>

```powershell
$notepad = Get-Process notepad
$notepad.Kill()
```

<span data-ttu-id="9e517-120">Det här exemplet kan kortas ned genom att kombinera ovanstående instruktioner.</span><span class="sxs-lookup"><span data-stu-id="9e517-120">This example can be shortened by combining the above statements.</span></span>

```powershell
(Get-Process Notepad).Kill()
```

<span data-ttu-id="9e517-121">`Get-Process`Kommandot omges av parenteser för att säkerställa att det körs innan Kill-metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="9e517-121">The `Get-Process` command is enclosed in parentheses to ensure that it runs before the Kill method is invoked.</span></span> <span data-ttu-id="9e517-122">`Kill`Metoden anropas sedan på det returnerade `Process` objektet.</span><span class="sxs-lookup"><span data-stu-id="9e517-122">The `Kill` method is then invoked on the returned `Process` object.</span></span>

<span data-ttu-id="9e517-123">En annan mycket användbar metod är `Replace` metoden för strängar.</span><span class="sxs-lookup"><span data-stu-id="9e517-123">Another very useful method is the `Replace` method of strings.</span></span> <span data-ttu-id="9e517-124">`Replace`Metoden ersätter text i en sträng.</span><span class="sxs-lookup"><span data-stu-id="9e517-124">The `Replace` method, replaces text within a string.</span></span> <span data-ttu-id="9e517-125">I exemplet nedan kan punkt (.) placeras omedelbart efter slut citatet i strängen.</span><span class="sxs-lookup"><span data-stu-id="9e517-125">In the example below, the dot (.) can be placed immediately after the end quote of the string.</span></span>

```powershell
'this is rocket science'.Replace('rocket', 'rock')
```

```Output
this is rock science
```

<span data-ttu-id="9e517-126">Som du ser i föregående exempel kan du anropa en metod för ett objekt som du får genom att använda ett kommando, ett objekt i en variabel eller något som resulterar i ett objekt (som en sträng i citat tecken).</span><span class="sxs-lookup"><span data-stu-id="9e517-126">As shown in the previous examples, you can invoke a method on an object that you get by using a command, an object in a variable, or anything that results in an object (like a string in quotes).</span></span>

<span data-ttu-id="9e517-127">Från och med PowerShell 4,0 stöds metod anrop med dynamiska metod namn.</span><span class="sxs-lookup"><span data-stu-id="9e517-127">Starting in PowerShell 4.0, method invocation by using dynamic method names is supported.</span></span>

### <a name="learning-about-methods"></a><span data-ttu-id="9e517-128">Lär dig mer om metoder</span><span class="sxs-lookup"><span data-stu-id="9e517-128">Learning about methods</span></span>

<span data-ttu-id="9e517-129">Om du vill hitta definitioner för ett objekts metoder går du till hjälp avsnittet för objekt typen och letar efter dess metoder-sida.</span><span class="sxs-lookup"><span data-stu-id="9e517-129">To find definitions of the methods of an object, go to help topic for the object type and look for its methods page.</span></span> <span data-ttu-id="9e517-130">Till exempel beskriver följande sida metoder för process objekt [system. Diagnostics. process](/dotnet/api/system.diagnostics.process#methods).</span><span class="sxs-lookup"><span data-stu-id="9e517-130">For example, the following page describes the methods of process objects [System.Diagnostics.Process](/dotnet/api/system.diagnostics.process#methods).</span></span>

<span data-ttu-id="9e517-131">Om du vill fastställa argumenten för en metod granskar du metod definitionen, som liknar syntax diagrammet för en PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e517-131">To determine the arguments of a method, review the method definition, which is like the syntax diagram of a PowerShell cmdlet.</span></span>

<span data-ttu-id="9e517-132">En metod definition kan ha en eller flera metod-signaturer, som liknar parameter uppsättningarna i PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="9e517-132">A method definition might have one or more method signatures, which are like the parameter sets of PowerShell cmdlets.</span></span> <span data-ttu-id="9e517-133">Signaturerna visar alla giltiga format för kommandon för att anropa-metoden.</span><span class="sxs-lookup"><span data-stu-id="9e517-133">The signatures show all of the valid formats of commands to invoke the method.</span></span>

<span data-ttu-id="9e517-134">`CopyTo`Metoden för `FileInfo` klassen innehåller till exempel följande två signaturer för metoden:</span><span class="sxs-lookup"><span data-stu-id="9e517-134">For example, the `CopyTo` method of the `FileInfo` class contains the following two method signatures:</span></span>

```
    CopyTo(String destFileName)
    CopyTo(String destFileName, Boolean overwrite)
```

<span data-ttu-id="9e517-135">Den första metoden signaturen använder mål fil namnet (och en sökväg).</span><span class="sxs-lookup"><span data-stu-id="9e517-135">The first method signature takes the destination file name (and a path).</span></span> <span data-ttu-id="9e517-136">I följande exempel används den första `CopyTo` metoden för att kopiera `Final.txt` filen till `C:\Bin` katalogen.</span><span class="sxs-lookup"><span data-stu-id="9e517-136">The following example uses the first `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt")
```

> [!NOTE]
> <span data-ttu-id="9e517-137">Till skillnad från PowerShell: s _argument_ läge körs objekt metoder i _uttrycks_ läge, som är ett pass-till-.NET Framework som PowerShell bygger på.</span><span class="sxs-lookup"><span data-stu-id="9e517-137">Unlike PowerShell's _argument_ mode, object methods execute in _expression_ mode, which is a pass-through to the .NET framework that PowerShell is built on.</span></span> <span data-ttu-id="9e517-138">I _uttrycks_ läge **bareword** argument (icke-citerade strängar) tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="9e517-138">In _expression_ mode **bareword** arguments (unquoted strings) are not allowed.</span></span> <span data-ttu-id="9e517-139">Du kan se skillnaden när du använder en sökväg som parameter, jämfört med sökvägen som ett argument.</span><span class="sxs-lookup"><span data-stu-id="9e517-139">You can see this difference when using a the path as a parameter, versus the path as an argument.</span></span> <span data-ttu-id="9e517-140">Du kan läsa mer om tolknings lägen i [about_Parsing](about_Parsing.md)</span><span class="sxs-lookup"><span data-stu-id="9e517-140">You can read more about parsing modes in [about_Parsing](about_Parsing.md)</span></span>

<span data-ttu-id="9e517-141">Signaturen för den andra metoden tar ett mål fil namn och ett booleskt värde som avgör om mål filen ska skrivas över, om den redan finns.</span><span class="sxs-lookup"><span data-stu-id="9e517-141">The second method signature takes a destination file name and a Boolean value that determines whether the destination file should be overwritten, if it already exists.</span></span>

<span data-ttu-id="9e517-142">I följande exempel används den andra `CopyTo` metoden för att kopiera `Final.txt` filen till `C:\Bin` katalogen och för att skriva över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="9e517-142">The following example uses the second `CopyTo` method to copy the `Final.txt` file to the `C:\Bin` directory, and to overwrite existing files.</span></span>

```powershell
(Get-ChildItem c:\final.txt).CopyTo("c:\bin\final.txt", $true)
```

### <a name="methods-of-scalar-objects-and-collections"></a><span data-ttu-id="9e517-143">Metoder för skalära objekt och samlingar</span><span class="sxs-lookup"><span data-stu-id="9e517-143">Methods of Scalar objects and Collections</span></span>

<span data-ttu-id="9e517-144">Metoderna för ett ("skalär") objekt av en viss typ skiljer sig ofta från metoder för en samling objekt av samma typ.</span><span class="sxs-lookup"><span data-stu-id="9e517-144">The methods of one ("scalar") object of a particular type are often different from the methods of a collection of objects of the same type.</span></span>

<span data-ttu-id="9e517-145">Till exempel har varje process en `Kill` metod, men en samling processer har ingen Kill-metod.</span><span class="sxs-lookup"><span data-stu-id="9e517-145">For example, every process has a `Kill` method, but a collection of processes does not have a Kill method.</span></span>

<span data-ttu-id="9e517-146">Från och med PowerShell 3,0 försöker PowerShell förhindra skript fel som orsakas av olika metoder för skalära objekt och samlingar.</span><span class="sxs-lookup"><span data-stu-id="9e517-146">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing methods of scalar objects and collections.</span></span>

<span data-ttu-id="9e517-147">Om du skickar en samling, men begär en metod som bara finns på en("skalär") objekt, anropar PowerShell metoden på alla objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="9e517-147">If you submit a collection, but request a method that exists only on single ("scalar") objects, PowerShell invokes the method on every object in the collection.</span></span>

<span data-ttu-id="9e517-148">Om metoden finns på de enskilda objekten och i samlingen, anropas bara samlingens metod.</span><span class="sxs-lookup"><span data-stu-id="9e517-148">If the method exists on the individual objects and on the collection, only the collection's method is invoked.</span></span>

<span data-ttu-id="9e517-149">Den här funktionen fungerar också med egenskaper för skalära objekt och samlingar.</span><span class="sxs-lookup"><span data-stu-id="9e517-149">This feature also works on properties of scalar objects and collections.</span></span> <span data-ttu-id="9e517-150">Mer information finns i [about_Properties](about_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="9e517-150">For more information, see [about_Properties](about_Properties.md).</span></span>

### <a name="examples"></a><span data-ttu-id="9e517-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="9e517-151">Examples</span></span>

<span data-ttu-id="9e517-152">I följande exempel körs metoden **Kill** för enskilda process objekt i en objekt samling.</span><span class="sxs-lookup"><span data-stu-id="9e517-152">The following example runs the **Kill** method of individual process objects in a collection of objects.</span></span>

<span data-ttu-id="9e517-153">Det första kommandot startar tre instanser av anteckningar-processen.</span><span class="sxs-lookup"><span data-stu-id="9e517-153">The first command starts three instances of the Notepad process.</span></span> <span data-ttu-id="9e517-154">`Get-Process` hämtar alla tre instanserna av anteckningar-processen och sparar dem i `$p` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9e517-154">`Get-Process` gets all three instance of the Notepad process and saves them in the `$p` variable.</span></span>

```powershell
Notepad; Notepad; Notepad
$p = Get-Process Notepad
$p.Count
```

```Output
3
```

<span data-ttu-id="9e517-155">Nästa kommando kör metoden **Kill** på alla tre processerna i `$p` variabeln.</span><span class="sxs-lookup"><span data-stu-id="9e517-155">The next command runs the **Kill** method on all three processes in the `$p` variable.</span></span> <span data-ttu-id="9e517-156">Kommandot fungerar även om en samling processer inte har någon `Kill` metod.</span><span class="sxs-lookup"><span data-stu-id="9e517-156">This command works even though a collection of processes does not have a `Kill` method.</span></span>

```powershell
$p.Kill()
Get-Process Notepad
```

<span data-ttu-id="9e517-157">`Get-Process`Kommandot bekräftar att `Kill` metoden fungerade.</span><span class="sxs-lookup"><span data-stu-id="9e517-157">The `Get-Process` command confirms that the `Kill` method worked.</span></span>

```Output
Get-Process : Cannot find a process with the name "notepad". Verify the proc
ess name and call the cmdlet again.
At line:1 char:12
+ Get-Process <<<<  notepad
    + CategoryInfo          : ObjectNotFound: (notepad:String) [Get-Process]
, ProcessCommandException
    + FullyQualifiedErrorId : NoProcessFoundForGivenName,Microsoft.PowerShel
l.Commands.GetProcessCommand
```

<span data-ttu-id="9e517-158">Det här exemplet är detsamma som att använda `Foreach-Object` cmdleten för att köra metoden på varje objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="9e517-158">This example is functionally equivalent to using the `Foreach-Object` cmdlet to run the method on each object in the collection.</span></span>

```powershell
$p | ForEach-Object {$_.Kill()}
```

### <a name="foreach-and-where-methods"></a><span data-ttu-id="9e517-159">Förvars och var metoderna</span><span class="sxs-lookup"><span data-stu-id="9e517-159">ForEach and Where methods</span></span>

<span data-ttu-id="9e517-160">Från och med PowerShell 4,0 stöds samlings filtrering med hjälp av metoden syntax.</span><span class="sxs-lookup"><span data-stu-id="9e517-160">Beginning in PowerShell 4.0, collection filtering by using a method syntax is supported.</span></span> <span data-ttu-id="9e517-161">Detta gör att du kan använda två nya metoder när du hanterar samlingar `ForEach` och `Where` .</span><span class="sxs-lookup"><span data-stu-id="9e517-161">This allows use of two new methods when dealing with collections `ForEach` and `Where`.</span></span>

<span data-ttu-id="9e517-162">Du kan läsa mer om de här metoderna i [about_arrays](about_arrays.md)</span><span class="sxs-lookup"><span data-stu-id="9e517-162">You can read more about these methods in [about_arrays](about_arrays.md)</span></span>

### <a name="calling-a-specific-method-when-multiple-overloads-exist"></a><span data-ttu-id="9e517-163">Anropa en speciell metod när det finns flera överlagringar</span><span class="sxs-lookup"><span data-stu-id="9e517-163">Calling a specific method when multiple overloads exist</span></span>

<span data-ttu-id="9e517-164">Tänk dig följande scenario när du anropar .NET-metoder.</span><span class="sxs-lookup"><span data-stu-id="9e517-164">Consider the following scenario when calling .NET methods.</span></span> <span data-ttu-id="9e517-165">Om en metod tar ett objekt men har en överlagring via ett gränssnitt med en mer specifik typ, väljer PowerShell den metod som accepterar objektet om du inte uttryckligen skickar den till det gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="9e517-165">If a method takes an object but has an overload via an interface taking a more specific type, PowerShell chooses the method that accepts the object unless you explicitly cast it to that interface.</span></span>

```powershell
Add-Type -TypeDefinition @'

   // Interface
   public interface IFoo {
     string Bar(int p);
   }

   // Type that implements the interface
   public class Foo : IFoo {

   // Direct member method named 'Bar'
   public string Bar(object p) { return $"object: {p}"; }

   // *Explicit* implementation of IFoo's 'Bar' method().
   string IFoo.Bar(int p) {
       return $"int: {p}";
   }

}
'@
```

<span data-ttu-id="9e517-166">I det här exemplet `object` valdes mindre viss överbelastning för **stapel** -metoden.</span><span class="sxs-lookup"><span data-stu-id="9e517-166">In this example the less specific `object` overload of the **Bar** method was chosen.</span></span>

```powershell
[Foo]::new().Bar(1)
```

```Output
object: 1
```

<span data-ttu-id="9e517-167">I det här exemplet har vi omvandlat-metoden till gränssnittet **IFoo** för att välja en mer detaljerad överlagring av **streckkods** metoden.</span><span class="sxs-lookup"><span data-stu-id="9e517-167">In this example we cast the method to the interface **IFoo** to select the more specific overload of the **Bar** method.</span></span>

```powershell
([IFoo] [Foo]::new()).Bar(1)
```

```Output
int: 1
```

## <a name="see-also"></a><span data-ttu-id="9e517-168">Se även</span><span class="sxs-lookup"><span data-stu-id="9e517-168">See Also</span></span>

[<span data-ttu-id="9e517-169">about_Objects</span><span class="sxs-lookup"><span data-stu-id="9e517-169">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="9e517-170">about_Properties</span><span class="sxs-lookup"><span data-stu-id="9e517-170">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="9e517-171">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="9e517-171">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
