---
title: Att lägga till parametrar som bearbetning av kommandoradsverktyget | Microsoft Docs
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
ms.openlocfilehash: fb113086ce89e4becff9bcaf3232905fde2bf610
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068818"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Lägga till parametrar som bearbetar kommandoradsindata

En källa av indata för en cmdlet är från kommandoraden. Det här avsnittet beskrivs hur du lägger till en parameter för att den **Get-Proc** cmdlet (som beskrivs i [skapa din första Cmdlet](./creating-a-cmdlet-without-parameters.md)) så att cmdleten kan bearbeta indata från den lokala datorn utifrån explicit objekt skickades till cmdlet: en. Den **Get-Proc** cmdlet som beskrivs här hämtar processer baserat på deras namn och visar information om processerna i en kommandotolk.

I följande avsnitt finns i det här avsnittet:

- [Definiera klassen Cmdlet](#Defining-the-Cmdlet-Class)

- [Deklarera parametrar](#Declaring-Parameters)

- [Stöd för parameterverifieringen](#Supporting-Parameter-Validation)

- [Åsidosätta indata metoden bearbetades](#Overriding-an-Input-Processing-Method)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definiera klassen Cmdlet

Det första steget i Skapa en cmdlet är cmdlet namngivning och deklarationen av .NET Framework-klass som implementerar cmdlet: en. Denna cmdlet hämtar information om, så verb valt här heter ”hämta”. (Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Här är klassdeklarationen för den **Get-Proc** cmdlet. Information om den här definitionen finns i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

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

En cmdlet-parameter gör det möjligt för användarna att ange indata till cmdleten. I följande exempel **Get-Proc** och `Get-Member` är namnen på pipeline cmdlet: ar, och `MemberType` är en parameter för den `Get-Member` cmdlet. Parametern har argumentet ”property”.

**PS > get-proc; `get-member` membertype - egenskapen**

För att deklarera parametrar för en cmdlet, måste du först definiera de egenskaper som representerar parametrarna. I den **Get-Proc** cmdlet, endast parametern är `Name`, som i det här fallet representerar namnet på .NET Framework processobjektet ska hämtas. Därför definierar klassen cmdlet en egenskap av typen sträng att godkänna en matris med namn.

Här är parameterdeklaration för den `Name` -parametern för den **Get-Proc** cmdlet.

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

Om Windows PowerShell-runtime som den här egenskapen är den `Name` parameter, en [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribut har lagts till i egenskapsdefinition. Grundläggande syntaxen för att deklarera det här attributet är `[Parameter()]`.

> [!NOTE]
> En parameter måste uttryckligen markeras som offentliga. Parametrar som inte är markerad som offentlig standard till interna och hittas inte av Windows PowerShell-körningen.

Den här cmdleten använder en matris med strängar för den `Name` parametern. Om möjligt definiera cmdlet: även en parameter som en matris, eftersom detta gör att cmdleten för att acceptera mer än ett objekt.

#### <a name="things-to-remember-about-parameter-definitions"></a>Att komma ihåg parameterdefinitioner

- Fördefinierade Windows PowerShell-parametern och datatyper ska återanvändas så mycket som möjligt för att säkerställa att din cmdlet är kompatibelt med Windows PowerShell-cmdletar. Exempel: om alla cmdletar som använder den fördefinierade `Id` parameternamn som identifierar en resurs måste användaren att enkelt förstå innebörden av parametern, oavsett vilka cmdlet som de använder. Parameternamn följer i princip samma regler som de som används för variabelnamn i common language runtime (CLR). Mer information om namngivning av parametern finns i [Cmdlet parameternamn](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell förbehåller sig några parameternamn att tillhandahålla en konsekvent användarupplevelse. Använd inte dessa parameternamn: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, och `OutBuffer`. Dessutom kan följande alias för dessa parameternamn är reserverade: `vb`, `db`, `ea`, `ev`, `ov`, och `ob`.

- `Name` är ett enkelt och vanliga parameternamn, rekommenderas för användning i dina cmdlets. Det är bättre att välja ett parameternamn så här än en komplex namn som är unika för en specifik cmdlet och svåra att komma ihåg.

- Parametrar är skiftlägeskänsliga i Windows PowerShell, även om som standard behåller gränssnittet skiftläge. Skiftlägeskänslighet av argumenten är beroende av driften av cmdlet: en. Argumenten skickas till en parameter som anges på kommandoraden.

- Exempel på andra parameterdeklarationer finns [Cmdlet-parametrarna](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Deklarera parametrar som namngivna eller namngivna

En cmdlet måste ange varje parameter som antingen en namngivna eller namngiven parameter. Båda typerna av parametrar acceptera enda argument, flera argument avgränsade med kommatecken, och booleska inställningar. En boolesk parameter som kallas även en *växla*, hanterar endast booleskt inställningar. Växeln används för att bestämma förekomst av parametern. Det rekommenderade standardvärdet är `false`.

Exemplet **Get-Proc** cmdlet definierar den `Name` parametern som ett namngivna parametern med position 0. Det innebär att det första argumentet som användaren anger på kommandoraden infogas automatiskt för den här parametern. Om du vill definiera en namngiven parameter för användaren måste ange parameternamnet från kommandoraden, lämnar den `Position` nyckelordet utanför deklaration av attribut.

> [!NOTE]
> Om inte måste ha namnet parametrar, rekommenderar vi att du gör de mest använda parametrarna namngivna så att användarna inte behöver skriva parameternamnet.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Deklarera parametrar som obligatoriska eller valfria

En cmdlet måste ange varje parameter som en valfri eller en obligatorisk parameter. I exemplet **Get-Proc** cmdlet, den `Name` parametern har definierats som valfria eftersom den `Mandatory` nyckelordet har inte angetts i deklarationen för attributet.

## <a name="supporting-parameter-validation"></a>Stöd för parameterverifieringen

Exemplet **Get-Proc** cmdlet lägger till en verifiering av indata-attribut, [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), i den `Name` parametern för att aktivera validering som den indata är varken `null` eller tomt. Det här attributet är en av flera verifiering attribut som tillhandahålls av Windows PowerShell. Exempel på andra verifiering attribut finns [verifierar indata för parametern](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Åsidosätta indata metoden bearbetades

Om din cmdlet är att hantera kommandoradsverktyget indata, måste den åsidosätta lämpliga indata metoderna. Grundläggande inkommande bearbetningsmetoder som introduceras i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

Den **Get-Proc** cmdlet åsidosätter den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att hantera den `Name` parametern indata från användaren eller ett skript. Den här metoden hämtar processer för varje begärda processnamn eller alla för processer om inget namn anges. Observera att i [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), anropet till [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) är utdata mekanism för att skicka utdata objekt till pipelinen. Den andra parametern för det här anropet `enumerateCollection`, är inställd på `true` om Windows PowerShell-runtime för att räkna upp utdata-matris med process-objekt och skriva en process i taget till kommandoraden.

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

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [GetProcessSample02 exempel](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .NET Framework-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller en cmdlet kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du har implementerat en cmdlet, måste du registrera den med Windows PowerShell med hjälp av en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När cmdlet: registreras med Windows PowerShell, kan du testa den genom att köra det på kommandoraden. Här finns två sätt att testa koden för exempel-cmdlet. Läs mer om hur du använder cmdlets från kommandoraden, [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Använder du följande kommando i Windows PowerShell-Kommandotolken visa en lista över Internet Explorer-processen, som heter ”IEXPLORE”.

    ```powershell
    PS> get-proc -name iexplore
    ```

Följande utdata visas.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Använd följande kommando om du vill visa de Internet Explorer, Outlook och anteckningar processer med namnet ”IEXPLORE”, ”OUTLOOK” och ”ANTECKNINGAR”,. Om det finns flera processer, visas alla.

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

[Att lägga till parametrar som indata för Process-pipelinen](./adding-parameters-that-process-pipeline-input.md)

[Skapa din första cmdlet:](./creating-a-cmdlet-without-parameters.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)
