---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/update-formatdata?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-FormatData
ms.openlocfilehash: 91d0274e485573de96d9960fa49f6d327156a79a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709414"
---
# Update-FormatData

## SAMMANFATTNING
Uppdaterar formaterings data i den aktuella sessionen.

## SYNTAX

```
Update-FormatData [[-AppendPath] <String[]>] [-PrependPath <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Update-FormatData`Cmdlet: en läser in formaterings data från att filerna formateras i den aktuella sessionen. Med den här cmdleten kan du uppdatera formaterings data utan att starta om PowerShell.

Utan parametrar `Update-FormatData` laddar om de filer som lästs in tidigare.
Du kan använda parametrarna för `Update-FormatData` för att lägga till nya filer i sessionen.

Filer formateras som textfiler i XML-format med `format.ps1xml` fil namns tillägget. Formaterings data i filerna definierar hur Microsoft .NET Ramverks objekt i sessionen.

När PowerShell startar läses format data in från PowerShell-källkoden. Du kan dock skapa anpassade format.ps1XML-filer för att uppdatera formateringen i den aktuella sessionen. Du kan använda `Update-FormatData` för att läsa in formaterings data i den aktuella sessionen utan att starta om PowerShell. Detta är användbart när du har lagt till eller ändrat en format fil, men inte vill avbryta sessionen.

Mer information om hur du formaterar filer i PowerShell finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).

## EXEMPEL

### Exempel 1: Läs in tidigare inlästa filer igen

```powershell
Update-FormatData
```

Det här kommandot laddar om de filer som lästes in tidigare.

### Exempel 2: läsa in filer för formatering och spåra och logga formatering

```powershell
Update-FormatData -AppendPath "trace.format.ps1xml, log.format.ps1xml"
```

Detta kommando laddar om filerna till sessionen, inklusive två nya filer, Trace.format.ps1XML och Log.format.ps1XML.

Eftersom kommandot använder parametern **AppendPath** läses formateringen i de nya filerna in efter formateringen från de inbyggda filerna.

Parametern **AppendPath** används eftersom de nya filerna innehåller formaterings data för objekt som inte refereras till i de inbyggda filerna.

### Exempel 3: redigera en fil format och Läs in den igen

```powershell
Update-FormatData -PrependPath "c:\test\NewFiles.format.ps1xml"

# Edit the NewFiles.format.ps1 file.

Update-FormatData
```

Det här exemplet visar hur du läser in en fil format igen när du har redigerat den.

Det första kommandot lägger till NewFiles.format.ps1XML-filen i sessionen. Parametern **PrependPath** används eftersom filen innehåller format data för objekt som refereras till i de inbyggda filerna.

När du har lagt till NewFiles.format.ps1XML-filen och testat den i dessa sessioner redigerar författaren filen.

Det andra kommandot använder `Update-FormatData` cmdleten för att läsa in formateringsattribut igen. Eftersom NewFiles.format.ps1XML-filen tidigare lästes `Update-FormatData` in igen, laddar den automatiskt om den utan att använda parametrar.

## PARAMETRAR

### -AppendPath

Anger formateringsattribut som denna cmdlet lägger till i sessionen. Filerna läses in efter att PowerShell har läst in de inbyggda filerna.

När .NET-objekt formateras, använder PowerShell den första format definition som hittas för varje .NET-typ. Om du använder parametern **AppendPath** söker PowerShell igenom data från de inbyggda filerna innan de påträffar de format data som du lägger till.

Använd den här parametern för att lägga till en fil som formaterar ett .NET-objekt som inte refereras till i de inbyggda filerna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -PrependPath

Anger formateringsattribut som denna cmdlet lägger till i sessionen. Filerna läses in innan PowerShell läser in de inbyggda filerna.

När .NET-objekt formateras, använder PowerShell den första format definition som hittas för varje .NET-typ. Om du använder parametern **PrependPath** söker PowerShell igenom data från filerna som du lägger till innan de påträffar formaterings data från de inbyggda filerna.

Använd den här parametern för att lägga till en fil som formaterar ett .NET-objekt som också refereras till i de inbyggda filerna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

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

### -WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

### System. String

Du kan lägga till en sträng som innehåller sökvägen till `Update-FormatData` .

## UTDATA

### Inga

Cmdleten returnerar inga utdata.

## ANTECKNINGAR

- `Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler. Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon. Du behöver inte importera modulen igen.

## RELATERADE LÄNKAR

[Get-FormatData](Get-FormatData.md)

[Exportera – FormatData](Export-FormatData.md)
