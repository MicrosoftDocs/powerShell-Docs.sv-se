---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: 1b0fbfca365e9cf369decbf4eafc0a8b4e2741bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267303"
---
# Remove-PSSession

## SAMMANFATTNING
Stänger en eller flera PowerShell-sessioner (PSSessions).

## SYNTAX

### ID (standard)

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Session

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Hålla

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMId

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### VMName

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Name

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet **: en Remove-PSSession** stänger PowerShell-sessioner ( **PSSessions** ) i den aktuella sessionen.
Alla kommandon som körs i **PSSessions** avslutas, avslutar **PSSession** och frigör de resurser som **PSSession** använde.
Om **PSSession** är ansluten till en fjärrdator, stänger denna cmdlet också anslutningen mellan lokala och fjärranslutna datorer.

Om du vill ta bort en **PSSession** anger du *namnet* , *computername* , *ID* eller *InstanceID* för sessionen.

Om du har sparat *PSSession* i en variabel finns objektet kvar i variabeln, men *PSSession* är stängt.

## EXEMPEL

### Exempel 1: ta bort sessioner med ID: n

```powershell
Remove-PSSession -Id 1, 2
```

Det här kommandot tar bort **PSSessions** med ID 1 och 2.

### Exempel 2: ta bort alla sessioner i den aktuella sessionen

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

De här kommandona tar bort alla **PSSessions** i den aktuella sessionen.
Även om de tre kommando formaten ser olika ut, har de samma resultat.

### Exempel 3: Stäng sessioner med hjälp av namn

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

Kommandona stänger **PSSessions** som är anslutna till datorer som har namn som börjar med serv.

### Exempel 4: Stäng sessioner som är anslutna till en port

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

Detta kommando stänger de **PSSessions** som är anslutna till port 90.
Du kan använda det här kommando formatet för att identifiera **PSSessions** efter andra egenskaper än *computername* , *Name* , *InstanceID* och *ID*.

### Exempel 5: Stäng en session baserat på instans-ID

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

Kommandona visar hur du stänger en **PSSession** baserat på dess instans-ID eller **RemoteRunspaceID**.

Det första kommandot använder **Get-PSSession** -cmdlet: en för att hämta **PSSessions** i den aktuella sessionen.
Den använder en pipeline-operator (|) för att skicka **PSSessions** till Format-Table-cmdlet, som formaterar deras **computername** -och **InstanceID** -egenskaper i en tabell.
Parametern *AutoSize* komprimerar kolumnerna för visning.

Från den resulterande visningen kan du identifiera **PSSession** som ska stängas och kopiera och klistra in *InstanceID* för **PSSession** i det andra kommandot.

Det andra kommandot använder cmdleten **Remove-PSSession** för att ta bort *PSSession* med angivet instans-ID.

### Exempel 6: skapa en funktion som tar bort alla sessioner i den aktuella sessionen

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

Den här funktionen tar bort alla **PSSessions** i den aktuella sessionen.
När du har lagt till den här funktionen i din PowerShell-profil, för att ta bort alla sessioner, skriver du `EndPSS` .

## PARAMETRAR

### -ComputerName

Anger en matris med namn på datorer.
Denna cmdlet stänger de **PSSessions** som är anslutna till de angivna datorerna.
Jokertecken är tillåtna.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer.
Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ContainerId

Anger en matris med ID: n för behållare. Den här cmdleten tar bort sessioner för var och en av de angivna behållarna. Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n. Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ID

Anger en matris med ID: n för sessioner.
Denna cmdlet stänger *PSSessions* med de angivna ID: na.
Skriv ett eller flera ID: n, avgränsade med kommatecken eller Använd intervall operatorn (..) för att ange ett intervall med ID: n.

Ett ID är ett heltal som unikt identifierar **PSSession** i den aktuella sessionen.
Det är enklare att komma ihåg och skriva än *InstanceID* , men det är endast unikt i den aktuella sessionen.
Om du vill hitta ID: t för en **PSSession** kör du cmdleten Get-PSSession utan parametrar.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger en matris med instans-ID: n.
Denna cmdlet stänger den **PSSessions** som har de angivna instans-ID: na.

Instans-ID är ett GUID som unikt identifierar en **PSSession** i den aktuella sessionen.
Instans-ID är unikt, även om du har flera sessioner som körs på en enda dator.

Instans-ID: t lagras i egenskapen **InstanceID** för objektet som representerar en **PSSession**.
Om du vill hitta **InstanceID** för **PSSessions** i den aktuella sessionen skriver du `Get-PSSession | Format-Table Name, ComputerName, InstanceId` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger en matris med användarvänliga namn på sessioner.
Denna cmdlet stänger den **PSSessions** som har angivna egna namn.
Jokertecken är tillåtna.

Eftersom det egna namnet på en **PSSession** kanske inte är unikt, när du använder parametern *Name* , bör du även överväga att använda parametern *whatIf* eller *Confirm* i kommandot **Remove-PSSession** .

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Session

Anger session-objekten för den **PSSessions** som ska stängas.
Ange en variabel som innehåller **PSSessions** eller ett kommando som skapar eller hämtar **PSSessions** , till exempel ett New-PSSession-eller **Get-PSSession-** kommando.
Du kan också skicka ett eller flera sessionsobjekt till **Remove-PSSession**.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMId

Anger en matris med ID för virtuella datorer.
Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.
Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – VMName

Anger en matris med namn på virtuella datorer.
Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna.
Använd cmdleten **Get-VM** för att se de virtuella datorer som är tillgängliga för dig.

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Management. Automation. körnings utrymmen. PSSession

Du kan skicka vidare ett sessionsobjekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga objekt.

## ANTECKNINGAR

* Parametern *ID* är obligatorisk. Om du vill ta bort alla **PSSessions** i den aktuella sessionen skriver du `Get-PSSession | Remove-PSSession` .
* En **PSSession** använder en permanent anslutning till en fjärrdator. Skapa en **PSSession** för att köra en serie kommandon som delar data. För mer information ange `Get-Help about_PSSessions`.
* **PSSessions** är bara aktuella för den aktuella sessionen. När du avslutar en session tvingas **PSSessions** som du skapade i sessionen att avslutas.

## RELATERADE LÄNKAR

[Anslut – PSSession](Connect-PSSession.md)

[Koppla från-PSSession](Disconnect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Ta emot – PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

