---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Service
ms.openlocfilehash: 0c007f1becd7364806cfd47e18cf05995b81e0f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266114"
---
# Get-Service

## SAMMANFATTNING
Hämtar tjänsterna på en lokal dator eller fjärrdator.

## SYNTAX

### Standard (standard)

```
Get-Service [[-Name] <String[]>] [-ComputerName <String[]>] [-DependentServices] [-RequiredServices]
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### DisplayName

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] -DisplayName <String[]>
 [-Include <String[]>] [-Exclude <String[]>] [<CommonParameters>]
```

### InputObject

```
Get-Service [-ComputerName <String[]>] [-DependentServices] [-RequiredServices] [-Include <String[]>]
 [-Exclude <String[]>] [-InputObject <ServiceController[]>] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Get-service** hämtar objekt som representerar tjänsterna på en lokal dator eller på en fjärrdator, inklusive tjänster som körs och stoppas.

Du kan dirigera denna cmdlet för att bara få vissa tjänster genom att ange tjänst namnet eller visnings namnet för tjänsterna, eller så kan du skicka pipe-tjänst objekt till denna cmdlet.

## EXEMPEL

### Exempel 1: Hämta alla tjänster på datorn

```powershell
Get-Service
```

Det här kommandot hämtar alla tjänster på datorn.
Det fungerar som om du skriver `Get-Service *` .
Standard visningen visar status, tjänst namn och visnings namn för varje tjänst.

### Exempel 2: Hämta tjänster som börjar med en Sök sträng

```powershell
Get-Service "wmi*"
```

Detta kommando hämtar tjänster med tjänst namn som börjar med WMI (akronym för Windows Management Instrumentation).

### Exempel 3: Visa tjänster som innehåller en Sök sträng

```powershell
Get-Service -Displayname "*network*"
```

Det här kommandot visar tjänster med ett visnings namn som innehåller ordet nätverk.
Om du söker efter visnings namnet hittar du nätverksrelaterade tjänster även om tjänst namnet inte innehåller "net", till exempel xmlprov, nätverks etablerings tjänsten.

### Exempel 4: Hämta tjänster som börjar med en Sök sträng och ett undantag

```powershell
Get-Service -Name "win*" -Exclude "WinRM"
```

De här kommandona hämtar bara tjänsterna med tjänst namn som börjar med Win, med undantag för WinRM-tjänsten.

### Exempel 5: Visa tjänster som är aktiva för närvarande

```powershell
Get-Service | Where-Object {$_.Status -eq "Running"}
```

Det här kommandot visar bara de tjänster som är aktiva för närvarande.
Den använder cmdleten **Get-service** för att hämta alla tjänster på datorn.
Pipeline-operatorn (|) skickar resultaten till Where-Object-cmdlet, som endast väljer de tjänster som har en status egenskap som är lika med kör.

Status är bara en egenskap för tjänst objekt.
Om du vill se alla egenskaper skriver du `Get-Service | Get-Member` .

### Exempel 6: Hämta tjänsterna på en fjärrdator

```powershell
Get-Service -ComputerName "Server02"
```

Detta kommando hämtar tjänsterna på den fjärranslutna Server02-datorn.

Eftersom parametern *computername* för **Get-service** inte använder Windows PowerShell-fjärrkommunikation kan du använda den här parametern även om datorn inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.

### Exempel 7: Visa en lista över tjänsterna på den lokala datorn som har beroende tjänster

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

Det första kommandot använder cmdleten **Get-service** för att hämta tjänsterna på datorn.
En pipeline-operator (|) skickar tjänsterna till **Where-Object-** cmdleten, som väljer de tjänster vars **DependentServices** -egenskap inte är null.

En annan pipeline-operator skickar resultatet till Format-List-cmdlet.
Kommandot använder *egenskaps* parametern för att visa namnet på tjänsten, namnet på de beroende tjänsterna och en beräknad egenskap som visar antalet beroende tjänster som varje tjänst har.

### Exempel 8: sortera tjänster efter egenskaps värde

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

Det här kommandot visar att när du sorterar tjänster i stigande ordning efter värdet för deras **status** egenskap visas stoppade tjänster innan tjänsterna körs.
Detta inträffar eftersom värdet för status är en uppräkning, där stoppad har värdet 1 och körs har värdet 4.

Om du vill visa en lista med tjänster som körs först använder du parametern *fallande* i Sort-Object-cmdleten.

### Exempel 9: Hämta tjänster på flera datorer

```powershell
Get-Service -Name "WinRM" -ComputerName "localhost", "Server01", "Server02" |
 Format-Table -Property MachineName, Status, Name, DisplayName -auto
```

```Output
MachineName    Status  Name  DisplayName
------------   ------  ----  -----------
localhost      Running WinRM Windows Remote Management (WS-Management)
Server01       Running WinRM Windows Remote Management (WS-Management)
Server02       Running WinRM Windows Remote Management (WS-Management)
```

Det här kommandot använder cmdleten **Get-service** för att köra ett Get-Service WinRM-kommando på två fjärranslutna datorer och den lokala datorn ("localhost").

Kommandot körs på fjärrdatorerna och resultaten returneras till den lokala datorn.
En pipeline-operator (|) skickar resultaten till **Format-Table-** cmdleten, som formaterar tjänsterna som en tabell.
Kommandot **Format-Table** använder *egenskaps* parametern för att ange de egenskaper som visas i tabellen, inklusive egenskapen **MachineName** .

### Exempel 10: Hämta de beroende tjänsterna för en tjänst

```powershell
Get-Service "WinRM" -RequiredServices
```

Det här kommandot hämtar de tjänster som krävs av WinRM-tjänsten.

Kommandot returnerar värdet för tjänstens **ServicesDependedOn** -egenskap.

### Exempel 11: Hämta en tjänst via pipeline-operatören

```powershell
"WinRM" | Get-Service
```

Det här kommandot hämtar WinRM-tjänsten på den lokala datorn.
Det här exemplet visar att du kan skicka en tjänst namn sträng (inom citat tecken) till **Get-service**.

## PARAMETRAR

### -ComputerName

Hämtar de tjänster som körs på de angivna datorerna.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern *computername* för **Get-service** även om datorn inte har kon figurer ATS för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DependentServices

Anger att denna cmdlet endast hämtar de tjänster som är beroende av den angivna tjänsten.

Som standard hämtar denna cmdlet alla tjänster.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: DS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisplayName

Anger, som en sträng mat ris, visnings namnen för de tjänster som ska hämtas.
Jokertecken är tillåtna.
Som standard hämtar denna cmdlet alla tjänster på datorn.

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
Värdet för den här parametern kvalificerar parametern *Name* .
Ange ett namn element eller ett mönster, till exempel "s *".
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

### -Inkludera

Anger, som en sträng mat ris, en tjänst eller tjänster som denna cmdlet inkluderar i åtgärden.
Värdet för den här parametern kvalificerar parametern *Name* .
Ange ett namn element eller ett mönster, till exempel "s *".
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

Anger **ServiceController** -objekt som representerar de tjänster som ska hämtas.
Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.
Du kan också skicka ett tjänst objekt till denna cmdlet.

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

Anger tjänst namnen för de tjänster som ska hämtas.
Jokertecken är tillåtna.
Som standard hämtar denna cmdlet alla tjänster på datorn.

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

Anger att denna cmdlet bara hämtar de tjänster som krävs för den här tjänsten.

Den här parametern hämtar värdet för tjänstens **ServicesDependedOn** -egenskap.
Som standard hämtar denna cmdlet alla tjänster.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: SDO, ServicesDependedOn

Required: False
Position: Named
Default value: None
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

Du kan också referera till **Get-service** med det inbyggda aliaset "GSV". Mer information finns i about_Aliases.

Den här cmdleten kan endast Visa tjänster när den aktuella användaren har behörighet att se dem.
Om denna cmdlet inte visar tjänster kanske du inte har behörighet att se dem.

Om du vill hitta tjänst namnet och visnings namnet för varje tjänst i systemet skriver du `Get-Service` .
Tjänst namnen visas i kolumnen namn och visnings namnen visas i kolumnen DisplayName.

När du sorterar i stigande ordning efter status värde visas "stoppad" tjänster innan "körs"-tjänster.
Tjänstens status egenskap är ett uppräknat värde där namnen på statusarna representerar heltals värden.
Sorteringen baseras på heltal svärdet, inte namnet.
"Körs" visas före "stoppad" eftersom "stoppad" har värdet "1" och "körs" har värdet "4".

## RELATERADE LÄNKAR

[New-Service](New-Service.md)

[Restart-Service](Restart-Service.md)

[Resume-Service](Resume-Service.md)

[Set-Service](Set-Service.md)

[Start-Service](Start-Service.md)

[Stop-Service](Stop-Service.md)

[Suspend-Service](Suspend-Service.md)
