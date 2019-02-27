---
title: Att lägga till parametrar som bearbetar indata från Pipeline | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: c790d20a792bcdb4a34485e53375560e129433a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845789"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Lägga till parametrar som bearbetar pipelineindata

En källa för indata för en cmdlet är ett objekt till pipelinen som kommer från en överordnad-cmdlet. Det här avsnittet beskrivs hur du lägger till en parameter till cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta pipelineobjekt.

Denna cmdlet Get-processen använder en `Name` parameter som godkänner indata från ett pipeline-objekt, hämtar information om från den lokala datorn baserat på angivna namnen och visar information om processerna på kommandoraden.

Ämnena i det här avsnittet omfattar följande:

- [Definiera klassen Cmdlet](#Defining-the-Cmdlet-Class)

- [Definiera indata från Pipeline](#Defining-Input-from-the-Pipeline)

- [Åsidosätta indata metoden bearbetades](#Overriding-an-Input-Processing-Method)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definiera klassen Cmdlet

Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en. Denna cmdlet hämtar information om, så verb valt här heter ”hämta”. (Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Följande är definitionen för denna cmdlet Get-processen. Information om den här definitionen anges i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Definiera indata från Pipeline

Det här avsnittet beskriver hur du definierar indata från pipeline för en cmdlet. Denna cmdlet Get-Proc definierar en egenskap som representerar den `Name` parametern enligt beskrivningen i [att lägga till parametrar som processen kommandoraden indata](./adding-parameters-that-process-command-line-input.md). (Se avsnittet allmän information om deklarerar parametrar.)

När en cmdlet behöver bearbeta indata från pipeline, måste den ha dess parametrar som är bunden till indatavärden av Windows PowerShell-körningen. Om du vill göra detta måste du lägga till den `ValueFromPipeline` nyckelord eller lägga till den `ValueFromPipelineByProperty` nyckelord till den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet deklaration. Ange den `ValueFromPipeline` nyckelordet om cmdlet: en har åtkomst till den fullständiga indataobjektet. Ange den `ValueFromPipelineByProperty` om cmdlet: en hämtar bara en egenskap för objektet.

Här är parameterdeklaration för den `Name` -parametern för denna Get-Proc-cmdlet som accepterar pipeline-indata.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

Föregående deklarationen anger den `ValueFromPipeline` nyckelord till `true` så att Windows PowerShell-runtime Binder parametern till det inkommande objektet om objektet är av samma typ som parameter, eller om den kan tvingas till samma typ. Den `ValueFromPipelineByPropertyName` nyckelordet anges också `true` så att Windows PowerShell-runtime kommer att kontrollera inkommande objekt för en `Name` egenskapen. Om inkommande objekt har sådan egenskap, körningen Binder den `Name` parametern till den `Name` egenskap hos det inkommande objektet.

> [!NOTE]
> Inställningen för den `ValueFromPipeline` attributet nyckelord för en parameter har företräde framför inställningen för den `ValueFromPipelineByPropertyName` nyckelord.

## <a name="overriding-an-input-processing-method"></a>Åsidosätta indata metoden bearbetades

Om din cmdlet är att hantera indata från pipeline, måste den åsidosätta lämplig in metoderna. Grundläggande inkommande bearbetningsmetoder som introduceras i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

Denna cmdlet Get-procedur åsidosätter den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att hantera den `Name` parametern indata från användaren eller ett skript. Den här metoden får processerna för varje begärda processnamn eller alla processer om inget namn anges. Observera att [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) är den utdata mekanism för att skicka utdata objekt till pipelinen. Den andra parametern för det här anropet `enumerateCollection`, är inställd på `true` som talar om Windows PowerShell-körning för att räkna upp processen objektmatris och skriva en process i taget till kommandoraden.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [GetProcessSample03 exempel](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

Efter tillämpning av en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra det på kommandoraden. Till exempel testa koden för exempel-cmdlet. Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Ange följande kommandon för att hämta processnamn genom pipelinen i Windows PowerShell-Kommandotolken.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

Följande utdata visas.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Ange följande rader för att få process-objekt som har en `Name` egenskap från de processer som kallas ”IEXPLORE”. Det här exemplet används den `Get-Process` cmdlet (som anges av Windows PowerShell) som en överordnad kommando för att hämta ”IEXPLORE”-processer.

    ```powershell
    PS> get-process iexplore | get-proc
    ```

Följande utdata visas.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Se även

[Att lägga till parametrar som bearbetning av kommandoraden](./adding-parameters-that-process-command-line-input.md)

[Skapa din första cmdlet:](./creating-a-cmdlet-without-parameters.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)
