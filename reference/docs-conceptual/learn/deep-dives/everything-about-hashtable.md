---
title: Allt du ville veta om hash
description: Hash är verkligen viktiga i PowerShell så det är bra att ha en solid förståelse för dem.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: a471c0fe2c48820d6c1d152e2850b1e431d28f23
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686072"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a>Allt du ville veta om hash

Jag vill göra ett steg tillbaka och prata om [hash][]. Jag använder dem nu. Jag har undervisat någon om dem efter vårt användar grupp möte förra natten och jag realiserade att jag hade samma förvirring om dem som han hade. Hash är verkligen viktiga i PowerShell så det är bra att ha en solid förståelse för dem.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="hashtable-as-a-collection-of-things"></a>Hash-objekt som en samling saker

Jag vill först se en hash- **hash** som en samling i den traditionella definitionen av en hash-tabellen. Den här definitionen ger dig en grundläggande förståelse för hur de fungerar när de används för mer avancerade saker senare. Att hoppa över den här förståelsen är ofta en källa för förvirring.

## <a name="what-is-an-array"></a>Vad är en matris?

Innan jag hoppar till vad en **hash** -tabell är måste jag nämna [matriser][] först. I den här diskussionen är en matris en lista eller samling med värden eller objekt.

```powershell
$array = @(1,2,3,5,7,11)
```

När du har dina objekt i en matris kan du antingen använda `foreach` för att iterera över listan eller använda ett index för att komma åt enskilda element i matrisen.

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

Du kan också uppdatera värden med hjälp av ett index på samma sätt.

```powershell
$array[2] = 13
```

Jag har precis skapat ytan på matriser, men den bör placera dem i rätt sammanhang när jag flyttar till hash.

## <a name="what-is-a-hashtable"></a>Vad är en hash-information?

Jag ska börja med en grundläggande teknisk beskrivning av vad hash är, i den allmänna meningen, innan jag växlar till andra sätt som PowerShell använder dem.

En hash-tabell är en data struktur, ungefär som en matris, förutom att du lagrar varje värde (objekt) med hjälp av en nyckel. Det är ett grundläggande nyckel/värde-lager. Först skapar vi en tom hash-sträng.

```powershell
$ageList = @{}
```

Observera att klammerparenteser, i stället för parenteser, används för att definiera en hash-hash. Sedan lägger vi till ett objekt med en nyckel som detta:

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

Personens namn är nyckeln och deras ålder är det värde som jag vill spara.

## <a name="using-the-brackets-for-access"></a>Använda hakparenteser för åtkomst

När du har lagt till värdena i hash-tabellen kan du dra tillbaka dem med samma nyckel (i stället för att använda ett numeriskt index som du skulle ha för en matris).

```powershell
$ageList['Kevin']
$ageList['Alex']
```

När jag vill att Kevins ålder ska jag använda sitt namn för att komma åt det. Vi kan använda den här metoden för att lägga till eller uppdatera värden i hash-tabellen. Detta är precis som att använda `add()` funktionen ovan.

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

Det finns en annan syntax som du kan använda för att komma åt och uppdatera värden som jag får i ett senare avsnitt. Om du kommer till PowerShell från ett annat språk bör dessa exempel anpassas i med hur du kan använda hash tidigare.

### <a name="creating-hashtables-with-values"></a>Skapa hash med värden

Hittills har jag skapat en tom hash-hash för de här exemplen. Du kan fylla i nycklar och värden i förväg när du skapar dem.

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a>Som en uppslags tabell

Det verkliga värdet för den här typen av hash-tabell är att du kan använda dem som en uppslags tabell. Här är ett enkelt exempel.

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

I det här exemplet anger du en miljö för `$env` variabeln och den kommer att välja rätt server. Du kan använda en `switch($env){...}` för ett val som detta, men en hash-hash är ett bra alternativ.

Detta blir ännu bättre när du skapar uppslags tabellen dynamiskt för att använda den senare. Tänk på att använda den här metoden när du behöver referera något. Jag tror att vi ser detta ännu mer om PowerShell inte var så användbart vid filtrering av pipe med `Where-Object` . Om du någonsin är i en situation där prestanda är viktigt måste den här metoden beaktas.

Jag säger inte att det går snabbare, men det passar i regeln [om prestanda, testa det][].

#### <a name="multiselection"></a>Multimarkering

I allmänhet tänker du på en hash som ett nyckel/värde-par, där du anger en nyckel och får ett värde. Med PowerShell kan du ange en matris med nycklar för att hämta flera värden.

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

I det här exemplet använder jag samma uppslags-hash från ovanstående och ger tre olika mat ris format för att hämta matchningarna. Det här är en dold gem i PowerShell som de flesta inte känner till.

## <a name="iterating-hashtables"></a>Iterera hash

Eftersom en hash-tabell är en samling nyckel/värde-par itererar du över den på ett annat sätt än för en matris eller en normal lista med objekt.

Det första du ska märka är att om du rör din hash-post behandlar pipe det som ett objekt.

```powershell
PS> $ageList | Measure-Object
count : 1
```

Även om `.count` egenskapen visar hur många värden den innehåller.

```powershell
PS> $ageList.count
2
```

Du kommer runt det här problemet genom att använda- `.values` egenskapen om allt du behöver är bara värdena.

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

Det är ofta mer användbart att räkna upp nycklar och använda dem för att få åtkomst till värdena.

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

Här är samma exempel med en `foreach(){...}` slinga.

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

Vi använder varje nyckel i hash-tabellen och använder den för att få åtkomst till värdet. Det här är ett vanligt mönster när du arbetar med hash som en samling.

### <a name="getenumerator"></a>GetEnumerator ()

Det gör att vi kan `GetEnumerator()` iterera över vår hash.

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

Uppräkna ren ger dig varje nyckel/värde-par ett efter ett annat. Den har utformats särskilt för detta användnings fall. Tack för att du [markerar Kraus](https://get-PowerShellblog.blogspot.com) för att påminna mig om det här.

### <a name="badenumeration"></a>BadEnumeration

En viktig information är att du inte kan ändra en hash-tabell när den har räknats upp. Om vi börjar med vårt grundläggande `$environments` exempel:

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

Och försök att ange varje nyckel till samma server värde Miss lyckas.

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

Detta kommer också att Miss Miss förfinat även om det ser ut så här:

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

Den här situationen är att klona nycklarna innan du utför uppräkningen.

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a>Hash-egenskap som en samling egenskaper

Hittills var den typ av objekt som vi placerade i vår hash alla samma typ av objekt. Jag har använt åldrar i alla dessa exempel och nyckeln var personens namn. Detta är ett bra sätt att titta på den när din samling objekt har ett namn. Ett annat vanligt sätt att använda hash i PowerShell är att lagra en samling egenskaper där nyckeln är namnet på egenskapen. Jag kommer att gå igenom den idén i nästa exempel.

### <a name="property-based-access"></a>Egenskaps-baserad åtkomst

Användningen av egenskaps-baserad åtkomst ändrar Dynamics-hash och hur du kan använda dem i PowerShell. Här är vårt vanliga exempel ovan som behandlar nycklarna som egenskaper.

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

Precis som i exemplen ovan lägger det här exemplet till dessa nycklar om de inte redan finns i hash-tabellen. Beroende på hur du har definierat dina nycklar och vilka värden som är, är detta antingen lite konstigt eller en perfekt anpassning. Exemplet på ålders listan har fungerat bra fram till den här punkten. Vi behöver ett nytt exempel för att det ska gå att gå vidare.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

Och vi kan lägga till och komma åt attribut på `$person` liknande sätt.

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

Alla en plötslig denna hash börjar känna och fungerar som ett-objekt. Det är fortfarande en samling saker, så alla exempel ovan gäller fortfarande. Vi är bara på plats från en annan vy.

### <a name="checking-for-keys-and-values"></a>Söker efter nycklar och värden

I de flesta fall kan du bara testa för värdet med något som liknar detta:

```powershell
if( $person.age ){...}
```

Det är enkelt men har varit källan till många buggar för mig eftersom jag skulle se en viktig information i min logik. Jag började använda den för att testa om en nyckel fanns. När värdet var `$false` eller noll returnerades instruktionen `$false` oväntad.

```powershell
if( $person.age -ne $null ){...}
```

Detta fungerar runt det här problemet för noll värden men inte $null vs-nycklar som inte finns. I de flesta fall behöver du inte göra åtskillnaden men det finns funktioner för när du gör det.

```powershell
if( $person.ContainsKey('age') ){...}
```

Vi har också en `ContainsValue()` för situation där du behöver testa ett värde utan att känna till nyckeln eller iterera hela samlingen.

### <a name="removing-and-clearing-keys"></a>Ta bort och rensa nycklar

Du kan ta bort nycklar med `.Remove()` funktionen.

```powershell
$person.remove('age')
```

Genom att tilldela dem ett `$null` värde är det bara att ha en nyckel som har ett `$null` värde.

Ett vanligt sätt att rensa en hash-text är att bara initiera den till en tom hash-text.

```powershell
$person = @{}
```

Även om det fungerar kan du försöka använda `clear()` funktionen i stället.

```powershell
$person.clear()
```

Detta är en av de instanser som använder funktionen för att skapa självdokumenterande kod och det gör avsikter i koden mycket rent.

## <a name="all-the-fun-stuff"></a>Alla roliga saker

### <a name="ordered-hashtables"></a>Beställda hash

Som standard beställs hash inte (eller sorteras). I det traditionella sammanhanget spelar det ingen roll när du alltid använder en nyckel för att få åtkomst till värden. Du kanske upptäcker att du vill att egenskaperna ska stanna kvar i den ordning som du definierar dem. Thankfully finns ett sätt att göra det med `ordered` nyckelordet.

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

Nu när du räknar upp nycklar och värden finns de kvar i den ordningen.

### <a name="inline-hashtables"></a>Infogad hash

När du definierar en hash-tabellen på en rad kan du avgränsa nyckel/värde-par med ett semikolon.

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

Detta är praktiskt om du skapar dem i en pipe.

### <a name="custom-expressions-in-common-pipeline-commands"></a>Anpassade uttryck i vanliga pipeline-kommandon

Det finns några cmdletar som stöder användningen av hash för att skapa anpassade eller beräknade egenskaper. Du ser ofta detta med `Select-Object` och `Format-Table` . Hash har en särskild syntax som ser ut så här när den är helt expanderad.

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

`name`Är vad cmdleten skulle märka den kolumnen. `expression`Är ett skript block som körs där `$_` är värdet för objektet i pipe. Här är skriptet i praktiken:

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Property name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

Jag placerade det i en variabel, men det kan enkelt definieras infogat och du kan förkorta `name` till `n` och `expression` `e` samtidigt när du befinner dig.

```powershell
$drives | Select-Object -property name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

Jag vill inte veta hur lång tid det tar för kommandon och ger ofta vissa dåliga beteenden som jag inte kan komma åt. Jag vill förmodligen skapa en ny hash-grupp eller `pscustomobject` med alla fält och egenskaper i stället för att använda den här metoden i skript. Men det finns en massa kod som gör det så att du kan vara medveten om det. Jag pratar om att skapa en `pscustomobject` senare version.

### <a name="custom-sort-expression"></a>Anpassat sorterings uttryck

Det är enkelt att sortera en samling om objekten har de data som du vill sortera på. Du kan antingen lägga till data i objektet innan du sorterar det eller skapar ett anpassat uttryck för `Sort-Object` .

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

I det här exemplet tar du en lista med användare och använder en anpassad cmdlet för att få ytterligare information för sorteringen.

#### <a name="sort-a-list-of-hashtables"></a>Sortera en lista över hash

Om du har en lista över hash som du vill sortera, ser du att de `Sort-Object` inte behandlar dina nycklar som egenskaper. Vi kan få en tur genom att använda ett anpassat sorterings uttryck.

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a>Ihopbuntning-hash vid cmdletar

Det här är en av mina favorit saker om hash som många människor inte kan upptäcka tidigt på.
Tanken är att i stället för att tillhandahålla alla egenskaper till en cmdlet på en rad kan du i stället paketera dem i en hash-regel först. Sedan kan du ge hash-tabellen till funktionen på ett särskilt sätt.
Här är ett exempel på hur du skapar ett DHCP-scope på vanligt sätt.

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

Utan att använda [ihopbuntning][]måste alla dessa saker definieras på en enda rad. Den rullar antingen bort från skärmen eller kommer att figursättas där det någonsin tycks som det ska. Jämför nu med ett kommando som använder ihopbuntning.

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

Användningen av- `@` tecknet i stället för `$` är vad som anropar åtgärden splat.

Ta en stund till att uppskatta hur enkelt det är att läsa. De är exakt samma kommando med samma värden. Den andra är enklare att förstå och fortsätta att gå vidare.

Jag använder ihopbuntning när kommandot är för långt. Jag definierar för länge för att det ska gå att rulla åt fönstret. Om jag träffar tre egenskaper för en funktion, är strider att jag skriver om den med en splatted-hash.

### <a name="splatting-for-optional-parameters"></a>Ihopbuntning för valfria parametrar

Ett av de vanligaste sätten att använda ihopbuntning är att hantera valfria parametrar som kommer från någon annan plats i skriptet. Anta att jag har en funktion som omsluter ett `Get-CIMInstance` samtal som har ett valfritt `$Credential` argument.

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

Jag börjar genom att skapa min hash-tabell med vanliga parametrar. Sedan lägger jag till den `$Credential` om den finns.
Eftersom jag använder ihopbuntning här behöver jag bara anropa `Get-CIMInstance` i min kod en gång. Det här design mönstret är mycket rent och kan hantera många valfria parametrar enkelt.

För att vara rättvist kan du skriva kommandon för att tillåta `$null` värden för parametrar. Du har precis inte alltid kontroll över de andra kommandon som du ringer.

### <a name="multiple-splats"></a>Flera splats

Du kan splat flera hash till samma cmdlet. Om vi besöker vårt ursprungliga ihopbuntning-exempel:

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

Jag använder den här metoden när jag har en gemensam uppsättning parametrar som jag skickar till flera kommandon.

### <a name="splatting-for-clean-code"></a>Ihopbuntning för ren kod

Det finns inget fel med ihopbuntning en enda parameter om du gör kod rensning.

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a>Körbara ihopbuntning

Ihopbuntning fungerar även på vissa körbara filer som använder en `/param:value` syntax. `Robocopy.exe`har till exempel vissa parametrar som detta.

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

Jag vet inte att det är allt som är användbart, men jag hittade det intressant.

## <a name="adding-hashtables"></a>Lägger till hash

Hash stöder addition-operatorn för att kombinera två hash.

```powershell
$person += @{Zip = '78701'}
```

Detta fungerar bara om de två hash inte delar en nyckel.

## <a name="nested-hashtables"></a>Kapslade hash

Vi kan använda hash som värden i en hash.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

Jag startade med en grundläggande hash-enhet som innehåller två nycklar. Jag har lagt till en nyckel `location` med namnet med en tom hash-nyckel. Sedan lade jag till de sista två objekten i den hash-tabellen `location` . Vi kan göra detta alla infogade.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

Detta skapar samma hash-typ som vi såg ovan och kan komma åt egenskaperna på samma sätt.

```powershell
$person.location.city
Austin
```

Det finns många sätt att närma dig strukturen för dina objekt. Här är ett andra sätt att titta på en kapslad hash.

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

Detta blandar konceptet med att använda hash som en samling objekt och en samling egenskaper. Värdena är fortfarande lätta att komma åt även när de är kapslade med den metod som du föredrar.

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

Jag brukar använda egenskapen dot när jag behandlar den som en egenskap. Det är vanligt att jag har definierat statiskt i min kod och jag vet att de inte är på huvud sidan. Om jag behöver gå igenom listan eller program mässigt komma åt nycklarna använder jag hakparenteser för att ange nyckel namnet.

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

Med möjligheten att kapsla hash får du stor flexibilitet och alternativ.

### <a name="looking-at-nested-hashtables"></a>Titta på kapslade hash

Så snart du börjar kapsla in hash kommer du att behöva ett enkelt sätt att titta på dem från-konsolen. Om jag tar den sista hash-enheten får jag en utmatning som ser ut så här och den går bara så djup:

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

Kommandot gå till för att titta på dessa saker är att `ConvertTo-JSON` det är mycket rent och jag använder ofta JSON på andra saker.

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

Även om du inte vet JSON bör du kunna se vad du letar efter. Det finns ett- `Format-Custom` kommando för strukturerade data, t. ex. om du fortfarande vill ha JSON-vyn bättre.

## <a name="creating-objects"></a>Skapa objekt

Ibland behöver du bara ha ett objekt och använda en hash-hash för att hålla egenskaper som inte får jobbet gjort. Oftast vill du se nycklarna som kolumn namn. En `pscustomobject` gör det enkelt.

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

Även om du inte skapar den `pscustomobject` från början, kan du alltid skicka den senare när det behövs.

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

Jag har redan en detaljerad uppskrivning för [PSCustomObject][] som du bör läsa efter det här. Det bygger på en stor mängd saker som du har lärt dig här.

## <a name="reading-and-writing-hashtables-to-file"></a>Läser och skriver hash till fil

### <a name="saving-to-csv"></a>Sparar till CSV

Kämpar med att hämta en hash-fil för att spara till en CSV-fil är ett av de problem som jag hade refererat till ovan. Konvertera din hash-post till en så `pscustomobject` sparas den korrekt till CSV. Det hjälper om du börjar med en `pscustomobject` så att kolumn ordningen bevaras. Men du kan omvandla det till en `pscustomobject` infogad, om det behövs.

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

Kolla återigen in My Write-in using a [PSCustomObject][].

### <a name="saving-a-nested-hashtable-to-file"></a>Spara en kapslad hash-fil i filen

Om jag behöver spara en kapslad hash-fil till en fil och sedan läsa in den igen, använder jag JSON-cmdletar för att göra det.

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

Det finns två viktiga punkter om den här metoden. Det första är att JSON skrivs ut flera rader så jag måste använda `-Raw` alternativet för att läsa tillbaka det till en enda sträng. Det andra är att det importerade objektet inte längre är ett `[hashtable]` . Det är nu en `[pscustomobject]` och som kan orsaka problem om du inte förväntar dig.

Titta efter djupt kapslade hash. När du konverterar den till JSON kanske du inte får de resultat du förväntar dig.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

Använd **djup** parameter för att se till att du har expanderat alla kapslade hash.

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

Om du behöver det för att `[hashtable]` Importera måste du använda- `Export-CliXml` och- `Import-CliXml` kommandona.

### <a name="converting-json-to-hashtable"></a>Konvertera JSON till hash-sträng

Om du behöver konvertera JSON till en finns `[hashtable]` det ett sätt som jag känner till för att göra det med [JavaScriptSerializer][] i .net.

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

Från och med PowerShell V6 använder JSON-stödet NewtonSoft-JSON.NET och lägger till hash-stöd.

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

PowerShell 6,2 lade till **djup** parametern till `ConvertFrom-Json` . Standard **djupet** är 1024.

### <a name="reading-directly-from-a-file"></a>Läsa direkt från en fil

Om du har en fil som innehåller en hash-tabell med PowerShell-syntax, finns det ett sätt att importera den direkt.

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

Innehållet i filen importeras till en `scriptblock` och kontrollerar sedan att det inte finns några andra PowerShell-kommandon i den innan den körs.

Visste du att ett modul manifest (psd1-filen) bara är en hash-modul?

## <a name="keys-can-be-any-object"></a>Nycklar kan vara valfritt objekt

De flesta av tiden är nycklarna bara strängar. Vi kan lägga till citat tecken runt vad som helst och göra den till en nyckel.

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

Du kan göra lite udda saker som du kanske inte har realiserat.

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

Bara för att du ska kunna göra något, betyder det inte att du borde. Det sista ser bara ut som ett fel som väntar på att hända och skulle vara lätt att förstå för alla som läser koden.

Tekniskt sett behöver din nyckel inte vara en sträng, men de är lättare att tänka på om du bara använder strängar. Indexeringen fungerar dock inte bra med de komplexa nycklarna.

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

Att komma åt ett värde i hash-tabellen efter dess nyckel fungerar inte alltid. Exempel:

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

När nyckeln är en matris måste du omsluta `$key` variabeln i ett under uttryck så att den kan användas med member Access ()- `.` notation. Du kan också använda format för mat ris index ( `[]` ).

## <a name="use-in-automatic-variables"></a>Använd i automatiska variabler

### <a name="psboundparameters"></a>$PSBoundParameters

[$PSBoundParameters] [] är en automatisk variabel som bara finns inuti kontexten för en funktion.
Den innehåller alla parametrar som funktionen anropades med. Detta är inte exakt en hash utan är tillräckligt nära så att du kan behandla den som en.

Detta inkluderar att ta bort nycklar och ihopbuntning den till andra funktioner. Ta en närmare titt på den här om du upptäcker att du skriver proxy-funktioner.

Se [about_Automatic_Variables][] för mer information.

### <a name="psboundparameters-gotcha"></a>PSBoundParameters information

En viktig sak att komma ihåg är att detta bara innehåller de värden som skickas som parametrar. Om du även har parametrar med standardvärden men som inte skickas in av anroparen, `$PSBoundParameters` innehåller inte dessa värden. Detta är vanligt vis överblickat.

### <a name="psdefaultparametervalues"></a>$PSDefaultParameterValues

Med den här automatiska variabeln kan du tilldela standardvärden till alla cmdletar utan att ändra cmdleten.
Ta en titt på det här exemplet.

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

Detta lägger till en post i `$PSDefaultParameterValues` hash-tabellen som anger `UTF8` som standardvärdet för `Out-File -Encoding` parametern. Detta är sessionsläge så att du kan placera den i din `$profile` .

Jag använder det ofta för att före tilldela värden som jag anger ofta.

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

Detta accepterar även jokertecken så att du kan ange värden i bulk. Här följer några exempel på hur du kan använda det:

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

En mer djupgående analys finns i den här fantastiska artikeln om [automatiska standardinställningar][] av [Michael Sorens][].

## <a name="regex-matches"></a>Regex $Matches

När du använder `-match` operatorn skapas en automatisk variabel `$matches` som heter med resultatet av matchningen. Om du har ett under uttryck i ditt regex visas även dessa underordnade matchningar.

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a>Namngivna matchningar

Det här är en av mina favorit funktioner som de flesta personer inte känner till. Om du använder en namngiven regex-matchning, kan du komma åt matchning efter namn på matchningarna.

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

I exemplet ovan `(?<Name>.*)` är ett namngivet under uttryck. Värdet placeras sedan i `$Matches.Name` egenskapen.

## <a name="group-object--ashashtable"></a>Group-Object-AsHashtable

En liten känd funktion i `Group-Object` är att den kan omvandla vissa data uppsättningar till en hash-mängd.

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

Varje rad läggs till i en hash-tabell och den angivna egenskapen används som nyckel för att komma åt den.

## <a name="copying-hashtables"></a>Kopierar hash

En viktig sak att veta är att hash är objekt. Och varje variabel är bara en referens till ett objekt. Det innebär att det tar mer arbete att skapa en giltig kopia av en hash-hash.

### <a name="assigning-reference-types"></a>Tilldela referens typer

När du har en hash-adress och tilldelar den till en andra variabel pekar båda variablerna på samma hash.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

Det innebär att de är desamma eftersom ändringar av värdena i samma ändrar även värdena i den andra. Detta gäller även när du skickar hash till andra funktioner. Om dessa funktioner gör ändringar i denna hash ändras även originalet.

### <a name="shallow-copies-single-level"></a>Ytliga kopior, en nivå

Om vi har en enkel datahash som exemplet ovan kan vi använda `.Clone()` för att skapa en ytlig kopia.

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

På så sätt kan vi göra några grundläggande ändringar av en som inte påverkar den andra.

### <a name="shallow-copies-nested"></a>Ytliga kopior, kapslade

Anledningen till att det kallas en ytlig kopia är att den bara kopierar bas nivå egenskaperna. Om en av dessa egenskaper är en referens typ (t. ex. en annan hash-adress) pekar dessa kapslade objekt fortfarande på varandra.

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

Så du kan se att även om jag har klonat en hash-tabellen `person` . Vi behöver göra en djup kopia för att verkligen ha en andra hash som inte är länkad till den första.

### <a name="deep-copies"></a>Djupgående kopior

Det finns ett par olika sätt att skapa en djup kopia av en hash-hash (och behålla den som en hash-hash). Här är en funktion som använder PowerShell för att rekursivt skapa en djup kopia:

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

Den hanterar inte andra referens typer eller matriser, men det är en lämplig start punkt.

Ett annat sätt är att använda .net för att deserialisera den med hjälp av **CliXml** som i den här funktionen:

```powershell
function Get-DeepClone
{
    param(
        $InputObject
    )
    $TempCliXmlString = [System.Management.Automation.PSSerializer]::Serialize($obj, [int32]::MaxValue)
    return [System.Management.Automation.PSSerializer]::Deserialize($TempCliXmlString)
}
```

För mycket stora hash är avserialiserings funktionen snabbare när den skalas ut. Det finns dock några saker att tänka på när du använder den här metoden. Eftersom den använder **CliXml** är det minnes intensivt och om du klonar enorma hash kan det vara ett problem. En annan begränsning av **CliXml** är att det finns en djup begränsning på 48. Om du har en hash-datahash med 48 lager av kapslade hash, kommer kloningen att Miss Miss och ingen hash-tabellen kommer att matas ut alls.

## <a name="anything-else"></a>Något mer?

Jag täckte mycket jord snabbt. Min idé är att du kan sätta en ny eller förståelse för det bättre varje gång du läser det. Eftersom jag täckte det fullständiga spektrumet av den här funktionen finns det aspekter som bara kan gälla just nu. Det är perfekt OK och är en typ av förväntat beroende på hur mycket du arbetar med PowerShell.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[hash]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[lagringsmatriser]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Testa det om prestanda är viktigt]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[ihopbuntning]: /powershell/module/microsoft.powershell.core/about/about_splatting
[PSCustomObject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatiska standardinställningar]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
