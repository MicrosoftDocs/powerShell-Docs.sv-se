---
title: Lägga till alias, expansion med jokertecken och hjälp till cmdlet-parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 244c50c73972c2760e0029c7fa4f4b5764b066da
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774974"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="1fc35-102">Lägga till alias, jokerteckenexpansion och hjälp i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="1fc35-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="1fc35-103">I det här avsnittet beskrivs hur du lägger till alias, expansion av jokertecken och hjälp meddelanden till parametrarna i cmdleten Stop-proc (beskrivs i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="1fc35-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="1fc35-104">Den här cmdleten Stop-proc försöker stoppa processer som hämtas med hjälp av cmdleten Get-proc (beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="1fc35-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="1fc35-105">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="1fc35-105">Defining the Cmdlet</span></span>

<span data-ttu-id="1fc35-106">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1fc35-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="1fc35-107">Eftersom du skriver en cmdlet för att ändra systemet bör den namnges.</span><span class="sxs-lookup"><span data-stu-id="1fc35-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="1fc35-108">Eftersom denna cmdlet stoppar system processer använder den verbet "Stop", som definieras av klassen [system. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , med Substantiv "proc" för att indikera processen.</span><span class="sxs-lookup"><span data-stu-id="1fc35-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="1fc35-109">Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="1fc35-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="1fc35-110">Följande kod är klass definitionen för den här Stop-proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1fc35-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="1fc35-111">Definiera parametrar för system ändring</span><span class="sxs-lookup"><span data-stu-id="1fc35-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="1fc35-112">Din cmdlet måste definiera parametrar som stöder system ändringar och feedback från användare.</span><span class="sxs-lookup"><span data-stu-id="1fc35-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="1fc35-113">Cmdleten bör definiera en `Name` parameter eller motsvarande så att cmdleten kan ändra systemet med en viss typ av identifierare.</span><span class="sxs-lookup"><span data-stu-id="1fc35-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="1fc35-114">Dessutom bör cmdleten definiera `Force` `PassThru` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="1fc35-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="1fc35-115">Mer information om dessa parametrar finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1fc35-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="1fc35-116">Definiera ett parameter Ali Aset</span><span class="sxs-lookup"><span data-stu-id="1fc35-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="1fc35-117">Ett parameter Ali Aset kan vara ett alternativt namn eller ett väldefinierat kort namn eller kort namn för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="1fc35-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="1fc35-118">I båda fallen är syftet med att använda alias att förenkla användar posten från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1fc35-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="1fc35-119">Windows PowerShell stöder parameter-alias via attributet [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) , som använder deklarationssyntax [alias ()].</span><span class="sxs-lookup"><span data-stu-id="1fc35-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="1fc35-120">Följande kod visar hur ett alias läggs till i `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="1fc35-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="1fc35-121">Förutom att använda attributet [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) , utför Windows PowerShell-körningen partiell namn matchning, även om inga alias anges.</span><span class="sxs-lookup"><span data-stu-id="1fc35-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="1fc35-122">Om din cmdlet till exempel har en `FileName` parameter och det är den enda parameter som börjar med `F` , kan användaren ange `Filename` ,,, `Filenam` `File` `Fi` eller `F` och fortfarande använda posten som `FileName` parameter.</span><span class="sxs-lookup"><span data-stu-id="1fc35-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="1fc35-123">Skapar hjälp för parametrar</span><span class="sxs-lookup"><span data-stu-id="1fc35-123">Creating Help for Parameters</span></span>

<span data-ttu-id="1fc35-124">Med Windows PowerShell kan du skapa hjälp för cmdlet-parametrar.</span><span class="sxs-lookup"><span data-stu-id="1fc35-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="1fc35-125">Gör detta för alla parametrar som används för system ändringar och feedback från användare.</span><span class="sxs-lookup"><span data-stu-id="1fc35-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="1fc35-126">För varje parameter som stöd för hjälp kan du ange `HelpMessage` nyckelordet Attribute i deklarationen [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -attribut.</span><span class="sxs-lookup"><span data-stu-id="1fc35-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="1fc35-127">Det här nyckelordet definierar texten som ska visas för användaren för hjälp med att använda-parametern.</span><span class="sxs-lookup"><span data-stu-id="1fc35-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="1fc35-128">Du kan också ange `HelpMessageBaseName` nyckelordet för att identifiera bas namnet för en resurs som ska användas för meddelandet.</span><span class="sxs-lookup"><span data-stu-id="1fc35-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="1fc35-129">Om du anger det här nyckelordet måste du också ange ett `HelpMessageResourceId` nyckelord för att ange resurs-ID.</span><span class="sxs-lookup"><span data-stu-id="1fc35-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="1fc35-130">Följande kod från denna Stop-proc-cmdlet definierar `HelpMessage` attributets nyckelord för `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="1fc35-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="1fc35-131">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="1fc35-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="1fc35-132">Din cmdlet måste åsidosätta en metod för bearbetning av indata, oftast är detta [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="1fc35-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="1fc35-133">När du ändrar systemet bör cmdleten anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) för att tillåta användaren att ge feedback innan en ändring görs.</span><span class="sxs-lookup"><span data-stu-id="1fc35-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="1fc35-134">Mer information om dessa metoder finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="1fc35-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="1fc35-135">Stöd för expansion med jokertecken</span><span class="sxs-lookup"><span data-stu-id="1fc35-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="1fc35-136">Om du vill tillåta att flera objekt väljs kan din cmdlet använda klassen [system. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) och [system. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) för att ge stöd för stöd för jokertecken för parameter ingångar.</span><span class="sxs-lookup"><span data-stu-id="1fc35-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="1fc35-137">Exempel på mönster för jokertecken är LSA \*, \* . txt och [a-c] \* .</span><span class="sxs-lookup"><span data-stu-id="1fc35-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="1fc35-138">Använd det bakre citat tecknet (") som ett escape-tecken när mönstret innehåller ett tecken som ska användas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="1fc35-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="1fc35-139">Jokertecken för fil-och Sök vägs namn är exempel på vanliga scenarier där cmdleten kanske vill tillåta stöd för Path-indata när valet av flera objekt krävs.</span><span class="sxs-lookup"><span data-stu-id="1fc35-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="1fc35-140">Ett vanligt fall är i fil systemet, där en användare vill se alla filer som finns i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="1fc35-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="1fc35-141">Du bör ha en anpassad matchning av jokertecken som matchar implementeringen sällan.</span><span class="sxs-lookup"><span data-stu-id="1fc35-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="1fc35-142">I det här fallet ska din cmdlet ha stöd för antingen den fullständiga POSIX 1003,2, 3,13-specifikationen för expansion av jokertecken eller följande förenklade del mängd:</span><span class="sxs-lookup"><span data-stu-id="1fc35-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="1fc35-143">**Frågetecken (?).**</span><span class="sxs-lookup"><span data-stu-id="1fc35-143">**Question mark (?).**</span></span> <span data-ttu-id="1fc35-144">Matchar alla bokstäver på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="1fc35-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="1fc35-145">**Asterisk ( \* ).**</span><span class="sxs-lookup"><span data-stu-id="1fc35-145">**Asterisk (\*).**</span></span> <span data-ttu-id="1fc35-146">Matchar noll eller flera tecken som börjar på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="1fc35-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="1fc35-147">**Öppna hak paren tes ([).**</span><span class="sxs-lookup"><span data-stu-id="1fc35-147">**Open bracket ([).**</span></span> <span data-ttu-id="1fc35-148">Introducerar ett mönster paren tes uttryck som kan innehålla tecken eller ett tecken intervall.</span><span class="sxs-lookup"><span data-stu-id="1fc35-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="1fc35-149">Om ett intervall krävs används ett bindestreck (-) för att ange intervallet.</span><span class="sxs-lookup"><span data-stu-id="1fc35-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="1fc35-150">**Avslutande hak paren tes (]).**</span><span class="sxs-lookup"><span data-stu-id="1fc35-150">**Close bracket (]).**</span></span> <span data-ttu-id="1fc35-151">Avslutar ett mönster paren tes uttryck.</span><span class="sxs-lookup"><span data-stu-id="1fc35-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="1fc35-152">**Escape-tecken för back citat (').**</span><span class="sxs-lookup"><span data-stu-id="1fc35-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="1fc35-153">Anger att nästa Character ska tas i bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="1fc35-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="1fc35-154">Tänk på att när du anger ett back citat tecken från kommando raden (i stället för att ange det program mässigt), måste Escape-tecknet för back-offerten anges två gånger.</span><span class="sxs-lookup"><span data-stu-id="1fc35-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="1fc35-155">Mer information om mönster för jokertecken finns i [stödjande jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1fc35-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="1fc35-156">Följande kod visar hur du ställer in jokertecken och definierar mönster för jokertecken som används för att matcha `Name` parametern för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1fc35-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="1fc35-157">Följande kod visar hur du testar om process namnet matchar det definierade jokertecken.</span><span class="sxs-lookup"><span data-stu-id="1fc35-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="1fc35-158">Observera att, i det här fallet, om process namnet inte matchar mönstret, fortsätter cmdleten på för att hämta nästa process namn.</span><span class="sxs-lookup"><span data-stu-id="1fc35-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="1fc35-159">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="1fc35-159">Code Sample</span></span>

<span data-ttu-id="1fc35-160">Den fullständiga exempel koden för C# finns i [StopProcessSample03-exempel](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="1fc35-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="1fc35-161">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="1fc35-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="1fc35-162">Windows PowerShell skickar information mellan cmdlets med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="1fc35-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="1fc35-163">Därför kan en cmdlet behöva definiera en egen typ, eller så kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1fc35-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="1fc35-164">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1fc35-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="1fc35-165">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="1fc35-165">Building the Cmdlet</span></span>

<span data-ttu-id="1fc35-166">När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="1fc35-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="1fc35-167">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="1fc35-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="1fc35-168">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="1fc35-168">Testing the Cmdlet</span></span>

<span data-ttu-id="1fc35-169">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1fc35-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="1fc35-170">Nu ska vi testa samplet Stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1fc35-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="1fc35-171">Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="1fc35-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="1fc35-172">Starta Windows PowerShell och använd Stop-PROC för att stoppa en process med ProcessName-aliaset för `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="1fc35-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    <span data-ttu-id="1fc35-173">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="1fc35-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="1fc35-174">Gör följande på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1fc35-174">Make the following entry on the command line.</span></span> <span data-ttu-id="1fc35-175">Eftersom namn parametern är obligatorisk uppmanas du att ange den.</span><span class="sxs-lookup"><span data-stu-id="1fc35-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="1fc35-176">Anger du "!?"</span><span class="sxs-lookup"><span data-stu-id="1fc35-176">Entering "!?"</span></span> <span data-ttu-id="1fc35-177">visar den hjälp text som är kopplad till parametern.</span><span class="sxs-lookup"><span data-stu-id="1fc35-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="1fc35-178">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="1fc35-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="1fc35-179">Gör nu följande post för att stoppa alla processer som matchar jokertecknet \* Obs! \* .</span><span class="sxs-lookup"><span data-stu-id="1fc35-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="1fc35-180">Du uppmanas att stoppa varje process som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="1fc35-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

    <span data-ttu-id="1fc35-181">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="1fc35-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    <span data-ttu-id="1fc35-182">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="1fc35-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    <span data-ttu-id="1fc35-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="1fc35-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="1fc35-184">Se även</span><span class="sxs-lookup"><span data-stu-id="1fc35-184">See Also</span></span>

[<span data-ttu-id="1fc35-185">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="1fc35-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="1fc35-186">Så här skapar du en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1fc35-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="1fc35-187">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1fc35-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="1fc35-188">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="1fc35-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="1fc35-189">Stöd för jokertecken i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="1fc35-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="1fc35-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1fc35-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
