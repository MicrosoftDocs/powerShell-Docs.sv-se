---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/convert-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-Path
ms.openlocfilehash: 3d39ea9498cec2669fa075d4630b7691671fea32
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709547"
---
# Convert-Path

## SAMMANFATTNING
Konverterar en sökväg från en PowerShell-sökväg till en PowerShell-providerns sökväg.

## SYNTAX

### Sökväg (standard)

```
Convert-Path [-Path] <String[]> [<CommonParameters>]
```

### LiteralPath

```
Convert-Path -LiteralPath <String[]> [<CommonParameters>]
```

## BESKRIVNING

`Convert-Path`Cmdleten konverterar en sökväg från en PowerShell-sökväg till en PowerShell-providerns sökväg.

## EXEMPEL

### Exempel 1: konvertera arbets katalogen till en standard fil system Sök väg

I det här exemplet konverteras den aktuella arbets katalogen, som representeras av en punkt ( `.` ), till en standard fil Sök väg.

```
PS C:\> Convert-Path .
C:\
```

### Exempel 2: konvertera en provider-sökväg till en standard register Sök väg

I det här exemplet konverteras PowerShell-providerns sökväg till en standard register Sök väg.

```powershell
PS C:\> Convert-Path HKLM:\Software\Microsoft
HKEY_LOCAL_MACHINE\Software\Microsoft
```

### Exempel 3: konvertera en sökväg till en sträng

I det här exemplet konverteras sökvägen till den aktuella providerns Hem Katalog, vilket är fil Systems leverantören, till en sträng.

```powershell
PS C:\> Convert-Path ~
C:\Users\User01
```

## PARAMETRAR

### -LiteralPath

Anger, som en sträng mat ris, den sökväg som ska konverteras. Värdet för parametern **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

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

Anger den PowerShell-sökväg som ska konverteras.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka en sökväg, men inte en literal sökväg, till denna cmdlet.

## UTDATA

### System. String

Den här cmdleten returnerar en sträng som innehåller den konverterade sökvägen.

## ANTECKNINGAR

Cmdlet: arna som innehåller sökvägen Substantiv ändrar Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka. De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format. Använd dem på samma sätt som du använder **logsdirectory**, **Normpath**, **realpath**, **Join** eller andra Sök vägs manipulerare.

Du kan använda Sök vägs-cmdlet: ar med flera providers, inklusive fil systemet system, register och certifikat leverantörer.

Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

`Convert-Path` konverterar bara befintliga sökvägar. Den kan inte användas för att konvertera en plats som ännu inte finns.

## RELATERADE LÄNKAR

[Anslut till sökväg](Join-Path.md)

[Lös-sökväg](Resolve-Path.md)

[Dela-sökväg](Split-Path.md)

[Test-sökväg](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

