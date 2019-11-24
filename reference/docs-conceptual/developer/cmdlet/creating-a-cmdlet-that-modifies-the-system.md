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
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Skapa en cmdlet som ändrar systemet

Ibland måste en cmdlet ändra systemets körnings tillstånd, inte bara läget för Windows PowerShell-körningsmiljön. I dessa fall bör cmdleten ge användaren möjlighet att bekräfta huruvida ändringen ska göras eller inte.

För att stödja en bekräftelse måste en cmdlet utföra två saker.

- Deklarera att cmdleten stöder bekräftelse när du anger attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) genom att ange nyckelordet SupportsShouldProcess till `true`.

- Anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) vid körningen av cmdleten (som visas i följande exempel).

Genom att tillhandahålla en bekräftelse visar en cmdlet de `Confirm` och `WhatIf` parametrar som tillhandahålls av Windows PowerShell och som också uppfyller utvecklings rikt linjerna för cmdlets (mer information om rikt linjer för utveckling av cmdlets finns i avsnittet om utvecklings rikt linjer [för cmdlets](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Ändra systemet

Syftet med att ändra systemet syftar på alla cmdletar som kan ändra systemets tillstånd utanför Windows PowerShell. Att till exempel stoppa en process, aktivera eller inaktivera ett användar konto eller lägga till en rad i en databas tabell är alla ändringar i systemet som bör bekräftas. Åtgärder som läser data eller upprättar tillfälliga anslutningar ändrar däremot inte systemet och behöver inte heller bekräfta. Bekräftelse behövs inte heller för åtgärder vars inverkan är begränsad till i Windows PowerShell-körningsmiljön, till exempel `set-variable`. Cmdletar som kan eller inte kan göra en beständig ändring bör deklarera `SupportsShouldProcess` och anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) endast om de ska göra en beständig ändring.

> [!NOTE]
> ShouldProcess-bekräftelse gäller endast för cmdletar. Om ett kommando eller skript ändrar körnings statusen för ett system genom att anropa .NET-metoder eller-egenskaper direkt, eller genom att anropa program utanför Windows PowerShell, kommer den här bekräftelse formen inte att vara tillgänglig.

## <a name="the-stopproc-cmdlet"></a>StopProc-cmdleten

I det här avsnittet beskrivs en stop-proc-cmdlet som försöker stoppa processer som hämtas med cmdleten Get-proc (beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten. Eftersom du skriver en cmdlet för att ändra systemet bör den namnges. Den här cmdleten stoppar system processer, så verbet som väljs här är "stopp", som definieras av klassen [system. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , med Substantiv "proc" för att indikera att cmdleten stoppar processer. Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

Följande är klass definitionen för den här Stop-proc-cmdleten.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tänk på att nyckelordet `SupportsShouldProcess` attribut är inställt på `true` för att aktivera cmdlet: en för att anropa [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)i [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) -deklarationen. Utan det här nyckelordet är parametrarna för `Confirm` och `WhatIf` inte tillgängliga för användaren.

### <a name="extremely-destructive-actions"></a>Extremt destruktiva åtgärder

Vissa åtgärder är extremt destruktiva, t. ex. att omformatera en aktiv hård disk partition. I dessa fall ska cmdleten ange `ConfirmImpact` = `ConfirmImpact.High` när du deklarerar attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . Med den här inställningen tvingas cmdleten att begära användar bekräftelse även om användaren inte har angett parametern `Confirm`. Cmdlet-utvecklare bör dock undvika att använda `ConfirmImpact` för åtgärder som är bara potentiellt destruktiva, t. ex. borttagning av ett användar konto. Kom ihåg att om `ConfirmImpact` har angetts till [system. Management. Automation. ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.

På samma sätt är vissa åtgärder troligen inte destruktiva, men de gör i teorin att ändra körnings läget för ett system utanför Windows PowerShell. Sådana cmdlets kan ange `ConfirmImpact` till [system. Management. Automation. Confirmimpact. Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Detta kommer att kringgå bekräftelse begär Anden där användaren har bett att bekräfta endast medels Tor och hög påverkan.

## <a name="defining-parameters-for-system-modification"></a>Definiera parametrar för system ändring

I det här avsnittet beskrivs hur du definierar cmdlet-parametrarna, inklusive de som behövs för att stödja system ändringar. Se [lägga till parametrar som bearbetar kommando rads indata](./adding-parameters-that-process-command-line-input.md) om du behöver allmän information om att definiera parametrar.

Cmdleten Stop-proc definierar tre parametrar: `Name`, `Force`och `PassThru`.

Parametern `Name` motsvarar egenskapen `Name` för det indataporta objektet. Tänk på att parametern `Name` i det här exemplet är obligatorisk, eftersom cmdleten Miss kan köras om den inte har en namngiven process att stoppa.

Parametern `Force` gör att användaren kan åsidosätta anrop till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). I själva verket ska alla cmdlets som anropar [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ha en `Force`-parameter så att när `Force` anges hoppar cmdleten över anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och fortsätter med åtgärden. Tänk på att detta inte påverkar anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Parametern `PassThru` gör att användaren kan ange om cmdleten skickar ett utgående objekt genom pipelinen, i det här fallet när en process har stoppats. Tänk på att den här parametern är kopplad till själva cmdleten i stället för till en egenskap i objektet.

Här är parameter deklarationen för cmdleten Stop-proc.

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

## <a name="overriding-an-input-processing-method"></a>Åsidosätta en metod för bearbetning av indata

Cmdleten måste åsidosätta en metod för bearbetning av indata. Följande kod illustrerar åsidosättningen [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) som används i samplet Stop-proc-cmdlet. För varje begärt process namn säkerställer den här metoden att processen inte är en särskild process, försöker stoppa processen och skickar sedan ett utgående objekt om parametern `PassThru` anges.

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

## <a name="calling-the-shouldprocess-method"></a>Anropar metoden ShouldProcess

Metoden för bearbetning av indata för cmdleten ska anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att bekräfta körningen av en åtgärd innan en ändring (till exempel borttagning av filer) görs till systemets körnings tillstånd. Detta gör att Windows PowerShell-körningsmiljön kan tillhandahålla rätt "WhatIf" och "Confirm"-beteende i gränssnittet.

> [!NOTE]
> Om en cmdlet anger att den stöder ska bearbeta och Miss lyckas med att göra ett anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , kan användaren ändra systemet oväntat.

Anropet till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till alla kommando rads inställningar eller variabler för att fastställa vad som ska visas för användaren.

I följande exempel visas anropet till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) i samplet Stop-proc-cmdlet.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Anropar metoden ShouldContinue

Anropet till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) skickar ett sekundärt meddelande till användaren. Anropet görs efter anrop till [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returnerar `true` och om parametern `Force` inte har angetts till `true`. Användaren kan sedan ge feedback för att säga om åtgärden ska fortsätta. Cmdleten anropar [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) som en ytterligare kontroll för potentiellt skadliga system ändringar eller när du vill ge användaren ja-till-alla-och inga-till-alla-alternativ.

I följande exempel visas anropet till [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) i samplet Stop-proc-cmdlet.

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

## <a name="stopping-input-processing"></a>Stoppa bearbetning av indata

Metoden för bearbetning av indata för en cmdlet som gör system ändringar måste tillhandahålla ett sätt att stoppa bearbetningen av indata. I händelse av denna Stop-proc-cmdlet görs ett anrop från metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) till metoden [system. Diagnostics. process. kill *](/dotnet/api/System.Diagnostics.Process.Kill) . Eftersom parametern `PassThru` anges till `true`, anropar [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) också [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) för att skicka processobjektet till pipelinen.

## <a name="code-sample"></a>Kod exempel

Den fullständiga C# exempel koden finns i [StopProcessSample01-exempel](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

Windows PowerShell skickar information mellan cmdlets med .net-objekt. Därför kan en cmdlet behöva definiera en egen typ, eller så kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden. Här följer flera test som testar cmdleten Stop-proc. Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starta Windows PowerShell och använd Stop-proc-cmdlet: en för att stoppa bearbetningen som visas nedan. Eftersom cmdleten anger den `Name` parametern som obligatorisk, frågar cmdleten för parametern.

    ```powershell
    PS> stop-proc
    ```

Följande utdata visas.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Nu ska vi använda cmdleten för att stoppa processen med namnet "NOTEPAD". I cmdleten uppmanas du att bekräfta åtgärden.

    ```powershell
    PS> stop-proc -Name notepad
    ```

Följande utdata visas.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Använd Stop-proc som visas för att stoppa den kritiska processen med namnet "WINLOGON". Du uppmanas och varnas om att utföra den här åtgärden eftersom det gör att operativ systemet startas om.

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

Följande utdata visas.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- Nu ska vi försöka stoppa WINLOGON-processen utan att ta emot en varning. Tänk på att den här kommando posten använder parametern `Force` för att åsidosätta varningen.

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

Följande utdata visas.

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Se även

[Lägga till parametrar som bearbetar kommando rads indatatyper](./adding-parameters-that-process-command-line-input.md)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)