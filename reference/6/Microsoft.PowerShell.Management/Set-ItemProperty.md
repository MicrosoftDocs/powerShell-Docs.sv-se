---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: b12ca6bda03c1eb3834916bf9bfce43ecc3a70fb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263805"
---
# Set-ItemProperty

## SAMMANFATTNING
Skapar eller ändrar värdet för en egenskap för ett objekt.

## SYNTAX

### propertyValuePathSet (standard)

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### propertyPSObjectPathSet

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### propertyValueLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### propertyPSObjectLiteralPathSet

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-ItemProperty`Cmdleten ändrar värdet för egenskapen för det angivna objektet.
Du kan använda cmdleten för att skapa eller ändra egenskaper för objekt.
Du kan till exempel använda `Set-ItemProperty` för att ange värdet för egenskapen **IsReadOnly** för ett fil objekt `$True` .

Du kan också använda `Set-ItemProperty` för att skapa och ändra register värden och data.
Du kan till exempel lägga till en ny register post i en nyckel och upprätta eller ändra dess värde.

## EXEMPEL

### Exempel 1: Ange en egenskap för en fil

Det här kommandot anger värdet för egenskapen **IsReadOnly** för filen "final.doc" till "true".
Den använder **sökvägen** för att ange filen, **namn** för att ange namnet på egenskapen och **värdet** parameter för att ange det nya värdet.

Filen är ett **system. io. fileinfo** -objekt och **IsReadOnly** är bara en av dess egenskaper.
Om du vill se alla egenskaper skriver du `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType
Property` .

Den `$true` automatiska variabeln representerar värdet "true".
Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### Exempel 2: skapa en register post och ett värde

Det här exemplet visar hur du kan använda `Set-ItemProperty` för att skapa en ny register post och tilldela ett värde till posten. Posten "NoOfEmployees" skapas i nyckeln "ContosoCompany" i `HKLM\Software` nyckeln och värdet anges till 823.

Eftersom register poster anses vara egenskaper för register nycklarna, som är objekt, använder du `Set-ItemProperty` för att skapa register poster och för att upprätta och ändra deras värden.

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823
```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```Output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

Det första kommandot skapar register posten.
Den använder **Path** för att ange sökvägen till `HKLM:` enheten och nyckeln "Software\MyCompany".
Kommandot använder **Name** för att ange postnamn och **värde** för att ange ett värde.

Det andra kommandot använder `Get-ItemProperty` cmdleten för att se den nya register posten.
Om du använder `Get-Item` -eller `Get-ChildItem` -cmdletarna visas inte posterna eftersom de är egenskaper för en nyckel, inte objekt eller underordnade objekt.

Det tredje kommandot ändrar värdet för posten **NoOfEmployees** till 824.

Du kan också använda cmdlet: en `New-ItemProperty` för att skapa register posten och dess värde och sedan använda `Set-ItemProperty` för att ändra värdet.

Om du vill ha mer information om `HKLM:` enheten skriver du `Get-Help Get-PSDrive` .
Mer information om hur du använder PowerShell för att hantera registret får du genom att skriva `Get-Help Registry` .

### Exempel 3: ändra ett objekt med hjälp av pipelinen

De här kommandona visar hur du använder en pipeline-operator ( `|` ) för att skicka ett objekt till `Set-ItemProperty` .

Den första delen av kommandot använder `Get-ChildItem` för att hämta ett objekt som representerar "Weekly.txt"-filen. Kommandot använder en pipeline-operator för att skicka objektet till `Set-ItemProperty` .
`Set-ItemProperty`Kommandot använder parametrarna **Name** och **Value** för att ange egenskapen och det nya värdet.

Det här kommandot motsvarar att använda parametern **InputObject** för att ange det objekt som ska `Get-ChildItem` hämtas.

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
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

### -Force

Tvingar cmdleten att ange en egenskap för objekt som annars inte kan nås av användaren.
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

### – InputObject

Anger det objekt som har de egenskaper som denna cmdlet ändrar.
Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: propertyPSObjectLiteralPathSet, propertyValueLiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger namnet på egenskapen.

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar egenskapen Item.
Som standard genererar denna cmdlet inga utdata.

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

### -Path

Anger sökvägen till objekten med egenskapen att ändra.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Typ

**Typ** är en dynamisk parameter som Registry-providern lägger till i `Set-ItemProperty` cmdleten.
Den här parametern fungerar bara i register enheterna.

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
Type: Microsoft.Win32.RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Värde

Anger egenskapens värde.

```yaml
Type: System.Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
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

### System. Management. Automation. PSObject

Du kan skicka pipe-objekt till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PSCustomObject

Denna cmdlet genererar ett **PSCustomObject** -objekt som representerar objektet som ändrades och dess nya egenskaps värde, om du anger parametern **Passthru** .
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

`Set-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Clear-ItemProperty](Clear-ItemProperty.md)

[Kopiera – ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Byt namn – ItemProperty](Rename-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
