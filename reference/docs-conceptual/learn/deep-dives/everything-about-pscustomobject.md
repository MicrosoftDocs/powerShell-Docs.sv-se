---
title: Allt du ville veta om PSCustomObject
description: PSCustomObject är ett enkelt sätt att skapa strukturerade data.
ms.date: 07/29/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 9a5cab7e662ef89b6565a29079ce1d5a657f94d0
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410146"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a>Allt du ville veta om PSCustomObject

`PSCustomObject`s är ett bra verktyg som du kan lägga till i ditt verktyg i PowerShell-verktyget. Vi börjar med grunderna och arbetar på vårt sätt i de mer avancerade funktionerna. Idén bakom att använda en `PSCustomObject` är att skapa strukturerade data på ett enkelt sätt. Ta en titt på det första exemplet och du får en bättre uppfattning om vad det innebär.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="creating-a-pscustomobject"></a>Skapa en PSCustomObject

Jag älskar att använda `[PSCustomObject]` i PowerShell. Det har aldrig varit enklare att skapa ett användbart objekt.
Därför ska jag hoppa över alla andra sätt som du kan skapa ett objekt, men jag behöver nämna att de flesta av dessa exempel är PowerShell v 3.0 och senare.

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

Den här metoden fungerar bra för mig eftersom jag använder hash för allt du behöver. Men det finns tillfällen då jag skulle vilja att PowerShell ska behandla hash mer som ett objekt. Den första platsen du märker skillnaden är när du vill använda `Format-Table` eller `Export-CSV` och du inser att en hash-tabellen bara är en samling nyckel/värde-par.

Du kan sedan komma åt och använda värdena som du skulle göra med ett vanligt objekt.

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a>Konvertera en hash-hash

När jag är på ämnet vet du att du kunde göra detta:

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

Jag föredrar att skapa objektet från Start, men det finns tillfällen då du måste arbeta med en hash-tabellen först. Det här exemplet fungerar eftersom konstruktorn tar en hash-tabellen för objekt egenskaperna. En viktig anmärkning är att medan den här metoden fungerar är den inte en exakt motsvarighet. Den största skillnaden är att ordningen på egenskaperna inte bevaras.

### <a name="legacy-approach"></a>Äldre metod

Du kanske har sett personer `New-Object` som använder för att skapa anpassade objekt.

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

På så sätt är det ganska lite långsammare, men det kan vara det bästa alternativet i tidiga versioner av PowerShell.

### <a name="saving-to-a-file"></a>Spara till en fil

Jag hittar det bästa sättet att spara en hash-fil i en fil är att spara den som JSON. Du kan importera tillbaka den till en `[PSCustomObject]`

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

Jag ser fler sätt att spara objekt i en fil i min artikel på [många sätt att läsa och skriva till filer][].

## <a name="working-with-properties"></a>Arbeta med egenskaper

### <a name="adding-properties"></a>Lägga till egenskaper

Du kan fortfarande lägga till nya egenskaper till din `PSCustomObject` med `Add-Member` .

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a>Ta bort egenskaper

Du kan också ta bort egenskaper från ett objekt.

```powershell
$myObject.psobject.properties.remove('ID')
```

`psobject`Är en dold egenskap som ger dig åtkomst till bas objektets metadata.

### <a name="enumerating-property-names"></a>Räknar upp egenskaps namn

Ibland behöver du en lista över alla egenskaps namn för ett objekt.

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

Vi kan även hämta samma lista av `psobject` egenskapen.

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a>Dynamiskt åtkomst till egenskaper

Jag har redan nämnt att du kan komma åt egenskaps värden direkt.

```powershell
$myObject.Name
```

Du kan använda en sträng för egenskaps namnet och den fungerar fortfarande.

```powershell
$myObject.'Name'
```

Vi kan ta det här ett steg och använda en variabel för egenskaps namnet.

```powershell
$property = 'Name'
$myObject.$property
```

Jag vet att det ser konstigt ut, men det fungerar.

### <a name="convert-pscustombobject-into-a-hashtable"></a>Konvertera PSCustombObject till en hash-form

Om du vill fortsätta från det sista avsnittet kan du dynamiskt gå igenom egenskaperna och skapa en hash-grupp från dem.

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a>Testa för egenskaper

Om du behöver veta om en egenskap finns kan du bara kontrol lera att egenskapen har ett värde.

```powershell
if( $null -ne $myObject.ID )
```

Men om värdet kan vara `$null` och du fortfarande behöver söka efter det kan du kontrol lera det `psobject.properties` .

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a>Lägga till objekt metoder

Om du behöver lägga till en skript metod i ett objekt kan du göra det med `Add-Member` och en `ScriptBlock` . Du måste använda den `this` automatiska variabeln Reference för det aktuella objektet. Här är en `scriptblock` för att omvandla ett objekt till en hash-objekt. (samma kod bildar det sista exemplet)

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

Sedan lägger vi till den till vårt objekt som en skript egenskap.

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

Sedan kan vi anropa vår funktion så här:

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a>Objekt vs värde typer

Objekt och värde typer hanterar inte variabel tilldelningar på samma sätt. Om du tilldelar värde typer till varandra kopieras bara värdet till den nya variabeln.

```powershell
$first = 1
$second = $first
$second = 2
```

I det här fallet `$first` är 1 och `$second` är 2.

Objektvariabler innehåller en referens till det faktiska objektet. När du tilldelar ett objekt till en ny variabel refererar de fortfarande till samma objekt.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

Eftersom `$third` och `$fourth` refererar samma instans av ett objekt, både `$third.key` och `$fourth.Key` är 4.

### <a name="psobjectcopy"></a>psobject. Copy ()

Om du behöver en äkta kopia av ett objekt kan du klona det.

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

Klona skapar en ytlig kopia av objektet. De har olika instanser nu och `$third.key` är 3 och `$fourth.Key` 4 i det här exemplet.

Jag kallar en ytlig kopia eftersom du har kapslade objekt. (där egenskaperna innehåller andra objekt). Endast värdena på den översta nivån kopieras. De underordnade objekten kommer att referera till varandra.

### <a name="pstypename-for-custom-object-types"></a>PSTypeName för anpassade objekt typer

Nu när vi har ett-objekt finns det några saker som vi kan göra med det som kanske inte är nästan uppenbart. Det första du behöver göra är att ge det ett `PSTypeName` . Det här är det vanligaste sättet att se vad de gör:

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

Jag har nyligen identifierat ett annat sätt att göra detta från det här [inlägget av/u/markekraus][]. Jag gjorde ett litet utforska och fler inlägg om idén från [Adam Bertram][] och [Mike Shepard][] där de pratar om den här metoden som gör det möjligt att definiera den infogade.

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

Jag älskar hur bra det här passar in i språket. Nu när vi har ett objekt med rätt typ namn kan vi göra några fler saker.

> [!NOTE]
> Du kan också skapa anpassade PowerShell-typer med PowerShell-klasser. Mer information finns i [Översikt över PowerShell-klass](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).

## <a name="using-defaultpropertyset-the-long-way"></a>Använda DefaultPropertySet (det långa sättet)

PowerShell bestämmer för oss vilka egenskaper som ska visas som standard. Många av de inbyggda kommandona har en `.ps1xml` [formateringsinformation][] som gör all tungbar. Från det här [inlägget av BOE Prox][]finns det ett annat sätt för oss att göra detta på vårt anpassade objekt med bara PowerShell. Vi kan ge den en `MemberSet` för IT-användning.

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

Nu när mitt objekt bara hamnar på gränssnittet visas endast dessa egenskaper som standard.

### <a name="update-typedata-with-defaultpropertyset"></a>Uppdatera-TypeData med DefaultPropertySet

Det här är bra men jag har nyligen sett ett bättre sätt att titta [på PowerShell unplugged 2016 med Jeffrey Snover & Dan Jones][psunplugged]. Jeffrey använde [Update-TypeData][] för att ange standard egenskaperna.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

Det är så enkelt att jag skulle kunna komma ihåg det om jag inte har det här inlägget som en snabb referens. Nu kan jag enkelt skapa objekt med massor av egenskaper och samtidigt ge det ett snyggt visnings läge när du tittar på det från gränssnittet. Om jag behöver åtkomst till eller se de andra egenskaperna finns de fortfarande där.

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a>Uppdatera-TypeData med ScriptProperty

Något annat jag fick från den videon skapade skript egenskaper för dina objekt. Det kan vara en lämplig stund att peka på att det här fungerar för befintliga objekt.

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

Du kan göra detta innan objektet skapas eller efter och det fungerar fortfarande. Detta är vad som gör detta annorlunda och använder `Add-Member` med en skript egenskap. När du använder `Add-Member` det som refereras tidigare finns det bara på den aktuella instansen av objektet. Den här gäller för alla objekt med detta `TypeName` .

## <a name="function-parameters"></a>Funktions parametrar

Du kan nu använda de här anpassade typerna för parametrar i dina funktioner och skript. Du kan använda en funktion för att skapa dessa anpassade objekt och sedan skicka dem till andra funktioner.

```powershell
param( [PSTypeName('My.Object')]$Data )
```

PowerShell kräver att objektet är av den typ som du har angett. Ett verifierings fel genereras om typen inte matchar automatiskt för att spara ditt steg för att testa det i din kod. Ett bra exempel på att låta PowerShell göra det bäst.

### <a name="function-outputtype"></a>Funktions OutputType

Du kan också definiera en `OutputType` för dina avancerade funktioner.

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

Värdet för **OutputType** -attributet är bara en dokumentations anteckning. Den är inte härledd från funktions koden eller jämförs med själva funktionen utdata.

Den främsta anledningen till att du använder en utdatatyp är så att meta-information om din funktion motsvarar dina avsikter. Saker som `Get-Command` och `Get-Help` som din utvecklings miljö kan dra nytta av. Om du vill ha mer information kan du ta en titt på hjälpen: [about_Functions_OutputTypeAttribute][].

Om du använder pester för att testa dina funktioner, är det en bra idé att verifiera objekten som matchar din **OutputType**. Detta kan fånga variabler som bara faller på röret när de inte borde det.

## <a name="closing-thoughts"></a>Stänga idéer

Kontexten för detta var allt om `[PSCustomObject]` , men en stor del av den här informationen gäller för objekt i allmänhet.

Jag har sett de flesta av de här funktionerna i överföring innan, men såg aldrig ut dem som en samling information på `PSCustomObject` . Precis den senaste veckan jag stumbled en annan och var förvånad att jag inte hade sett det tidigare. Jag ville hämta alla dessa idéer, så du kan förhoppnings vis se den större bilden och vara medveten om dem när du har möjlighet att använda dem. Jag hoppas att du har lärt dig något och kan hitta ett sätt att arbeta med dina skript.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[publicera efter BOE prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[formaterar fil]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[Många sätt att läsa och skriva till filer]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[publicera efter/u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam-Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Uppdatera – TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
