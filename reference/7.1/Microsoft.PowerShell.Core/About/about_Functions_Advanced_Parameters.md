---
description: Förklarar hur du lägger till parametrar till avancerade funktioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 2a5b13475dd648a9f778d23b4089da00351b237c
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/28/2020
ms.locfileid: "93273459"
---
# <a name="about-functions-advanced-parameters"></a>Om functions avancerade parametrar

## <a name="short-description"></a>Kort beskrivning

Förklarar hur du lägger till parametrar till avancerade funktioner.

## <a name="long-description"></a>Lång beskrivning

Du kan lägga till parametrar till de avancerade funktioner som du skriver och använda parametriserade och-argument för att begränsa de parameter värden som användarna skickar med parametern.

De parametrar som du lägger till i din funktion är tillgängliga för användare utöver de vanliga parametrarna som PowerShell automatiskt lägger till i alla cmdletar och avancerade funktioner. Mer information om de gemensamma PowerShell-parametrarna finns i [about_CommonParameters](about_CommonParameters.md).

Från och med PowerShell 3,0 kan du använda ihopbuntning med `@Args` för att representera parametrarna i ett kommando. Ihopbuntning är giltig för enkla och avancerade funktioner. Mer information finns i [about_Functions](about_Functions.md) och [about_Splatting](about_Splatting.md).

## <a name="type-conversion-of-parameter-values"></a>Typ konvertering av parameter värden

När du anger strängar som argument för parametrar som förväntar sig en annan typ, konverterar PowerShell implicit strängarna till parameter måltypen.
Avancerade funktioner utför konstruktor-invariant-parsning av parameter värden.

En kultur känslig konvertering utförs däremot under parameter bindning för kompilerade cmdlets.

I det här exemplet skapar vi en cmdlet och en skript funktion som tar en `[datetime]` parameter. Den aktuella kulturen ändras till att använda tyska inställningar.
Ett tyskt formaterat datum skickas till parametern.

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

Som du ser ovan använder cmdlet: en kultur känslig parsning för att konvertera strängen.

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

Avancerade funktioner använder kulturen-invariant-parsning, vilket resulterar i följande fel.

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a>Statiska parametrar

Statiska parametrar är parametrar som alltid är tillgängliga i funktionen.
De flesta parametrar i PowerShell-cmdletar och skript är statiska parametrar.

I följande exempel visas en deklaration av en **computername** -parameter med följande egenskaper:

- Det är obligatoriskt (obligatoriskt).
- Det tar emot inmatade från pipelinen.
- Det tar en matris med strängar som inmatade.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>Attribut för parametrar

I det här avsnittet beskrivs de attribut som du kan lägga till i funktions parametrar.

Alla attribut är valfria. Men om du utelämnar attributet **CmdletBinding** , och sedan ska identifieras som en avancerad funktion, måste funktionen innehålla attributet- **parameter** .

Du kan lägga till ett eller flera attribut i varje parameter deklaration. Det finns ingen gräns för antalet attribut som du kan lägga till i en parameter deklaration.

### <a name="parameter-attribute"></a>Parameter-attribut

Attributet **parameter** används för att deklarera attributen för funktions parametrar.

Attributet **parameter** är valfritt och du kan utelämna det om ingen av parametrarna för dina funktioner behöver attribut. Men för att kunna identifieras som en avancerad funktion, i stället för en enkel funktion, måste en funktion ha antingen attributet **CmdletBinding** eller attributet **parameter** eller båda.

Attributet **parameter** innehåller argument som definierar parameterns egenskaper, till exempel om parametern är obligatorisk eller valfri.

Använd följande syntax för att deklarera **parameter** -attributet, ett argument och ett argument värde. De parenteser som omger argumentet och dess värde måste följa **parametern** utan något mellanliggande blank steg.

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

Använd kommatecken för att avgränsa argument inom parentes. Använd följande syntax för att deklarera två argument för attributet **parameter** .

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

De booleska argument typerna för **parametern** attribut är **false** när de utelämnas från attributet **parameter** . Ange värdet för argumentet till `$true` eller bara lista argumentet efter namn. Följande **parameter** -attribut är till exempel likvärdiga.

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

Om du använder **parameter** -attributet utan argument, som ett alternativ till att använda attributet **CmdletBinding** , krävs fortfarande de parenteser som följer attributnamnet.

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>Obligatoriskt argument

`Mandatory`Argumentet anger att parametern är obligatorisk. Om det här argumentet inte anges är parametern valfri.

I följande exempel deklareras parametern **computername** . `Mandatory`Argumentet används för att göra parametern obligatorisk.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Positions argument

`Position`Argumentet avgör om parameter namnet krävs när parametern används i ett kommando. När en parameter deklaration innehåller `Position` argumentet, kan parameter namnet utelämnas och PowerShell identifierar det namnlösa parametervärdet med dess position, eller ordning, i listan över namnlösa parameter värden i kommandot.

Om `Position` argumentet inte anges måste parameter namnet eller ett alias eller en förkortning för parameter namn föregå parametervärdet när parametern används i ett kommando.

Som standard är alla funktions parametrar placerade i position. PowerShell tilldelar positions nummer till parametrar i den ordning som parametrarna deklareras i funktionen. Om du vill inaktivera den här funktionen ställer du in värdet för `PositionalBinding` argumentet för attributet **CmdletBinding** till `$False` . `Position`Argumentet prioriteras över värdet för `PositionalBinding` argumentet för attributet **CmdletBinding** . Mer information finns `PositionalBinding` i i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).

Värdet för `Position` argumentet anges som ett heltal. Position svärdet **0** representerar den första positionen i kommandot, ett positions värde på **1** representerar den andra positionen i kommandot och så vidare.

Om en funktion inte har några positions parametrar tilldelar PowerShell positioner till varje parameter baserat på i vilken ordning parametrarna deklareras.
Vi rekommenderar dock inte att du använder den här tilldelningen. Använd argumentet om du vill att parametrar ska placeras i position `Position` .

I följande exempel deklareras parametern **computername** . `Position`Argumentet använder argumentet med värdet **0**. Det innebär att när `-ComputerName` har utelämnats från kommandot måste dess värde vara det första eller det enda parameter värde som inte är namn i kommandot.

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>ParameterSetName-argument

`ParameterSetName`Argumentet anger den parameter som en parameter tillhör. Om ingen parameter uppsättning anges, tillhör parametern alla parameter uppsättningar som definieras av funktionen. För att vara unik måste därför varje parameter uppsättning ha minst en parameter som inte är medlem i någon annan parameter uppsättning.

> [!NOTE]
> För en cmdlet eller funktion finns det en gräns på 32 parameter uppsättningar.

I följande exempel deklareras en **computername** -parameter i `Computer` parameter uppsättningen, en **username** -parameter i `User` parameter uppsättningen och en **sammanfattnings** parameter i båda parameter uppsättningarna.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

Du kan bara ange ett `ParameterSetName` värde i varje argument och bara ett `ParameterSetName` argument i varje **parameter** -attribut. Om du vill ange att en parameter visas i mer än en parameter uppsättning lägger du till ytterligare **parameter** -attribut.

I följande exempel lägger du uttryckligen till **sammanfattnings** parametern `Computer` i `User` parameter uppsättningarna och. **Sammanfattnings** parametern är valfri i `Computer` parameter uppsättningen och obligatorisk i `User` parameter uppsättningen.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

Mer information om parameter uppsättningar finns i [About parameter set](about_parameter_sets.md).

#### <a name="valuefrompipeline-argument"></a>ValueFromPipeline-argument

`ValueFromPipeline`Argumentet anger att parametern accepterar inmatade objekt från ett pipeline-objekt. Ange det här argumentet om funktionen accepterar hela objektet, inte bara en egenskap för objektet.

I följande exempel deklareras en **computername** -parameter som är obligatorisk och accepterar ett objekt som skickas till funktionen från pipelinen.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>ValueFromPipelineByPropertyName-argument

`ValueFromPipelineByPropertyName`Argumentet anger att parametern accepterar inmatade objekt från en egenskap i ett pipeline-objekt. Objekt egenskapen måste ha samma namn eller alias som parametern.

Om funktionen till exempel har en **computername** -parameter och skickas-objektet har egenskapen **computername** , tilldelas värdet för egenskapen **computername** till funktionens **computername** -parameter.

I följande exempel deklareras en **computername** -parameter som är obligatorisk och accepterar indatamängden från objektets **computername** -egenskap som skickas till funktionen via pipelinen.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken _Delay-bind_ i parametern.
>
> Skript blocket _Delay-bind_ körs automatiskt under **ParameterBinding**. Resultatet är kopplat till parametern. Fördröjd bindning fungerar inte för parametrar som definierats som typ `ScriptBlock` eller `System.Object` . Skript blocket skickas genom _utan_ att anropas.
>
> Du kan läsa mer om _fördröjning – binda_ skript block här [about_Script_Blocks. MD](about_Script_Blocks.md).

#### <a name="valuefromremainingarguments-argument"></a>ValueFromRemainingArguments-argument

`ValueFromRemainingArguments`Argumentet anger att parametern accepterar alla parameter värden i kommandot som inte har tilldelats andra parametrar för funktionen.

I följande exempel deklareras en **värde** parameter som är obligatorisk och en **återstående** parameter som accepterar alla återstående parameter värden som skickas till funktionen.

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> Före PowerShell 6,2 anslöts **ValueFromRemainingArguments** -samlingen som en enskild enhet under index **0**.

#### <a name="helpmessage-argument"></a>HelpMessage-argument

`HelpMessage`Argumentet anger en sträng som innehåller en kort beskrivning av parametern eller dess värde. PowerShell visar det här meddelandet i den prompt som visas när ett nödvändigt parameter värde saknas i ett kommando. Det här argumentet har ingen påverkan på valfria parametrar.

I följande exempel deklareras en obligatorisk **computername** -parameter och ett hjälp meddelande som förklarar det förväntade parametervärdet.

Om det inte finns någon annan [kommenterings-baserad hjälpfil](./about_comment_based_help.md) för funktionen (till exempel `.SYNOPSIS` ) visas även det här meddelandet i `Get-Help` utdata.

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Alias-attribut

Attributet **alias** upprättar ett alternativt namn för parametern.
Det finns ingen gräns för antalet alias som du kan tilldela till en parameter.

I följande exempel visas en parameter deklaration som lägger till **CN** -och **MachineName** -alias till den obligatoriska **computername** -parametern.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>SupportsWildcards-attribut

Attributet **SupportsWildcards** används för att indikera att parametern accepterar jokertecken. I följande exempel visas en parameter deklaration för en obligatorisk **Sök vägs** parameter som stöder jokertecken.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

Om du använder det här attributet aktive ras inte stöd för jokertecken automatiskt. Cmdlet-utvecklaren måste implementera koden för att hantera jokertecken. Vilka jokertecken som stöds kan variera beroende på underliggande API eller PowerShell-Provider. Mer information finns i [about_Wildcards](about_Wildcards.md).

### <a name="parameter-and-variable-validation-attributes"></a>Attribut för parameter-och variabel verifiering

Validera attribut Direct PowerShell för att testa de parameter värden som användarna skickar när de anropar funktionen Advanced. Om parameter värden inte fungerar som testet, genereras ett fel och funktionen anropas inte. Parameter verifiering tillämpas endast på angivna indata och andra värden som standardvärden är inte verifierade.

Du kan också använda verifierings-attributen för att begränsa de värden som användarna kan ange för variabler. När du använder en typ konverterare tillsammans med ett verifierings attribut måste typ konverteraren definieras före-attributet.

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>AllowNull-verifierings attribut

Attributet **AllowNull** tillåter att värdet för en obligatorisk parameter ska vara `$null` . I följande exempel deklareras en hash- **ComputerInfo** -parameter som kan ha ett **Null** -värde.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> Attributet **AllowNull** fungerar inte om typ konverteraren är inställd på sträng eftersom sträng typen inte accepterar ett null-värde. Du kan använda attributet **AllowEmptyString** för det här scenariot.

### <a name="allowemptystring-validation-attribute"></a>AllowEmptyString-verifierings attribut

Attributet **AllowEmptyString** tillåter att värdet för en obligatorisk parameter är en tom sträng ( `""` ). I följande exempel deklareras en **computername** -parameter som kan ha ett tomt sträng värde.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>AllowEmptyCollection-verifierings attribut

Attributet **AllowEmptyCollection** tillåter att värdet för en obligatorisk parameter är en tom samling `@()` . I följande exempel deklareras en **computername** -parameter som kan ha ett tomt samlings värde.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>ValidateCount-verifierings attribut

Attributet **ValidateCount** anger det lägsta och högsta antalet parameter värden som en parameter accepterar. PowerShell genererar ett fel om antalet parameter värden i kommandot som anropar funktionen ligger utanför intervallet.

Följande parameter deklaration skapar en **computername** -parameter som tar en till fem parameter värden.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>ValidateLength-verifierings attribut

Attributet **ValidateLength** anger det lägsta och högsta antalet tecken i en parameter eller ett variabel värde. PowerShell genererar ett fel om längden på ett värde som har angetts för en parameter eller en variabel ligger utanför intervallet.

I följande exempel måste varje dator namn ha ett till tio tecken.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

I följande exempel måste värdet för variabeln `$number` vara minst ett tecken långt och högst tio tecken.

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> I det här exemplet är värdet för `01` inkapslat i enkla citat tecken. **ValidateLength** -attributet accepterar inte ett tal utan att de omges av citat tecken.

### <a name="validatepattern-validation-attribute"></a>ValidatePattern-verifierings attribut

Attributet **ValidatePattern** anger ett reguljärt uttryck som jämförs med parametern eller variabeln värde. PowerShell genererar ett fel om värdet inte matchar mönstret för reguljära uttryck.

I följande exempel måste parametervärdet innehålla ett fyrsiffrigt tal och varje siffra måste vara ett tal mellan noll och nio.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

I följande exempel måste värdet för variabeln `$number` vara exakt ett fyrsiffrigt tal och varje siffra måste vara ett tal från noll till nio.

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>ValidateRange-verifierings attribut

Attributet **ValidateRange** anger ett numeriskt intervall eller ett **ValidateRangeKind** Enum-värde för varje parameter eller variabel värde.
PowerShell genererar ett fel om ett värde ligger utanför intervallet.

**ValidateRangeKind** -uppräkningen tillåter följande värden:

- **Positivt** – ett tal som är större än noll.
- **Negativt** – ett tal som är mindre än noll.
- Ej **positivt** -ett tal som är mindre än eller lika med noll.
- Icke- **negativt** – ett tal som är större än eller lika med noll.

I följande exempel måste värdet **för parametern** Parameters vara mellan noll och tio.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

I följande exempel måste värdet för variabeln `$number` vara mellan noll och tio.

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

I följande exempel måste värdet för variabeln `$number` vara större än noll.

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>ValidateScript-verifierings attribut

Attributet **ValidateScript** anger ett skript som används för att validera en parameter eller ett variabel värde. PowerShell rör värdet i skriptet och genererar ett fel om skriptet returnerar `$false` eller om skriptet genererar ett undantag.

När du använder attributet **ValidateScript** mappas värdet som verifieras till `$_` variabeln. Du kan använda `$_` variabeln för att referera till värdet i skriptet.

I följande exempel måste värdet för parametern **EventDate** vara större än eller lika med det aktuella datumet.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

I följande exempel måste värdet för variabeln `$date` vara större än eller lika med aktuellt datum och tid.

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> Om du använder **ValidateScript** kan du inte skicka ett `$null` värde till parametern. När du skickar ett null-värde kan **ValidateScript** inte validera argumentet.

### <a name="validateset-attribute"></a>ValidateSet-attribut

Attributet **ValidateSet** anger en uppsättning giltiga värden för en parameter eller en variabel och möjliggör slut för ande av tabbar. PowerShell genererar ett fel om en parameter eller ett variabel värde inte matchar ett värde i mängden. I följande exempel kan värdet för **detalj** parametern endast vara låg, genomsnitt eller hög.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

I följande exempel måste värdet för variabeln `$flavor` vara choklad, Strawberry eller vanilj.

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

Verifieringen sker när variabeln tilldelas även inom skriptet. Följande resulterar exempelvis i ett fel vid körning:

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>Dynamiska validateSet-värden

Du kan använda en **klass** för att dynamiskt generera värden för **ValidateSet** vid körning. I följande exempel genereras giltiga värden för variabeln `$Sound` via en **klass** med namnet **SoundNames** som kontrollerar tre fil Systems sökvägar för tillgängliga ljudfiler:

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

`[SoundNames]`Klassen implementeras sedan som ett dynamiskt **ValidateSet** -värde enligt följande:

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a>ValidateNotNull-verifierings attribut

Attributet **ValidateNotNull** anger att parametervärdet får inte vara `$null` . PowerShell genererar ett fel om parametervärdet är `$null` .

Attributet **ValidateNotNull** är utformat för användning när parametern är valfri och typen är odefinierad eller har en typ konverterare som inte kan implicit konvertera ett null-värde som- **objekt**. Om du anger en typ som implicit ska konvertera ett null-värde, till exempel en **sträng** , konverteras värdet null till en tom sträng även när du använder attributet **ValidateNotNull** . För det här scenariot använder du **ValidateNotNullOrEmpty**

I följande exempel kan värdet för **ID-** parametern inte vara `$null` .

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>ValidateNotNullOrEmpty-verifierings attribut

Attributet **ValidateNotNullOrEmpty** anger att parametervärdet får inte vara `$null` en tom sträng ( `""` ). PowerShell genererar ett fel om parametern används i ett funktions anrop, men dess värde är `$null` en tom sträng ( `""` ) eller en tom matris `@()` .

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>ValidateDrive-verifierings attribut

Attributet **ValidateDrive** anger att parametervärdet måste representera sökvägen, som bara refererar till tillåtna enheter. PowerShell genererar ett fel om parametervärdet refererar till andra enheter än vad som tillåts. Förekomsten av sökvägen, förutom själva enheten, är inte verifierad.

Om du använder en relativ sökväg måste den aktuella enheten finnas i listan över tillåtna enheter.

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>ValidateUserDrive-verifierings attribut

Attributet **ValidateUserDrive** anger att parametervärdet måste representera sökvägen som refererar till `User` enheten. PowerShell genererar ett fel om sökvägen refererar till en annan enhet. Verifierings attributet testar bara för att det finns en enhets del av sökvägen.

Om du använder relativ sökväg måste den aktuella enheten vara `User` .

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

Du kan definiera `User` enhet i Jea-sessionsinställningar (bara för administration). I det här exemplet skapar vi användaren: enhet.

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a>ValidateTrustedData-verifierings attribut

Det här attributet lades till i PowerShell-startattributet.

För tillfället används attributet internt av PowerShell och är inte avsett för extern användning.

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är parametrar för en cmdlet, funktion eller ett skript som endast är tillgängliga under vissa förhållanden.

Till exempel har flera Provider-cmdlets parametrar som endast är tillgängliga när cmdleten används i leverantörs enheten, eller i en viss sökväg för providerns enhet. Till exempel är **encoding** -parametern endast tillgänglig på `Add-Content` `Get-Content` cmdletarna, och `Set-Content` när den används i en fil system enhet.

Du kan också skapa en parameter som bara visas när en annan parameter används i funktions kommandot eller när en annan parameter har ett visst värde.

Dynamiska parametrar kan vara användbara, men Använd dem bara när det behövs, eftersom det kan vara svårt för användarna att identifiera sig. Om du vill hitta en dynamisk parameter måste användaren finnas i providerns sökväg, använda parametern **argument List** i `Get-Command` cmdleten eller använda parametern **Path** i `Get-Help` .

Om du vill skapa en dynamisk parameter för en funktion eller ett skript använder du `DynamicParam` nyckelordet.

Syntaxen ser ut så här:

`DynamicParam {<statement-list>}`

Använd en instruktion i instruktions listan `If` för att ange de villkor under vilka parametern är tillgänglig i funktionen.

Använd `New-Object` cmdleten för att skapa ett **system. Management. Automation. RuntimeDefinedParameter** -objekt för att representera parametern och ange dess namn.

Du kan använda ett `New-Object` kommando för att skapa ett **system. Management. Automation. ParameterAttribute** -objekt som representerar attribut för parametern, till exempel **obligatorisk** , **position** eller **ValueFromPipeline** eller dess parameter uppsättning.

I följande exempel visas en exempel funktion med standard parametrar med namnet **Name** och **Path** , och en valfri dynamisk parameter med namnet **DP1**. Parametern **DP1** är i `PSet1` parameter uppsättningen och har en typ av `Int32` .
Parametern **DP1** är endast tillgänglig i `Get-Sample` funktionen när värdet för **Sök vägs** parametern börjar med `HKLM:` , vilket anger att den används i `HKEY_LOCAL_MACHINE` register enheten.

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

Mer information finns i [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).

## <a name="switch-parameters"></a>Växla parametrar

Växlings parametrar är parametrar utan parameter värde. De är bara effektiva när de används och har bara en effekt.

Till exempel är parametern **noprofile** i **powershell.exe** en switch-parameter.

Om du vill skapa en växel parameter i en funktion anger du `Switch` typen i parameter definitionen.

Ett exempel:

```powershell
Param([Switch]<ParameterName>)
```

Eller så kan du använda en annan metod:

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

Växlings parametrar är enkla att använda och föredras över booleska parametrar som har en mer svår syntax.

Om du till exempel vill använda en växlings parameter skriver användaren parametern i kommandot.

`-IncludeAll`

Om du vill använda en boolesk parameter skriver användaren parametern och ett booleskt värde.

`-IncludeAll:$true`

När du skapar växlings parametrar väljer du parameter namnet noggrant. Se till att parameter namnet meddelar användaren om parameterns resultat.
Undvik tvetydiga termer, till exempel **filter** eller **maximum** som kan innebära att ett värde krävs.

## <a name="argumentcompleter-attribute"></a>ArgumentCompleter-attribut

Med attributet **ArgumentCompleter** kan du lägga till TABB-slutförande-värden till en speciell parameter. Ett **ArgumentCompleter** -attribut måste definieras för varje parameter som kräver TABB-slutförande. Precis som med **DynamicParameters** beräknas de tillgängliga värdena vid körning när användaren trycker på <kbd>TABB</kbd> efter parameter namnet.

Om du vill lägga till ett **ArgumentCompleter** -attribut måste du definiera ett skript block som bestämmer värdena. Skript blocket måste ha följande parametrar i den ordning som anges nedan. Parameterns namn spelar ingen roll när värdena anges i position.

Syntaxen ser ut så här:

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a>ArgumentCompleter-skript block

Skript block parametrarna har angetts till följande värden:

- `$commandName` (Position 0) – den här parametern anges till namnet på det kommando som skript blocket tillhandahåller för att slutföra tabben.
- `$parameterName` (Position 1) – den här parametern har angetts till den parameter vars värde kräver att tabbtangenten slutförs.
- `$wordToComplete` (Position 2) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.
- `$commandAst` (Position 3) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden. Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).
- `$fakeBoundParameters` (Position 4) – den här parametern anges till en hash-text som innehåller `$PSBoundParameters` för cmdleten innan användaren tryckte på <kbd>fliken</kbd>. Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).

**ArgumentCompleter** -skript blocket måste avregistrera värdena med hjälp av pipelinen, till exempel, `ForEach-Object` `Where-Object` eller någon annan lämplig metod.
Om du returnerar en matris med värden kan PowerShell behandla hela matrisen som **ett** värde för sista tabb.

I följande exempel läggs TABB-slutförande till **Value** -parametern. Om bara **värde** parametern anges visas alla möjliga värden eller argument för **värdet** . När **typ** parametern anges visar **värde** parametern bara möjliga värden för den typen.

Dessutom `-like` säkerställer operatorn att om användaren skriver följande kommando och använder <kbd>TABB</kbd> -slutförande, returneras bara **Apple** .

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
