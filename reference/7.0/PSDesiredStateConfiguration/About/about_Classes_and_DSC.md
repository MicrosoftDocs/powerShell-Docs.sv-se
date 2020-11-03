---
description: Beskriver hur du kan använda klasser för att utveckla i PowerShell med önskad tillstånds konfiguration (DSC).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: 272d6872d096de864044ae41449caff472bb1799
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271316"
---
# <a name="about-classes-and-desired-state-configuration"></a>Om klasser och önskad tillstånds konfiguration

## <a name="short-description"></a>Kort beskrivning

Beskriver hur du kan använda klasser för att utveckla i PowerShell med önskad tillstånds konfiguration (DSC).

## <a name="long-description"></a>Lång beskrivning

Från och med Windows PowerShell 5,0 lades språk till för att definiera klasser och andra användardefinierade typer med hjälp av formell syntax och semantik som liknar andra objektorienterade programmeringsspråk. Målet är att göra det möjligt för utvecklare och IT-proffs att använda PowerShell för ett bredare utbud av användnings fall, förenkla utvecklingen av PowerShell-artefakter som DSC-resurser och påskynda täckning av hanterings ytor.

## <a name="supported-scenarios"></a>Scenarier som stöds

Följande scenarier stöds:

- Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket.
- Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterade programmerings konstruktioner, till exempel klasser, egenskaper, metoder och arv.
- Fel söknings typer med hjälp av PowerShell-språket.
- Generera och hantera undantag med hjälp av formella mekanismer och på rätt nivå.

## <a name="define-dsc-resources-with-classes"></a>Definiera DSC-resurser med klasser

Utöver ändringar i syntaxen är de större skillnaderna mellan en klass definierad DSC-resurs och en cmdlet DSC-resurs leverantör följande objekt:

- Det krävs ingen MOF-fil (Management Object Format).
- En Dscresource Keyword Supports-undermapp i mappen module krävs inte.
- En PowerShell-modul kan innehålla flera DSC-resurs klasser.

## <a name="create-a-class-defined-dsc-resource-provider"></a>Skapa en klass definierad DSC-resurs leverantör

Följande exempel är en klass-definierad DSC-resurs-Provider som sparas som en modul, MyDSCResource. psm1. Du måste alltid ta med en nyckel egenskap i en klass definierad DSC-resurs leverantör.

```powershell
enum Ensure
{
    Absent
    Present
}

<#
    This resource manages the file in a specific path.
    [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
        This property is the fully qualified path to the file that is
        expected to be present or absent.

        The [DscProperty(Key)] attribute indicates the property is a
        key and its value uniquely identifies a resource instance.
        Defining this attribute also means the property is required
        and DSC will ensure a value is set before calling the resource.

        A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
        This property defines the fully qualified path to a file that will
        be placed on the system if $Ensure = Present and $Path does not
        exist.

        NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
        This property reports the file's create timestamp.

        [DscProperty(NotConfigurable)] attribute indicates the property is
        not configurable in DSC configuration.  Properties marked this way
        are populated by the Get() method to report additional details
        about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
{
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }
        return $this
    }

    <#
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }
        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
# This module defines a class for a DSC "FileResource" provider.

enum Ensure
{
    Absent
    Present
}

<# This resource manages the file in a specific path.
[DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource{

    <# This is a key property
        [DscResourceKey()] also means the property is required.
        It is guaranteed to be set, other properties may not
        be set if the configuration did not specify values.
    #>
    [DscResourceKey()]
    [string]$Path

    <#
        [DscResourceMandatory()] means the property is required.
        It is guaranteed to be set, other properties may not be set
        if the configuration did not specify values.
    #>
    [DscResourceMandatory()]
    [Ensure] $Ensure

    <#
        [DscResourceMandatory()] means the property is required.
    #>
    [DscResourceMandatory()]
    [string] $SourcePath

    [DscResource

    <#
        This method replaces the Set-TargetResource DSC script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = Test-Path -path $this.Path -PathType Leaf
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $this.Path"
                Remove-Item -LiteralPath $this.Path
            }
        }
    }

    <#

        This method replaces the Test-TargetResource function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>

    [bool] Test()
    {
        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path."
        }

        $fileExists = Test-Path -path $this.Path -PathType Leaf

        if($this.ensure -eq [Ensure]::Present)
        {
            return $fileExists
        }

        return (-not $fileExists)
    }

    <#
        This method replaces the Get-TargetResource function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>

    [FileResource] Get()
    {
        $file = Get-item $this.Path
        return $this
    }

    <#
        Helper method to copy file from source to path.
        Because this resource provider run under system,
        Only the Administrators and system have full
        access to the new created directory and file
    #>
    CopyFile()
    {
        if(Test-Path -path $this.SourcePath -PathType Container)
        {
            throw "SourcePath '$this.SourcePath' is a directory path"
        }

        if( -not (Test-Path -path $this.SourcePath -PathType Leaf))
        {
            throw "SourcePath '$this.SourcePath' is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid lines
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -path $this.Path -PathType Container)
        {
            throw "Path '$this.Path' is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a>Skapa ett modul manifest

När du har skapat den Class-definierade DSC-adressresursen och sparat den som en modul, skapar du ett modul manifest för modulen. Om du vill göra en klass baserad resurs tillgänglig för DSC-motorn måste du inkludera en `DscResourcesToExport` instruktion i manifest filen som instruerar modulen att exportera resursen. I det här exemplet sparas följande modul-manifest som MyDscResource.psd1.

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a>Distribuera en DSC-resurs-Provider

Distribuera den nya DSC-resurs leverantören genom att skapa en MyDscResource-mapp i `$pshome\Modules` eller `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .

Du behöver inte skapa en undermapp för Dscresource Keyword Supports. Kopiera modul-och modul manifest-filerna (MyDscResource. psm1 och MyDscResource.psd1) till mappen MyDscResource.

Nu skapar du och kör ett konfigurations skript som du skulle ha med valfri DSC-resurs.

## <a name="create-a-dsc-configuration-script"></a>Skapa ett DSC-konfigurationsskript

När du har sparat klass-och manifest filerna i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen. Följande konfiguration refererar till MyDSCResource-modulen. Spara konfigurationen som ett skript MyResource.ps1.

Information om hur du kör en DSC-konfiguration finns i [Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers).

Innan du kör konfigurationen skapar du `C:\test.txt` . Konfigurationen kontrollerar om filen finns på `c:\test\test.txt` . Om filen inte finns kopierar konfigurationen filen från `C:\test.txt` .

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

Kör det här skriptet som valfritt DSC-konfigurations skript. Starta konfigurationen genom att köra följande i en upphöjd PowerShell-konsol:

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a>Arv i PowerShell-klasser

### <a name="declare-base-classes-for-powershell-classes"></a>Deklarera bas klasser för PowerShell-klasser

Du kan deklarera en PowerShell-klass som bastyp för en annan PowerShell-klass, som du ser i följande exempel där **frukten** är en bastyp för **Apple**.

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a>Deklarera implementerade gränssnitt för PowerShell-klasser

Du kan deklarera implementerade gränssnitt efter grund typer, eller omedelbart efter ett kolon ( `:` ) om det inte finns någon bastyp angiven. Avgränsa alla typnamn med kommatecken. Detta liknar C#-syntaxen.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a>Anropa Bask lass konstruktörer

Om du vill anropa en konstruktor för Bask Lassen från en underklass lägger du till `base` nyckelordet, som du ser i följande exempel:

```powershell
class A {
    [int]$a
    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

    [B]::new().a # return 103
```

Om en basklass har en standardkonstruktor (inga parametrar) kan du utelämna ett explicit konstruktor-anrop, som visas.

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a>Anropa Bask lass metoder

Du kan åsidosätta befintliga metoder i underklasser. För att göra åsidosättningen deklarerar du metoder med hjälp av samma namn och signatur.

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

För att anropa Bask lass metoder från åsidosatta implementeringar, omvandlas till Bask Lassen `([baseclass]$this)` för anrop.

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

Alla PowerShell-metoder är virtuella. Du kan dölja icke-virtuella .NET-metoder i en underklass med samma syntax som du gör för en åsidosättning: deklarera metoder med samma namn och signatur.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="current-limitations-with-class-inheritance"></a>Aktuella begränsningar med klass arv

En begränsning av klass arvet är att det inte finns någon syntax för att deklarera gränssnitt i PowerShell.

## <a name="defining-custom-types-in-powershell"></a>Definiera anpassade typer i PowerShell

Windows PowerShell 5,0 introducerade flera språk element.

### <a name="class-keyword"></a>Klass nyckelord

Definierar en ny klass.
`class`Nyckelordet är av typen true .NET Framework.
Klass medlemmar är offentliga.

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a>Räkna upp nyckelord och uppräkningar

Stöd för `enum` nyckelordet har lagts till och är en avbrytande ändring. `enum`Avgränsaren är för närvarande en ny rad. En lösning för de som redan använder `enum` är att infoga ett et-tecken ( `&` ) före ordet. Aktuella begränsningar: du kan inte definiera en uppräknare i själva fallet, men du kan initiera `enum` i villkor för en annan `enum` , som du ser i följande exempel:

Det går för närvarande inte att ange bastypen. Bastypen är alltid [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Ett uppräknings värde måste vara en konstant för en parse. Uppräkning svärdet kan inte anges till resultatet av ett anropat kommando.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

`Enum` stöder aritmetiska åtgärder, som du ser i följande exempel:

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a>Dolt nyckelord

`hidden`Nyckelordet, som introducerades i Windows PowerShell 5,0, döljer klass medlemmar från standard `Get-Member` resultat. Ange den dolda egenskapen som visas på följande rad:

```powershell
hidden [type] $classmember = <value>
```

Dolda medlemmar visas inte med hjälp av tabb-slutförande eller IntelliSense, om inte slut för ande sker i den klass som definierar den dolda medlemmen.

Ett nytt attribut, **system. Management. Automation. HiddenAttribute** , har lagts till, så att C#-koden kan ha samma semantik i PowerShell.

Mer information finns i [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` är nu ett faktiskt dynamiskt nyckelord. PowerShell parsar den angivna modulens rotdomän, söker efter klasser som innehåller attributet Dscresource Keyword Supports.

### <a name="properties"></a>Egenskaper

Ett nytt fält, `ImplementingAssembly` ,, har lagts till i `ModuleInfo` . Om skriptet definierar klasser eller om den inlästa sammansättningen för binära moduler `ImplementingAssembly` är inställd på den dynamiska sammansättning som skapats för en-modul. Den anges inte när ModuleType = manifestet har angetts.

Reflektion i `ImplementingAssembly` fältet identifierar resurser i en modul. Det innebär att du kan identifiera resurser som skrivits på antingen PowerShell eller andra hanterade språk.

Fält med initierare.

`[int] $i = 5`

Statisk stöds och fungerar som ett attribut, liknande typ begränsningar, så att det kan anges i valfri ordning.

`static [int] $count = 0`

En typ är valfri.

`$s = "hello"`

Alla medlemmar är offentliga. Egenskaperna kräver antingen en ny rad eller ett semikolon. Om ingen objekt typ anges är egenskaps typen **objekt**.

### <a name="constructors-and-instantiation"></a>Konstruktörer och instansiering

PowerShell-klasser kan ha konstruktorer som har samma namn som klassen. Konstruktörer kan vara överbelastade. Statiska konstruktorer stöds.
Egenskaper med initierings uttryck initieras innan all kod körs i en konstruktor. Statiska egenskaper initieras före bröd texten i en statisk konstruktor och instans egenskaper initieras före bröd texten i den icke-statiska konstruktorn. För närvarande finns det ingen syntax för att anropa en konstruktor från en annan konstruktor, till exempel C#-syntax: `": this()")` . Lösningen är att definiera en gemensam init-metod.

Följande är sätt att instansiera klasser:

- Instansieras med hjälp av Standardkonstruktorn. Observera att `New-Object` det inte finns stöd för i den här versionen.

  `$a = [MyClass]::new()`

- Anropar en konstruktor med en parameter.

  `$b = [MyClass]::new(42)`

- Skicka en matris till en konstruktor med flera parametrar

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

I den här versionen är typ namnet bara synligt i lexikalt, vilket innebär att det inte är synligt utanför modulen eller skriptet som definierar klassen. Funktioner kan returnera instanser av en klass som definierats i PowerShell och instanser fungerar bra utanför modulen eller skriptet.

Med den `Get-Member` **statiska** parametern visas konstruktörer, så att du kan visa överlagringar på samma sätt som andra metoder. Prestanda för den här syntaxen är också avsevärt snabbare än `New-Object` .

Den pseudo-statiska metoden med namnet **New** fungerar med .net-typer, som du ser i följande exempel. `[hashtable]::new()`

Du kan nu se överbelastningar i konstruktorn med `Get-Member` eller som visas i det här exemplet:

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a>Metoder

En PowerShell-klass metod implementeras som en **script block** som bara har ett slut block. Alla metoder är offentliga. Nedan visas ett exempel på hur du definierar en metod med namnet **doSomething**.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a>Metod anrop

Överlagrade metoder stöds. Överlagrade metoder har samma namn som en befintlig metod men åtskiljs av de angivna värdena.

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a>Anrop

Se [metod anrop](#method-invocation).

### <a name="attributes"></a>Attribut

Tre nya attribut har lagts till: `DscResource` , `DscResourceKey` och `DscResourceMandatory` .

### <a name="return-types"></a>Retur typer

Retur typen är ett kontrakt. Returvärdet konverteras till den förväntade typen.
Om ingen returtyp anges är retur typen Void. Det finns ingen strömning av objekt och objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.

### <a name="lexical-scoping-of-variables"></a>Lexikalt omfång av variabler

Nedan visas ett exempel på hur lexikalt scope fungerar i den här versionen.

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a>Exempel: skapa anpassade klasser

I följande exempel skapas flera nya, anpassade klasser för att implementera ett HTML-dynamiskt StyleSheet-språk (DSL). Exemplet lägger till hjälp funktioner för att skapa olika element typer som en del av klassen element, till exempel rubrik format och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
function HREF
{
    param (
        $Name,
        $Link
    )

    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
        [Parameter(Mandatory)]
        [object[]]
            $Data,
        [Parameter()]
        [string[]]
            $Properties = "*",
        [Parameter()]
        [hashtable]
            $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )

    $bodyText = ""
    # Add the header tags
    $bodyText +=  $Properties.foreach{TH $_}
    # Add the rows
    $bodyText += foreach ($row in $Data)
                {
                            TR (-join $Properties.Foreach{ TD ($row.$_) } )
                }

    $table = [Element] @{
                Tag = "Table"
                Attributes = $Attributes
                Text = $bodyText
            }
    $table
}
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a>Se även

[about_Enum](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Methods](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[Bygg anpassade PowerShell-resurser för Desired State Configuration](/powershell/scripting/dsc/resources/authoringResource)
