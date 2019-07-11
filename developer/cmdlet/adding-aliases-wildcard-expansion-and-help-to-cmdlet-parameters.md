---
title: Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733843"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="0caeb-102">Lägga till alias, jokerteckenexpansion och hjälp i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="0caeb-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="0caeb-103">Det här avsnittet beskrivs hur du lägger till alias och jokertecken expansion och hjälp med att meddelanden till parametrarna för cmdleten Stop-processen (beskrivs i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="0caeb-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="0caeb-104">Denna cmdlet Stop-Proc försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="0caeb-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="0caeb-105">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="0caeb-105">Defining the Cmdlet</span></span>

<span data-ttu-id="0caeb-106">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="0caeb-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="0caeb-107">Eftersom du skriver en cmdlet om du vill ändra systemet bör den vara namn därefter.</span><span class="sxs-lookup"><span data-stu-id="0caeb-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="0caeb-108">Eftersom denna cmdlet stoppas systemprocesser används verb ”stoppa”, som definieras av den [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klassen, substantiv ”Proc” för att indikera processen.</span><span class="sxs-lookup"><span data-stu-id="0caeb-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="0caeb-109">Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0caeb-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="0caeb-110">Följande kod är klassdefinitionen för denna cmdlet Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="0caeb-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="0caeb-111">Definiera parametrar för ändring av systemet</span><span class="sxs-lookup"><span data-stu-id="0caeb-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="0caeb-112">Din cmdlet måste definiera parametrar som supportsystem ändringar och användarfeedback.</span><span class="sxs-lookup"><span data-stu-id="0caeb-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="0caeb-113">Cmdlet: en ska definiera en `Name` parametern eller motsvarande så att cmdleten kommer att kunna ändra systemet med någon typ av identifierare.</span><span class="sxs-lookup"><span data-stu-id="0caeb-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="0caeb-114">Dessutom kan cmdleten bör definiera den `Force` och `PassThru` parametrar.</span><span class="sxs-lookup"><span data-stu-id="0caeb-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="0caeb-115">Mer information om dessa parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="0caeb-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="0caeb-116">Definiera ett Parameteralias</span><span class="sxs-lookup"><span data-stu-id="0caeb-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="0caeb-117">Ett parameteralias kan vara ett alternativt namn eller ett väldefinierade 1 bokstav eller en 2-bokstav kort namn för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="0caeb-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="0caeb-118">I båda fallen är avsikten att använda alias att förenkla användarpost från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="0caeb-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="0caeb-119">Windows PowerShell har stöd för parameteralias via den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, som använder deklarationssyntax [Alias()].</span><span class="sxs-lookup"><span data-stu-id="0caeb-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="0caeb-120">Följande kod visar hur ett alias har lagts till i den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="0caeb-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="0caeb-121">Förutom att använda den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, Windows PowerShell körningen utför partiella namnmatchning, även om inga alias anges.</span><span class="sxs-lookup"><span data-stu-id="0caeb-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="0caeb-122">Om din cmdlet har till exempel en `FileName` parametern och det är den enda parameter som börjar med `F`, användaren kan ange `Filename`, `Filenam`, `File`, `Fi`, eller `F` och fortfarande identifiera den posten som den `FileName` parametern.</span><span class="sxs-lookup"><span data-stu-id="0caeb-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="0caeb-123">Skapa hjälp för parametrar</span><span class="sxs-lookup"><span data-stu-id="0caeb-123">Creating Help for Parameters</span></span>

<span data-ttu-id="0caeb-124">Windows PowerShell kan du skapa hjälpen för cmdlet-parametrarna.</span><span class="sxs-lookup"><span data-stu-id="0caeb-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="0caeb-125">Du kan göra detta för valfri parameter som används för system ändring och användarfeedback.</span><span class="sxs-lookup"><span data-stu-id="0caeb-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="0caeb-126">För varje parameter för hjälp med att du kan ange den `HelpMessage` attributet nyckelord i den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet deklaration.</span><span class="sxs-lookup"><span data-stu-id="0caeb-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="0caeb-127">Det här nyckelordet definierar vilken text som ska visas för användaren om du behöver hjälp med hjälp av parametern.</span><span class="sxs-lookup"><span data-stu-id="0caeb-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="0caeb-128">Du kan också ange den `HelpMessageBaseName` nyckelord att identifiera det grundläggande namnet på en resurs som ska användas för meddelandet.</span><span class="sxs-lookup"><span data-stu-id="0caeb-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="0caeb-129">Om du ställer in det här nyckelordet måste du också ange den `HelpMessageResourceId` nyckelord att ange resursidentifieraren.</span><span class="sxs-lookup"><span data-stu-id="0caeb-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="0caeb-130">Följande kod från denna cmdlet Stop-Proc definierar den `HelpMessage` attributet nyckelord för den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="0caeb-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="0caeb-131">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="0caeb-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="0caeb-132">Cmdlet: måste åsidosätta indata metoden bearbetades, oftast det här är [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="0caeb-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="0caeb-133">När du ändrar systemet cmdleten ska anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder för att tillåta användaren vill ge feedback innan en ändring görs.</span><span class="sxs-lookup"><span data-stu-id="0caeb-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="0caeb-134">Läs mer om de här metoderna [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="0caeb-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="0caeb-135">Stöd för jokertecken Expansion</span><span class="sxs-lookup"><span data-stu-id="0caeb-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="0caeb-136">Cmdlet: kan använda för att tillåta val av flera objekt, den [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) och [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klasser för att tillhandahålla stöd för jokertecken expansion för parametern som indata.</span><span class="sxs-lookup"><span data-stu-id="0caeb-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="0caeb-137">Exempel på jokerteckensmönster är lsa \* \*.txt och [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="0caeb-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="0caeb-138">Använd tillbaka citattecken (') som escape-tecken när mönstret innehåller ett tecken som ska användas bokstavligt.</span><span class="sxs-lookup"><span data-stu-id="0caeb-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="0caeb-139">Jokertecken expansion av fil-och sökvägen är exempel på vanliga scenarier där cmdleten kanske vill tillåta stöd för sökvägen indata när valet av flera objekt krävs.</span><span class="sxs-lookup"><span data-stu-id="0caeb-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="0caeb-140">Det är vanligt i filsystem, där en användare vill se alla filer som finns i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="0caeb-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="0caeb-141">Du behöver en anpassad jokertecken mönstret matchande implementering bara sällan.</span><span class="sxs-lookup"><span data-stu-id="0caeb-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="0caeb-142">I så fall cmdlet: ska ha stöd för fullständig POSIX-1003.2, 3,13 specifikation för jokertecken expansion eller följande förenklad delmängden:</span><span class="sxs-lookup"><span data-stu-id="0caeb-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="0caeb-143">**Frågetecken (?).**</span><span class="sxs-lookup"><span data-stu-id="0caeb-143">**Question mark (?).**</span></span> <span data-ttu-id="0caeb-144">Matchar alla tecken på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="0caeb-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="0caeb-145">**Asterisk (\*).**</span><span class="sxs-lookup"><span data-stu-id="0caeb-145">**Asterisk (\*).**</span></span> <span data-ttu-id="0caeb-146">Matchar noll eller flera tecken med början vid den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="0caeb-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="0caeb-147">**Öppna hakparentes ().**</span><span class="sxs-lookup"><span data-stu-id="0caeb-147">**Open bracket ([).**</span></span> <span data-ttu-id="0caeb-148">Introducerar ett mönster hakparentes uttryck som kan innehålla tecken eller ett teckenintervall.</span><span class="sxs-lookup"><span data-stu-id="0caeb-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="0caeb-149">Om ett intervall krävs, används ett bindestreck (-) som anger intervallet.</span><span class="sxs-lookup"><span data-stu-id="0caeb-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="0caeb-150">**Stäng hakparentes (]).**</span><span class="sxs-lookup"><span data-stu-id="0caeb-150">**Close bracket (]).**</span></span> <span data-ttu-id="0caeb-151">Slutar ett mönster hakparentes uttryck.</span><span class="sxs-lookup"><span data-stu-id="0caeb-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="0caeb-152">**Tillbaka-offert escape-tecknet (').**</span><span class="sxs-lookup"><span data-stu-id="0caeb-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="0caeb-153">Anger att nästa tecken ska att tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="0caeb-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="0caeb-154">Tänk på att när du anger tillbaka till citattecken från kommandoraden (i stället för att ange den programmässigt) tillbaka-offert escape-tecken måste anges två gånger.</span><span class="sxs-lookup"><span data-stu-id="0caeb-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="0caeb-155">Läs mer om jokerteckensmönstren [stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0caeb-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="0caeb-156">Följande kod visar hur du ställer in alternativ för jokertecken och definierar jokerteckensmönster som används för att lösa den `Name` parametern för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0caeb-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="0caeb-157">Följande kod visar hur du testar om processens namn matchar mönstret definierade jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0caeb-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="0caeb-158">Observera att, i det här fallet om processens namn inte matchar mönstret, cmdleten fortfarande på att hämta nästa processnamn.</span><span class="sxs-lookup"><span data-stu-id="0caeb-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="0caeb-159">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="0caeb-159">Code Sample</span></span>

<span data-ttu-id="0caeb-160">För hela C# exempelkoden, se [StopProcessSample03 exempel](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0caeb-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="0caeb-161">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="0caeb-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="0caeb-162">Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="0caeb-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="0caeb-163">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0caeb-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="0caeb-164">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0caeb-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="0caeb-165">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="0caeb-165">Building the Cmdlet</span></span>

<span data-ttu-id="0caeb-166">När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="0caeb-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="0caeb-167">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0caeb-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="0caeb-168">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="0caeb-168">Testing the Cmdlet</span></span>

<span data-ttu-id="0caeb-169">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="0caeb-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="0caeb-170">Nu ska vi testa exempel Stop-Proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0caeb-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="0caeb-171">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="0caeb-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="0caeb-172">Starta Windows PowerShell och Använd Stop-processen för att stoppa en process som använder ProcessName alias för den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="0caeb-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="0caeb-173">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="0caeb-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="0caeb-174">Se följande post från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="0caeb-174">Make the following entry on the command line.</span></span> <span data-ttu-id="0caeb-175">Eftersom Name-parametern är obligatorisk, uppmanas du för den.</span><span class="sxs-lookup"><span data-stu-id="0caeb-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="0caeb-176">Ange ”!”?</span><span class="sxs-lookup"><span data-stu-id="0caeb-176">Entering "!?"</span></span> <span data-ttu-id="0caeb-177">öppnar hjälptexten som är associerade med parametern.</span><span class="sxs-lookup"><span data-stu-id="0caeb-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="0caeb-178">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="0caeb-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="0caeb-179">Nu göra följande post att stoppa alla processer som matchar mönstret jokertecknet ”\* Obs\*”.</span><span class="sxs-lookup"><span data-stu-id="0caeb-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="0caeb-180">Du uppmanas innan du stoppar varje process som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="0caeb-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="0caeb-181">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="0caeb-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="0caeb-182">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="0caeb-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="0caeb-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="0caeb-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="0caeb-184">Se även</span><span class="sxs-lookup"><span data-stu-id="0caeb-184">See Also</span></span>

[<span data-ttu-id="0caeb-185">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="0caeb-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="0caeb-186">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0caeb-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="0caeb-187">[Utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0caeb-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="0caeb-188">[Hur du registrerar Cmdlets, Providers och vara värd för program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0caeb-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="0caeb-189">Stöd för jokertecken i Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="0caeb-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="0caeb-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0caeb-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
