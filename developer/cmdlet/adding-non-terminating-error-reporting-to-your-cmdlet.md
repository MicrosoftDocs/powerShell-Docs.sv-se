---
title: 'Att lägga till icke-avslutande fel som rapporterar till cmdlet: | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 3741982f81efa04d8fe7ab448fba5f2fdf4b0c01
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068872"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="627b1-102">Lägga till rapportering av fel som avbryter körningen i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="627b1-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="627b1-103">Cmdlet: ar kan rapportera oändliga fel genom att anropa den [System.Management.Automation.Cmdlet.WriteError][] metod och fortfarande fortsätter att fungera på den aktuella indataobjektet eller på ytterligare inkommande pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="627b1-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span>
<span data-ttu-id="627b1-104">Det här avsnittet beskrivs hur du skapar en cmdlet som rapporterar oändliga fel från dess inkommande bearbetningsmetoder.</span><span class="sxs-lookup"><span data-stu-id="627b1-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="627b1-105">Cmdlet: en måste klara för oändliga fel (samt avslutande fel), en [System.Management.Automation.ErrorRecord][] objekt identifierar felet.</span><span class="sxs-lookup"><span data-stu-id="627b1-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span>
<span data-ttu-id="627b1-106">Varje Felpost identifieras med en unik sträng som kallas ”fel-ID”.</span><span class="sxs-lookup"><span data-stu-id="627b1-106">Each error record is identified by a unique string called the "error identifier".</span></span>
<span data-ttu-id="627b1-107">Förutom identifieraren kategorin för varje fel anges av konstanterna som definieras av en [System.Management.Automation.ErrorCategory][] uppräkning.</span><span class="sxs-lookup"><span data-stu-id="627b1-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span>
<span data-ttu-id="627b1-108">Du kan visa fel baserat på deras kategori genom att ange den `$ErrorView` variabeln ”CategoryView”.</span><span class="sxs-lookup"><span data-stu-id="627b1-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="627b1-109">Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="627b1-110">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="627b1-110">Defining the Cmdlet</span></span>

<span data-ttu-id="627b1-111">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="627b1-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span>
<span data-ttu-id="627b1-112">Denna cmdlet hämtar information om, så verb valt här heter ”hämta”.</span><span class="sxs-lookup"><span data-stu-id="627b1-112">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span>
<span data-ttu-id="627b1-113">(Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-113">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="627b1-114">Följande är definitionen för denna cmdlet Get-processen.</span><span class="sxs-lookup"><span data-stu-id="627b1-114">The following is the definition for this Get-Proc cmdlet.</span></span>
<span data-ttu-id="627b1-115">Information om den här definitionen anges i [skapa din första cmdleten](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-115">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="627b1-116">Definiera parametrar</span><span class="sxs-lookup"><span data-stu-id="627b1-116">Defining Parameters</span></span>

<span data-ttu-id="627b1-117">Om det behövs måste cmdlet: definiera parametrar för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="627b1-117">If necessary, your cmdlet must define parameters for processing input.</span></span>
<span data-ttu-id="627b1-118">Denna cmdlet Get-Proc definierar en **namn** parametern enligt beskrivningen i [att lägga till parametrar som processen Command-Line indata](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-118">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="627b1-119">Här är parameterdeklaration för den **namn** -parametern för denna cmdlet Get-processen.</span><span class="sxs-lookup"><span data-stu-id="627b1-119">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="627b1-120">Åsidosätta indata metoderna</span><span class="sxs-lookup"><span data-stu-id="627b1-120">Overriding Input Processing Methods</span></span>

<span data-ttu-id="627b1-121">Alla cmdlets måste åsidosätta minst en av de indata som bearbetar metoder som tillhandahålls av den [System.Management.Automation.Cmdlet][] klass.</span><span class="sxs-lookup"><span data-stu-id="627b1-121">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span>
<span data-ttu-id="627b1-122">Dessa metoder beskrivs i [skapa din första cmdleten](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-122">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="627b1-123">Cmdlet: bör hantera varje post oberoende som möjligt.</span><span class="sxs-lookup"><span data-stu-id="627b1-123">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="627b1-124">Denna cmdlet Get-procedur åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord][] metod för att hantera den **namn** parameter för indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="627b1-124">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span>
<span data-ttu-id="627b1-125">Den här metoden får processerna för varje begärda processnamn eller alla processer om inget namn anges.</span><span class="sxs-lookup"><span data-stu-id="627b1-125">This method will get the processes for each requested process name or all processes if no name is provided.</span></span>
<span data-ttu-id="627b1-126">Information om den här åsidosättningen anges i [skapa din första cmdleten](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-126">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="627b1-127">Kom ihåg följande när du har rapporterat fel</span><span class="sxs-lookup"><span data-stu-id="627b1-127">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="627b1-128">Den [System.Management.Automation.ErrorRecord][] objekt som cmdleten skickar när du skriver ett fel kräver ett undantag kärnpunkter.</span><span class="sxs-lookup"><span data-stu-id="627b1-128">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span>
<span data-ttu-id="627b1-129">Följ riktlinjerna .NET när du fastställer undantaget att använda.</span><span class="sxs-lookup"><span data-stu-id="627b1-129">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="627b1-130">I praktiken, om felet är från samma som ett befintligt undantag, cmdleten bör använda eller härledd från detta undantag.</span><span class="sxs-lookup"><span data-stu-id="627b1-130">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span>
<span data-ttu-id="627b1-131">I annat fall bör den härleda ett nytt undantag eller undantag hierarki direkt från den [System.Exception][] klass.</span><span class="sxs-lookup"><span data-stu-id="627b1-131">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="627b1-132">Tänk på följande när du skapar fel-ID (öppnas via egenskapen FullyQualifiedErrorId i klassen ErrorRecord).</span><span class="sxs-lookup"><span data-stu-id="627b1-132">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="627b1-133">Använd strängar som är avsedda för diagnostiskt syfte så att vid kontroll av fullständigt kvalificerat ID kan du fastställa vilka felet är och där felet kommer ifrån.</span><span class="sxs-lookup"><span data-stu-id="627b1-133">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="627b1-134">En korrekt formaterad fullständiga fel-ID kan vara på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="627b1-134">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="627b1-135">Observera att i föregående exempel fel-ID (första token) betecknar felet och den återstående delen indikerar var felet kommer ifrån.</span><span class="sxs-lookup"><span data-stu-id="627b1-135">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="627b1-136">Fel-ID kan vara en punkt avgränsade token som kan tolkas i granskning för mer komplicerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="627b1-136">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span>
  <span data-ttu-id="627b1-137">På så sätt kan du för grenen på delar av fel-ID samt felkategori identifierare och fel.</span><span class="sxs-lookup"><span data-stu-id="627b1-137">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="627b1-138">Cmdlet: en ska tilldela specifika fel-ID till olika kodsökvägar.</span><span class="sxs-lookup"><span data-stu-id="627b1-138">The cmdlet should assign specific error identifiers to different code paths.</span></span>
<span data-ttu-id="627b1-139">Tänk på följande information för tilldelning av fel-ID:</span><span class="sxs-lookup"><span data-stu-id="627b1-139">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="627b1-140">En identifierare som fel ska förblir konstant under cmdlet hela livscykel.</span><span class="sxs-lookup"><span data-stu-id="627b1-140">An error identifier should remain constant throughout the cmdlet life cycle.</span></span>
  <span data-ttu-id="627b1-141">Ändra inte semantiken för en identifierare som fel mellan cmdlet-versioner.</span><span class="sxs-lookup"><span data-stu-id="627b1-141">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="627b1-142">Använd text efter ett fel-ID som motsvarar tersely fel har rapporterats.</span><span class="sxs-lookup"><span data-stu-id="627b1-142">Use text for an error identifier that tersely corresponds to the error being reported.</span></span>
  <span data-ttu-id="627b1-143">Använd inte blanksteg eller skiljetecken.</span><span class="sxs-lookup"><span data-stu-id="627b1-143">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="627b1-144">Har din cmdleten som genererar endast fel-ID som är reproducerbar.</span><span class="sxs-lookup"><span data-stu-id="627b1-144">Have your cmdlet generate only error identifiers that are reproducible.</span></span>
  <span data-ttu-id="627b1-145">Den ska till exempel inte skapa en identifierare som innehåller ett process-ID.</span><span class="sxs-lookup"><span data-stu-id="627b1-145">For example, it should not generate an identifier that includes a process identifier.</span></span>
  <span data-ttu-id="627b1-146">Fel-ID är användbara för en användare bara när de motsvarar identifierare som ses av andra användare som upplever samma problem.</span><span class="sxs-lookup"><span data-stu-id="627b1-146">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="627b1-147">Ett ohanterat undantag omfattas inte av PowerShell under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="627b1-147">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="627b1-148">Om en cmdlet skapar en ny tråd och kod som körs i den tråd kastar ett ohanterat undantag, kommer inte att fånga felet PowerShell och kommer att avsluta processen.</span><span class="sxs-lookup"><span data-stu-id="627b1-148">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="627b1-149">Om ett objekt har kod i dess destruktorn eller Dispose metoder som orsakar ett ohanterat undantag, kommer inte att fånga felet PowerShell och kommer att avsluta processen.</span><span class="sxs-lookup"><span data-stu-id="627b1-149">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="627b1-150">Rapportering oändliga fel</span><span class="sxs-lookup"><span data-stu-id="627b1-150">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="627b1-151">Någon av metoderna indata kan rapportera ett oändliga fel i utdata stream med hjälp av den [System.Management.Automation.Cmdlet.WriteError][] metod.</span><span class="sxs-lookup"><span data-stu-id="627b1-151">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="627b1-152">Här är ett exempel från denna cmdlet för Get-processen som illustrerar anropet till [System.Management.Automation.Cmdlet.WriteError][] från inom åsidosättningen av den [System.Management.Automation.Cmdlet.ProcessRecord][] metod.</span><span class="sxs-lookup"><span data-stu-id="627b1-152">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span>
<span data-ttu-id="627b1-153">I det här fallet görs anropet om cmdlet: en inte kan hitta en process för en angiven process-ID.</span><span class="sxs-lookup"><span data-stu-id="627b1-153">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="627b1-154">Kom ihåg följande om hur du skriver oändliga fel</span><span class="sxs-lookup"><span data-stu-id="627b1-154">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="627b1-155">Cmdlet: en måste generera ett specifikt fel-ID för varje specifik indataobjektet för ett oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="627b1-155">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="627b1-156">En cmdlet måste ofta ändrar PowerShell-åtgärden som produceras av en oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="627b1-156">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span>
<span data-ttu-id="627b1-157">Det kan göra detta genom att definiera den `ErrorAction` och `ErrorVariable` parametrar.</span><span class="sxs-lookup"><span data-stu-id="627b1-157">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span>
<span data-ttu-id="627b1-158">Om definierar den `ErrorAction` parametern cmdlet: en anger användaralternativen [System.Management.Automation.ActionPreference][], du kan också direkt påverka åtgärden genom att ange den `$ErrorActionPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="627b1-158">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="627b1-159">Cmdlet: en kan spara oändliga fel i en variabel med det `ErrorVariable` parametern, som inte påverkas av inställningen för `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="627b1-159">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span>
<span data-ttu-id="627b1-160">Fel kan läggas till en befintlig variabel fel genom att lägga till ett plustecken (+) framför variabelnamnet.</span><span class="sxs-lookup"><span data-stu-id="627b1-160">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="627b1-161">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="627b1-161">Code Sample</span></span>

<span data-ttu-id="627b1-162">För hela C# exempelkoden, se [GetProcessSample04 exempel](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="627b1-162">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="627b1-163">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="627b1-163">Define Object Types and Formatting</span></span>

<span data-ttu-id="627b1-164">PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="627b1-164">PowerShell passes information between cmdlets using .NET objects.</span></span>
<span data-ttu-id="627b1-165">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="627b1-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span>
<span data-ttu-id="627b1-166">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="627b1-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="627b1-167">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="627b1-167">Building the Cmdlet</span></span>

<span data-ttu-id="627b1-168">När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="627b1-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span>
<span data-ttu-id="627b1-169">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="627b1-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="627b1-170">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="627b1-170">Testing the Cmdlet</span></span>

<span data-ttu-id="627b1-171">När din cmdlet har registrerats med PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="627b1-171">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span>
<span data-ttu-id="627b1-172">Nu ska vi testa exempel Get-Proc-cmdlet för att se om den rapporterar ett fel:</span><span class="sxs-lookup"><span data-stu-id="627b1-172">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="627b1-173">Starta PowerShell och Använd cmdleten Get-processen för att hämta processer med namnet ”TEST”.</span><span class="sxs-lookup"><span data-stu-id="627b1-173">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="627b1-174">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="627b1-174">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="627b1-175">Se även</span><span class="sxs-lookup"><span data-stu-id="627b1-175">See Also</span></span>

[<span data-ttu-id="627b1-176">Att lägga till parametrar som indata för Process-pipelinen</span><span class="sxs-lookup"><span data-stu-id="627b1-176">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="627b1-177">Att lägga till parametrar som bearbetar av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="627b1-177">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="627b1-178">Skapa din första cmdlet:</span><span class="sxs-lookup"><span data-stu-id="627b1-178">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="627b1-179">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="627b1-179">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="627b1-180">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="627b1-180">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="627b1-181">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="627b1-181">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="627b1-182">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="627b1-182">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
