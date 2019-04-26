---
title: Att lägga till parametern anger att en Cmdlet | Microsoft Docs
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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068845"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Lägga till parameteruppsättningar i en cmdlet

Det här avsnittet beskrivs hur du lägger till parametern anger att cmdleten Stop-processen (beskrivs i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)). Precis som andra cmdlets i Stop-processen som beskrivs i den här Programmeringsguide kan denna cmdlet försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).

Ämnena i det här avsnittet omfattar följande:

- [Att känna till om parameteruppsättningar](#Adding-Parameter-Sets-to-a-Cmdlet)

- [Fastställa Cmdlet-klassen](#Declaring-the-Cmdlet-Class)

- [Deklarera parametrarna för cmdleten](#Declaring-the-Parameters-of-the-Cmdlet)

- [Åsidosätta indata metoden bearbetades](#Overriding-an-Input-Processing-Method)

- [Kodexempel](#Declaring-the-Parameters-of-the-Cmdlet)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>Att känna till om parameteruppsättningar

Windows PowerShell definierar en parameter som angetts som en grupp med parametrar som fungerar tillsammans. Du kan skapa en enkel cmdlet som kan ändra dess funktioner baserat på vilken grupp av parametrarna användaren anger genom att gruppera parametrarna för en cmdlet.

Ett exempel på en cmdlet som använder två parameteruppsättningar för att definiera olika funktioner är den `Get-EventLog` cmdlet som tillhandahålls av Windows PowerShell. Denna cmdlet returnerar olika typer av information när användaren anger den `List` eller `LogName` parametern. Om den `LogName` parameter har angetts, returnerar cmdleten information om händelser i en viss händelselogg. Om den `List` parameter har angetts, returnerar cmdleten information om loggen filer själva (inte händelseinformationen i dem). I det här fallet den `List` och `LogName` parametrar identifiera två separata parameteruppsättningar.

Två viktiga saker att tänka på parameteruppsättningar är att Windows PowerShell-runtime använder bara en parameteruppsättning för en viss indata och att varje parameteruppsättningen måste ha minst en parameter som är unikt för den parameteruppsättningen.

För att visa den senaste tidpunkten kan denna cmdlet Stop-processen använder tre parameteruppsättningar: `ProcessName`, `ProcessId`, och `InputObject`. Var och en av dessa parameteruppsättningar har en parameter som inte är i andra parameteruppsättningar. Parameteruppsättningar kan dela andra parametrar, men använder de unika parametrarna för cmdleten `ProcessName`, `ProcessId`, och `InputObject` att identifiera vilken uppsättning parametrar som ska användas i Windows PowerShell-runtime.

## <a name="declaring-the-cmdlet-class"></a>Fastställa Cmdlet-klassen

Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en. Livscykeln verb ”stoppa” används för denna cmdlet, eftersom cmdleten stoppar systemprocesser. Substantiv namnet ”Proc” används eftersom cmdlet fungerar på processer. Observera att cmdlet verb och substantiv namnet visas namnet på klassen cmdlet i förklaringen nedan.

> [!NOTE]
> Läs mer om godkända cmdlet verb-namnen [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Följande kod är klassdefinitionen för denna cmdlet Stop-processen.

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

Denna cmdlet definierar tre parametrar som behövs som indata för cmdlet (dessa parametrar också definiera parameteruppsättningar), samt en `Force` parameter som hanterar vad cmdleten gör och en `PassThru` parameter som anger om cmdlet: en ska skicka ett utdataobjekt genom pipelinen. Som standard skickar denna cmdlet inte ett objekt genom pipelinen. Mer information om dessa två sista parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>Deklarera Namnparametern

Denna indataparameter gör att användaren kan ange namnen på processerna som ska stoppas. Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `ProcessName` parameteruppsättning för den här parametern.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

Observera också att alias ”ProcessName” ges till den här parametern.

### <a name="declaring-the-id-parameter"></a>Deklarera Id-Parameter

Denna indataparameter gör att användaren att ange identifierare av processer som ska stoppas. Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `ProcessId` parameteruppsättningen.

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

Observera också att alias ”ProcessId” ges till den här parametern.

### <a name="declaring-the-inputobject-parameter"></a>Deklarera parametern InputObject

Denna indataparameter gör att användaren kan ange ett inkommande objekt som innehåller information om processerna som ska stoppas. Observera att den `ParameterSetName` attributet nyckelordet för den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet anger den `InputObject` parameteruppsättning för den här parametern.

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

Observera också att den här parametern har inget alias.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Deklarera parametrar i flera parameteruppsättningar

Även om det måste vara en parameter som är unika för varje parameteruppsättningen, kan parametrar tillhöra mer än en parameter. I dessa fall kan ge parametern delade en [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) deklaration av attribut för var och en principuppsättningsparameter som de tillhör. Om det finns en parameter i alla parameteruppsättningar kommer du bara har deklarera parameterattributet en gång och behöver inte ange parameteruppsättning namn.

## <a name="overriding-an-input-processing-method"></a>Åsidosätta indata metoden bearbetades

Alla cmdlets måste åsidosätta indata metoden bearbetades, oftast det här är den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod. I den här cmdleten den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metoden åsidosätts så att cmdleten kan bearbeta valfritt antal processer. Den innehåller en Select-instruktion som anropar en annan metod baserat på vilka parameteruppsättningen användaren har angett.

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

Hjälpmetoder som anropas av Select-instruktion som inte beskrivs här, men du kan se deras implementering i hela kodexemplet i nästa avsnitt.

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [StopProcessSample04 exempel](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra det på kommandoraden. Här följer några tester som visar hur `ProcessId` och `InputObject` parametrar kan användas för att testa sina parameteruppsättningar för att stoppa en process.

- Med Windows PowerShell igång, kör du cmdleten Stop-processen med den `ProcessId` parameteruppsättning för att stoppa en process som baserat på dess identifierare. I så fall cmdlet: en använder den `ProcessId` parameteruppsättning för att stoppa processen.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Med Windows PowerShell igång, kör du cmdleten Stop-processen med den `InputObject` parameteruppsättning stoppa processer på objektet anteckningar som hämtas av den `Get-Process` kommando.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Se även

[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Så här skapar du en Windows PowerShell-Cmdlet](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
