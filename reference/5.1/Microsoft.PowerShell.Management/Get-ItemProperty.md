---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266126"
---
# Get-ItemProperty

## SAMMANFATTNING
Hämtar egenskaperna för ett angivet objekt.

## SYNTAX

### Sökväg (standard)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING

`Get-ItemProperty`Cmdlet: en hämtar egenskaperna för de angivna objekten.
Du kan till exempel använda denna cmdlet för att hämta värdet för egenskapen LastAccessTime för ett fil objekt.
Du kan också använda denna cmdlet för att Visa register poster och deras värden.

## EXEMPEL

### Exempel 1: Hämta information om en angiven katalog

Det här kommandot hämtar information om katalogen "C:\Windows".

```powershell
Get-ItemProperty C:\Windows
```

### Exempel 2: Hämta egenskaperna för en enskild fil

Det här kommandot hämtar egenskaperna för filen "C:\Test\Weather.xls".
Resultatet är skickas till `Format-List` cmdleten för att visa utdata som en lista.

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### Exempel 3: Visa värde namnet och data för register poster i en register under nyckel

Det här kommandot visar värde namnet och data för alla register poster som finns i register under nyckeln "CurrentVersion".
Observera att kommandot kräver att det finns en PowerShell-enhet med namnet `HKLM:` som är mappad till registrerings data filen "HKEY_LOCAL_MACHINE" i registret.
En enhet med det namnet och mappningen är tillgänglig i PowerShell som standard.
Du kan också ange sökvägen till den här register under nyckeln med hjälp av följande alternativa sökväg som börjar med Providerns namn följt av två kolon:

"Registry:: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion".

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### Exempel 4: Hämta värde namn och data för en register post i en register under nyckel

Det här kommandot hämtar värde namnet och data för register posten "ProgramFilesDir" i register under nyckeln "CurrentVersion".
Kommandot använder parametern **Path** för att ange under nyckeln och parametern name för att ange värde namnet för posten.

Kommandot använder en bakgrunds-eller grav accent ( \` ), PowerShell-fortsättnings tecknen, för att fortsätta kommandot på den andra raden.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### Exempel 5: Hämta värde namn och data för register poster i en register nyckel

Det här kommandot hämtar värde namn och data för register posterna i register nyckeln "PowerShellEngine".
Resultatet visas i följande exempel på utdata.

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

### Exempel 6: Hämta, formatera och visa resultaten av register värden och data

Det här exemplet visar hur du formaterar utdata från ett `Get-ItemProperty` kommando i en lista för att göra det enkelt att se registervärdena och data och göra det enkelt att tolka resultaten.

Det första kommandot använder `Get-ItemProperty` cmdleten för att hämta register poster i **Microsoft. PowerShell** -undernyckeln.
Den här under nyckeln innehåller alternativ för standard gränssnittet för PowerShell.
Resultatet visas i följande exempel på utdata.

Utdata visar att det finns två register poster, "Path" och "ExecutionPolicy".
När en register nyckel innehåller färre än fem poster, visas den som standard i en tabell, men den är ofta enklare att visa i en lista.

Det andra kommandot använder samma `Get-ItemProperty` kommando.
Men den här gången använder kommandot en pipeline-operator ( `|` ) för att skicka kommandots resultat till `Format-List` cmdleten.
`Format-List`Kommandot använder egenskaps parametern med värdet * (all) för att visa alla egenskaper för objekten i en lista.
Resultatet visas i följande exempel på utdata.

Den resulterande visningen visar register posterna "Path" och "ExecutionPolicy", tillsammans med flera mindre välbekanta egenskaper för objektet i register nyckeln.
De andra egenskaperna, som har prefixet PS, är egenskaper för anpassade PowerShell-objekt, till exempel de objekt som representerar register nycklarna.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## PARAMETRAR

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.
Om du anger ett användar namn uppmanas du att ange ett lösen ord.

> [!WARNING]
> Den här parametern stöds inte av några providrar som installeras med Windows PowerShell.

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

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar från åtgärden.
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
Accept wildcard characters: False
```

### -Filter

Anger ett filter i formatet eller språket för providern.
Värdet för den här parametern kvalificerar parametern **Path** .

Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.
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

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.
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
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till egenskapens aktuella plats.
Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger namnet på egenskapen eller egenskaperna som ska hämtas.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till objektet eller objekten.

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

### – UseTransaction

Inkluderar kommandot i den aktiva transaktionen.
Den här parametern är bara giltig medan en transaktion pågår.
Mer information finns i inkluderar kommandot i den aktiva transaktionen.
Den här parametern är bara giltig medan en transaktion pågår.
Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till `Get-ItemProperty` .

## UTDATA

### System. Boolean, system. String, system. DateTime

`Get-ItemProperty` Returnerar ett objekt för varje objekt egenskap som det får.
Objekt typen beror på vilket objekt som hämtas.
I en fil system enhet kan det exempelvis returnera en fil eller mapp.

## ANTECKNINGAR

`Get-ItemProperty`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i sessionen skriver du " `Get-PSProvider` ". Mer information finns i about_Providers.

## RELATERADE LÄNKAR

[Clear-ItemProperty](Clear-ItemProperty.md)

[Kopiera – ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Byt namn – ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)
