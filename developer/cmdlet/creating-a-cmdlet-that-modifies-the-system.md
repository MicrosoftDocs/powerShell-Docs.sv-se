---
title: Skapa en Cmdlet som ändrar systemet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: a4fa9ce52855928679a2425f24f2e49a68030c63
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854921"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="c3e85-102">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="c3e85-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="c3e85-103">Ibland ändra en cmdlet körs av systemet, inte bara Tillståndet för Windows PowerShell-runtime.</span><span class="sxs-lookup"><span data-stu-id="c3e85-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="c3e85-104">I dessa fall kan bör cmdleten Tillåt att användaren en chans att bekräfta huruvida att genomföra ändringen.</span><span class="sxs-lookup"><span data-stu-id="c3e85-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="c3e85-105">En cmdlet måste göra två saker för att stödja bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="c3e85-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="c3e85-106">Deklarera att cmdleten stöder bekräftelse när du anger den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut genom att ställa in nyckelordet SupportsShouldProcess `true`.</span><span class="sxs-lookup"><span data-stu-id="c3e85-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="c3e85-107">Anropa [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) under körningen av cmdlet: en (som visas i följande exempel).</span><span class="sxs-lookup"><span data-stu-id="c3e85-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="c3e85-108">Som stöd för bekräftelse, en cmdlet exponerar den `Confirm` och `WhatIf` parametrar som tillhandahålls av Windows PowerShell och uppfyller också utveckling riktlinjer för cmdlet: ar (Mer information om cmdlet utveckling riktlinjer finns i [ Riktlinjer för utveckling av cmdlet](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="c3e85-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="c3e85-109">Ändra systemet</span><span class="sxs-lookup"><span data-stu-id="c3e85-109">Changing the System</span></span>

<span data-ttu-id="c3e85-110">Av ”ändra systemet” syftar på alla cmdletar som potentiellt ändrar tillståndet för systemet utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3e85-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="c3e85-111">Exempelvis stoppa en process, aktivera eller inaktivera ett användarkonto eller att lägga till en rad i en databastabell är alla ändringar som ska bekräftas.</span><span class="sxs-lookup"><span data-stu-id="c3e85-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="c3e85-112">Däremot ändra inte systemet åtgärder som läser data eller upprätta tillfälliga anslutningar och allmänt kräver inte bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="c3e85-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="c3e85-113">Bekräftelse krävs inte heller för åtgärder som är begränsad till i Windows PowerShell-körning, till exempel `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="c3e85-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="c3e85-114">Cmdletar som kan eller inte kan göra en permanent förändring bör deklarera `SupportsShouldProcess` och anropa [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) endast om de är på väg att göra en permanent ändring.</span><span class="sxs-lookup"><span data-stu-id="c3e85-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="c3e85-115">ShouldProcess bekräftelse gäller enbart för cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="c3e85-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="c3e85-116">Om ett kommando eller skript ändrar driftläget för ett system genom att anropa .NET-metoder, egenskaper eller direkt eller genom att anropa program utanför Windows PowerShell, den här typen av bekräftelse inte är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="c3e85-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="c3e85-117">Cmdleten StopProc</span><span class="sxs-lookup"><span data-stu-id="c3e85-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="c3e85-118">Det här avsnittet beskrivs en Stop-Proc-cmdlet som försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="c3e85-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="c3e85-119">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="c3e85-119">Defining the Cmdlet</span></span>

<span data-ttu-id="c3e85-120">Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="c3e85-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="c3e85-121">Eftersom du skriver en cmdlet om du vill ändra systemet bör den vara namn därefter.</span><span class="sxs-lookup"><span data-stu-id="c3e85-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="c3e85-122">Den här cmdleten stoppas systemprocesser, så verb valt här heter ”stoppa”, som definieras av den [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klassen, substantiv ”Proc” för att indikera att cmdleten stoppar processer.</span><span class="sxs-lookup"><span data-stu-id="c3e85-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="c3e85-123">Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c3e85-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="c3e85-124">Följande är klassdefinitionen för denna cmdlet Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="c3e85-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="c3e85-125">Tänk som i den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklarationen den `SupportsShouldProcess` nyckelord för attribut har angetts till `true` att aktivera cmdlet: en att göra anrop till [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="c3e85-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="c3e85-126">Utan den här uppsättningen med nyckelord, den `Confirm` och `WhatIf` parametrar är inte tillgänglig för användaren.</span><span class="sxs-lookup"><span data-stu-id="c3e85-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="c3e85-127">Extremt destruktiva åtgärder</span><span class="sxs-lookup"><span data-stu-id="c3e85-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="c3e85-128">Vissa åtgärder är extremt destruktiv, till exempel formatera om en aktiv hårddiskpartition.</span><span class="sxs-lookup"><span data-stu-id="c3e85-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="c3e85-129">I dessa fall kan cmdleten bör ange `ConfirmImpact`  =  `ConfirmImpact.High` när deklarera den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut.</span><span class="sxs-lookup"><span data-stu-id="c3e85-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="c3e85-130">Den här inställningen tvingar cmdlet: en till begäran om användaren ska bekräfta även om användaren inte har angett den `Confirm` parametern.</span><span class="sxs-lookup"><span data-stu-id="c3e85-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="c3e85-131">Cmdlet: en utvecklare bör dock undvika överanvändning av `ConfirmImpact` för åtgärder som är bara potentiellt skadliga, till exempel ta bort ett användarkonto.</span><span class="sxs-lookup"><span data-stu-id="c3e85-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="c3e85-132">Kom ihåg att om `ConfirmImpact` är inställd på [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span><span class="sxs-lookup"><span data-stu-id="c3e85-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="c3e85-133">Vissa åtgärder är inte troligt att destruktiva, även om de i teorin ändra driftläget för ett system utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3e85-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="c3e85-134">Dessa cmdletar kan ställa in `ConfirmImpact` till [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="c3e85-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="c3e85-135">Detta kommer kringgå begäranden om händelsebekräftelse där användaren har bett att bekräfta endast påverkan medium och hög inverkan.</span><span class="sxs-lookup"><span data-stu-id="c3e85-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="c3e85-136">Definiera parametrar för ändring av systemet</span><span class="sxs-lookup"><span data-stu-id="c3e85-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="c3e85-137">Det här avsnittet beskriver hur du definierar cmdlet-parametrarna, inklusive de som behövs för att supportsystem ändring.</span><span class="sxs-lookup"><span data-stu-id="c3e85-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="c3e85-138">Se [att lägga till parametrar som processen CommandLine indata](./adding-parameters-that-process-command-line-input.md) om du behöver allmän information om hur du definierar parametrar.</span><span class="sxs-lookup"><span data-stu-id="c3e85-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="c3e85-139">Cmdlet Stop-Proc definierar tre parametrar: `Name`, `Force`, och `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="c3e85-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="c3e85-140">Den `Name` parametern motsvarar den `Name` egenskapen för inkommande processobjektet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="c3e85-141">Tänk på som det `Name` parametern i det här exemplet är obligatorisk, som cmdleten misslyckas om den inte har en namngiven process för att stoppa.</span><span class="sxs-lookup"><span data-stu-id="c3e85-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="c3e85-142">Den `Force` parameter gör det möjligt för användarna att åsidosätta anrop till [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="c3e85-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="c3e85-143">I själva verket en cmdlet som anropar [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) bör ha en `Force` parametern så att när `Force` anges cmdleten hoppar över anropet till [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och fortsätter med åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c3e85-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="c3e85-144">Observera att detta inte påverkar anrop till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="c3e85-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="c3e85-145">Den `PassThru` parameter gör det möjligt för användaren att ange om cmdlet: en skickar ett objekt genom pipelinen och i det här fallet när en process har stoppats.</span><span class="sxs-lookup"><span data-stu-id="c3e85-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="c3e85-146">Tänk på att den här parametern är knutna till cmdleten själv i stället för till en egenskap för indataobjektet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="c3e85-147">Här är parameterdeklaration för cmdleten Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="c3e85-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="c3e85-148">Åsidosätta indata metoden bearbetades</span><span class="sxs-lookup"><span data-stu-id="c3e85-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="c3e85-149">Cmdlet: en måste åsidosätta indata metoden bearbetades.</span><span class="sxs-lookup"><span data-stu-id="c3e85-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="c3e85-150">Följande kod visar den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) åsidosättning som används i exemplet Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="c3e85-151">För var och en begärd processnamn, den här metoden garanterar att processen inte är en särskild process, försöker stoppa processen och skickar sedan ett objekt om de `PassThru` parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="c3e85-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="c3e85-152">Att anropa metoden ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="c3e85-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="c3e85-153">Indata bearbetning av-metoden för cmdlet: ska anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod för att bekräfta körning av en åtgärd innan en ändring (till exempel ta bort filer) görs till körtillstånd av systemet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="c3e85-154">På så sätt kan Windows PowerShell-körning för att ange ”WhatIf” och ”Confirm”-beteendet i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="c3e85-155">Om en cmdlet säger att den stöder ska bearbetas och inte kan se den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropa måste användaren kan ändra systemet oväntat.</span><span class="sxs-lookup"><span data-stu-id="c3e85-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="c3e85-156">Anropet till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) skickar namnet på resursen som ska ändras för användaren med Windows PowerShell-körning med hänsyn till eventuella kommandoradsinställningar eller variabler avgöra vad som ska visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="c3e85-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="c3e85-157">I följande exempel visas anropet till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från åsidosättningen av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -metod i exemplet Stoppa Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="c3e85-158">Att anropa metoden ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="c3e85-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="c3e85-159">Anropet till den [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden skickar ett sekundära meddelande för användaren.</span><span class="sxs-lookup"><span data-stu-id="c3e85-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="c3e85-160">Det här anropet görs efter anropet till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returnerar `true` och om den `Force` parametern har inte angetts `true`.</span><span class="sxs-lookup"><span data-stu-id="c3e85-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="c3e85-161">Användaren kan sedan ge feedback om du vill säga om åtgärden bör vara fortsatt.</span><span class="sxs-lookup"><span data-stu-id="c3e85-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="c3e85-162">Cmdlet-anrop [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) som ytterligare en kontroll för ändringar av potentiellt skadliga system eller när du vill ange Ja till alla och Nej till alla alternativ för användaren.</span><span class="sxs-lookup"><span data-stu-id="c3e85-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="c3e85-163">I följande exempel visas anropet till [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) från åsidosättningen av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -metod i exemplet Stoppa Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="c3e85-164">Stoppar inkommande bearbetning</span><span class="sxs-lookup"><span data-stu-id="c3e85-164">Stopping Input Processing</span></span>

<span data-ttu-id="c3e85-165">Indata bearbetning av-metoden för en cmdlet som ändrar system måste ange ett sätt att stoppa bearbetningen av indata.</span><span class="sxs-lookup"><span data-stu-id="c3e85-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="c3e85-166">När det gäller denna cmdlet Stop-processen, ett anrop görs från den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att den [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) metod.</span><span class="sxs-lookup"><span data-stu-id="c3e85-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="c3e85-167">Eftersom den `PassThru` parametern är inställd på `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) också anropar [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) att skicka processobjektet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c3e85-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c3e85-168">Kodexempel</span><span class="sxs-lookup"><span data-stu-id="c3e85-168">Code Sample</span></span>

<span data-ttu-id="c3e85-169">För hela C# exempelkoden, se [StopProcessSample01 exempel](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c3e85-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="c3e85-170">Definiera objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="c3e85-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="c3e85-171">Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="c3e85-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="c3e85-172">Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3e85-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="c3e85-173">Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="c3e85-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="c3e85-174">Att skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="c3e85-174">Building the Cmdlet</span></span>

<span data-ttu-id="c3e85-175">När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="c3e85-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="c3e85-176">Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="c3e85-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="c3e85-177">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="c3e85-177">Testing the Cmdlet</span></span>

<span data-ttu-id="c3e85-178">När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="c3e85-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="c3e85-179">Här följer flera tester som testar cmdlet Stop-processen.</span><span class="sxs-lookup"><span data-stu-id="c3e85-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="c3e85-180">Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c3e85-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="c3e85-181">Starta Windows PowerShell och Använd cmdleten Stop-processen för att stoppa bearbetningen enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="c3e85-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="c3e85-182">Eftersom cmdlet: en anger den `Name` parametern som obligatorisk, cmdlet-förfrågningarna för parametern.</span><span class="sxs-lookup"><span data-stu-id="c3e85-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="c3e85-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="c3e85-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="c3e85-184">Nu ska vi använda cmdlet för att stoppa processen med namnet ”ANTECKNINGAR”.</span><span class="sxs-lookup"><span data-stu-id="c3e85-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="c3e85-185">Cmdlet: en ber dig att bekräfta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="c3e85-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="c3e85-186">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="c3e85-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="c3e85-187">Använd Stop-processen som du ser för att stoppa kritiska processen med namnet ”WINLOGON”.</span><span class="sxs-lookup"><span data-stu-id="c3e85-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="c3e85-188">Du uppmanas och om hur du utför den här åtgärden eftersom det leder operativsystemet för att starta om en varning.</span><span class="sxs-lookup"><span data-stu-id="c3e85-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="c3e85-189">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="c3e85-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="c3e85-190">Nu ska vi prova nu att stoppa processen WINLOGON utan att du får en varning.</span><span class="sxs-lookup"><span data-stu-id="c3e85-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="c3e85-191">Tänk på att den här posten kommando använder de `Force` parametern åsidosätta varningen.</span><span class="sxs-lookup"><span data-stu-id="c3e85-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="c3e85-192">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="c3e85-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="c3e85-193">Se även</span><span class="sxs-lookup"><span data-stu-id="c3e85-193">See Also</span></span>

[<span data-ttu-id="c3e85-194">Att lägga till parametrar som bearbetar av kommandoraden</span><span class="sxs-lookup"><span data-stu-id="c3e85-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="c3e85-195">Utöka objekttyper och formatering</span><span class="sxs-lookup"><span data-stu-id="c3e85-195">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="c3e85-196">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="c3e85-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="c3e85-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c3e85-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="c3e85-198">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="c3e85-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)