---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 308aee6f58443bb4e1e3d9751e7bd421b8072d8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709541"
---
# Clear-Content

## SAMMANFATTNING
Tar bort innehållet i ett objekt, men tar inte bort objektet.

## SYNTAX

### Sökväg (standard)

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### LiteralPath

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## BESKRIVNING

`Clear-Content`Cmdleten tar bort innehållet i ett objekt, t. ex. att ta bort texten från en fil, men objektet tas inte bort.
Därför finns objektet, men det är tomt.
`Clear-Content`Liknar `Clear-Item` , men den fungerar på objekt med innehåll, i stället för objekt med värden.

## EXEMPEL

### Exempel 1: ta bort allt innehåll från en katalog

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

Det här kommandot tar bort allt innehåll från "init.txt"-filer i alla under kataloger i SmpUsers-katalogen.
Filerna tas inte bort, men de är tomma.

### Exempel 2: ta bort innehållet för alla filer med ett jokertecken

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

Det här kommandot tar bort innehållet i alla filer i den aktuella katalogen med fil namns tillägget ". log", inklusive filer med attributet skrivskyddad.
Asterisken ( \* ) i sökvägen representerar alla objekt i den aktuella katalogen.
**Force** -parametern gör kommandot effektivt på skrivskyddade filer.
Om du använder ett filter för att begränsa kommandot till filer med fil namns tillägget. log i stället för att ange \* . log i sökvägen gör åtgärden snabbare.

### Exempel 3: Rensa alla data från en ström

Det här exemplet visar hur `Clear-Content` cmdleten rensar innehållet från en alternativ data ström och låter strömmen vara intakt.

Det första kommandot använder `Get-Content` cmdleten för att hämta innehållet i zonen. identifierarens data ström i den Copy-Script.ps1 filen som hämtades från Internet.

Det andra kommandot använder `Clear-Content` cmdleten för att rensa innehållet.

Det tredje kommandot upprepar det första kommandot. Den verifierar att innehållet är rensat, men data strömmen är kvar. Om strömmen har tagits bort genererar kommandot ett fel.

Du kan använda en metod som den här för att rensa innehållet i en alternativ data ström. Det är dock inte det rekommenderade sättet att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet. Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## PARAMETRAR

### -Stream

Anger en alternativ data ström för innehåll.
Om data strömmen inte finns skapar den här cmdleten den.
Jokertecken stöds inte.

Stream är en dynamisk parameter som fil Systems leverantören lägger till i `Clear-Content` .
Den här parametern fungerar bara i fil system enheter.

Du kan använda `Clear-Content` cmdleten för att ändra innehållet i zonen. unik identifierare för den alternativa data strömmen.
Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.
Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.

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

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell. Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du Invoke-Command.

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

Anger, som en sträng mat ris, strängar som denna cmdlet utelämnar från sökvägen till innehållet.
Värdet för den här parametern kvalificerar parametern **Path** .
Ange ett Sök vägs element eller ett mönster, till exempel "*. txt".
Jokertecken är tillåtna.

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

Anger ett filter i providerns format eller språk.
Värdet för den här parametern kvalificerar parametern **Path** .
Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.
Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.

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

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

Anger, som en sträng mat ris, innehåll som denna cmdlet rensar.
Värdet för den här parametern kvalificerar parametern **Path** .
Ange ett Sök vägs element eller ett mönster, till exempel "*. txt".
Jokertecken är tillåtna.

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

Anger sökvägar till objekten som innehållet tas bort från.
Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken ser till att PowerShell inte tolkar några tecken som escape-sekvenser.

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

Anger sökvägar till objekten som innehållet tas bort från.
Jokertecken är tillåtna.
Sök vägarna måste vara sökvägar till objekt, inte behållare.
Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.
Jokertecken är tillåtna.
Den här parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.

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

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inga

Det går inte att skicka pipe-objekt till `Clear-Content` .

## UTDATA

### Inga

Denna cmdlet returnerar inga objekt.

## ANTECKNINGAR

Du kan använda `Clear-Content` med PowerShell-filsystem-providern och med andra leverantörer som hanterar innehåll.
Om du vill rensa objekt som inte anses vara innehåll, till exempel objekt som hanteras av PowerShell-certifikatet eller register leverantörer, använder du `Clear-Item` .

`Clear-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.
Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .
Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Lägg till innehåll](Add-Content.md)

[Hämta innehåll](Get-Content.md)

[Hämta objekt](Get-Item.md)

[Ange innehåll](Set-Content.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

