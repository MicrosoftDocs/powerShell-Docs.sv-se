---
description: Filsystem
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_filesystem_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: FileSystem-Provider
ms.openlocfilehash: 085d714fce8475dd3eeee656d1cd17db02e772a6
ms.sourcegitcommit: 7f712e12ec5b3f3f3e695da804b050ea0ce58b3a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94661400"
---
# <a name="filesystem-provider"></a>FileSystem-Provider

## <a name="provider-name"></a>Providernamn

Filsystem

## <a name="drives"></a>Enheter

`C:`, `D:` ...

## <a name="capabilities"></a>Funktioner

**Filter**, **ShouldProcess**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till filer och kataloger.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell- **dataprovidern** kan du hämta, lägga till, ändra, rensa och ta bort filer och kataloger i PowerShell.

**Fil Systems** enheter är ett hierarkiskt namn område som innehåller de kataloger och filer som finns på din dator. En **fil Systems** enhet kan vara en logisk eller fysisk enhet, katalog eller mappad nätverks resurs.

En enhet `TEMP:` som heter kommer att mappas till användarens tillfälliga katalog Sök väg.

>[!NOTE]
> Innehåll i TEMP: enheten tas inte bort automatiskt av PowerShell och är upp till den användare eller det operativ system som ska hanteras. Den här funktionen har flyttats från experimentella funktioner i PowerShell version 7,0

**Fil Systems** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Anropa-objekt](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Flytta objekt](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Get-ACL](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Ange ACL](xref:Microsoft.PowerShell.Security.Set-Acl)
- [Get-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [Set-AuthenticodeSignature](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Filerna är instanser av klassen [system. io. fileinfo](/dotnet/api/system.io.fileinfo) . Kataloger är instanser av klassen [system. io. DirectoryInfo](/dotnet/api/system.io.directoryinfo) .

## <a name="navigating-the-filesystem-drives"></a>Navigera i fil Systems enheter

**Fil Systems** leverantören visar sina data lager genom att mappa alla logiska enheter på datorn som PowerShell-enheter. Om du vill arbeta med en **fil Systems** enhet kan du ändra din plats till en enhet med hjälp av enhets namnet följt av ett kolon ( `:` ).

```powershell
Set-Location C:
```

Du kan också arbeta med **fil Systems** leverantören från någon annan PowerShell-enhet. Om du vill referera till en fil eller katalog från en annan plats använder du enhets namnet ( `C:` ,... `D:` ) i sökvägen.

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location). och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-files-and-directories"></a>Hämta filer och kataloger

`Get-ChildItem`Cmdleten returnerar alla filer och kataloger på den aktuella platsen. Du kan ange en annan sökväg för att söka efter och använda inbyggda parametrar för att filtrera och styra rekursion-djupet.

```powershell
Get-ChildItem
```

Läs mer om cmdlet-användning i [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem).

## <a name="copying-files-and-directories"></a>Kopiera filer och kataloger

`Copy-Item`Cmdleten kopierar filer och kataloger till en plats som du anger.
Parametrar är tillgängliga för att filtrera och rekursivt, ungefär som `Get-ChildItem` .

Följande kommando kopierar alla filer och kataloger under sökvägen "C:\Temp" \" till mappen "C:\Windows\Temp".

```powershell
Copy-Item -Path C:\temp\* -Destination C:\Windows\Temp -Recurse -File
```

`Copy-Item` skriver över filer i mål katalogen utan att uppmanas att bekräfta.

Det här kommandot kopierar `a.txt` filen från `C:\a` katalogen till `C:\a\bb` katalogen.

```powershell
Copy-Item -Path C:\a\a.txt -Destination C:\a\bb\a.txt
```

Kopierar alla kataloger och filer i `C:\a` katalogen till `C:\c` katalogen. Om någon av de kataloger som ska kopieras redan finns i mål katalogen, kommer kommandot att Miss kopie ras om du inte anger en Force-parameter.

```powershell
Copy-Item -Path C:\a\* -Destination C:\c -Recurse
```

Mer information finns i [Kopiera objekt](xref:Microsoft.PowerShell.Management.Copy-Item).

## <a name="moving-files-and-directories"></a>Flytta filer och kataloger

Det här kommandot flyttar `c.txt` filen i `C:\a` katalogen till `C:\a\aa` katalogen:

```powershell
Move-Item -Path C:\a\c.txt -Destination C:\a\aa
```

Kommandot kommer inte att skriva över en befintlig fil som har samma namn automatiskt. Om du vill tvinga cmdleten att skriva över en befintlig fil anger du parametern Force.

Du kan inte flytta en katalog när katalogen är den aktuella platsen. När du använder `Move-Item` för att flytta katalogen på den aktuella platsen visas det här felet.

```
C:\temp> Move-Item -Path C:\temp\ -Destination C:\Windows\Temp

Move-Item : Cannot move item because the item at 'C:\temp\' is in use.
At line:1 char:1
+ Move-Item C:\temp\ C:\temp2\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Move-Item], PSInvalidOperationException
    + FullyQualifiedErrorId : InvalidOperation,Microsoft.PowerShell.Commands.MoveItemCommand
```

## <a name="managing-file-content"></a>Hantera fil innehåll

### <a name="get-the-content-of-a-file"></a>Hämta innehållet i en fil

Det här kommandot hämtar innehållet i filen "Test.txt" och visar dem i-konsolen.

```powershell
Get-Content -Path Test.txt
```

Du kan skicka vidare innehållet i filen till en annan cmdlet. Följande kommando läser till exempel innehållet i `Test.txt` filen och skickar dem som indata till [ConvertTo-HTML-](xref:Microsoft.PowerShell.Utility.ConvertTo-Html) cmdleten:

```powershell
Get-Content -Path Test.txt | ConvertTo-Html
```

Du kan också hämta innehållet i en fil genom att förkorrigera dess Provider-sökväg med dollar tecknet ( `$` ). Sökvägen måste stå inom klammerparenteser på grund av variabla namngivnings begränsningar. Mer information finns i [about_Variables](about_Variables.md).

```powershell
${C:\Windows\System32\Drivers\etc\hosts}
```

### <a name="add-content-to-a-file"></a>Lägga till innehåll i en fil

Detta kommando lägger till strängen "testa innehåll" till `Test.txt` filen:

```powershell
Add-Content -Path test.txt -Value "test content"
```

Det befintliga innehållet i `Test.txt` filen tas inte bort.

### <a name="replace-the-content-of-a-file"></a>Ersätt innehållet i en fil

Det här kommandot ersätter `Test.txt` filens innehåll med strängen "test content":

```powershell
Set-Content -Path test.txt -Value "test content"
```

Innehållet i skrivs över `Test.txt` . Du kan använda **Value** -parametern för cmdleten [New-item](xref:Microsoft.PowerShell.Management.New-Item) för att lägga till innehåll i en fil när du skapar den.

### <a name="loop-through-the-contents-of-a-file"></a>Loopa igenom innehållet i en fil

Som standard `Get-Content` använder cmdleten rad slutet som avgränsare, så den hämtar en fil som en samling strängar, med varje rad som en sträng i filen.

Du kan använda `-Delimiter` parametern för att ange en alternativ avgränsare. Om du ställer in det på tecknen som anger slutet på ett avsnitt eller början av nästa avsnitt, kan du dela upp filen i logiska delar.

Det första kommandot hämtar `Employees.txt` filen och delar den i avsnitt, som var och en slutar med orden "slutet av medarbetar posten" och sparar den i `$e` variabeln.

Det andra kommandot använder mat ris notation för att hämta det första objektet i samlingen i `$e` . Det använder ett index på 0, eftersom PowerShell-matriser är noll-baserade.

Mer information om `Get-Content` cmdlet finns i hjälp avsnittet för [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content).

Mer information om matriser finns [about_Arrays](../About/about_Arrays.md).

```powershell
$e = Get-Content c:\test\employees.txt -Delimited "End Of Employee Record"
$e[0]
```

## <a name="managing-security-descriptors"></a>Hantera säkerhets beskrivningar

### <a name="view-the-acl-for-a-file"></a>Visa ACL för en fil

Det här kommandot returnerar ett [system. Security. AccessControl. FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -objekt:

```powershell
Get-Acl -Path test.txt | Format-List -Property *
```

Om du vill ha mer information om det här objektet, rör du kommandot till cmdleten [Get-Member](xref:Microsoft.PowerShell.Utility.Get-Member) . Eller, se [FileSecurity](/dotnet/api/system.security.accesscontrol.filesecurity) -klass.

### <a name="modify-the-acl-for-a-file"></a>Ändra ACL för en fil

### <a name="create-and-set-an-acl-for-a-file"></a>Skapa och ange en ACL för en fil

## <a name="creating-files-and-directories"></a>Skapa filer och kataloger

### <a name="create-a-directory"></a>Skapa en katalog

Det här kommandot skapar `logfiles` katalogen på `C` enheten:

```powershell
New-Item -Path c:\ -Name logfiles -Type directory
```

PowerShell innehåller också en `mkdir` funktion (alias `md` ) som använder cmdleten [New-item](xref:Microsoft.PowerShell.Management.New-Item) för att skapa en ny katalog.

### <a name="create-a-file"></a>Skapa en fil

Det här kommandot skapar `log2.txt` filen i `C:\logfiles` katalogen och lägger sedan till strängen "testa logg" i filen:

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file
```

### <a name="create-a-file-with-content"></a>Skapa en fil med innehåll

Skapar en fil som kallas `log2.txt` i `C:\logfiles` katalogen och lägger till strängen "test loggen" i filen.

```powershell
New-Item -Path c:\logfiles -Name log2.txt -Type file -Value "test log"
```

## <a name="renaming-files-and-directories"></a>Byta namn på filer och kataloger

### <a name="rename-a-file"></a>Byt namn på en fil

Det här kommandot byter namn på `a.txt` filen i `C:\a` katalogen till `b.txt` :

```powershell
Rename-Item -Path c:\a\a.txt -NewName b.txt
```

### <a name="rename-a-directory"></a>Byta namn på en katalog

Det här kommandot byter namn på `C:\a\cc` katalogen till `C:\a\dd` :

```powershell
Rename-Item -Path c:\a\cc -NewName dd
```

## <a name="deleting-files-and-directories"></a>Ta bort filer och kataloger

### <a name="delete-a-file"></a>Ta bort en fil

Det här kommandot tar bort `Test.txt` filen i den aktuella katalogen:

```powershell
Remove-Item -Path test.txt
```

### <a name="delete-files-using-wildcards"></a>Ta bort filer med jokertecken

Det här kommandot tar bort alla filer i den aktuella katalogen som har `.xml` fil namns tillägget:

```powershell
Remove-Item -Path *.xml
```

## <a name="starting-a-program-by-invoking-an-associated-file"></a>Starta ett program genom att anropa en associerad fil

### <a name="invoke-a-file"></a>Anropa en fil

Det första kommandot använder cmdleten [Get-service](xref:Microsoft.PowerShell.Management.Get-Service) för att hämta information om lokala tjänster.

Den rör informationen till [export-csv-](xref:Microsoft.PowerShell.Utility.Export-Csv) cmdleten och lagrar sedan informationen i `Services.csv` filen.

Det andra kommandot använder [Invoke-item](xref:Microsoft.PowerShell.Management.Invoke-Item) för att öppna `services.csv` filen i programmet som är associerat med `.csv` tillägget:

```powershell
Get-Service | Export-Csv -Path services.csv
Invoke-Item -Path services.csv
```

## <a name="getting-files-and-folders-with-specified-attributes"></a>Hämta filer och mappar med angivna attribut

### <a name="get-system-files"></a>Hämta systemfiler

Detta kommando hämtar systemfiler i den aktuella katalogen och dess under kataloger.

`-File`Parametern används för att bara hämta filer (inte kataloger) och `-System` parametern för att bara hämta objekt med attributet "system".

Den använder `-Recurse` parametern för att hämta objekten i den aktuella katalogen och alla under kataloger.

```powershell
Get-ChildItem -File -System -Recurse
```

### <a name="get-hidden-files"></a>Hämta dolda filer

Det här kommandot hämtar alla filer, inklusive dolda filer, i den aktuella katalogen.

Den använder parametern **attributes** med två värden, `!Directory+Hidden` , som hämtar dolda filer och `!Directory` , som hämtar alla andra filer.

```powershell
Get-ChildItem -Attributes !Directory,!Directory+Hidden
```

`dir -att !d,!d+h` är motsvarigheten till det här kommandot.

### <a name="get-compressed-and-encrypted-files"></a>Hämta komprimerade och krypterade filer

Det här kommandot hämtar filer i den aktuella katalogen som är antingen komprimerade eller krypterade.

`-Attributes`Parametern med två värden används `Compressed` och `Encrypted` . Värdena avgränsas med ett kommatecken `,` som representerar operatorn "eller".

```powershell
Get-ChildItem -Attributes Compressed,Encrypted
```

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.

### <a name="encoding-microsoftpowershellcommandsfilesystemcmdletproviderencoding"></a>Inställning \<Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding\>

Anger fil kodningen. Standardvärdet är ASCII.

- **ASCII**: använder kodningen för ASCII-teckenuppsättningen (7-bitars).
- **BigEndianUnicode**: kodar i UTF-16-format med big-endian byte-ordningen.
- **Sträng**: använder kodnings typen för en sträng.
- **Unicode**: kodar i UTF-16-format med en liten-endian-order.
- **UTF7**: kodar i UTF-7-format.
- **Utf8**: kodar i UTF-8-format.
- **UTF8BOM**: kodar i UTF-8-format med byte ordnings tecken (BOM)
- **UF8NOBOM**: kodar i UTF-8-format utan byte ordnings tecken (BOM)
- **UTF32**: kodar i UTF-32-format.
- **Standard**: kodas på den installerade standard tecken tabellen.
- **OEM**: använder standard kodning för MS-DOS-och-konsol program.
- **Okänd**: kodnings typen är okänd eller ogiltig. Data kan behandlas som binära.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Lägg till innehåll](xref:Microsoft.PowerShell.Management.Add-Content)
- [Hämta innehåll](xref:Microsoft.PowerShell.Management.Get-Content)
- [Ange innehåll](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="delimiter-systemstring"></a>Avgränsare \<System.String\>

Anger den avgränsare som [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) använder för att dela upp filen i objekt när den läses.

Standardvärdet är `\n` rad slutet.

När du läser en textfil returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) en samling av sträng objekt, som var och en slutar med avgränsnings tecken.

Om du anger en avgränsare som inte finns i filen returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) hela filen som ett enskilt avgränsat objekt.

Du kan använda den här parametern för att dela upp en stor fil i mindre filer genom att ange en fil avgränsare, till exempel "slutet av exemplet", som avgränsare. Avgränsaren bevaras (tas inte bort) och blir det sista objektet i varje fil avsnitt.

> [!NOTE]
> När värdet för `-Delimiter` parametern är en tom sträng returnerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) inte något.
> Detta är ett känt problem. Om du vill tvinga [Get-innehåll](xref:Microsoft.PowerShell.Management.Get-Content) att returnera hela filen som en enskild, icke-avgränsad sträng anger du ett värde som inte finns i filen.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Hämta innehåll](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="wait-systemmanagementautomationswitchparameter"></a>Vänta \<System.Management.Automation.SwitchParameter\>

Väntar på att innehåll ska läggas till i filen. Om innehållet läggs till, returneras det tillagda innehållet. Om innehållet har ändrats returnerar det hela filen.

När du väntar så kontrollerar [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content) att filen är en gång i sekunden tills du avbryter den, till exempel genom att trycka på CTRL + C.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Hämta innehåll](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="attributes-flagsexpression"></a>Dokumentattribut \<FlagsExpression\>

Hämtar filer och mappar med de angivna attributen. Den här parametern stöder alla attribut och gör att du kan ange komplexa kombinationer av attribut.

`-Attributes`Parametern introducerades i Windows PowerShell 3,0.

`-Attributes`Parametern stöder följande attribut:

- **Arkiv**
- **Komprimerade**
- **Enhet**
- **Katalog**
- **Krypterad**
- **Dold**
- **Normal**
- **NotContentIndexed**
- **Offline**
- **ReadOnly**
- **ReparsePoint**
- **SparseFile**
- **System**
- **Tillfälliga**

En beskrivning av dessa attribut finns i [FileAttributes](/dotnet/api/system.io.fileattributes) -uppräkningen.

Använd följande operatorer för att kombinera attribut.

- `!` – INTE
- `+` -OCH
- `,` -ELLER

Inga blank steg är tillåtna mellan en operator och dess attribut. Blank steg tillåts dock före kommatecken.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="directory-systemmanagementautomationswitchparameter"></a>Katalogen \<System.Management.Automation.SwitchParameter\>

Hämtar kataloger (mappar).

`-Directory`Parametern introducerades i Windows PowerShell 3,0.

Om du bara vill hämta kataloger använder du `-Directory` parametern och utelämnar `-File` parametern. Om du vill utesluta kataloger använder du `-File` parametern och utelämnar `-Directory` parametern, eller använder `-Attributes` parametern.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="file-systemmanagementautomationswitchparameter"></a>Arkiv \<System.Management.Automation.SwitchParameter\>

Hämtar filer.

`-File`Parametern introducerades i Windows PowerShell 3,0.

Om du bara vill hämta filer använder du `-File` parametern och utelämnar `-Directory` parametern. Om du vill undanta filer använder du `-Directory` parametern och utelämnar `-File` parametern, eller så använder du `-Attributes` parametern.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="hidden-systemmanagementautomationswitchparameter"></a>Dölja \<System.Management.Automation.SwitchParameter\>

Hämtar endast dolda filer och kataloger (mappar). Som standard får [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) endast icke-dolda objekt.

`-Hidden`Parametern introducerades i Windows PowerShell 3,0.

Om du bara vill ha dolda objekt använder du `-Hidden` parametern, dess `h` eller `ah` alias eller det **dolda** värdet för `-Attributes` parametern. Om du vill utesluta dolda objekt utelämnar du `-Hidden` parametern eller använder `-Attributes` parametern.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="readonly-systemmanagementautomationswitchparameter"></a>ReadOnly \<System.Management.Automation.SwitchParameter\>

Hämtar endast skrivskyddade filer och kataloger (mappar).

`-ReadOnly`Parametern introducerades i Windows PowerShell 3,0.

Om du bara vill hämta skrivskyddade objekt använder du `-ReadOnly` parametern, dess `ar` alias eller det **skrivskyddade** värdet för `-Attributes` parametern. Använd parametern för att undanta skrivskyddade objekt `-Attributes` .

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="system-systemmanagementautomationswitchparameter"></a>Säker \<System.Management.Automation.SwitchParameter\>

Hämtar endast systemfiler och kataloger (mappar).

`-System`Parametern introducerades i Windows PowerShell 3,0.

Om du bara vill hämta systemfiler och mappar använder du `-System` parametern, dess `as` alias eller **systemets** värde för `-Attributes` parametern. Om du vill undanta systemfiler och mappar använder du `-Attributes` parametern.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="newerthan-systemdatetime"></a>NewerThan \<System.DateTime\>

Returnerar `$True` när `LastWriteTime` värdet för en fil är större än det angivna datumet. Annars returneras `$False` .

Ange ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel ett som cmdleten [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) returnerar, eller en sträng som kan konverteras till ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel `"August 10, 2011 2:00 PM"` .

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Test-sökväg](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="olderthan-systemdatetime"></a>OlderThan \<System.DateTime\>

Returnerar `$True` när `LastWriteTime` värdet för en fil är mindre än det angivna datumet. Annars returneras `$False` .

Ange ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel ett som cmdleten [Get-date](xref:Microsoft.PowerShell.Utility.Get-Date) returnerar, eller en sträng som kan konverteras till ett [datetime](/dotnet/api/system.datetime) -objekt, till exempel `"August 10, 2011 2:00 PM"` .

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Test-sökväg](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="stream-systemstring"></a>Skicka \<System.String\>

Hanterar alternativa data strömmar. Ange data ström namnet. Jokertecken tillåts endast i kommandona [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) för och [Remove-item](xref:Microsoft.PowerShell.Management.Remove-Item) i en fil systemen het.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Lägg till innehåll](xref:Microsoft.PowerShell.Management.Add-Content)
- [Rensa innehåll](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Hämta innehåll](xref:Microsoft.PowerShell.Management.Get-Content)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Ange innehåll](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="raw-switchparameter"></a>Outspädd \<SwitchParameter\>

Ignorerar rad matnings tecken. Returnerar innehåll som ett enda objekt.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Hämta innehåll](xref:Microsoft.PowerShell.Management.Get-Content)

### <a name="itemtype-string"></a>ItemType \<String\>

Med den här parametern kan du ange Tye för det objekt som ska skapas med `New-Item`

De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.

I en `FileSystem` enhet tillåts följande värden:

- Fil
- Katalog
- SymbolicLink
- Knutpunkt
- HardLink

### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

## <a name="using-the-pipeline"></a>Använda pipelinen

Provider-cmdletar accepterar pipeline-ininformation. Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.
Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.

## <a name="getting-help"></a>Få hjälp

Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.

Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path c:
```

## <a name="see-also"></a>Se även

[about_Providers](../About/about_Providers.md)
