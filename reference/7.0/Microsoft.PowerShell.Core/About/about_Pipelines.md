---
description: Kombinera kommandon till pipelines i PowerShell
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: bf5e57389d286a2bb1cca9b3dd73ea59674461ec
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271850"
---
# <a name="about-pipelines"></a>Om pipelines

## <a name="short-description"></a>Kort beskrivning

Kombinera kommandon till pipelines i PowerShell

## <a name="long-description"></a>Lång beskrivning

En pipeline är en serie kommandon som är anslutna av pipeline-operatorer ( `|` ) (ASCII 124). Varje pipeline-operator skickar resultatet från föregående kommando till nästa kommando.

Utdata från det första kommandot kan skickas för bearbetning som indata till det andra kommandot. Och utdata kan skickas till ännu ett annat kommando. Resultatet är en komplex kommando kedja eller en _pipeline_ som består av en serie enkla kommandon.

Exempel:

```powershell
Command-1 | Command-2 | Command-3
```

I det här exemplet skickas objekten som utvärderar `Command-1` till `Command-2` .
`Command-2` bearbetar objekten och skickar dem till `Command-3` . `Command-3` bearbetar objekten och skickar dem nedåt i pipelinen. Eftersom det inte finns några fler kommandon i pipelinen visas resultaten i-konsolen.

I en pipeline bearbetas kommandona i ordning från vänster till höger. Bearbetningen hanteras som en enda åtgärd och utdata visas när den genereras.

Här är ett enkelt exempel. Följande kommando hämtar anteckningar-processen och stoppar det sedan.

Exempel:

```powershell
Get-Process notepad | Stop-Process
```

Det första kommandot använder `Get-Process` cmdleten för att hämta ett objekt som representerar anteckningar-processen. Den använder en pipeline-operator ( `|` ) för att skicka processobjektet till `Stop-Process` cmdleten, vilket stoppar anteckningar-processen. Observera att `Stop-Process` kommandot inte har en **namn** -eller **ID-** parameter för att ange processen, eftersom den angivna processen skickas via pipelinen.

Detta pipeline-exempel hämtar textfilerna i den aktuella katalogen, väljer bara de filer som är större än 10 000 byte långa, sorterar dem efter längd och visar namn och längd för varje fil i en tabell.

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

Den här pipelinen består av fyra kommandon i den angivna ordningen. Följande bild visar utdata från varje kommando när de skickas till nästa kommando i pipelinen.

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a>Använda pipelines

De flesta PowerShell-cmdletar har utformats för att stödja pipeliner. I de flesta _fall kan du_ skicka vidare resultatet av en **Get** -cmdlet till en annan cmdlet av samma substantiv.
Du kan till exempel skicka utdata från `Get-Service` cmdleten till `Start-Service` `Stop-Service` cmdletarna eller.

Den här exempel tjänsten startar WMI-tjänsten på datorn:

```powershell
Get-Service wmi | Start-Service
```

Du kan till exempel skicka vidare utdata från `Get-Item` eller `Get-ChildItem` i PowerShell-registernyckeln till `New-ItemProperty` cmdlet: en. I det här exemplet lägger du till en ny register post, **NoOfEmployees** , med värdet **8124** till **företagets** register nyckel.

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

Många av verktygs-cmdletarna, till exempel `Get-Member` ,,, `Where-Object` `Sort-Object` `Group-Object` och `Measure-Object` används nästan uteslutande i pipeliner. Du kan skicka vidare valfri objekt typ till dessa cmdletar. Det här exemplet visar hur du sorterar alla processer på datorn med antalet öppna referenser i varje process.

```powershell
Get-Process | Sort-Object -Property handles
```

Du kan skicka pipe-objekt till formaterings-, export-och utdata-cmdletar, till exempel,,, `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` och `Out-File` .

Det här exemplet visar hur du använder `Format-List` cmdleten för att visa en lista över egenskaper för ett process objekt.

```powershell
Get-Process winlogon | Format-List -Property *
```

Med lite praxis kan du se att kombinerar enkla kommandon i pipelines sparar tid och skriver och gör skripten mer effektiv.

## <a name="how-pipelines-work"></a>Så här fungerar pipeliner

I det här avsnittet beskrivs hur inobjekten binds till cmdlet-parametrar och bearbetas under pipeline-körning.

### <a name="accepts-pipeline-input"></a>Accepterar inmatade pipelines

För att stödja pipelinen måste den mottagande cmdleten ha en parameter som godkänner pipeline-inflöden. Använd `Get-Help` kommandot med alternativen **fullständig** eller **parameter** för att avgöra vilka parametrar i en cmdlet som accepterar pipeline-inflöden.

Om du till exempel vill ta reda på vilken av parametrarna i `Start-Service` cmdleten som accepterar pipeline-Indatatyp, skriver du:

```powershell
Get-Help Start-Service -Full
```

eller

```powershell
Get-Help Start-Service -Parameter *
```

Hjälpen för `Start-Service` cmdleten visar att endast **InputObject** och **namn** parametrarna accepterar pipeline-ininformation.

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

När du skickar objekt via pipeline till `Start-Service` försöker PowerShell koppla objekten till parametrarna **InputObject** och **Name** .

### <a name="methods-of-accepting-pipeline-input"></a>Metoder för att godkänna pipeline-inflöden

Cmdlets-parametrar kan acceptera pipeline-inmatade på ett av två olika sätt:

- **ByValue** : parametern accepterar värden som matchar den förväntade .net-typen eller som kan konverteras till den typen.

  Till exempel är **namn** parametern för `Start-Service` accepterar pipeline-inmatade med värde. Det kan ta emot sträng objekt eller objekt som kan konverteras till strängar.

- **ByPropertyName** : parametern accepterar endast inmatade objekt när indatamängden har en egenskap med samma namn som parametern.

  Namn parametern för kan till exempel `Start-Service` ta emot objekt som har egenskapen **Name** . Om du vill visa en lista över egenskaperna för ett objekt, rör du det `Get-Member` .

Vissa parametrar kan acceptera objekt med både värde-eller egenskaps namn, vilket gör det lättare att ta emot inmatade objekt från pipelinen.

### <a name="parameter-binding"></a>Parameter bindning

När du rör objekt från ett kommando till ett annat kommando försöker PowerShell associera skickas-objekt med en parameter för den mottagande cmdleten.

PowerShell: s parameter bindnings komponent associerar inobjekten med cmdlet-parametrar enligt följande kriterier:

- Parametern måste acceptera inmatade värden från en pipeline.
- Parametern måste godkänna vilken typ av objekt som skickas eller en typ som kan konverteras till den förväntade typen.
- Parametern användes inte i kommandot.

Till exempel `Start-Service` har cmdleten många parametrar, men endast två av dem, **namn** och **InputObject** accepterar pipeline-ininformation. Parametern **Name** tar strängar och **InputObject** -parametern använder tjänst objekt. Därför kan du skicka pipe-strängar, service objekt och objekt med egenskaper som kan konverteras till sträng-eller tjänst objekt.

PowerShell hanterar parameter bindning så effektivt som möjligt. Du kan inte föreslå eller tvinga PowerShell att binda till en angiven parameter. Kommandot Miss lyckas om PowerShell inte kan binda skickas-objekten.

Mer information om fel sökning av bindnings fel finns i [undersöka pipeline-fel](#investigating-pipeline-errors) senare i den här artikeln.

### <a name="one-at-a-time-processing"></a>En-vid-tidpunkt-bearbetning

Överföring av objekt till ett kommando är ungefär som att använda en parameter för kommandot för att skicka objekten. Nu ska vi titta på ett pipeline-exempel. I det här exemplet använder vi en pipeline för att visa en tabell med tjänst objekt.

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

Funktions sätt är att använda **InputObject** -parametern för `Format-Table` för att skicka objekt samlingen.

Vi kan till exempel spara samlingen med tjänster till en variabel som skickas med parametern **InputObject** .

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

Eller så kan vi bädda in kommandot i parametern **InputObject** .

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

Det finns dock en viktig skillnad. När du rör flera objekt till ett kommando skickar PowerShell objekten till kommandot ett i taget. När du använder en kommando parameter skickas objekten som ett enda mat ris objekt. Den här mindre skillnaden har betydande konsekvenser.

Vid körning av en pipeline räknar PowerShell automatiskt upp alla typer som implementerar `IEnumerable` gränssnittet och skickar medlemmar via pipelinen en i taget. Undantaget är `[hashtable]` , vilket kräver ett anrop till `GetEnumerator()` metoden.

I följande exempel är en matris och en hash-tabell skickas till `Measure-Object` cmdleten för att räkna antalet objekt som tas emot från pipelinen. Matrisen har flera medlemmar och hash-tabellen innehåller flera nyckel/värde-par. Endast matrisen räknas upp en i taget.

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

Om du dessutom skickar flera process objekt från `Get-Process` cmdlet `Get-Member` : en till cmdleten skickar PowerShell varje process objekt, ett i taget, till `Get-Member` . `Get-Member` visar process objektens .NET-klass (typ) och deras egenskaper och metoder.

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> `Get-Member` eliminerar dubbletter, så om objekten är av samma typ visas bara en objekt typ.

Men om du använder parametern **InputObject** i `Get-Member` , `Get-Member` tar emot en matris med **system. Diagnostics. bearbeta** objekt som en enda enhet. Den visar egenskaperna för en objekt mat ris. (Observera mat ris symbolen ( `[]` ) efter **systemets. objekt** typ namn.)

Exempel:

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

Det är inte säkert att det här resultatet är det du avsåg. Men när du förstår det kan du använda det. Alla mat ris objekt har till exempel egenskapen **Count** . Du kan använda det för att räkna antalet processer som körs på datorn.

Exempel:

```powershell
(Get-Process).count
```

Det är viktigt att komma ihåg att objekt som skickas ned pipelinen levereras en i taget.

## <a name="investigating-pipeline-errors"></a>Undersöka pipeline-fel

När PowerShell inte kan associera skickas-objekt med en parameter för den mottagande cmdleten Miss lyckas kommandot.

I följande exempel försöker vi flytta en register post från en register nyckel till en annan. Cmdlet: en `Get-Item` hämtar mål Sök vägen, som sedan skickas till `Move-ItemProperty` cmdleten. `Move-ItemProperty`Kommandot anger den aktuella sökvägen till och namnet på den register post som ska flyttas.

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

Kommandot Miss lyckas och PowerShell visar följande fel meddelande:

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

Använd cmdleten för att `Trace-Command` spåra parameter bindnings komponenten i PowerShell för att undersöka. I följande exempel kalkeras parameter bindning medan pipelinen körs. Parametern **PSHost** visar spårnings resultatet i-konsolen och parametern **fil Sök väg** skickar spårnings resultatet till `debug.txt` filen för senare referens.

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

Resultatet av spårningen är långvarigt, men de visar värdena som binds till `Get-Item` cmdleten och sedan de namngivna värdena binds till `Move-ItemProperty` cmdleten.

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

Slutligen visar det att försöket att binda sökvägen till **mål** parametern för `Move-ItemProperty` misslyckades.

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

Använd `Get-Help` cmdleten för att visa attributen för **mål** parametern.

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

Resultatet visar att **målet** endast tar emot pipelinen genom att skriva in egenskaps namn. Därför måste skickas-objektet ha en egenskap med namnet **destination**.

Används `Get-Member` för att visa egenskaperna för objektet som kommer från `Get-Item` .

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

Utdata visar att objektet är ett **Microsoft. Win32. RegistryKey** -objekt som inte har en **mål** egenskap. Det förklarar varför kommandot misslyckades.

Parametern **Path** godkänner pipeline-inmatade efter namn eller värde.

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

För att åtgärda kommandot måste vi ange målet i `Move-ItemProperty` cmdleten och använda `Get-Item` för att hämta **sökvägen** till det objekt som vi vill flytta.

Exempel:

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a>Fortsättning på inre rad

Som redan diskuterats är en pipeline en serie kommandon som är anslutna via pipeline-operatorer ( `|` ), vanligt vis skrivna på en enda rad. Med hjälp av PowerShell kan du dock dela upp pipelinen över flera rader.
När en pipe-operator är den sista token på raden, kopplas PowerShell-parsern till nästa rad till aktuellt kommando för att fortsätta att bygga pipelinen.

Till exempel följande enradig pipeline:

```powershell
Command-1 | Command-2 | Command-3
```

kan skrivas som:

```powershell
Command-1 |
  Command-2 |
    Command-3
```

De inledande blank stegen på de efterföljande raderna är inte signifikanta. Indraget ökar läsbarheten.

PowerShell 7 lägger till stöd för fortsättning av pipeliner med pipelinen i början av en rad. I följande exempel visas hur du kan använda den här nya funktionen.

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> När du arbetar interaktivt i gränssnittet, klistrar du in kod med pipelines i början av en rad endast när du använder <kbd>CTRL</kbd> + <kbd>V</kbd> för att klistra in.
> Högerklicka på Klistra in åtgärder infoga raderna en i taget. Eftersom raden inte avslutas med ett pipeline-värde, ser PowerShell ut som att de är inaktuella och kör den raden som anges.

## <a name="see-also"></a>Se även

[about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)

[about_Objects](about_objects.md)

[about_Parameters](about_parameters.md)

[about_Command_Syntax](about_command_syntax.md)

[about_ForEach](about_foreach.md)
