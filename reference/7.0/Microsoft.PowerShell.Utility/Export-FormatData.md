---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: d89d80b296d8800d65c5acfae37434e9b3f3bce9
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262898"
---
# Export-FormatData

## SAMMANFATTNING
Sparar formatering av data från den aktuella sessionen i en format fil.

## SYNTAX

### ByPath (standard)

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### ByLiteralPath

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## BESKRIVNING

`Export-FormatData`Cmdleten skapar PowerShell-formateringsattribut (format.ps1XML) från formateringselement i den aktuella sessionen. Det tar **ExtendedTypeDefinition** -objekt som `Get-FormatData` returnerar och sparar dem i en fil i XML-format.

PowerShell använder datan i att formatera filer (format.ps1XML) för att generera standard visningen av Microsoft .NET Framework-objekt i sessionen. Du kan visa och redigera formateringsattribut och använda Update-FormatData cmdlet för att lägga till formaterings data i en session.

Mer information om hur du formaterar filer i PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

## EXEMPEL

### Exempel 1: exportera session format data

```powershell
Get-FormatData -TypeName "*" -PowerShellVersion 5.1 | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

Detta kommando exporterar alla format data i sessionen till AllFormat.ps1XML-filen.

Kommandot använder `Get-FormatData` cmdleten för att hämta format data i sessionen. Värdet `*` (alla) för parametern **TypeName** dirigerar cmdleten för att hämta alla data i sessionen.

Kommandot använder en pipeline-operator ( `|` ) för att skicka format data från `Get-FormatData` kommandot till `Export-FormatData` cmdleten, som exporterar format data till AllFormat.ps1-filen.

`Export-FormatData`Kommandot använder parametern **IncludeScriptBlock** för att inkludera skript block i format data i filen.

### Exempel 2: exportera format data för en typ

```powershell
$F = Get-FormatData -TypeName "helpinfoshort" -PowerShellVersion 5.1
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

Dessa kommandon exporterar format data för **HelpInfoShort** -typen till Help.format.ps1XML-filen.

Det första kommandot använder `Get-FormatData` cmdleten för att hämta format data för **HelpInfoShort** -typen, och den sparas i `$F` variabeln.

Det andra kommandot använder cmdlet: en **InputObject** -parameter för `Export-FormatData` att ange de format data som sparats i `$F` variabeln. Den använder också parametern **IncludeScriptBlock** för att inkludera skript block i utdata.

### Exempel 3: exportera format data utan ett skript block

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" -PowerShellVersion 5.1 | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

Det här exemplet visar effekterna av att utelämna parametern **IncludeScriptBlock** från ett `Export-FormatData` kommando.

Det första kommandot använder `Get-FormatData` cmdleten för att hämta format data för objektet **system. Diagnostics. Process** som Get-Process cmdlet returnerar. Kommandot använder en pipeline-operator ( `|` ) för att skicka formaterings data till `Export-FormatData` cmdleten, som exporterar den till Process.format.ps1XML-fil i den aktuella katalogen.

I det här fallet `Export-FormatData` använder kommandot inte parametern **IncludeScriptBlock** .

Det andra kommandot använder `Update-FormatData` cmdleten för att lägga till Process.format.ps1XML-filen i den aktuella sessionen. Kommandot använder parametern **PrependPath** för att se till att formaterings data för process objekt i Process.format.ps1XML-filen hittas före standardformateringen för process objekt.

Det tredje kommandot visar effekterna av den här ändringen. Kommandot använder `Get-Process` cmdleten för att hämta processer som har namn som börjar med P. Utdata visar att egenskaps värden som beräknas med hjälp av skript block saknas i visningen.

## PARAMETRAR

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

### -IncludeScriptBlock

Anger om skript block i format data ska exporteras.

Eftersom skript block innehåller kod och kan användas på ett skadligt sätt exporteras de inte som standard.

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

### – InputObject

Anger det format data objekt som ska exporteras. Ange en variabel som innehåller objekten eller ett kommando som hämtar objekten, till exempel ett `Get-FormatData` kommando. Du kan också skicka objekt från `Get-FormatData` till `Export-FormatData` .

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger en plats för utdatafilen. Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Anger att cmdleten inte skriver över befintliga filer. Som standard `Export-FormatData` skriver överskrivna filer utan varning om inte filen har attributet skrivskyddad.

Om du vill dirigera `Export-FormatData` Skriv över skrivskyddade filer använder du parametern **Force** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger en plats för utdatafilen.
Ange en sökväg (valfritt) och fil namn med fil namns tillägget format.ps1XML.
Om du utelämnar sökvägen `Export-FormatData` skapas filen i den aktuella katalogen.

Om du använder ett fil namns tillägg som inte är. ps1xml `Update-FormatData` känner inte cmdleten igen filen.

Om du anger en befintlig fil `Export-FormatData` skrivs filen över utan varning, om inte filen har attributet skrivskyddad. Använd parametern **Force** om du vill skriva över en skrivskyddad fil. Använd parametern **NoClobber** om du vill förhindra att filer skrivs över.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. ExtendedTypeDefinition

Du kan skicka pipe- **ExtendedTypeDefinition** objekt från `Get-FormatData` till `Export-FormatData` .

## UTDATA

### Inget

`Export-FormatData` returnerar inga objekt.
Den genererar en fil och sparar den på den angivna sökvägen.

## ANTECKNINGAR

- Om du vill använda en format fil, inklusive en exporterad formatering, måste körnings principen för sessionen tillåta att skript och konfigurationsfiler körs. Mer information finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).

## RELATERADE LÄNKAR

[Get-FormatData](Get-FormatData.md)

[Uppdatera – FormatData](Update-FormatData.md)
