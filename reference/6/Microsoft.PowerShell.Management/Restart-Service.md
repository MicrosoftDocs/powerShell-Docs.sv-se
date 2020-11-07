---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: 44d9ba20bfc8a9423b8a1e67477e95da424c43a7
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343784"
---
# Restart-Service

## SAMMANFATTNING
Stoppar och startar sedan en eller flera tjänster.

## SYNTAX

### InputObject (standard)

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standard

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### DisplayName

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Restart-Service`Cmdleten skickar ett stopp meddelande och ett Start meddelande till Windows-tjänstens kontrollant för en angiven tjänst. Om en tjänst redan har stoppats startas den utan att du får ett fel meddelande. Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett objekt som representerar varje tjänst som du vill starta om.

## EXEMPEL

### Exempel 1: starta om en tjänst på den lokala datorn

```powershell
PS C:\> Restart-Service -Name winmgmt
```

Det här kommandot startar om Windows Management Instrumentation tjänsten (WinMgmt) på den lokala datorn.

### Exempel 2: undanta en tjänst

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

Det här kommandot startar om tjänsterna som har ett visnings namn som börjar med net, förutom tjänsten Net Logon.

### Exempel 3: starta alla stoppade nätverks tjänster

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

Detta kommando startar alla stoppade nätverks tjänster på datorn.

Det här kommandot använder `Get-Service` cmdleten för att hämta objekt som representerar de tjänster vars tjänst namn börjar med net. Pipeline-operatorn ( `|` ) skickar objektet tjänster till `Where-Object` cmdleten, som endast väljer de tjänster som har statusen stoppad. En annan pipeline-operator skickar de valda tjänsterna till `Restart-Service` .

I praktiken använder du parametern **whatIf** för att fastställa kommandots effekter innan du kör det.

## PARAMETRAR

### -DisplayName

Anger visnings namnen för de tjänster som ska startas om. Jokertecken är tillåtna.

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

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

Anger tjänster som den här cmdleten startar om. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel s *. Jokertecken är tillåtna.

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

Anger **ServiceController** -objekt som representerar de tjänster som ska startas om. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

Anger tjänst namnen för de tjänster som ska startas om.

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

Denna cmdlet genererar ett **system. ServiceProcess. ServiceController** -objekt som representerar den omstartade tjänsten om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

- `Restart-Service` kan bara styra tjänster när den aktuella användaren har behörighet att göra detta. Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.
- Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` ".
  Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-service](Remove-Service.md)
