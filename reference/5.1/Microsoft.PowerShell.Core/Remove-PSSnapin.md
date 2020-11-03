---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264176"
---
# Remove-PSSnapin

## SAMMANFATTNING
Tar bort Windows PowerShell-snapin-moduler från den aktuella sessionen.

## SYNTAX

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Remove-PSSnapin** tar bort en Windows PowerShell-snapin-modul från den aktuella sessionen.
Du kan använda den för att ta bort snapin-moduler som du har lagt till i Windows PowerShell du kan inte använda denna cmdlet för att ta bort snapin-modulerna som installeras med Windows PowerShell.

När du har tagit bort en snapin-modul från den aktuella sessionen är snapin-modulen fortfarande inläst, men cmdlets och providers i snapin-modulen är inte längre tillgängliga i sessionen.

## EXEMPEL

### Exempel 1: ta bort en snapin-modul

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

Det här kommandot tar bort snapin-modulen **Microsoft. Exchange** från den aktuella sessionen.
När kommandot har slutförts är de cmdlets och providers som stöds av snapin-modulen inte tillgängliga i sessionen.

### Exempel 2: ta bort snapin-moduler med namn med pipelinen

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

Det här kommandot tar bort Windows PowerShell-snapin-moduler som har namn som börjar med SMP från den aktuella sessionen.

Kommandot använder cmdleten **Get-PSSnapin** för att hämta objekt som representerar snapin-modulerna. Pipeline-operatorn (|) skickar resultatet till cmdleten **Remove-PSSnapin** , som tar bort dem från sessionen.
De providers och cmdlets som den här snapin-modulen stöder är inte längre tillgängliga i sessionen.

När du rör objekt som ska **tas bort-PSSnapin** , är namnen på objekten associerade med parametern *Name* , som accepterar objekt från pipelinen som har egenskapen **Name** .

### Exempel 3: ta bort snapin-moduler med hjälp av namn

```
PS C:\> Remove-PSSnapin -Name *event*
```

Det här kommandot tar bort alla Windows PowerShell-snapin-moduler som har namn som inkluderar event.

## PARAMETRAR

### -Name
Anger namnen på Windows PowerShell-snapin-modulerna som ska tas bort från den aktuella sessionen.
Jokertecken (*) tillåts.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru
Returnerar ett objekt som representerar snapin-modulen.
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

### System. Management. Automation. PSSnapInInfo
Du kan skicka vidare ett snapin-objekt till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PSSnapInInfo
Denna cmdlet skapar ett **system. Management. Automation. PSSnapInInfo** -objekt som representerar snapin-modulen, om du anger parametern *Passthru* .
Som standard genererar **Remove-PSSnapin** inga utdata.

## ANTECKNINGAR

* **Remove-PSSnapin** kontrollerar inte versionen av Windows PowerShell innan en snapin-modul tas bort från sessionen. Om det inte går att ta bort en snapin-modul visas en varning och kommandot Miss lyckas.
* **Remove-PSSnapin** påverkar endast den aktuella sessionen. Om du har lagt till ett Add-PSSnapin-kommando i din Windows PowerShell-profil bör du ta bort kommandot för att ta bort snapin-modulen från framtida sessioner. För instruktioner skriver du `Get-Help about_Profiles` .

## RELATERADE LÄNKAR

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)
