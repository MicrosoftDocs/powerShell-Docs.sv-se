---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 5e4037c4ba8947f8efb438103f2bfd47eb05d1f5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343750"
---
# Suspend-Service

## SAMMANFATTNING
Pausar (pausar) en eller flera tjänster som körs.

## SYNTAX

### InputObject (standard)

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standard

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Suspend-Service`Cmdleten skickar ett uppehålls meddelande till Windows-Tjänstekontrollanten för var och en av de angivna tjänsterna. Tjänsten körs fortfarande när den har pausats, men dess åtgärd stoppas tills den återupptas, till exempel av usingthe- `Resume-Service` cmdlet. Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att skicka ett tjänst objekt som representerar de tjänster som du vill pausa.

## EXEMPEL

### Exempel 1: pausa en tjänst

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

Med det här kommandot pausas tjänsten Telnet service (Tlntsvr) på den lokala datorn.

### Exempel 2: Visa vad som händer om du inaktiverar tjänster

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

Det här kommandot anger vad som skulle hända om du har avbrutit tjänsterna som har ett tjänst namn som börjar med LANMAN. Om du vill inaktivera tjänsterna kör du kommandot igen utan parametern **whatIf** .

### Exempel 3: Hämta och pausa en tjänst

```
PS C:\> Get-Service schedule | Suspend-Service
```

Det här kommandot använder `Get-Service` cmdleten för att hämta ett objekt som representerar tjänsten Schemaläggaren (Schedule) på datorn. Pipeline-operatorn ( `|` ) skickar resultatet till `Suspend-Service` , vilket gör att tjänsten pausas.

### Exempel 4: inaktivera alla tjänster som kan pausas

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

Det här kommandot pausar alla tjänster på datorn som kan pausas. Den använder `Get-Service` för att hämta objekt som representerar tjänsterna på datorn. Pipeline-operatorn skickar resultaten till `Where-Object` cmdleten, som endast väljer de tjänster som har värdet `$True` för egenskapen **CanPauseAndContinue** . En annan pipeline-operator skickar resultatet till `Suspend-Service` . Parametern **Confirm** meddelar dig om bekräftelse innan du pausar varje tjänst.

## PARAMETRAR

### -DisplayName

Anger visnings namnen för de tjänster som ska pausas. Jokertecken är tillåtna.

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

Anger tjänster som ska uteslutas från de angivna tjänsterna. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel "s *". Jokertecken är tillåtna.

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

Anger vilka tjänster som ska pausas. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel "s *". Jokertecken är tillåtna.

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

Anger **ServiceController** -objekt som representerar de tjänster som ska pausas. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

Anger tjänst namnen för de tjänster som ska pausas. Jokertecken är tillåtna.

Parameter namnet är valfritt. Du kan använda **namn** eller dess alias, **ServiceName** eller så kan du utelämna parameter namnet.

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

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

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

Du kan skicka vidare ett tjänst objekt eller en sträng som innehåller ett tjänst namn till denna cmdlet.

## UTDATA

### Ingen, system. ServiceProcess. ServiceController

Denna cmdlet skapar ett **system. ServiceProcess. ServiceController** -objekt som representerar tjänsten om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

- `Suspend-Service` kan bara styra tjänster när den aktuella användaren har behörighet att göra detta. Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.
- `Suspend-Service` kan endast pausa tjänster som stöder inaktive ring och återupptagning. För att avgöra om en viss tjänst kan pausas använder du `Get-Service` cmdleten tillsammans med egenskapen **CanPauseAndContinue** . Exempelvis `Get-Service wmi | Format-List Name, CanPauseAndContinue`. Om du vill hitta alla tjänster på datorn som kan inaktive ras skriver du `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` .
- Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .
  Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Remove-service](Remove-Service.md)
