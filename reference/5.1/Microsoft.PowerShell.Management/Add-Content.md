---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 903c4eb784c1bb86b66766c7dfb563f586545dc1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266270"
---
# Add-Content

## SAMMANFATTNING
Lägger till innehåll till de angivna objekten, till exempel att lägga till ord i en fil.

## SYNTAX

### Sökväg (standard)

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### LiteralPath

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## BESKRIVNING

`Add-Content`Cmdleten lägger till innehåll i ett angivet objekt eller en angiven fil. Du kan ange innehållet genom att skriva innehållet i kommandot eller genom att ange ett objekt som innehåller innehållet.

Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).

## EXEMPEL

### Exempel 1: Lägg till en sträng till alla textfiler med ett undantag

I det här exemplet läggs ett värde till i textfiler i den aktuella katalogen, men filer som är baserade på fil namnet exkluderas.

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

`Add-Content`Cmdleten använder parametern **Path** för att ange alla. txt-filer i den aktuella katalogen. Parametern **exclude** ignorerar fil namn som matchar det angivna mönstret. Parametern **Value** anger text strängen som skrivs till filerna.

Använd [Get-Content](Get-Content.md) för att visa innehållet i de här filerna.

### Exempel 2: Lägg till ett datum i slutet av de angivna filerna

I det här exemplet läggs datumet till i den aktuella katalogen och datumet visas i PowerShell-konsolen.

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

`Add-Content`Cmdleten använder parametrarna **Path** och **Value** för att skapa två nya filer i den aktuella katalogen. Parametern **Value** anger den `Get-Date` cmdlet som ska hämta datumet och skickar datumet till `Add-Content` . `Add-Content`Cmdleten skriver datumet till varje fil. Parametern **Passthru** skickar ett objekt som representerar date-objektet. Eftersom det inte finns någon annan cmdlet för att ta emot det skickade objektet visas det i PowerShell-konsolen. `Get-Content`Cmdleten visar den uppdaterade filen DateTimeFile1. log.

### Exempel 3: lägga till innehållet i en angiven fil till en annan fil

Det här exemplet hämtar innehållet från en fil och lägger till innehållet i en annan fil.

```powershell
Add-Content -Path .\CopyToFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\CopyToFile.txt
```

`Add-Content`Cmdleten använder parametern **Path** för att ange den nya filen i den aktuella katalogen CopyToFile.txt. Parametern **Value** använder `Get-Content` cmdleten för att hämta innehållet i filen CopyFromFile.txt. Parenteserna runt `Get-Content` cmdleten ser till att kommandot slutförs innan `Add-Content` kommandot börjar. Parametern **Value** skickas till `Add-Content` . `Add-Content`Cmdleten lägger till data i CopyToFile.txts filen. `Get-Content`Cmdleten visar den uppdaterade filen CopyToFile.txt.

### Exempel 4: Använd en variabel för att lägga till innehållet i en angiven fil till en annan fil

Det här exemplet hämtar innehållet från en fil och lagrar innehållet i en variabel. Variabeln används för att lägga till innehållet i en annan fil.

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

`Get-Content`Cmdlet: en hämtar innehållet i CopyFromFile.txt och lagrar innehållet i `$From` variabeln. `Add-Content`Cmdleten använder parametern **Path** för att ange CopyToFile.txt filen i den aktuella katalogen. **Värde** parametern använder `$From` variabeln och skickar innehållet till `Add-Content` . `Add-Content`Cmdleten uppdaterar CopyToFile.txt-filen. `Get-Content`Cmdleten visar CopyToFile.txt.

### Exempel 5: skapa en ny fil och kopiera innehåll

Det här exemplet skapar en ny fil och kopierar en befintlig fils innehåll till den nya filen.

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

`Add-Content`Cmdleten använder **sökvägen** och **värde** parametrarna för att skapa en ny fil i den aktuella katalogen. Parametern **Value** använder `Get-Content` cmdleten för att hämta innehållet i en befintlig fil CopyFromFile.txt. Parenteserna runt `Get-Content` cmdleten ser till att kommandot slutförs innan `Add-Content` kommandot börjar. **Värdet** parameter överför det innehåll som `Add-Content` NewFile.txt-filen uppdateras till. `Get-Content`Cmdleten visar innehållet i den nya filen NewFile.txt.

### Exempel 6: Lägg till innehåll i en skrivskyddad fil

Det här kommandot lägger till värdet i filen även om Filattributet **IsReadOnly** har angetts till true.
Stegen för att skapa en skrivskyddad fil ingår i exemplet.

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar---        1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

`New-Item`Cmdleten använder parametrarna **Path** och **itemType** för att skapa filen IsReadOnlyTextFile.txt i den aktuella katalogen. `Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true. `Get-ChildItem`Cmdleten visar att filen är tom (0) och har attributet skrivskyddad ( `r` ). `Add-Content`Cmdleten använder parametern **Path** för att ange filen. Parametern **Value** innehåller text strängen som ska läggas till i filen. Parametern **Force** skriver texten till den skrivskyddade filen. `Get-Content`Cmdleten använder parametern **Path** för att visa filens innehåll.

Om du vill ta bort det skrivskyddade attributet använder du `Set-ItemProperty` kommandot med **värdet** parameter inställt på `False` .

## PARAMETRAR

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord.

> [!WARNING]
> Den här parametern stöds inte av några providrar som installeras med PowerShell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är `Default`.

De acceptabla värdena för den här parametern är följande:

- `Ascii` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `BigEndianUTF32` Använder UTF-32 med big-endian byte-ordningen.
- `Byte` Kodar en uppsättning tecken i en sekvens med byte.
- `Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).
- `Oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.
- `String` Samma som **Unicode**.
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `Unknown` Samma som **Unicode**.
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8.
- `UTF32` Använder UTF-32 med en liten-endian-order.

Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` cmdleten. Den här parametern fungerar bara i fil system enheter.

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Undanta

Utesluter de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel **\* . txt**. Jokertecken är tillåtna.

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

Anger ett filter i providerns format eller språk. Värdet för den här parametern kvalificerar parametern **Path** . Syntaxen för filtret, inklusive användning av jokertecken, beror på providern. **Filter** är mer effektiva än andra parametrar eftersom providern använder filter när objekt hämtas. Annars filtrerar PowerShell-processen efter att objekten har hämtats.

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

Åsidosätter det skrivskyddade attributet så att du kan lägga till innehåll i en skrivskyddad fil. **Tvinga** åsidosätter till exempel det skrivskyddade attributet eller skapa kataloger för att slutföra en fil Sök väg, men kommer inte att försöka ändra fil behörigheter.

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

### -Inkludera

Lägger bara till de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel **\* . txt**. Jokertecken är tillåtna.

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

Anger sökvägen till de objekt som tar emot det ytterligare innehållet. Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – NoNewline

Anger att denna cmdlet inte lägger till en ny rad eller vagn retur i innehållet.

Sträng representationerna av indata-objekten sammanfogas för att bilda utdata. Inga blank steg eller newlines infogas mellan utgående strängar. Ingen ny rad läggs till efter den sista utgående strängen.

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

### – PassThru

Returnerar ett objekt som representerar det tillagda innehållet. Som standard genererar denna cmdlet inga utdata.

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

### -Path

Anger sökvägen till de objekt som tar emot det ytterligare innehållet. Jokertecken är tillåtna. Om du anger flera sökvägar använder du kommatecken för att avgränsa Sök vägarna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Stream

Anger en alternativ data ström för innehåll. Om data strömmen inte finns skapar den här cmdleten den. Jokertecken stöds inte.

**Stream** är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` . Den här parametern fungerar bara i fil system enheter.

Du kan använda `Add-Content` cmdleten för att ändra innehållet i **zonen. unik identifierare** för den alternativa data strömmen. Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet. Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – UseTransaction

Inkluderar kommandot i den aktiva transaktionen. Den här parametern är bara giltig medan en transaktion pågår. Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Värde

Anger det innehåll som ska läggas till. Skriv en Citerad sträng, till exempel **den här informationen endast för intern användning** eller ange ett objekt som innehåller innehåll, till exempel det **datetime** -objekt som `Get-Date` genereras.

Du kan inte ange innehållet i en fil genom att ange dess sökväg, eftersom sökvägen bara är en sträng.
Du kan använda ett `Get-Content` kommando för att hämta innehållet och skicka det till **värde** parametern.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Object, system. Management. Automation. PSCredential

Du kan skicka pipe-värden, sökvägar eller autentiseringsuppgifter till `Set-Content` .

## UTDATA

### Ingen eller system. String

När du använder parametern **Passthru** `Add-Content` genererar ett **system. String** -objekt som representerar innehållet. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

När du rör ett objekt till `Add-Content` konverteras objektet till en sträng innan det läggs till i objektet. Objekt typen bestämmer sträng formatet, men formatet kan vara ett annat än standard visningen av objektet. Om du vill kontrol lera sträng formatet använder du formateringsegenskaperna för sändnings-cmdleten.

Du kan också referera till `Add-Content` med dess inbyggda alias `ac` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

`Add-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[Rensa innehåll](Clear-Content.md)

[Hämta innehåll](Get-Content.md)

[Hämta objekt](Get-Item.md)

[Nytt objekt](New-Item.md)

[Ange innehåll](Set-Content.md)
