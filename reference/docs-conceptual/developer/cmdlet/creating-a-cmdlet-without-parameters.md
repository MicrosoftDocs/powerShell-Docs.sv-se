---
title: Skapa en cmdlet utan parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415668"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="80720-102">Skapa en cmdlet utan parametrar</span><span class="sxs-lookup"><span data-stu-id="80720-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="80720-103">I det här avsnittet beskrivs hur du skapar en-cmdlet som hämtar information från den lokala datorn utan att använda parametrar, och sedan skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="80720-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="80720-104">Den cmdlet som beskrivs här är en get-proc-cmdlet som hämtar information om processerna på den lokala datorn och sedan visar informationen på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="80720-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="80720-105">Tänk på att när du skriver cmdlets, kommer Windows PowerShell-® referens sammansättningarna att hämtas till disken (som standard på C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="80720-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="80720-106">De installeras inte i GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="80720-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="80720-107">Namnge cmdleten</span><span class="sxs-lookup"><span data-stu-id="80720-107">Naming the Cmdlet</span></span>

<span data-ttu-id="80720-108">Ett cmdlet-namn består av ett verb som anger vilken åtgärd som cmdleten tar och ett substantiv som anger vilka objekt som cmdleten agerar på.</span><span class="sxs-lookup"><span data-stu-id="80720-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="80720-109">Eftersom den här exempel cmdleten Get-proc hämtar process objekt, används verbet "Get", som definieras av [system. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -uppräkningen och Substantiv "proc" för att indikera att cmdleten fungerar på process objekt.</span><span class="sxs-lookup"><span data-stu-id="80720-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="80720-110">När du namnger cmdletar ska du inte använda något av följande tecken: #, () {} [] &-/\ $; : "' < > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="80720-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="80720-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="80720-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="80720-112">Välja ett substantiv</span><span class="sxs-lookup"><span data-stu-id="80720-112">Choosing a Noun</span></span>

<span data-ttu-id="80720-113">Du bör välja ett substantiv som är speciellt.</span><span class="sxs-lookup"><span data-stu-id="80720-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="80720-114">Det är bäst att använda en singularisk substantiv med en förkortad version av produkt namnet.</span><span class="sxs-lookup"><span data-stu-id="80720-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="80720-115">Ett exempel på ett cmdlet-namn av den här typen är "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="80720-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="80720-116">Välja ett verb</span><span class="sxs-lookup"><span data-stu-id="80720-116">Choosing a Verb</span></span>

<span data-ttu-id="80720-117">Du bör använda ett verb från uppsättningen godkända cmdlet-verb.</span><span class="sxs-lookup"><span data-stu-id="80720-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="80720-118">Mer information om godkända cmdlet-verb finns i cmdlet- [verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="80720-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="80720-119">Definiera cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="80720-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="80720-120">När du har valt ett cmdlet-namn definierar du en .NET-klass för att implementera cmdleten.</span><span class="sxs-lookup"><span data-stu-id="80720-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="80720-121">Här är klass definitionen för det här exemplet get-proc-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="80720-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="80720-122">Observera att föregående till klass definitionen, attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , med syntaxen `[Cmdlet(verb, noun, ...)]`, används för att identifiera den här klassen som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80720-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="80720-123">Detta är det enda obligatoriska attributet för alla cmdletar, och det gör att Windows PowerShell-körningsmiljön kan anropa dem korrekt.</span><span class="sxs-lookup"><span data-stu-id="80720-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="80720-124">Du kan ange nyckelord för attribut för att ytterligare deklarera klassen om det behövs.</span><span class="sxs-lookup"><span data-stu-id="80720-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="80720-125">Tänk på att attributet deklaration för vår exempel-GetProcCommand klass endast deklarerar Substantiv-och verben för Get-proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="80720-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="80720-126">För alla klasser för Windows PowerShell-attribut är de nyckelord som du kan ange motsvarar egenskaperna för klassen Attribute.</span><span class="sxs-lookup"><span data-stu-id="80720-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="80720-127">När du namnger klassen för cmdleten är det en bra idé att spegla cmdlet-namnet i klass namnet.</span><span class="sxs-lookup"><span data-stu-id="80720-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="80720-128">Det gör du genom att använda formatet "VerbNounCommand" och ersätta "verb" och "substantiv" med verbet och substantiv som används i cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="80720-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="80720-129">Som det visas i den föregående klass definitionen definierar cmdleten Get-proc en klass med namnet GetProcCommand, som härleds från Bask Lassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="80720-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80720-130">Om du vill definiera en cmdlet som ansluter till Windows PowerShell-körningen direkt ska din .NET-klass härledas från Bask Lassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="80720-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="80720-131">Mer information om den här klassen finns i [skapa en cmdlet som definierar parameter uppsättningar](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="80720-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="80720-132">Klassen för en cmdlet måste markeras explicit som offentlig.</span><span class="sxs-lookup"><span data-stu-id="80720-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="80720-133">Klasser som inte är markerade som offentliga kommer att standardvärdet internt och hittas inte av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="80720-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="80720-134">Windows PowerShell använder namn området [Microsoft. PowerShell. commands](/dotnet/api/Microsoft.PowerShell.Commands) för dess cmdlet-klasser.</span><span class="sxs-lookup"><span data-stu-id="80720-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="80720-135">Vi rekommenderar att du placerar dina cmdlet-klasser i ett kommandon namnrymd för API-namnrymden, till exempel xxx. PS. commands.</span><span class="sxs-lookup"><span data-stu-id="80720-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="80720-136">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="80720-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="80720-137">Klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) tillhandahåller tre huvudsakliga metoder för bearbetning av indata, minst en av vilka din cmdlet måste åsidosätta.</span><span class="sxs-lookup"><span data-stu-id="80720-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="80720-138">Mer information om hur Windows PowerShell bearbetar poster finns i [hur Windows PowerShell fungerar](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="80720-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="80720-139">För alla typer av indata anropar Windows PowerShell-körningen [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för att aktivera bearbetning.</span><span class="sxs-lookup"><span data-stu-id="80720-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="80720-140">Om din cmdlet måste utföra vissa förbehandlingar eller inställningar kan det göra detta genom att åsidosätta den här metoden.</span><span class="sxs-lookup"><span data-stu-id="80720-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="80720-141">Windows PowerShell använder termen "Record" för att beskriva den uppsättning parameter värden som anges när en cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="80720-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="80720-142">Om din cmdlet accepterar pipeline-inmatade måste den åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och eventuellt metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="80720-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="80720-143">En cmdlet kan till exempel åsidosätta båda metoderna om den samlar in alla ininformation med hjälp av [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och sedan arbetar med inmatat i stället för ett element i taget, som `Sort-Object` cmdleten gör.</span><span class="sxs-lookup"><span data-stu-id="80720-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="80720-144">Om cmdleten inte tar emot pipelinen bör den åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="80720-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="80720-145">Tänk på att den här metoden ofta används i stället för [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) när cmdleten inte kan köras på ett element i taget, vilket är fallet för en sorterings-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80720-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="80720-146">Eftersom den här exempel cmdleten Get-proc måste ta emot pipeline-inmatade objekt, åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och använder standard implementeringarna för [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="80720-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="80720-147">Åsidosättningen [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) hämtar processer och skriver dem till kommando raden med hjälp av metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .</span><span class="sxs-lookup"><span data-stu-id="80720-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="80720-148">Saker att komma ihåg om bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="80720-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="80720-149">Standard källan för indata är ett explicit objekt (till exempel en sträng) som tillhandahålls av användaren på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="80720-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="80720-150">Mer information finns i [skapa en cmdlet för att bearbeta kommando rads indata](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="80720-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="80720-151">En metod för att bearbeta indata kan också ta emot indata från objektet utdata i en överordnad cmdlet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="80720-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="80720-152">Mer information finns i [skapa en cmdlet för att bearbeta pipeline-indata](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="80720-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="80720-153">Tänk på att din cmdlet kan ta emot ininformation från en kombination av kommando rads-och pipeline-källor.</span><span class="sxs-lookup"><span data-stu-id="80720-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="80720-154">Den underordnade cmdleten kanske inte kan returneras under en längre tid, eller inte alls.</span><span class="sxs-lookup"><span data-stu-id="80720-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="80720-155">Av den anledningen bör indata bearbetnings metoden i din cmdlet inte innehålla lås under anrop till [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), särskilt lås för vilka omfattningen sträcker sig utanför cmdlet-instansen.</span><span class="sxs-lookup"><span data-stu-id="80720-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80720-156">Cmdletar ska aldrig anropa [system. Console. WriteLine \*](/dotnet/api/System.Console.WriteLine) eller motsvarande.</span><span class="sxs-lookup"><span data-stu-id="80720-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="80720-157">Cmdleten kan ha objektvariabler som rensas när bearbetningen är klar (till exempel om den öppnar en fil referens i metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och håller handtaget öppet för användning av [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="80720-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="80720-158">Det är viktigt att komma ihåg att Windows PowerShell runtime inte alltid anropar metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , som bör utföra rensning av objekt.</span><span class="sxs-lookup"><span data-stu-id="80720-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="80720-159">Till exempel kanske [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) inte anropas om cmdleten avbryts halvvägs eller om ett avslutande fel inträffar i någon del av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="80720-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="80720-160">Därför bör en cmdlet som kräver rensning av objekt implementera hela [system. IDisposable](/dotnet/api/System.IDisposable) -mönstret, inklusive slut för ande processen, så att körningen kan anropa både [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [system. IDisposable. Dispose \*](/dotnet/api/System.IDisposable.Dispose) i slutet av bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="80720-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="80720-161">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="80720-161">Code Sample</span></span>

<span data-ttu-id="80720-162">Den fullständiga C# exempel koden finns i [GetProcessSample01-exempel](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="80720-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="80720-163">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="80720-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="80720-164">Windows PowerShell skickar information mellan cmdlets med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="80720-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="80720-165">Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="80720-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="80720-166">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="80720-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="80720-167">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="80720-167">Building the Cmdlet</span></span>

<span data-ttu-id="80720-168">När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="80720-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="80720-169">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="80720-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="80720-170">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="80720-170">Testing the Cmdlet</span></span>

<span data-ttu-id="80720-171">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="80720-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="80720-172">Koden för vår exempel get-proc cmdlet är liten, men den använder fortfarande Windows PowerShell-körningsmiljön och ett befintligt .NET-objekt, vilket är tillräckligt för att göra det användbart.</span><span class="sxs-lookup"><span data-stu-id="80720-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="80720-173">Vi testar det för att bättre förstå vad get-proc kan göra och hur dess utdata kan användas.</span><span class="sxs-lookup"><span data-stu-id="80720-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="80720-174">Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="80720-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="80720-175">Starta Windows PowerShell och få de aktuella processerna som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="80720-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="80720-176">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="80720-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="80720-177">Tilldela en variabel till cmdlet-resultaten för enklare manipulering.</span><span class="sxs-lookup"><span data-stu-id="80720-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="80720-178">Hämta antalet processer.</span><span class="sxs-lookup"><span data-stu-id="80720-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="80720-179">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="80720-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="80720-180">Hämta en speciell process.</span><span class="sxs-lookup"><span data-stu-id="80720-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="80720-181">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="80720-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="80720-182">Hämta start tiden för den här processen.</span><span class="sxs-lookup"><span data-stu-id="80720-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="80720-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="80720-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="80720-184">Hämta de processer som antalet referenser är större än 500 och sortera resultatet.</span><span class="sxs-lookup"><span data-stu-id="80720-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="80720-185">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="80720-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="80720-186">Använd `Get-Member`-cmdleten för att visa en lista över de egenskaper som är tillgängliga för varje process.</span><span class="sxs-lookup"><span data-stu-id="80720-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="80720-187">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="80720-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="80720-188">Se även</span><span class="sxs-lookup"><span data-stu-id="80720-188">See Also</span></span>

[<span data-ttu-id="80720-189">Skapa en cmdlet för bearbetning av kommando rads ingångar</span><span class="sxs-lookup"><span data-stu-id="80720-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="80720-190">Skapa en cmdlet för att bearbeta pipeline-inflöden</span><span class="sxs-lookup"><span data-stu-id="80720-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="80720-191">Så här skapar du en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="80720-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="80720-192">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="80720-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="80720-193">[Så här fungerar Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="80720-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="80720-194">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="80720-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="80720-195">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="80720-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="80720-196">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="80720-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
