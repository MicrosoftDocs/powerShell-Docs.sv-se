---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 4189201cd373d29e8ea8e88441376e0df902742e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263307"
---
# Join-Path

## SAMMANFATTNING
Kombinerar en sökväg och en underordnad sökväg till en enda sökväg.

## SYNTAX

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## BESKRIVNING

`Join-Path`Cmdleten kombinerar en sökväg och en underordnad sökväg till en enda sökväg.
Providern tillhandahåller Sök vägs avgränsare.

## EXEMPEL

### Exempel 1: kombinera en sökväg med en underordnad sökväg

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

Det här kommandot använder `Join-Path` för att kombinera en sökväg med en childpath.

Eftersom kommandot körs från `FileSystem` providern, är det den `\` avgränsare som ska användas för att ansluta Sök vägarna.

### Exempel 2: kombinera sökvägar som redan innehåller katalog avgränsare

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

Befintliga katalog avgränsare `\` och hanterade så det finns bara en avgränsare mellan `Path` och `ChildPath`

### Exempel 3: Visa filer och mappar genom att koppla en sökväg med en underordnad sökväg

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

Det här kommandot visar de filer och mappar som refereras till genom att ansluta till C:\Win- \* sökvägen och den \* underordnade system Sök vägen.
Den visar samma filer och mappar som `Get-ChildItem` , men visar den fullständigt kvalificerade sökvägen till varje objekt.
I det här kommandot `Path` `ChildPath` utelämnas de valfria parameter namnen.

### Exempel 4: Använd Join-Path med PowerShell-dataprovidern

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

Det här kommandot visar register nycklarna i `HKLM\System` register under nyckeln som innehåller `ControlSet` .

`Resolve`Parametern försöker matcha den anslutna sökvägen, inklusive jokertecken från den aktuella providerns sökväg`HKLM:\`

### Exempel 5: kombinera flera Sök vägs rötter med en underordnad sökväg

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

Det här kommandot använder `Join-Path` för att kombinera flera Sök vägs rötter med en underordnad sökväg.

> [!NOTE]
> De enheter som anges av `Path` måste finnas eller så går det inte att ansluta till posten.

### Exempel 6: kombinera rötter för en fil system enhet med en underordnad sökväg

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

Detta kommando kombinerar rötter för varje PowerShell-fil system enhet i-konsolen med den underordnade Underkat-sökvägen.

Kommandot använder `Get-PSDrive` cmdleten för att hämta de PowerShell-enheter som stöds av fil tjänst leverantören.
`ForEach-Object`Instruktionen väljer bara rot egenskapen för `PSDriveInfo` objekten och kombinerar den med den angivna underordnade sökvägen.

Utdata visar att PowerShell-enheterna på datorn innehåller en enhet som är mappad till katalogen C:\Programs.

### Exempel 7: kombinera ett obestämt antal sökvägar

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

`AdditionalChildPath`Parametern gör det möjligt att ansluta till ett obegränsat antal sökvägar.

I det här exemplet används inga parameter namn, vilket innebär att "a" binder till `Path` , "b" till `ChildPath` och "c-g" till `AdditionalChildPath`

## PARAMETRAR

### -AdditionalChildPath

Anger ytterligare element som ska läggas till i värdet för parametern *Path* . `ChildPath`Parametern är fortfarande obligatorisk och måste också anges.

Den här parametern anges med `ValueFromRemainingArguments` egenskapen som gör det möjligt att ansluta till ett obestämt antal sökvägar.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ChildPath

Anger de element som ska läggas till i `Path` parameterns värde.
Jokertecken är tillåtna.
`ChildPath`Parametern är obligatorisk, men parameter namnet ("ChildPath") är valfritt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger den huvud Sök väg (eller sökvägar) som den underordnade sökvägen ska läggas till i.
Jokertecken är tillåtna.

Värdet för `Path` avgör vilken provider som ansluter till Sök vägarna och lägger till Sök vägs avgränsare.
`Path`Parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Lös

Anger att denna cmdlet ska försöka matcha den anslutna sökvägen från den aktuella providern.

- Om jokertecken används, returnerar cmdleten alla sökvägar som matchar den anslutna sökvägen.
- Om **inga** jokertecken används, kommer cmdleten att fel om sökvägen inte finns.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### System. String

Denna cmdlet returnerar en sträng som innehåller den resulterande sökvägen.

## ANTECKNINGAR

Cmdlet: arna som innehåller sökvägen Substantiv (Sök vägs-cmdletar) ändrar Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka. De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format. Använd dem på samma sätt som du använder Logsdirectory, Normpath, realpath, JOIN eller andra Sök vägs manipulerare.

Du kan använda Sök vägs-cmdlet: ar med flera providers, inklusive `FileSystem` -, `Registry` -och- `Certificate` providers.

Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.
Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .
Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Konvertera-sökväg](Convert-Path.md)

[Lös-sökväg](Resolve-Path.md)

[Dela-sökväg](Split-Path.md)

[Test-sökväg](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)

