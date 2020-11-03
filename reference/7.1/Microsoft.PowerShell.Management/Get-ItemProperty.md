---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: dafcd7fadcf73c705158bff119ddd8a59d684c8b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263870"
---
# Get-ItemProperty

## SAMMANFATTNING
Hämtar egenskaperna för ett angivet objekt.

## SYNTAX

### Sökväg (standard)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [<CommonParameters>]
```

## BESKRIVNING

`Get-ItemProperty`Cmdlet: en hämtar egenskaperna för de angivna objekten.
Du kan till exempel använda denna cmdlet för att hämta värdet för egenskapen LastAccessTime för ett fil objekt. Du kan också använda denna cmdlet för att Visa register poster och deras värden.

## EXEMPEL

### Exempel 1: Hämta information om en angiven katalog

Det här kommandot hämtar information om `C:\Windows` katalogen.

```powershell
Get-ItemProperty C:\Windows
```

### Exempel 2: Hämta egenskaperna för en enskild fil

Det här kommandot hämtar `C:\Test\Weather.xls` filens egenskaper.
Resultatet är skickas till `Format-List` cmdleten för att visa utdata som en lista.

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### Exempel 3: Visa värde namnet och data för register poster i en register under nyckel

Det här kommandot visar värde namnet och data för alla register poster som finns i register under nyckeln "CurrentVersion".

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

> [!NOTE]
> Det här kommandot kräver att det finns en PowerShell-enhet med namnet `HKLM:` som är mappad till registrerings data filen "HKEY_LOCAL_MACHINE" i registret.
>
> En enhet med det namnet och mappningen är tillgänglig i PowerShell som standard.
> Du kan också ange sökvägen till den här register under nyckeln med hjälp av följande alternativa sökväg som börjar med Providerns namn följt av två kolon:
>
> `Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

### Exempel 4: Hämta värde namn och data för en register post i en register under nyckel

Det här kommandot hämtar värde namnet och data för register posten "ProgramFilesDir" i register under nyckeln "CurrentVersion".
**Sökvägen** anger under nyckeln och parametern **Name** anger värde namnet för posten.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### Exempel 5: Hämta värde namn och data för register poster i en register nyckel

Det här kommandot hämtar värde namn och data för register posterna i register nyckeln "PowerShellEngine". Resultatet visas i följande exempel på utdata.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

## PARAMETRAR

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Undanta

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna. Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter. Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.

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

### -Inkludera

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` . Jokertecken är tillåtna. Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

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

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

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

### -Name

Anger namnet på egenskapen eller egenskaperna som ska hämtas.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Anger sökvägen till objektet eller objekten.
Jokertecken är tillåtna.

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

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till `Get-ItemProperty` .

## UTDATA

### System. Boolean, system. String, system. DateTime

`Get-ItemProperty` Returnerar ett objekt för varje objekt egenskap som det får. Objekt typen beror på vilket objekt som hämtas. I en fil system enhet kan det exempelvis returnera en fil eller mapp.

## ANTECKNINGAR

`Get-ItemProperty`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Clear-ItemProperty](Clear-ItemProperty.md)

[Kopiera – ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Byt namn – ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

