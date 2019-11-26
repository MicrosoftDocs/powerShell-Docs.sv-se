---
title: Lägga till parameter uppsättningar till en cmdlet | Microsoft Docs
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
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416321"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="e34f9-102">Lägga till parameteruppsättningar i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="e34f9-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="e34f9-103">Saker att känna till om parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="e34f9-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="e34f9-104">Windows PowerShell definierar en parameter uppsättning som en grupp parametrar som fungerar tillsammans.</span><span class="sxs-lookup"><span data-stu-id="e34f9-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="e34f9-105">Genom att gruppera parametrarna för en cmdlet kan du skapa en enda cmdlet som kan ändra dess funktioner baserat på vilken grupp av parametrar som användaren anger.</span><span class="sxs-lookup"><span data-stu-id="e34f9-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="e34f9-106">Ett exempel på en cmdlet som använder två parameter uppsättningar för att definiera olika funktioner är den `Get-EventLog`-cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e34f9-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="e34f9-107">Den här cmdleten returnerar annan information när användaren anger parametern `List` eller `LogName`.</span><span class="sxs-lookup"><span data-stu-id="e34f9-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="e34f9-108">Om parametern `LogName` anges, returnerar cmdleten information om händelserna i en viss händelse logg.</span><span class="sxs-lookup"><span data-stu-id="e34f9-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="e34f9-109">Om parametern `List` anges, returnerar cmdleten information om själva loggfilerna (inte den händelse information de innehåller).</span><span class="sxs-lookup"><span data-stu-id="e34f9-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="e34f9-110">I det här fallet identifierar parametrarna för `List` och `LogName` två separata parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="e34f9-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="e34f9-111">Två viktiga saker att komma ihåg om parameter uppsättningar är att Windows PowerShell-körningsmiljön endast använder en parameter uppsättning för en viss Indatatyp och att varje parameter uppsättning måste ha minst en parameter som är unik för den parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e34f9-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="e34f9-112">För att illustrera den sista punkten använder denna Stop-proc-cmdlet tre parameter uppsättningar: `ProcessName`, `ProcessId`och `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="e34f9-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="e34f9-113">Var och en av dessa parameter uppsättningar har en parameter som inte finns i de andra parameter uppsättningarna.</span><span class="sxs-lookup"><span data-stu-id="e34f9-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="e34f9-114">Parameter uppsättningarna kan dela andra parametrar, men cmdleten använder de unika parametrarna `ProcessName`, `ProcessId`och `InputObject` för att identifiera vilken uppsättning parametrar som Windows PowerShell-körningen ska använda.</span><span class="sxs-lookup"><span data-stu-id="e34f9-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="e34f9-115">Deklarera cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="e34f9-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="e34f9-116">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e34f9-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e34f9-117">För denna cmdlet används livs cykel verbet "Stop" eftersom cmdleten stoppar system processer.</span><span class="sxs-lookup"><span data-stu-id="e34f9-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="e34f9-118">Substantiv namnet "proc" används eftersom cmdleten fungerar på processer.</span><span class="sxs-lookup"><span data-stu-id="e34f9-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="e34f9-119">I deklarationen nedan noterar du att cmdlet-verbet och Substantiv namnet visas i namnet på cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="e34f9-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="e34f9-120">Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e34f9-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e34f9-121">Följande kod är klass definitionen för den här Stop-proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e34f9-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="e34f9-122">Deklarera parametrarna för cmdleten</span><span class="sxs-lookup"><span data-stu-id="e34f9-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="e34f9-123">Den här cmdleten definierar tre parametrar som krävs som indata till cmdleten (dessa parametrar definierar även parameter uppsättningar), samt en `Force` parameter som hanterar vad cmdleten gör och en `PassThru` parameter som avgör om cmdleten skickar ett utdata-objekt via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e34f9-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="e34f9-124">Som standard skickar denna cmdlet inget objekt via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e34f9-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="e34f9-125">Mer information om de sista två parametrarna finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="e34f9-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="e34f9-126">Att deklarera namn parametern</span><span class="sxs-lookup"><span data-stu-id="e34f9-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="e34f9-127">Med den här Indataparametern kan användaren ange namnen på de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="e34f9-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="e34f9-128">Observera att attributet `ParameterSetName` attribut för attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) anger den `ProcessName` parameter uppsättningen för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="e34f9-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="e34f9-129">Observera också att aliaset "ProcessName" anges för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="e34f9-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="e34f9-130">Deklarera ID-parametern</span><span class="sxs-lookup"><span data-stu-id="e34f9-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="e34f9-131">Med den här Indataparametern kan användaren ange identifierare för de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="e34f9-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="e34f9-132">Observera att attributet `ParameterSetName` attribut för attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) anger den `ProcessId` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e34f9-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="e34f9-133">Observera också att alias "ProcessId" anges för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="e34f9-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="e34f9-134">Deklarera parametern InputObject</span><span class="sxs-lookup"><span data-stu-id="e34f9-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="e34f9-135">Med den här Indataparametern kan användaren ange ett indata-objekt som innehåller information om de processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="e34f9-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="e34f9-136">Observera att attributet `ParameterSetName` attribut för attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) anger den `InputObject` parameter uppsättningen för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="e34f9-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="e34f9-137">Observera också att den här parametern inte har något alias.</span><span class="sxs-lookup"><span data-stu-id="e34f9-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="e34f9-138">Deklarera parametrar i flera parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="e34f9-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="e34f9-139">Även om det måste finnas en unik parameter för varje parameter uppsättning kan parametrarna tillhöra mer än en parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="e34f9-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="e34f9-140">I dessa fall ger du den delade parametern en deklaration för [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) för varje uppsättning som parametern tillhör.</span><span class="sxs-lookup"><span data-stu-id="e34f9-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="e34f9-141">Om en parameter är i alla parameter uppsättningar behöver du bara deklarera attributet-parameter en gång och behöver inte ange parameter uppsättningens namn.</span><span class="sxs-lookup"><span data-stu-id="e34f9-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="e34f9-142">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="e34f9-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="e34f9-143">Varje cmdlet måste åsidosätta en metod för bearbetning av indata, oftast används metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="e34f9-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="e34f9-144">I den här cmdleten åsidosätts metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , så att cmdleten kan bearbeta valfritt antal processer.</span><span class="sxs-lookup"><span data-stu-id="e34f9-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="e34f9-145">Den innehåller en SELECT-instruktion som anropar en annan metod baserat på vilken parameter uppsättning användaren har angett.</span><span class="sxs-lookup"><span data-stu-id="e34f9-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="e34f9-146">De hjälp metoder som anropas av SELECT-instruktionen beskrivs inte här, men du kan se deras implementering i hela kod exemplet i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="e34f9-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e34f9-147">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="e34f9-147">Code Sample</span></span>

<span data-ttu-id="e34f9-148">Den fullständiga C# exempel koden finns i [StopProcessSample04-exempel](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e34f9-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="e34f9-149">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="e34f9-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="e34f9-150">Windows PowerShell skickar information mellan cmdlets med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="e34f9-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="e34f9-151">Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e34f9-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e34f9-152">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e34f9-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e34f9-153">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e34f9-153">Building the Cmdlet</span></span>

<span data-ttu-id="e34f9-154">När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="e34f9-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e34f9-155">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e34f9-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e34f9-156">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e34f9-156">Testing the Cmdlet</span></span>

<span data-ttu-id="e34f9-157">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e34f9-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="e34f9-158">Här följer några tester som visar hur parametrarna `ProcessId` och `InputObject` kan användas för att testa parameter uppsättningar för att stoppa en process.</span><span class="sxs-lookup"><span data-stu-id="e34f9-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="e34f9-159">Med Windows PowerShell igång kör du Stop-proc-cmdlet: en med parametern `ProcessId` som har angetts för att stoppa en process baserat på dess identifierare.</span><span class="sxs-lookup"><span data-stu-id="e34f9-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="e34f9-160">I det här fallet använder cmdleten `ProcessId` parameter inställd för att stoppa processen.</span><span class="sxs-lookup"><span data-stu-id="e34f9-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="e34f9-161">Med Windows PowerShell igång kör du Stop-proc-cmdlet: en med parametern `InputObject` som har angetts för att stoppa processer på objektet Notepad som hämtats av `Get-Process` kommandot.</span><span class="sxs-lookup"><span data-stu-id="e34f9-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="e34f9-162">Se även</span><span class="sxs-lookup"><span data-stu-id="e34f9-162">See Also</span></span>

[<span data-ttu-id="e34f9-163">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="e34f9-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="e34f9-164">Så här skapar du en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="e34f9-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="e34f9-165">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e34f9-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="e34f9-166">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e34f9-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="e34f9-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e34f9-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
