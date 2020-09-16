---
title: Lägga till icke-avslutande fel rapportering till din cmdlet | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6421d510f3701c12807568ad8786459123e80223
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784596"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Lägga till rapportering av fel som avbryter körningen i en cmdlet

-Cmdletar kan rapportera icke-avslutande fel genom att anropa metoden [system. Management. Automation. cmdlet. WriteError][] och fortfarande fortsätta att använda det aktuella indatamängdet eller på ytterligare inkommande pipelines-objekt. I det här avsnittet beskrivs hur du skapar en-cmdlet som rapporterar att det inte går att avsluta fel från dess metoder för bearbetning av indata.

För att inte avsluta fel (och avsluta fel) måste cmdleten skicka ett [system. Management. Automation. ErrorRecord][] -objekt som identifierar felet. Varje felpost identifieras av en unik sträng som kallas "fel identifierare". Förutom identifieraren anges kategorin för varje fel av konstanter som definieras av en [system. Management. Automation. ErrorCategory][] -uppräkning. Användaren kan visa fel baserat på deras kategori genom `$ErrorView` att ange variabeln till "CategoryView".

Mer information om fel poster finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten. Den här cmdleten hämtar process information, så verbet som väljs här är "Get". (Nästan alla sorters cmdlets som kan hämta information kan bearbeta kommando rads indata.) Mer information om godkända cmdlet-verb finns i [cmdlet-verb](approved-verbs-for-windows-powershell-commands.md).

Följande är definitionen för denna `Get-Proc` cmdlet. Information om den här definitionen anges i [skapa din första cmdlet](creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>Definiera parametrar

Vid behov måste cmdleten definiera parametrar för att bearbeta indata. Den här cmdleten Get-proc definierar en **namn** parameter enligt beskrivningen i [lägga till parametrar som bearbetar kommando rads indatatyper](adding-parameters-that-process-command-line-input.md).

Här är parameter deklarationen för **namn** parametern för Get-proc-cmdleten.

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

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

## <a name="overriding-input-processing-methods"></a>Åsidosätta metoder för bearbetning av indata

Alla cmdletar måste åsidosätta minst en av de metoder för bearbetning av indata som tillhandahålls av klassen [system. Management. Automation. cmdlet][] . Dessa metoder beskrivs i [skapa din första cmdlet](creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Din cmdlet ska hantera varje post så oberoende som möjligt.

Den här cmdleten Get-proc åsidosätter metoden [system. Management. Automation. cmdlet. ProcessRecord][] för att hantera **namn** parametern för indata som tillhandahålls av användaren eller ett skript. Med den här metoden hämtas processerna för varje begärt process namn eller alla processer om inget namn anges. Information om den här åsidosättningen anges i [skapa din första cmdlet](creating-a-cmdlet-without-parameters.md).

### <a name="things-to-remember-when-reporting-errors"></a>Saker att komma ihåg när du rapporterar fel

Objektet [system. Management. Automation. ErrorRecord][] som cmdleten skickar när ett fel skrivs måste ha ett undantag i kärnan. Följ .NET-rikt linjerna när du avgör vilket undantag som ska användas.
I princip, om felet är semantiskt på samma sätt som ett befintligt undantag, ska cmdlet: en använda eller härleda från det undantaget. Annars bör den härleda en ny undantags-eller undantags hierarki direkt från [system. Exception][] -klassen.

Tänk på följande när du skapar fel identifierare (nås via egenskapen FullyQualifiedErrorId för ErrorRecord-klassen).

- Använd strängar som är avsedda för diagnostiska syfte så att när du inspekterar den fullständigt kvalificerade identifieraren kan du fastställa vad felet är och var felet kom från.

- En välformulerad fullständigt kvalificerad fel identifierare kan vara följande.

  `CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

Observera att fel identifieraren (den första token) i föregående exempel bestämmer vad felet är och den återstående delen anger var felet kom från.

- För mer komplexa scenarier kan fel identifieraren vara en punktavgränsad punktavgränsad token som kan analyseras vid inspektion. På så sätt kan du för grenar om delar av fel identifieraren samt fel-och fel kategorin.

Cmdleten ska tilldela vissa fel identifierare till olika kod Sök vägar. Tänk på följande när du ska tilldela fel identifierare:

- En fel-ID bör vara konstant under hela cmdlet-livs cykeln. Ändra inte semantiken för en fel identifierare mellan cmdlet-versioner.
- Använd texten för en fel identifierare som tersely motsvarar det fel som rapporteras. Använd inte blank steg eller skiljetecken.
- Låt din cmdlet generera endast fel identifierare som är reproducerbara. Det ska till exempel inte generera en identifierare som innehåller en process identifierare. Fel identifierare är bara användbara för en användare när de motsvarar identifierare som visas av andra användare som har samma problem.

Ohanterade undantag fångas inte av PowerShell i följande fall:

- Om en cmdlet skapar en ny tråd och kod som körs i den tråden ger upphov till ett ohanterat undantag, kommer PowerShell inte att fånga fel meddelandet och kommer att avsluta processen.
- Om ett objekt har kod i sin destruktorn eller tar bort metoder som orsakar ett ohanterat undantag, kommer PowerShell inte att fånga fel meddelandet och kommer att avsluta processen.

## <a name="reporting-nonterminating-errors"></a>Rapportera fel som inte avslutas

Någon av metoderna för bearbetning av indata kan rapportera ett fel som inte kan avslutas till utdataströmmen med hjälp av metoden [system. Management. Automation. cmdlet. WriteError][] .

Här är ett kod exempel från den här cmdleten Get-proc som illustrerar anropet till [system. Management. Automation. cmdlet. WriteError][] inifrån åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord][] . I det här fallet görs anropet om cmdleten inte kan hitta någon process för en angiven process-ID.

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Saker att komma ihåg om att skriva fel som inte avslutas

För ett fel som inte är avslutande måste cmdleten generera en angiven fel identifierare för varje angivet inobjekt.

En cmdlet behöver ofta ändra PowerShell-åtgärden som genereras av ett fel som inte går att avsluta. Det kan du göra genom att definiera `ErrorAction` `ErrorVariable` parametrarna och. Om du definierar `ErrorAction` parametern, visar cmdleten användar alternativen [system. Management. Automation. Åtgärdsinställning][]. du kan också direkt påverka åtgärden genom att ställa in `$ErrorActionPreference` variabeln.

Cmdleten kan spara icke-avslutande fel i en variabel med hjälp av `ErrorVariable` parametern, som inte påverkas av inställningen för `ErrorAction` . Fel kan läggas till i en befintlig felvariabel genom att lägga till ett plus tecken (+) framför variabelns namn.

## <a name="code-sample"></a>Kod exempel

Den fullständiga exempel koden för C# finns i [GetProcessSample04-exempel](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definiera objekt typer och formatering

PowerShell skickar information mellan cmdlet: ar med .NET-objekt. Därför kan en cmdlet behöva definiera en egen typ, annars kan cmdleten behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Mer information om hur du definierar nya typer eller utökar befintliga typer finns i [utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Skapa cmdleten

När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med PowerShell kan du testa den genom att köra den på kommando raden. Nu ska vi testa cmdleten Get-PROC för att se om den rapporterar ett fel:

- Starta PowerShell och Använd cmdleten Get-PROC för att hämta processerna med namnet "TEST".

  ```powershell
  get-proc -name test
  ```

  Följande utdata visas.

  ```
  get-proc : Operation is not valid due to the current state of the object.
  At line:1 char:9
  + get-proc  <<<< -name test
  ```

## <a name="see-also"></a>Se även

[Lägga till parametrar som bearbetar pipelineindata](./adding-parameters-that-process-pipeline-input.md)

[Lägga till parametrar som bearbetar kommando rads indatatyper](./adding-parameters-that-process-command-line-input.md)

[Skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md)

[Utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85))

[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)

[System. Exception]: /dotnet/api/System.Exception
[System. Management. Automation. Åtgärdsinställning]: /dotnet/api/System.Management.Automation.ActionPreference
[System. Management. Automation. cmdlet. ProcessRecord]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
[System. Management. Automation. cmdlet. WriteError]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System. Management. Automation. cmdlet]: /dotnet/api/System.Management.Automation.Cmdlet
[System. Management. Automation. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System. Management. Automation. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
