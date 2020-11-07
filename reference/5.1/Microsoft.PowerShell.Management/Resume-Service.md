---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 0902e944f2976bbdbc35fd051926422c5ae6f8c5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342645"
---
# Resume-Service

## SAMMANFATTNING
Återupptar en eller flera pausade tjänster.

## SYNTAX

### InputObject (standard)

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standard

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Resume-Service`Cmdleten skickar ett återställnings meddelande till Windows-Domänkontrollanttjänsten för varje angiven tjänst. Om en tjänst pausas återupptas den. Om den körs, ignoreras meddelandet. Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett tjänst objekt som representerar de tjänster som du vill återuppta.

## EXEMPEL

### Exempel 1: återuppta en tjänst på den lokala datorn

```
PS C:\> Resume-Service "sens"
```

Det här kommandot återupptar tjänsten system Event notification på den lokala datorn. Tjänst namnet visas i kommandot av Sens. Kommandot använder **Name** -parametern för att ange tjänst namnet för tjänsten, men kommandot utesluter parameter namnet eftersom parameter namnet är valfritt.

### Exempel 2: återuppta alla pausade tjänster

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

Detta kommando återupptar alla pausade tjänster på datorn. `Get-Service`Cmdlet-kommandot hämtar alla tjänster på datorn. Pipeline-operatorn ( `|` ) skickar resultatet till `Where-Object` cmdleten, som väljer de tjänster som har **statusen** pausad. Nästa pipeline-operator skickar resultatet till `Resume-Service` , vilket återupptar de pausade tjänsterna.

I praktiken använder du parametern **whatIf** för att fastställa kommandots effekter innan du kör det.

## PARAMETRAR

### -DisplayName

Anger visnings namnen för de tjänster som ska återupptas.
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

Anger tjänster som denna cmdlet utelämnar. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel s *. Jokertecken är tillåtna.

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

### -Inkludera

Anger vilka tjänster som ska återupptas. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel s *. Jokertecken är tillåtna.

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

Anger **ServiceController** -objekt som representerar tjänsterna som ska återupptas. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

Anger tjänst namnen för de tjänster som ska återupptas.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar tjänsten. Som standard genererar denna cmdlet inga utdata.

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

### System. ServiceProcess. ServiceController, system. String

Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller ett tjänst namn till denna cmdlet.

## UTDATA

### Ingen, system. ServiceProcess. ServiceController

Denna cmdlet genererar ett **system. ServiceProcess. ServiceController** -objekt som representerar den återupptog tjänsten om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- Statusen för tjänster som har pausats har pausats. När tjänsterna återupptas körs deras status.
- `Resume-Service` kan bara styra tjänster när den aktuella användaren har behörighet att göra detta. Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.
- Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .
  Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
