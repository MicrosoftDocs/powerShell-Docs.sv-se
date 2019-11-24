---
title: Skapa en cmdlet som ändrar systemet | Microsoft Docs
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
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356457"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="00dd4-102">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="00dd4-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="00dd4-103">Ibland måste en cmdlet ändra systemets körnings tillstånd, inte bara läget för Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="00dd4-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="00dd4-104">I dessa fall bör cmdleten ge användaren möjlighet att bekräfta huruvida ändringen ska göras eller inte.</span><span class="sxs-lookup"><span data-stu-id="00dd4-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="00dd4-105">För att stödja en bekräftelse måste en cmdlet utföra två saker.</span><span class="sxs-lookup"><span data-stu-id="00dd4-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="00dd4-106">Deklarera att cmdleten stöder bekräftelse när du anger attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) genom att ange nyckelordet SupportsShouldProcess till `true`.</span><span class="sxs-lookup"><span data-stu-id="00dd4-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="00dd4-107">Anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) vid körningen av cmdleten (som visas i följande exempel).</span><span class="sxs-lookup"><span data-stu-id="00dd4-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="00dd4-108">Genom att tillhandahålla en bekräftelse visar en cmdlet de `Confirm` och `WhatIf` parametrar som tillhandahålls av Windows PowerShell och som också uppfyller utvecklings rikt linjerna för cmdlets (mer information om rikt linjer för utveckling av cmdlets finns i avsnittet om utvecklings rikt linjer [för cmdlets](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="00dd4-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="00dd4-109">Ändra systemet</span><span class="sxs-lookup"><span data-stu-id="00dd4-109">Changing the System</span></span>

<span data-ttu-id="00dd4-110">Syftet med att ändra systemet syftar på alla cmdletar som kan ändra systemets tillstånd utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00dd4-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="00dd4-111">Att till exempel stoppa en process, aktivera eller inaktivera ett användar konto eller lägga till en rad i en databas tabell är alla ändringar i systemet som bör bekräftas.</span><span class="sxs-lookup"><span data-stu-id="00dd4-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="00dd4-112">Åtgärder som läser data eller upprättar tillfälliga anslutningar ändrar däremot inte systemet och behöver inte heller bekräfta.</span><span class="sxs-lookup"><span data-stu-id="00dd4-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="00dd4-113">Bekräftelse behövs inte heller för åtgärder vars inverkan är begränsad till i Windows PowerShell-körningsmiljön, till exempel `set-variable`.</span><span class="sxs-lookup"><span data-stu-id="00dd4-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="00dd4-114">Cmdletar som kan eller inte kan göra en beständig ändring bör deklarera `SupportsShouldProcess` och anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) endast om de ska göra en beständig ändring.</span><span class="sxs-lookup"><span data-stu-id="00dd4-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="00dd4-115">ShouldProcess-bekräftelse gäller endast för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="00dd4-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="00dd4-116">Om ett kommando eller skript ändrar körnings statusen för ett system genom att anropa .NET-metoder eller-egenskaper direkt, eller genom att anropa program utanför Windows PowerShell, kommer den här bekräftelse formen inte att vara tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="00dd4-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="00dd4-117">StopProc-cmdleten</span><span class="sxs-lookup"><span data-stu-id="00dd4-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="00dd4-118">I det här avsnittet beskrivs en stop-proc-cmdlet som försöker stoppa processer som hämtas med cmdleten Get-proc (beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="00dd4-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="00dd4-119">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="00dd4-119">Defining the Cmdlet</span></span>

<span data-ttu-id="00dd4-120">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00dd4-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="00dd4-121">Eftersom du skriver en cmdlet för att ändra systemet bör den namnges.</span><span class="sxs-lookup"><span data-stu-id="00dd4-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="00dd4-122">Den här cmdleten stoppar system processer, så verbet som väljs här är "stopp", som definieras av klassen [system. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , med Substantiv "proc" för att indikera att cmdleten stoppar processer.</span><span class="sxs-lookup"><span data-stu-id="00dd4-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="00dd4-123">Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="00dd4-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="00dd4-124">Följande är klass definitionen för den här Stop-proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00dd4-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="00dd4-125">Tänk på att nyckelordet `SupportsShouldProcess` attribut är inställt på `true` för att aktivera cmdlet: en för att anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)i [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -deklarationen.</span><span class="sxs-lookup"><span data-stu-id="00dd4-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="00dd4-126">Utan det här nyckelordet är parametrarna för `Confirm` och `WhatIf` inte tillgängliga för användaren.</span><span class="sxs-lookup"><span data-stu-id="00dd4-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="00dd4-127">Extremt destruktiva åtgärder</span><span class="sxs-lookup"><span data-stu-id="00dd4-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="00dd4-128">Vissa åtgärder är extremt destruktiva, t. ex. att omformatera en aktiv hård disk partition.</span><span class="sxs-lookup"><span data-stu-id="00dd4-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="00dd4-129">I dessa fall ska cmdleten ange `ConfirmImpact` = `ConfirmImpact.High` när du deklarerar attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="00dd4-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="00dd4-130">Med den här inställningen tvingas cmdleten att begära användar bekräftelse även om användaren inte har angett parametern `Confirm`.</span><span class="sxs-lookup"><span data-stu-id="00dd4-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="00dd4-131">Cmdlet-utvecklare bör dock undvika att använda `ConfirmImpact` för åtgärder som är bara potentiellt destruktiva, t. ex. borttagning av ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="00dd4-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="00dd4-132">Kom ihåg att om `ConfirmImpact` har angetts till [system. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span><span class="sxs-lookup"><span data-stu-id="00dd4-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="00dd4-133">På samma sätt är vissa åtgärder troligen inte destruktiva, men de gör i teorin att ändra körnings läget för ett system utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00dd4-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="00dd4-134">Sådana cmdlets kan ange `ConfirmImpact` till [system. Management. Automation. Confirmimpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="00dd4-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="00dd4-135">Detta kommer att kringgå bekräftelse begär Anden där användaren har bett att bekräfta endast medels Tor och hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="00dd4-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="00dd4-136">Definiera parametrar för system ändring</span><span class="sxs-lookup"><span data-stu-id="00dd4-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="00dd4-137">I det här avsnittet beskrivs hur du definierar cmdlet-parametrarna, inklusive de som behövs för att stödja system ändringar.</span><span class="sxs-lookup"><span data-stu-id="00dd4-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="00dd4-138">Se [lägga till parametrar som bearbetar kommando rads indata](./adding-parameters-that-process-command-line-input.md) om du behöver allmän information om att definiera parametrar.</span><span class="sxs-lookup"><span data-stu-id="00dd4-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="00dd4-139">Cmdleten Stop-proc definierar tre parametrar: `Name`, `Force`och `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="00dd4-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="00dd4-140">Parametern `Name` motsvarar egenskapen `Name` för det indataporta objektet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="00dd4-141">Tänk på att parametern `Name` i det här exemplet är obligatorisk, eftersom cmdleten Miss kan köras om den inte har en namngiven process att stoppa.</span><span class="sxs-lookup"><span data-stu-id="00dd4-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="00dd4-142">Parametern `Force` gör att användaren kan åsidosätta anrop till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="00dd4-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="00dd4-143">I själva verket ska alla cmdlets som anropar [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ha en `Force`-parameter så att när `Force` anges hoppar cmdleten över anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och fortsätter med åtgärden.</span><span class="sxs-lookup"><span data-stu-id="00dd4-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="00dd4-144">Tänk på att detta inte påverkar anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="00dd4-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="00dd4-145">Parametern `PassThru` gör att användaren kan ange om cmdleten skickar ett utgående objekt genom pipelinen, i det här fallet när en process har stoppats.</span><span class="sxs-lookup"><span data-stu-id="00dd4-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="00dd4-146">Tänk på att den här parametern är kopplad till själva cmdleten i stället för till en egenskap i objektet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="00dd4-147">Här är parameter deklarationen för cmdleten Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="00dd4-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="00dd4-148">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="00dd4-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="00dd4-149">Cmdleten måste åsidosätta en metod för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="00dd4-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="00dd4-150">Följande kod illustrerar åsidosättningen [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) som används i samplet Stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="00dd4-151">För varje begärt process namn säkerställer den här metoden att processen inte är en särskild process, försöker stoppa processen och skickar sedan ett utgående objekt om parametern `PassThru` anges.</span><span class="sxs-lookup"><span data-stu-id="00dd4-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="00dd4-152">Anropar metoden ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="00dd4-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="00dd4-153">Metoden för bearbetning av indata för cmdleten ska anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att bekräfta körningen av en åtgärd innan en ändring (till exempel borttagning av filer) görs till systemets körnings tillstånd.</span><span class="sxs-lookup"><span data-stu-id="00dd4-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="00dd4-154">Detta gör att Windows PowerShell-körningsmiljön kan tillhandahålla rätt "WhatIf" och "Confirm"-beteende i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="00dd4-155">Om en cmdlet anger att den stöder ska bearbeta och Miss lyckas med att göra ett anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , kan användaren ändra systemet oväntat.</span><span class="sxs-lookup"><span data-stu-id="00dd4-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="00dd4-156">Anropet till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till alla kommando rads inställningar eller variabler för att fastställa vad som ska visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="00dd4-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="00dd4-157">I följande exempel visas anropet till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) i samplet Stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="00dd4-158">Anropar metoden ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="00dd4-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="00dd4-159">Anropet till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) skickar ett sekundärt meddelande till användaren.</span><span class="sxs-lookup"><span data-stu-id="00dd4-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="00dd4-160">Anropet görs efter anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returnerar `true` och om parametern `Force` inte har angetts till `true`.</span><span class="sxs-lookup"><span data-stu-id="00dd4-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="00dd4-161">Användaren kan sedan ge feedback för att säga om åtgärden ska fortsätta.</span><span class="sxs-lookup"><span data-stu-id="00dd4-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="00dd4-162">Cmdleten anropar [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) som en ytterligare kontroll för potentiellt skadliga system ändringar eller när du vill ge användaren ja-till-alla-och inga-till-alla-alternativ.</span><span class="sxs-lookup"><span data-stu-id="00dd4-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="00dd4-163">I följande exempel visas anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) i samplet Stop-proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="00dd4-164">Stoppa bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="00dd4-164">Stopping Input Processing</span></span>

<span data-ttu-id="00dd4-165">Metoden för bearbetning av indata för en cmdlet som gör system ändringar måste tillhandahålla ett sätt att stoppa bearbetningen av indata.</span><span class="sxs-lookup"><span data-stu-id="00dd4-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="00dd4-166">I händelse av denna Stop-proc-cmdlet görs ett anrop från metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) till metoden [system. Diagnostics. process. kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="00dd4-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="00dd4-167">Eftersom parametern `PassThru` anges till `true`, anropar [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) också [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) för att skicka processobjektet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="00dd4-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="00dd4-168">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="00dd4-168">Code Sample</span></span>

<span data-ttu-id="00dd4-169">Den fullständiga C# exempel koden finns i [StopProcessSample01-exempel](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="00dd4-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="00dd4-170">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="00dd4-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="00dd4-171">Windows PowerShell skickar information mellan cmdlets med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="00dd4-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="00dd4-172">Därför kan en cmdlet behöva definiera en egen typ, eller så kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="00dd4-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="00dd4-173">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="00dd4-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="00dd4-174">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00dd4-174">Building the Cmdlet</span></span>

<span data-ttu-id="00dd4-175">När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="00dd4-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="00dd4-176">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="00dd4-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="00dd4-177">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="00dd4-177">Testing the Cmdlet</span></span>

<span data-ttu-id="00dd4-178">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="00dd4-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="00dd4-179">Här följer flera test som testar cmdleten Stop-proc.</span><span class="sxs-lookup"><span data-stu-id="00dd4-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="00dd4-180">Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="00dd4-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="00dd4-181">Starta Windows PowerShell och använd Stop-proc-cmdlet: en för att stoppa bearbetningen som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="00dd4-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="00dd4-182">Eftersom cmdleten anger den `Name` parametern som obligatorisk, frågar cmdleten för parametern.</span><span class="sxs-lookup"><span data-stu-id="00dd4-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="00dd4-183">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00dd4-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="00dd4-184">Nu ska vi använda cmdleten för att stoppa processen med namnet "NOTEPAD".</span><span class="sxs-lookup"><span data-stu-id="00dd4-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="00dd4-185">I cmdleten uppmanas du att bekräfta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="00dd4-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="00dd4-186">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00dd4-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="00dd4-187">Använd Stop-proc som visas för att stoppa den kritiska processen med namnet "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="00dd4-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="00dd4-188">Du uppmanas och varnas om att utföra den här åtgärden eftersom det gör att operativ systemet startas om.</span><span class="sxs-lookup"><span data-stu-id="00dd4-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="00dd4-189">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00dd4-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="00dd4-190">Nu ska vi försöka stoppa WINLOGON-processen utan att ta emot en varning.</span><span class="sxs-lookup"><span data-stu-id="00dd4-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="00dd4-191">Tänk på att den här kommando posten använder parametern `Force` för att åsidosätta varningen.</span><span class="sxs-lookup"><span data-stu-id="00dd4-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="00dd4-192">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="00dd4-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="00dd4-193">Se även</span><span class="sxs-lookup"><span data-stu-id="00dd4-193">See Also</span></span>

[<span data-ttu-id="00dd4-194">Lägga till parametrar som bearbetar kommando rads indatatyper</span><span class="sxs-lookup"><span data-stu-id="00dd4-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="00dd4-195">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="00dd4-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="00dd4-196">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="00dd4-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="00dd4-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="00dd4-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="00dd4-198">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="00dd4-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)