---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till användarmeddelanden i en cmdlet
description: Lägga till användarmeddelanden i en cmdlet
ms.openlocfilehash: de6fcc093af1d01287eed1eb8cc7b81cf5d2fdd8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668345"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="00a92-103">Lägga till användarmeddelanden i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="00a92-103">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="00a92-104">Cmdletar kan skriva flera typer av meddelanden som kan visas för användaren av Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="00a92-104">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="00a92-105">Dessa meddelanden innehåller följande typer:</span><span class="sxs-lookup"><span data-stu-id="00a92-105">These messages include the following types:</span></span>

- <span data-ttu-id="00a92-106">Utförliga meddelanden som innehåller allmän användar information.</span><span class="sxs-lookup"><span data-stu-id="00a92-106">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="00a92-107">Felsök meddelanden som innehåller felsöknings information.</span><span class="sxs-lookup"><span data-stu-id="00a92-107">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="00a92-108">Varnings meddelanden som innehåller ett meddelande om att cmdleten är på väg att utföra en åtgärd som kan ha oväntade resultat.</span><span class="sxs-lookup"><span data-stu-id="00a92-108">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="00a92-109">Förlopps rapport meddelanden som innehåller information om hur mycket arbete som cmdleten har slutförts när en åtgärd utförs som tar lång tid.</span><span class="sxs-lookup"><span data-stu-id="00a92-109">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="00a92-110">Det finns ingen gräns för hur många meddelanden som din cmdlet kan skriva eller vilken typ av meddelanden som cmdleten skriver.</span><span class="sxs-lookup"><span data-stu-id="00a92-110">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="00a92-111">Varje meddelande skrivs genom att ett speciellt anrop görs inom den indata bearbetnings metoden i din cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00a92-111">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="00a92-112">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="00a92-112">Defining the Cmdlet</span></span>

<span data-ttu-id="00a92-113">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00a92-113">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="00a92-114">Alla sorters cmdlets kan skriva användar meddelanden från dess metoder för bearbetning av indata. i allmänhet kan du namnge denna cmdlet med hjälp av verb som anger vilka system ändringar som cmdleten utför.</span><span class="sxs-lookup"><span data-stu-id="00a92-114">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="00a92-115">Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="00a92-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="00a92-116">Stop-Proc cmdlet är utformad för att ändra systemet; Därför måste deklarationen [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) för .net-klassen innehålla `SupportsShouldProcess` nyckelordet attribut och anges till `true` .</span><span class="sxs-lookup"><span data-stu-id="00a92-116">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="00a92-117">Följande kod är definitionen för den här Stop-Proc cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="00a92-117">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="00a92-118">Mer information om den här definitionen finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="00a92-118">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="00a92-119">Definiera parametrar för system ändring</span><span class="sxs-lookup"><span data-stu-id="00a92-119">Defining Parameters for System Modification</span></span>

<span data-ttu-id="00a92-120">Stop-Proc cmdleten definierar tre parametrar: `Name` , `Force` , och `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="00a92-120">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="00a92-121">Mer information om hur du definierar dessa parametrar finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="00a92-121">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="00a92-122">Här är parameter deklarationen för Stop-Proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00a92-122">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="00a92-123">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="00a92-123">Overriding an Input Processing Method</span></span>

<span data-ttu-id="00a92-124">Din cmdlet måste åsidosätta en metod för bearbetning av indata, oftast är den [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="00a92-124">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="00a92-125">Denna Stop-Proc-cmdlet åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="00a92-125">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="00a92-126">I den här implementeringen av Stop-Proc cmdlet görs anrop för att skriva utförliga meddelanden, felsöka meddelanden och varnings meddelanden.</span><span class="sxs-lookup"><span data-stu-id="00a92-126">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="00a92-127">Mer information om hur den här metoden anropar metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="00a92-127">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="00a92-128">Skriva ett utförligt meddelande</span><span class="sxs-lookup"><span data-stu-id="00a92-128">Writing a Verbose Message</span></span>

<span data-ttu-id="00a92-129">Metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) används för att skriva allmän information på användar nivå som inte är relaterad till vissa fel villkor.</span><span class="sxs-lookup"><span data-stu-id="00a92-129">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="00a92-130">System administratören kan sedan använda den informationen för att fortsätta bearbeta andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="00a92-130">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="00a92-131">Dessutom bör all information som skrivs med den här metoden lokaliseras efter behov.</span><span class="sxs-lookup"><span data-stu-id="00a92-131">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="00a92-132">Följande kod från denna Stop-Proc-cmdlet visar två anrop till metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="00a92-132">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="00a92-133">Skriva ett fel söknings meddelande</span><span class="sxs-lookup"><span data-stu-id="00a92-133">Writing a Debug Message</span></span>

<span data-ttu-id="00a92-134">Metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) används för att skriva fel söknings meddelanden som kan användas för att felsöka cmdletens funktion.</span><span class="sxs-lookup"><span data-stu-id="00a92-134">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="00a92-135">Anropet görs från en metod för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="00a92-135">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="00a92-136">Windows PowerShell definierar också en `Debug` parameter som visar både utförlig och felsöknings information.</span><span class="sxs-lookup"><span data-stu-id="00a92-136">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="00a92-137">Om din cmdlet stöder den här parametern behöver den inte anropa [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) i samma kod som anropar [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="00a92-137">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="00a92-138">I följande två avsnitt av kod från exempel Stop-Proc cmdlet visas anrop till metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="00a92-138">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="00a92-139">Det här fel söknings meddelandet skrivs omedelbart innan [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.</span><span class="sxs-lookup"><span data-stu-id="00a92-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="00a92-140">Det här fel söknings meddelandet skrivs omedelbart innan [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) anropas.</span><span class="sxs-lookup"><span data-stu-id="00a92-140">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="00a92-141">Windows PowerShell dirigerar automatiskt alla [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -anrop till spårnings infrastrukturen och-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="00a92-141">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="00a92-142">Detta gör att metod anrop kan spåras till värd programmet, en fil eller en fel sökare utan att du behöver göra några extra utvecklings arbeten i-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00a92-142">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="00a92-143">Följande kommando rads post implementerar en spårnings åtgärd.</span><span class="sxs-lookup"><span data-stu-id="00a92-143">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="00a92-144">**PS> trace-Expression Stop-proc-File proc. log-Command Stop-proc anteckningar**</span><span class="sxs-lookup"><span data-stu-id="00a92-144">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="00a92-145">Skriver ett varnings meddelande</span><span class="sxs-lookup"><span data-stu-id="00a92-145">Writing a Warning Message</span></span>

<span data-ttu-id="00a92-146">Metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) används för att skriva en varning när cmdleten är på väg att utföra en åtgärd som kan ha ett oväntat resultat, till exempel skriva över en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="00a92-146">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="00a92-147">Följande kod från exempel Stop-Proc-cmdleten visar anropet till metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="00a92-147">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="00a92-148">Skriver ett förlopps meddelande</span><span class="sxs-lookup"><span data-stu-id="00a92-148">Writing a Progress Message</span></span>

<span data-ttu-id="00a92-149">[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) används för att skriva förlopps meddelanden när cmdlet-åtgärder tar en längre tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="00a92-149">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="00a92-150">Ett anrop till [system. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) skickar ett [system. Management. Automation. progressRecord](/dotnet/api/System.Management.Automation.ProgressRecord) -objekt som skickas till värd programmet för rendering till användaren.</span><span class="sxs-lookup"><span data-stu-id="00a92-150">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="00a92-151">Denna Stop-Proc-cmdlet innehåller inget anrop till metoden [system. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .</span><span class="sxs-lookup"><span data-stu-id="00a92-151">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="00a92-152">Följande kod är ett exempel på ett förlopps meddelande som skrivits av en cmdlet som försöker kopiera ett objekt.</span><span class="sxs-lookup"><span data-stu-id="00a92-152">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="00a92-153">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="00a92-153">Code Sample</span></span>

<span data-ttu-id="00a92-154">Den fullständiga exempel koden för C# finns i [StopProcessSample02-exempel](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="00a92-154">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="00a92-155">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="00a92-155">Define Object Types and Formatting</span></span>

<span data-ttu-id="00a92-156">Windows PowerShell skickar information mellan cmdlets med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="00a92-156">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="00a92-157">Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00a92-157">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="00a92-158">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="00a92-158">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="00a92-159">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00a92-159">Building the Cmdlet</span></span>

<span data-ttu-id="00a92-160">När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="00a92-160">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="00a92-161">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="00a92-161">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="00a92-162">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00a92-162">Testing the Cmdlet</span></span>

<span data-ttu-id="00a92-163">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="00a92-163">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="00a92-164">Nu ska vi testa exemplet Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00a92-164">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="00a92-165">Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="00a92-165">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="00a92-166">Följande kommando rads post använder Stop-Proc för att stoppa processen med namnet "NOTEPAD", ange utförliga meddelanden och skriva ut felsöknings information.</span><span class="sxs-lookup"><span data-stu-id="00a92-166">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    <span data-ttu-id="00a92-167">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00a92-167">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="00a92-168">Se även</span><span class="sxs-lookup"><span data-stu-id="00a92-168">See Also</span></span>

[<span data-ttu-id="00a92-169">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="00a92-169">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="00a92-170">Så här skapar du en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="00a92-170">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="00a92-171">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="00a92-171">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="00a92-172">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="00a92-172">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="00a92-173">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="00a92-173">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
