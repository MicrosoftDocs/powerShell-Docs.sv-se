---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-computersecurechannel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ComputerSecureChannel
ms.openlocfilehash: 20ea76e725a8ab53d7090078dc819a6297a639ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265323"
---
# Test-ComputerSecureChannel

## SAMMANFATTNING
Testar och reparerar den säkra kanalen mellan den lokala datorn och dess domän.

## SYNTAX

```
Test-ComputerSecureChannel [-Repair] [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **test-ComputerSecureChannel** verifierar att kanalen mellan den lokala datorn och dess domän fungerar som den ska genom att kontrol lera status för dess förtroende relationer.
Om anslutningen Miss lyckas kan du använda *reparations* parametern för att försöka återställa den.

**Test-ComputerSecureChannel** returnerar $true om kanalen fungerar korrekt och $false om den inte är det.
Detta innebär att du kan använda-cmdleten i villkorliga uttryck i funktioner och skript.
Använd *verbose* -parametern för att få mer detaljerade test resultat.

Denna cmdlet fungerar ungefär som NetDom.exe.
Både NetDom och **test-ComputerSecureChannel** använder tjänsten **Netlogon** för att utföra åtgärderna.

## EXEMPEL

### Exempel 1: testa en kanal mellan den lokala datorn och dess domän

```
PS C:\> Test-ComputerSecureChannel
True
```

Det här kommandot testar kanalen mellan den lokala datorn och den domän som den är ansluten till.

### Exempel 2: testa en kanal mellan den lokala datorn och en domänkontrollant

```
PS C:\> Test-ComputerSecureChannel -Server "DCName.fabrikam.com"
True
```

Det här kommandot anger en prioriterad domänkontrollant för testet.

### Exempel 3: återställa kanalen mellan den lokala datorn och dess domän

```
PS C:\> Test-ComputerSecureChannel -Repair
True
```

Det här kommandot återställer kanalen mellan den lokala datorn och dess domän.

### Exempel 4: Visa detaljerad information om testet

```
PS C:\> Test-ComputerSecureChannel -verbose
VERBOSE: Performing operation "Test-ComputerSecureChannel" on Target "SERVER01".
True
VERBOSE: "The secure channel between 'SERVER01' and 'net.fabrikam.com' is alive and working correctly."
```

Detta kommando använder den *utförliga* gemensamma parametern för att begära detaljerade meddelanden om åtgärden.
Mer information om *verbose* finns about_CommonParameters.

### Exempel 5: testa en anslutning innan du kör ett skript

```
PS C:\> Set-Alias tcsc Test-ComputerSecureChannel
if (!(tcsc))
{Write-Host "Connection failed. Reconnect and retry."}
else { &(.\Get-Servers.ps1) }
```

Det här exemplet visar hur du använder **test-ComputerSecureChannel** för att testa en anslutning innan du kör ett skript som kräver anslutningen.

Det första kommandot använder cmdleten Set-Alias för att skapa ett alias för cmdlet-namnet.
Detta sparar utrymme och förhindrar skrivfel.

Instruktionen **IF** kontrollerar värdet som **test-ComputerSecureChannel** returnerar innan ett skript körs.

## PARAMETRAR

### -Credential
Anger ett användar konto som har behörighet att utföra den här åtgärden.
Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som Get-Credential cmdlet returnerar.
Som standard använder cmdleten autentiseringsuppgifterna för den aktuella användaren.

Parametern *Credential* är utformad för att användas i kommandon som använder *Repair* -parametern för att reparera kanalen mellan datorn och domänen.

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

### -Reparera
Anger att den här cmdleten tar bort och sedan återupprättar kanalen som upprättats av tjänsten NetLogon.
Använd den här parametern om du vill försöka återställa en anslutning som har misslyckats med testet.

Om du vill använda den här parametern måste den aktuella användaren vara medlem i gruppen Administratörer på den lokala datorn.

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

### -Server
Anger den domänkontrollant som ska köra kommandot.
Om den här parametern inte anges, väljer denna cmdlet en Standarddomänkontrollant för åtgärden.

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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Boolean
Den här cmdleten returnerar $True om anslutningen fungerar korrekt och $False om den inte är det.

## ANTECKNINGAR

* Om du vill köra ett **test-ComputerSecureChannel** kommando i Windows Vista och senare versioner av Windows operativ system öppnar du Windows PowerShell med alternativet Kör som administratör.
* **Test-ComputerSecureChannel** implementeras med hjälp av funktionen **I_NetLogonControl2** som styr olika aspekter av tjänsten Netlogon.

## RELATERADE LÄNKAR

[Checkpoint-Computer](Checkpoint-Computer.md)

[Återställ-ComputerMachinePassword](Reset-ComputerMachinePassword.md)

[Starta om datorn](Restart-Computer.md)

[Stoppa – dator](Stop-Computer.md)
