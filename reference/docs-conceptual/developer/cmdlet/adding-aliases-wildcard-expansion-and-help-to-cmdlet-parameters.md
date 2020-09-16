---
title: Lägga till alias, expansion med jokertecken och hjälp till cmdlet-parametrar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 244c50c73972c2760e0029c7fa4f4b5764b066da
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774974"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Lägga till alias, jokerteckenexpansion och hjälp i cmdlet-parametrar

I det här avsnittet beskrivs hur du lägger till alias, expansion av jokertecken och hjälp meddelanden till parametrarna i cmdleten Stop-proc (beskrivs i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)).

Den här cmdleten Stop-proc försöker stoppa processer som hämtas med hjälp av cmdleten Get-proc (beskrivs i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten. Eftersom du skriver en cmdlet för att ändra systemet bör den namnges. Eftersom denna cmdlet stoppar system processer använder den verbet "Stop", som definieras av klassen [system. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) , med Substantiv "proc" för att indikera processen. Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).

Följande kod är klass definitionen för den här Stop-proc-cmdleten.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Definiera parametrar för system ändring

Din cmdlet måste definiera parametrar som stöder system ändringar och feedback från användare. Cmdleten bör definiera en `Name` parameter eller motsvarande så att cmdleten kan ändra systemet med en viss typ av identifierare. Dessutom bör cmdleten definiera `Force` `PassThru` parametrarna och. Mer information om dessa parametrar finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Definiera ett parameter Ali Aset

Ett parameter Ali Aset kan vara ett alternativt namn eller ett väldefinierat kort namn eller kort namn för en cmdlet-parameter. I båda fallen är syftet med att använda alias att förenkla användar posten från kommando raden. Windows PowerShell stöder parameter-alias via attributet [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) , som använder deklarationssyntax [alias ()].

Följande kod visar hur ett alias läggs till i `Name` parametern.

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

Förutom att använda attributet [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) , utför Windows PowerShell-körningen partiell namn matchning, även om inga alias anges. Om din cmdlet till exempel har en `FileName` parameter och det är den enda parameter som börjar med `F` , kan användaren ange `Filename` ,,, `Filenam` `File` `Fi` eller `F` och fortfarande använda posten som `FileName` parameter.

## <a name="creating-help-for-parameters"></a>Skapar hjälp för parametrar

Med Windows PowerShell kan du skapa hjälp för cmdlet-parametrar. Gör detta för alla parametrar som används för system ändringar och feedback från användare. För varje parameter som stöd för hjälp kan du ange `HelpMessage` nyckelordet Attribute i deklarationen [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -attribut. Det här nyckelordet definierar texten som ska visas för användaren för hjälp med att använda-parametern. Du kan också ange `HelpMessageBaseName` nyckelordet för att identifiera bas namnet för en resurs som ska användas för meddelandet. Om du anger det här nyckelordet måste du också ange ett `HelpMessageResourceId` nyckelord för att ange resurs-ID.

Följande kod från denna Stop-proc-cmdlet definierar `HelpMessage` attributets nyckelord för `Name` parametern.

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

## <a name="overriding-an-input-processing-method"></a>Åsidosätta en metod för bearbetning av indata

Din cmdlet måste åsidosätta en metod för bearbetning av indata, oftast är detta [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). När du ändrar systemet bör cmdleten anropa metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) för att tillåta användaren att ge feedback innan en ändring görs. Mer information om dessa metoder finns i [skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Stöd för expansion med jokertecken

Om du vill tillåta att flera objekt väljs kan din cmdlet använda klassen [system. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) och [system. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) för att ge stöd för stöd för jokertecken för parameter ingångar. Exempel på mönster för jokertecken är LSA *, \* . txt och [a-c] \* . Använd det bakre citat tecknet (") som ett escape-tecken när mönstret innehåller ett tecken som ska användas bokstavligen.

Jokertecken för fil-och Sök vägs namn är exempel på vanliga scenarier där cmdleten kanske vill tillåta stöd för Path-indata när valet av flera objekt krävs. Ett vanligt fall är i fil systemet, där en användare vill se alla filer som finns i den aktuella mappen.

Du bör ha en anpassad matchning av jokertecken som matchar implementeringen sällan. I det här fallet ska din cmdlet ha stöd för antingen den fullständiga POSIX 1003,2, 3,13-specifikationen för expansion av jokertecken eller följande förenklade del mängd:

- **Frågetecken (?).** Matchar alla bokstäver på den angivna platsen.

- **Asterisk ( \* ).** Matchar noll eller flera tecken som börjar på den angivna platsen.

- **Öppna hak paren tes ([).** Introducerar ett mönster paren tes uttryck som kan innehålla tecken eller ett tecken intervall. Om ett intervall krävs används ett bindestreck (-) för att ange intervallet.

- **Avslutande hak paren tes (]).** Avslutar ett mönster paren tes uttryck.

- **Escape-tecken för back citat (').** Anger att nästa Character ska tas i bokstavligen. Tänk på att när du anger ett back citat tecken från kommando raden (i stället för att ange det program mässigt), måste Escape-tecknet för back-offerten anges två gånger.

> [!NOTE]
> Mer information om mönster för jokertecken finns i [stödjande jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md).

Följande kod visar hur du ställer in jokertecken och definierar mönster för jokertecken som används för att matcha `Name` parametern för denna cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

Följande kod visar hur du testar om process namnet matchar det definierade jokertecken. Observera att, i det här fallet, om process namnet inte matchar mönstret, fortsätter cmdleten på för att hämta nästa process namn.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Kod exempel

Den fullständiga exempel koden för C# finns i [StopProcessSample03-exempel](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definiera objekt typer och formatering

Windows PowerShell skickar information mellan cmdlets med .net-objekt. Därför kan en cmdlet behöva definiera en egen typ, eller så kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste den vara registrerad med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden. Nu ska vi testa samplet Stop-proc-cmdlet. Mer information om hur du använder cmdlets från kommando raden finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Starta Windows PowerShell och använd Stop-PROC för att stoppa en process med ProcessName-aliaset för `Name` parametern.

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

- Gör följande på kommando raden. Eftersom namn parametern är obligatorisk uppmanas du att ange den. Anger du "!?" visar den hjälp text som är kopplad till parametern.

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

- Gör nu följande post för att stoppa alla processer som matchar jokertecknet * Obs! \* . Du uppmanas att stoppa varje process som matchar mönstret.

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

[Skapa en cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Så här skapar du en Windows PowerShell-cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))

[Stöd för jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
