---
title: Lägga till parametrar som bearbetar kommando rads indatatyper | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.openlocfilehash: 6ccc873d9c6b93546b3dae8c0d2e406763fdfb8a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784579"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="6335f-102">Lägga till parametrar som bearbetar kommandoradsindata</span><span class="sxs-lookup"><span data-stu-id="6335f-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="6335f-103">En källa för indatamängden för en cmdlet är kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6335f-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="6335f-104">I det här avsnittet beskrivs hur du lägger till en parameter till `Get-Proc` cmdleten (som beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta indata från den lokala datorn baserat på explicita objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-104">This topic describes how to add a parameter to the `Get-Proc` cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="6335f-105">Den `Get-Proc` cmdlet som beskrivs här hämtar processer baserat på deras namn och visar sedan information om processerna i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="6335f-105">The `Get-Proc` cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="6335f-106">Definiera cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="6335f-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="6335f-107">Det första steget i att skapa cmdleten är cmdlet-namn och deklarationen för den .NET Framework-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="6335f-108">Den här cmdleten hämtar process information, så verbet som väljs här är "Hämta".</span><span class="sxs-lookup"><span data-stu-id="6335f-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="6335f-109">(Nästan alla sorters cmdlets som kan hämta information kan bearbeta kommando rads indata.) Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="6335f-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="6335f-110">Här är klass deklarationen för `Get-Proc` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-110">Here's the class declaration for the `Get-Proc` cmdlet.</span></span> <span data-ttu-id="6335f-111">Information om den här definitionen finns i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6335f-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="6335f-112">Deklarera parametrar</span><span class="sxs-lookup"><span data-stu-id="6335f-112">Declaring Parameters</span></span>

<span data-ttu-id="6335f-113">En cmdlet-parameter gör att användaren kan ange indata till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="6335f-114">I följande exempel `Get-Proc` och `Get-Member` är namnen på de pipeliniska cmdletarna och `MemberType` är en parameter för `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-114">In the following example, `Get-Proc` and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="6335f-115">Parametern har argumentet "Property."</span><span class="sxs-lookup"><span data-stu-id="6335f-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="6335f-116">**PS> get-proc; `get-member` -MemberType-egenskap**</span><span class="sxs-lookup"><span data-stu-id="6335f-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="6335f-117">Om du vill deklarera parametrar för en cmdlet måste du först definiera de egenskaper som representerar parametrarna.</span><span class="sxs-lookup"><span data-stu-id="6335f-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="6335f-118">I `Get-Proc` -cmdleten är den enda parametern `Name` , som i det här fallet representerar namnet på det .NET Framework process objekt som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="6335f-118">In the `Get-Proc` cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="6335f-119">Därför definierar cmdlet-klassen en egenskap av typen sträng för att acceptera en namn mat ris.</span><span class="sxs-lookup"><span data-stu-id="6335f-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="6335f-120">Här är parameter deklarationen för `Name` parametern för `Get-Proc` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-120">Here's the parameter declaration for the `Name` parameter of the `Get-Proc` cmdlet.</span></span>

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<span data-ttu-id="6335f-121">För att informera Windows PowerShell-körningsmiljön om att den här egenskapen är `Name` parametern läggs ett attribut för [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) till i egenskaps definitionen.</span><span class="sxs-lookup"><span data-stu-id="6335f-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="6335f-122">Den grundläggande syntaxen för att deklarera det här attributet är `[Parameter()]` .</span><span class="sxs-lookup"><span data-stu-id="6335f-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="6335f-123">En parameter måste markeras som offentlig.</span><span class="sxs-lookup"><span data-stu-id="6335f-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="6335f-124">Parametrar som inte har marker ATS som offentliga som offentliga som standard som interna och inte hittas av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="6335f-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="6335f-125">Denna cmdlet använder en sträng mat ris för `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="6335f-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="6335f-126">Om möjligt bör cmdleten även definiera en parameter som en matris, eftersom detta tillåter att cmdleten accepterar mer än ett objekt.</span><span class="sxs-lookup"><span data-stu-id="6335f-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="6335f-127">Saker att komma ihåg om parameter definitioner</span><span class="sxs-lookup"><span data-stu-id="6335f-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="6335f-128">Fördefinierade parameter namn och data typer för Windows PowerShell bör återanvändas så mycket som möjligt för att säkerställa att din cmdlet är kompatibel med Windows PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="6335f-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="6335f-129">Om till exempel alla cmdlet: ar använder det fördefinierade `Id` parameter namnet för att identifiera en resurs, kommer användaren enkelt att förstå betydelsen av parametern, oavsett vilken cmdlet de använder.</span><span class="sxs-lookup"><span data-stu-id="6335f-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="6335f-130">Parameter namn följer i princip samma regler som används för variabel namn i Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6335f-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="6335f-131">Mer information om parameter namn finns i [cmdlet parameter Names](/previous-versions/ms714468(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="6335f-131">For more information about parameter naming, see [Cmdlet Parameter Names](/previous-versions/ms714468(v=vs.85)).</span></span>

- <span data-ttu-id="6335f-132">Windows PowerShell reserverar några parameter namn för att ge en konsekvent användar upplevelse.</span><span class="sxs-lookup"><span data-stu-id="6335f-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="6335f-133">Använd inte följande parameter namn:,,,,,, `WhatIf` `Confirm` `Verbose` `Debug` `Warn` `ErrorAction` `ErrorVariable` `OutVariable` , och `OutBuffer` .</span><span class="sxs-lookup"><span data-stu-id="6335f-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="6335f-134">Dessutom är följande alias för dessa parameter namn reserverade:,,, `vb` , `db` `ea` `ev` `ov` och `ob` .</span><span class="sxs-lookup"><span data-stu-id="6335f-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="6335f-135">`Name` är ett enkelt och vanligt parameter namn som rekommenderas för användning i dina cmdletar.</span><span class="sxs-lookup"><span data-stu-id="6335f-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="6335f-136">Det är bättre att välja ett parameter namn som detta än ett komplext namn som är unikt för en speciell cmdlet och svårt att komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="6335f-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="6335f-137">Parametrar är Skift läges känsliga i Windows PowerShell, men som standard bevarar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6335f-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="6335f-138">Skift läges känslighet för argumenten beror på driften av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="6335f-139">Argument skickas till en parameter som anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6335f-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="6335f-140">Exempel på andra parameter deklarationer finns i [cmdlet-parametrar](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6335f-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="6335f-141">Deklarera parametrar som positions-eller namngivna</span><span class="sxs-lookup"><span data-stu-id="6335f-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="6335f-142">En cmdlet måste ange varje parameter som antingen en positions-eller namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="6335f-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="6335f-143">Båda typerna av parametrar accepterar enstaka argument, flera argument avgränsade med kommatecken och booleska inställningar.</span><span class="sxs-lookup"><span data-stu-id="6335f-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="6335f-144">En boolesk parameter, som även kallas för en *växel*, hanterar endast booleska inställningar.</span><span class="sxs-lookup"><span data-stu-id="6335f-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="6335f-145">Växeln används för att bestämma förekomst av parametern.</span><span class="sxs-lookup"><span data-stu-id="6335f-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="6335f-146">Det rekommenderade standardvärdet är `false` .</span><span class="sxs-lookup"><span data-stu-id="6335f-146">The recommended default is `false`.</span></span>

<span data-ttu-id="6335f-147">Exempel- `Get-Proc` cmdleten definierar `Name` parametern som en positions parameter med position</span><span class="sxs-lookup"><span data-stu-id="6335f-147">The sample `Get-Proc` cmdlet defines the `Name` parameter as a positional parameter with position</span></span>
0. <span data-ttu-id="6335f-148">Det innebär att det första argumentet som användaren anger på kommando raden automatiskt infogas för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="6335f-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="6335f-149">Om du vill definiera en namngiven parameter för vilken användaren måste ange parameter namnet från kommando raden lämnar du `Position` nyckelordet utanför deklarationen för attributet.</span><span class="sxs-lookup"><span data-stu-id="6335f-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="6335f-150">Om parametrar måste namnges, rekommenderar vi att du använder de mest använda parametrarna så att användarna inte behöver ange parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="6335f-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="6335f-151">Deklarera parametrar som obligatoriska eller valfria</span><span class="sxs-lookup"><span data-stu-id="6335f-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="6335f-152">En cmdlet måste ange varje parameter som antingen en valfri eller en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="6335f-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="6335f-153">I exempel `Get-Proc` -cmdleten `Name` definieras parametern som valfri eftersom `Mandatory` nyckelordet inte har angetts i deklarationen för attributet.</span><span class="sxs-lookup"><span data-stu-id="6335f-153">In the sample `Get-Proc` cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="6335f-154">Stöd för parameter validering</span><span class="sxs-lookup"><span data-stu-id="6335f-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="6335f-155">Exempel- `Get-Proc` cmdleten lägger till ett verifierings-attribut, [system. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), till `Name` parametern för att aktivera verifiering av att inaktuella inaktuella inaktuella `null` eller inte är tomma.</span><span class="sxs-lookup"><span data-stu-id="6335f-155">The sample `Get-Proc` cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="6335f-156">Det här attributet är ett av flera verifierings attribut från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6335f-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="6335f-157">Exempel på andra verifierings attribut finns i [Verifiera parameter Indatatyp](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="6335f-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="6335f-158">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="6335f-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="6335f-159">Om cmdleten ska hantera kommando rads indata måste den åsidosätta lämpliga metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="6335f-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="6335f-160">De grundläggande metoderna för indata-bearbetning införs när [du skapar din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6335f-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="6335f-161">Cmdlet: en `Get-Proc` åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att hantera `Name` parameter indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="6335f-161">The `Get-Proc` cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="6335f-162">Den här metoden hämtar processerna för varje begärt process namn, eller alla för-processer om inget namn har angetts.</span><span class="sxs-lookup"><span data-stu-id="6335f-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="6335f-163">Observera att i [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [system. Management. Automation. cmdlet. WriteObject% 28System. Object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) är utmatnings mekanismen för att skicka utgående objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6335f-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="6335f-164">Den andra parametern för det här anropet, `enumerateCollection` , är inställd på `true` att informera Windows PowerShell-körningsmiljön om att räkna upp utdata-matrisen för process objekt och skriva en process i taget till kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6335f-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="6335f-165">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="6335f-165">Code Sample</span></span>

<span data-ttu-id="6335f-166">Den fullständiga exempel koden för C# finns i [GetProcessSample02-exempel](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6335f-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="6335f-167">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="6335f-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="6335f-168">Windows PowerShell skickar information mellan cmdletar med hjälp av .NET Framework objekt.</span><span class="sxs-lookup"><span data-stu-id="6335f-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="6335f-169">Därför kan en cmdlet behöva definiera en egen typ, eller så kan en cmdlet behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6335f-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="6335f-170">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="6335f-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="6335f-171">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="6335f-171">Building the Cmdlet</span></span>

<span data-ttu-id="6335f-172">När du har implementerat en cmdlet måste du registrera den med Windows PowerShell med hjälp av en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="6335f-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="6335f-173">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="6335f-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="6335f-174">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="6335f-174">Testing the Cmdlet</span></span>

<span data-ttu-id="6335f-175">När cmdleten har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6335f-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="6335f-176">Här följer två sätt att testa koden för exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6335f-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="6335f-177">Mer information om hur du använder cmdlets från kommando raden finns [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="6335f-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="6335f-178">Använd följande kommando i Windows PowerShell-prompten för att visa en lista över Internet Explorer-processen, som heter "iexplore".</span><span class="sxs-lookup"><span data-stu-id="6335f-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

  ```powershell
  get-proc -name iexplore
  ```

  <span data-ttu-id="6335f-179">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="6335f-179">The following output appears.</span></span>

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- <span data-ttu-id="6335f-180">Om du vill visa en lista över Internet Explorer-, Outlook-och anteckningar-processer med namnet "iexplore", "OUTLOOK" och "NOTEPAD" använder du följande kommando.</span><span class="sxs-lookup"><span data-stu-id="6335f-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="6335f-181">Om det finns flera processer visas alla.</span><span class="sxs-lookup"><span data-stu-id="6335f-181">If there are multiple processes, all of them are displayed.</span></span>

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  <span data-ttu-id="6335f-182">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="6335f-182">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a><span data-ttu-id="6335f-183">Se även</span><span class="sxs-lookup"><span data-stu-id="6335f-183">See Also</span></span>

[<span data-ttu-id="6335f-184">Lägga till parametrar som bearbetar pipelineindata</span><span class="sxs-lookup"><span data-stu-id="6335f-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="6335f-185">Skapa din första cmdlet</span><span class="sxs-lookup"><span data-stu-id="6335f-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="6335f-186">[Utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6335f-186">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="6335f-187">[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6335f-187">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="6335f-188">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="6335f-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="6335f-189">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="6335f-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
