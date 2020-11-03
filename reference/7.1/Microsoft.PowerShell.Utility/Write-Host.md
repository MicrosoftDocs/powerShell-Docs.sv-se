---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 47a4d9bb66e3e6c3267bbdf18f41c8af8e5448f0
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2020
ms.locfileid: "93269498"
---
# Write-Host

## SAMMANFATTNING

Skriver anpassade utdata till en värd.

## SYNTAX

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## BESKRIVNING

`Write-Host`Cmdletens primära syfte är att producera för-(värd) – endast visning av utdata, till exempel att skriva ut färgad text, t. ex. när användaren uppmanas att ange indata tillsammans med [Read-Host](Read-Host.md).
`Write-Host` använder metoden [toString ()](/dotnet/api/system.object.tostring) för att skriva utdata. Om du däremot vill mata ut data till pipelinen kan du använda [Write-output](Write-Output.md) eller implicit utdata.

Du kan ange färg på text med hjälp av `ForegroundColor` parametern och du kan ange bakgrunds färgen med hjälp av `BackgroundColor` parametern. Med parametern avgränsning kan du ange en sträng som ska användas för att separera visade objekt. Det specifika resultatet beror på vilket program som är värd för PowerShell.

> [!NOTE]
> Från och med Windows PowerShell 5,0 `Write-Host` är en omslutning som `Write-Information` gör att du kan använda `Write-Host` för att generera utdata till informations strömmen. Detta gör det möjligt att **samla in** eller **undertrycka** data som skrivits med samtidigt som du `Write-Host` behåller bakåtkompatibilitet.
>
> `$InformationPreference`Variabeln Preference och `InformationAction` common parameter påverkar inte `Write-Host` meddelanden. Undantaget till den här regeln är `-InformationAction Ignore` , vilket förhindrar `Write-Host` utdata. (se "exempel 5")

## EXEMPEL

### Exempel 1: Skriv till konsolen utan att lägga till en ny rad

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

Det här kommandot visar strängen "inget rad matnings test" med `NoNewline` parametern.

En andra sträng skrivs, men den avslutas på samma rad som första gången på grund av att en ny rad avgränsar strängarna.

### Exempel 2: Skriv till konsolen och ta med en avgränsare

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Det här kommandot visar de jämna talen från två till tolv. **Avgränsnings** parametern används för att lägga till strängen `, +2= ` (komma, blank steg,,,, `+` `2` `=` blank steg).

### Exempel 3: skriva med olika text-och bakgrunds färger

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

Det här kommandot visar de jämna talen från två till tolv. Den använder `ForegroundColor` parametern för att mata ut mörkt grönt text och `BackgroundColor` parametern för att visa en vit bakgrund.

### Exempel 4: skriva med olika text-och bakgrunds färger

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

Det här kommandot visar strängen "röd på vit text". Texten är röd, som definieras av `ForegroundColor` parametern. Bakgrunden är vit, som definieras av `BackgroundColor` parametern.

### Exempel 5: Ignorera utdata från Write-Host

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

Dessa kommandon undertrycker effektivt utdata från `Write-Host` cmdleten. Den första använder `InformationAction` parametern med `Ignore` värdet för att ignorera utdata till informations strömmen.
I det andra exemplet omdirigeras informations strömmen för kommandot till `$null` variabeln och därmed ignoreras den.

## PARAMETRAR

### – BackgroundColor

Anger bakgrunds färgen. Det finns inget standardvärde. De acceptabla värdena för den här parametern är:

- Svart
- DarkBlue
- DarkGreen
- DarkCyan
- DarkRed
- DarkMagenta
- DarkYellow
- Mörkgrå
- DarkGray
- Blå
- Green
- Cyan
- Röd
- Röda
- Gul
- Vit

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForegroundColor

Anger text färgen. Det finns inget standardvärde. De acceptabla värdena för den här parametern är:

- Svart
- DarkBlue
- DarkGreen
- DarkCyan
- DarkRed
- DarkMagenta
- DarkYellow
- Mörkgrå
- DarkGray
- Blå
- Green
- Cyan
- Röd
- Röda
- Gul
- Vit

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – NoNewline

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

### – Objekt

Objekt som ska visas på värden.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Avgränsare

Anger en avgränsnings sträng som ska infogas mellan objekt som visas av värden.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Object

Du kan skicka pipe-objekt som ska skrivas till värden.

## UTDATA

### Inget

`Write-Host` skickar objekten till värden. Det returnerar inga objekt. Värden visar dock de objekt som `Write-Host` skickar till den.

## ANTECKNINGAR

- När en samling skrivs till värden skrivs elementen i samlingen ut på samma rad, separerade med ett enda blank steg. Detta kan åsidosättas med **avgränsnings** parametern.

- Icke-primitiva data typer, till exempel objekt med egenskaper kan orsaka oväntade resultat och ger inte meningsfulla utdata. Skrivs till exempel `Write-Host @{a = 1; b = 2}` `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` till värden.

## RELATERADE LÄNKAR

[Rensa värd](../Microsoft.PowerShell.Core/Clear-Host.md)

[Ut-värd](../Microsoft.PowerShell.Core/Out-Host.md)

[Skriv-debug](Write-Debug.md)

[Skriv-fel](Write-Error.md)

[Skriva-utdata](Write-Output.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)

[Skriv varning](Write-Warning.md)
