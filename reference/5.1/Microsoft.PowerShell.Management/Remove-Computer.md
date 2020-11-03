---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/04/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Computer
ms.openlocfilehash: 89e43220a8d5ac675ea232db09cf3edec2ca2b97
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265485"
---
# Remove-Computer

## SAMMANFATTNING
Tar bort den lokala datorn från dess domän.

## SYNTAX

### Lokalt (standard)

```
Remove-Computer [[-UnjoinDomainCredential] <PSCredential>] [-Restart] [-Force] [-PassThru]
 [-WorkgroupName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Fjärransluten

```
Remove-Computer -UnjoinDomainCredential <PSCredential> [-LocalCredential <PSCredential>] [-Restart]
 [-ComputerName <String[]>] [-Force] [-PassThru] [-WorkgroupName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Remove-Computer`Cmdleten tar bort den lokala datorn och fjärrdatorerna från deras aktuella domäner.

När du tar bort en dator från en domän `Remove-Computer` inaktive ras även domän kontot för datorn. Du måste ange explicita autentiseringsuppgifter för att kunna koppla från datorn från dess domän, även om de är autentiseringsuppgifterna för den aktuella användaren. Du måste starta om datorn för att ändringen ska börja gälla. När du tar bort en dator från en domän måste du också flytta den till en arbets grupp. Använd parametern **WorkgroupName** för att ange arbets gruppen.

Om du vill flytta en dator från en arbets grupp till en domän, från en arbets grupp till en annan, eller från en domän till en annan, använder du `Add-Computer` cmdleten.

Om du vill hämta resultatet av kommandot använder du parametrarna **verbose** och **Passthru** . Använd **Force** -parametern för att utelämna användar frågan.

`Remove-Computer` tar bort den lokala datorn och fjärrdatorer från domäner. Den innehåller parametrar för autentiseringsuppgifter som anger alternativa autentiseringsuppgifter för att ansluta till fjärrdatorer och att koppla från en domän, en **omstarts** parameter för att starta om de berörda datorerna och en **WorkgroupName** -parameter för att ange namnet på arbets gruppen som datorer läggs till i.

## EXEMPEL

### Exempel 1: ta bort den lokala datorn från dess domän

Det här exemplet tar bort den lokala datorn från den domän som den är ansluten till.

```powershell
Remove-Computer -UnjoinDomaincredential Domain01\Admin01 -PassThru -Verbose -Restart
```

Parametern **UnjoinDomainCredential** innehåller autentiseringsuppgifterna för en domän administratör. **Passthru** och de **utförliga** gemensamma parametrarna visar information om kommandot lyckades eller misslyckades. Parametern **restart** startar om datorn för att slutföra borttagnings åtgärden.

När inget arbets grupps namn har angetts flyttas datorn till arbets gruppen med namnet när den har tagits bort från domänen.

### Exempel 2: flytta flera datorer till en äldre arbets grupp

Det här exemplet tar bort alla datorer som listas i `OldServers.txt` filen från sina domäner och flyttar dem till den **äldre** arbets gruppen.

```powershell
Remove-Computer -ComputerName (Get-Content OldServers.txt) -LocalCredential Domain01\Admin01 -UnJoinDomainCredential Domain01\Admin01 -WorkgroupName "Legacy" -Force -Restart
```

Parametern **LocalCredential** innehåller autentiseringsuppgifterna för en användare som har behörighet att ansluta till fjärrdatorer. Parametern **UnjoinDomainCredential** innehåller autentiseringsuppgifterna för en användare som har behörighet att ta bort datorerna från sina domäner. **Force** -parametern utelämnar bekräftelse frågorna för varje dator. Parametern **restart** startar om var och en av datorerna när den har tagits bort från domänen.

### Exempel 3: ta bort datorer från en arbets grupp utan bekräftelse

Det här exemplet tar bort fjärrdatorn, Server01 och den lokala datorn från deras domäner och lägger till dem i den **lokala** arbets gruppen.

```powershell
Remove-Computer -ComputerName "Server01", "localhost" -UnjoinDomainCredential Domain01\Admin01 -WorkgroupName "Local" -Restart -Force
```

**Force** -parametern undertrycker bekräftelse frågan för varje dator. Parametern **restart** startar om datorerna för att ändringen ska börja gälla.

## PARAMETRAR

### -ComputerName

Anger vilka datorer som ska tas bort från sina domäner. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för fjärrdatorerna. Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** för `Remove-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Force

Förhindrar att användaren tillfrågas. Som standard `Remove-Computer` uppmanas du att bekräfta innan du tar bort varje dator.

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

### -LocalCredential

Anger ett användar konto som har behörighet att ansluta till de datorer som parametern **computername** anger. Standard är den aktuella användaren.

Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten. Om du anger ett användar namn, uppmanas du att ange ett lösen ord för cmdleten. Använd parametern **UnjoinDomainCredential** om du vill ange ett användar konto som har behörighet att ta bort datorn från den aktuella domänen.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Remote
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar kommandots resultat. Annars genererar denna cmdlet inga utdata.

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

### -Restart

Anger att den här cmdleten startar om de datorer som tas bort. En omstart krävs ofta för att ändringen ska börja gälla.

Den här parametern introducerades i PowerShell 3,0.

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

### -UnjoinDomainCredential

Anger ett användar konto som har behörighet att ta bort datorerna från deras aktuella domäner.
Explicita autentiseringsuppgifter som anges i den här parametern krävs för att ta bort fjärrdatorer från en domän, även om värdet är den aktuella användarens autentiseringsuppgifter.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, t. ex. ett som genereras av `Get-Credential` . Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Använd parametern **LocalCredential** för att ange ett användar konto som har behörighet att ansluta till fjärrdatorerna.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Local, Remote
Aliases: Credential

Required: False (Local), True (Remote)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WorkgroupName

Anger namnet på en arbets grupp som datorerna läggs till i när de tas bort från deras domäner. Standardvärdet är **Workgroup**. När du tar bort en dator från en domän måste du lägga till den i en arbets grupp.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
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

### System. String

Du kan skicka pipe-dator namn till thiscmdlet.

## UTDATA

### Microsoft. PowerShell. commands. ComputerChangeInfo

När du använder parametern **Passthru** `Remove-Computer` returnerar ett **ComputerChangeInfo** -objekt.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Den här cmdleten tar inte bort datorer från arbets grupper.

## RELATERADE LÄNKAR

[Lägg till dator](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Ta bort dator](Remove-Computer.md)

[Byt namn – dator](Rename-Computer.md)

[Starta om datorn](Restart-Computer.md)

[Återställa-dator](Restore-Computer.md)

[Stoppa – dator](Stop-Computer.md)

[Test-Connection](Test-Connection.md)
