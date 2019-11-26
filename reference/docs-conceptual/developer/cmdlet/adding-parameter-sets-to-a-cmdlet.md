---
title: Lägga till parameter uppsättningar till en cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416321"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Lägga till parameteruppsättningar i en cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Saker att känna till om parameter uppsättningar

Windows PowerShell definierar en parameter uppsättning som en grupp parametrar som fungerar tillsammans. Genom att gruppera parametrarna för en cmdlet kan du skapa en enda cmdlet som kan ändra dess funktioner baserat på vilken grupp av parametrar som användaren anger.

Ett exempel på en cmdlet som använder två parameter uppsättningar för att definiera olika funktioner är den `Get-EventLog`-cmdlet som tillhandahålls av Windows PowerShell. Den här cmdleten returnerar annan information när användaren anger parametern `List` eller `LogName`. Om parametern `LogName` anges, returnerar cmdleten information om händelserna i en viss händelse logg. Om parametern `List` anges, returnerar cmdleten information om själva loggfilerna (inte den händelse information de innehåller). I det här fallet identifierar parametrarna för `List` och `LogName` två separata parameter uppsättningar.

Två viktiga saker att komma ihåg om parameter uppsättningar är att Windows PowerShell-körningsmiljön endast använder en parameter uppsättning för en viss Indatatyp och att varje parameter uppsättning måste ha minst en parameter som är unik för den parameter uppsättningen.

För att illustrera den sista punkten använder denna Stop-proc-cmdlet tre parameter uppsättningar: `ProcessName`, `ProcessId`och `InputObject`. Var och en av dessa parameter uppsättningar har en parameter som inte finns i de andra parameter uppsättningarna. Parameter uppsättningarna kan dela andra parametrar, men cmdleten använder de unika parametrarna `ProcessName`, `ProcessId`och `InputObject` för att identifiera vilken uppsättning parametrar som Windows PowerShell-körningen ska använda.

## <a name="declaring-the-cmdlet-class"></a>Deklarera cmdlet-klassen

Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten. För denna cmdlet används livs cykel verbet "Stop" eftersom cmdleten stoppar system processer. Substantiv namnet "proc" används eftersom cmdleten fungerar på processer. I deklarationen nedan noterar du att cmdlet-verbet och Substantiv namnet visas i namnet på cmdlet-klassen.

> [!NOTE]
> Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

Följande kod är klass definitionen för den här Stop-proc-cmdleten.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>Deklarera parametrarna för cmdleten

Den här cmdleten definierar tre parametrar som krävs som indata till cmdleten (dessa parametrar definierar även parameter uppsättningar), samt en `Force` parameter som hanterar vad cmdleten gör och en `PassThru` parameter som avgör om cmdleten skickar ett utdata-objekt via pipelinen. Som standard skickar denna cmdlet inget objekt via pipelinen. Mer information om de sista två parametrarna finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Att deklarera namn parametern

Med den här Indataparametern kan användaren ange namnen på de processer som ska stoppas. Observera att attributet `ParameterSetName` attribut för attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) anger den `ProcessName` parameter uppsättningen för den här parametern.

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Observera också att aliaset "ProcessName" anges för den här parametern.

### <a name="declaring-the-id-parameter"></a>Deklarera ID-parametern

Med den här Indataparametern kan användaren ange identifierare för de processer som ska stoppas. Observera att attributet `ParameterSetName` attribut för attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) anger den `ProcessId` parameter uppsättningen.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Observera också att alias "ProcessId" anges för den här parametern.

### <a name="declaring-the-inputobject-parameter"></a>Deklarera parametern InputObject

Med den här Indataparametern kan användaren ange ett indata-objekt som innehåller information om de processer som ska stoppas. Observera att attributet `ParameterSetName` attribut för attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) anger den `InputObject` parameter uppsättningen för den här parametern.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Observera också att den här parametern inte har något alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Deklarera parametrar i flera parameter uppsättningar

Även om det måste finnas en unik parameter för varje parameter uppsättning kan parametrarna tillhöra mer än en parameter uppsättning. I dessa fall ger du den delade parametern en deklaration för [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) för varje uppsättning som parametern tillhör. Om en parameter är i alla parameter uppsättningar behöver du bara deklarera attributet-parameter en gång och behöver inte ange parameter uppsättningens namn.

## <a name="overriding-an-input-processing-method"></a>Åsidosätta en metod för bearbetning av indata

Varje cmdlet måste åsidosätta en metod för bearbetning av indata, oftast används metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . I den här cmdleten åsidosätts metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , så att cmdleten kan bearbeta valfritt antal processer. Den innehåller en SELECT-instruktion som anropar en annan metod baserat på vilken parameter uppsättning användaren har angett.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

De hjälp metoder som anropas av SELECT-instruktionen beskrivs inte här, men du kan se deras implementering i hela kod exemplet i nästa avsnitt.

## <a name="code-sample"></a>Kod exempel

Den fullständiga C# exempel koden finns i [StopProcessSample04-exempel](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

Windows PowerShell skickar information mellan cmdlets med .NET-objekt. Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden. Här följer några tester som visar hur parametrarna `ProcessId` och `InputObject` kan användas för att testa parameter uppsättningar för att stoppa en process.

- Med Windows PowerShell igång kör du Stop-proc-cmdlet: en med parametern `ProcessId` som har angetts för att stoppa en process baserat på dess identifierare. I det här fallet använder cmdleten `ProcessId` parameter inställd för att stoppa processen.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Med Windows PowerShell igång kör du Stop-proc-cmdlet: en med parametern `InputObject` som har angetts för att stoppa processer på objektet Notepad som hämtats av `Get-Process` kommandot.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Se även

[Skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Så här skapar du en Windows PowerShell-cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
