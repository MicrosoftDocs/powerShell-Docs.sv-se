---
title: 'Att lägga till meddelanden för användare i cmdlet: | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 138c6a43937e72fffaa2a09243e500e9822e6111
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854927"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="b2a74-102">Lägga till användarmeddelanden i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2a74-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="b2a74-103">Cmdlet: ar kan skriva flera olika typer av meddelanden som visas för användaren av Windows PowerShell-körningen.</span><span class="sxs-lookup"><span data-stu-id="b2a74-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="b2a74-104">Dessa meddelanden innehåller följande typer:</span><span class="sxs-lookup"><span data-stu-id="b2a74-104">These messages include the following types:</span></span>

- <span data-ttu-id="b2a74-105">Utförliga meddelanden som innehåller allmän användarinformation.</span><span class="sxs-lookup"><span data-stu-id="b2a74-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="b2a74-106">Felsök meddelanden som innehåller information om felsökning.</span><span class="sxs-lookup"><span data-stu-id="b2a74-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="b2a74-107">Varningsmeddelanden som innehåller ett meddelande som cmdlet: en är på väg att utföra en åtgärd som kan ha oväntade resultat.</span><span class="sxs-lookup"><span data-stu-id="b2a74-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="b2a74-108">Utvecklingsrapporten meddelanden som innehåller information om hur mycket fungerar cmdlet: en har slutförts när du utför en åtgärd som tar lång tid.</span><span class="sxs-lookup"><span data-stu-id="b2a74-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="b2a74-109">Det finns några gränser för antalet meddelanden som cmdlet: kan skriva eller typen av meddelanden som cmdlet: skriver.</span><span class="sxs-lookup"><span data-stu-id="b2a74-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="b2a74-110">Varje meddelande skrivs genom att göra ett specifikt anrop från i indata metoden av cmdlet: bearbetades.</span><span class="sxs-lookup"><span data-stu-id="b2a74-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="b2a74-111">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="b2a74-111">Defining the Cmdlet</span></span>

<span data-ttu-id="b2a74-112">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="b2a74-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b2a74-113">Alla slags cmdlet kan skriva användarmeddelanden från indata metoderna; därför i allmänhet kan du kalla den här cmdleten med alla verb som anger vilka system ändringar cmdlet utför.</span><span class="sxs-lookup"><span data-stu-id="b2a74-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="b2a74-114">Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b2a74-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b2a74-115">Cmdlet Stop-processen har utformats för att ändra systemet. Därför kan den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklarationen för .NET-klass måste innehålla den `SupportsShouldProcess` attributet nyckelord och anges till `true`.</span><span class="sxs-lookup"><span data-stu-id="b2a74-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="b2a74-116">Följande kod är definitionen för den här cmdlet Stop-Proc-klassen.</span><span class="sxs-lookup"><span data-stu-id="b2a74-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="b2a74-117">Läs mer om den här definitionen [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b2a74-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="b2a74-118">Definiera parametrar för ändring av systemet</span><span class="sxs-lookup"><span data-stu-id="b2a74-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="b2a74-119">Cmdlet Stop-Proc definierar tre parametrar: `Name`, `Force`, och `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="b2a74-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="b2a74-120">Mer information om hur du definierar dessa parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b2a74-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="b2a74-121">Här är parameterdeklaration för cmdleten Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="b2a74-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b2a74-122">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="b2a74-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b2a74-123">Cmdlet: måste åsidosätta indata metoden bearbetades, oftast blir [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="b2a74-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="b2a74-124">Denna cmdlet Stop-Proc åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) indatametod för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="b2a74-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="b2a74-125">I den här implementeringen av cmdlet Stop-Proc rings samtal att skriva utförliga meddelanden och felsökningsmeddelanden varningsmeddelanden.</span><span class="sxs-lookup"><span data-stu-id="b2a74-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="b2a74-126">Mer information om hur den här metoden anropar den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder, se [Skapar en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="b2a74-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="b2a74-127">Skriva ett utförligt meddelande</span><span class="sxs-lookup"><span data-stu-id="b2a74-127">Writing a Verbose Message</span></span>

<span data-ttu-id="b2a74-128">Den [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod för att skriva allmän användarnivå information som är inte relaterat till specifika felvillkor.</span><span class="sxs-lookup"><span data-stu-id="b2a74-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="b2a74-129">Systemadministratören kan sedan använda informationen för att fortsätta att bearbeta andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="b2a74-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="b2a74-130">All information som skrivits med den här metoden bör dessutom vara lokaliserade efter behov.</span><span class="sxs-lookup"><span data-stu-id="b2a74-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="b2a74-131">Följande kod från denna cmdlet Stop-Proc visar två anrop till den [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod som du åsidosättandet av den [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="b2a74-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="b2a74-132">Skriva ett meddelande för felsökning</span><span class="sxs-lookup"><span data-stu-id="b2a74-132">Writing a Debug Message</span></span>

<span data-ttu-id="b2a74-133">Den [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod för att skriva felsökningsmeddelanden som kan användas för att felsöka driften av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="b2a74-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="b2a74-134">Anropet görs från indata metoden bearbetades.</span><span class="sxs-lookup"><span data-stu-id="b2a74-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="b2a74-135">Windows PowerShell definierar också en `Debug` parameter som anger både utförlig och felsökningsinformation.</span><span class="sxs-lookup"><span data-stu-id="b2a74-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="b2a74-136">Om din cmdlet har stöd för den här parametern, det måste inte att anropa [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) i samma kod som anropar [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="b2a74-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="b2a74-137">Följande två avsnitt av kod från cmdlet Stop-Proc exemplet visar anrop till den [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod som du åsidosättandet av den [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="b2a74-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="b2a74-138">Det här debug-meddelandet skrivs omedelbart före [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.</span><span class="sxs-lookup"><span data-stu-id="b2a74-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="b2a74-139">Det här debug-meddelandet skrivs omedelbart före [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) anropas.</span><span class="sxs-lookup"><span data-stu-id="b2a74-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="b2a74-140">Windows PowerShell dirigerar automatiskt någon [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) anrop till spårning av infrastruktur och cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b2a74-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="b2a74-141">På så sätt kan metodanrop kan spåras till värd, en fil eller en felsökare utan att du behöver göra några extra utvecklingsarbete i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b2a74-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="b2a74-142">Följande kommandorad post implementerar en spårning av åtgärd.</span><span class="sxs-lookup"><span data-stu-id="b2a74-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="b2a74-143">**PS > trace-uttrycket stop-proc-filen proc.log-kommandot stop-proc anteckningar**</span><span class="sxs-lookup"><span data-stu-id="b2a74-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="b2a74-144">Skriva ett varningsmeddelande</span><span class="sxs-lookup"><span data-stu-id="b2a74-144">Writing a Warning Message</span></span>

<span data-ttu-id="b2a74-145">Den [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod för att skriva en varning när cmdleten ska utföra en åtgärd som kan ha ett oväntat resultat, till exempel skriva över en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="b2a74-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="b2a74-146">Följande kod från cmdlet Stop-Proc exemplet visar anropet till den [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod som du åsidosättandet av den [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="b2a74-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="b2a74-147">Skriva ett meddelande om pågående</span><span class="sxs-lookup"><span data-stu-id="b2a74-147">Writing a Progress Message</span></span>

<span data-ttu-id="b2a74-148">Den [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) används för att skriva förloppsmeddelanden när cmdlet åtgärder ta lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="b2a74-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="b2a74-149">Ett anrop till [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) skickar en [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objekt som ska skickas till programmet som är värd för rendering för användaren.</span><span class="sxs-lookup"><span data-stu-id="b2a74-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="b2a74-150">Denna cmdlet Stop-processen inte innehåller ett anrop till den [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metod.</span><span class="sxs-lookup"><span data-stu-id="b2a74-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="b2a74-151">Följande kod är ett exempel på en pågående meddelande som skrivits av en cmdlet som försöker att kopiera ett objekt.</span><span class="sxs-lookup"><span data-stu-id="b2a74-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="b2a74-152">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="b2a74-152">Code Sample</span></span>

<span data-ttu-id="b2a74-153">För hela C# exempelkoden, se [StopProcessSample02 exempel](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b2a74-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="b2a74-154">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="b2a74-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="b2a74-155">Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="b2a74-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="b2a74-156">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a74-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b2a74-157">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="b2a74-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b2a74-158">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="b2a74-158">Building the Cmdlet</span></span>

<span data-ttu-id="b2a74-159">När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="b2a74-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b2a74-160">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="b2a74-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b2a74-161">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="b2a74-161">Testing the Cmdlet</span></span>

<span data-ttu-id="b2a74-162">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="b2a74-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="b2a74-163">Nu ska vi testa exempel Stop-Proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2a74-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="b2a74-164">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b2a74-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="b2a74-165">Följande kommandorad post använder Stop-processen för att stoppa processen med namnet ”ANTECKNINGAR” anger utförlig meddelanden och skriva ut felsökningsinformation.</span><span class="sxs-lookup"><span data-stu-id="b2a74-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="b2a74-166">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="b2a74-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="b2a74-167">Se även</span><span class="sxs-lookup"><span data-stu-id="b2a74-167">See Also</span></span>

[<span data-ttu-id="b2a74-168">Skapa en Cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="b2a74-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="b2a74-169">Så här skapar du en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2a74-169">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="b2a74-170">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="b2a74-170">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="b2a74-171">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="b2a74-171">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="b2a74-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b2a74-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
