---
title: 'Att lägga till icke-avslutande fel som rapporterar till cmdlet: | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851018"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>Lägga till rapportering av fel som avbryter körningen i en cmdlet

Cmdlet: ar kan rapportera oändliga fel genom att anropa den [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod och fortfarande fortsätter att fungera på den aktuella indataobjektet eller på ytterligare inkommande pipeline-objekt. Det här avsnittet beskrivs hur du skapar en cmdlet som rapporterar oändliga fel från dess inkommande bearbetningsmetoder.

Cmdlet: en måste klara för oändliga fel (samt avslutande fel), en [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt identifierar felet. Varje Felpost identifieras med en unik sträng som kallas ”fel identifierare”. Förutom identifieraren kategorin för varje fel anges av konstanterna som definieras av en [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) uppräkning. Du kan visa fel baserat på deras kategori genom att ange den `$ErrorView` variabeln ”CategoryView”.

Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).

Ämnena i det här avsnittet omfattar följande:

- [Definiera cmdleten](#Defining-the-Cmdlet)

- [Definiera parametrar](#Defining-Parameters)

- [Åsidosätta indata metoderna](#Overriding-Input-Processing-Methods)

- [Rapportering oändliga fel](#Reporting-Nonterminating-Errors)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Define-Object-Types-and-Formatting)

- [Att skapa cmdleten](#Building-the-Cmdlet)

- [Testa cmdleten](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>Definiera cmdleten

Det första steget i Skapa en cmdlet är alltid namngivning av cmdlet: en och deklarerar .NET-klass som implementerar cmdlet: en. Denna cmdlet hämtar information om, så verb valt här heter ”hämta”. (Du kan bearbeta kommandoradsverktyget indata för nästan alla slags cmdlet som kan hämta information.) Läs mer om godkända cmdlet verb [Cmdlet Verb-namnen](./approved-verbs-for-windows-powershell-commands.md).

Följande är definitionen för denna cmdlet Get-processen. Information om den här definitionen anges i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

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

Om det behövs måste cmdlet: definiera parametrar för bearbetning av indata. Denna cmdlet Get-Proc definierar en `Name` parametern enligt beskrivningen i [att lägga till parametrar som processen Command-Line indata](./adding-parameters-that-process-command-line-input.md).

Här är parameterdeklaration för den `Name` -parametern för denna cmdlet Get-processen.

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

## <a name="overriding-input-processing-methods"></a>Åsidosätta indata metoderna

Alla cmdlets måste åsidosätta minst en av de indata som bearbetar metoder som tillhandahålls av den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass. Dessa metoder beskrivs i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

> [!NOTE]
> Cmdlet: bör hantera varje post oberoende som möjligt.

Denna cmdlet Get-procedur åsidosätter den [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att hantera den `Name` parameter för indata från användaren eller ett skript. Den här metoden får processerna för varje begärda processnamn eller alla processer om inget namn anges. Information om den här åsidosättningen anges i [skapa din första cmdleten](./creating-a-cmdlet-without-parameters.md).

#### <a name="things-to-remember-when-reporting-errors"></a>Kom ihåg följande när du har rapporterat fel

Den [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) objekt som cmdleten skickar när du skriver ett fel kräver ett undantag kärnpunkter. Följ riktlinjerna .NET när du fastställer undantaget att använda. I praktiken, om felet är från samma som ett befintligt undantag, cmdleten bör använda eller härledd från detta undantag. I annat fall bör den härleda ett nytt undantag eller undantag hierarki direkt från den [System.Exception](/dotnet/api/System.Exception) klass.

Tänk på följande när du skapar fel-ID (öppnas via egenskapen FullyQualifiedErrorId i klassen ErrorRecord).

- Använd strängar som är avsedda för diagnostiskt syfte så att vid kontroll av fullständigt kvalificerat ID kan du fastställa vilka felet är och där felet kommer ifrån.

- En korrekt formaterad fullständiga fel-ID kan vara på följande sätt.

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

Observera att i föregående exempel fel-ID (första token) betecknar felet och den återstående delen indikerar var felet kommer ifrån.

- Fel-ID kan vara en punkt avgränsade token som kan tolkas i granskning för mer komplicerade scenarier. På så sätt kan du för grenen på delar av fel-ID samt felkategori identifierare och fel.

Cmdlet: en ska tilldela specifika fel-ID till olika kodsökvägar. Tänk på följande information för tilldelning av fel-ID:

- En identifierare som fel ska förblir konstant under cmdlet hela livscykel. Ändra inte semantiken för en identifierare som fel mellan cmdlet-versioner.

- Använd text efter ett fel-ID som motsvarar tersely fel har rapporterats. Använd inte blanksteg eller skiljetecken.

- Har din cmdleten som genererar endast fel-ID som är reproducerbar. Den ska till exempel inte skapa en identifierare som innehåller ett process-ID. Fel-ID är användbara för en användare bara när de motsvarar identifierare som ses av andra användare som upplever samma problem.

Ett ohanterat undantag omfattas inte av Windows PowerShell under följande förhållanden:

- Om en cmdlet skapar en ny tråd och kod som körs i den tråd kastar ett ohanterat undantag, kommer inte att fånga felet Windows PowerShell och kommer att avsluta processen.

- Om ett objekt har kod i dess destruktorn eller Dispose metoder som orsakar ett ohanterat undantag, kommer inte att fånga felet i Windows PowerShell och kommer att avsluta processen.

## <a name="reporting-nonterminating-errors"></a>Rapportering oändliga fel

Någon av metoderna indata kan rapportera ett oändliga fel i utdata stream med hjälp av den [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod. Här är ett exempel från denna cmdlet för Get-processen som illustrerar anropet till [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från inom åsidosättningen av den [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod. I det här fallet görs anropet om cmdlet: en inte kan hitta en process för en angiven process-ID.

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>Kom ihåg följande om hur du skriver oändliga fel

Cmdlet: en måste generera ett specifikt fel-ID för varje specifik indataobjektet för ett oändliga fel.

En cmdlet måste ofta ändrar Windows PowerShell-åtgärden som produceras av en oändliga fel. Det kan göra detta genom att definiera den `ErrorAction` och `ErrorVariable` parametrar. Om definierar den `ErrorAction` parametern cmdlet: en anger användaralternativen [System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference), du kan också direkt påverka åtgärden genom att ange den `$ErrorActionPreference` variabeln.

Cmdlet: en kan spara oändliga fel i en variabel med det `ErrorVariable` parametern, som inte påverkas av inställningen för `ErrorAction`. Fel kan läggas till en befintlig variabel fel genom att lägga till ett plustecken (+) framför variabelnamnet.

## <a name="code-sample"></a>Kodexempel

För hela C# exempelkoden, se [GetProcessSample04 exempel](./getprocesssample04-sample.md).

## <a name="define-object-types-and-formatting"></a>Definiera objekttyper och formatering

Windows PowerShell skickar information mellan cmdlet: ar med .NET-objekt. Därför måste en cmdlet kan behöva definiera sin egen typ eller cmdlet: en kan behöva utöka en befintlig typ som tillhandahålls av en annan cmdlet. Läs mer om att definiera nya typer eller utöka befintliga typer [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Att skapa cmdleten

När du implementerar en cmdlet, måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul. Mer information om hur du registrerar cmdlets finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testa cmdleten

När din cmdlet har registrerats med Windows PowerShell kan testa du den genom att köra det på kommandoraden. Nu ska vi testa exempel Get-Proc-cmdlet för att se om den rapporterar ett fel:

- Starta Windows PowerShell och Använd cmdleten Get-processen för att hämta processer med namnet ”TEST”.

    ```powershell
    PS> get-proc -name test
    ```

Följande utdata visas.

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>Se även

[Att lägga till parametrar som indata för Process-pipelinen](./adding-parameters-that-process-pipeline-input.md)

[Att lägga till parametrar som bearbetar av kommandoraden](./adding-parameters-that-process-command-line-input.md)

[Skapa din första cmdlet:](./creating-a-cmdlet-without-parameters.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referens](../windows-powershell-reference.md)

[Cmdlet-exempel](./cmdlet-samples.md)
