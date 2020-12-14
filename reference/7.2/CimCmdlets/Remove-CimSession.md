---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimSession
ms.openlocfilehash: a3ff2132c531df1ab19bf7149a55ea0df4a787a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708546"
---
# Remove-CimSession

## SAMMANFATTNING
Tar bort en eller flera CIM-sessioner.

## SYNTAX

### CimSessionSet (standard)

```
Remove-CimSession [-CimSession] <CimSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameSet

```
Remove-CimSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### SessionIdSet

```
Remove-CimSession [-Id] <UInt32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdSet

```
Remove-CimSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameSet

```
Remove-CimSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Remove-CimSession`Cmdleten tar bort ett eller flera CIM-sessionsobjekt från den lokala PowerShell-sessionen.

## EXEMPEL

### Exempel 1: ta bort alla CIM-sessioner

Det här exemplet hämtar alla tillgängliga CIM-sessioner på den lokala datorn med hjälp av cmdleten [Get-CimSession](Get-CimSession.md) och tar sedan bort dem med hjälp av `Remove-CimSession` .

```powershell
Get-CimSession | Remove-CimSession
```

### Exempel 2: ta bort en angiven CIM-session

I det här exemplet tas CIM-sessionen bort som har **ID-** värdet 5.

```powershell
Remove-CimSession -Id 5
```

### Exempel 3: Visa listan över CIM-sessioner som ska tas bort med hjälp av parametern WhatIf

I det här exemplet används den gemensamma parametern **whatIf** för att ange att borttagningen inte ska göras, men endast utdata som skulle inträffa om den är färdig.

```powershell
Remove-CimSession -Name a* -WhatIf
```

## PARAMETRAR

### – CimSession

Anger session-objekten för de CIM-sessioner som ska stängas.

Ange en variabel som innehåller CIM-sessionen, eller ett kommando som skapar eller hämtar CIM-sessionen, t. ex [`New-CimSession`](New-CimSession.md) . eller- [`Get-CimSession`](Get-CimSession.md) cmdletar.
Mer information finns i [about_CimSessions](../Microsoft.PowerShell.Core/About/about_CimSession.md).

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ComputerName

Anger en matris med namn på datorer. Tar bort de sessioner som ansluter till de angivna datorerna. Du kan ange ett fullständigt kvalificerat domän namn (FQDN) eller ett NetBIOS-namn.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ID

Anger ID för CIM-sessionen som ska tas bort. Ange ett eller flera ID: n avgränsade med kommatecken eller Använd intervall operatorn ( `..` ) för att ange ett intervall med ID: n. Ett **ID** är ett heltal som unikt identifierar CIM-sessionen i den aktuella PowerShell-sessionen.

Mer information om operatorn Range finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID för CIM-sessionen som ska tas bort. **InstanceID** är en globalt unik IDENTIFIERARE (GUID) som unikt identifierar en CIM-session. **InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.

**InstanceID** lagras i egenskapen **InstanceID** för objektet som representerar en CIM-session.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger det egna namnet på CIM-sessionen som ska tas bort. Du kan använda jokertecken med den här parametern.

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
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

## INDATA

### Inga

Denna cmdlet accepterar inga inobjekt.

## UTDATA

### System. Object

Den här cmdleten returnerar ett objekt som innehåller information om CIM-session.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-CimSession](Get-CimSession.md)

[New-CimSession](New-CimSession.md)

[about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)

