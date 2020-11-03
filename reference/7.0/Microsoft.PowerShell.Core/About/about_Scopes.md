---
description: Förklarar begreppet omfång i PowerShell och visar hur du anger och ändrar elementets omfattning.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 2149a1dec14e4de9c6ff1021e98689ca93307cb8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269985"
---
# <a name="about-scopes"></a>Om omfång

## <a name="short-description"></a>Kort beskrivning
Förklarar begreppet omfång i PowerShell och visar hur du anger och ändrar elementets omfattning.

## <a name="long-description"></a>Lång beskrivning

PowerShell skyddar åtkomsten till variabler, alias, funktioner och PowerShell-enheter (PSDrives) genom att begränsa var de kan läsas och ändras. I PowerShell används omfattnings regler för att se till att du inte oavsiktligt ändrar ett objekt som inte ska ändras.

Följande är de grundläggande reglerna för omfattning:

- Omfattningar kan kapslas. En yttre omfattning kallas för en överordnad omfattning. Alla kapslade omfång är underordnade omfång för den överordnade.

- Ett objekt visas i den omfattning där det skapades och i alla underordnade omfattningar, om du inte uttryckligen gör det privat. Du kan placera variabler, alias, funktioner eller PowerShell-enheter i ett eller flera omfång.

- Ett objekt som du har skapat i ett omfång kan bara ändras i det omfång som det skapades i, såvida du inte uttryckligen anger ett annat omfång.

Om du skapar ett objekt i ett omfång och objektet delar sitt namn med ett objekt i ett annat omfång, kan det ursprungliga objektet vara dolt under det nya objektet, men det åsidosätts eller ändras inte.

## <a name="powershell-scopes"></a>PowerShell-scope

PowerShell stöder följande omfång:

- Global: det omfång som aktive ras när PowerShell startas. Variabler och funktioner som förekommer när PowerShell startar har skapats i det globala omfånget, till exempel automatiska variabler och variabler. Variablerna, aliasen och funktionerna i dina PowerShell-profiler skapas också i det globala omfånget.

- Lokal: det aktuella omfånget. Det lokala omfånget kan vara det globala omfånget eller andra omfång.

- Skript: den omfattning som skapas när en skript fil körs. Endast kommandona i skriptet körs i skript omfånget. I kommandona i ett skript är skript omfånget det lokala omfånget.

> [!NOTE]
> **Private** är inte ett omfång. Det är ett [alternativ](#private-option) som ändrar synligheten för ett objekt utanför omfånget där objektet definieras.

## <a name="parent-and-child-scopes"></a>Överordnad och underordnad omfattning

Du kan skapa ett nytt omfång genom att köra ett skript eller en funktion, genom att skapa en session eller genom att starta en ny instans av PowerShell. När du skapar ett nytt omfång är resultatet ett överordnat område (det ursprungliga omfånget) och ett underordnat omfång (det omfång som du skapade).

I PowerShell är alla omfattningar underordnade omfång i det globala omfånget, men du kan skapa många omfattningar och många rekursiva omfång.

Om du inte uttryckligen gör objekten privat är objekten i det överordnade omfånget tillgängliga för det underordnade omfånget. Objekt som du skapar och ändrar i det underordnade omfånget påverkar dock inte det överordnade omfånget, såvida du inte uttryckligen anger omfånget när du skapar objekten.

## <a name="inheritance"></a>Arv

En underordnad omfattning ärver inte variabler, alias och funktioner från det överordnade omfånget. Om ett objekt är privat kan det underordnade omfånget Visa objekten i det överordnade omfånget. Och kan ändra objekten genom att uttryckligen ange det överordnade omfånget, men objekten ingår inte i det underordnade omfånget.

En underordnad omfattning skapas dock med en uppsättning objekt. Normalt innehåller den alla alias som har alternativet **AllScope** . Det här alternativet beskrivs längre fram i den här artikeln. Den innehåller alla variabler som har alternativet **AllScope** , plus några automatiska variabler.

Om du vill hitta objekt i ett visst omfång använder du omfattnings parametern för `Get-Variable` eller `Get-Alias` .

Om du till exempel vill hämta alla variabler i det lokala omfånget skriver du:

```powershell
Get-Variable -Scope local
```

Om du vill hämta alla variabler i det globala omfånget skriver du:

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a>Omfångs modifierare

En variabel, ett alias eller ett funktions namn kan innehålla någon av följande valfria omfångs modifierare:

- `global:` -Anger att namnet finns i det **globala** omfånget.
- `local:` -Anger att namnet finns i det **lokala** omfånget. Det aktuella omfånget är alltid det **lokala** omfånget.
- `private:` -Anger att namnet är **privat** och bara visas för det aktuella omfånget.
- `script:` -Anger att namnet finns i **skript** omfånget.
  **Skript** omfattningen är den närmast överordnade skript filens omfattning eller **Global** om det inte finns någon närmast överordnade skript fil.
- `using:` – Används för att komma åt variabler som definierats i ett annat omfång samtidigt som skript körs via cmdletar som `Start-Job` och `Invoke-Command` .
- `workflow:` -Anger att namnet finns i ett arbets flöde. Obs! arbets flöden stöds inte i PowerShell Core.
- `<variable-namespace>` – En modifierare som skapats av en PowerShell PSDrive-Provider.
  Ett exempel:

  |  Namnområde  |                    Beskrivning                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | Alias som definierats i det aktuella omfånget               |
  | `Env:`      | Miljövariabler som definierats i det aktuella omfånget |
  | `Function:` | Funktioner som definierats i det aktuella omfånget             |
  | `Variable:` | Variabler som definierats i det aktuella omfånget             |

Standard omfånget för skript är skript omfånget. Standard omfånget för functions och alias är det lokala omfånget, även om de är definierade i ett skript.

### <a name="using-scope-modifiers"></a>Använda omfångs modifierare

Om du vill ange omfånget för en ny variabel, ett alias eller en funktion använder du en omfattnings modifierare.

Syntaxen för en omfattnings modifierare i en variabel är:

```
$[<scope-modifier>:]<name> = <value>
```

Syntaxen för en omfattnings modifierare i en funktion är:

```
function [<scope-modifier>:]<name> {<function-body>}
```

Följande kommando, som inte använder en omfångs modifierare, skapar en variabel i den aktuella eller **lokala** omfattningen:

```powershell
$a = "one"
```

Om du vill skapa samma variabel i det **globala** omfånget använder du omfångs `global:` modifieraren:

```powershell
$global:a = "one"
```

Om du vill skapa samma variabel i **skript** omfånget använder du `script:` omfångs modifieraren:

```powershell
$script:a = "one"
```

Du kan också använda en omfattnings modifierare med Functions. Följande funktions definition skapar en funktion i det **globala** omfånget:

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

Du kan också använda omfattnings modifierare för att referera till en variabel i ett annat omfång.
Följande kommando refererar till `$test` variabeln, först i det lokala området och sedan i det globala omfånget:

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a>`Using:`Omfångs modifieraren

Att använda är en särskild omfattnings modifierare som identifierar en lokal variabel i ett fjärrkommando. Utan modifierare förväntar PowerShell variabler i fjärrkommandon som ska definieras i fjärrsessionen.

`Using`Omfångs modifieraren introduceras i PowerShell 3,0.

För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem. `Using`Omfångs modifieraren stöds i följande kontexter:

- Fjärrkörning av kommandon, startade med `Invoke-Command` användning **av ComputerName** , **hostname** , **SSHConnection** eller **sessionstillstånd** (fjärrsession)
- Bakgrunds jobb, startade med `Start-Job` (out-of-process-session)
- Tråd jobb, startade via `Start-ThreadJob` eller `ForEach-Object -Parallel` (separat trådpool)

Beroende på sammanhanget är inbäddade variabel värden antingen oberoende kopior av data i anroparens omfång eller referenser till den. I fjärranslutna och inaktiva sessioner är de alltid oberoende kopior.

Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).

De skickas som referens i Thread-sessioner. Det innebär att det är möjligt att ändra variabler för anrops omfång i en annan tråd. För att på ett säkert sätt ändra variabler krävs Thread-synkronisering.

Mer information finns i:

- [Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)
- [-Objekt](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a>Serialisering av variabel värden

Fjärrkörning av kommandon och bakgrunds jobb körs utanför processen.
Sessioner utanför processen använder XML-baserad serialisering och deserialisering för att göra värdena för variabler tillgängliga över process gränserna. Serialiserings processen konverterar objekt till en **PSObject** som innehåller de ursprungliga objekt egenskaperna, men inte dess metoder.

För en begränsad uppsättning typer, deserialiserar objekt tillbaka till den ursprungliga typen. Det dehydratiserade objektet är en kopia av den ursprungliga objekt instansen.
Den har typ egenskaper och metoder. För enkla typer, till exempel **system. version** , är kopian exakt. För komplexa typer är kopian perfekt. Till exempel innehåller inte rehydratiserade certifikat objekt den privata nyckeln.

Instanser av alla andra typer är **PSObject** -instanser. Egenskapen **PSTypeNames** innehåller det ursprungliga typ namnet som föregås av **deserialiserad** , till exempel **Deserialized.System. Data. DataTable**

### <a name="the-allscope-option"></a>Alternativet AllScope

Variabler och alias har en **alternativ** egenskap som kan ha värdet **AllScope**. Objekt som har egenskapen **AllScope** blir en del av alla underordnade omfång som du skapar, även om de inte retroaktivt ärvs av överordnade omfång.

Ett objekt som har egenskapen **AllScope** visas i det underordnade omfånget och ingår i det omfånget. Ändringar i objektet i alla omfattningar påverkar alla omfattningar där variabeln definieras.

### <a name="managing-scope"></a>Hantera omfattning

Flera cmdlets har en **omfattnings** parameter som låter dig hämta eller ange (skapa och ändra) objekt i ett visst omfång. Använd följande kommando för att hitta alla cmdletar i sessionen som har en **omfattnings** parameter:

```powershell
Get-Help * -Parameter scope
```

Om du vill hitta variablerna som är synliga i ett visst omfång använder du- `Scope` parametern för `Get-Variable` . De synliga variablerna inkluderar globala variabler, variabler i det överordnade omfånget och variabler i det aktuella omfånget.

Följande kommando hämtar till exempel variablerna som visas i det lokala omfånget:

```powershell
Get-Variable -Scope local
```

Om du vill skapa en variabel i ett visst omfång använder du en omfångs modifierare eller **omfattnings** parametern för `Set-Variable` . Följande kommando skapar en variabel i det globala omfånget:

```powershell
New-Variable -Scope global -Name a -Value "One"
```

Du kan också använda omfattnings parametern för `New-Alias` `Set-Alias` cmdletarna, eller `Get-Alias` för att ange omfånget. Följande kommando skapar ett alias i det globala omfånget:

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

Om du vill hämta funktionerna i ett visst omfång använder `Get-Item` du cmdleten när du befinner dig i omfånget. `Get-Item`Cmdleten har ingen **omfattnings** parameter.

> [!NOTE]
> För de cmdletar som använder **omfattnings** parametern kan du också referera till omfång efter nummer. Talet beskriver den relativa positionen för ett omfång till ett annat. Omfattning 0 representerar den aktuella eller lokala omfattningen. Område 1 anger den direkta överordnade omfattningen. Omfattning 2 visar överordnad för det överordnade omfånget och så vidare. Numrerade omfattningar är användbara om du har skapat många rekursiva omfång.

### <a name="using-dot-source-notation-with-scope"></a>Använda punkt käll notation med omfång

Skript och funktioner följer alla regler för omfattning. Du skapar dem i ett visst omfång, och de påverkar bara det omfånget om du inte använder en cmdlet-parameter eller en omfångs modifierare för att ändra omfattningen.

Men du kan lägga till ett skript eller en funktion i det aktuella omfånget med hjälp av punkt käll notation. När ett skript körs i det aktuella omfånget är alla funktioner, alias och variabler som skriptet skapar tillgängliga i det aktuella omfånget.

Om du vill lägga till en funktion i det aktuella omfånget skriver du en punkt (.) och ett blank steg före sökvägen och namnet på funktionen i funktions anropet.

Om du till exempel vill köra Sample.ps1-skriptet från C:\Scripts-katalogen i skript omfånget (standard för skript) använder du följande kommando:

```powershell
c:\scripts\sample.ps1
```

Om du vill köra Sample.ps1 skriptet i det lokala omfånget använder du följande kommando:

```powershell
. c:\scripts.sample.ps1
```

När du använder anrops operatorn (&) för att köra en funktion eller ett skript, läggs den inte till i det aktuella omfånget. I följande exempel används anrops operatorn:

```powershell
& c:\scripts.sample.ps1
```

Du kan läsa mer om anrops operatorn i [about_operators](about_operators.md).

Alla alias, funktioner eller variabler som Sample.ps1 skriptet skapar är inte tillgängliga i det aktuella omfånget.

## <a name="restricting-without-scope"></a>Begränsa utan omfång

Några PowerShell-begrepp liknar omfång eller interagerar med omfång. Dessa begrepp kan vara förvirrande med omfång eller beteende för omfång.

Sessioner, moduler och kapslade prompter är fristående miljöer, men de är inte underordnade omfång av det globala omfånget i sessionen.

### <a name="sessions"></a>Sessioner

En session är en miljö där PowerShell körs. När du skapar en-session på en fjärrdator upprättar PowerShell en permanent anslutning till fjärrdatorn. Med den permanenta anslutningen kan du använda sessionen för flera relaterade kommandon.

Eftersom en session är en innesluten miljö har den ett eget omfång, men en session är inte ett underordnat omfång för den session där den skapades. Sessionen börjar med en egen global omfattning. Det här omfånget är oberoende av sessionens globala omfång. Du kan skapa underordnade scope i sessionen. Du kan till exempel köra ett skript för att skapa en underordnad omfattning i en session.

### <a name="modules"></a>Moduler

Du kan använda en PowerShell-modul för att dela och leverera PowerShell-verktyg. En modul är en enhet som kan innehålla cmdlets, skript, funktioner, variabler, alias och andra användbara objekt. Om inget annat uttryckligen anges går det inte att nå objekten i en modul utanför modulen. Därför kan du lägga till modulen i din session och använda de offentliga objekten utan att oroa dig för att de andra objekten kan åsidosätta cmdlets, skript, funktioner och andra objekt i sessionen.

Som standard läses moduler in i den högsta nivån för det aktuella _sessionstillståndet_ , inte det aktuella _omfånget_. Det aktuella sessionstillståndet kan vara en sessionstillstånd eller det globala sessionstillståndet. Om du lägger till en modul i en session ändras inte omfånget. Om du befinner dig i det globala omfånget läses moduler in i det globala sessionstillståndet. Alla exporter placeras i globala tabeller.
Om du läser in module2 _inifrån Module1 läses_ module2 in i sessionstillståndet för Module1 inte det globala sessionstillståndet. Alla exporter från module2 placeras överst i Module1-sessionstillståndet. Om du använder `Import-Module -Scope local` placeras exporten i det aktuella omfångs objektet i stället för på den översta nivån. Om du är _i en modul_ och använder `Import-Module -Scope global` (eller `Import-Module -Global` ) för att läsa in en annan modul, läses den modulen och den exporteras till det globala sessionstillståndet i stället för modulens lokala sessionstillstånd. Den här funktionen har utformats för att skriva modul som manipulerar moduler. **WindowsCompatibility** -modulen gör detta för att importera proxy-moduler till läget för den globala sessionen.

I sessionstillstånd har moduler sin egen omfattning. Överväg följande modul `C:\temp\mod1.psm1` :

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

Nu skapar vi en global variabel `$a` , ger den ett värde och anropar funktionen **foo**.

```powershell
$a = "Goodbye"
foo
```

Modulen deklarerar variabeln `$a` i modulen scope, och funktionen **foo** matar sedan ut värdet för variabeln i båda omfattningarna.

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a>Kapslade prompter

Kapslade prompter har inget eget omfång. När du anger en kapslad prompt är den kapslade prompten en del av miljön. Men du är kvar inom det lokala omfånget.

Skript har sin egen omfattning. Om du felsöker ett skript och du når en Bryt punkt i skriptet, anger du skriptets omfattning.

### <a name="private-option"></a>Privat alternativ

Alias och variabler har en **alternativ** egenskap som kan ta värdet **privat**. Objekt som har alternativet **privat** kan visas och ändras i det omfång som de skapas i, men de kan inte visas eller ändras utanför det omfånget.

Om du till exempel skapar en variabel som har ett privat alternativ i det globala omfånget och sedan kör ett skript, `Get-Variable` visar kommandon i skriptet inte den privata variabeln. Om du använder den globala omfångs modifieraren i den här instansen visas inte den privata variabeln.

Du kan använda alternativ parametern för `New-Variable` `Set-Variable` cmdletarna,, `New-Alias` och `Set-Alias` för att ställa in värdet för alternativ egenskapen på privat.

### <a name="visibility"></a>Visibility (Sikt)

Egenskapen **visibility** för en variabel eller ett alias bestämmer om du kan se objektet utanför behållaren där det skapades. En behållare kan vara en modul, ett skript eller en snapin-modul. Synligheten är utformad för behållare på samma sätt som **alternativ** egenskapens **privata** värde är utformat för omfattningar.

Egenskapen **visibility** tar de **offentliga** och **privata** värdena. Objekt som har privat synlighet kan endast visas och ändras i den behållare där de skapades. Om behållaren läggs till eller importeras går det inte att visa eller ändra objekt som har privat synlighet.

Eftersom synligheten är utformad för behållare fungerar den på olika sätt i ett omfång.

- Om du skapar ett objekt som har privat synlighet i det globala omfånget kan du inte Visa eller ändra objektet i någon omfattning.
- Om du försöker visa eller ändra värdet för en variabel som har privat synlighet, returnerar PowerShell ett fel meddelande.

Du kan använda `New-Variable` `Set-Variable` cmdletarna och för att skapa en variabel som har privat synlighet.

## <a name="examples"></a>Exempel

### <a name="example-1-change-a-variable-value-only-in-a-script"></a>Exempel 1: ändra bara ett variabel värde i ett skript

Följande kommando ändrar värdet för `$ConfirmPreference` variabeln i ett skript. Ändringen påverkar inte det globala omfånget.

För att visa värdet för `$ConfirmPreference` variabeln i det lokala omfånget använder du följande kommando:

```
PS>  $ConfirmPreference
High
```

Skapa ett Scope.ps1-skript som innehåller följande kommandon:

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

Kör skriptet. Skriptet ändrar värdet för `$ConfirmPreference` variabeln och rapporterar värdet i skript omfånget. Utdata bör likna följande utdata:

```output
The value of $ConfirmPreference is Low.
```

Testa sedan det aktuella värdet för `$ConfirmPreference` variabeln i det aktuella omfånget.

```
PS>  $ConfirmPreference
High
```

Det här exemplet visar att ändringar av värdet för en variabel i skript omfattningen inte påverkar variabelns värde i det överordnade omfånget.

### <a name="example-2-view-a-variable-value-in-different-scopes"></a>Exempel 2: Visa ett variabel värde i olika omfång

Du kan använda omfångs modifierare för att visa värdet för en variabel i det lokala området och i en överordnad omfattning.

Definiera först en `$test` variabel i det globala omfånget.

```powershell
$test = "Global"
```

Skapa sedan ett Sample.ps1-skript som definierar `$test` variabeln. I skriptet använder du en omfattnings modifierare för att referera till antingen den globala eller lokala versionen av `$test` variabeln.

I Sample.ps1:

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

När du kör Sample.ps1 bör utdata likna följande utdata:

```output
The local value of $test is Local.
The global value of $test is Global.
```

När skriptet har slutförts definieras bara det globala värdet för `$test` i sessionen.

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a>Exempel 3: ändra värdet för en variabel i ett överordnat område

Om du inte skyddar ett objekt med hjälp av alternativet privat eller någon annan metod, kan du Visa och ändra värdet för en variabel i ett överordnat område.

Definiera först en `$test` variabel i det globala omfånget.

```powershell
$test = "Global"
```

Skapa sedan ett Sample.ps1-skript som definierar `$test` variabeln. I skriptet använder du en omfattnings modifierare för att referera till antingen den globala eller lokala versionen av `$test` variabeln.

I Sample.ps1:

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

När skriptet har slutförts ändras det globala värdet för `$test` .

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a>Exempel 4: skapa en privat variabel

En privat variabel är en variabel som har en **alternativ** egenskap som har värdet *privat*. *Privata* variabler ärvs av det underordnade omfånget, men de kan bara visas eller ändras i den omfattning som de skapades i.

Följande kommando skapar en privat variabel som kallas `$ptest` i det lokala omfånget.

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

Du kan visa och ändra värdet för `$ptest` i det lokala omfånget.

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

Skapa sedan ett Sample.ps1-skript som innehåller följande kommandon. Kommandot försöker visa och ändra värdet för `$ptest` .

I Sample.ps1:

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

`$ptest`Variabeln är inte synlig i skript omfånget, utdata är tom.

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a>Exempel 5: använda en lokal variabel i ett fjärran slutet kommando

För variabler i ett fjärrkommando som skapats i den lokala sessionen använder du `Using` omfångs modifieraren. PowerShell förutsätter att variablerna i fjärrkommandon har skapats i fjärrsessionen.

Syntax:

```
$Using:<VariableName>
```

Följande kommandon skapar till exempel en `$Cred` variabel i den lokala sessionen och använder sedan `$Cred` variabeln i ett fjärran slutet kommando:

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

Användnings området introducerades i PowerShell 3,0. I PowerShell 2,0, för att ange att en variabel har skapats i den lokala sessionen, använder du följande kommando format.

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a>Se även

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[Start-ThreadJob](/powershell/module/ThreadJob/Start-ThreadJob)
