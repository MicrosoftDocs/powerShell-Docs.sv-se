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
ms.openlocfilehash: bbe9f0213754d1cc47e0fd9a7a898bde916c0636
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068456"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>Skapa en cmdlet som ändrar systemet

Ibland ändra en cmdlet körs av systemet, inte bara Tillståndet för Windows PowerShell-runtime. I dessa fall kan bör cmdleten Tillåt att användaren en chans att bekräfta huruvida att genomföra ändringen.

En cmdlet måste göra två saker för att stödja bekräftelse.

- Deklarera att cmdleten stöder bekräftelse när du anger den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut genom att ställa in nyckelordet SupportsShouldProcess `true`.

- Anropa [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) under körningen av cmdlet: en (som visas i följande exempel).

Som stöd för bekräftelse, en cmdlet exponerar den `Confirm` och `WhatIf` parametrar som tillhandahålls av Windows PowerShell och uppfyller också utveckling riktlinjer för cmdlet: ar (Mer information om cmdlet utveckling riktlinjer finns i [ Riktlinjer för utveckling av cmdlet](./cmdlet-development-guidelines.md).).

## <a name="changing-the-system"></a>Ändra systemet

Av ”ändra systemet” syftar på alla cmdletar som potentiellt ändrar tillståndet för systemet utanför Windows PowerShell. Exempelvis stoppa en process, aktivera eller inaktivera ett användarkonto eller att lägga till en rad i en databastabell är alla ändringar som ska bekräftas. Däremot ändra inte systemet åtgärder som läser data eller upprätta tillfälliga anslutningar och allmänt kräver inte bekräftelse. Bekräftelse krävs inte heller för åtgärder som är begränsad till i Windows PowerShell-körning, till exempel `set-variable`. Cmdletar som kan eller inte kan göra en permanent förändring bör deklarera `SupportsShouldProcess` och anropa [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) endast om de är på väg att göra en permanent ändring.

> [!NOTE]
> ShouldProcess bekräftelse gäller enbart för cmdlet: ar. Om ett kommando eller skript ändrar driftläget för ett system genom att anropa .NET-metoder, egenskaper eller direkt eller genom att anropa program utanför Windows PowerShell, den här typen av bekräftelse inte är tillgänglig.

## <a name="the-stopproc-cmdlet"></a>Cmdleten StopProc

Det här avsnittet beskrivs en Stop-Proc-cmdlet som försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).

Ämnena i det här avsnittet omfattar följande:

- [Definiera cmdleten](#Defining-the-Cmdlet)

- [Definiera parametrar för ändring av systemet](#Defining-Parameters-for-System-Modification)

- [Åsidosätta indata metoden bearbetades](#Overriding-an-Input-Processing-Method)

- [Att anropa metoden ShouldProcess](#Calling-the-ShouldProcess-Method)

- [Att anropa metoden ShouldContinue](#Calling-the-ShouldContinue-Method)

- [Stoppar inkommande bearbetning](#Stopping-Input-Processing)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en. Eftersom du skriver en cmdlet om du vill ändra systemet bör den vara namn därefter. Den här cmdleten stoppas systemprocesser, så verb valt här heter ”stoppa”, som definieras av den [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klassen, substantiv ”Proc” för att indikera att cmdleten stoppar processer. Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Följande är klassdefinitionen för denna cmdlet Stop-processen.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

Tänk som i den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklarationen den `SupportsShouldProcess` nyckelord för attribut har angetts till `true` att aktivera cmdlet: en att göra anrop till [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). Utan den här uppsättningen med nyckelord, den `Confirm` och `WhatIf` parametrar är inte tillgänglig för användaren.

### <a name="extremely-destructive-actions"></a>Extremt destruktiva åtgärder

Vissa åtgärder är extremt destruktiv, till exempel formatera om en aktiv hårddiskpartition. I dessa fall kan cmdleten bör ange `ConfirmImpact`  =  `ConfirmImpact.High` när deklarera den [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribut. Den här inställningen tvingar cmdlet: en till begäran om användaren ska bekräfta även om användaren inte har angett den `Confirm` parametern. Cmdlet: en utvecklare bör dock undvika överanvändning av `ConfirmImpact` för åtgärder som är bara potentiellt skadliga, till exempel ta bort ett användarkonto. Kom ihåg att om `ConfirmImpact` är inställd på [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).

Vissa åtgärder är inte troligt att destruktiva, även om de i teorin ändra driftläget för ett system utanför Windows PowerShell. Dessa cmdletar kan ställa in `ConfirmImpact` till [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0). Detta kommer kringgå begäranden om händelsebekräftelse där användaren har bett att bekräfta endast påverkan medium och hög inverkan.

## <a name="defining-parameters-for-system-modification"></a>Definiera parametrar för ändring av systemet

Det här avsnittet beskriver hur du definierar cmdlet-parametrarna, inklusive de som behövs för att supportsystem ändring. Se [att lägga till parametrar som processen CommandLine indata](./adding-parameters-that-process-command-line-input.md) om du behöver allmän information om hur du definierar parametrar.

Cmdlet Stop-Proc definierar tre parametrar: `Name`, `Force`, och `PassThru`.

Den `Name` parametern motsvarar den `Name` egenskapen för inkommande processobjektet. Tänk på som det `Name` parametern i det här exemplet är obligatorisk, som cmdleten misslyckas om den inte har en namngiven process för att stoppa.

Den `Force` parameter gör det möjligt för användarna att åsidosätta anrop till [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue). I själva verket en cmdlet som anropar [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) bör ha en `Force` parametern så att när `Force` anges cmdleten hoppar över anropet till [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och fortsätter med åtgärden. Observera att detta inte påverkar anrop till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).

Den `PassThru` parameter gör det möjligt för användaren att ange om cmdlet: en skickar ett objekt genom pipelinen och i det här fallet när en process har stoppats. Tänk på att den här parametern är knutna till cmdleten själv i stället för till en egenskap för indataobjektet.

Här är parameterdeklaration för cmdleten Stop-processen.

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

## <a name="overriding-an-input-processing-method"></a>Åsidosätta indata metoden bearbetades

Cmdlet: en måste åsidosätta indata metoden bearbetades. Följande kod visar den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) åsidosättning som används i exemplet Stop-Proc cmdlet. För var och en begärd processnamn, den här metoden garanterar att processen inte är en särskild process, försöker stoppa processen och skickar sedan ett objekt om de `PassThru` parameter har angetts.

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

## <a name="calling-the-shouldprocess-method"></a>Att anropa metoden ShouldProcess

Indata bearbetning av-metoden för cmdlet: ska anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod för att bekräfta körning av en åtgärd innan en ändring (till exempel ta bort filer) görs till körtillstånd av systemet. På så sätt kan Windows PowerShell-körning för att ange ”WhatIf” och ”Confirm”-beteendet i gränssnittet.

> [!NOTE]
> Om en cmdlet säger att den stöder ska bearbetas och inte kan se den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropa måste användaren kan ändra systemet oväntat.

Anropet till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) skickar namnet på resursen som ska ändras för användaren med Windows PowerShell-körning med hänsyn till eventuella kommandoradsinställningar eller variabler avgöra vad som ska visas för användaren.

I följande exempel visas anropet till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från åsidosättningen av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -metod i exemplet Stoppa Proc cmdlet.

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>Att anropa metoden ShouldContinue

Anropet till den [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden skickar ett sekundära meddelande för användaren. Det här anropet görs efter anropet till [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returnerar `true` och om den `Force` parametern har inte angetts `true`. Användaren kan sedan ge feedback om du vill säga om åtgärden bör vara fortsatt. Cmdlet-anrop [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) som ytterligare en kontroll för ändringar av potentiellt skadliga system eller när du vill ange Ja till alla och Nej till alla alternativ för användaren.

I följande exempel visas anropet till [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) från åsidosättningen av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -metod i exemplet Stoppa Proc cmdlet.

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

## <a name="stopping-input-processing"></a>Stoppar inkommande bearbetning

Indata bearbetning av-metoden för en cmdlet som ändrar system måste ange ett sätt att stoppa bearbetningen av indata. När det gäller denna cmdlet Stop-processen, ett anrop görs från den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att den [System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill) metod. Eftersom den `PassThru` parametern är inställd på `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) också anropar [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) att skicka processobjektet till pipelinen.

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [StopProcessSample01 exempel](./stopprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden. Här följer flera tester som testar cmdlet Stop-processen. Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starta Windows PowerShell och Använd cmdleten Stop-processen för att stoppa bearbetningen enligt nedan. Eftersom cmdlet: en anger den `Name` parametern som obligatorisk, cmdlet-förfrågningarna för parametern.

    ```powershell
    PS> stop-proc
    ```

Följande utdata visas.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- Nu ska vi använda cmdlet för att stoppa processen med namnet ”ANTECKNINGAR”. Cmdlet: en ber dig att bekräfta åtgärden.

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

- Använd Stop-processen som du ser för att stoppa kritiska processen med namnet ”WINLOGON”. Du uppmanas och om hur du utför den här åtgärden eftersom det leder operativsystemet för att starta om en varning.

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

- Nu ska vi prova nu att stoppa processen WINLOGON utan att du får en varning. Tänk på att den här posten kommando använder de `Force` parametern åsidosätta varningen.

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

[Att lägga till parametrar som bearbetar av kommandoraden](./adding-parameters-that-process-command-line-input.md)

[Utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)