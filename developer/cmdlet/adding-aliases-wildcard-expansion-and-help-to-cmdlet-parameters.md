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
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075264"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="453f7-102">Lägga till alias, jokerteckenexpansion och hjälp i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="453f7-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="453f7-103">Det här avsnittet beskrivs hur du lägger till alias och jokertecken expansion och hjälp med att meddelanden till parametrarna för cmdleten Stop-processen (beskrivs i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="453f7-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="453f7-104">Denna cmdlet Stop-Proc försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="453f7-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="453f7-105">Ämnena i det här avsnittet omfattar följande:</span><span class="sxs-lookup"><span data-stu-id="453f7-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="453f7-106">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="453f7-106">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="453f7-107">Definiera parametrar för ändring av systemet</span><span class="sxs-lookup"><span data-stu-id="453f7-107">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="453f7-108">Definiera ett Parameteralias</span><span class="sxs-lookup"><span data-stu-id="453f7-108">Defining a Parameter Alias</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="453f7-109">Skapa hjälp för parametrar</span><span class="sxs-lookup"><span data-stu-id="453f7-109">Creating Help for Parameters</span></span>](#Creating-Help-for-Parameters)

- [<span data-ttu-id="453f7-110">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="453f7-110">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="453f7-111">Stöd för jokertecken Expansion</span><span class="sxs-lookup"><span data-stu-id="453f7-111">Supporting Wildcard Expansion</span></span>](#Supporting-Wildcard-Expansion)

- [<span data-ttu-id="453f7-112">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="453f7-112">Code Sample</span></span>](#Defining-a-Parameter-Alias)

- [<span data-ttu-id="453f7-113">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="453f7-113">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="453f7-114">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="453f7-114">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="453f7-115">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="453f7-115">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="453f7-116">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="453f7-116">Defining the Cmdlet</span></span>

<span data-ttu-id="453f7-117">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="453f7-117">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="453f7-118">Eftersom du skriver en cmdlet om du vill ändra systemet bör den vara namn därefter.</span><span class="sxs-lookup"><span data-stu-id="453f7-118">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="453f7-119">Eftersom denna cmdlet stoppas systemprocesser används verb ”stoppa”, som definieras av den [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klassen, substantiv ”Proc” för att indikera processen.</span><span class="sxs-lookup"><span data-stu-id="453f7-119">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="453f7-120">Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="453f7-120">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="453f7-121">Följande kod är klassdefinitionen för denna cmdlet Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="453f7-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="453f7-122">Definiera parametrar för ändring av systemet</span><span class="sxs-lookup"><span data-stu-id="453f7-122">Defining Parameters for System Modification</span></span>

<span data-ttu-id="453f7-123">Din cmdlet måste definiera parametrar som supportsystem ändringar och användarfeedback.</span><span class="sxs-lookup"><span data-stu-id="453f7-123">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="453f7-124">Cmdlet: en ska definiera en `Name` parametern eller motsvarande så att cmdleten kommer att kunna ändra systemet med någon typ av identifierare.</span><span class="sxs-lookup"><span data-stu-id="453f7-124">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="453f7-125">Dessutom kan cmdleten bör definiera den `Force` och `PassThru` parametrar.</span><span class="sxs-lookup"><span data-stu-id="453f7-125">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="453f7-126">Mer information om dessa parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="453f7-126">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="453f7-127">Definiera ett Parameteralias</span><span class="sxs-lookup"><span data-stu-id="453f7-127">Defining a Parameter Alias</span></span>

<span data-ttu-id="453f7-128">Ett parameteralias kan vara ett alternativt namn eller ett väldefinierade 1 bokstav eller en 2-bokstav kort namn för en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="453f7-128">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="453f7-129">I båda fallen är avsikten att använda alias att förenkla användarpost från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="453f7-129">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="453f7-130">Windows PowerShell har stöd för parameteralias via den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, som använder deklarationssyntax [Alias()].</span><span class="sxs-lookup"><span data-stu-id="453f7-130">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="453f7-131">Följande kod visar hur ett alias har lagts till i den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="453f7-131">The following code shows how an alias is added to the `Name` parameter.</span></span>

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

<span data-ttu-id="453f7-132">Förutom att använda den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, Windows PowerShell körningen utför partiella namnmatchning, även om inga alias anges.</span><span class="sxs-lookup"><span data-stu-id="453f7-132">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="453f7-133">Om din cmdlet har till exempel en `FileName` parametern och det är den enda parameter som börjar med `F`, användaren kan ange `Filename`, `Filenam`, `File`, `Fi`, eller `F` och fortfarande identifiera den posten som den `FileName` parametern.</span><span class="sxs-lookup"><span data-stu-id="453f7-133">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="453f7-134">Skapa hjälp för parametrar</span><span class="sxs-lookup"><span data-stu-id="453f7-134">Creating Help for Parameters</span></span>

<span data-ttu-id="453f7-135">Windows PowerShell kan du skapa hjälpen för cmdlet-parametrarna.</span><span class="sxs-lookup"><span data-stu-id="453f7-135">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="453f7-136">Du kan göra detta för valfri parameter som används för system ändring och användarfeedback.</span><span class="sxs-lookup"><span data-stu-id="453f7-136">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="453f7-137">För varje parameter för hjälp med att du kan ange den `HelpMessage` attributet nyckelord i den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet deklaration.</span><span class="sxs-lookup"><span data-stu-id="453f7-137">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="453f7-138">Det här nyckelordet definierar vilken text som ska visas för användaren om du behöver hjälp med hjälp av parametern.</span><span class="sxs-lookup"><span data-stu-id="453f7-138">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="453f7-139">Du kan också ange den `HelpMessageBaseName` nyckelord att identifiera det grundläggande namnet på en resurs som ska användas för meddelandet.</span><span class="sxs-lookup"><span data-stu-id="453f7-139">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="453f7-140">Om du ställer in det här nyckelordet måste du också ange den `HelpMessageResourceId` nyckelord att ange resursidentifieraren.</span><span class="sxs-lookup"><span data-stu-id="453f7-140">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="453f7-141">Följande kod från denna cmdlet Stop-Proc definierar den `HelpMessage` attributet nyckelord för den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="453f7-141">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="453f7-142">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="453f7-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="453f7-143">Cmdlet: måste åsidosätta indata metoden bearbetades, oftast det här är [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="453f7-143">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="453f7-144">När du ändrar systemet cmdleten ska anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder för att tillåta användaren vill ge feedback innan en ändring görs.</span><span class="sxs-lookup"><span data-stu-id="453f7-144">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="453f7-145">Läs mer om de här metoderna [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="453f7-145">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="453f7-146">Stöd för jokertecken Expansion</span><span class="sxs-lookup"><span data-stu-id="453f7-146">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="453f7-147">Cmdlet: kan använda för att tillåta val av flera objekt, den [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) och [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klasser för att tillhandahålla stöd för jokertecken expansion för parametern som indata.</span><span class="sxs-lookup"><span data-stu-id="453f7-147">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="453f7-148">Exempel på jokerteckensmönster är lsa \* \*.txt och [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="453f7-148">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="453f7-149">Använd tillbaka citattecken (') som escape-tecken när mönstret innehåller ett tecken som ska användas bokstavligt.</span><span class="sxs-lookup"><span data-stu-id="453f7-149">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="453f7-150">Jokertecken expansion av fil-och sökvägen är exempel på vanliga scenarier där cmdleten kanske vill tillåta stöd för sökvägen indata när valet av flera objekt krävs.</span><span class="sxs-lookup"><span data-stu-id="453f7-150">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="453f7-151">Det är vanligt i filsystem, där en användare vill se alla filer som finns i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="453f7-151">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="453f7-152">Du behöver en anpassad jokertecken mönstret matchande implementering bara sällan.</span><span class="sxs-lookup"><span data-stu-id="453f7-152">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="453f7-153">I så fall cmdlet: ska ha stöd för fullständig POSIX-1003.2, 3,13 specifikation för jokertecken expansion eller följande förenklad delmängden:</span><span class="sxs-lookup"><span data-stu-id="453f7-153">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="453f7-154">**Frågetecken (?).**</span><span class="sxs-lookup"><span data-stu-id="453f7-154">**Question mark (?).**</span></span> <span data-ttu-id="453f7-155">Matchar alla tecken på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="453f7-155">Matches any character at the specified location.</span></span>

- <span data-ttu-id="453f7-156">**Asterisk (\*).**</span><span class="sxs-lookup"><span data-stu-id="453f7-156">**Asterisk (\*).**</span></span> <span data-ttu-id="453f7-157">Matchar noll eller flera tecken med början vid den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="453f7-157">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="453f7-158">**Öppna hakparentes ().**</span><span class="sxs-lookup"><span data-stu-id="453f7-158">**Open bracket ([).**</span></span> <span data-ttu-id="453f7-159">Introducerar ett mönster hakparentes uttryck som kan innehålla tecken eller ett teckenintervall.</span><span class="sxs-lookup"><span data-stu-id="453f7-159">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="453f7-160">Om ett intervall krävs, används ett bindestreck (-) som anger intervallet.</span><span class="sxs-lookup"><span data-stu-id="453f7-160">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="453f7-161">**Stäng hakparentes (]).**</span><span class="sxs-lookup"><span data-stu-id="453f7-161">**Close bracket (]).**</span></span> <span data-ttu-id="453f7-162">Slutar ett mönster hakparentes uttryck.</span><span class="sxs-lookup"><span data-stu-id="453f7-162">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="453f7-163">**Tillbaka-offert escape-tecknet (').**</span><span class="sxs-lookup"><span data-stu-id="453f7-163">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="453f7-164">Anger att nästa tecken ska att tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="453f7-164">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="453f7-165">Tänk på att när du anger tillbaka till citattecken från kommandoraden (i stället för att ange den programmässigt) tillbaka-offert escape-tecken måste anges två gånger.</span><span class="sxs-lookup"><span data-stu-id="453f7-165">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="453f7-166">Läs mer om jokerteckensmönstren [stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="453f7-166">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="453f7-167">Följande kod visar hur du ställer in alternativ för jokertecken och definierar jokerteckensmönster som används för att lösa den `Name` parametern för denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="453f7-167">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="453f7-168">Följande kod visar hur du testar om processens namn matchar mönstret definierade jokertecken.</span><span class="sxs-lookup"><span data-stu-id="453f7-168">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="453f7-169">Observera att, i det här fallet om processens namn inte matchar mönstret, cmdleten fortfarande på att hämta nästa processnamn.</span><span class="sxs-lookup"><span data-stu-id="453f7-169">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="453f7-170">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="453f7-170">Code Sample</span></span>

<span data-ttu-id="453f7-171">För hela C# exempelkoden, se [StopProcessSample03 exempel](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="453f7-171">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="453f7-172">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="453f7-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="453f7-173">Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="453f7-173">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="453f7-174">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="453f7-174">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="453f7-175">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="453f7-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="453f7-176">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="453f7-176">Building the Cmdlet</span></span>

<span data-ttu-id="453f7-177">När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="453f7-177">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="453f7-178">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="453f7-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="453f7-179">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="453f7-179">Testing the Cmdlet</span></span>

<span data-ttu-id="453f7-180">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="453f7-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="453f7-181">Nu ska vi testa exempel Stop-Proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="453f7-181">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="453f7-182">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="453f7-182">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="453f7-183">Starta Windows PowerShell och Använd Stop-processen för att stoppa en process som använder ProcessName alias för den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="453f7-183">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="453f7-184">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="453f7-184">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="453f7-185">Se följande post från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="453f7-185">Make the following entry on the command line.</span></span> <span data-ttu-id="453f7-186">Eftersom Name-parametern är obligatorisk, uppmanas du för den.</span><span class="sxs-lookup"><span data-stu-id="453f7-186">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="453f7-187">Ange ”!”?</span><span class="sxs-lookup"><span data-stu-id="453f7-187">Entering "!?"</span></span> <span data-ttu-id="453f7-188">öppnar hjälptexten som är associerade med parametern.</span><span class="sxs-lookup"><span data-stu-id="453f7-188">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="453f7-189">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="453f7-189">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="453f7-190">Nu göra följande post att stoppa alla processer som matchar mönstret jokertecknet ”\* Obs\*”.</span><span class="sxs-lookup"><span data-stu-id="453f7-190">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="453f7-191">Du uppmanas innan du stoppar varje process som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="453f7-191">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="453f7-192">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="453f7-192">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="453f7-193">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="453f7-193">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="453f7-194">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="453f7-194">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="453f7-195">Se även</span><span class="sxs-lookup"><span data-stu-id="453f7-195">See Also</span></span>

[<span data-ttu-id="453f7-196">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="453f7-196">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="453f7-197">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="453f7-197">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="453f7-198">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="453f7-198">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="453f7-199">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="453f7-199">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="453f7-200">Stöd för jokertecken i Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="453f7-200">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="453f7-201">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="453f7-201">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
