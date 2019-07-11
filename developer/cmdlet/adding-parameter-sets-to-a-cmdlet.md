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
ms.openlocfilehash: d330b9be1da9fbb36be324e68fd6cf2d874fc06b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733805"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="05251-102">Lägga till parameteruppsättningar i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="05251-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="05251-103">Att känna till om parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="05251-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="05251-104">Windows PowerShell definierar en parameter som angetts som en grupp med parametrar som fungerar tillsammans.</span><span class="sxs-lookup"><span data-stu-id="05251-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="05251-105">Du kan skapa en enkel cmdlet som kan ändra dess funktioner baserat på vilken grupp av parametrarna användaren anger genom att gruppera parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05251-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="05251-106">Ett exempel på en cmdlet som använder två parameteruppsättningar för att definiera olika funktioner är den `Get-EventLog` cmdlet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05251-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="05251-107">Denna cmdlet returnerar olika typer av information när användaren anger den `List` eller `LogName` parametern.</span><span class="sxs-lookup"><span data-stu-id="05251-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="05251-108">Om den `LogName` parameter har angetts, returnerar cmdleten information om händelser i en viss händelselogg.</span><span class="sxs-lookup"><span data-stu-id="05251-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="05251-109">Om den `List` parameter har angetts, returnerar cmdleten information om loggen filer själva (inte händelseinformationen i dem).</span><span class="sxs-lookup"><span data-stu-id="05251-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="05251-110">I det här fallet den `List` och `LogName` parametrar identifiera två separata parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="05251-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="05251-111">Två viktiga saker att tänka på parameteruppsättningar är att Windows PowerShell-runtime använder bara en parameteruppsättning för en viss indata och att varje parameteruppsättningen måste ha minst en parameter som är unikt för den parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05251-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="05251-112">För att visa den senaste tidpunkten kan denna cmdlet Stop-processen använder tre parameteruppsättningar: `ProcessName`, `ProcessId`, och `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="05251-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="05251-113">Var och en av dessa parameteruppsättningar har en parameter som inte är i andra parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="05251-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="05251-114">Parameteruppsättningar kan dela andra parametrar, men använder de unika parametrarna för cmdleten `ProcessName`, `ProcessId`, och `InputObject` att identifiera vilken uppsättning parametrar som ska användas i Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="05251-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="05251-115">Fastställa Cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="05251-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="05251-116">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="05251-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="05251-117">Livscykeln verb ”stoppa” används för denna cmdlet, eftersom cmdleten stoppar systemprocesser.</span><span class="sxs-lookup"><span data-stu-id="05251-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="05251-118">Substantiv namnet ”Proc” används eftersom cmdlet fungerar på processer.</span><span class="sxs-lookup"><span data-stu-id="05251-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="05251-119">Observera att cmdlet verb och substantiv namnet visas namnet på klassen cmdlet i förklaringen nedan.</span><span class="sxs-lookup"><span data-stu-id="05251-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="05251-120">Läs mer om godkända cmdlet verb-namnen [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="05251-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="05251-121">Följande kod är klassdefinitionen för denna cmdlet Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="05251-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="05251-122">Deklarera parametrarna för cmdleten</span><span class="sxs-lookup"><span data-stu-id="05251-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="05251-123">Denna cmdlet definierar tre parametrar som behövs som indata för cmdlet (dessa parametrar också definiera parameteruppsättningar), samt en `Force` parameter som hanterar vad cmdleten gör och en `PassThru` parameter som anger om cmdlet: en ska skicka ett utdataobjekt genom pipelinen.</span><span class="sxs-lookup"><span data-stu-id="05251-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="05251-124">Som standard skickar denna cmdlet inte ett objekt genom pipelinen.</span><span class="sxs-lookup"><span data-stu-id="05251-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="05251-125">Mer information om dessa två sista parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="05251-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="05251-126">Deklarera Namnparametern</span><span class="sxs-lookup"><span data-stu-id="05251-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="05251-127">Denna indataparameter gör att användaren kan ange namnen på processerna som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="05251-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="05251-128">Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `ProcessName` parameteruppsättning för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="05251-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

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

<span data-ttu-id="05251-129">Observera också att alias ”ProcessName” ges till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="05251-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="05251-130">Deklarera Id-Parameter</span><span class="sxs-lookup"><span data-stu-id="05251-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="05251-131">Denna indataparameter gör att användaren att ange identifierare av processer som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="05251-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="05251-132">Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `ProcessId` parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="05251-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="05251-133">Observera också att alias ”ProcessId” ges till den här parametern.</span><span class="sxs-lookup"><span data-stu-id="05251-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="05251-134">Deklarera parametern InputObject</span><span class="sxs-lookup"><span data-stu-id="05251-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="05251-135">Denna indataparameter gör att användaren kan ange ett inkommande objekt som innehåller information om processerna som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="05251-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="05251-136">Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `InputObject` parameteruppsättning för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="05251-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="05251-137">Observera också att den här parametern har inget alias.</span><span class="sxs-lookup"><span data-stu-id="05251-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="05251-138">Deklarera parametrar i flera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="05251-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="05251-139">Även om det måste vara en parameter som är unika för varje parameteruppsättningen, kan parametrar tillhöra mer än en parameter.</span><span class="sxs-lookup"><span data-stu-id="05251-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="05251-140">I dessa fall kan ge parametern delade en [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaration av attribut för var och en principuppsättningsparameter som de tillhör.</span><span class="sxs-lookup"><span data-stu-id="05251-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="05251-141">Om det finns en parameter i alla parameteruppsättningar kommer du bara har deklarera parameterattributet en gång och behöver inte ange parameteruppsättning namn.</span><span class="sxs-lookup"><span data-stu-id="05251-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="05251-142">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="05251-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="05251-143">Alla cmdlets måste åsidosätta indata metoden bearbetades, oftast det här är den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="05251-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="05251-144">I den här cmdleten den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden åsidosätts så att cmdleten kan bearbeta valfritt antal processer.</span><span class="sxs-lookup"><span data-stu-id="05251-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="05251-145">Den innehåller en Select-instruktion som anropar en annan metod baserat på vilka parameteruppsättningen användaren har angett.</span><span class="sxs-lookup"><span data-stu-id="05251-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="05251-146">Hjälpmetoder som anropas av Select-instruktion som inte beskrivs här, men du kan se deras implementering i hela kodexemplet i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="05251-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="05251-147">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="05251-147">Code Sample</span></span>

<span data-ttu-id="05251-148">För hela C# exempelkoden, se [StopProcessSample04 exempel](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="05251-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="05251-149">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="05251-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="05251-150">Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="05251-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="05251-151">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="05251-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="05251-152">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="05251-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="05251-153">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="05251-153">Building the Cmdlet</span></span>

<span data-ttu-id="05251-154">När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="05251-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="05251-155">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="05251-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="05251-156">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="05251-156">Testing the Cmdlet</span></span>

<span data-ttu-id="05251-157">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="05251-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="05251-158">Här följer några tester som visar hur `ProcessId` och `InputObject` parametrar kan användas för att testa sina parameteruppsättningar för att stoppa en process.</span><span class="sxs-lookup"><span data-stu-id="05251-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="05251-159">Med Windows PowerShell igång, kör du cmdleten Stop-processen med den `ProcessId` parameteruppsättning för att stoppa en process som baserat på dess identifierare.</span><span class="sxs-lookup"><span data-stu-id="05251-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="05251-160">I så fall cmdlet: en använder den `ProcessId` parameteruppsättning för att stoppa processen.</span><span class="sxs-lookup"><span data-stu-id="05251-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="05251-161">Med Windows PowerShell igång, kör du cmdleten Stop-processen med den `InputObject` parameteruppsättning stoppa processer på objektet anteckningar som hämtas av den `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="05251-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="05251-162">Se även</span><span class="sxs-lookup"><span data-stu-id="05251-162">See Also</span></span>

[<span data-ttu-id="05251-163">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="05251-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="05251-164">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="05251-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="05251-165">[Utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="05251-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="05251-166">[Hur du registrerar Cmdlets, Providers och vara värd för program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="05251-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="05251-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="05251-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
