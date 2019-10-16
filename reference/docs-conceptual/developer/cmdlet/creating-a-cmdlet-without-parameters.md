---
title: Skapa en cmdlet utan parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359430"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Skapa en cmdlet utan parametrar

I det här avsnittet beskrivs hur du skapar en-cmdlet som hämtar information från den lokala datorn utan att använda parametrar, och sedan skriver informationen till pipelinen. Den cmdlet som beskrivs här är en get-proc-cmdlet som hämtar information om processerna på den lokala datorn och sedan visar informationen på kommando raden.

> [!NOTE]
> Tänk på att när du skriver cmdlets, kommer Windows PowerShell-® referens sammansättningarna att hämtas till disken (som standard på C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). De installeras inte i GAC (Global Assembly Cache).

## <a name="naming-the-cmdlet"></a>Namnge cmdleten

Ett cmdlet-namn består av ett verb som anger vilken åtgärd som cmdleten tar och ett substantiv som anger vilka objekt som cmdleten agerar på. Eftersom den här exempel cmdleten Get-proc hämtar process objekt, används verbet "Get", som definieras av [system. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) -uppräkningen och Substantiv "proc" för att indikera att cmdleten fungerar på process objekt.

När du namnger cmdletar ska du inte använda något av följande tecken: #, () {} [] &-/\ $; : "' < > &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Välja ett substantiv

Du bör välja ett substantiv som är speciellt. Det är bäst att använda en singularisk substantiv med en förkortad version av produkt namnet. Ett exempel på ett cmdlet-namn av den här typen är "`Get-SQLServer`".

### <a name="choosing-a-verb"></a>Välja ett verb

Du bör använda ett verb från uppsättningen godkända cmdlet-verb. Mer information om godkända cmdlet-verb finns i cmdlet- [verb](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definiera cmdlet-klassen

När du har valt ett cmdlet-namn definierar du en .NET-klass för att implementera cmdleten. Här är klass definitionen för det här exemplet get-proc-cmdlet:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Observera att föregående till klass definitionen, attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) , med syntaxen `[Cmdlet(verb, noun, ...)]`, används för att identifiera den här klassen som en cmdlet. Detta är det enda obligatoriska attributet för alla cmdletar, och det gör att Windows PowerShell-körningsmiljön kan anropa dem korrekt. Du kan ange nyckelord för attribut för att ytterligare deklarera klassen om det behövs. Tänk på att attributet deklaration för vår exempel-GetProcCommand klass endast deklarerar Substantiv-och verben för Get-proc-cmdleten.

> [!NOTE]
> För alla klasser för Windows PowerShell-attribut är de nyckelord som du kan ange motsvarar egenskaperna för klassen Attribute.

När du namnger klassen för cmdleten är det en bra idé att spegla cmdlet-namnet i klass namnet. Det gör du genom att använda formatet "VerbNounCommand" och ersätta "verb" och "substantiv" med verbet och substantiv som används i cmdlet-namnet. Som det visas i den föregående klass definitionen definierar cmdleten Get-proc en klass med namnet GetProcCommand, som härleds från Bask Lassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .

> [!IMPORTANT]
> Om du vill definiera en cmdlet som ansluter till Windows PowerShell-körningen direkt ska din .NET-klass härledas från Bask Lassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) . Mer information om den här klassen finns i [skapa en cmdlet som definierar parameter uppsättningar](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> Klassen för en cmdlet måste markeras explicit som offentlig. Klasser som inte är markerade som offentliga kommer att standardvärdet internt och hittas inte av Windows PowerShell-körningsmiljön.

Windows PowerShell använder namn området [Microsoft. PowerShell. commands](/dotnet/api/Microsoft.PowerShell.Commands) för dess cmdlet-klasser. Vi rekommenderar att du placerar dina cmdlet-klasser i ett kommandon namnrymd för API-namnrymden, till exempel xxx. PS. commands.

## <a name="overriding-an-input-processing-method"></a>Åsidosätta en metod för bearbetning av indata

Klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) tillhandahåller tre huvudsakliga metoder för bearbetning av indata, minst en av vilka din cmdlet måste åsidosätta. Mer information om hur Windows PowerShell bearbetar poster finns i [hur Windows PowerShell fungerar](/previous-versions//ms714658(v=vs.85)).

För alla typer av indata anropar Windows PowerShell-körningen [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för att aktivera bearbetning. Om din cmdlet måste utföra vissa förbehandlingar eller inställningar kan det göra detta genom att åsidosätta den här metoden.

> [!NOTE]
> Windows PowerShell använder termen "Record" för att beskriva den uppsättning parameter värden som anges när en cmdlet anropas.

Om din cmdlet accepterar pipeline-inmatade måste den åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och eventuellt metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . En cmdlet kan till exempel åsidosätta båda metoderna om den samlar in alla inmatade med hjälp av [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och sedan arbetar med inmatat i stället för ett element i taget, eftersom `Sort-Object`-cmdleten gör.

Om cmdleten inte tar emot pipelinen bör den åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Tänk på att den här metoden ofta används i stället för [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) när cmdleten inte kan köras på ett element i taget, vilket är fallet för en sorterings-cmdlet.

Eftersom den här exempel cmdleten Get-proc måste ta emot pipeline-inmatade objekt, åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och använder standard implementeringarna för [system. Management. Automation. cmdlet. BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)och [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Åsidosättningen [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) hämtar processer och skriver dem till kommando raden med hjälp av metoden [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) .

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>Saker att komma ihåg om bearbetning av indata

- Standard källan för indata är ett explicit objekt (till exempel en sträng) som tillhandahålls av användaren på kommando raden. Mer information finns i [skapa en cmdlet för att bearbeta kommando rads indata](./adding-parameters-that-process-command-line-input.md).

- En metod för att bearbeta indata kan också ta emot indata från objektet utdata i en överordnad cmdlet i pipelinen. Mer information finns i [skapa en cmdlet för att bearbeta pipeline-indata](./adding-parameters-that-process-pipeline-input.md). Tänk på att din cmdlet kan ta emot ininformation från en kombination av kommando rads-och pipeline-källor.

- Den underordnade cmdleten kanske inte kan returneras under en längre tid, eller inte alls. Av den anledningen bör indata bearbetnings metoden i din cmdlet inte innehålla lås under anrop till [system. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), särskilt lås för vilka omfattningen sträcker sig utanför cmdlet-instansen.

> [!IMPORTANT]
> Cmdletar ska aldrig anropa [system. Console. WriteLine *](/dotnet/api/System.Console.WriteLine) eller motsvarande.

- Cmdleten kan ha objektvariabler som rensas när bearbetningen är klar (till exempel om den öppnar en fil referens i metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och håller handtaget öppet för användning av [ System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Det är viktigt att komma ihåg att Windows PowerShell runtime inte alltid anropar metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) , som bör utföra rensning av objekt.

Till exempel kanske [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) inte anropas om cmdleten avbryts halvvägs eller om ett avslutande fel inträffar i någon del av cmdleten. Därför bör en cmdlet som kräver rensning av objekt implementera hela [system. IDisposable](/dotnet/api/System.IDisposable) -mönstret, inklusive slutföraren, så att körningen kan anropa både [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [ System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) i slutet av bearbetningen.

## <a name="code-sample"></a>Kod exempel

Den fullständiga C# exempel koden finns i [GetProcessSample01-exempel](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

Windows PowerShell skickar information mellan cmdlets med .NET-objekt. Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden. Koden för vår exempel get-proc cmdlet är liten, men den använder fortfarande Windows PowerShell-körningsmiljön och ett befintligt .NET-objekt, vilket är tillräckligt för att göra det användbart. Vi testar det för att bättre förstå vad get-proc kan göra och hur dess utdata kan användas. Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Starta Windows PowerShell och få de aktuella processerna som körs på datorn.

    ```powershell
    get-proc
    ```

    Följande utdata visas.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. Tilldela en variabel till cmdlet-resultaten för enklare manipulering.

    ```powershell
    $p=get-proc
    ```

3. Hämta antalet processer.

    ```powershell
    $p.length
    ```

    Följande utdata visas.

    ```output
    63
    ```

4. Hämta en speciell process.

    ```powershell
    $p[6]
    ```

    Följande utdata visas.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Hämta start tiden för den här processen.

    ```powershell
    $p[6].starttime
    ```

    Följande utdata visas.

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. Hämta de processer som antalet referenser är större än 500 och sortera resultatet.

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    Följande utdata visas.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. Använd cmdleten `Get-Member` för att visa en lista över de egenskaper som är tillgängliga för varje process.

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    Följande utdata visas.

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>Se även

[Skapa en cmdlet för bearbetning av kommando rads ingångar](./adding-parameters-that-process-command-line-input.md)

[Skapa en cmdlet för att bearbeta pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md)

[Så här skapar du en Windows PowerShell-cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Så här fungerar Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)