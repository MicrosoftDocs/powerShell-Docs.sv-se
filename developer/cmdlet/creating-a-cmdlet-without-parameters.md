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
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733964"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="3622b-102">Skapa en cmdlet utan parametrar</span><span class="sxs-lookup"><span data-stu-id="3622b-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="3622b-103">Det här avsnittet beskriver hur du skapar en cmdlet som hämtar information från den lokala datorn utan att använda parametrar och skriver informationen till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3622b-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="3622b-104">Cmdlet: en som beskrivs här är en Get-Proc-cmdlet som hämtar information om processerna på den lokala datorn och visar informationen på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="3622b-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="3622b-105">Tänk på att när du skriver cmdletar referenssammansättningar Windows PowerShell® hämtas på disk (som standard i C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="3622b-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="3622b-106">De är inte installerad i Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="3622b-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="3622b-107">Namngivning av cmdlet: en</span><span class="sxs-lookup"><span data-stu-id="3622b-107">Naming the Cmdlet</span></span>

<span data-ttu-id="3622b-108">En cmdlet-namn som består av ett verb som anger åtgärden cmdlet: en börjar och ett substantiv som visar de objekt som cmdleten agerar på.</span><span class="sxs-lookup"><span data-stu-id="3622b-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="3622b-109">Eftersom det här exemplet Get-Proc cmdlet: en hämtar processen objekt, används verbet ”hämta”, enligt den [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) uppräkningen och substantiv ”Proc” för att indikera att cmdlet fungerar på processen objekt.</span><span class="sxs-lookup"><span data-stu-id="3622b-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="3622b-110">När du namnger cmdlet: ar, inte använda någon av följande tecken: #, () {} [] & - / \ $; ”:” <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="3622b-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="3622b-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="3622b-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="3622b-112">Välja ett substantiv</span><span class="sxs-lookup"><span data-stu-id="3622b-112">Choosing a Noun</span></span>

<span data-ttu-id="3622b-113">Du bör välja ett substantiv som är specifik.</span><span class="sxs-lookup"><span data-stu-id="3622b-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="3622b-114">Det är bäst att använda en enda substantiv föregås av en förkortad version av produktens namn.</span><span class="sxs-lookup"><span data-stu-id="3622b-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="3622b-115">En exempel-cmdlet-namn för den här typen är ”`Get-SQLServer`”.</span><span class="sxs-lookup"><span data-stu-id="3622b-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="3622b-116">Välja ett Verb</span><span class="sxs-lookup"><span data-stu-id="3622b-116">Choosing a Verb</span></span>

<span data-ttu-id="3622b-117">Du bör använda ett verb från uppsättningen med godkända cmdlet verb-namnen.</span><span class="sxs-lookup"><span data-stu-id="3622b-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="3622b-118">Läs mer om godkända cmdletens verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3622b-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="3622b-119">Definiera klassen Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3622b-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="3622b-120">När du har valt en cmdlet-namn, definierar du en .NET-klass för att implementera cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="3622b-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="3622b-121">Här är klassdefinitionen för det här exemplet Get-Proc cmdlet:</span><span class="sxs-lookup"><span data-stu-id="3622b-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="3622b-122">Observera att före klassdefinitionen, den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributet med syntaxen `[Cmdlet(verb, noun, ...)]`, används för att identifiera den här klassen som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3622b-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="3622b-123">Detta är det enda obligatoriska attributet för alla cmdletar och tillåter Windows PowerShell-körning för att anropa dem korrekt.</span><span class="sxs-lookup"><span data-stu-id="3622b-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="3622b-124">Du kan ange attributet nyckelord för ytterligare deklarera klassen om det behövs.</span><span class="sxs-lookup"><span data-stu-id="3622b-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="3622b-125">Tänk på att attributet-deklarationen för våra exempel GetProcCommand klassen deklarerar endast substantiv och verb namnen för cmdleten Get-processen.</span><span class="sxs-lookup"><span data-stu-id="3622b-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="3622b-126">För alla Windows PowerShell-Attributklasser motsvarar nyckelord som du kan ange egenskaper för attributklassen.</span><span class="sxs-lookup"><span data-stu-id="3622b-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="3622b-127">När du namnger klassen för cmdlet: en är en bra idé att återspegla cmdlet-namn i klassnamnet.</span><span class="sxs-lookup"><span data-stu-id="3622b-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="3622b-128">Om du vill göra detta använder formatet ”VerbNounCommand” och Ersätt ”Verb” och ”substantiv” med verb och substantiv som används i cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="3622b-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="3622b-129">Visas i föregående klassdefinitionen kan cmdleten Get-Proc exemplet definierar en klass med namnet GetProcCommand som härrör från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basklassen.</span><span class="sxs-lookup"><span data-stu-id="3622b-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3622b-130">Om du vill definiera en cmdlet som ansluter direkt till Windows PowerShell-runtime .NET-klass måste härledas från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basklassen.</span><span class="sxs-lookup"><span data-stu-id="3622b-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="3622b-131">Läs mer om den här klassen [och skapa en Cmdlet som definierar parameteruppsättningar](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="3622b-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3622b-132">Klass för en cmdlet måste uttryckligen markeras som offentliga.</span><span class="sxs-lookup"><span data-stu-id="3622b-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="3622b-133">Klasser som inte är markerad som offentlig som standard till interna och kommer inte att hitta av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="3622b-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="3622b-134">Windows PowerShell använder den [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namnrymd för dess cmdlet-klasser.</span><span class="sxs-lookup"><span data-stu-id="3622b-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="3622b-135">Vi rekommenderar att placera dina cmdlet-klasser i ett namnområde för kommandon med ditt API-namnområde, till exempel xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="3622b-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3622b-136">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="3622b-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3622b-137">Den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klassen innehåller bearbetningsmetoder för tre huvudsakliga inkommande, varav minst en cmdlet: måste åsidosätta.</span><span class="sxs-lookup"><span data-stu-id="3622b-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="3622b-138">Mer information om hur Windows PowerShell bearbetar poster finns i [hur Windows PowerShell fungerar](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3622b-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="3622b-139">För alla typer av indata Windows PowerShell-runtime anropar [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) att aktivera bearbetning.</span><span class="sxs-lookup"><span data-stu-id="3622b-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="3622b-140">Om din cmdlet måste utföra vissa Förbearbeta eller konfiguration, kan det göra detta genom att åsidosätta den här metoden.</span><span class="sxs-lookup"><span data-stu-id="3622b-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="3622b-141">Windows PowerShell använder termen ”post” för att beskriva uppsättningen parametervärden som anges när en cmdlet anropas.</span><span class="sxs-lookup"><span data-stu-id="3622b-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="3622b-142">Om din cmdlet accepterar pipeline-indata, den måste åsidosätta de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod, och eventuellt den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)metod.</span><span class="sxs-lookup"><span data-stu-id="3622b-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3622b-143">Till exempel en cmdlet kan åsidosätta de båda metoderna om den samlar in alla indata med [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och sedan fungerar på indata som helhet i stället för ett element i taget, som den `Sort-Object` cmdlet har.</span><span class="sxs-lookup"><span data-stu-id="3622b-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="3622b-144">Om din cmdlet inte tar indata från pipeline, bör det åsidosätter den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="3622b-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="3622b-145">Tänk på att den här metoden används ofta i stället för [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) när cmdlet: en fungerar inte på ett element i taget, liksom vad gäller för en sortering cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3622b-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="3622b-146">Eftersom det här exemplet Get-Proc cmdlet måste ta emot indata från pipeline, åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod och använder standardimplementeringar för [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="3622b-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="3622b-147">Den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) åsidosättning hämtar processer och skriver dem till den från kommandoraden med hjälp av den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod.</span><span class="sxs-lookup"><span data-stu-id="3622b-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="3622b-148">Kom ihåg följande om inkommande bearbetning</span><span class="sxs-lookup"><span data-stu-id="3622b-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="3622b-149">Standard-källan för indata är ett explicit objekt (till exempel en sträng) som anges av användaren på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="3622b-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="3622b-150">Mer information finns i [skapar en Cmdlet för att bearbeta kommandoraden indata](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="3622b-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="3622b-151">Indata metoden bearbetades kan också ta emot indata från utgående objekt av en överordnad cmdlet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3622b-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="3622b-152">Mer information finns i [skapar en Cmdlet för att bearbeta indata från Pipeline](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="3622b-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="3622b-153">Tänk på att din cmdlet kan ta emot indata från en kombination av kommandorad och pipeline-datakällor.</span><span class="sxs-lookup"><span data-stu-id="3622b-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="3622b-154">Cmdleten underordnade kanske inte returnerar under en längre tid eller inte alls.</span><span class="sxs-lookup"><span data-stu-id="3622b-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="3622b-155">Därför bör indata metoden i din cmdlet bearbetades inte har Lås under anrop till [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), särskilt lås som omfattningen som sträcker sig utanför cmdlet-instans.</span><span class="sxs-lookup"><span data-stu-id="3622b-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3622b-156">Cmdlet: ar aldrig ska anropa [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) eller motsvarande.</span><span class="sxs-lookup"><span data-stu-id="3622b-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="3622b-157">Cmdlet: kanske objektvariabler för att rensa upp när den är klar bearbetning (till exempel om den öppnas en filreferens i den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod och ser referensen öppna för användning av [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="3622b-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="3622b-158">Det är viktigt att komma ihåg att Windows PowerShell-runtime alltid inte anropar den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod som utför rensningen för objektet.</span><span class="sxs-lookup"><span data-stu-id="3622b-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="3622b-159">Till exempel [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan inte anropas om cmdlet: en har avbrutits mitt eller om avslutande fel uppstår i någon del av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="3622b-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="3622b-160">Därför kan en cmdlet som kräver objektet rensningen ska implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) mönstret, inklusive finaliserare, så att körningen kan anropa båda [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) i slutet av bearbetning.</span><span class="sxs-lookup"><span data-stu-id="3622b-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="3622b-161">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="3622b-161">Code Sample</span></span>

<span data-ttu-id="3622b-162">För hela C# exempelkoden, se [GetProcessSample01 exempel](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3622b-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="3622b-163">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="3622b-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="3622b-164">Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="3622b-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="3622b-165">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3622b-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3622b-166">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3622b-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3622b-167">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="3622b-167">Building the Cmdlet</span></span>

<span data-ttu-id="3622b-168">När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="3622b-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3622b-169">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3622b-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3622b-170">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="3622b-170">Testing the Cmdlet</span></span>

<span data-ttu-id="3622b-171">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="3622b-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3622b-172">Koden för våra exempel Get-Proc-cmdlet är liten, men den fortfarande använder Windows PowerShell-runtime och ett befintligt .NET-objekt, vilket är tillräckligt för att göra det användbart.</span><span class="sxs-lookup"><span data-stu-id="3622b-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="3622b-173">Nu ska vi testa den för att bättre förstå vad Get-processen kan göra och hur dess utdata kan användas.</span><span class="sxs-lookup"><span data-stu-id="3622b-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="3622b-174">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3622b-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="3622b-175">Starta Windows PowerShell och hämta aktuella processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="3622b-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="3622b-176">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3622b-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="3622b-177">Tilldela en variabel till cmdlet-resultat för enklare manipulering.</span><span class="sxs-lookup"><span data-stu-id="3622b-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="3622b-178">Få en processer.</span><span class="sxs-lookup"><span data-stu-id="3622b-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="3622b-179">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3622b-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="3622b-180">Hämta en särskild process.</span><span class="sxs-lookup"><span data-stu-id="3622b-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="3622b-181">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3622b-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="3622b-182">Hämta starttiden för den här processen.</span><span class="sxs-lookup"><span data-stu-id="3622b-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="3622b-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3622b-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="3622b-184">Få de processer som antal referenser är större än 500 och sortera resultatet.</span><span class="sxs-lookup"><span data-stu-id="3622b-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="3622b-185">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3622b-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="3622b-186">Använd den `Get-Member` cmdlet för att lista egenskaperna som är tillgängliga för varje process.</span><span class="sxs-lookup"><span data-stu-id="3622b-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="3622b-187">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="3622b-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="3622b-188">Se även</span><span class="sxs-lookup"><span data-stu-id="3622b-188">See Also</span></span>

[<span data-ttu-id="3622b-189">Skapa en Cmdlet för bearbetning av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="3622b-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="3622b-190">Skapa en Cmdlet för att bearbeta indata från Pipeline</span><span class="sxs-lookup"><span data-stu-id="3622b-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="3622b-191">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3622b-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="3622b-192">[Utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3622b-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="3622b-193">[Så här fungerar Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3622b-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="3622b-194">[Hur du registrerar Cmdlets, Providers och vara värd för program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="3622b-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="3622b-195">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="3622b-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="3622b-196">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="3622b-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)