---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: fac6369859c3f8e3181a9044d381d01c12fea062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263774"
---
# Stop-Service

## SAMMANFATTNING
Stoppar en eller flera tjänster som körs.

## SYNTAX

### InputObject (standard)

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Default

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **stoppa-service** skickar ett stopp meddelande till Windows-tjänstens kontrollant för var och en av de angivna tjänsterna.
Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett tjänst objekt som representerar den tjänst som du vill stoppa.

## EXEMPEL

### Exempel 1: stoppa en tjänst på den lokala datorn

```
PS C:\> Stop-Service -Name "sysmonlog"
```

Det här kommandot stoppar Prestandaloggar och-varningar-tjänsten (SysmonLog) på den lokala datorn.

### Exempel 2: stoppa en tjänst med hjälp av visnings namnet

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

Det här kommandot stoppar Telnet-tjänsten på den lokala datorn.
Kommandot använder **Get-service** för att hämta ett objekt som representerar Telnet-tjänsten.
Pipeline-operatorn (|) rör objektet att **stoppa-service** , vilket stoppar tjänsten.

### Exempel 3: stoppa en tjänst som har beroende tjänster

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

I det här exemplet stoppas IISAdmin-tjänsten på den lokala datorn.
Eftersom den här tjänsten stoppas stoppas även de tjänster som är beroende av IISAdmin-tjänsten, men det är bäst att föregå **Stop service** med ett kommando som visar de tjänster som är beroende av IISADMIN-tjänsten.

Det första kommandot listar de tjänster som är beroende av IISAdmin.
Tjänsten använder **Get-service** för att hämta ett objekt som representerar IISADMIN-tjänsten.
Pipeline-operatorn (|) skickar resultatet till Format-List-cmdlet.
Kommandot använder *egenskaps* parametern i **format-listan** för att endast lista **namn** och **DependentServices** egenskaper för tjänsten.

Det andra kommandot stoppar IISAdmin-tjänsten.
Parametern *Force* krävs för att stoppa en tjänst som har beroende tjänster.
Kommandot använder *Confirm* -parametern för att begära bekräftelse från användaren innan varje tjänst stoppas.

## PARAMETRAR

### -DisplayName

Anger visnings namnen för de tjänster som ska stoppas.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Undanta

Anger tjänster som denna cmdlet utelämnar.
Värdet för den här parametern kvalificerar parametern *Name* .
Ange ett namn element eller ett mönster, till exempel s *.
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

### -Force

Tvingar cmdleten att stoppa en tjänst även om tjänsten har beroende tjänster.

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

### -Inkludera

Anger tjänster som denna cmdlet stoppar.
Värdet för den här parametern kvalificerar parametern *Name* .
Ange ett namn element eller ett mönster, till exempel s *.
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

### – InputObject

Anger **ServiceController** -objekt som representerar de tjänster som ska stoppas.
Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger tjänst namnen för de tjänster som ska stoppas.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Nowait

Anger att denna cmdlet använder alternativet No wait.

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

### – PassThru

Returnerar ett objekt som representerar tjänsten.
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

### System. ServiceProcess. ServiceController, system. String

Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller namnet på en tjänst till denna cmdlet.

## UTDATA

### Ingen, system. ServiceProcess. ServiceController

Denna cmdlet skapar ett **system. ServiceProcess. ServiceController** -objekt som representerar tjänsten om du använder parametern *Passthru* .
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Du kan också referera till **Stop service** med det inbyggda aliaset **spsv**. Mer information finns i about_Aliases.

  **Stoppa-tjänsten** kan bara styra tjänster när den aktuella användaren har behörighet att göra detta.
Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.

  Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .
Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .

*

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-service](Remove-Service.md)
