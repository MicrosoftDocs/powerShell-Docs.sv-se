---
title: Att lägga till parametrar som bearbetar indata från Pipeline | Microsoft Docs
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
ms.openlocfilehash: 34643d20c16f8cc45e7fb20dc2a87d78b18bbf10
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298632"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="53646-102">Lägga till parametrar som bearbetar pipelineindata</span><span class="sxs-lookup"><span data-stu-id="53646-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="53646-103">En källa för indata för en cmdlet är ett objekt till pipelinen som kommer från en överordnad-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53646-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="53646-104">Det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta pipelineobjekt.</span><span class="sxs-lookup"><span data-stu-id="53646-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="53646-105">Denna cmdlet Get-processen använder en `Name` parameter som godkänner indata från ett pipeline-objekt, hämtar information om från den lokala datorn baserat på angivna namnen och visar information om processerna på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="53646-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="53646-106">Definiera klassen Cmdlet</span><span class="sxs-lookup"><span data-stu-id="53646-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="53646-107">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="53646-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="53646-108">Denna cmdlet hämtar information om, så verb valt här heter ”hämta”.</span><span class="sxs-lookup"><span data-stu-id="53646-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="53646-109">(Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="53646-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="53646-110">Följande är definitionen för denna cmdlet Get-processen.</span><span class="sxs-lookup"><span data-stu-id="53646-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="53646-111">Information om den här definitionen anges i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="53646-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="53646-112">Definiera indata från Pipeline</span><span class="sxs-lookup"><span data-stu-id="53646-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="53646-113">Det här avsnittet beskriver hur du definierar indata från pipeline för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53646-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="53646-114">Denna cmdlet Get-Proc definierar en egenskap som representerar den `Name` parametern enligt beskrivningen i [att lägga till parametrar som processen kommandoraden indata](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="53646-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="53646-115">(Se avsnittet allmän information om deklarerar parametrar.)</span><span class="sxs-lookup"><span data-stu-id="53646-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="53646-116">När en cmdlet behöver bearbeta indata från pipeline, måste den ha dess parametrar som är bunden till indatavärden av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="53646-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="53646-117">Om du vill göra detta måste du lägga till den `ValueFromPipeline` nyckelord eller lägga till den `ValueFromPipelineByProperty` nyckelord till den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet deklaration.</span><span class="sxs-lookup"><span data-stu-id="53646-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="53646-118">Ange den `ValueFromPipeline` nyckelordet om cmdlet: en har åtkomst till den fullständiga indataobjektet.</span><span class="sxs-lookup"><span data-stu-id="53646-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="53646-119">Ange den `ValueFromPipelineByProperty` om cmdlet: en hämtar bara en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="53646-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="53646-120">Här är parameterdeklaration för den `Name` -parametern för denna Get-Proc-cmdlet som accepterar pipeline-indata.</span><span class="sxs-lookup"><span data-stu-id="53646-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

<span data-ttu-id="53646-121">Föregående deklarationen anger den `ValueFromPipeline` nyckelord till `true` så att Windows PowerShell-runtime Binder parametern till det inkommande objektet om objektet är av samma typ som parameter, eller om den kan tvingas till samma typ.</span><span class="sxs-lookup"><span data-stu-id="53646-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="53646-122">Den `ValueFromPipelineByPropertyName` nyckelordet anges också `true` så att Windows PowerShell-runtime kommer att kontrollera inkommande objekt för en `Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="53646-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="53646-123">Om inkommande objekt har sådan egenskap, körningen Binder den `Name` parametern till den `Name` egenskap hos det inkommande objektet.</span><span class="sxs-lookup"><span data-stu-id="53646-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="53646-124">Inställningen för den `ValueFromPipeline` attributet nyckelord för en parameter har företräde framför inställningen för den `ValueFromPipelineByPropertyName` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="53646-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="53646-125">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="53646-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="53646-126">Om din cmdlet är att hantera indata från pipeline, måste den åsidosätta lämplig in metoderna.</span><span class="sxs-lookup"><span data-stu-id="53646-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="53646-127">Grundläggande inkommande bearbetningsmetoder som introduceras i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="53646-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="53646-128">Denna cmdlet Get-procedur åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att hantera den `Name` parametern indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="53646-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="53646-129">Den här metoden får processerna för varje begärda processnamn eller alla processer om inget namn anges.</span><span class="sxs-lookup"><span data-stu-id="53646-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="53646-130">Observera att [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) utdata-mekanism för att skicka utdata objekt till den pipeline.</span><span class="sxs-lookup"><span data-stu-id="53646-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="53646-131">Den andra parametern för det här anropet `enumerateCollection`, är inställd på `true` som talar om Windows PowerShell-körning för att räkna upp processen objektmatris och skriva en process i taget till kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="53646-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="53646-132">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="53646-132">Code Sample</span></span>

<span data-ttu-id="53646-133">För hela C# exempelkoden, se [GetProcessSample03 exempel](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="53646-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="53646-134">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="53646-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="53646-135">Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="53646-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="53646-136">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53646-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="53646-137">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="53646-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="53646-138">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="53646-138">Building the Cmdlet</span></span>

<span data-ttu-id="53646-139">Efter tillämpning av en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="53646-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="53646-140">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="53646-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="53646-141">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="53646-141">Testing the Cmdlet</span></span>

<span data-ttu-id="53646-142">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="53646-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="53646-143">Till exempel testa koden för exempel-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53646-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="53646-144">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="53646-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="53646-145">Ange följande kommandon för att hämta processnamn genom pipelinen i Windows PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="53646-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="53646-146">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="53646-146">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="53646-147">Ange följande rader för att få process-objekt som har en `Name` egenskap från de processer som kallas ”IEXPLORE”.</span><span class="sxs-lookup"><span data-stu-id="53646-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="53646-148">Det här exemplet används den `Get-Process` cmdlet (som anges av Windows PowerShell) som en överordnad kommando för att hämta ”IEXPLORE”-processer.</span><span class="sxs-lookup"><span data-stu-id="53646-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="53646-149">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="53646-149">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="53646-150">Se även</span><span class="sxs-lookup"><span data-stu-id="53646-150">See Also</span></span>

[<span data-ttu-id="53646-151">Att lägga till parametrar som bearbetning av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="53646-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="53646-152">Skapa din första cmdlet:</span><span class="sxs-lookup"><span data-stu-id="53646-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="53646-153">[Utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="53646-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="53646-154">[Hur du registrerar Cmdlets, Providers och vara värd för program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="53646-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="53646-155">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="53646-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="53646-156">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="53646-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
