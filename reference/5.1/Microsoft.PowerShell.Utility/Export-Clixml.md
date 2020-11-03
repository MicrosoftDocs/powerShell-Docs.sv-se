---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-clixml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Clixml
ms.openlocfilehash: 8485591165cce0425c85d52fbd31d40614af6249
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265113"
---
# Export-Clixml

## SAMMANFATTNING
Skapar en XML-baserad representation av ett objekt eller objekt och lagrar det i en fil.

## SYNTAX

### ByPath (standard)

```
Export-Clixml [-Path] <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Clixml -LiteralPath <String> -InputObject <PSObject> [-Depth <Int32>] [-Force] [-NoClobber]
 [-Encoding <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Export-Clixml`Cmdlet: en skapar en XML-baserad representation av ett objekt eller objekt och lagrar den i en fil. Du kan sedan använda `Import-Clixml` cmdleten för att återskapa det sparade objektet baserat på innehållet i filen.
Mer information om CLI finns i [språk oberoende](/dotnet/standard/language-independence).

Denna cmdlet liknar `ConvertTo-Xml` , förutom att den kommer att `Export-Clixml` lagra XML i en fil. `ConvertTo-XML` Returnerar XML, så du kan fortsätta att bearbeta den i PowerShell.

En värdefull användning av `Export-Clixml` Windows-datorer är att exportera autentiseringsuppgifter och säkra strängar på ett säkert sätt till XML. Ett exempel finns i exempel 3.

## EXEMPEL

### Exempel 1: exportera en sträng till en XML-fil

I det här exemplet skapas en XML-fil som lagras i den aktuella katalogen, en representation av strängen som **Detta är ett test**.

```powershell
"This is a test" | Export-Clixml -Path .\sample.xml
```

Strängen som **Detta är ett test** skickas ned i pipelinen. `Export-Clixml` använder parametern **Path** för att skapa en XML-fil med namnet `sample.xml` i den aktuella katalogen.

### Exempel 2: exportera ett objekt till en XML-fil

Det här exemplet visar hur du exporterar ett objekt till en XML-fil och sedan skapar ett objekt genom att importera XML-filen från filen.

```powershell
Get-Acl C:\test.txt | Export-Clixml -Path .\FileACL.xml
$fileacl = Import-Clixml -Path .\FileACL.xml
```

`Get-Acl`Cmdlet: en hämtar filens säkerhets Beskrivning `Test.txt` . Det skickar objektet nedåt i pipelinen för att skicka säkerhets beskrivningen till `Export-Clixml` . XML-baserad representation av objektet lagras i en fil med namnet `FileACL.xml` .

`Import-Clixml`Cmdleten skapar ett objekt från XML-filen i `FileACL.xml` filen. Sedan sparas objektet i `$fileacl` variabeln.

### Exempel 3: kryptera ett exporterat Credential-objekt

I det här exemplet har du fått en autentiseringsuppgift som du har lagrat i `$Credential` variabeln genom `Get-Credential` att köra cmdleten, så du kan köra `Export-Clixml` cmdleten för att spara autentiseringsuppgifterna på disken.

> [!IMPORTANT]
> `Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows. På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som oformaterad text.

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

`Export-Clixml`Cmdleten krypterar Credential-objekt med hjälp av Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).
Krypteringen säkerställer att endast ditt användar konto på den datorn kan dekryptera innehållet i Credential-objektet. Den exporterade `CLIXML` filen kan inte användas på en annan dator eller av en annan användare.

I exemplet representeras filen där autentiseringsuppgiften lagras av `TestScript.ps1.credential` . Ersätt **TestScript** med namnet på skriptet som du läser in autentiseringsuppgiften med.

Du skickar Credential-objektet ned till pipelinen till `Export-Clixml` och sparar det på den sökväg, `$Credxmlpath` som du angav i det första kommandot.

Kör de sista två kommandona om du vill importera autentiseringsuppgiften automatiskt till ditt skript. Kör `Import-Clixml` för att importera det skyddade objektet Credential till skriptet. Den här importen eliminerar risken att exponera lösen ord i klartext i skriptet.

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

### -Djup

Anger hur många nivåer med objekt som ingår i XML-representationen. Standardvärdet är `2`.

Standardvärdet kan åsidosättas av objekt typen i `Types.ps1xml` filerna. Mer information finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är **Unicode**.

De acceptabla värdena för den här parametern är följande:

- `ASCII` Använder ASCII-teckenuppsättning (7-bitars).
- `BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.
- `Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).
- `OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.
- `Unicode` Använder UTF-16 med en liten-endian-order.
- `UTF7` Använder UTF-7.
- `UTF8` Använder UTF-8.
- `UTF32` Använder UTF-32 med en liten-endian-order.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

Gör att cmdleten tar bort det skrivskyddade attributet för utdatafilen om det behövs. Cmdleten försöker återställa det skrivskyddade attributet när kommandot har slutförts.

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

### – InputObject

Anger det objekt som ska konverteras. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan också skicka pipe-objekt till `Export-Clixml` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till filen där XML-representationen av objektet kommer att lagras. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Anger att cmdleten inte skriver över innehållet i en befintlig fil. Om en fil finns på den angivna sökvägen skrivs filen som standard `Export-Clixml` utan varning.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till filen där XML-representationen av objektet kommer att lagras.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan pipelina ett objekt till `Export-Clixml` .

## UTDATA

### System. IO. FileInfo

`Export-Clixml` skapar en fil som innehåller XML.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[ConvertTo-Html](ConvertTo-Html.md)

[ConvertTo-Xml](ConvertTo-Xml.md)

[Exportera-CSV](Export-Csv.md)

[Importera – CliXml](Import-Clixml.md)

[Anslut till sökväg](../Microsoft.PowerShell.Management/Join-Path.md)

[Lagra autentiseringsuppgifter på ett säkert sätt på disken](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[Använd PowerShell för att skicka autentiseringsuppgifter till äldre system](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

[Windows. Security. Cryptography. DataProtection](/uwp/api/windows.security.cryptography.dataprotection)
