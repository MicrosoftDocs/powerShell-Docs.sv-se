---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 9ba056a7c85b62ac02137959a5586fdd87d9ceb4
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346317"
---
# Stop-Computer

## SAMMANFATTNING
Stoppar (stänger av) lokala och fjärranslutna datorer.

## SYNTAX

### Alla

```
Stop-Computer [-WsmanAuthentication <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Stop-Computer`Cmdleten stänger av den lokala datorn och fjärrdatorer.

Du kan använda parametrarna för `Stop-Computer` för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter och för att framtvinga en omedelbar avstängning.

## EXEMPEL

### Exempel 1: Stäng av den lokala datorn

I det här exemplet stängs den lokala datorn av.

```powershell
Stop-Computer -ComputerName localhost
```

### Exempel 2: Stäng av två fjärranslutna datorer och den lokala datorn

I det här exemplet stoppas två fjärranslutna datorer och den lokala datorn.

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

`Stop-Computer` använder parametern **computername** för att ange två fjärranslutna datorer och den lokala datorn. Varje dator stängs av.

### Exempel 3: Stäng av fjärrdatorer som bakgrunds jobb

I det här exemplet `Stop-Computer` körs som ett bakgrunds jobb på två fjärranslutna datorer.

Bakgrunds operatorn `&` kör `Stop-Computer` kommandot som ett bakgrunds jobb. Mer information finns i [about_Operators](../microsoft.powershell.core/about/about_operators.md#background-operator-).

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" &
$results = $j | Receive-Job
$results
```

`Stop-Computer` använder parametern **computername** för att ange två fjärrdatorer. `&`Bakgrunds operatorn kör kommandot som ett bakgrunds jobb. Jobb objekten lagras i `$j` variabeln.

Jobb objekt i `$j` variabeln skickas ned till pipelinen till `Receive-Job` , som hämtar jobb resultatet. Objekten lagras i `$results` variabeln. `$results`Variabeln visar jobb informationen i PowerShell-konsolen.

### Exempel 4: Stäng av en fjärran sluten dator

I det här exemplet stängs en fjärrdator med angiven autentisering.

```powershell
Stop-Computer -ComputerName "Server01" -WsmanAuthentication Kerberos
```

`Stop-Computer` använder parametern **computername** för att ange fjärrdatorn. Parametern **WsmanAuthentication** anger att Kerberos ska användas för att upprätta en fjärr anslutning.

### Exempel 5: Stäng av datorer i en domän

I det här exemplet tvingar kommandon en omedelbar avstängning av alla datorer i en angiven domän.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -Credential $c
```

`Get-Content` använder parametern **Path** för att hämta en fil i den aktuella katalogen med listan över domän datorer. Objekten lagras i `$s` variabeln.

`Get-Credential` använder parametern **Credential** för att ange autentiseringsuppgifter för en domän administratör. Autentiseringsuppgifterna lagras i `$c` variabeln.

`Stop-Computer` stänger av datorerna som anges med parametern **computername** i listan över datorer i `$s` variabeln. **Force** -parametern tvingar en omedelbar avstängning. Parametern **Credential** skickar de autentiseringsuppgifter som sparats i `$c` variabeln.

## PARAMETRAR

### -ComputerName

Anger vilka datorer som ska stoppas. Standard är den lokala datorn.

Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista. Om du vill ange den lokala datorn skriver du datorns namn eller localhost.

Den här parametern är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
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

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar fram en omedelbar avstängning av datorn.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet. Standardvärdet är **default**.

De acceptabla värdena för den här parametern är:

- Basic
- CredSSP
- Standard
- Sammandrag
- Kerberos
- Fram.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
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

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Den här cmdleten fungerar bara på Windows och använder **Win32Shutdown** -metoden i **Win32_OperatingSystem** WMI-klassen. Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.

## RELATERADE LÄNKAR

[Byt namn – dator](Rename-Computer.md)

[Starta om datorn](Restart-Computer.md)

[Test-Connection](Test-Connection.md)
