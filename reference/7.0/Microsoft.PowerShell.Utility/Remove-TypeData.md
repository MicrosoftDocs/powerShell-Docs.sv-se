---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-TypeData
ms.openlocfilehash: 1011011c8ce5471f976336e6b563f6d1662e17e4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262322"
---
# Remove-TypeData

## Sammanfattning
Tar bort utökade typer från den aktuella sessionen.

## Syntax

### RemoveTypeDataSet (standard)

```
Remove-TypeData -TypeData <TypeData> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveTypeSet

```
Remove-TypeData [-TypeName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### RemoveFileSet

```
Remove-TypeData -Path <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Remove-TypeData`Cmdleten tar bort utökade typ data från den aktuella sessionen. Denna cmdlet påverkar endast den aktuella sessionen och de sessioner som skapas i den aktuella sessionen.

Du kan lägga till egenskaper och metoder för objekt i PowerShell genom att definiera dem i `Update-TypeData` kommandon och `Types.ps1xml` filer. `Remove-TypeData` tar bort dessa utökade egenskaper och metoder från den aktuella sessionen. `Remove-TypeData` tar inte bort `Types.ps1xml` filerna eller tar bort eventuella definitioner av utökad typ från `Types.ps1xml` filerna. Mer information om `Types.ps1xml` filer finns i [about_Types.ps1XML](../Microsoft.PowerShell.Core/about/about_Types.ps1xml.md).

Den här cmdleten introducerades i Windows PowerShell 3,0.

## Exempel

### Exempel 1: ta bort typ data för en angiven typ

Det här exemplet tar bort alla typ data för **system. mat ris** typen från sessionen, inklusive typ data som har lagts till av en `Types.ps1xml` fil och dynamiska typ data som har lagts till i sessionen med hjälp av `Update-TypeData` cmdleten.

```powershell
Remove-TypeData -TypeName System.Array
```

### Exempel 2: ta bort en utökad datatyp från en session

I det här exemplet visas effekterna av att ta bort utökade typ data från en session. Det första `Get-TypeData` hämtar utökade typ data för **system. DateTime** -typen. Utdata visar att en **datetime** -egenskap har lagts till i alla **system. DateTime** -objekt i PowerShell. `Get-Date`Cmdleten returnerar ett **system. DateTime** -objekt. Kommandot använder punkt notation för att hämta värdet för egenskapen **datetime** för objektet **system. DateTime** som `Get-Date` returnerar.

```powershell
Get-TypeData System.DateTime
(Get-Date).DateTime
Get-TypeData System.DateTime | Remove-TypeData
(Get-Date).DateTime
```

```Output
TypeName        Members
--------        -------
System.DateTime {[DateTime, System.Management.Automation.Runspaces.ScriptPropertyData]}

Friday, January 20, 2012 9:01:00 PM
```

Nästa `Get-TypeData` cmdlet för att hämta alla utökade typ data för **system. DateTime** -typen och pipes som till `Remove-TypeData` cmdleten för att ta bort de utökade data typerna. Den sista `Get-Date` cmdleten visar effekterna av att ta bort den utökade typen av data för **system. DateTime** -typen. Eftersom egenskapen **system. DateTime** inte längre finns returnerar ett kommando för att hämta dess värde Nothing.

### Exempel 3: ta bort utökade typer för moduler

Det här exemplet tar bort alla utökade typ data för modul-objekt. När du flyttar ett objekt till `Remove-TypeData` `Remove-TypeData` hämtar namnet på objekt typen och tar bort alla typ data för alla objekt av den typen.

```powershell
Get-Module | Remove-TypeData
```

### Exempel 4: ta bort utökade typer från angivna moduler

I det här exemplet används cmdlet **-parametern för** `Remove-TypeData` cmdleten för att ta bort de utökade typer som definieras i de `Types.ps1xml` filer som läggs till av **PSScheduledJob** -och **PSWorkflow** -modulerna. Det här kommandot påverkar inte dynamiska typ data som läggs till med hjälp av `Update-TypeData` cmdleten. Kommandot slutförs endast när modulerna har importer ATS till den aktuella sessionen.

```powershell
Remove-TypeData -Path "$PSHOME\Modules\PSScheduledJob", "$PSHOME\Modules\PSWorkflow\PSWorkflow.types.ps1xml"
```

Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

### Exempel 5: ta bort utökade typer från en fjärran sluten session

I det här exemplet tas utökade typer bort från en fjärran sluten session. Kommandot använder `Invoke-Command` cmdleten för att ta bort utökade typ data för alla CIM-typer i sessionerna i `$S` variabeln.

```powershell
Invoke-Command -Session $S {Get-TypeData -TypeName *CIM* | Remove-TypeData}
```

## Parametrar

### -Path

Anger en matris med filer som den här cmdleten tar bort från data för den utökade typen av session. Den här parametern är obligatorisk.

Ange sökvägar och fil namn för en eller flera `Types.ps1xml` filer. Jokertecken stöds inte. Om du utelämnar sökvägen är standard platsen den aktuella katalogen.

```yaml
Type: System.String[]
Parameter Sets: RemoveFileSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TypeData

Anger typ data som denna cmdlet tar bort från sessionen. Den här parametern är obligatorisk. Ange en variabel som innehåller **TypeData** -objekt ( **system. Management. Automation. körnings utrymmen. TypeData** ) eller ett kommando som hämtar **TypeData** -objekt, till exempel ett `Get-TypeData` kommando. Du kan också skicka pipe- **TypeData** objekt till `Remove-TypeData` .

```yaml
Type: System.Management.Automation.Runspaces.TypeData
Parameter Sets: RemoveTypeDataSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -TypeName

Anger de typer som denna cmdlet tar bort all utökad typ av data för. För typer i system namn området anger du det korta namnet. Annars krävs det fullständiga typ namnet. Jokertecken stöds inte.

Du kan skicka pipe-typnamn till `Remove-TypeData` . När du flyttar ett objekt till `Remove-TypeData` , `Remove-TypeData` hämtar typ namnet för objektet och tar bort alla typ data för objekt typen.

```yaml
Type: System.String
Parameter Sets: RemoveTypeSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

## Indata

### System. Management. Automation. körnings utrymmen. TypeData

Du kan skicka pipe **TypeData** -objekt, till exempel de som `Get-TypeData` cmdleten returnerar, till `Remove-TypeData` .

### System. String

Du kan skicka vidare typ namn till `Remove-TypeData` . När du flyttar ett objekt till `Remove-TypeData` , `Remove-TypeData` hämtar typ namnet för objektet och tar bort alla typ data för objekt typen.

## Utdata

### Inget

Denna cmdlet genererar inga utdata.

## Kommentarer

`Remove-TypeData` Det går bara att ta bort utökade typ data i den aktuella sessionen. Det går inte att ta bort utökade typ data som finns på datorn, men som inte har lagts till i den aktuella sessionen, till exempel utökade typer som har definierats i moduler som inte har importer ATS till den aktuella sessionen.

## Relaterade länkar

[Get-TypeData](Get-TypeData.md)

[Uppdatera – TypeData](Update-TypeData.md)
