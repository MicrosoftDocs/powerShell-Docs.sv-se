---
title: Att lägga till parametrar som bearbetning av kommandoradsverktyget | Microsoft Docs
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
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854955"
---
# <a name="adding-parameters-that-process-command-line-input"></a><span data-ttu-id="67b00-102">Lägga till parametrar som bearbetar kommandoradsindata</span><span class="sxs-lookup"><span data-stu-id="67b00-102">Adding Parameters That Process Command-Line Input</span></span>

<span data-ttu-id="67b00-103">En källa av indata för en cmdlet är från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="67b00-103">One source of input for a cmdlet is the command line.</span></span> <span data-ttu-id="67b00-104">Det här avsnittet beskrivs hur du lägger till en parameter för att den **Get-Proc** cmdlet (som beskrivs i [skapa din första Cmdlet](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta indata från den lokala datorn utifrån explicit objekt skickades till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="67b00-104">This topic describes how to add a parameter to the **Get-Proc** cmdlet (which is described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process input from the local computer based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="67b00-105">Den **Get-Proc** cmdlet som beskrivs här hämtar processer baserat på deras namn och visar information om processerna i en kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="67b00-105">The **Get-Proc** cmdlet described here retrieves processes based on their names, and then displays information about the processes at a command prompt.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="67b00-106">Definiera klassen Cmdlet</span><span class="sxs-lookup"><span data-stu-id="67b00-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="67b00-107">Det första steget i Skapa en cmdlet är cmdlet namngivning och deklarationen av .NET Framework-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="67b00-107">The first step in cmdlet creation is cmdlet naming and the declaration of the .NET Framework class that implements the cmdlet.</span></span> <span data-ttu-id="67b00-108">Denna cmdlet hämtar information om, så verb valt här heter ”hämta”.</span><span class="sxs-lookup"><span data-stu-id="67b00-108">This cmdlet retrieves process information, so the verb name chosen here is "Get."</span></span> <span data-ttu-id="67b00-109">(Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="67b00-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="67b00-110">Här är klassdeklarationen för den **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67b00-110">Here's the class declaration for the **Get-Proc** cmdlet.</span></span> <span data-ttu-id="67b00-111">Information om den här definitionen finns i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="67b00-111">Details about this definition are provided in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a><span data-ttu-id="67b00-112">Deklarera parametrar</span><span class="sxs-lookup"><span data-stu-id="67b00-112">Declaring Parameters</span></span>

<span data-ttu-id="67b00-113">En cmdlet-parameter gör det möjligt för användarna att ange indata till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="67b00-113">A cmdlet parameter enables the user to provide input to the cmdlet.</span></span> <span data-ttu-id="67b00-114">I följande exempel **Get-Proc** och `Get-Member` är namnen på pipeline cmdlet: ar, och `MemberType` är en parameter för den `Get-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67b00-114">In the following example, **Get-Proc** and `Get-Member` are the names of pipelined cmdlets, and `MemberType` is a parameter for the `Get-Member` cmdlet.</span></span> <span data-ttu-id="67b00-115">Parametern har argumentet ”property”.</span><span class="sxs-lookup"><span data-stu-id="67b00-115">The parameter has the argument "property."</span></span>

<span data-ttu-id="67b00-116">**PS > get-proc; `get-member` membertype - egenskapen**</span><span class="sxs-lookup"><span data-stu-id="67b00-116">**PS> get-proc ; `get-member` -membertype property**</span></span>

<span data-ttu-id="67b00-117">För att deklarera parametrar för en cmdlet, måste du först definiera de egenskaper som representerar parametrarna.</span><span class="sxs-lookup"><span data-stu-id="67b00-117">To declare parameters for a cmdlet, you must first define the properties that represent the parameters.</span></span> <span data-ttu-id="67b00-118">I den **Get-Proc** cmdlet, endast parametern är `Name`, som i det här fallet representerar namnet på .NET Framework processobjektet ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="67b00-118">In the **Get-Proc** cmdlet, the only parameter is `Name`, which in this case represents the name of the .NET Framework process object to retrieve.</span></span> <span data-ttu-id="67b00-119">Därför definierar klassen cmdlet en egenskap av typen sträng att godkänna en matris med namn.</span><span class="sxs-lookup"><span data-stu-id="67b00-119">Therefore, the cmdlet class defines a property of type string to accept an array of names.</span></span>

<span data-ttu-id="67b00-120">Här är parameterdeklaration för den `Name` -parametern för den **Get-Proc** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67b00-120">Here's the parameter declaration for the `Name` parameter of the **Get-Proc** cmdlet.</span></span>

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

<span data-ttu-id="67b00-121">Om Windows PowerShell-runtime som den här egenskapen är den `Name` parameter, en [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut har lagts till i egenskapsdefinition.</span><span class="sxs-lookup"><span data-stu-id="67b00-121">To inform the Windows PowerShell runtime that this property is the `Name` parameter, a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute is added to the property definition.</span></span> <span data-ttu-id="67b00-122">Grundläggande syntaxen för att deklarera det här attributet är `[Parameter()]`.</span><span class="sxs-lookup"><span data-stu-id="67b00-122">The basic syntax for declaring this attribute is `[Parameter()]`.</span></span>

> [!NOTE]
> <span data-ttu-id="67b00-123">En parameter måste uttryckligen markeras som offentliga.</span><span class="sxs-lookup"><span data-stu-id="67b00-123">A parameter must be explicitly marked as public.</span></span> <span data-ttu-id="67b00-124">Parametrar som inte är markerad som offentlig standard till interna och hittas inte av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="67b00-124">Parameters that are not marked as public default to internal and are not found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="67b00-125">Den här cmdleten använder en matris med strängar för den `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="67b00-125">This cmdlet uses an array of strings for the `Name` parameter.</span></span> <span data-ttu-id="67b00-126">Om möjligt definiera cmdlet: även en parameter som en matris, eftersom detta gör att cmdleten för att acceptera mer än ett objekt.</span><span class="sxs-lookup"><span data-stu-id="67b00-126">If possible, your cmdlet should also define a parameter as an array, because this allows the cmdlet to accept more than one item.</span></span>

#### <a name="things-to-remember-about-parameter-definitions"></a><span data-ttu-id="67b00-127">Att komma ihåg parameterdefinitioner</span><span class="sxs-lookup"><span data-stu-id="67b00-127">Things to Remember About Parameter Definitions</span></span>

- <span data-ttu-id="67b00-128">Fördefinierade Windows PowerShell-parametern och datatyper ska återanvändas så mycket som möjligt för att säkerställa att din cmdlet är kompatibelt med Windows PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="67b00-128">Predefined Windows PowerShell parameter names and data types should be reused as much as possible to ensure that your cmdlet is compatible with Windows PowerShell cmdlets.</span></span> <span data-ttu-id="67b00-129">Exempel: om alla cmdletar som använder den fördefinierade `Id` parameternamn som identifierar en resurs måste användaren att enkelt förstå innebörden av parametern, oavsett vilka cmdlet som de använder.</span><span class="sxs-lookup"><span data-stu-id="67b00-129">For example, if all cmdlets use the predefined `Id` parameter name to identify a resource, user will easily understand the meaning of the parameter, regardless of what cmdlet they are using.</span></span> <span data-ttu-id="67b00-130">Parameternamn följer i princip samma regler som de som används för variabelnamn i common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="67b00-130">Basically, parameter names follow the same rules as those used for variable names in the common language runtime (CLR).</span></span> <span data-ttu-id="67b00-131">Mer information om namngivning av parametern finns i [Cmdlet parameternamn](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span><span class="sxs-lookup"><span data-stu-id="67b00-131">For more information about parameter naming, see [Cmdlet Parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).</span></span>

- <span data-ttu-id="67b00-132">Windows PowerShell förbehåller sig några parameternamn att tillhandahålla en konsekvent användarupplevelse.</span><span class="sxs-lookup"><span data-stu-id="67b00-132">Windows PowerShell reserves a few parameter names to provide a consistent user experience.</span></span> <span data-ttu-id="67b00-133">Använd inte dessa parameternamn: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, och `OutBuffer`.</span><span class="sxs-lookup"><span data-stu-id="67b00-133">Do not use these parameter names: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, and `OutBuffer`.</span></span> <span data-ttu-id="67b00-134">Dessutom kan följande alias för dessa parameternamn är reserverade: `vb`, `db`, `ea`, `ev`, `ov`, och `ob`.</span><span class="sxs-lookup"><span data-stu-id="67b00-134">Additionally, the following aliases for these parameter names are reserved: `vb`, `db`, `ea`, `ev`, `ov`, and `ob`.</span></span>

- <span data-ttu-id="67b00-135">`Name` är ett enkelt och vanliga parameternamn, rekommenderas för användning i dina cmdlets.</span><span class="sxs-lookup"><span data-stu-id="67b00-135">`Name` is a simple and common parameter name, recommended for use in your cmdlets.</span></span> <span data-ttu-id="67b00-136">Det är bättre att välja ett parameternamn så här än en komplex namn som är unika för en specifik cmdlet och svåra att komma ihåg.</span><span class="sxs-lookup"><span data-stu-id="67b00-136">It is better to choose a parameter name like this than a complex name that is unique to a specific cmdlet and hard to remember.</span></span>

- <span data-ttu-id="67b00-137">Parametrar är skiftlägeskänsliga i Windows PowerShell, även om som standard behåller gränssnittet skiftläge.</span><span class="sxs-lookup"><span data-stu-id="67b00-137">Parameters are case-insensitive in Windows PowerShell, although by default the shell preserves case.</span></span> <span data-ttu-id="67b00-138">Skiftlägeskänslighet av argumenten är beroende av driften av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="67b00-138">Case-sensitivity of the arguments depends on the operation of the cmdlet.</span></span> <span data-ttu-id="67b00-139">Argumenten skickas till en parameter som anges på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="67b00-139">Arguments are passed to a parameter as specified at the command line.</span></span>

- <span data-ttu-id="67b00-140">Exempel på andra parameterdeklarationer finns [Cmdlet-parametrarna](./cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="67b00-140">For examples of other parameter declarations, see [Cmdlet Parameters](./cmdlet-parameters.md).</span></span>

## <a name="declaring-parameters-as-positional-or-named"></a><span data-ttu-id="67b00-141">Deklarera parametrar som namngivna eller namngivna</span><span class="sxs-lookup"><span data-stu-id="67b00-141">Declaring Parameters as Positional or Named</span></span>

<span data-ttu-id="67b00-142">En cmdlet måste ange varje parameter som antingen en namngivna eller namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="67b00-142">A cmdlet must set each parameter as either a positional or named parameter.</span></span> <span data-ttu-id="67b00-143">Båda typerna av parametrar acceptera enda argument, flera argument avgränsade med kommatecken, och booleska inställningar.</span><span class="sxs-lookup"><span data-stu-id="67b00-143">Both kinds of parameters accept single arguments, multiple arguments separated by commas, and Boolean settings.</span></span> <span data-ttu-id="67b00-144">En boolesk parameter som kallas även en *växla*, hanterar endast booleskt inställningar.</span><span class="sxs-lookup"><span data-stu-id="67b00-144">A Boolean parameter, also called a *switch*, handles only Boolean settings.</span></span> <span data-ttu-id="67b00-145">Växeln används för att bestämma förekomst av parametern.</span><span class="sxs-lookup"><span data-stu-id="67b00-145">The switch is used to determine the presence of the parameter.</span></span> <span data-ttu-id="67b00-146">Det rekommenderade standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="67b00-146">The recommended default is `false`.</span></span>

<span data-ttu-id="67b00-147">Exemplet **Get-Proc** cmdlet definierar den `Name` parametern som ett namngivna parametern med position 0.</span><span class="sxs-lookup"><span data-stu-id="67b00-147">The sample **Get-Proc** cmdlet defines the `Name` parameter as a positional parameter with position 0.</span></span> <span data-ttu-id="67b00-148">Det innebär att det första argumentet som användaren anger på kommandoraden infogas automatiskt för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="67b00-148">This means that the first argument the user enters on the command line is automatically inserted for this parameter.</span></span> <span data-ttu-id="67b00-149">Om du vill definiera en namngiven parameter för användaren måste ange parameternamnet från kommandoraden, lämnar den `Position` nyckelordet utanför deklaration av attribut.</span><span class="sxs-lookup"><span data-stu-id="67b00-149">If you want to define a named parameter, for which the user must specify the parameter name from the command line, leave the `Position` keyword out of the attribute declaration.</span></span>

> [!NOTE]
> <span data-ttu-id="67b00-150">Om inte måste ha namnet parametrar, rekommenderar vi att du gör de mest använda parametrarna namngivna så att användarna inte behöver skriva parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="67b00-150">Unless parameters must be named, we recommend that you make the most-used parameters positional so that users will not have to type the parameter name.</span></span>

## <a name="declaring-parameters-as-mandatory-or-optional"></a><span data-ttu-id="67b00-151">Deklarera parametrar som obligatoriska eller valfria</span><span class="sxs-lookup"><span data-stu-id="67b00-151">Declaring Parameters as Mandatory or Optional</span></span>

<span data-ttu-id="67b00-152">En cmdlet måste ange varje parameter som en valfri eller en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="67b00-152">A cmdlet must set each parameter as either an optional or a mandatory parameter.</span></span> <span data-ttu-id="67b00-153">I exemplet **Get-Proc** cmdlet, den `Name` parametern har definierats som valfria eftersom den `Mandatory` nyckelordet har inte angetts i deklarationen för attributet.</span><span class="sxs-lookup"><span data-stu-id="67b00-153">In the sample **Get-Proc** cmdlet, the `Name` parameter is defined as optional because the `Mandatory` keyword is not set in the attribute declaration.</span></span>

## <a name="supporting-parameter-validation"></a><span data-ttu-id="67b00-154">Stöd för parameterverifieringen</span><span class="sxs-lookup"><span data-stu-id="67b00-154">Supporting Parameter Validation</span></span>

<span data-ttu-id="67b00-155">Exemplet **Get-Proc** cmdlet lägger till en verifiering av indata-attribut, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), i den `Name` parametern för att aktivera validering som den indata är varken `null` eller tomt.</span><span class="sxs-lookup"><span data-stu-id="67b00-155">The sample **Get-Proc** cmdlet adds an input validation attribute, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), to the `Name` parameter to enable validation that the input is neither `null` nor empty.</span></span> <span data-ttu-id="67b00-156">Det här attributet är en av flera verifiering attribut som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67b00-156">This attribute is one of several validation attributes provided by Windows PowerShell.</span></span> <span data-ttu-id="67b00-157">Exempel på andra verifiering attribut finns [verifierar indata för parametern](./validating-parameter-input.md).</span><span class="sxs-lookup"><span data-stu-id="67b00-157">For examples of other validation attributes, see [Validating Parameter Input](./validating-parameter-input.md).</span></span>

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="67b00-158">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="67b00-158">Overriding an Input Processing Method</span></span>

<span data-ttu-id="67b00-159">Om din cmdlet är att hantera kommandoradsverktyget indata, måste den åsidosätta lämpliga indata metoderna.</span><span class="sxs-lookup"><span data-stu-id="67b00-159">If your cmdlet is to handle command-line input, it must override the appropriate input processing methods.</span></span> <span data-ttu-id="67b00-160">Grundläggande inkommande bearbetningsmetoder som introduceras i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="67b00-160">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="67b00-161">Den **Get-Proc** cmdlet åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att hantera den `Name` parametern indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="67b00-161">The **Get-Proc** cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="67b00-162">Den här metoden hämtar processer för varje begärda processnamn eller alla för processer om inget namn anges.</span><span class="sxs-lookup"><span data-stu-id="67b00-162">This method gets the processes for each requested process name, or all for processes if no name is provided.</span></span> <span data-ttu-id="67b00-163">Observera att i [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) är utdata mekanism för att skicka utdata objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="67b00-163">Notice that in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="67b00-164">Den andra parametern för det här anropet `enumerateCollection`, är inställd på `true` om Windows PowerShell-runtime för att räkna upp utdata-matris med process-objekt och skriva en process i taget till kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="67b00-164">The second parameter of this call, `enumerateCollection`, is set to `true` to inform the Windows PowerShell runtime to enumerate the output array of process objects and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="67b00-165">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="67b00-165">Code Sample</span></span>

<span data-ttu-id="67b00-166">För hela C# exempelkoden, se [GetProcessSample02 exempel](./getprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="67b00-166">For the complete C# sample code, see [GetProcessSample02 Sample](./getprocesssample02-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="67b00-167">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="67b00-167">Defining Object Types and Formatting</span></span>

<span data-ttu-id="67b00-168">Windows PowerShell skickar information mellan cmdlet: ar med .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="67b00-168">Windows PowerShell passes information between cmdlets by using .NET Framework objects.</span></span> <span data-ttu-id="67b00-169">Därför måste en cmdlet kan behöva definiera sin egen typ eller en cmdlet kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67b00-169">Consequently, a cmdlet might need to define its own type, or a cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="67b00-170">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="67b00-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="67b00-171">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="67b00-171">Building the Cmdlet</span></span>

<span data-ttu-id="67b00-172">När du har implementerat en cmdlet, måste du registrera den med Windows PowerShell med hjälp av en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="67b00-172">After you implement a cmdlet, you must register it with Windows PowerShell by using a Windows PowerShell snap-in.</span></span> <span data-ttu-id="67b00-173">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="67b00-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="67b00-174">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="67b00-174">Testing the Cmdlet</span></span>

<span data-ttu-id="67b00-175">När cmdlet: registreras med Windows PowerShell, kan du testa den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="67b00-175">When your cmdlet is registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="67b00-176">Här finns två sätt att testa koden för exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67b00-176">Here are two ways to test the code for the sample cmdlet.</span></span> <span data-ttu-id="67b00-177">Läs mer om hur du använder cmdlets från kommandoraden, [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="67b00-177">For more information about using cmdlets from the command line, see [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="67b00-178">Använder du följande kommando i Windows PowerShell-Kommandotolken visa en lista över Internet Explorer-processen, som heter ”IEXPLORE”.</span><span class="sxs-lookup"><span data-stu-id="67b00-178">At the Windows PowerShell prompt, use the following command to list the Internet Explorer process, which is named "IEXPLORE."</span></span>

    ```powershell
    PS> get-proc -name iexplore
    ```

<span data-ttu-id="67b00-179">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="67b00-179">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- <span data-ttu-id="67b00-180">Använd följande kommando om du vill visa de Internet Explorer, Outlook och anteckningar processer med namnet ”IEXPLORE”, ”OUTLOOK” och ”ANTECKNINGAR”,.</span><span class="sxs-lookup"><span data-stu-id="67b00-180">To list the Internet Explorer, Outlook, and Notepad processes named "IEXPLORE," "OUTLOOK," and "NOTEPAD," use the following command.</span></span> <span data-ttu-id="67b00-181">Om det finns flera processer, visas alla.</span><span class="sxs-lookup"><span data-stu-id="67b00-181">If there are multiple processes, all of them are displayed.</span></span>

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

<span data-ttu-id="67b00-182">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="67b00-182">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a><span data-ttu-id="67b00-183">Se även</span><span class="sxs-lookup"><span data-stu-id="67b00-183">See Also</span></span>

[<span data-ttu-id="67b00-184">Att lägga till parametrar som indata för Process-pipelinen</span><span class="sxs-lookup"><span data-stu-id="67b00-184">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="67b00-185">Skapa din första cmdlet:</span><span class="sxs-lookup"><span data-stu-id="67b00-185">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="67b00-186">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="67b00-186">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="67b00-187">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="67b00-187">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="67b00-188">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="67b00-188">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="67b00-189">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="67b00-189">Cmdlet Samples</span></span>](./cmdlet-samples.md)
