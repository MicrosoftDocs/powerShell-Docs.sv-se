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
ms.openlocfilehash: e0550dacc33f45f45ba105ca5cb4d2e5b5d675fb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056064"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a><span data-ttu-id="e78bb-102">Lägga till rapportering av fel som avbryter körningen i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="e78bb-102">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>

<span data-ttu-id="e78bb-103">Cmdlet: ar kan rapportera oändliga fel genom att anropa den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod och fortfarande fortsätter att fungera på den aktuella indataobjektet eller på ytterligare inkommande pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="e78bb-103">Cmdlets can report nonterminating errors by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method and still continue to operate on the current input object or on further incoming pipeline objects.</span></span> <span data-ttu-id="e78bb-104">Det här avsnittet beskrivs hur du skapar en cmdlet som rapporterar oändliga fel från dess inkommande bearbetningsmetoder.</span><span class="sxs-lookup"><span data-stu-id="e78bb-104">This section explains how to create a cmdlet that reports nonterminating errors from its input processing methods.</span></span>

<span data-ttu-id="e78bb-105">Cmdlet: en måste klara för oändliga fel (samt avslutande fel), en [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt identifierar felet.</span><span class="sxs-lookup"><span data-stu-id="e78bb-105">For nonterminating errors (as well as terminating errors), the cmdlet must pass an [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object identifying the error.</span></span> <span data-ttu-id="e78bb-106">Varje Felpost identifieras med en unik sträng som kallas ”fel identifierare”.</span><span class="sxs-lookup"><span data-stu-id="e78bb-106">Each error record is identified by a unique string called the "error identifier."</span></span> <span data-ttu-id="e78bb-107">Förutom identifieraren kategorin för varje fel anges av konstanterna som definieras av en [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) uppräkning.</span><span class="sxs-lookup"><span data-stu-id="e78bb-107">In addition to the identifier, the category of each error is specified by constants defined by a [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="e78bb-108">Du kan visa fel baserat på deras kategori genom att ange den `$ErrorView` variabeln ”CategoryView”.</span><span class="sxs-lookup"><span data-stu-id="e78bb-108">The user can view errors based on their category by setting the `$ErrorView` variable to "CategoryView".</span></span>

<span data-ttu-id="e78bb-109">Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-109">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="e78bb-110">Ämnena i det här avsnittet omfattar följande:</span><span class="sxs-lookup"><span data-stu-id="e78bb-110">Topics in this section include the following:</span></span>

- [<span data-ttu-id="e78bb-111">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="e78bb-111">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="e78bb-112">Definiera parametrar</span><span class="sxs-lookup"><span data-stu-id="e78bb-112">Defining Parameters</span></span>](#Defining-Parameters)

- [<span data-ttu-id="e78bb-113">Åsidosätta indata metoderna</span><span class="sxs-lookup"><span data-stu-id="e78bb-113">Overriding Input Processing Methods</span></span>](#Overriding-Input-Processing-Methods)

- [<span data-ttu-id="e78bb-114">Rapportering oändliga fel</span><span class="sxs-lookup"><span data-stu-id="e78bb-114">Reporting Nonterminating Errors</span></span>](#Reporting-Nonterminating-Errors)

- [<span data-ttu-id="e78bb-115">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="e78bb-115">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="e78bb-116">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="e78bb-116">Defining Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="e78bb-117">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e78bb-117">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="e78bb-118">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e78bb-118">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="e78bb-119">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="e78bb-119">Defining the Cmdlet</span></span>

<span data-ttu-id="e78bb-120">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e78bb-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e78bb-121">Denna cmdlet hämtar information om, så verb valt här heter ”hämta”.</span><span class="sxs-lookup"><span data-stu-id="e78bb-121">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="e78bb-122">(Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-122">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e78bb-123">Följande är definitionen för denna cmdlet Get-processen.</span><span class="sxs-lookup"><span data-stu-id="e78bb-123">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="e78bb-124">Information om den här definitionen anges i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-124">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a><span data-ttu-id="e78bb-125">Definiera parametrar</span><span class="sxs-lookup"><span data-stu-id="e78bb-125">Defining Parameters</span></span>

<span data-ttu-id="e78bb-126">Om det behövs måste cmdlet: definiera parametrar för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="e78bb-126">If necessary, your cmdlet must define parameters for processing input.</span></span> <span data-ttu-id="e78bb-127">Denna cmdlet Get-Proc definierar en `Name` parametern enligt beskrivningen i [att lägga till parametrar som processen Command-Line indata](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-127">This Get-Proc cmdlet defines a `Name` parameter as described in [Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

<span data-ttu-id="e78bb-128">Här är parameterdeklaration för den `Name` -parametern för denna cmdlet Get-processen.</span><span class="sxs-lookup"><span data-stu-id="e78bb-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet.</span></span>

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

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="e78bb-129">Åsidosätta indata metoderna</span><span class="sxs-lookup"><span data-stu-id="e78bb-129">Overriding Input Processing Methods</span></span>

<span data-ttu-id="e78bb-130">Alla cmdlets måste åsidosätta minst en av de indata som bearbetar metoder som tillhandahålls av den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass.</span><span class="sxs-lookup"><span data-stu-id="e78bb-130">All cmdlets must override at least one of the input processing methods provided by the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="e78bb-131">Dessa metoder beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-131">These methods are discussed in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e78bb-132">Cmdlet: bör hantera varje post oberoende som möjligt.</span><span class="sxs-lookup"><span data-stu-id="e78bb-132">Your cmdlet should handle each record as independently as possible.</span></span>

<span data-ttu-id="e78bb-133">Denna cmdlet Get-procedur åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att hantera den `Name` parameter för indata från användaren eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="e78bb-133">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter for input provided by the user or a script.</span></span> <span data-ttu-id="e78bb-134">Den här metoden får processerna för varje begärda processnamn eller alla processer om inget namn anges.</span><span class="sxs-lookup"><span data-stu-id="e78bb-134">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="e78bb-135">Information om den här åsidosättningen anges i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-135">Details of this override are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

#### <a name="things-to-remember-when-reporting-errors"></a><span data-ttu-id="e78bb-136">Kom ihåg följande när du har rapporterat fel</span><span class="sxs-lookup"><span data-stu-id="e78bb-136">Things to Remember When Reporting Errors</span></span>

<span data-ttu-id="e78bb-137">Den [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt som cmdleten skickar när du skriver ett fel kräver ett undantag kärnpunkter.</span><span class="sxs-lookup"><span data-stu-id="e78bb-137">The [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) object that the cmdlet passes when writing an error requires an exception at its core.</span></span> <span data-ttu-id="e78bb-138">Följ riktlinjerna .NET när du fastställer undantaget att använda.</span><span class="sxs-lookup"><span data-stu-id="e78bb-138">Follow the .NET guidelines when determining the exception to use.</span></span> <span data-ttu-id="e78bb-139">I praktiken, om felet är från samma som ett befintligt undantag, cmdleten bör använda eller härledd från detta undantag.</span><span class="sxs-lookup"><span data-stu-id="e78bb-139">Basically, if the error is semantically the same as an existing exception, the cmdlet should use or derive from that exception.</span></span> <span data-ttu-id="e78bb-140">I annat fall bör den härleda ett nytt undantag eller undantag hierarki direkt från den [System.Exception](/dotnet/api/System.Exception) klass.</span><span class="sxs-lookup"><span data-stu-id="e78bb-140">Otherwise, it should derive a new exception or exception hierarchy directly from the [System.Exception](/dotnet/api/System.Exception) class.</span></span>

<span data-ttu-id="e78bb-141">Tänk på följande när du skapar fel-ID (öppnas via egenskapen FullyQualifiedErrorId i klassen ErrorRecord).</span><span class="sxs-lookup"><span data-stu-id="e78bb-141">When creating error identifiers (accessed through the FullyQualifiedErrorId property of the ErrorRecord class) keep the following in mind.</span></span>

- <span data-ttu-id="e78bb-142">Använd strängar som är avsedda för diagnostiskt syfte så att vid kontroll av fullständigt kvalificerat ID kan du fastställa vilka felet är och där felet kommer ifrån.</span><span class="sxs-lookup"><span data-stu-id="e78bb-142">Use strings that are targeted for diagnostic purposes so that when inspecting the fully qualified identifier you can determine what the error is and where the error came from.</span></span>

- <span data-ttu-id="e78bb-143">En korrekt formaterad fullständiga fel-ID kan vara på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="e78bb-143">A well formed fully qualified error identifier might be as follows.</span></span>

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

<span data-ttu-id="e78bb-144">Observera att i föregående exempel fel-ID (första token) betecknar felet och den återstående delen indikerar var felet kommer ifrån.</span><span class="sxs-lookup"><span data-stu-id="e78bb-144">Notice that in the previous example, the error identifier (the first token) designates what the error is and the remaining part indicates where the error came from.</span></span>

- <span data-ttu-id="e78bb-145">Fel-ID kan vara en punkt avgränsade token som kan tolkas i granskning för mer komplicerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="e78bb-145">For more complex scenarios, the error identifier can be a dot separated token that can be parsed on inspection.</span></span> <span data-ttu-id="e78bb-146">På så sätt kan du för grenen på delar av fel-ID samt felkategori identifierare och fel.</span><span class="sxs-lookup"><span data-stu-id="e78bb-146">This allows you too branch on the parts of the error identifier as well as the error identifier and error category.</span></span>

<span data-ttu-id="e78bb-147">Cmdlet: en ska tilldela specifika fel-ID till olika kodsökvägar.</span><span class="sxs-lookup"><span data-stu-id="e78bb-147">The cmdlet should assign specific error identifiers to different code paths.</span></span> <span data-ttu-id="e78bb-148">Tänk på följande information för tilldelning av fel-ID:</span><span class="sxs-lookup"><span data-stu-id="e78bb-148">Keep the following information in mind for assignment of error identifiers:</span></span>

- <span data-ttu-id="e78bb-149">En identifierare som fel ska förblir konstant under cmdlet hela livscykel.</span><span class="sxs-lookup"><span data-stu-id="e78bb-149">An error identifier should remain constant throughout the cmdlet life cycle.</span></span> <span data-ttu-id="e78bb-150">Ändra inte semantiken för en identifierare som fel mellan cmdlet-versioner.</span><span class="sxs-lookup"><span data-stu-id="e78bb-150">Do not change the semantics of an error identifier between cmdlet versions.</span></span>

- <span data-ttu-id="e78bb-151">Använd text efter ett fel-ID som motsvarar tersely fel har rapporterats.</span><span class="sxs-lookup"><span data-stu-id="e78bb-151">Use text for an error identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="e78bb-152">Använd inte blanksteg eller skiljetecken.</span><span class="sxs-lookup"><span data-stu-id="e78bb-152">Do not use white space or punctuation.</span></span>

- <span data-ttu-id="e78bb-153">Har din cmdleten som genererar endast fel-ID som är reproducerbar.</span><span class="sxs-lookup"><span data-stu-id="e78bb-153">Have your cmdlet generate only error identifiers that are reproducible.</span></span> <span data-ttu-id="e78bb-154">Den ska till exempel inte skapa en identifierare som innehåller ett process-ID.</span><span class="sxs-lookup"><span data-stu-id="e78bb-154">For example, it should not generate an identifier that includes a process identifier.</span></span> <span data-ttu-id="e78bb-155">Fel-ID är användbara för en användare bara när de motsvarar identifierare som ses av andra användare som upplever samma problem.</span><span class="sxs-lookup"><span data-stu-id="e78bb-155">Error identifiers are useful to a user only when they correspond to identifiers that are seen by other users experiencing the same problem.</span></span>

<span data-ttu-id="e78bb-156">Ett ohanterat undantag omfattas inte av Windows PowerShell under följande förhållanden:</span><span class="sxs-lookup"><span data-stu-id="e78bb-156">Unhandled exceptions are not caught by Windows PowerShell in the following conditions:</span></span>

- <span data-ttu-id="e78bb-157">Om en cmdlet skapar en ny tråd och kod som körs i den tråd kastar ett ohanterat undantag, kommer inte att fånga felet Windows PowerShell och kommer att avsluta processen.</span><span class="sxs-lookup"><span data-stu-id="e78bb-157">If a cmdlet creates a new thread and code running in that thread throws an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

- <span data-ttu-id="e78bb-158">Om ett objekt har kod i dess destruktorn eller Dispose metoder som orsakar ett ohanterat undantag, kommer inte att fånga felet i Windows PowerShell och kommer att avsluta processen.</span><span class="sxs-lookup"><span data-stu-id="e78bb-158">If an object has code in its destructor or Dispose methods that causes an unhandled exception, Windows PowerShell will not catch the error and will terminate the process.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="e78bb-159">Rapportering oändliga fel</span><span class="sxs-lookup"><span data-stu-id="e78bb-159">Reporting Nonterminating Errors</span></span>

<span data-ttu-id="e78bb-160">Någon av metoderna indata kan rapportera ett oändliga fel i utdata stream med hjälp av den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod.</span><span class="sxs-lookup"><span data-stu-id="e78bb-160">Any one of the input processing methods can report a nonterminating error to the output stream using the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="e78bb-161">Här är ett exempel från denna cmdlet för Get-processen som illustrerar anropet till [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från inom åsidosättningen av den [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="e78bb-161">Here is a code example from this Get-Proc cmdlet that illustrates the call to [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="e78bb-162">I det här fallet görs anropet om cmdlet: en inte kan hitta en process för en angiven process-ID.</span><span class="sxs-lookup"><span data-stu-id="e78bb-162">In this case, the call is made if the cmdlet cannot find a process for a specified process identifier.</span></span>

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a><span data-ttu-id="e78bb-163">Kom ihåg följande om hur du skriver oändliga fel</span><span class="sxs-lookup"><span data-stu-id="e78bb-163">Things to Remember About Writing Nonterminating Errors</span></span>

<span data-ttu-id="e78bb-164">Cmdlet: en måste generera ett specifikt fel-ID för varje specifik indataobjektet för ett oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="e78bb-164">For a nonterminating error, the cmdlet must generate a specific error identifier for each specific input object.</span></span>

<span data-ttu-id="e78bb-165">En cmdlet måste ofta ändrar Windows PowerShell-åtgärden som produceras av en oändliga fel.</span><span class="sxs-lookup"><span data-stu-id="e78bb-165">A cmdlet frequently needs to modify the Windows PowerShell action produced by a nonterminating error.</span></span> <span data-ttu-id="e78bb-166">Det kan göra detta genom att definiera den `ErrorAction` och `ErrorVariable` parametrar.</span><span class="sxs-lookup"><span data-stu-id="e78bb-166">It can do this by defining the `ErrorAction` and `ErrorVariable` parameters.</span></span> <span data-ttu-id="e78bb-167">Om definierar den `ErrorAction` parametern cmdlet: en anger användaralternativen [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), du kan också direkt påverka åtgärden genom att ange den `$ErrorActionPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e78bb-167">If defining the `ErrorAction` parameter, the cmdlet presents the user options [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), you can also directly influence the action by setting the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="e78bb-168">Cmdlet: en kan spara oändliga fel i en variabel med det `ErrorVariable` parametern, som inte påverkas av inställningen för `ErrorAction`.</span><span class="sxs-lookup"><span data-stu-id="e78bb-168">The cmdlet can save nonterminating errors to a variable using the `ErrorVariable` parameter, which is not affected by the setting of `ErrorAction`.</span></span> <span data-ttu-id="e78bb-169">Fel kan läggas till en befintlig variabel fel genom att lägga till ett plustecken (+) framför variabelnamnet.</span><span class="sxs-lookup"><span data-stu-id="e78bb-169">Failures can be appended to an existing error variable by adding a plus sign (+) to the front of the variable name.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e78bb-170">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="e78bb-170">Code Sample</span></span>

<span data-ttu-id="e78bb-171">För hela C# exempelkoden, se [GetProcessSample04 exempel](./getprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e78bb-171">For the complete C# sample code, see [GetProcessSample04 Sample](./getprocesssample04-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="e78bb-172">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="e78bb-172">Define Object Types and Formatting</span></span>

<span data-ttu-id="e78bb-173">Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="e78bb-173">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="e78bb-174">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78bb-174">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="e78bb-175">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="e78bb-175">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="e78bb-176">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e78bb-176">Building the Cmdlet</span></span>

<span data-ttu-id="e78bb-177">När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="e78bb-177">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e78bb-178">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="e78bb-178">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e78bb-179">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e78bb-179">Testing the Cmdlet</span></span>

<span data-ttu-id="e78bb-180">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="e78bb-180">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e78bb-181">Nu ska vi testa exempel Get-Proc-cmdlet för att se om den rapporterar ett fel:</span><span class="sxs-lookup"><span data-stu-id="e78bb-181">Let's test the sample Get-Proc cmdlet to see whether it reports an error:</span></span>

- <span data-ttu-id="e78bb-182">Starta Windows PowerShell och Använd cmdleten Get-processen för att hämta processer med namnet ”TEST”.</span><span class="sxs-lookup"><span data-stu-id="e78bb-182">Start Windows PowerShell, and use the Get-Proc cmdlet to retrieve the processes named "TEST".</span></span>

    ```powershell
    PS> get-proc -name test
    ```

<span data-ttu-id="e78bb-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e78bb-183">The following output appears.</span></span>

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a><span data-ttu-id="e78bb-184">Se även</span><span class="sxs-lookup"><span data-stu-id="e78bb-184">See Also</span></span>

[<span data-ttu-id="e78bb-185">Att lägga till parametrar som indata för Process-pipelinen</span><span class="sxs-lookup"><span data-stu-id="e78bb-185">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="e78bb-186">Att lägga till parametrar som bearbetar av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="e78bb-186">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="e78bb-187">Skapa din första cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e78bb-187">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="e78bb-188">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="e78bb-188">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="e78bb-189">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="e78bb-189">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="e78bb-190">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="e78bb-190">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="e78bb-191">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="e78bb-191">Cmdlet Samples</span></span>](./cmdlet-samples.md)
