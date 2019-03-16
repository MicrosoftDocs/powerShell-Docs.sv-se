---
title: Skapa en Cmdlet utan parametrar | Microsoft Docs
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
ms.openlocfilehash: c380b28570c955de6f41152fd617f5c1b0f9e4bd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054704"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="00252-102">Skapa en cmdlet utan parametrar</span><span class="sxs-lookup"><span data-stu-id="00252-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="00252-103">Det här avsnittet beskriver hur du skapar en cmdlet som hämtar information från den lokala datorn utan att använda parametrar och skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00252-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="00252-104">Cmdlet: en som beskrivs här är en Get-Proc-cmdlet som hämtar information om processerna på den lokala datorn och visar informationen på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="00252-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

<span data-ttu-id="00252-105">Ämnena i det här avsnittet omfattar följande:</span><span class="sxs-lookup"><span data-stu-id="00252-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="00252-106">Namngivning av cmdlet: en</span><span class="sxs-lookup"><span data-stu-id="00252-106">Naming the Cmdlet</span></span>](#Naming-the-Cmdlet)

- [<span data-ttu-id="00252-107">Definiera klassen Cmdlet</span><span class="sxs-lookup"><span data-stu-id="00252-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="00252-108">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="00252-108">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="00252-109">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="00252-109">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="00252-110">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="00252-110">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="00252-111">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00252-111">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="00252-112">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00252-112">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

> [!NOTE]
> <span data-ttu-id="00252-113">Tänk på att när du skriver cmdletar referenssammansättningar Windows PowerShell® hämtas på disk (som standard i C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). De är inte installerad i Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="00252-113">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="00252-114">Namngivning av cmdlet: en</span><span class="sxs-lookup"><span data-stu-id="00252-114">Naming the Cmdlet</span></span>

<span data-ttu-id="00252-115">En cmdlet-namn som består av ett verb som anger åtgärden cmdlet: en börjar och ett substantiv som visar de objekt som cmdleten agerar på.</span><span class="sxs-lookup"><span data-stu-id="00252-115">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="00252-116">Eftersom det här exemplet Get-Proc cmdlet: en hämtar processen objekt, används verbet ”hämta”, enligt den [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) uppräkningen och substantiv ”Proc” för att indikera att cmdlet fungerar på processen objekt.</span><span class="sxs-lookup"><span data-stu-id="00252-116">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="00252-117">När du namnger cmdlet: ar, inte använda någon av följande tecken: #, () {} [] & - / \ $; ”:” <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="00252-117">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="00252-118">@ \` .</span><span class="sxs-lookup"><span data-stu-id="00252-118">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="00252-119">Välja ett substantiv</span><span class="sxs-lookup"><span data-stu-id="00252-119">Choosing a Noun</span></span>

<span data-ttu-id="00252-120">Du bör välja ett substantiv som är specifik.</span><span class="sxs-lookup"><span data-stu-id="00252-120">You should choose a noun that is specific.</span></span> <span data-ttu-id="00252-121">Det är bäst att använda en enda substantiv föregås av en förkortad version av produktens namn.</span><span class="sxs-lookup"><span data-stu-id="00252-121">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="00252-122">En exempel-cmdlet-namn för den här typen är ”`Get-SQLServer`”.</span><span class="sxs-lookup"><span data-stu-id="00252-122">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="00252-123">Välja ett Verb</span><span class="sxs-lookup"><span data-stu-id="00252-123">Choosing a Verb</span></span>

<span data-ttu-id="00252-124">Du bör använda ett verb från uppsättningen med godkända cmdlet verb-namnen.</span><span class="sxs-lookup"><span data-stu-id="00252-124">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="00252-125">Läs mer om godkända cmdletens verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="00252-125">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="00252-126">Definiera klassen Cmdlet</span><span class="sxs-lookup"><span data-stu-id="00252-126">Defining the Cmdlet Class</span></span>

<span data-ttu-id="00252-127">När du har valt en cmdlet-namn, definierar du en .NET-klass för att implementera cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="00252-127">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="00252-128">Här är klassdefinitionen för det här exemplet Get-Proc cmdlet:</span><span class="sxs-lookup"><span data-stu-id="00252-128">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="00252-129">Observera att före klassdefinitionen, den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributet med syntaxen `[Cmdlet(verb, noun, ...)]`, används för att identifiera den här klassen som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00252-129">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="00252-130">Detta är det enda obligatoriska attributet för alla cmdletar och tillåter Windows PowerShell-körning för att anropa dem korrekt.</span><span class="sxs-lookup"><span data-stu-id="00252-130">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="00252-131">Du kan ange attributet nyckelord för ytterligare deklarera klassen om det behövs.</span><span class="sxs-lookup"><span data-stu-id="00252-131">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="00252-132">Tänk på att attributet-deklarationen för våra exempel GetProcCommand klassen deklarerar endast substantiv och verb namnen för cmdleten Get-processen.</span><span class="sxs-lookup"><span data-stu-id="00252-132">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="00252-133">För alla Windows PowerShell-Attributklasser motsvarar nyckelord som du kan ange egenskaper för attributklassen.</span><span class="sxs-lookup"><span data-stu-id="00252-133">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="00252-134">När du namnger klassen för cmdlet: en är en bra idé att återspegla cmdlet-namn i klassnamnet.</span><span class="sxs-lookup"><span data-stu-id="00252-134">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="00252-135">Om du vill göra detta använder formatet ”VerbNounCommand” och Ersätt ”Verb” och ”substantiv” med verb och substantiv som används i cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="00252-135">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="00252-136">Visas i föregående klassdefinitionen kan cmdleten Get-Proc exemplet definierar en klass med namnet GetProcCommand som härrör från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basklassen.</span><span class="sxs-lookup"><span data-stu-id="00252-136">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00252-137">Om du vill definiera en cmdlet som ansluter direkt till Windows PowerShell-runtime .NET-klass måste härledas från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basklassen.</span><span class="sxs-lookup"><span data-stu-id="00252-137">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="00252-138">Läs mer om den här klassen [och skapa en Cmdlet som definierar parameteruppsättningar](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="00252-138">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="00252-139">Klass för en cmdlet måste uttryckligen markeras som offentliga.</span><span class="sxs-lookup"><span data-stu-id="00252-139">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="00252-140">Klasser som inte är markerad som offentlig som standard till interna och kommer inte att hitta av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="00252-140">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="00252-141">Windows PowerShell använder den [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namnrymd för dess cmdlet-klasser.</span><span class="sxs-lookup"><span data-stu-id="00252-141">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="00252-142">Vi rekommenderar att placera dina cmdlet-klasser i ett namnområde för kommandon med ditt API-namnområde, till exempel xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="00252-142">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="00252-143">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="00252-143">Overriding an Input Processing Method</span></span>

<span data-ttu-id="00252-144">Den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klassen innehåller bearbetningsmetoder för tre huvudsakliga inkommande, varav minst en cmdlet: måste åsidosätta.</span><span class="sxs-lookup"><span data-stu-id="00252-144">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="00252-145">Mer information om hur Windows PowerShell bearbetar poster finns i [hur Windows PowerShell fungerar](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span><span class="sxs-lookup"><span data-stu-id="00252-145">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

<span data-ttu-id="00252-146">För alla typer av indata Windows PowerShell-runtime anropar [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) att aktivera bearbetning.</span><span class="sxs-lookup"><span data-stu-id="00252-146">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="00252-147">Om din cmdlet måste utföra vissa Förbearbeta eller konfiguration, kan det göra detta genom att åsidosätta den här metoden.</span><span class="sxs-lookup"><span data-stu-id="00252-147">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="00252-148">Windows PowerShell använder termen ”post” för att beskriva uppsättningen parametervärden som anges när en cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="00252-148">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="00252-149">Om din cmdlet accepterar pipeline-indata, den måste åsidosätta de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod, och eventuellt den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)metod.</span><span class="sxs-lookup"><span data-stu-id="00252-149">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="00252-150">Till exempel en cmdlet kan åsidosätta de båda metoderna om den samlar in alla indata med [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och sedan fungerar på indata som helhet i stället för ett element i taget, som den `Sort-Object` cmdlet har.</span><span class="sxs-lookup"><span data-stu-id="00252-150">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="00252-151">Om din cmdlet inte tar indata från pipeline, bör det åsidosätter den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="00252-151">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="00252-152">Tänk på att den här metoden används ofta i stället för [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) när cmdlet: en fungerar inte på ett element i taget, liksom vad gäller för en sortering cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00252-152">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="00252-153">Eftersom det här exemplet Get-Proc cmdlet måste ta emot indata från pipeline, åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod och använder standardimplementeringar för [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="00252-153">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="00252-154">Den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) åsidosättning hämtar processer och skriver dem till den från kommandoraden med hjälp av den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod.</span><span class="sxs-lookup"><span data-stu-id="00252-154">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="00252-155">Kom ihåg följande om inkommande bearbetning</span><span class="sxs-lookup"><span data-stu-id="00252-155">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="00252-156">Standard-källan för indata är ett explicit objekt (till exempel en sträng) som anges av användaren på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="00252-156">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="00252-157">Mer information finns i [skapar en Cmdlet för att bearbeta kommandoraden indata](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="00252-157">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="00252-158">Indata metoden bearbetades kan också ta emot indata från utgående objekt av en överordnad cmdlet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00252-158">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="00252-159">Mer information finns i [skapar en Cmdlet för att bearbeta indata från Pipeline](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="00252-159">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="00252-160">Tänk på att din cmdlet kan ta emot indata från en kombination av kommandorad och pipeline-datakällor.</span><span class="sxs-lookup"><span data-stu-id="00252-160">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="00252-161">Cmdleten underordnade kanske inte returnerar under en längre tid eller inte alls.</span><span class="sxs-lookup"><span data-stu-id="00252-161">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="00252-162">Därför bör indata metoden i din cmdlet bearbetades inte har Lås under anrop till [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), särskilt lås som omfattningen som sträcker sig utanför cmdlet-instans.</span><span class="sxs-lookup"><span data-stu-id="00252-162">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00252-163">Cmdlet: ar aldrig ska anropa [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) eller motsvarande.</span><span class="sxs-lookup"><span data-stu-id="00252-163">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="00252-164">Cmdlet: kanske objektvariabler för att rensa upp när den är klar bearbetning (till exempel om den öppnas en filreferens i den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod och ser referensen öppna för användning av [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="00252-164">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="00252-165">Det är viktigt att komma ihåg att Windows PowerShell-runtime alltid inte anropar den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod som utför rensningen för objektet.</span><span class="sxs-lookup"><span data-stu-id="00252-165">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="00252-166">Till exempel [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan inte anropas om cmdlet: en har avbrutits mitt eller om avslutande fel uppstår i någon del av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="00252-166">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="00252-167">Därför kan en cmdlet som kräver objektet rensningen ska implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) mönstret, inklusive finaliserare, så att körningen kan anropa båda [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) i slutet av bearbetning.</span><span class="sxs-lookup"><span data-stu-id="00252-167">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="00252-168">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="00252-168">Code Sample</span></span>

<span data-ttu-id="00252-169">För hela C# exempelkoden, se [GetProcessSample01 exempel](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="00252-169">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="00252-170">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="00252-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="00252-171">Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="00252-171">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="00252-172">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00252-172">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="00252-173">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="00252-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="00252-174">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00252-174">Building the Cmdlet</span></span>

<span data-ttu-id="00252-175">När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="00252-175">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="00252-176">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="00252-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="00252-177">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00252-177">Testing the Cmdlet</span></span>

<span data-ttu-id="00252-178">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="00252-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="00252-179">Koden för våra exempel Get-Proc-cmdlet är liten, men den fortfarande använder Windows PowerShell-runtime och ett befintligt .NET-objekt, vilket är tillräckligt för att göra det användbart.</span><span class="sxs-lookup"><span data-stu-id="00252-179">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="00252-180">Nu ska vi testa den för att bättre förstå vad Get-processen kan göra och hur dess utdata kan användas.</span><span class="sxs-lookup"><span data-stu-id="00252-180">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="00252-181">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="00252-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="00252-182">Starta Windows PowerShell och hämta aktuella processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="00252-182">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="00252-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00252-183">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="00252-184">Tilldela en variabel till cmdlet-resultat för enklare manipulering.</span><span class="sxs-lookup"><span data-stu-id="00252-184">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="00252-185">Få en processer.</span><span class="sxs-lookup"><span data-stu-id="00252-185">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="00252-186">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00252-186">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="00252-187">Hämta en särskild process.</span><span class="sxs-lookup"><span data-stu-id="00252-187">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="00252-188">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00252-188">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="00252-189">Hämta starttiden för den här processen.</span><span class="sxs-lookup"><span data-stu-id="00252-189">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="00252-190">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00252-190">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="00252-191">Få de processer som antal referenser är större än 500 och sortera resultatet.</span><span class="sxs-lookup"><span data-stu-id="00252-191">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="00252-192">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00252-192">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="00252-193">Använd den `Get-Member` cmdlet för att lista egenskaperna som är tillgängliga för varje process.</span><span class="sxs-lookup"><span data-stu-id="00252-193">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="00252-194">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00252-194">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="00252-195">Se även</span><span class="sxs-lookup"><span data-stu-id="00252-195">See Also</span></span>

[<span data-ttu-id="00252-196">Skapa en Cmdlet för bearbetning av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="00252-196">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="00252-197">Skapa en Cmdlet för att bearbeta indata från Pipeline</span><span class="sxs-lookup"><span data-stu-id="00252-197">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="00252-198">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="00252-198">How to Create a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="00252-199">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="00252-199">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="00252-200">Så här fungerar Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="00252-200">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="00252-201">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="00252-201">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="00252-202">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="00252-202">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="00252-203">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="00252-203">Cmdlet Samples</span></span>](./cmdlet-samples.md)