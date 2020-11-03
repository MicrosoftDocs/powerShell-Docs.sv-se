---
description: Beskriver hur du kan använda klasser för att skapa dina egna anpassade typer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 27950034806caf53b2cdbe50329709a8ab177aee
ms.sourcegitcommit: 16d62a98449e3ddaf8d7c65bc1848ede1fd8a3e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2020
ms.locfileid: "93269522"
---
# <a name="about-classes"></a>Om klasser

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du kan använda klasser för att skapa dina egna anpassade typer.

## <a name="long-description"></a>Lång beskrivning

PowerShell 5,0 lägger till en formell syntax för att definiera klasser och andra användardefinierade typer. Genom att lägga till klasser kan utvecklare och IT-proffs använda PowerShell för en större mängd användnings fall. Det fören klar utvecklingen av PowerShell-artefakter och påskyndar täckningen av hanterings ytor.

En klass deklaration är en skiss som används för att skapa instanser av objekt vid körning. När du definierar en klass är klass namnet namnet på typen. Om du till exempel deklarerar en klass med namnet **Device** och initierar en variabel `$dev` till en ny instans av **enhet** , `$dev` är ett objekt eller en instans av typen **enhet**. Varje instans av **enheten** kan ha olika värden i egenskaperna.

## <a name="supported-scenarios"></a>Scenarier som stöds

- Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterade programmerings semantik som klasser, egenskaper, metoder, arv osv.
- Fel söknings typer med PowerShell-språket.
- Generera och hantera undantag med hjälp av formella mekanismer.
- Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket.

## <a name="syntax"></a>Syntax

Klasser deklareras med hjälp av följande syntax:

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

Klasser instansieras med hjälp av någon av följande syntaxer:

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> När du använder `[<class-name>]::new()` syntaxen är hakparenteser runt klass namnet obligatoriska. Hakparenteserna signalerar en typ definition för PowerShell.

### <a name="example-syntax-and-usage"></a>Exempel på syntax och användning

I det här exemplet visas den minsta syntax som krävs för att skapa en användbar klass.

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a>Klass egenskaper

Egenskaper är variabler som deklareras i klass omfånget. En egenskap kan vara av valfri inbyggd typ eller instans av en annan klass. Klasser har ingen begränsning i antalet egenskaper som de har.

### <a name="example-class-with-simple-properties"></a>Exempel klass med enkla egenskaper

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a>Exempel på komplexa typer i klass egenskaper

I det här exemplet definieras en tom **rack** klass med hjälp av **enhets** klassen. I exemplen nedan visas hur du lägger till enheter i racket och hur du börjar med ett förinställt rack.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a>Klass metoder

Metoder definierar de åtgärder som en klass kan utföra. Metoder kan ta parametrar som tillhandahåller indata. Metoder kan returnera utdata. Data som returneras av en metod kan vara alla definierade data typer.

När du definierar en metod för en klass refererar du till det aktuella Class-objektet med hjälp av den `$this` automatiska variabeln. På så sätt kan du få åtkomst till egenskaper och andra metoder som definierats i den aktuella klassen.

### <a name="example-simple-class-with-properties-and-methods"></a>Exempel på en enkel klass med egenskaper och metoder

Utöka **rack** klassen för att lägga till och ta bort enheter i eller från den.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a>Utdata i klass metoder

Metoder bör ha en definierad returtyp. Om en metod inte returnerar utdata ska utdatatypen vara `[void]` .

I klass metoder skickas inga objekt till pipelinen förutom de som nämns i `return` instruktionen. Det finns inga oavsiktliga utdata till pipelinen från koden.

> [!NOTE]
> Detta är i grunden annorlunda än hur PowerShell-funktioner hanterar utdata, där allt går till pipelinen.

Icke-avslutande fel som skrivs till fel strömmen inifrån en klass metod skickas inte genom. Du måste använda `throw` för att visa ett avslutande fel meddelande.
Med hjälp av `Write-*` cmdletarna kan du fortfarande skriva till PowerShell: s utgående strömmar från en klass metod. Detta bör dock undvikas så att metoden avger objekt med endast `return` instruktionen.

### <a name="method-output"></a>Metodens utdata

Det här exemplet visar inga oavsiktliga utdata till pipelinen från klass metoder, förutom i `return` instruktionen.

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a>Konstruktor

Med konstruktorer kan du ange standardvärden och validera objekt logik när du skapar instansen av klassen. Konstruktörer har samma namn som klassen. Konstruktörer kan ha argument för att initiera data medlemmar för det nya objektet.

Klassen kan ha noll eller flera definierade konstruktorer. Om ingen konstruktor har definierats tilldelas klassen en standardkonstruktor utan parametrar. Den här konstruktorn initierar alla medlemmar till sina standardvärden. Objekt typer och strängar får null-värden. När du definierar konstruktorn skapas ingen standardkonstruktor utan parametrar. Skapa en parameter lös konstruktor om en sådan krävs.

### <a name="constructor-basic-syntax"></a>Grundläggande syntax för konstruktor

I det här exemplet definieras enhets klassen med egenskaper och en konstruktor.
Om du vill använda den här klassen måste användaren ange värden för parametrarna som anges i konstruktorn.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a>Exempel med flera konstruktorer

I det här exemplet definieras **enhets** klassen med egenskaper, en standardkonstruktor och en konstruktor för att initiera instansen.

Standardkonstruktorn anger **varumärket** **Odefinierad** och lämnar **modell** och **leverantörs-SKU** med null-värden.

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a>Dolt attribut

`hidden`Attributet döljer en egenskap eller metod. Egenskapen eller metoden är fortfarande tillgänglig för användaren och är tillgänglig i alla omfattningar där objektet är tillgängligt. Dolda medlemmar är dolda från `Get-Member` cmdleten och kan inte visas med hjälp av tabb-slutförande eller IntelliSense utanför klass definitionen.

Mer information finns i [About_hidden](About_hidden.md).

### <a name="example-using-hidden-attributes"></a>Exempel med dolda attribut

När ett **rack** objekt skapas, är antalet platser för enheter ett fast värde som inte ska ändras när som helst. Det här värdet är känt vid skapande tillfället.

Genom att använda attributet dold kan utvecklaren hålla antalet platser dolda och förhindra oavsiktliga ändringar av rackets storlek.

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

Egenskapen anslags **platser** visas inte i `$r1` utdata. Storleken ändrades dock av konstruktorn.

## <a name="static-attribute"></a>Statiskt attribut

`static`Attributet definierar en egenskap eller en metod som finns i klassen och behöver ingen instans.

En statisk egenskap är alltid tillgänglig, oberoende av klass instansiering. En statisk egenskap delas över alla instanser av klassen. En statisk metod är alltid tillgänglig. Alla statiska egenskaper som är aktiva för hela sessions intervallet.

### <a name="example-using-static-attributes-and-methods"></a>Exempel med statiska attribut och metoder

Anta att de rack som instansieras här finns i ditt data Center. Så du vill hålla koll på racken i din kod.

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a>Testning av statisk egenskap och metod finns

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

Observera att antalet rack ökar varje gången du kör det här exemplet.

## <a name="property-validation-attributes"></a>Attribut för egenskaps verifiering

Med verifierings attribut kan du testa att värden som ges till egenskaperna uppfyller definierade krav. Verifieringen utlöses så snart värdet tilldelas. Se [about_functions_advanced_parameters](about_functions_advanced_parameters.md).

### <a name="example-using-validation-attributes"></a>Exempel som använder verifierings-attribut

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a>Arv i PowerShell-klasser

Du kan utöka en klass genom att skapa en ny klass som härleds från en befintlig klass. Den härledda klassen ärver egenskaperna för Bask Lassen. Du kan lägga till eller åsidosätta metoder och egenskaper efter behov.

PowerShell stöder inte flera arv. Klasser kan inte ärva från mer än en klass. Du kan dock använda gränssnitt för detta ändamål.

Arv implementering definieras av `:` operatorn, vilket innebär att den här klassen utökas eller implementeras dessa gränssnitt. Den härledda klassen ska alltid ligga längst till vänster i klass deklarationen.

### <a name="example-using-simple-inheritance-syntax"></a>Exempel med enkel syntax för arv

Det här exemplet visar den enkla PowerShell-syntaxen för PowerShell-klass.

```powershell
Class Derived : Base {...}
```

Det här exemplet visar arv med en gränssnitts deklaration som kommer efter Bask Lassen.

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a>Exempel på enkelt arv i PowerShell-klasser

I det här exemplet är de **rack** -och **enhets** klasser som används i de föregående exemplen bättre definierade för: Undvik egenskaps repetitioner, bättre justera gemensamma egenskaper och återanvänd vanliga affärs logik.

De flesta objekt i data centret är företags till gångar, vilket är meningsfullt att börja spåra dem som till gångar. Enhets typer definieras av `DeviceType` uppräkningen, se [about_Enum](about_Enum.md) för information om uppräkningar.

I vårt exempel definierar vi bara `Rack` och `ComputeServer` , båda tilläggen i `Device` klassen.

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a>Anropa Bask lass konstruktorer

Om du vill anropa en konstruktor för basklass från en underordnad klass lägger du till `base` nyckelordet.

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a>Anropa Bask lass metoder

Om du vill åsidosätta befintliga metoder i underklasser deklarerar du metoder med samma namn och signatur.

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

För att anropa Bask lass metoder från åsidosatta implementeringar, omvandlas till Bask Lassen ([BaseClass] $this) vid anrop.

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a>Ärver från gränssnitt

PowerShell-klasser kan implementera ett gränssnitt med samma arvs-syntax som används för att utöka bas klasserna. Eftersom gränssnitt tillåter flera arv kan en PowerShell-klass som implementerar ett gränssnitt ärva från flera typer, genom att avgränsa typ namnen efter kolon ( `:` ) med kommatecken ( `,` ). En PowerShell-klass som implementerar ett gränssnitt måste implementera alla medlemmar i det gränssnittet. Att utelämna medlemmar i implementations gränssnittet orsakar ett parsningsfel i skriptet.

> [!NOTE]
> PowerShell stöder för närvarande inte att deklarera nya gränssnitt i PowerShell-skript.

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a>Importera klasser från en PowerShell-modul

`Import-Module` och `#requires` instruktionen importerar bara modulens funktioner, alias och variabler, som definieras av modulen. Klasser importeras inte. `using module`Instruktionen importerar de klasser som definierats i modulen. Om modulen inte har lästs in i den aktuella sessionen, `using` Miss lyckas instruktionen. Mer information om `using` instruktionen finns i [about_Using](about_Using.md).

## <a name="the-psreference-type-is-not-supported-with-class-members"></a>PSReference-typen stöds inte med klass medlemmar

Det `[ref]` går inte att använda typen-Cast med en klass medlem tyst. Det går inte att använda API: er som använder `[ref]` parametrar med klass medlemmar. **PSReference** har utformats för att stödja com-objekt. COM-objekt har fall där du behöver skicka ett värde i som referens.

Mer information om `[ref]` typen finns i PSReference- [klass](/dotnet/api/system.management.automation.psreference).

## <a name="see-also"></a>Se även

- [About_hidden](About_hidden.md)
- [about_Enum](about_Enum.md)
- [about_Language_Keywords](about_language_keywords.md)
- [about_Methods](about_methods.md)
- [about_Using](about_using.md)
