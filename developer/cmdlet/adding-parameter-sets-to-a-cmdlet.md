---
title: Att lägga till parametern anger att en Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054993"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="148c6-102">Lägga till parameteruppsättningar i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="148c6-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="148c6-103">Det här avsnittet beskrivs hur du lägger till parametern anger att cmdleten Stop-processen (beskrivs i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="148c6-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="148c6-104">Precis som andra cmdlets i Stop-processen som beskrivs i den här Programmeringsguide kan denna cmdlet försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="148c6-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="148c6-105">Ämnena i det här avsnittet omfattar följande:</span><span class="sxs-lookup"><span data-stu-id="148c6-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="148c6-106">Att känna till om parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="148c6-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="148c6-107">Fastställa Cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="148c6-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="148c6-108">Deklarera parametrarna för cmdleten</span><span class="sxs-lookup"><span data-stu-id="148c6-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="148c6-109">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="148c6-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="148c6-110">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="148c6-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="148c6-111">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="148c6-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="148c6-112">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="148c6-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="148c6-113">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="148c6-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="148c6-114">Att känna till om parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="148c6-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="148c6-115">Windows PowerShell definierar en parameter som angetts som en grupp med parametrar som fungerar tillsammans.</span><span class="sxs-lookup"><span data-stu-id="148c6-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="148c6-116">Du kan skapa en enkel cmdlet som kan ändra dess funktioner baserat på vilken grupp av parametrarna användaren anger genom att gruppera parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="148c6-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="148c6-117">Ett exempel på en cmdlet som använder två parameteruppsättningar för att definiera olika funktioner är den `Get-EventLog` cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="148c6-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="148c6-118">Denna cmdlet returnerar olika typer av information när användaren anger den `List` eller `LogName` parametern.</span><span class="sxs-lookup"><span data-stu-id="148c6-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="148c6-119">Om den `LogName` parameter har angetts, returnerar cmdleten information om händelser i en viss händelselogg.</span><span class="sxs-lookup"><span data-stu-id="148c6-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="148c6-120">Om den `List` parameter har angetts, returnerar cmdleten information om loggen filer själva (inte händelseinformationen i dem).</span><span class="sxs-lookup"><span data-stu-id="148c6-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="148c6-121">I det här fallet den `List` och `LogName` parametrar identifiera två separata parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="148c6-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="148c6-122">Två viktiga saker att tänka på parameteruppsättningar är att Windows PowerShell-runtime använder bara en parameteruppsättning för en viss indata och att varje parameteruppsättningen måste ha minst en parameter som är unikt för den parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="148c6-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="148c6-123">För att visa den senaste tidpunkten kan denna cmdlet Stop-processen använder tre parameteruppsättningar: `ProcessName`, `ProcessId`, och `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="148c6-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="148c6-124">Var och en av dessa parameteruppsättningar har en parameter som inte är i andra parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="148c6-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="148c6-125">Parameteruppsättningar kan dela andra parametrar, men använder de unika parametrarna för cmdleten `ProcessName`, `ProcessId`, och `InputObject` att identifiera vilken uppsättning parametrar som ska användas i Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="148c6-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="148c6-126">Fastställa Cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="148c6-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="148c6-127">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="148c6-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="148c6-128">Livscykeln verb ”stoppa” används för denna cmdlet, eftersom cmdleten stoppar systemprocesser.</span><span class="sxs-lookup"><span data-stu-id="148c6-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="148c6-129">Substantiv namnet ”Proc” används eftersom cmdlet fungerar på processer.</span><span class="sxs-lookup"><span data-stu-id="148c6-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="148c6-130">Observera att cmdlet verb och substantiv namnet visas namnet på klassen cmdlet i förklaringen nedan.</span><span class="sxs-lookup"><span data-stu-id="148c6-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="148c6-131">Läs mer om godkända cmdlet verb-namnen [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="148c6-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="148c6-132">Följande kod är klassdefinitionen för denna cmdlet Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="148c6-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="148c6-133">Deklarera parametrarna för cmdleten</span><span class="sxs-lookup"><span data-stu-id="148c6-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="148c6-134">Denna cmdlet definierar tre parametrar som behövs som indata för cmdlet (dessa parametrar också definiera parameteruppsättningar), samt en `Force` parameter som hanterar vad cmdleten gör och en `PassThru` parameter som anger om cmdlet: en ska skicka ett utdataobjekt genom pipelinen.</span><span class="sxs-lookup"><span data-stu-id="148c6-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="148c6-135">Som standard skickar denna cmdlet inte ett objekt genom pipelinen.</span><span class="sxs-lookup"><span data-stu-id="148c6-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="148c6-136">Mer information om dessa två sista parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="148c6-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="148c6-137">Deklarera Namnparametern</span><span class="sxs-lookup"><span data-stu-id="148c6-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="148c6-138">Denna indataparameter gör att användaren kan ange namnen på processerna som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="148c6-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="148c6-139">Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `ProcessName` parameteruppsättning för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="148c6-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="148c6-140">Observera också att alias ”ProcessName” ges till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="148c6-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="148c6-141">Deklarera Id-Parameter</span><span class="sxs-lookup"><span data-stu-id="148c6-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="148c6-142">Denna indataparameter gör att användaren att ange identifierare av processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="148c6-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="148c6-143">Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `ProcessId` parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="148c6-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="148c6-144">Observera också att alias ”ProcessId” ges till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="148c6-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="148c6-145">Deklarera parametern InputObject</span><span class="sxs-lookup"><span data-stu-id="148c6-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="148c6-146">Denna indataparameter gör att användaren kan ange ett inkommande objekt som innehåller information om processerna som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="148c6-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="148c6-147">Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `InputObject` parameteruppsättning för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="148c6-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="148c6-148">Observera också att den här parametern har inget alias.</span><span class="sxs-lookup"><span data-stu-id="148c6-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="148c6-149">Deklarera parametrar i flera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="148c6-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="148c6-150">Även om det måste vara en parameter som är unika för varje parameteruppsättningen, kan parametrar tillhöra mer än en parameter.</span><span class="sxs-lookup"><span data-stu-id="148c6-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="148c6-151">I dessa fall kan ge parametern delade en [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaration av attribut för var och en principuppsättningsparameter som de tillhör.</span><span class="sxs-lookup"><span data-stu-id="148c6-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="148c6-152">Om det finns en parameter i alla parameteruppsättningar kommer du bara har deklarera parameterattributet en gång och behöver inte ange parameteruppsättning namn.</span><span class="sxs-lookup"><span data-stu-id="148c6-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="148c6-153">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="148c6-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="148c6-154">Alla cmdlets måste åsidosätta indata metoden bearbetades, oftast det här är den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="148c6-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="148c6-155">I den här cmdleten den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden åsidosätts så att cmdleten kan bearbeta valfritt antal processer.</span><span class="sxs-lookup"><span data-stu-id="148c6-155">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="148c6-156">Den innehåller en Select-instruktion som anropar en annan metod baserat på vilka parameteruppsättningen användaren har angett.</span><span class="sxs-lookup"><span data-stu-id="148c6-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="148c6-157">Hjälpmetoder som anropas av Select-instruktion som inte beskrivs här, men du kan se deras implementering i hela kodexemplet i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="148c6-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="148c6-158">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="148c6-158">Code Sample</span></span>

<span data-ttu-id="148c6-159">För hela C# exempelkoden, se [StopProcessSample04 exempel](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="148c6-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="148c6-160">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="148c6-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="148c6-161">Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="148c6-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="148c6-162">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="148c6-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="148c6-163">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="148c6-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="148c6-164">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="148c6-164">Building the Cmdlet</span></span>

<span data-ttu-id="148c6-165">När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="148c6-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="148c6-166">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="148c6-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="148c6-167">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="148c6-167">Testing the Cmdlet</span></span>

<span data-ttu-id="148c6-168">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="148c6-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="148c6-169">Här följer några tester som visar hur `ProcessId` och `InputObject` parametrar kan användas för att testa sina parameteruppsättningar för att stoppa en process.</span><span class="sxs-lookup"><span data-stu-id="148c6-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="148c6-170">Med Windows PowerShell igång, kör du cmdleten Stop-processen med den `ProcessId` parameteruppsättning för att stoppa en process som baserat på dess identifierare.</span><span class="sxs-lookup"><span data-stu-id="148c6-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="148c6-171">I så fall cmdlet: en använder den `ProcessId` parameteruppsättning för att stoppa processen.</span><span class="sxs-lookup"><span data-stu-id="148c6-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="148c6-172">Med Windows PowerShell igång, kör du cmdleten Stop-processen med den `InputObject` parameteruppsättning stoppa processer på objektet anteckningar som hämtas av den `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="148c6-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="148c6-173">Se även</span><span class="sxs-lookup"><span data-stu-id="148c6-173">See Also</span></span>

[<span data-ttu-id="148c6-174">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="148c6-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="148c6-175">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="148c6-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="148c6-176">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="148c6-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="148c6-177">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="148c6-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="148c6-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="148c6-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
