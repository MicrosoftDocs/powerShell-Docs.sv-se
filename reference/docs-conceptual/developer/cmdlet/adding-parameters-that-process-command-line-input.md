---
title: Lägga till parametrar som bearbetar kommando rads indatatyper | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355666"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="ef1de-102">Lägga till parametrar som bearbetar kommandoradsindata</span><span class="sxs-lookup"><span data-stu-id="ef1de-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="ef1de-103">En källa för indatamängden för en cmdlet är kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ef1de-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="ef1de-104">I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten **Get-proc** (som beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta indata från den lokala datorn baserat på explicita objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="ef1de-105">Cmdleten **Get-proc** som beskrivs här hämtar processer baserat på deras namn och visar sedan information om processerna i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="ef1de-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="ef1de-106">Definiera cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="ef1de-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="ef1de-107">Det första steget i att skapa cmdleten är cmdlet-namn och deklarationen för den .NET Framework-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="ef1de-108">Den här cmdleten hämtar process information, så verbet som väljs här är "Hämta".</span><span class="sxs-lookup"><span data-stu-id="ef1de-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="ef1de-109">(Nästan alla sorters cmdlets som kan hämta information kan bearbeta kommando rads indata.) Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ef1de-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ef1de-110">Här är klass deklarationen för **Get-proc-** cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="ef1de-111">Information om den här definitionen finns i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ef1de-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="ef1de-112">Deklarera parametrar</span><span class="sxs-lookup"><span data-stu-id="ef1de-112">Declaring Parameters</span></span>

<span data-ttu-id="ef1de-113">En cmdlet-parameter gör att användaren kan ange indata till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="ef1de-114">I följande exempel är **Get-proc** och `Get-Member` namnen på de pipeliniska cmdletarna och `MemberType` är en parameter för `Get-Member`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="ef1de-115">Parametern har argumentet "Property."</span><span class="sxs-lookup"><span data-stu-id="ef1de-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="ef1de-116">**PS > Get-proc; `get-member`-MemberType-egenskap**</span><span class="sxs-lookup"><span data-stu-id="ef1de-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="ef1de-117">Om du vill deklarera parametrar för en cmdlet måste du först definiera de egenskaper som representerar parametrarna.</span><span class="sxs-lookup"><span data-stu-id="ef1de-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="ef1de-118">I cmdleten **Get-proc** är den enda parametern `Name`, som i det här fallet representerar namnet på det .NET Framework processobjektet som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="ef1de-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="ef1de-119">Därför definierar cmdlet-klassen en egenskap av typen sträng för att acceptera en namn mat ris.</span><span class="sxs-lookup"><span data-stu-id="ef1de-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="ef1de-120">Här är parameter deklarationen för parametern `Name` för cmdleten **Get-proc** .</span><span class="sxs-lookup"><span data-stu-id="ef1de-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="ef1de-121">För att informera Windows PowerShell-körningsmiljön att den här egenskapen är parametern `Name`, läggs attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) till i egenskaps definitionen.</span><span class="sxs-lookup"><span data-stu-id="ef1de-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="ef1de-122">Den grundläggande syntaxen för att deklarera det här attributet är `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="ef1de-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="ef1de-123">En parameter måste markeras som offentlig.</span><span class="sxs-lookup"><span data-stu-id="ef1de-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="ef1de-124">Parametrar som inte har marker ATS som offentliga som offentliga som standard som interna och inte hittas av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="ef1de-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="ef1de-125">Denna cmdlet använder en sträng mat ris för parametern `Name`.</span><span class="sxs-lookup"><span data-stu-id="ef1de-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="ef1de-126">Om möjligt bör cmdleten även definiera en parameter som en matris, eftersom detta tillåter att cmdleten accepterar mer än ett objekt.</span><span class="sxs-lookup"><span data-stu-id="ef1de-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="ef1de-127">Saker att komma ihåg om parameter definitioner</span><span class="sxs-lookup"><span data-stu-id="ef1de-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="ef1de-128">Fördefinierade parameter namn och data typer för Windows PowerShell bör återanvändas så mycket som möjligt för att säkerställa att din cmdlet är kompatibel med Windows PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ef1de-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="ef1de-129">Om till exempel alla cmdlet: ar använder fördefinierade `Id`-parameter namn för att identifiera en resurs, kommer användaren enkelt att förstå betydelsen av parametern, oavsett vilken cmdlet de använder.</span><span class="sxs-lookup"><span data-stu-id="ef1de-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="ef1de-130">Parameter namn följer i princip samma regler som används för variabel namn i Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ef1de-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="ef1de-131">Mer information om parameter namn finns i [cmdlet parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="ef1de-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="ef1de-132">Windows PowerShell reserverar några parameter namn för att ge en konsekvent användar upplevelse.</span><span class="sxs-lookup"><span data-stu-id="ef1de-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="ef1de-133">Använd inte följande parameter namn: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable` och `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="ef1de-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="ef1de-134">Dessutom är följande alias för dessa parameter namn reserverade: `vb`, `db`, `ea`, `ev`, `ov` och `ob`.</span><span class="sxs-lookup"><span data-stu-id="ef1de-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="ef1de-135">`Name` är ett enkelt och vanligt parameter namn som rekommenderas för användning i dina cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ef1de-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="ef1de-136">Det är bättre att välja ett parameter namn som detta än ett komplext namn som är unikt för en speciell cmdlet och svårt att komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="ef1de-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="ef1de-137">Parametrar är Skift läges känsliga i Windows PowerShell, men som standard bevarar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ef1de-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="ef1de-138">Skift läges känslighet för argumenten beror på driften av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="ef1de-139">Argument skickas till en parameter som anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ef1de-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="ef1de-140">Exempel på andra parameter deklarationer finns i [cmdlet-parametrar](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ef1de-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="ef1de-141">Deklarera parametrar som positions-eller namngivna</span><span class="sxs-lookup"><span data-stu-id="ef1de-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="ef1de-142">En cmdlet måste ange varje parameter som antingen en positions-eller namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="ef1de-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="ef1de-143">Båda typerna av parametrar accepterar enstaka argument, flera argument avgränsade med kommatecken och booleska inställningar.</span><span class="sxs-lookup"><span data-stu-id="ef1de-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="ef1de-144">En boolesk parameter, som även kallas för en *växel*, hanterar endast booleska inställningar.</span><span class="sxs-lookup"><span data-stu-id="ef1de-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="ef1de-145">Växeln används för att bestämma förekomst av parametern.</span><span class="sxs-lookup"><span data-stu-id="ef1de-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="ef1de-146">Rekommenderat standardvärde är `false`.</span><span class="sxs-lookup"><span data-stu-id="ef1de-146">The recommended default is `false`.</span></span>

<span data-ttu-id="ef1de-147">Cmdleten **Get-proc** definierar parametern `Name` som en positions parameter med position 0.</span><span class="sxs-lookup"><span data-stu-id="ef1de-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="ef1de-148">Det innebär att det första argumentet som användaren anger på kommando raden automatiskt infogas för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="ef1de-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="ef1de-149">Om du vill definiera en namngiven parameter för vilken användaren måste ange parameter namnet från kommando raden lämnar du `Position`-nyckelordet från deklarationen för attributet.</span><span class="sxs-lookup"><span data-stu-id="ef1de-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="ef1de-150">Om parametrar måste namnges, rekommenderar vi att du använder de mest använda parametrarna så att användarna inte behöver ange parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="ef1de-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="ef1de-151">Deklarera parametrar som obligatoriska eller valfria</span><span class="sxs-lookup"><span data-stu-id="ef1de-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="ef1de-152">En cmdlet måste ange varje parameter som antingen en valfri eller en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="ef1de-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="ef1de-153">I samplet **Get-proc-** cmdleten definieras `Name`-parametern som valfri eftersom nyckelordet `Mandatory` inte har angetts i deklarationen för attributet.</span><span class="sxs-lookup"><span data-stu-id="ef1de-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="ef1de-154">Stöd för parameter validering</span><span class="sxs-lookup"><span data-stu-id="ef1de-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="ef1de-155">Cmdleten **Get-proc** lägger till ett verifierings-attribut, [system. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), till parametern `Name` för att aktivera verifieringen att indatatypen inte är `null` eller tomt.</span><span class="sxs-lookup"><span data-stu-id="ef1de-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="ef1de-156">Det här attributet är ett av flera verifierings attribut från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef1de-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="ef1de-157">Exempel på andra verifierings attribut finns i [Verifiera parameter Indatatyp](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="ef1de-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ef1de-158">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="ef1de-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ef1de-159">Om cmdleten ska hantera kommando rads indata måste den åsidosätta lämpliga metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="ef1de-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="ef1de-160">De grundläggande metoderna för indata-bearbetning införs när [du skapar din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ef1de-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="ef1de-161">Cmdleten **Get-proc** åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att hantera `Name`-parameter indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="ef1de-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="ef1de-162">Den här metoden hämtar processerna för varje begärt process namn, eller alla för-processer om inget namn har angetts.</span><span class="sxs-lookup"><span data-stu-id="ef1de-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="ef1de-163">Observera att i [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [system. Management. Automation. cmdlet. WriteObject% 28System. Object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) är utmatnings mekanismen för att skicka utgående objekt till pipeline.</span><span class="sxs-lookup"><span data-stu-id="ef1de-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="ef1de-164">Den andra parametern för det här anropet, `enumerateCollection`, anges till `true` för att informera Windows PowerShell-körningsmiljön om att räkna upp utdata-matrisen för process objekt och skriva en process i taget till kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ef1de-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="ef1de-165">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="ef1de-165">Code Sample</span></span>

<span data-ttu-id="ef1de-166">Den fullständiga C# exempel koden finns i [GetProcessSample02-exempel](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ef1de-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ef1de-167">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="ef1de-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ef1de-168">Windows PowerShell skickar information mellan cmdletar med hjälp av .NET Framework objekt.</span><span class="sxs-lookup"><span data-stu-id="ef1de-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="ef1de-169">Därför kan en cmdlet behöva definiera en egen typ, eller så kan en cmdlet behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef1de-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ef1de-170">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="ef1de-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ef1de-171">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="ef1de-171">Building the Cmdlet</span></span>

<span data-ttu-id="ef1de-172">När du har implementerat en cmdlet måste du registrera den med Windows PowerShell med hjälp av en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="ef1de-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ef1de-173">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="ef1de-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ef1de-174">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="ef1de-174">Testing the Cmdlet</span></span>

<span data-ttu-id="ef1de-175">När cmdleten har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ef1de-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="ef1de-176">Här följer två sätt att testa koden för exempel-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef1de-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="ef1de-177">Mer information om hur du använder cmdlets från kommando raden finns [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ef1de-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="ef1de-178">Använd följande kommando i Windows PowerShell-prompten för att visa en lista över Internet Explorer-processen, som heter "iexplore".</span><span class="sxs-lookup"><span data-stu-id="ef1de-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="ef1de-179">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="ef1de-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="ef1de-180">Om du vill visa en lista över Internet Explorer-, Outlook-och anteckningar-processer med namnet "iexplore", "OUTLOOK" och "NOTEPAD" använder du följande kommando.</span><span class="sxs-lookup"><span data-stu-id="ef1de-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="ef1de-181">Om det finns flera processer visas alla.</span><span class="sxs-lookup"><span data-stu-id="ef1de-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="ef1de-182">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="ef1de-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="ef1de-183">Se även</span><span class="sxs-lookup"><span data-stu-id="ef1de-183">See Also</span></span>

[<span data-ttu-id="ef1de-184">Lägga till parametrar som bearbetar pipeline-inflöden</span><span class="sxs-lookup"><span data-stu-id="ef1de-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="ef1de-185">Skapa din första cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef1de-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="ef1de-186">Utöka objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="ef1de-186">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="ef1de-187">Registrera cmdlets, providers och värd program</span><span class="sxs-lookup"><span data-stu-id="ef1de-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="ef1de-188">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="ef1de-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="ef1de-189">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="ef1de-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
