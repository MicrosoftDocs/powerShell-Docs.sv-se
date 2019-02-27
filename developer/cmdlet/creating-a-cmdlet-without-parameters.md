---
title: Skapa en Cmdlet utan parametrar | Microsoft Docs
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
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850066"
---
# <a name="creating-a-cmdlet-without-parameters"></a>Skapa en cmdlet utan parametrar

Det här avsnittet beskriver hur du skapar en cmdlet som hämtar information från den lokala datorn utan att använda parametrar och skriver informationen till pipelinen. Cmdlet: en som beskrivs här är en Get-Proc-cmdlet som hämtar information om processerna på den lokala datorn och visar informationen på kommandoraden.

Ämnena i det här avsnittet omfattar följande:

- [Namngivning av cmdlet: en](#Naming-the-Cmdlet)

- [Definiera klassen Cmdlet](#Defining-the-Cmdlet-Class)

- [Åsidosätta indata metoden bearbetades](#Overriding-an-Input-Processing-Method)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

> [!NOTE]
> Tänk på att när du skriver cmdletar referenssammansättningar Windows PowerShell® hämtas på disk (som standard i C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0). De är inte installerad i Global Assembly Cache (GAC).

## <a name="naming-the-cmdlet"></a>Namngivning av cmdlet: en

En cmdlet-namn som består av ett verb som anger åtgärden cmdlet: en börjar och ett substantiv som visar de objekt som cmdleten agerar på. Eftersom det här exemplet Get-Proc cmdlet: en hämtar processen objekt, används verbet ”hämta”, enligt den [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) uppräkningen och substantiv ”Proc” för att indikera att cmdlet fungerar på processen objekt.

När du namnger cmdlet: ar, inte använda någon av följande tecken: #, () {} [] & - / \ $; ”:” <> &#124; ? @ ` .

### <a name="choosing-a-noun"></a>Välja ett substantiv

Du bör välja ett substantiv som är specifik. Det är bäst att använda en enda substantiv föregås av en förkortad version av produktens namn. En exempel-cmdlet-namn för den här typen är ”`Get-SQLServer`”.

### <a name="choosing-a-verb"></a>Välja ett Verb

Du bör använda ett verb från uppsättningen med godkända cmdlet verb-namnen. Läs mer om godkända cmdletens verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

## <a name="defining-the-cmdlet-class"></a>Definiera klassen Cmdlet

När du har valt en cmdlet-namn, definierar du en .NET-klass för att implementera cmdlet: en. Här är klassdefinitionen för det här exemplet Get-Proc cmdlet:

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

Observera att före klassdefinitionen, den [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributet med syntaxen `[Cmdlet(verb, noun, ...)]`, används för att identifiera den här klassen som en cmdlet. Detta är det enda obligatoriska attributet för alla cmdletar och tillåter Windows PowerShell-körning för att anropa dem korrekt. Du kan ange attributet nyckelord för ytterligare deklarera klassen om det behövs. Tänk på att attributet-deklarationen för våra exempel GetProcCommand klassen deklarerar endast substantiv och verb namnen för cmdleten Get-processen.

> [!NOTE]
> För alla Windows PowerShell-Attributklasser motsvarar nyckelord som du kan ange egenskaper för attributklassen.

När du namnger klassen för cmdlet: en är en bra idé att återspegla cmdlet-namn i klassnamnet. Om du vill göra detta använder formatet ”VerbNounCommand” och Ersätt ”Verb” och ”substantiv” med verb och substantiv som används i cmdlet-namn. Visas i föregående klassdefinitionen kan cmdleten Get-Proc exemplet definierar en klass med namnet GetProcCommand som härrör från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) basklassen.

> [!IMPORTANT]
> Om du vill definiera en cmdlet som ansluter direkt till Windows PowerShell-runtime .NET-klass måste härledas från den [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) basklassen. Läs mer om den här klassen [och skapa en Cmdlet som definierar parameteruppsättningar](./adding-parameter-sets-to-a-cmdlet.md).

> [!NOTE]
> Klass för en cmdlet måste uttryckligen markeras som offentliga. Klasser som inte är markerad som offentlig som standard till interna och kommer inte att hitta av Windows PowerShell-körningen.

Windows PowerShell använder den [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namnrymd för dess cmdlet-klasser. Vi rekommenderar att placera dina cmdlet-klasser i ett namnområde för kommandon med ditt API-namnområde, till exempel xxx.PS.Commands.

## <a name="overriding-an-input-processing-method"></a>Åsidosätta indata metoden bearbetades

Den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klassen innehåller bearbetningsmetoder för tre huvudsakliga inkommande, varav minst en cmdlet: måste åsidosätta. Mer information om hur Windows PowerShell bearbetar poster finns i [hur Windows PowerShell fungerar](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

För alla typer av indata Windows PowerShell-runtime anropar [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) att aktivera bearbetning. Om din cmdlet måste utföra vissa Förbearbeta eller konfiguration, kan det göra detta genom att åsidosätta den här metoden.

> [!NOTE]
> Windows PowerShell använder termen ”post” för att beskriva uppsättningen parametervärden som anges när en cmdlet anropas.

Om din cmdlet accepterar pipeline-indata, den måste åsidosätta de [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod, och eventuellt den [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)metod. Till exempel en cmdlet kan åsidosätta de båda metoderna om den samlar in alla indata med [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) och sedan fungerar på indata som helhet i stället för ett element i taget, som den `Sort-Object` cmdlet har.

Om din cmdlet inte tar indata från pipeline, bör det åsidosätter den [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod. Tänk på att den här metoden används ofta i stället för [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) när cmdlet: en fungerar inte på ett element i taget, liksom vad gäller för en sortering cmdlet.

Eftersom det här exemplet Get-Proc cmdlet måste ta emot indata från pipeline, åsidosätter den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod och använder standardimplementeringar för [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) och [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing). Den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) åsidosättning hämtar processer och skriver dem till den från kommandoraden med hjälp av den [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metoden.

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

#### <a name="things-to-remember-about-input-processing"></a>Kom ihåg följande om inkommande bearbetning

- Standard-källan för indata är ett explicit objekt (till exempel en sträng) som anges av användaren på kommandoraden. Mer information finns i [skapar en Cmdlet för att bearbeta kommandoraden indata](./adding-parameters-that-process-command-line-input.md).

- Indata metoden bearbetades kan också ta emot indata från utgående objekt av en överordnad cmdlet till pipelinen. Mer information finns i [skapar en Cmdlet för att bearbeta indata från Pipeline](./adding-parameters-that-process-pipeline-input.md). Tänk på att din cmdlet kan ta emot indata från en kombination av kommandorad och pipeline-datakällor.

- Cmdleten underordnade kanske inte returnerar under en längre tid eller inte alls. Därför bör indata metoden i din cmdlet bearbetades inte har Lås under anrop till [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), särskilt lås som omfattningen som sträcker sig utanför cmdlet-instans.

> [!IMPORTANT]
> Cmdlet: ar aldrig ska anropa [System.Console.Writeline*](/dotnet/api/System.Console.WriteLine) eller motsvarande.

- Cmdlet: kanske objektvariabler för att rensa upp när den är klar bearbetning (till exempel om den öppnas en filreferens i den [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod och ser referensen öppna för användning av [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)). Det är viktigt att komma ihåg att Windows PowerShell-runtime alltid inte anropar den [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod som utför rensningen för objektet.

Till exempel [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) kan inte anropas om cmdlet: en har avbrutits mitt eller om avslutande fel uppstår i någon del av cmdlet: en. Därför kan en cmdlet som kräver objektet rensningen ska implementera hela [System.Idisposable](/dotnet/api/System.IDisposable) mönstret, inklusive finaliserare, så att körningen kan anropa båda [ System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) och [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) i slutet av bearbetning.

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [GetProcessSample01 exempel](./getprocesssample01-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden. Koden för våra exempel Get-Proc-cmdlet är liten, men den fortfarande använder Windows PowerShell-runtime och ett befintligt .NET-objekt, vilket är tillräckligt för att göra det användbart. Nu ska vi testa den för att bättre förstå vad Get-processen kan göra och hur dess utdata kan användas. Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

1. Starta Windows PowerShell och hämta aktuella processer som körs på datorn.

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

2. Tilldela en variabel till cmdlet-resultat för enklare manipulering.

    ```powershell
    $p=get-proc
    ```

3. Få en processer.

    ```powershell
    $p.length
    ```

    Följande utdata visas.

    ```output
    63
    ```

4. Hämta en särskild process.

    ```powershell
    $p[6]
    ```

    Följande utdata visas.

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. Hämta starttiden för den här processen.

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

6. Få de processer som antal referenser är större än 500 och sortera resultatet.

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

7. Använd den `Get-Member` cmdlet för att lista egenskaperna som är tillgängliga för varje process.

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

[Skapa en Cmdlet för bearbetning av kommandoraden](./adding-parameters-that-process-command-line-input.md)

[Skapa en Cmdlet för att bearbeta indata från Pipeline](./adding-parameters-that-process-pipeline-input.md)

[Så här skapar du en Windows PowerShell-Cmdlet](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Utöka objekttyper och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Så här fungerar Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Hur du registrerar Cmdlets, Providers och vara värd för program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)