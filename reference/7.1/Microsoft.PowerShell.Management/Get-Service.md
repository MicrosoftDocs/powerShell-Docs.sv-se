---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 1cbecd37217c4c0113079dfa9ac7008dd0d91823
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342237"
---
# Get-Service

## SAMMANFATTNING
Hämtar tjänsterna på datorn.

## SYNTAX

### Standard (standard)

```
Get-Service [[-Name] <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-DependentServices] [-RequiredServices] -DisplayName <String[]> [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-DependentServices] [-RequiredServices] [-Include <String[]>] [-Exclude <String[]>]
 [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Service`Cmdleten hämtar objekt som representerar tjänsterna på en dator, inklusive tjänster som körs och stoppas. När körs `Get-Service` utan parametrar returneras som standard den lokala datorns tjänster.

Du kan dirigera denna cmdlet för att bara få vissa tjänster genom att ange tjänst namnet eller visnings namnet för tjänsterna, eller så kan du skicka pipe-tjänst objekt till denna cmdlet.

## EXEMPEL

### Exempel 1: Hämta alla tjänster på datorn

Det här exemplet hämtar alla tjänster på datorn. Det fungerar som om du skriver `Get-Service *` . Standard visningen visar status, tjänst namn och visnings namn för varje tjänst.

```powershell
Get-Service
```

### Exempel 2: Hämta tjänster som börjar med en Sök sträng

I det här exemplet hämtas tjänster med tjänst namn som börjar med WMI (Windows Management Instrumentation).

```powershell
Get-Service "wmi*"
```

### Exempel 3: Visa tjänster som innehåller en Sök sträng

I det här exemplet visas tjänster med ett visnings namn som innehåller ordet nätverk. Om du söker efter visnings namnet hittar du nätverksrelaterade tjänster även om tjänst namnet inte omfattar net, till exempel xmlprov, nätverks etablerings tjänsten.

```powershell
Get-Service -Displayname "*network*"
```

### Exempel 4: Hämta tjänster som börjar med en Sök sträng och ett undantag

I det här exemplet hämtas endast tjänster med tjänst namn som börjar med **Win** , med undantag för WinRM-tjänsten.

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

### Exempel 5: Visa tjänster som är aktiva för närvarande

I det här exemplet visas endast tjänsterna med statusen körs.

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` hämtar alla tjänster på datorn och skickar objekten nedåt i pipelinen. `Where-Object`Cmdlet: en väljer bara de tjänster med en **status** egenskap som är lika med kör.

Status är bara en egenskap för tjänst objekt. Om du vill se alla egenskaper skriver du `Get-Service | Get-Member` .

### Exempel 6: Visa en lista över tjänsterna på datorn som har beroende tjänster

Det här exemplet hämtar tjänster som har beroende tjänster.

```powershell
Get-Service |
  Where-Object {$_.DependentServices} |
    Format-List -Property Name, DependentServices, @{
      Label="NoOfDependentServices"; Expression={$_.dependentservices.count}
    }
```

```Output
Name                  : AudioEndpointBuilder
DependentServices     : {AudioSrv}
NoOfDependentServices : 1

Name                  : Dhcp
DependentServices     : {WinHttpAutoProxySvc}
NoOfDependentServices : 1
...
```

`Get-Service`Cmdlet: en hämtar alla tjänster på datorn och skickar objekten nedåt i pipelinen. `Where-Object`Cmdleten väljer de tjänster vars **DependentServices** -egenskap inte är null.

Resultaten skickas ned pipelinen till `Format-List` cmdleten. **Egenskaps** parametern visar namnet på tjänsten, namnet på de beroende tjänsterna och en beräknad egenskap som visar antalet beroende tjänster för varje tjänst.

### Exempel 7: sortera tjänster efter egenskaps värde

Det här exemplet visar att när du sorterar tjänster i stigande ordning efter värdet för deras **status** egenskap visas stoppade tjänster innan tjänsterna körs. Orsaken är att värdet för **status** är en uppräkning, där stoppad har värdet 1 och körs har värdet 4. Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

Om du vill visa en lista med tjänster som körs först använder du parametern **fallande** i `Sort-Object` cmdleten.

```powershell
Get-Service "s*" | Sort-Object status
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  stisvc             Windows Image Acquisition (WIA)
Stopped  SwPrv              MS Software Shadow Copy Provider
Stopped  SysmonLog          Performance Logs and Alerts
Running  Spooler            Print Spooler
Running  srservice          System Restore Service
Running  SSDPSRV            SSDP Discovery Service
Running  ShellHWDetection   Shell Hardware Detection
Running  Schedule           Task Scheduler
Running  SCardSvr           Smart Card
Running  SamSs              Security Accounts Manager
Running  SharedAccess       Windows Firewall/Internet Connectio...
Running  SENS               System Event Notification
Running  seclogon           Secondary Logon
```

### Exempel 8: Hämta de beroende tjänsterna för en tjänst

Det här exemplet hämtar de tjänster som krävs av WinRM-tjänsten. Värdet för tjänstens **ServicesDependedOn** -egenskap returneras.

```powershell
Get-Service "WinRM" -RequiredServices
```

### Exempel 9: Hämta en tjänst via pipeline-operatören

Det här exemplet hämtar WinRM-tjänsten på den lokala datorn. Tjänst namn strängen, som omges av citat tecken, skickas till pipelinen `Get-Service` .

```powershell
"WinRM" | Get-Service
```

## PARAMETRAR

### -DependentServices

Anger att denna cmdlet endast hämtar de tjänster som är beroende av den angivna tjänsten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Anger, som en sträng mat ris, visnings namnen för de tjänster som ska hämtas. Jokertecken är tillåtna.

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

Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet exkluderar från åtgärden.
Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel `s*` . Jokertecken är tillåtna.

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

Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel `s*` . Jokertecken är tillåtna.

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

Anger **ServiceController** -objekt som representerar de tjänster som ska hämtas. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan skicka vidare ett tjänst objekt till denna cmdlet.

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger tjänst namnen för de tjänster som ska hämtas. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -RequiredServices

Anger att denna cmdlet bara hämtar de tjänster som krävs för den här tjänsten. Den här parametern hämtar värdet för tjänstens **ServicesDependedOn** -egenskap.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. ServiceProcess. ServiceController, system. String

Du kan skicka vidare ett tjänst objekt eller ett tjänst namn till denna cmdlet.

## UTDATA

### System. ServiceProcess. ServiceController

Denna cmdlet returnerar objekt som representerar tjänsterna på datorn.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Från och med PowerShell 6,0 läggs följande egenskaper till i **ServiceController** -objekten: **username** , **Description** , **DelayedAutoStart** , **BinaryPathName** och **startuptype tjänst** .

Du kan också referera till `Get-Service` med dess inbyggda alias `gsv` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

Den här cmdleten kan endast Visa tjänster när den aktuella användaren har behörighet att se dem. Om denna cmdlet inte visar tjänster kanske du inte har behörighet att se dem.

Om du vill hitta tjänst namnet och visnings namnet för varje tjänst i systemet skriver du `Get-Service` . Tjänst namnen visas i kolumnen namn och visnings namnen visas i kolumnen **DisplayName** .

När du sorterar i stigande ordning efter värdet för egenskapen **status** visas stoppade tjänster innan tjänsterna körs. Tjänstens **status** egenskap är ett uppräknat värde och status namnen representerar heltals värden. Sorterings ordningen baseras på heltal svärdet, inte namnet. Stoppad visas innan eftersom det stoppades eftersom det stoppats, och det har värdet 1, och körning har värdet 4. Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

## RELATERADE LÄNKAR

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)

[Remove-service](Remove-Service.md)
