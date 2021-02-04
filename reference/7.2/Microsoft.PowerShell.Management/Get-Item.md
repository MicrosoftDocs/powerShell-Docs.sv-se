---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 67d9f351b8ef4936dcb4e9cff6583da0f464bc12
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693044"
---
# Get-Item

## SAMMANFATTNING
Hämtar objektet på den angivna platsen.

## SYNTAX

### Sökväg (standard)

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### LiteralPath

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Item`Cmdlet: en hämtar objektet på den angivna platsen. Det får inte innehållet i objektet på platsen om du inte använder ett jokertecken ( `*` ) för att begära allt innehåll i objektet.

Denna cmdlet används av PowerShell-leverantörer för att navigera mellan olika typer av data lager.

## EXEMPEL

### Exempel 1: hämta den aktuella katalogen

Det här exemplet hämtar den aktuella katalogen. Punkten ('. ') representerar objektet på den aktuella platsen (inte dess innehåll).

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### Exempel 2: Hämta alla objekt i den aktuella katalogen

Det här exemplet hämtar alla objekt i den aktuella katalogen. Jokertecknet ( `*` ) representerar allt innehåll i det aktuella objektet.

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### Exempel 3: hämta den aktuella katalogen för en enhet

Det här exemplet hämtar enhetens aktuella katalog `C:` . Objektet som hämtas representerar bara katalogen, inte dess innehåll.

```powershell
Get-Item C:\
```

### Exempel 4: Hämta objekt på den angivna enheten

I det här exemplet hämtas objekt i `C:` enheten. Jokertecknet ( `*` ) representerar alla objekt i behållaren, inte bara behållaren.

```powershell
Get-Item C:\*
```

I PowerShell använder du en enda asterisk ( `*` ) för att hämta innehåll i stället för den traditionella `*.*` . Formatet tolkas bokstavligen, så `*.*` skulle inte hämta kataloger eller fil namn utan punkt.

### Exempel 5: Hämta en egenskap i den angivna katalogen

Det här exemplet hämtar katalogens **LastAccessTime** -egenskap `C:\Windows` . **LastAccessTime** är bara en egenskap för fil system kataloger. Om du vill se alla egenskaper för en katalog skriver du `(Get-Item <directory-name>) | Get-Member` .

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### Exempel 6: Visa innehållet i en register nyckel

Det här exemplet visar innehållet i register nyckeln **Microsoft. PowerShell** . Du kan använda den här cmdleten med PowerShell-registerposten för att hämta register nycklar och under nycklar, men du måste använda cmdlet: en `Get-ItemProperty` för att hämta register värden och data.

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### Exempel 7: Hämta objekt i en katalog som har ett undantag

Det här exemplet hämtar objekt i Windows-katalogen med namn som innehåller en punkt ( `.` ), men börjar inte med `w*` . Det här exemplet fungerar bara om sökvägen innehåller ett jokertecken ( `*` ) för att ange innehållet i objektet.

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### Exempel 8: Hämta hardlink-information

I PowerShell 6,2 lades en alternativ vy till för att hämta hardlink-information. För att få information om hardlink, skicka in utdata till `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### Exempel 9: utdata för operativ system som inte är Windows-operativsystem

I PowerShell 7,1 på UNIX `Get-Item` -system tillhandahåller cmdlet: en UNIX-liknande utdata:

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

De nya egenskaperna som nu är en del av utdata är:

- **UnixMode** är de fil behörigheter som representeras i ett UNIX-system
- **Användaren** är filens ägare
- **Grupp** är grupp ägare
- **Storlek** är storleken på filen eller katalogen som representeras på ett UNIX-system

> [!NOTE]
> Den här funktionen har flyttats från experimentell till vanlig i PowerShell 7,1.

## PARAMETRAR

### -Stream

> [!NOTE]
> Den här parametern är endast tillgänglig i Windows.

Hämtar den angivna alternativa data strömmen från filen. Ange data ström namnet. Jokertecken stöds. Använd en asterisk () om du vill hämta alla strömmar `*` . Den här parametern är giltig för kataloger, men Observera att kataloger inte har data strömmar som standard.

Den här parametern introducerades i PowerShell 3,0.  Från och med PowerShell 7,2 `Get-Item` kan du hämta alternativa data strömmar från kataloger och filer.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
Accept wildcard characters: True
```

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell.
> Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Undanta

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna. Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

### -Filter

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder filter. Filter är mer effektiva än andra parametrar. Providern använder filter när-cmdlet: en hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats. Filter strängen skickas till .NET-API: et för att räkna upp filer. API: t stöder bara `*` och `?` jokertecken.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Anger att den här cmdleten hämtar objekt som inte kan nås på annat sätt, t. ex. dolda objekt.
Implementeringen varierar från providern till providern. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md). Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

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

### -Inkludera

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna. Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till ett objekt. Denna cmdlet hämtar objektet på den angivna platsen. Jokertecken är tillåtna. Den här parametern är obligatorisk, men parameterns namn **Sök väg** är valfri.

`.`Ange den aktuella platsen genom att använda en punkt (). Använd jokertecknet ( `*` ) för att ange alla objekt på den aktuella platsen.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### System. Object

Denna cmdlet returnerar de objekt som den hämtar. Typen bestäms av typen av objekt i sökvägen.

## ANTECKNINGAR

Denna cmdlet har ingen **rekursivt** -parameter, eftersom den bara får ett objekt, inte dess innehåll.
Använd om du vill hämta innehållet i ett objekt rekursivt `Get-ChildItem` .

Använd denna cmdlet för att hämta register nycklar och `Get-ItemProperty` för att hämta register värden och data för att navigera i registret. Register värden anses vara egenskaper för register nyckeln.

Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Rensa objekt](Clear-Item.md)

[Kopiera objekt](Copy-Item.md)

[Anropa-objekt](Invoke-Item.md)

[Flytta objekt](Move-Item.md)

[Nytt objekt](New-Item.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – objekt](Rename-Item.md)

[Ange objekt](Set-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

