---
description: Beskriver hur du använder objekt egenskaper i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: d4d3cd93e6b177e80d85315f125c647219fc4a45
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272552"
---
# <a name="about-properties"></a>Om egenskaper

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du använder objekt egenskaper i PowerShell.

## <a name="long-description"></a>Lång beskrivning

PowerShell använder strukturerade samlingar med information som kallas objekt för att representera objekten i data lager eller datorns tillstånd. Normalt arbetar du med objekt som ingår i Microsoft .NET Framework, men du kan också skapa anpassade objekt i PowerShell.

Associationen mellan ett objekt och dess objekt är mycket nära. När du ändrar ett objekt ändrar du vanligt vis objektet som det representerar. Om du till exempel får en fil i PowerShell får du inte den faktiska filen. I stället får du ett FileInfo-objekt som representerar filen. När du ändrar FileInfo-objektet ändras filen också.

De flesta objekt har egenskaper. Egenskaper är de data som är associerade med ett objekt. Olika typer av objekt har olika egenskaper. Ett FileInfo-objekt som representerar en fil har till exempel en **IsReadOnly** -egenskap som innehåller $True om filen är skrivskyddad och $false om den inte gör det.
Ett DirectoryInfo-objekt som representerar en fil system katalog har en överordnad egenskap som innehåller sökvägen till den överordnade katalogen.

### <a name="object-properties"></a>Objekt egenskaper

Använd cmdleten för att hämta egenskaperna för ett objekt `Get-Member` . Om du till exempel vill hämta egenskaperna för ett **fileinfo** -objekt använder du `Get-ChildItem` cmdleten för att hämta fileinfo-objektet som representerar en fil. Använd sedan en pipeline-operatör (&#124;) för att skicka **fileinfo** -objektet till `Get-Member` . Följande kommando hämtar PowerShell.exe-filen och skickar den till `Get-Member` .
Den \$ automatiska variabeln Pshome innehåller sökvägen till PowerShell-katalogen för installationen.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

Kommandots utdata visar medlemmar i **fileinfo** -objektet.
Medlemmarna inkluderar både egenskaper och metoder. När du arbetar i PowerShell har du åtkomst till alla medlemmar i objekten.

Om du bara vill hämta egenskaperna för ett objekt och inte metoderna använder du parametern MemberType i `Get-Member` cmdleten med värdet "Property", som du ser i följande exempel.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

När du har hittat egenskaperna kan du använda dem i PowerShell-kommandon.

## <a name="property-values"></a>Egenskaps värden

Även om varje objekt av en viss typ har samma egenskaper, beskriver värdena för dessa egenskaper det specifika objektet. Till exempel har varje FileInfo-objekt en CreationTime-egenskap, men värdet för egenskapen skiljer sig åt för varje fil.

Det vanligaste sättet att hämta värdena i egenskaperna för ett objekt är att använda punkt-metoden. Skriv en referens till objektet, till exempel en variabel som innehåller objektet, eller ett kommando som hämtar objektet. Skriv sedan en punkt (.) följt av egenskaps namnet.

Till exempel visar följande kommando värdet för egenskapen CreationTime i PowerShell.exe-filen. `Get-ChildItem`Kommandot returnerar ett fileinfo-objekt som representerar PowerShell.exes filen. Kommandot omges av parenteser för att kontrol lera att det körs innan det går att komma åt egenskaperna. `Get-ChildItem`Kommandot följs av en punkt och namnet på egenskapen CreationTime, enligt följande:

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

Du kan också spara ett objekt i en variabel och sedan hämta dess egenskaper med hjälp av punkt metoden, som du ser i följande exempel:

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

Du kan också använda `Select-Object` `Format-List` cmdletarna och för att Visa egenskaps värden för ett objekt. `Select-Object` och `Format-List` var och en har en **egenskaps** parameter. Du kan använda **egenskaps** parametern för att ange en eller flera egenskaper och deras värden. Eller så kan du använda jokertecknet ( \* ) för att representera alla egenskaper.

Följande kommando visar till exempel värdena för alla egenskaper för PowerShell.exe-filen.

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a>Statiska egenskaper

Du kan använda statiska egenskaper för .NET-klasser i PowerShell. Statiska egenskaper är egenskaper för klass, till skillnad från standard egenskaper, som är egenskaper för ett objekt.

Om du vill hämta statiska egenskaper för en klass använder du den statiska parametern i Get-Member-cmdleten.

Följande kommando hämtar till exempel `System.DateTime` klassens statiska egenskaper.

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

Använd följande syntax för att hämta värdet för en statisk egenskap.

```
[<ClassName>]::<Property>
```

Till exempel hämtar följande kommando värdet för klassens statiska egenskap UtcNow `System.DateTime` .

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a>Egenskaper för skalära objekt och samlingar

Egenskaperna för ett ("skalär") objekt av en viss typ skiljer sig ofta från egenskaperna för en samling objekt av samma typ.
Varje tjänst har till exempel egenskapen **DisplayName** , men en samling tjänster har inte egenskapen **DisplayName** .

Följande kommando hämtar värdet för egenskapen **DisplayName** för tjänsten "audiosrv".

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

Från och med PowerShell 3,0 försöker PowerShell förhindra skript fel som orsakas av de olika egenskaperna för skalära objekt och samlingar. Samma kommando returnerar värdet för egenskapen **DisplayName** för varje tjänst som `Get-Service` returneras.

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

När du skickar en samling, men begär en egenskap som bara finns på enstaka ("skalära") objekt, returnerar PowerShell värdet för den egenskapen för varje objekt i samlingen.

Alla samlingar har en **Count** -egenskap som returnerar hur många objekt som finns i samlingen.

```powershell
(Get-Service).Count
```

```output
176
```

Från och med PowerShell 3,0 returnerar PowerShell rätt värde om du begär egenskapen Count eller length för noll objekt eller ett objekt.

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

Om det finns en egenskap för de enskilda objekten och i samlingen returneras bara samlingens egenskap.

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

Den här funktionen fungerar också med metoder för skalära objekt och samlingar. Mer information finns i [about_Methods](about_methods.md).

## <a name="see-also"></a>Se även

[about_Methods](about_Methods.md)

[about_Objects](about_Objects.md)

[Hämta medlem](xref:Microsoft.PowerShell.Utility.Get-Member)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

