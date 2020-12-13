---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till rapportering av fel som avbryter körningen i en cmdlet
description: Lägga till rapportering av fel som avbryter körningen i en cmdlet
ms.openlocfilehash: 883ff2d522266495e409fb0d45f29713baa6f047
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648666"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="65a10-103">Lägga till rapportering av fel som avbryter körningen i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="65a10-103">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="65a10-104">-Cmdletar kan rapportera icke-avslutande fel genom att anropa metoden [system. Management. Automation. cmdlet. WriteError][] och fortfarande fortsätta att använda det aktuella indatamängdet eller på ytterligare inkommande pipelines-objekt.</span><span class="sxs-lookup"><span data-stu-id="65a10-104">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError][] method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="65a10-105">I det här avsnittet beskrivs hur du skapar en-cmdlet som rapporterar att det inte går att avsluta fel från dess metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="65a10-105">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="65a10-106">För att inte avsluta fel (och avsluta fel) måste cmdleten skicka ett [system. Management. Automation. ErrorRecord][] -objekt som identifierar felet.</span><span class="sxs-lookup"><span data-stu-id="65a10-106">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord][] object identifying the error.</span></span> <span data-ttu-id="65a10-107">Varje felpost identifieras av en unik sträng som kallas "fel identifierare".</span><span class="sxs-lookup"><span data-stu-id="65a10-107">Each error record is identified by a unique string called the "error identifier".</span></span> <span data-ttu-id="65a10-108">Förutom identifieraren anges kategorin för varje fel av konstanter som definieras av en [system. Management. Automation. ErrorCategory][] -uppräkning.</span><span class="sxs-lookup"><span data-stu-id="65a10-108">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.ErrorCategory][] enumeration.</span></span> <span data-ttu-id="65a10-109">Användaren kan visa fel baserat på deras kategori genom `$ErrorView` att ange variabeln till "CategoryView".</span><span class="sxs-lookup"><span data-stu-id="65a10-109">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="65a10-110">Mer information om fel poster finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-110">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="65a10-111">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="65a10-111">Defining the Cmdlet</span></span>

<span data-ttu-id="65a10-112">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="65a10-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="65a10-113">Den här cmdleten hämtar process information, så verbet som väljs här är "Get".</span><span class="sxs-lookup"><span data-stu-id="65a10-113">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="65a10-114">(Nästan alla sorters cmdlets som kan hämta information kan bearbeta kommando rads indata.) Mer information om godkända cmdlet-verb finns i [cmdlet-verb](approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-114">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="65a10-115">Följande är definitionen för denna `Get-Proc` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65a10-115">The following is the definition for this `Get-Proc` cmdlet.</span></span> <span data-ttu-id="65a10-116">Information om den här definitionen anges i [skapa din första cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-116">Details of this definition are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="65a10-117">Definiera parametrar</span><span class="sxs-lookup"><span data-stu-id="65a10-117">Defining Parameters</span></span>

<span data-ttu-id="65a10-118">Vid behov måste cmdleten definiera parametrar för att bearbeta indata.</span><span class="sxs-lookup"><span data-stu-id="65a10-118">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="65a10-119">Den här Get-Proc cmdleten definierar en **namn** parameter som beskrivs i [lägga till parametrar som bearbetar Command-Line inmatade](adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-119">This Get-Proc cmdlet defines a **Name** parameter as described in [Adding Parameters that Process Command-Line Input](adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="65a10-120">Här är parameter deklarationen för **namn** parametern för denna Get-Proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65a10-120">Here is the parameter declaration for the **Name** parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="65a10-121">Åsidosätta metoder för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="65a10-121">Overriding Input Processing Methods</span></span>

<span data-ttu-id="65a10-122">Alla cmdletar måste åsidosätta minst en av de metoder för bearbetning av indata som tillhandahålls av klassen [system. Management. Automation. cmdlet][] .</span><span class="sxs-lookup"><span data-stu-id="65a10-122">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet][] class.</span></span> <span data-ttu-id="65a10-123">Dessa metoder beskrivs i [skapa din första cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-123">These methods are discussed in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="65a10-124">Din cmdlet ska hantera varje post så oberoende som möjligt.</span><span class="sxs-lookup"><span data-stu-id="65a10-124">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="65a10-125">Den här Get-Proc cmdleten åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord][] för att hantera **namn** parametern för indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="65a10-125">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord][] method to handle the **Name** parameter for input provided by the user or a script.</span></span> <span data-ttu-id="65a10-126">Med den här metoden hämtas processerna för varje begärt process namn eller alla processer om inget namn anges.</span><span class="sxs-lookup"><span data-stu-id="65a10-126">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="65a10-127">Information om den här åsidosättningen anges i [skapa din första cmdlet](creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-127">Details of this override are given in [Creating Your First Cmdlet](creating-a-cmdlet-without-parameters.md).</span></span>

### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="65a10-128">Saker att komma ihåg när du rapporterar fel</span><span class="sxs-lookup"><span data-stu-id="65a10-128">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="65a10-129">Objektet [system. Management. Automation. ErrorRecord][] som cmdleten skickar när ett fel skrivs måste ha ett undantag i kärnan.</span><span class="sxs-lookup"><span data-stu-id="65a10-129">The [System.Management.Automation.ErrorRecord][] object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="65a10-130">Följ .NET-rikt linjerna när du avgör vilket undantag som ska användas.</span><span class="sxs-lookup"><span data-stu-id="65a10-130">Follow the .NET guidelines when determining the exception to use.</span></span>
<span data-ttu-id="65a10-131">I princip, om felet är semantiskt på samma sätt som ett befintligt undantag, ska cmdlet: en använda eller härleda från det undantaget.</span><span class="sxs-lookup"><span data-stu-id="65a10-131">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="65a10-132">Annars bör den härleda en ny undantags-eller undantags hierarki direkt från [system. Exception][] -klassen.</span><span class="sxs-lookup"><span data-stu-id="65a10-132">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception][] class.</span></span>

<span data-ttu-id="65a10-133">Tänk på följande när du skapar fel identifierare (nås via egenskapen FullyQualifiedErrorId för ErrorRecord-klassen).</span><span class="sxs-lookup"><span data-stu-id="65a10-133">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="65a10-134">Använd strängar som är avsedda för diagnostiska syfte så att när du inspekterar den fullständigt kvalificerade identifieraren kan du fastställa vad felet är och var felet kom från.</span><span class="sxs-lookup"><span data-stu-id="65a10-134">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="65a10-135">En välformulerad fullständigt kvalificerad fel identifierare kan vara följande.</span><span class="sxs-lookup"><span data-stu-id="65a10-135">A well formed fully qualified error identifier might be as follows.</span></span>

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

<span data-ttu-id="65a10-136">Observera att fel identifieraren (den första token) i föregående exempel bestämmer vad felet är och den återstående delen anger var felet kom från.</span><span class="sxs-lookup"><span data-stu-id="65a10-136">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="65a10-137">För mer komplexa scenarier kan fel identifieraren vara en punktavgränsad punktavgränsad token som kan analyseras vid inspektion.</span><span class="sxs-lookup"><span data-stu-id="65a10-137">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="65a10-138">På så sätt kan du för grenar om delar av fel identifieraren samt fel-och fel kategorin.</span><span class="sxs-lookup"><span data-stu-id="65a10-138">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="65a10-139">Cmdleten ska tilldela vissa fel identifierare till olika kod Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="65a10-139">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="65a10-140">Tänk på följande när du ska tilldela fel identifierare:</span><span class="sxs-lookup"><span data-stu-id="65a10-140">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="65a10-141">En fel-ID bör vara konstant under hela cmdlet-livs cykeln.</span><span class="sxs-lookup"><span data-stu-id="65a10-141">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="65a10-142">Ändra inte semantiken för en fel identifierare mellan cmdlet-versioner.</span><span class="sxs-lookup"><span data-stu-id="65a10-142">Do not change the semantics of an error identifier between cmdlet versions.</span></span>
- <span data-ttu-id="65a10-143">Använd texten för en fel identifierare som tersely motsvarar det fel som rapporteras.</span><span class="sxs-lookup"><span data-stu-id="65a10-143">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="65a10-144">Använd inte blank steg eller skiljetecken.</span><span class="sxs-lookup"><span data-stu-id="65a10-144">Do not use white space or punctuation.</span></span>
- <span data-ttu-id="65a10-145">Låt din cmdlet generera endast fel identifierare som är reproducerbara.</span><span class="sxs-lookup"><span data-stu-id="65a10-145">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="65a10-146">Det ska till exempel inte generera en identifierare som innehåller en process identifierare.</span><span class="sxs-lookup"><span data-stu-id="65a10-146">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="65a10-147">Fel identifierare är bara användbara för en användare när de motsvarar identifierare som visas av andra användare som har samma problem.</span><span class="sxs-lookup"><span data-stu-id="65a10-147">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="65a10-148">Ohanterade undantag fångas inte av PowerShell i följande fall:</span><span class="sxs-lookup"><span data-stu-id="65a10-148">Unhandled exceptions are not caught by PowerShell in the following conditions:</span></span>

- <span data-ttu-id="65a10-149">Om en cmdlet skapar en ny tråd och kod som körs i den tråden ger upphov till ett ohanterat undantag, kommer PowerShell inte att fånga fel meddelandet och kommer att avsluta processen.</span><span class="sxs-lookup"><span data-stu-id="65a10-149">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>
- <span data-ttu-id="65a10-150">Om ett objekt har kod i sin destruktorn eller tar bort metoder som orsakar ett ohanterat undantag, kommer PowerShell inte att fånga fel meddelandet och kommer att avsluta processen.</span><span class="sxs-lookup"><span data-stu-id="65a10-150">If an object has code in its destructor or Dispose methods that causes an unhandled exception, PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="65a10-151">Rapportera fel som inte avslutas</span><span class="sxs-lookup"><span data-stu-id="65a10-151">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="65a10-152">Någon av metoderna för bearbetning av indata kan rapportera ett fel som inte kan avslutas till utdataströmmen med hjälp av metoden [system. Management. Automation. cmdlet. WriteError][] .</span><span class="sxs-lookup"><span data-stu-id="65a10-152">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError][] method.</span></span>

<span data-ttu-id="65a10-153">Här är ett kod exempel från den här Get-Proc cmdleten som illustrerar anropet till [system. Management. Automation. cmdlet. WriteError][] inifrån åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord][] .</span><span class="sxs-lookup"><span data-stu-id="65a10-153">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError][] from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord][] method.</span></span> <span data-ttu-id="65a10-154">I det här fallet görs anropet om cmdleten inte kan hitta någon process för en angiven process-ID.</span><span class="sxs-lookup"><span data-stu-id="65a10-154">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="65a10-155">Saker att komma ihåg om att skriva fel som inte avslutas</span><span class="sxs-lookup"><span data-stu-id="65a10-155">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="65a10-156">För ett fel som inte är avslutande måste cmdleten generera en angiven fel identifierare för varje angivet inobjekt.</span><span class="sxs-lookup"><span data-stu-id="65a10-156">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="65a10-157">En cmdlet behöver ofta ändra PowerShell-åtgärden som genereras av ett fel som inte går att avsluta.</span><span class="sxs-lookup"><span data-stu-id="65a10-157">A cmdlet frequently needs to modify the PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="65a10-158">Det kan du göra genom att definiera `ErrorAction` `ErrorVariable` parametrarna och.</span><span class="sxs-lookup"><span data-stu-id="65a10-158">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="65a10-159">Om du definierar `ErrorAction` parametern, visar cmdleten användar alternativen [system. Management. Automation. Åtgärdsinställning][]. du kan också direkt påverka åtgärden genom att ställa in `$ErrorActionPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="65a10-159">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.ActionPreference][], you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="65a10-160">Cmdleten kan spara icke-avslutande fel i en variabel med hjälp av `ErrorVariable` parametern, som inte påverkas av inställningen för `ErrorAction` .</span><span class="sxs-lookup"><span data-stu-id="65a10-160">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="65a10-161">Fel kan läggas till i en befintlig felvariabel genom att lägga till ett plus tecken (+) framför variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="65a10-161">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="65a10-162">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="65a10-162">Code Sample</span></span>

<span data-ttu-id="65a10-163">Den fullständiga exempel koden för C# finns i [GetProcessSample04-exempel](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="65a10-163">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="65a10-164">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="65a10-164">Define Object Types and Formatting</span></span>

<span data-ttu-id="65a10-165">PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="65a10-165">PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="65a10-166">Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="65a10-166">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="65a10-167">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="65a10-167">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="65a10-168">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="65a10-168">Building the Cmdlet</span></span>

<span data-ttu-id="65a10-169">När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="65a10-169">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="65a10-170">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="65a10-170">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="65a10-171">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="65a10-171">Testing the Cmdlet</span></span>

<span data-ttu-id="65a10-172">När din cmdlet har registrerats med PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="65a10-172">When your cmdlet has been registered with PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="65a10-173">Nu ska vi testa exemplet Get-Proc cmdlet för att se om det rapporterar ett fel:</span><span class="sxs-lookup"><span data-stu-id="65a10-173">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="65a10-174">Starta PowerShell och Använd Get-Proc cmdlet för att hämta processerna med namnet "TEST".</span><span class="sxs-lookup"><span data-stu-id="65a10-174">Start PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

  ```powershell
  get-proc -name test
  ```

  <span data-ttu-id="65a10-175">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="65a10-175">The following output appears.</span></span>

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a><span data-ttu-id="65a10-176">Se även</span><span class="sxs-lookup"><span data-stu-id="65a10-176">See Also</span></span>

[<span data-ttu-id="65a10-177">Lägga till parametrar som bearbetar pipelineindata</span><span class="sxs-lookup"><span data-stu-id="65a10-177">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="65a10-178">Lägga till parametrar som bearbetar Command-Line-Indatatyp</span><span class="sxs-lookup"><span data-stu-id="65a10-178">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="65a10-179">Skapa din första cmdlet</span><span class="sxs-lookup"><span data-stu-id="65a10-179">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="65a10-180">[Utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="65a10-180">[Extending Object Types and Formatting](/previous-versions/ms714665(v=vs.85))</span></span>

<span data-ttu-id="65a10-181">[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="65a10-181">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="65a10-182">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="65a10-182">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="65a10-183">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="65a10-183">Cmdlet Samples</span></span>](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System.Exception]: /dotnet/api/System.Exception
[System. Management. Automation. Åtgärdsinställning]: /dotnet/api/System.Management.Automation.ActionPreference
[System.Management.Automation.ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System.Management.Automation.Cmdlet.ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.Management.Automation.Cmdlet.WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System.Management.Automation.Cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.Management.Automation.ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
[System.Management.Automation.ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
