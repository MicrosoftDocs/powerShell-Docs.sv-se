---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: 14b1c5d0f37301a5312f37a115f0abc1c7b5990e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266816"
---
# Get-ChildItem

## SAMMANFATTNING

Hämtar objekten och underordnade objekt på en eller flera angivna platser.

## SYNTAX

### Objekt (standard)

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### LiteralItems

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## BESKRIVNING

`Get-ChildItem`Cmdlet: en hämtar objekten på en eller flera angivna platser. Om objektet är en behållare hämtas objekten inuti behållaren, så kallade underordnade objekt. Du kan använda parametern **rekursivt** för att hämta objekt i alla underordnade behållare och använda parametern **djup** för att begränsa antalet nivåer till rekursivt.

`Get-ChildItem` visar inte tomma kataloger. När ett `Get-ChildItem` kommando innehåller **djup** -eller **rekursivt** -parametrarna tas tomma kataloger inte med i utdata.

Platser exponeras `Get-ChildItem` av PowerShell-leverantörer. En plats kan vara en fil system katalog, en registrerings data fil eller ett certifikat arkiv. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## EXEMPEL

### Exempel 1: Hämta underordnade objekt från en fil system katalog

Det här exemplet hämtar underordnade objekt från en fil system katalog. Fil namnen och under katalog namnen visas. För tomma platser returnerar kommandot inga utdata och återgår till PowerShell-prompten.

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen `C:\Test` .
`Get-ChildItem` visar filer och kataloger i PowerShell-konsolen.

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

Som standard `Get-ChildItem` visas läget ( **attribut** ), **LastWriteTime** , fil storlek ( **längd** ) och **namnet** på objektet. Bokstäverna i egenskapen **mode** kan tolkas på följande sätt:

- `l` Operationsföljdslänkkod
- `d` katalogen
- `a` arkivattributet
- `r` (skrivskyddad)
- `h` dölja
- `s` (system).

Mer information om läges flaggor finns [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression).

### Exempel 2: Hämta underordnade objekt namn i en katalog

I det här exemplet visas endast namn på objekt i en katalog.

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen `C:\Test` . Parametern **Name** returnerar bara fil-eller katalog namnen från den angivna sökvägen.

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### Exempel 3: Hämta underordnade objekt i den aktuella katalogen och under kataloger

I det här exemplet visas **. txt** -filer som finns i den aktuella katalogen och dess under kataloger.

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange `C:\Test\*.txt` . **Sökvägen** använder jokertecknet asterisk ( `*` ) för att ange alla filer med fil namns tillägget `.txt` . Parametern **rekursivt** söker igenom **Sök vägs** katalogen under kataloger, som du ser i **katalogen:** rubriker. Parametern **Force** visar dolda filer som `hiddenfile.txt` har ett läge på **h**.

### Exempel 4: Hämta underordnade objekt med parametern include

I det här exemplet `Get-ChildItem` används parametern **include** för att hitta specifika objekt från katalogen som anges i parametern **Path** .

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen **C:\test**. Parametern **Path** innehåller ett avslutande asterisk ( `*` )-jokertecken för att ange katalogens innehåll.
Parametern **include** använder en asterisk ( `*` ) som jokertecken för att ange alla filer med fil namns tillägget **. txt**.

När parametern **include** används, behöver parametern **Path** en avslutande asterisk ( `*` ) som jokertecken för att ange katalogens innehåll. Till exempel `-Path C:\Test\*`.

- Om parametern **rekursivt** läggs till i kommandot är den efterföljande asterisken ( `*` ) i parametern **Path** valfri. Parametern **rekursivt** hämtar objekt från **Sök vägs** katalogen och dess under kataloger. Till exempel `-Path C:\Test\ -Recurse -Include *.txt`
- Om en avslutande asterisk ( `*` ) inte ingår i parametern **Path** returnerar kommandot inga utdata och återgår till PowerShell-prompten. Till exempel `-Path C:\Test\`.

### Exempel 5: Hämta underordnade objekt med parametern exclude

I exemplet visas innehållet i katalogen **C:\Test\Logs**. Utdata är en referens för de andra kommandona som använder parametrarna **exclude** och **rekursivt** .

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen `C:\Test\Logs` .
Parametern **exclude** använder jokertecknet asterisk ( `*` ) för att ange vilka filer eller kataloger som börjar med **A** eller som **a** ska uteslutas från utdata.

När **exkluderings** parametern används är en efterföljande asterisk ( `*` ) i parametern **Path** valfri. Exempel: `-Path C:\Test\Logs` eller `-Path C:\Test\Logs\*`.

- Om en avslutande asterisk ( `*` ) inte ingår i parametern **Path** , visas innehållet i parametern **Path** . Undantag är fil namn eller under Katalog namn som matchar värdet för **exkluderings** parametern.
- Om en avslutande asterisk ( `*` ) ingår i parametern **Path** , recurses kommandot till **Sök vägs** parameterns under kataloger. Undantag är fil namn eller under Katalog namn som matchar värdet för **exkluderings** parametern.
- Om parametern **rekursivt** läggs till i kommandot är rekursion-utdata detsamma, oavsett om **Sök vägs** parametern innehåller en efterföljande asterisk ( `*` ).

### Exempel 6: Hämta register nycklar från en registrerings data fil

Det här exemplet hämtar alla register nycklar från `HKEY_LOCAL_MACHINE\HARDWARE` .

`Get-ChildItem` använder parametern **Path** för att ange register nyckeln `HKLM:\HARDWARE` . Hive-sökvägen och den översta nivån i register nycklar visas i PowerShell-konsolen.

Mer information finns i [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md).

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

Det första kommandot visar innehållet i `HKLM:\HARDWARE` register nyckeln. Parametern **exclud** instruerar `Get-ChildItem` att inte returnera några under nycklar som börjar med `D*` . För närvarande fungerar inte parametern **exclude** på under nycklar, inte objekt egenskaper.

### Exempel 7: Hämta alla certifikat med kod signerings utfärdare

Det här exemplet hämtar varje certifikat i PowerShell- **certifikatet:** enhet som har kod signerings auktoritet.

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange **certifikatet:** Provider. Parametern **rekursivt** söker igenom katalogen som anges av **sökväg** och dess under kataloger. Parametern **CodeSigningCert** hämtar endast certifikat som har kod signerings auktoritet.

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

Mer information om certifikat leverantören och certifikatet: enhet finns i [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md).

### Exempel 8: Hämta objekt med hjälp av parametern djup

I det här exemplet visas objekten i en katalog och dess under kataloger. Parametern **djup** anger antalet under katalog nivåer som ska tas med i rekursion. Tomma kataloger undantas från utdata.

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange **C:\Parent**. Parametern **djup** anger två nivåer av rekursion. `Get-ChildItem` visar innehållet i katalogen som anges av parametern **Path** och de två nivåerna av under kataloger.

### Exempel 9: Hämta information om hårda länkar

I PowerShell 6,2 lades en alternativ vy till för att hämta information om hårda länkar.

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

## Parametrar

### -Attribut

Hämtar filer och mappar med de angivna attributen. Den här parametern stöder alla attribut och gör att du kan ange komplexa kombinationer av attribut.

Om du till exempel vill hämta icke-systemfiler (inte kataloger) som är krypterade eller komprimerade skriver du:

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

Om du vill söka efter filer och mappar med attribut som används ofta använder du parametern **attribut** . Eller Parameters- **katalogen** , **fil** , **dold** , **ReadOnly** och **system**.

Parametern **attributs** stöder följande egenskaper:

- **Arkiv**
- **Komprimerade**
- **Enhet**
- **Katalog**
- **Krypterad**
- **Dold**
- **IntegrityStream**
- **Normal**
- **NoScrubData**
- **NotContentIndexed**
- **Offline**
- **ReadOnly**
- **ReparsePoint**
- **SparseFile**
- **System**
- **Tillfälliga**

En beskrivning av dessa attribut finns i FileAttributes- [uppräkningen](/dotnet/api/system.io.fileattributes).

Använd följande operatorer för att kombinera attribut:

- `!` Ogiltigt
- `+` SÄRSKILT
- `,` ELLER

Använd inte blank steg mellan en operator och dess attribut. Blank steg accepteras efter kommatecken.

Använd följande förkortningar för gemensamma attribut:

- `D` Katalogen
- `H` Dölja
- `R` (Skrivskyddad)
- `S` Säker

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Djup

Den här parametern lades till i PowerShell 5,0 och du kan kontrol lera djupet i rekursion. Som standard `Get-ChildItem` visas innehållet i den överordnade katalogen. Parametern **djup** avgör antalet under katalog nivåer som ingår i rekursion och visar innehållet.

Innehåller till exempel `Depth 2` **Sök vägs** parameterns katalog, första nivån av under kataloger och den andra nivån av under kataloger. Som standard inkluderas katalog namn och fil namn i utdata.

> [!NOTE]
> På en Windows-dator från PowerShell eller **cmd.exe** kan du Visa en grafisk vy över en katalog struktur med kommandot **Tree.com** .

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Directory

Om du vill hämta en lista över kataloger använder du **katalog** parametern eller parametern **attribut** med **katalog** egenskapen. Du kan använda parametern **rekursivt** med **Directory**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Undanta

Anger, som en sträng mat ris, en egenskap eller egenskap som denna cmdlet exkluderar från åtgärden.
Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` eller `A*` . Jokertecken accepteras.

En efterföljande asterisk ( `*` ) i parametern **Path** är valfri. Exempel: `-Path C:\Test\Logs` eller `-Path C:\Test\Logs\*`. Om en avslutande asterisk ( `*` ) tas med, recurses kommandot till **Sök vägs** parameterns under kataloger. Utan asterisk ( `*` ) visas innehållet i **Sök vägs** parametern. Mer information finns i exempel 5 och avsnittet om anteckningar.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Fil

Använd **fil** parametern om du vill hämta en lista över filer. Du kan använda parametern **rekursivt** med **filen**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder filter. Filter är mer effektiva än andra parametrar. Providern använder filter när-cmdlet: en hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats. Filter strängen skickas till .NET-API: et för att räkna upp filer. API: t stöder bara `*` och `?` jokertecken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -FollowSymlink

Som standard `Get-ChildItem` visar cmdlet symboliska länkar till kataloger som hittades under rekursion, men rekursivt inte till dem. Använd parametern **FollowSymlink** för att söka i de kataloger som är riktade mot de symboliska länkarna. **FollowSymlink** är en dynamisk parameter och stöds bara i **fil** tjänst leverantören.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tillåter att cmdleten hämtar objekt som annars inte kan nås av användaren, till exempel dolda filer eller systemfiler. Parametern **Force** åsidosätter inte säkerhets begränsningar. Implementeringen varierar mellan olika leverantörer. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Dold

Om du bara vill ha dolda objekt använder du parametern **Hidden** eller parametern **attribut** med egenskapen **Hidden** . Som standard `Get-ChildItem` visar inte dolda objekt. Använd parametern **Force** för att hämta dolda objekt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Inkludera

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` . Jokertecken är tillåtna. Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken anger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hämtar endast namnen på objekten på platsen. Utdata är ett sträng objekt som kan skickas ned pipelinen till andra kommandon. Jokertecken är tillåtna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Anger en sökväg till en eller flera platser. Jokertecken accepteras. Standard platsen är den aktuella katalogen ( `.` ).

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – ReadOnly

Om du bara vill hämta skrivskyddade objekt kan du använda **ReadOnly** -parametern eller egenskapen **attributs** **ReadOnly** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Rekursivt

Hämtar objekten på de angivna platserna och i alla underordnade objekt på platserna.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – System

Hämtar endast systemfiler och kataloger. Om du bara vill hämta systemfiler och mappar använder du **system** parametern eller **attributets** parameter **system** egenskap.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till `Get-ChildItem` .

## UTDATA

### System. Object

Vilken typ av objekt som `Get-ChildItem` returneras bestäms av objekten i providerns enhets Sök väg.

### System. String

Om du använder parametern **Name** `Get-ChildItem` returneras objekt namnen som strängar.

## ANTECKNINGAR

- `Get-ChildItem` kan köras med något av de inbyggda aliasen,, `ls` `dir` och `gci` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Get-ChildItem` som standard visas inte dolda objekt. Använd parametern **Force** för att hämta dolda objekt.
- `Get-ChildItem`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .
  Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-alias](../Microsoft.PowerShell.Utility/Get-Alias.md)

[Hämta objekt](Get-Item.md)

[Get-location](Get-Location.md)

[Hämta process](Get-Process.md)

[Get-PSProvider](Get-PSProvider.md)

[Dela-sökväg](Split-Path.md)
