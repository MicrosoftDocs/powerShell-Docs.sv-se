---
title: Lägga till parametrar som bearbetar pipeline-ininformation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: 9ecb73a4138a5853fa5fb378874da2d81c5dbdba
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355645"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="3788e-102">Lägga till parametrar som bearbetar pipelineindata</span><span class="sxs-lookup"><span data-stu-id="3788e-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="3788e-103">En källa för indata för en cmdlet är ett objekt i pipelinen som härstammar från en överordnad cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3788e-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="3788e-104">I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-proc (beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta pipelines-objekt.</span><span class="sxs-lookup"><span data-stu-id="3788e-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="3788e-105">Den här cmdleten Get-proc använder en `Name` parameter som accepterar indata från ett pipeline-objekt, hämtar process information från den lokala datorn baserat på de angivna namnen och visar sedan information om processerna på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="3788e-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="3788e-106">Definiera cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="3788e-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="3788e-107">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3788e-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="3788e-108">Den här cmdleten hämtar process information, så verbet som väljs här är "Get".</span><span class="sxs-lookup"><span data-stu-id="3788e-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="3788e-109">(Nästan alla sorters cmdlets som kan hämta information kan bearbeta kommando rads indata.) Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3788e-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3788e-110">Följande är definitionen för den här cmdleten Get-proc.</span><span class="sxs-lookup"><span data-stu-id="3788e-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="3788e-111">Information om den här definitionen anges i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3788e-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="3788e-112">Definiera ininformation från pipelinen</span><span class="sxs-lookup"><span data-stu-id="3788e-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="3788e-113">I det här avsnittet beskrivs hur du definierar ininformation från pipelinen för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3788e-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="3788e-114">Den här cmdleten Get-proc definierar en egenskap som representerar den `Name` parametern enligt beskrivningen i [lägga till parametrar som bearbetar kommando rads indatatyper](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="3788e-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="3788e-115">(Se avsnittet för allmän information om att deklarera parametrar.)</span><span class="sxs-lookup"><span data-stu-id="3788e-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="3788e-116">Men när en cmdlet måste bearbeta pipeline-inmatade, måste den ha sina parametrar som är kopplade till indatavärden av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="3788e-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="3788e-117">Om du vill göra detta måste du lägga till nyckelordet `ValueFromPipeline` eller lägga till nyckelordet `ValueFromPipelineByProperty` till attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3788e-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="3788e-118">Ange nyckelordet `ValueFromPipeline` om cmdleten har åtkomst till det kompletta indatamängdet.</span><span class="sxs-lookup"><span data-stu-id="3788e-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="3788e-119">Ange `ValueFromPipelineByProperty` om cmdleten har åtkomst till en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="3788e-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="3788e-120">Här är parameter deklarationen för `Name`-parametern för den här cmdleten Get-proc som godkänner pipeline-inmatade.</span><span class="sxs-lookup"><span data-stu-id="3788e-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="3788e-121">I den föregående deklarationen anges `ValueFromPipeline` nyckelordet till `true` så att Windows PowerShell-körningsmiljön binder parametern till det inkommande objektet om objektet är av samma typ som parametern, eller om den kan tvingas till samma typ.</span><span class="sxs-lookup"><span data-stu-id="3788e-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="3788e-122">Nyckelordet `ValueFromPipelineByPropertyName` är också inställt på `true` så att Windows PowerShell-körningsmiljön kontrollerar det inkommande objektet för en `Name`-egenskap.</span><span class="sxs-lookup"><span data-stu-id="3788e-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="3788e-123">Om det inkommande objektet har en sådan egenskap, kommer körningen att binda `Name`-parametern till egenskapen `Name` för det inkommande objektet.</span><span class="sxs-lookup"><span data-stu-id="3788e-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="3788e-124">Inställningen för nyckelordet `ValueFromPipeline` attribut för en parameter prioriteras över inställningen för nyckelordet `ValueFromPipelineByPropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3788e-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3788e-125">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="3788e-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3788e-126">Om cmdleten ska hantera pipeline-indata måste den åsidosätta lämpliga metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="3788e-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="3788e-127">De grundläggande metoderna för indata-bearbetning införs när [du skapar din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3788e-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="3788e-128">Den här cmdleten Get-proc åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att hantera `Name` parameter-indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="3788e-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="3788e-129">Med den här metoden hämtas processerna för varje begärt process namn eller alla processer om inget namn anges.</span><span class="sxs-lookup"><span data-stu-id="3788e-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="3788e-130">Observera att i [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [WriteObject (system. Object, system. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) är utmatnings mekanismen för att skicka utgående objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3788e-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="3788e-131">Den andra parametern för det här anropet, `enumerateCollection`, har ställts in på `true` för att tala om för Windows PowerShell-körningen att räkna upp matrisen med process objekt och skriva en process i taget till kommando raden.</span><span class="sxs-lookup"><span data-stu-id="3788e-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="3788e-132">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="3788e-132">Code Sample</span></span>

<span data-ttu-id="3788e-133">Den fullständiga C# exempel koden finns i [GetProcessSample03-exempel](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3788e-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="3788e-134">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="3788e-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="3788e-135">Windows PowerShell skickar information mellan cmdlets med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="3788e-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="3788e-136">Därför kan en cmdlet behöva definiera en egen typ, eller så kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3788e-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3788e-137">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3788e-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3788e-138">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="3788e-138">Building the Cmdlet</span></span>

<span data-ttu-id="3788e-139">När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="3788e-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3788e-140">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3788e-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3788e-141">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="3788e-141">Testing the Cmdlet</span></span>

<span data-ttu-id="3788e-142">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="3788e-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="3788e-143">Testa till exempel koden för exempel-cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="3788e-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="3788e-144">Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3788e-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="3788e-145">I Windows PowerShell-prompten anger du följande kommandon för att hämta process namnen via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3788e-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="3788e-146">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3788e-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="3788e-147">Ange följande rader för att hämta de process objekt som har en `Name`-egenskap från processerna som kallas "iexplore".</span><span class="sxs-lookup"><span data-stu-id="3788e-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="3788e-148">I det här exemplet används `Get-Process` cmdlet (tillhandahålls av Windows PowerShell) som ett uppströms kommando för att hämta processerna "iexplore".</span><span class="sxs-lookup"><span data-stu-id="3788e-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="3788e-149">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3788e-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="3788e-150">Se även</span><span class="sxs-lookup"><span data-stu-id="3788e-150">See Also</span></span>

[<span data-ttu-id="3788e-151">Lägga till parametrar som bearbetar kommando rads indatatyper</span><span class="sxs-lookup"><span data-stu-id="3788e-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3788e-152">Skapa din första cmdlet</span><span class="sxs-lookup"><span data-stu-id="3788e-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="3788e-153">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3788e-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="3788e-154">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3788e-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="3788e-155">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="3788e-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="3788e-156">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="3788e-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
