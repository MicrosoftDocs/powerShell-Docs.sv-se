---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resolve-path?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resolve-Path
ms.openlocfilehash: 7e88e873c5c6aa0733869cdaaf1fba583468261d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263822"
---
# Resolve-Path

## SAMMANFATTNING
Matchar jokertecken i en sökväg och visar Sök vägs innehållet.

## SYNTAX

### Sökväg (standard)

```
Resolve-Path [-Path] <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Resolve-Path -LiteralPath <String[]> [-Relative] [-Credential <PSCredential>] [<CommonParameters>]
```

## BESKRIVNING

`Resolve-Path`Cmdleten visar de objekt och behållare som matchar jokertecken på den angivna platsen. Matchningen kan innehålla filer, mappar, register nycklar eller andra objekt som är tillgängliga från en PSDrive-Provider.

## EXEMPEL

### Exempel 1: matcha Arbetsmappens sökväg

Tilde-tecknet (~) är en kort SKRIFTS notation för den aktuella användarens arbetsmapp. I det här exemplet visas `Resolve-Path` det fullständiga värdet för sökvägen som returneras.

```powershell
PS C:\> Resolve-Path ~
```

```Output
Path
----
C:\Users\User01
```

### Exempel 2: matcha sökvägen till Windows-mappen

```powershell
PS C:\> Resolve-Path -Path "windows"
```

```Output
Path
----
C:\Windows
```

När det körs från roten på C:-enheten returnerar det här kommandot sökvägen till Windows-mappen på enheten C:.

### Exempel 3: Hämta alla sökvägar i Windows-mappen

```powershell
PS C:\> "C:\windows\*" | Resolve-Path
```

Det här kommandot returnerar alla mappar i mappen C:\Windows. Kommandot använder en pipeline-operator (|) för att skicka en Sök vägs sträng till `Resolve-Path` .

### Exempel 4: matcha en UNC-sökväg

```powershell
PS C:\> Resolve-Path -Path "\\Server01\public"
```

Det här kommandot löser en Universal Naming Convention-sökväg (UNC) och returnerar resurserna i sökvägen.

### Exempel 5: Hämta relativa sökvägar

```powershell
PS C:\> Resolve-Path -Path "c:\prog*" -Relative
```

```Output
.\Program Files
.\Program Files (x86)
.\programs.txt
```

Det här kommandot returnerar relativa sökvägar för katalogerna i roten på enheten C:.

### Exempel 6: matcha en sökväg som innehåller hakparenteser

I det här exemplet används parametern **LiteralPath** för att matcha sökvägen till \[ undermappen test-XML \] .
Om du använder **LiteralPath** behandlas hakparenteserna som vanliga tecken i stället för ett reguljärt uttryck.

```powershell
PS C:\> Resolve-Path -LiteralPath 'test[xml]'
```

## PARAMETRAR

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller skicka ett **PSCredential** -objekt. Du kan skapa ett **PSCredential** -objekt med hjälp av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Den här parametern stöds inte av några providrar som installeras med PowerShell.

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

### -LiteralPath

Anger den sökväg som ska matchas. Värdet för parametern **LiteralPath** används precis som det skrivs. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

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

Anger PowerShell-sökvägen som ska lösas. Den här parametern är obligatorisk. Du kan också skicka en Sök vägs sträng till `Resolve-Path` . Jokertecken är tillåtna.

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

### – Relativ

Anger att denna cmdlet returnerar en relativ sökväg.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### System. Management. Automation. PathInfo, system. String

Returnerar ett **PathInfo** -objekt. Returnerar ett sträng värde för den matchade sökvägen om du anger en **relativ** parameter.

## ANTECKNINGAR

`*-Path`Cmdletarna fungerar med fil systemet system, register och certifikat.

`Resolve-Path` är utformad för att fungera med alla providrar. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_providers](../microsoft.powershell.core/about/about_providers.md).

`Resolve-Path` matchar bara befintliga sökvägar. Det går inte att använda den för att lösa en plats som ännu inte finns.

## RELATERADE LÄNKAR

[Konvertera-sökväg](Convert-Path.md)

[Anslut till sökväg](Join-Path.md)

[Dela-sökväg](Split-Path.md)

[Test-sökväg](Test-Path.md)
