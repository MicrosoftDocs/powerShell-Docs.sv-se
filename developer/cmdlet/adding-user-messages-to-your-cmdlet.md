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
ms.openlocfilehash: ffc08d2713c4bfc0938b2e07146102af8b5467d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846804"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>Lägga till användarmeddelanden i en cmdlet

Cmdlet: ar kan skriva flera olika typer av meddelanden som visas för användaren av Windows PowerShell-körningen. Dessa meddelanden innehåller följande typer:

- Utförliga meddelanden som innehåller allmän användarinformation.

- Felsök meddelanden som innehåller information om felsökning.

- Varningsmeddelanden som innehåller ett meddelande som cmdlet: en är på väg att utföra en åtgärd som kan ha oväntade resultat.

- Utvecklingsrapporten meddelanden som innehåller information om hur mycket fungerar cmdlet: en har slutförts när du utför en åtgärd som tar lång tid.

Det finns några gränser för antalet meddelanden som cmdlet: kan skriva eller typen av meddelanden som cmdlet: skriver. Varje meddelande skrivs genom att göra ett specifikt anrop från i indata metoden av cmdlet: bearbetades.

## <a name="the-stopproc-cmdlet"></a>Cmdleten StopProc

Ämnena i det här avsnittet omfattar följande:

- [Definiera cmdleten](#Defining-the-Cmdlet)

- [Definiera parametrar för ändring av systemet](#Defining-Parameters-for-System-Modification)

- [Åsidosätta indata metoden bearbetades](#Overriding-an-Input-Processing-Method)

- [Skriva ett utförligt meddelande](#Writing-a-Verbose-Message)

- [Skriva ett meddelande för felsökning](#Writing-a-Debug-Message)

- [Skriva ett varningsmeddelande](#Writing-a-Warning-Message)

- [Skriva ett meddelande om pågående](#Writing-a-Progress-Message)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Define-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en. Alla slags cmdlet kan skriva användarmeddelanden från indata metoderna; därför i allmänhet kan du kalla den här cmdleten med alla verb som anger vilka system ändringar cmdlet utför. Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Cmdlet Stop-processen har utformats för att ändra systemet. Därför kan den [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) deklarationen för .NET-klass måste innehålla den `SupportsShouldProcess` attributet nyckelord och anges till `true`.

Följande kod är definitionen för den här cmdlet Stop-Proc-klassen. Läs mer om den här definitionen [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definiera parametrar för ändring av systemet

Cmdlet Stop-Proc definierar tre parametrar: `Name`, `Force`, och `PassThru`. Mer information om hur du definierar dessa parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

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

Cmdlet: måste åsidosätta indata metoden bearbetades, oftast blir [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Denna cmdlet Stop-Proc åsidosätter den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) indatametod för bearbetning. I den här implementeringen av cmdlet Stop-Proc rings samtal att skriva utförliga meddelanden och felsökningsmeddelanden varningsmeddelanden.

> [!NOTE]
> Mer information om hur den här metoden anropar den [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder, se [Skapar en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="writing-a-verbose-message"></a>Skriva ett utförligt meddelande

Den [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod för att skriva allmän användarnivå information som är inte relaterat till specifika felvillkor. Systemadministratören kan sedan använda informationen för att fortsätta att bearbeta andra kommandon. All information som skrivits med den här metoden bör dessutom vara lokaliserade efter behov.

Följande kod från denna cmdlet Stop-Proc visar två anrop till den [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod som du åsidosättandet av den [System.Management.Automation.Cmdlet.Processrecord* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>Skriva ett meddelande för felsökning

Den [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod för att skriva felsökningsmeddelanden som kan användas för att felsöka driften av cmdlet: en. Anropet görs från indata metoden bearbetades.

> [!NOTE]
> Windows PowerShell definierar också en `Debug` parameter som anger både utförlig och felsökningsinformation. Om din cmdlet har stöd för den här parametern, det måste inte att anropa [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) i samma kod som anropar [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

Följande två avsnitt av kod från cmdlet Stop-Proc exemplet visar anrop till den [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod som du åsidosättandet av den [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.

Det här debug-meddelandet skrivs omedelbart före [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

Det här debug-meddelandet skrivs omedelbart före [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) anropas.

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell dirigerar automatiskt någon [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) anrop till spårning av infrastruktur och cmdletar. På så sätt kan metodanrop kan spåras till värd, en fil eller en felsökare utan att du behöver göra några extra utvecklingsarbete i cmdleten. Följande kommandorad post implementerar en spårning av åtgärd.

**PS > trace-uttrycket stop-proc-filen proc.log-kommandot stop-proc anteckningar**

## <a name="writing-a-warning-message"></a>Skriva ett varningsmeddelande

Den [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod för att skriva en varning när cmdleten ska utföra en åtgärd som kan ha ett oväntat resultat, till exempel skriva över en skrivskyddad fil.

Följande kod från cmdlet Stop-Proc exemplet visar anropet till den [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod som du åsidosättandet av den [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>Skriva ett meddelande om pågående

Den [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) används för att skriva förloppsmeddelanden när cmdlet åtgärder ta lång tid att slutföra. Ett anrop till [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) skickar en [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) objekt som ska skickas till programmet som är värd för rendering för användaren.

> [!NOTE]
> Denna cmdlet Stop-processen inte innehåller ett anrop till den [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metod.

Följande kod är ett exempel på en pågående meddelande som skrivits av en cmdlet som försöker att kopiera ett objekt.

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [StopProcessSample02 exempel](./stopprocesssample02-sample.md).

## <a name="define-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden. Nu ska vi testa exempel Stop-Proc-cmdlet. Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Följande kommandorad post använder Stop-processen för att stoppa processen med namnet ”ANTECKNINGAR” anger utförlig meddelanden och skriva ut felsökningsinformation.

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

[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Så här skapar du en Windows PowerShell-Cmdlet](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
