---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: a79bcdaa60c420c4436276749c1b4d298158f8a6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343019"
---
# Start-Service

## SAMMANFATTNING
Startar en eller flera stoppade tjänster.

## SYNTAX

### InputObject (standard)

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Standard

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DisplayName

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Start-Service`Cmdleten skickar ett Start meddelande till Windows-Domänkontrollanttjänsten för varje angiven tjänst. Om en tjänst redan körs ignoreras meddelandet utan fel. Du kan ange tjänsterna efter tjänst namn eller visnings namn, eller så kan du använda parametern **InputObject** för att ange ett tjänst objekt som representerar de tjänster som du vill starta.

## EXEMPEL

### Exempel 1: starta en tjänst med hjälp av dess namn

I det här exemplet startas tjänsten EventLog på den lokala datorn. Parametern **Name** identifierar tjänsten med dess tjänst namn.

```powershell
Start-Service -Name "eventlog"
```

### Exempel 2: Visa information utan att starta en tjänst

Det här exemplet visar vad som skulle hända om du startade tjänsterna som har ett visnings namn som innehåller "fjärran".

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

Parametern **DisplayName** identifierar tjänsterna med deras visnings namn i stället för deras tjänst namn. Parametern **whatIf** gör att cmdleten visar vad som skulle hända när du kör kommandot men inte gör några ändringar.

### Exempel 3: starta en tjänst och registrera åtgärden i en textfil

Det här exemplet startar tjänsten Windows Management Instrumentation (WMI) på datorn och lägger till en post för åtgärden i services.txt-filen.

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

Först använder vi `Get-Service` för att hämta ett objekt som representerar WMI-tjänsten och lagrar det i `$s` variabeln. Nu startar vi tjänsten. Utan parametern **Passthru** `Start-Service` skapas inga utdata. Pipeline-operatorn (|) skickar objektet utdata från `Start-Service` till `Format-List` cmdleten för att formatera objektet som en lista över dess egenskaper. Operatorn Lägg till omdirigering ( \> \> ) dirigerar om utdata till services.txt-filen. Utdata läggs till i slutet av den befintliga filen.

### Exempel 4: starta en inaktive rad tjänst

Det här exemplet visar hur du startar en tjänst när start typen för tjänsten är **inaktive rad**.

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

Det första försöket att starta Telnet-tjänsten (Tlntsvr) misslyckades. `Get-CimInstance`Kommandot visar att egenskapen **Start mode** för Tlntsvr-tjänsten är **inaktive rad**. `Set-Service`Cmdleten ändrar Start typen till **manuell**. Nu kan vi skicka `Start-Service` kommandot igen. Den här gången lyckades kommandot. Verifiera att kommandot har slutförts genom att köra `Get-Service` .

## PARAMETRAR

### -DisplayName

Anger visnings namnen för de tjänster som ska startas. Jokertecken är tillåtna.

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

Anger tjänster som denna cmdlet utelämnar. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel `s*` . Jokertecken är tillåtna.

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

Anger tjänster som den här cmdleten startar. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel `s*` . Jokertecken är tillåtna.

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

Anger **ServiceController** -objekt som representerar de tjänster som ska startas. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

Anger tjänst namnen för den tjänst som ska startas.

Parameter namnet är valfritt. Du kan använda **namn** eller dess alias, **ServiceName** eller så kan du utelämna parameter namnet.

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

Du kan skicka pipe-objekt som representerar de tjänster eller strängar som innehåller tjänst namnen till denna cmdlet.

## UTDATA

### Ingen, system. ServiceProcess. ServiceController

Denna cmdlet skapar ett **system. ServiceProcess. ServiceController** -objekt som representerar tjänsten om du anger **Passthru**. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

- Du kan också referera till `Start-Service` med dess inbyggda alias `sasv` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Start-Service` kan bara styra tjänster om den aktuella användaren har behörighet att göra detta. Om ett kommando inte fungerar som det ska kanske du inte har de behörigheter som krävs.
- Om du vill hitta tjänst namn och visnings namn för tjänsterna i systemet skriver du `Get-Service` .
  Tjänst namnen visas i kolumnen **namn** och visnings namnen visas i kolumnen **DisplayName** .
- Du kan bara starta de tjänster som har start typen manuell, automatisk eller automatisk (fördröjd start). Det går inte att starta tjänsterna som har start typen inaktive rad. Om ett `Start-Service` kommando Miss lyckas med meddelandet `Cannot start service \<service-name\> on computer` använder `Get-CimInstance` du för att hitta starttyp för tjänsten och om du behöver kan du använda `Set-Service` cmdleten för att ändra start typen för tjänsten.
- Vissa tjänster, till exempel Prestandaloggar och-varningar (SysmonLog) stoppas automatiskt om de inte har något arbete att göra. När PowerShell startar en tjänst som stannar nästan omedelbart visas följande meddelande: `Service \<display-name\> start failed.`

## RELATERADE LÄNKAR

[Get-Service](Get-Service.md)

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-service](Remove-Service.md)
