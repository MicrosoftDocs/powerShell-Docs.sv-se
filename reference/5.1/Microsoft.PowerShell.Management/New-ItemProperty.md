---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 2569f4778f54f6cdad22e10cf92e727b73c323e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265526"
---
# New-ItemProperty

## SAMMANFATTNING
Skapar en ny egenskap för ett objekt och anger dess värde.

## SYNTAX

### Sökväg (standard)

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING

`New-ItemProperty`Cmdleten skapar en ny egenskap för ett angivet objekt och anger dess värde.
Normalt används denna cmdlet för att skapa nya register värden, eftersom register värden är egenskaper för ett register nyckel objekt.

Denna cmdlet lägger inte till egenskaper till ett objekt.

- Använd cmdleten om du vill lägga till en egenskap till en instans av ett objekt `Add-Member` .
- Om du vill lägga till en egenskap för alla objekt av en viss typ ändrar du Types.ps1XML-filen.

## EXEMPEL

### Exempel 1: Lägg till en register post

Det här kommandot lägger till en ny register post, "NoOfEmployees", till nyckeln "företaget" i "HKLM: \ program registrerings data".

Det första kommandot använder parametern **Path** för att ange sökvägen till register nyckeln "företaget".
Parametern **Name** används för att ange ett namn för posten och **värde** parametern för att ange dess värde.

Det andra kommandot använder `Get-ItemProperty` cmdleten för att se den nya register posten.

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### Exempel 2: lägga till en register post i en nyckel

Detta kommando lägger till en ny register post i en register nyckel. För att ange nyckeln använder den en pipeline-operator (|) för att skicka ett objekt som representerar nyckeln till `New-ItemProperty` .

Den första delen av kommandot använder `Get-Item` cmdleten för att hämta register nyckeln "företaget". Pipeline-operatorn skickar resultatet från kommandot till `New-ItemProperty` , som lägger till den nya register posten ("NoOfLocations") och dess värde (3) till nyckeln "företaget".

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

Det här kommandot fungerar eftersom funktionen parameter-binding i Windows PowerShell associerar sökvägen till det `RegistryKey` objekt som `Get-Item` returneras med **LiteralPath** -parametern för `New-ItemProperty` . Mer information finns i [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).

### Exempel 3: skapa ett multisträng-värde i registret med hjälp av en Here-String

I det här exemplet skapas ett multisträng värde med hjälp av en här-sträng.

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### Exempel 4: skapa ett multisträng-värde i registret med hjälp av en matris

Exemplet visar hur du använder en matris med värden för att skapa `MultiString` värdet.

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## PARAMETRAR

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord.

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

Anger, som en sträng mat ris, en egenskap eller egenskap som denna cmdlet exkluderar från åtgärden.
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

Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern. Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.

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

### -Force

Tvingar cmdleten att skapa en egenskap för ett objekt som annars inte kan kommas åt av användaren.
Implementeringen varierar från providern till providern.
Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

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

Anger ett namn för den nya egenskapen.
Om egenskapen är en register post anger den här parametern namnet på posten.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger objektets sökväg.
Den här parametern identifierar objektet som den här cmdleten lägger till den nya egenskapen i.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PropertyType

Anger vilken typ av egenskap som denna cmdlet lägger till.
De acceptabla värdena för den här parametern är:

- **Sträng** : anger en null-avslutad sträng. Motsvarar **REG_SZ**.
- **ExpandString** : anger en null-avslutad sträng som innehåller expanderade referenser till miljövariabler som expanderas när värdet hämtas. Motsvarar **REG_EXPAND_SZ**.
- **Binary** : anger binära data i alla former. Motsvarar **REG_BINARY**.
- **DWORD** : anger ett 32-bitars binärt tal. Motsvarar **REG_DWORD**.
- **Multisträng** : anger en matris med null-terminerade strängar som avslutas med två NULL-tecken.
  Motsvarar **REG_MULTI_SZ**.
- **QWORD** : anger ett 64-bitars binärt tal. Motsvarar **REG_QWORD**.
- **Okänd** : anger en register data typ som inte stöds, till exempel **REG_RESOURCE_LIST**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – UseTransaction

Inkluderar kommandot i den aktiva transaktionen.
Den här parametern är bara giltig medan en transaktion pågår.
Mer information finns i about_Transactions.

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

### -Värde

Anger egenskap svärdet.
Om egenskapen är en register post anger den här parametern värdet för posten.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PSCustomObject

`New-ItemProperty` Returnerar ett anpassat objekt som innehåller den nya egenskapen.

## ANTECKNINGAR

`New-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Clear-ItemProperty](Clear-ItemProperty.md)

[Kopiera – ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Byt namn – ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
