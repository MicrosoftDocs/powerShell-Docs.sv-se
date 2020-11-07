---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-computer?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Computer
ms.openlocfilehash: 54624058b57b88b820391cc5afba638aa39ff873
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345246"
---
# Rename-Computer

## SAMMANFATTNING
Byter namn på en dator.

## SYNTAX

```
Rename-Computer [-ComputerName <String>] [-PassThru] [-DomainCredential <PSCredential>]
 [-LocalCredential <PSCredential>] [-NewName] <String> [-Force] [-Restart] [-WsmanAuthentication <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Rename-Computer`Cmdleten byter namn på den lokala datorn eller en fjärrdator.
Det byter namn på en dator i varje kommando.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Byt namn på den lokala datorn

Det här kommandot byter namn på den lokala datorn till `Server044` och startar sedan om den för att ändringen ska börja gälla.

```powershell
Rename-Computer -NewName "Server044" -DomainCredential Domain01\Admin01 -Restart
```

### Exempel 2: Byt namn på en fjärran sluten dator

Det här kommandot byter namn på `Srv01` datorn till `Server001` . Datorn har inte startats om.

Parametern **DomainCredential** anger autentiseringsuppgifterna för en användare som har behörighet att byta namn på datorer i domänen.

**Force** -parametern förhindrar bekräftelse frågan.

```powershell
Rename-Computer -ComputerName "Srv01" -NewName "Server001" -DomainCredential Domain01\Admin01 -Force
```

## PARAMETRAR

### -ComputerName

Byter namn på den angivna fjärrdatorn.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ) eller `localhost` .

Den här parametern är inte beroende av PowerShell-fjärrkommunikation.
Du kan använda parametern **computername** för `Rename-Computer` även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local Computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -DomainCredential

Anger ett användar konto som har behörighet att ansluta till domänen.
Explicita autentiseringsuppgifter krävs för att byta namn på en dator som är ansluten till en domän.

Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.

Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Om du vill ange ett användar konto som har behörighet att ansluta till den dator som anges av parametern **computername** , använder du parametern **LocalCredential** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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

### -LocalCredential

Anger ett användar konto som har behörighet att ansluta till den dator som anges av parametern **computername** . Standard är den aktuella användaren.

Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.

Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Använd parametern **DomainCredential** för att ange ett användar konto som har behörighet att ansluta till domänen.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current User
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nyttnamn

Anger ett nytt namn för datorn.
Den här parametern är obligatorisk.

Standard namn får innehålla bokstäver ( `a-z` ), ( `A-Z` ), siffror ( `0-9` ) och bindestreck ( `-` ), men inte blank steg eller punkter ( `.` ). Namnet får inte bestå av enbart siffror och får inte vara längre än 63 tecken

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar kommandots resultat.
Annars genererar denna cmdlet inga utdata.

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

Anger att den här cmdleten startar om datorn som har bytt namn.
En omstart krävs ofta för att ändringen ska börja gälla.

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

### -WsmanAuthentication

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet. De acceptabla värdena för den här parametern är:

- **Basic**
- **CredSSP**
- **Standard**
- **Digest**
- **Kerberos**
- **Fram**

Standardvärdet är **default**.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!WARNING]
> Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.
> Den här mekanismen ökar säkerhets risken för Fjärråtgärden.
> Om fjärrdatorn komprometteras kan autentiseringsuppgifterna som skickas till den användas för att kontrol lera > nätverks sessionen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Den här cmdleten har inte parametrar som tar in inaktuella värden. Du kan dock skicka vidare värdena för egenskaperna **computername** och **Nyttnamn** för objekt till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. ComputerChangeInfo

Denna cmdlet returnerar ett **ComputerChangeInfo** -objekt om du anger parametern **Passthru** .
Annars returneras inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

## RELATERADE LÄNKAR

[Starta om datorn](Restart-Computer.md)

[Stoppa – dator](Stop-Computer.md)
