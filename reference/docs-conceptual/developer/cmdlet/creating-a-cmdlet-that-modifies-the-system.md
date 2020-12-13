---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en cmdlet som ändrar systemet
description: Skapa en cmdlet som ändrar systemet
ms.openlocfilehash: 757f2c97bb4b5dcf2fb633cd35fe52bc5f6c5cf9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355552"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="ab909-103">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="ab909-103">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="ab909-104">Ibland måste en cmdlet ändra systemets körnings tillstånd, inte bara läget för Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="ab909-104">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="ab909-105">I dessa fall bör cmdleten ge användaren möjlighet att bekräfta huruvida ändringen ska göras eller inte.</span><span class="sxs-lookup"><span data-stu-id="ab909-105">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="ab909-106">För att stödja en bekräftelse måste en cmdlet utföra två saker.</span><span class="sxs-lookup"><span data-stu-id="ab909-106">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="ab909-107">Deklarera att cmdleten stöder bekräftelse när du anger attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) genom att ange nyckelordet SupportsShouldProcess till `true` .</span><span class="sxs-lookup"><span data-stu-id="ab909-107">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="ab909-108">Anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) vid körningen av cmdleten (som visas i följande exempel).</span><span class="sxs-lookup"><span data-stu-id="ab909-108">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="ab909-109">Genom att få en bekräftelse visar en cmdlet de `Confirm` och de `WhatIf` parametrar som tillhandahålls av Windows PowerShell, och det uppfyller även utvecklings rikt linjerna för cmdlets (mer information om rikt linjer för utveckling av cmdletar finns i avsnittet om utvecklings rikt linjer för [cmdlets](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="ab909-109">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="ab909-110">Ändra systemet</span><span class="sxs-lookup"><span data-stu-id="ab909-110">Changing the System</span></span>

<span data-ttu-id="ab909-111">Syftet med att ändra systemet syftar på alla cmdletar som kan ändra systemets tillstånd utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab909-111">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="ab909-112">Att till exempel stoppa en process, aktivera eller inaktivera ett användar konto eller lägga till en rad i en databas tabell är alla ändringar i systemet som bör bekräftas.</span><span class="sxs-lookup"><span data-stu-id="ab909-112">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span>
<span data-ttu-id="ab909-113">Åtgärder som läser data eller upprättar tillfälliga anslutningar ändrar däremot inte systemet och behöver inte heller bekräfta.</span><span class="sxs-lookup"><span data-stu-id="ab909-113">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="ab909-114">Bekräftelse behövs inte heller för åtgärder vars inverkan är begränsad till i Windows PowerShell-körningsmiljön, till exempel `set-variable` .</span><span class="sxs-lookup"><span data-stu-id="ab909-114">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="ab909-115">Cmdletar som kan eller inte kan göra en beständig ändring bör deklarera `SupportsShouldProcess` och anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) endast om de ska göra en beständig ändring.</span><span class="sxs-lookup"><span data-stu-id="ab909-115">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="ab909-116">ShouldProcess-bekräftelse gäller endast för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ab909-116">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="ab909-117">Om ett kommando eller skript ändrar körnings statusen för ett system genom att anropa .NET-metoder eller-egenskaper direkt, eller genom att anropa program utanför Windows PowerShell, kommer den här bekräftelse formen inte att vara tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="ab909-117">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="ab909-118">StopProc-cmdleten</span><span class="sxs-lookup"><span data-stu-id="ab909-118">The StopProc Cmdlet</span></span>

<span data-ttu-id="ab909-119">I det här avsnittet beskrivs en Stop-Proc-cmdlet som försöker stoppa processer som hämtas med hjälp av Get-Proc-cmdlet (beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="ab909-119">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="ab909-120">Definiera cmdleten</span><span class="sxs-lookup"><span data-stu-id="ab909-120">Defining the Cmdlet</span></span>

<span data-ttu-id="ab909-121">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab909-121">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="ab909-122">Eftersom du skriver en cmdlet för att ändra systemet bör den namnges.</span><span class="sxs-lookup"><span data-stu-id="ab909-122">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="ab909-123">Den här cmdleten stoppar system processer, så verbet som väljs här är "stopp", som definieras av klassen [system. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , med Substantiv "proc" för att indikera att cmdleten stoppar processer.</span><span class="sxs-lookup"><span data-stu-id="ab909-123">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="ab909-124">Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="ab909-124">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ab909-125">Följande är klass definitionen för denna Stop-Proc-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab909-125">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="ab909-126">Observera att [](/dotnet/api/System.Management.Automation.CmdletAttribute) `SupportsShouldProcess` nyckelordet Attribute är inställt på `true` att aktivera cmdleten för att anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)i system. Management. Automation. CmdletAttribute-deklarationen.</span><span class="sxs-lookup"><span data-stu-id="ab909-126">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="ab909-127">Utan det här nyckelordet är `Confirm` `WhatIf` parametrarna och inte tillgängliga för användaren.</span><span class="sxs-lookup"><span data-stu-id="ab909-127">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="ab909-128">Extremt destruktiva åtgärder</span><span class="sxs-lookup"><span data-stu-id="ab909-128">Extremely Destructive Actions</span></span>

<span data-ttu-id="ab909-129">Vissa åtgärder är extremt destruktiva, t. ex. att omformatera en aktiv hård disk partition.</span><span class="sxs-lookup"><span data-stu-id="ab909-129">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="ab909-130">I dessa fall bör cmdleten anges `ConfirmImpact`  =  `ConfirmImpact.High` när du deklarerar attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ab909-130">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="ab909-131">Med den här inställningen tvingas cmdleten att begära användar bekräftelse även om användaren inte har angett `Confirm` parametern.</span><span class="sxs-lookup"><span data-stu-id="ab909-131">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="ab909-132">Cmdlet-utvecklare bör dock undvika att använda `ConfirmImpact` för åtgärder som är bara potentiellt destruktiva, t. ex. borttagning av ett användar konto.</span><span class="sxs-lookup"><span data-stu-id="ab909-132">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="ab909-133">Kom ihåg att om `ConfirmImpact` anges till [system. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) 
 **High**.</span><span class="sxs-lookup"><span data-stu-id="ab909-133">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact)
**High**.</span></span>

<span data-ttu-id="ab909-134">På samma sätt är vissa åtgärder troligen inte destruktiva, men de gör i teorin att ändra körnings läget för ett system utanför Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab909-134">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="ab909-135">Sådana cmdletar kan anges `ConfirmImpact` till [system. Management. Automation. Confirmimpact. Low](/dotnet/api/system.management.automation.confirmimpact).</span><span class="sxs-lookup"><span data-stu-id="ab909-135">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact).</span></span>
<span data-ttu-id="ab909-136">Detta kommer att kringgå bekräftelse begär Anden där användaren har bett att bekräfta endast medels Tor och hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="ab909-136">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="ab909-137">Definiera parametrar för system ändring</span><span class="sxs-lookup"><span data-stu-id="ab909-137">Defining Parameters for System Modification</span></span>

<span data-ttu-id="ab909-138">I det här avsnittet beskrivs hur du definierar cmdlet-parametrarna, inklusive de som behövs för att stödja system ändringar.</span><span class="sxs-lookup"><span data-stu-id="ab909-138">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="ab909-139">Se [lägga till parametrar som bearbetar kommando rads indata](./adding-parameters-that-process-command-line-input.md) om du behöver allmän information om att definiera parametrar.</span><span class="sxs-lookup"><span data-stu-id="ab909-139">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="ab909-140">Stop-Proc cmdleten definierar tre parametrar: `Name` , `Force` , och `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="ab909-140">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="ab909-141">`Name`Parametern motsvarar `Name` egenskapen för objektet bearbeta inobjekt.</span><span class="sxs-lookup"><span data-stu-id="ab909-141">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="ab909-142">Tänk på att `Name` parametern i det här exemplet är obligatorisk, eftersom cmdleten Miss kan köras om den inte har en namngiven process att stoppa.</span><span class="sxs-lookup"><span data-stu-id="ab909-142">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="ab909-143">`Force`Parametern gör att användaren kan åsidosätta anrop till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span><span class="sxs-lookup"><span data-stu-id="ab909-143">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="ab909-144">I själva verket ska alla cmdlets som anropar [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ha en `Force` parameter så att när anges `Force` , hoppar cmdleten anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och fortsätter med åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ab909-144">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="ab909-145">Tänk på att detta inte påverkar anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span><span class="sxs-lookup"><span data-stu-id="ab909-145">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="ab909-146">`PassThru`Parametern gör det möjligt för användaren att ange om cmdleten skickar ett utgående objekt genom pipelinen, i det här fallet när en process har stoppats.</span><span class="sxs-lookup"><span data-stu-id="ab909-146">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="ab909-147">Tänk på att den här parametern är kopplad till själva cmdleten i stället för till en egenskap i objektet.</span><span class="sxs-lookup"><span data-stu-id="ab909-147">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="ab909-148">Här är parameter deklarationen för Stop-Proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab909-148">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ab909-149">Åsidosätta en metod för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="ab909-149">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ab909-150">Cmdleten måste åsidosätta en metod för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="ab909-150">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="ab909-151">Följande kod illustrerar åsidosättningen [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) som används i exempel-Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab909-151">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="ab909-152">För varje begärt process namn säkerställer den här metoden att processen inte är en särskild process, försöker stoppa processen och skickar sedan ett utgående objekt om `PassThru` parametern anges.</span><span class="sxs-lookup"><span data-stu-id="ab909-152">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="ab909-153">Anropar metoden ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="ab909-153">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="ab909-154">Metoden för bearbetning av indata för cmdleten ska anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att bekräfta körningen av en åtgärd innan en ändring (till exempel borttagning av filer) görs till systemets körnings tillstånd.</span><span class="sxs-lookup"><span data-stu-id="ab909-154">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="ab909-155">Detta gör att Windows PowerShell-körningsmiljön kan tillhandahålla rätt "WhatIf" och "Confirm"-beteende i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ab909-155">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="ab909-156">Om en cmdlet anger att den stöder ska bearbeta och Miss lyckas med att göra ett anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , kan användaren ändra systemet oväntat.</span><span class="sxs-lookup"><span data-stu-id="ab909-156">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="ab909-157">Anropet till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till alla kommando rads inställningar eller variabler för att fastställa vad som ska visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="ab909-157">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="ab909-158">I följande exempel visas anropet till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) i exemplet Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab909-158">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="ab909-159">Anropar metoden ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="ab909-159">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="ab909-160">Anropet till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) skickar ett sekundärt meddelande till användaren.</span><span class="sxs-lookup"><span data-stu-id="ab909-160">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="ab909-161">Anropet görs efter anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returnerar `true` och om `Force` parametern inte har angetts till `true` .</span><span class="sxs-lookup"><span data-stu-id="ab909-161">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="ab909-162">Användaren kan sedan ge feedback för att säga om åtgärden ska fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ab909-162">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="ab909-163">Cmdleten anropar [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) som en ytterligare kontroll för potentiellt skadliga system ändringar eller när du vill ge användaren ja-till-alla-och inga-till-alla-alternativ.</span><span class="sxs-lookup"><span data-stu-id="ab909-163">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="ab909-164">I följande exempel visas anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) i exemplet Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab909-164">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="ab909-165">Stoppa bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="ab909-165">Stopping Input Processing</span></span>

<span data-ttu-id="ab909-166">Metoden för bearbetning av indata för en cmdlet som gör system ändringar måste tillhandahålla ett sätt att stoppa bearbetningen av indata.</span><span class="sxs-lookup"><span data-stu-id="ab909-166">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="ab909-167">Om detta Stop-Proc-cmdlet görs ett anrop från metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) till metoden [system. Diagnostics. process. kill \*](/dotnet/api/System.Diagnostics.Process.Kill) .</span><span class="sxs-lookup"><span data-stu-id="ab909-167">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="ab909-168">Eftersom `PassThru` parametern är inställd på `true` , anropar [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) också [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) för att skicka processobjektet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="ab909-168">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ab909-169">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="ab909-169">Code Sample</span></span>

<span data-ttu-id="ab909-170">Den fullständiga exempel koden för C# finns i [StopProcessSample01-exempel](./stopprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="ab909-170">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ab909-171">Definiera objekt typer och formatering</span><span class="sxs-lookup"><span data-stu-id="ab909-171">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ab909-172">Windows PowerShell skickar information mellan cmdlets med .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="ab909-172">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="ab909-173">Därför kan en cmdlet behöva definiera en egen typ, eller så kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab909-173">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ab909-174">Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ab909-174">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ab909-175">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="ab909-175">Building the Cmdlet</span></span>

<span data-ttu-id="ab909-176">När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="ab909-176">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ab909-177">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ab909-177">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ab909-178">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="ab909-178">Testing the Cmdlet</span></span>

<span data-ttu-id="ab909-179">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ab909-179">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="ab909-180">Här följer flera tester som testar Stop-Proc-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab909-180">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="ab909-181">Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ab909-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="ab909-182">Starta Windows PowerShell och Använd Stop-Proc-cmdleten för att stoppa bearbetningen som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="ab909-182">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="ab909-183">Eftersom cmdleten anger `Name` parametern som obligatorisk, frågar cmdleten för parametern.</span><span class="sxs-lookup"><span data-stu-id="ab909-183">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="ab909-184">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="ab909-184">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="ab909-185">Nu ska vi använda cmdleten för att stoppa processen med namnet "NOTEPAD".</span><span class="sxs-lookup"><span data-stu-id="ab909-185">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="ab909-186">I cmdleten uppmanas du att bekräfta åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ab909-186">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

    <span data-ttu-id="ab909-187">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="ab909-187">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="ab909-188">Använd Stop-Proc som visas för att stoppa den kritiska processen med namnet "WINLOGON".</span><span class="sxs-lookup"><span data-stu-id="ab909-188">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="ab909-189">Du uppmanas och varnas om att utföra den här åtgärden eftersom det gör att operativ systemet startas om.</span><span class="sxs-lookup"><span data-stu-id="ab909-189">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    <span data-ttu-id="ab909-190">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="ab909-190">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="ab909-191">Nu ska vi försöka stoppa WINLOGON-processen utan att ta emot en varning.</span><span class="sxs-lookup"><span data-stu-id="ab909-191">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="ab909-192">Tänk på att den här kommando posten använder `Force` parametern för att åsidosätta varningen.</span><span class="sxs-lookup"><span data-stu-id="ab909-192">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    <span data-ttu-id="ab909-193">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="ab909-193">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="ab909-194">Se även</span><span class="sxs-lookup"><span data-stu-id="ab909-194">See Also</span></span>

[<span data-ttu-id="ab909-195">Lägga till parametrar som bearbetar Command-Line-Indatatyp</span><span class="sxs-lookup"><span data-stu-id="ab909-195">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="ab909-196">[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ab909-196">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="ab909-197">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ab909-197">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="ab909-198">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ab909-198">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="ab909-199">Cmdlet-exempel</span><span class="sxs-lookup"><span data-stu-id="ab909-199">Cmdlet Samples</span></span>](./cmdlet-samples.md)
