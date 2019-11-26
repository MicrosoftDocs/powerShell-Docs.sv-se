---
title: Lägga till användar meddelanden i din cmdlet | Microsoft Docs
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
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416024"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Lägga till användarmeddelanden i en cmdlet

Cmdletar kan skriva flera typer av meddelanden som kan visas för användaren av Windows PowerShell-körningsmiljön. Dessa meddelanden innehåller följande typer:

- Utförliga meddelanden som innehåller allmän användar information.

- Felsök meddelanden som innehåller felsöknings information.

- Varnings meddelanden som innehåller ett meddelande om att cmdleten är på väg att utföra en åtgärd som kan ha oväntade resultat.

- Förlopps rapport meddelanden som innehåller information om hur mycket arbete som cmdleten har slutförts när en åtgärd utförs som tar lång tid.

Det finns ingen gräns för hur många meddelanden som din cmdlet kan skriva eller vilken typ av meddelanden som cmdleten skriver. Varje meddelande skrivs genom att ett speciellt anrop görs inom den indata bearbetnings metoden i din cmdlet.

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten. Alla sorters cmdlets kan skriva användar meddelanden från dess metoder för bearbetning av indata. i allmänhet kan du namnge denna cmdlet med hjälp av verb som anger vilka system ändringar som cmdleten utför. Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

Cmdleten Stop-proc är utformad för att ändra systemet; Därför måste deklarationen [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) för .net-klassen innehålla nyckelordet `SupportsShouldProcess` attribut och vara inställt på `true`.

Följande kod är definitionen för den här cmdlet-klassen Stop-proc. Mer information om den här definitionen finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definiera parametrar för system ändring

Cmdleten Stop-proc definierar tre parametrar: `Name`, `Force`och `PassThru`. Mer information om hur du definierar dessa parametrar finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

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

Din cmdlet måste åsidosätta en metod för bearbetning av indata, oftast är den [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Den här cmdleten för Stop-proc åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för bearbetning av indata. I den här implementeringen av cmdleten Stop-proc görs anrop för att skriva utförliga meddelanden, felsöka meddelanden och varnings meddelanden.

> [!NOTE]
> Mer information om hur den här metoden anropar metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Skriva ett utförligt meddelande

Metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) används för att skriva allmän information på användar nivå som inte är relaterad till vissa fel villkor. System administratören kan sedan använda den informationen för att fortsätta bearbeta andra kommandon. Dessutom bör all information som skrivs med den här metoden lokaliseras efter behov.

Följande kod från denna Stop-proc-cmdlet visar två anrop till metoden [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Skriva ett fel söknings meddelande

Metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) används för att skriva fel söknings meddelanden som kan användas för att felsöka cmdletens funktion. Anropet görs från en metod för bearbetning av indata.

> [!NOTE]
> Windows PowerShell definierar också en `Debug` parameter som visar både utförlig och felsöknings information. Om din cmdlet stöder den här parametern behöver den inte anropa [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) i samma kod som anropar [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

I följande två avsnitt av kod från samplet Stop-proc-cmdlet visas anrop till metoden [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

Det här fel söknings meddelandet skrivs omedelbart innan [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Det här fel söknings meddelandet skrivs omedelbart innan [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) anropas.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell dirigerar automatiskt alla [system. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -anrop till spårnings infrastrukturen och-cmdletar. Detta gör att metod anrop kan spåras till värd programmet, en fil eller en fel sökare utan att du behöver göra några extra utvecklings arbeten i-cmdleten. Följande kommando rads post implementerar en spårnings åtgärd.

**PS > trace-Expression Stop-proc-File proc. log-Command Stop-proc anteckningar**

## <a name="writing-a-warning-message"></a>Skriver ett varnings meddelande

Metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) används för att skriva en varning när cmdleten är på väg att utföra en åtgärd som kan ha ett oväntat resultat, till exempel skriva över en skrivskyddad fil.

Följande kod från samplet Stop-proc-cmdleten visar anropet till metoden [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Skriver ett förlopps meddelande

[System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) används för att skriva förlopps meddelanden när cmdlet-åtgärder tar en längre tid att slutföra. Ett anrop till [system. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) skickar ett [system. Management. Automation. progressRecord](/dotnet/api/System.Management.Automation.ProgressRecord) -objekt som skickas till värd programmet för rendering till användaren.

> [!NOTE]
> Denna Stop-proc-cmdlet inkluderar inte ett anrop till metoden [system. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

Följande kod är ett exempel på ett förlopps meddelande som skrivits av en cmdlet som försöker kopiera ett objekt.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Kod exempel

Den fullständiga C# exempel koden finns i [StopProcessSample02-exempel](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definiera objekt typer och formatering

Windows PowerShell skickar information mellan cmdlets med .NET-objekt. Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden. Nu ska vi testa samplet Stop-proc-cmdlet. Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Följande kommando rads post använder Stop-PROC för att stoppa processen med namnet "NOTEPAD", tillhandahålla utförliga meddelanden och skriva ut felsöknings information.

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

Följande utdata visas.

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

## <a name="see-also"></a>Se även

[Skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Så här skapar du en Windows PowerShell-cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
