---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FormatData
ms.openlocfilehash: 28eab1709de12ec5d391009aacccfd4e973a8b9b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708659"
---
# Get-FormatData

## SAMMANFATTNING
Hämtar formaterings data i den aktuella sessionen.

## SYNTAX

```
Get-FormatData [[-TypeName] <String[]>] [-PowerShellVersion <Version>] [<CommonParameters>]
```

## BESKRIVNING

`Get-FormatData`Cmdleten hämtar formateringen i den aktuella sessionen.

Formateringen i sessionen innehåller formatering av data från `Format.ps1xml` filer, till exempel i `$PSHOME` katalogen, formatering av data för moduler som du importerar till sessionen och hur du formaterar data för kommandon som du importerar i sessionen med hjälp av `Import-PSSession` cmdleten.

Du kan använda den här cmdleten för att undersöka formaterings data. Sedan kan du använda `Export-FormatData` cmdleten för att serialisera objekten, konvertera dem till XML och spara dem i `Format.ps1xml` filer.

Mer information om hur du formaterar filer i PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

## EXEMPEL

### Exempel 1: Hämta alla format data

Det här exemplet hämtar alla formaterings data i sessionen.

```powershell
Get-FormatData
```

### Exempel 2: Hämta formatering av data efter typnamn

Det här exemplet hämtar de format data objekt vars namn börjar med `System.Management.Automation.Cmd` .

```powershell
Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
```

### Exempel 3: granska formatering av data objekt

Det här exemplet visar hur du hämtar ett formaterat data objekt och granskar dess egenskaper.

```powershell
$F = Get-FormatData -TypeName 'System.Management.Automation.Cmd*'
$F
```

```Output
TypeName        FormatViewDefinition
--------        --------------------
HelpInfoShort   {help , TableControl}
```

```powershell
$F.FormatViewDefinition[0].control
```

```Output
Headers          : {System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader,
                   System.Management.Automation.TableControlColumnHeader}
Rows             : {System.Management.Automation.TableControlRow}
AutoSize         : False
HideTableHeaders : False
GroupBy          :
OutOfBand        : False
```

```powershell
$F.FormatViewDefinition[0].control.Headers
```

```Output
Label       Alignment Width
-----       --------- -----
CommandType Undefined    15
Name        Undefined    50
Version     Undefined    10
Source      Undefined     0
```

### Exempel 4: Hämta formatering av data och exportera dem

Det här exemplet visar hur du använder `Get-FormatData` och `Export-FormatData` för att exportera de format data som läggs till av en modul.

```powershell
$A = Get-FormatData
Import-Module bitstransfer
$B = Get-FormatData
Compare-Object $A $B
```

```Output
InputObject                                                SideIndicator
-----------                                                -------------
Microsoft.BackgroundIntelligentTransfer.Management.BitsJob =>
```

```powershell
Get-FormatData *bits* | Export-FormatData -FilePath c:\test\bits.format.ps1xml
Get-Content c:\test\bits.format.ps1xml
```

```Output
<?xml version="1.0" encoding="utf-8"?><Configuration><ViewDefinitions>
<View><Name>Microsoft.BackgroundIntelligentTransfer.Management.BitsJob</Name>
...
```

De första fyra kommandona använder `Get-FormatData` `Import-Module` `Compare-Object` cmdletarna, och för att identifiera den format typ som **BitsTransfer** -modulen lägger till i sessionen.

Det femte kommandot använder `Get-FormatData` cmdleten för att hämta den format typ som **BitsTransfer** -modulen lägger till. Den använder en pipeline-operator ( `|` ) för att skicka format typs objektet till `Export-FormatData` cmdleten, vilket konverterar tillbaka det till XML och sparar det i den angivna `format.ps1xml` filen.

Det sista kommandot visar ett utdrag av `format.ps1xml` fil innehållet.

### Exempel 5: Hämta formatering av data baserat på den angivna versionen av PowerShell

Det här exemplet visar hur du kan använda `Get-FormatData` för att hämta format data för ett angivet **TypeName** och en PowerShell-version.

```powershell
Get-FormatData -TypeName 'Microsoft.Powershell.Utility.FileHash' -PowerShellVersion $PSVersionTable.PSVersion

TypeNames                               FormatViewDefinition
---------                               --------------------
{Microsoft.Powershell.Utility.FileHash} {Microsoft.Powershell.Utility.FileHash}
```

## PARAMETRAR

### – PowerShellVersion

Ange den version av PowerShell som denna cmdlet hämtar för att formatera data. Ange ett tvåsiffrigt tal avgränsat med en punkt.

Den här parametern lades till i PowerShell 5,1 för att förbättra kompatibiliteten när fjärrdatorer som kör äldre versioner av PowerShell.

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeName

Anger typ namnen som denna cmdlet hämtar för att formatera data.
Ange typ namn.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. ExtendedTypeDefinition

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Exportera – FormatData](Export-FormatData.md)

[Uppdatera – FormatData](Update-FormatData.md)
