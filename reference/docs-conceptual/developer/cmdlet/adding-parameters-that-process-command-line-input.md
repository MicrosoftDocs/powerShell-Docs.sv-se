---
title: Lägga till parametrar som bearbetar kommando rads indatatyper | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: 7db93af33717dc4802ed915793f6cd570cfb48f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355666"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Lägga till parametrar som bearbetar kommandoradsindata

En källa för indatamängden för en cmdlet är kommando raden. I det här avsnittet beskrivs hur du lägger till en parameter till cmdleten **Get-proc** (som beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta indata från den lokala datorn baserat på explicita objekt som skickas till cmdleten. Cmdleten **Get-proc** som beskrivs här hämtar processer baserat på deras namn och visar sedan information om processerna i kommando tolken.

## <a name="defining-the-cmdlet-class"></a>Definiera cmdlet-klassen

Det första steget i att skapa cmdleten är cmdlet-namn och deklarationen för den .NET Framework-klass som implementerar cmdleten. Den här cmdleten hämtar process information, så verbet som väljs här är "Hämta". (Nästan alla sorters cmdlets som kan hämta information kan bearbeta kommando rads indata.) Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

Här är klass deklarationen för **Get-proc-** cmdleten. Information om den här definitionen finns i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Deklarera parametrar

En cmdlet-parameter gör att användaren kan ange indata till cmdleten. I följande exempel är **Get-proc** och `Get-Member` namnen på de pipeliniska cmdletarna och `MemberType` är en parameter för `Get-Member`-cmdleten. Parametern har argumentet "Property."

**PS > Get-proc; `get-member`-MemberType-egenskap**

Om du vill deklarera parametrar för en cmdlet måste du först definiera de egenskaper som representerar parametrarna. I cmdleten **Get-proc** är den enda parametern `Name`, som i det här fallet representerar namnet på det .NET Framework processobjektet som ska hämtas. Därför definierar cmdlet-klassen en egenskap av typen sträng för att acceptera en namn mat ris.

Här är parameter deklarationen för parametern `Name` i **Get-proc-** cmdleten.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

För att informera Windows PowerShell-körningsmiljön om att den här egenskapen är `Name`-parametern, läggs attributet [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) till i egenskaps definitionen. Den grundläggande syntaxen för att deklarera det här attributet är `[Parameter()]`.

> [!NOTE]
> En parameter måste markeras som offentlig. Parametrar som inte har marker ATS som offentliga som offentliga som standard som interna och inte hittas av Windows PowerShell-körningsmiljön.

Denna cmdlet använder en sträng mat ris för parametern `Name`. Om möjligt bör cmdleten även definiera en parameter som en matris, eftersom detta tillåter att cmdleten accepterar mer än ett objekt.

#### <a name="things-to-remember-about-parameter-definitions"></a>Saker att komma ihåg om parameter definitioner

- Fördefinierade parameter namn och data typer för Windows PowerShell bör återanvändas så mycket som möjligt för att säkerställa att din cmdlet är kompatibel med Windows PowerShell-cmdletar. Om till exempel alla cmdlet: ar använder det fördefinierade `Id` parameter namnet för att identifiera en resurs, kommer användaren enkelt att förstå parameterns innebörd, oavsett vilken cmdlet de använder. Parameter namn följer i princip samma regler som används för variabel namn i Common Language Runtime (CLR). Mer information om parameter namn finns i [cmdlet parameter Names](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell reserverar några parameter namn för att ge en konsekvent användar upplevelse. Använd inte följande parameter namn: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`och `OutBuffer`. Dessutom är följande alias för dessa parameter namn reserverade: `vb`, `db`, `ea`, `ev`, `ov`och `ob`.

- `Name` är ett enkelt och vanligt parameter namn som rekommenderas för användning i dina cmdletar. Det är bättre att välja ett parameter namn som detta än ett komplext namn som är unikt för en speciell cmdlet och svårt att komma ihåg.

- Parametrar är Skift läges känsliga i Windows PowerShell, men som standard bevarar gränssnittet. Skift läges känslighet för argumenten beror på driften av cmdleten. Argument skickas till en parameter som anges på kommando raden.

- Exempel på andra parameter deklarationer finns i [cmdlet-parametrar](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Deklarera parametrar som positions-eller namngivna

En cmdlet måste ange varje parameter som antingen en positions-eller namngiven parameter. Båda typerna av parametrar accepterar enstaka argument, flera argument avgränsade med kommatecken och booleska inställningar. En boolesk parameter, som även kallas för en *växel*, hanterar endast booleska inställningar. Växeln används för att bestämma förekomst av parametern. Det rekommenderade standardvärdet är `false`.

Cmdleten **Get-proc** definierar `Name`-parametern som en positions parameter med position 0. Det innebär att det första argumentet som användaren anger på kommando raden automatiskt infogas för den här parametern. Om du vill definiera en namngiven parameter för vilken användaren måste ange parameter namnet från kommando raden lämnar du `Position` nyckelordet från deklarationen för attributet.

> [!NOTE]
> Om parametrar måste namnges, rekommenderar vi att du använder de mest använda parametrarna så att användarna inte behöver ange parameter namnet.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Deklarera parametrar som obligatoriska eller valfria

En cmdlet måste ange varje parameter som antingen en valfri eller en obligatorisk parameter. I exempel cmdleten **Get-proc** definieras `Name`-parametern som valfri eftersom nyckelordet `Mandatory` inte har angetts i deklarationen för attributet.

## <a name="supporting-parameter-validation"></a>Stöd för parameter validering

Exemplet **Get-proc-** cmdlet: en lägger till ett verifierings-attribut, [system. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), till parametern `Name` för att aktivera verifieringen att inaktuella inaktuella inkommer inte `null` eller tomt. Det här attributet är ett av flera verifierings attribut från Windows PowerShell. Exempel på andra verifierings attribut finns i [Verifiera parameter Indatatyp](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Åsidosätta en metod för bearbetning av indata

Om cmdleten ska hantera kommando rads indata måste den åsidosätta lämpliga metoder för bearbetning av indata. De grundläggande metoderna för indata-bearbetning införs när [du skapar din första cmdlet](./creating-a-cmdlet-without-parameters.md).

Cmdleten **Get-proc** åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att hantera `Name` parameter-indata från användaren eller ett skript. Den här metoden hämtar processerna för varje begärt process namn, eller alla för-processer om inget namn har angetts. Observera att i [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [system. Management. Automation. cmdlet. WriteObject% 28System. Object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) är utmatnings mekanismen för att skicka utgående objekt till pipelinen. Den andra parametern för det här anropet, `enumerateCollection`, har ställts in på `true` för att informera Windows PowerShell-körningsmiljön om att räkna upp utdata-matrisen för process objekt och skriva en process i taget till kommando raden.

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
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Kod exempel

Den fullständiga C# exempel koden finns i [GetProcessSample02-exempel](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

Windows PowerShell skickar information mellan cmdletar med hjälp av .NET Framework objekt. Därför kan en cmdlet behöva definiera en egen typ, eller så kan en cmdlet behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste du registrera den med Windows PowerShell med hjälp av en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När cmdleten har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden. Här följer två sätt att testa koden för exempel-cmdleten. Mer information om hur du använder cmdlets från kommando raden finns [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Använd följande kommando i Windows PowerShell-prompten för att visa en lista över Internet Explorer-processen, som heter "iexplore".

    ```powershell
    PS> get-proc -name iexplore
    ```

Följande utdata visas.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Om du vill visa en lista över Internet Explorer-, Outlook-och anteckningar-processer med namnet "iexplore", "OUTLOOK" och "NOTEPAD" använder du följande kommando. Om det finns flera processer visas alla.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

Följande utdata visas.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Se även

[Lägga till parametrar som bearbetar pipeline-inflöden](./adding-parameters-that-process-pipeline-input.md)

[Skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)

[Utöka objekt typer och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Registrera cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)
