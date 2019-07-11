---
title: Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733843"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Lägga till alias, jokerteckenexpansion och hjälp i cmdlet-parametrar

Det här avsnittet beskrivs hur du lägger till alias och jokertecken expansion och hjälp med att meddelanden till parametrarna för cmdleten Stop-processen (beskrivs i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)).

Denna cmdlet Stop-Proc försöker avsluta processer som hämtas med hjälp av cmdleten Get-processen (beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en. Eftersom du skriver en cmdlet om du vill ändra systemet bör den vara namn därefter. Eftersom denna cmdlet stoppas systemprocesser används verb ”stoppa”, som definieras av den [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klassen, substantiv ”Proc” för att indikera processen. Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Följande kod är klassdefinitionen för denna cmdlet Stop-processen.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definiera parametrar för ändring av systemet

Din cmdlet måste definiera parametrar som supportsystem ändringar och användarfeedback. Cmdlet: en ska definiera en `Name` parametern eller motsvarande så att cmdleten kommer att kunna ändra systemet med någon typ av identifierare. Dessutom kan cmdleten bör definiera den `Force` och `PassThru` parametrar. Mer information om dessa parametrar finns i [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definiera ett Parameteralias

Ett parameteralias kan vara ett alternativt namn eller ett väldefinierade 1 bokstav eller en 2-bokstav kort namn för en cmdlet-parameter. I båda fallen är avsikten att använda alias att förenkla användarpost från kommandoraden. Windows PowerShell har stöd för parameteralias via den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, som använder deklarationssyntax [Alias()].

Följande kod visar hur ett alias har lagts till i den `Name` parametern.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Förutom att använda den [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribut, Windows PowerShell körningen utför partiella namnmatchning, även om inga alias anges. Om din cmdlet har till exempel en `FileName` parametern och det är den enda parameter som börjar med `F`, användaren kan ange `Filename`, `Filenam`, `File`, `Fi`, eller `F` och fortfarande identifiera den posten som den `FileName` parametern.

## <a name="creating-help-for-parameters"></a>Skapa hjälp för parametrar

Windows PowerShell kan du skapa hjälpen för cmdlet-parametrarna. Du kan göra detta för valfri parameter som används för system ändring och användarfeedback. För varje parameter för hjälp med att du kan ange den `HelpMessage` attributet nyckelord i den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributet deklaration. Det här nyckelordet definierar vilken text som ska visas för användaren om du behöver hjälp med hjälp av parametern. Du kan också ange den `HelpMessageBaseName` nyckelord att identifiera det grundläggande namnet på en resurs som ska användas för meddelandet. Om du ställer in det här nyckelordet måste du också ange den `HelpMessageResourceId` nyckelord att ange resursidentifieraren.

Följande kod från denna cmdlet Stop-Proc definierar den `HelpMessage` attributet nyckelord för den `Name` parametern.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Åsidosätta indata metoden bearbetades

Cmdlet: måste åsidosätta indata metoden bearbetades, oftast det här är [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). När du ändrar systemet cmdleten ska anropa den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder för att tillåta användaren vill ge feedback innan en ändring görs. Läs mer om de här metoderna [skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Stöd för jokertecken Expansion

Cmdlet: kan använda för att tillåta val av flera objekt, den [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) och [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klasser för att tillhandahålla stöd för jokertecken expansion för parametern som indata. Exempel på jokerteckensmönster är lsa * \*.txt och [a-c]\*. Använd tillbaka citattecken (') som escape-tecken när mönstret innehåller ett tecken som ska användas bokstavligt.

Jokertecken expansion av fil-och sökvägen är exempel på vanliga scenarier där cmdleten kanske vill tillåta stöd för sökvägen indata när valet av flera objekt krävs. Det är vanligt i filsystem, där en användare vill se alla filer som finns i den aktuella mappen.

Du behöver en anpassad jokertecken mönstret matchande implementering bara sällan. I så fall cmdlet: ska ha stöd för fullständig POSIX-1003.2, 3,13 specifikation för jokertecken expansion eller följande förenklad delmängden:

- **Frågetecken (?).** Matchar alla tecken på den angivna platsen.

- **Asterisk (\*).** Matchar noll eller flera tecken med början vid den angivna platsen.

- **Öppna hakparentes ().** Introducerar ett mönster hakparentes uttryck som kan innehålla tecken eller ett teckenintervall. Om ett intervall krävs, används ett bindestreck (-) som anger intervallet.

- **Stäng hakparentes (]).** Slutar ett mönster hakparentes uttryck.

- **Tillbaka-offert escape-tecknet (').** Anger att nästa tecken ska att tolkas bokstavligen. Tänk på att när du anger tillbaka till citattecken från kommandoraden (i stället för att ange den programmässigt) tillbaka-offert escape-tecken måste anges två gånger.

> [!NOTE]
> Läs mer om jokerteckensmönstren [stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Följande kod visar hur du ställer in alternativ för jokertecken och definierar jokerteckensmönster som används för att lösa den `Name` parametern för denna cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Följande kod visar hur du testar om processens namn matchar mönstret definierade jokertecken. Observera att, i det här fallet om processens namn inte matchar mönstret, cmdleten fortfarande på att hämta nästa processnamn.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [StopProcessSample03 exempel](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .net-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du implementerar en cmdlet, måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden. Nu ska vi testa exempel Stop-Proc-cmdlet. Mer information om hur du använder cmdlets från kommandoraden finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starta Windows PowerShell och Använd Stop-processen för att stoppa en process som använder ProcessName alias för den `Name` parametern.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

Följande utdata visas.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Se följande post från kommandoraden. Eftersom Name-parametern är obligatorisk, uppmanas du för den. Ange ”!”? öppnar hjälptexten som är associerade med parametern.

    ```powershell
    PS> stop-proc
    ```

Följande utdata visas.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Nu göra följande post att stoppa alla processer som matchar mönstret jokertecknet ”* Obs\*”. Du uppmanas innan du stoppar varje process som matchar mönstret.

    ```powershell
    PS> stop-proc -Name *note*
    ```

Följande utdata visas.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

Följande utdata visas.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

Följande utdata visas.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Se även

[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Så här skapar du en Windows PowerShell-Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Utöka objekttyper och formatering](/previous-versions//ms714665(v=vs.85))

[Hur du registrerar Cmdlets, Providers och vara värd för program](/previous-versions//ms714644(v=vs.85))

[Stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
