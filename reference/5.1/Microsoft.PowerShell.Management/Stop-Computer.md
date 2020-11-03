---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268227"
---
# Stop-Computer

## SAMMANFATTNING
Stoppar (stänger av) lokala och fjärranslutna datorer.

## SYNTAX

### Alla

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Stop-Computer`Cmdleten stänger av den lokala datorn och fjärrdatorer.

Du kan använda parametrarna för `Stop-Computer` för att köra avstängnings åtgärderna som ett bakgrunds jobb, för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter, för att begränsa de samtidiga anslutningar som skapas för att köra kommandot och framtvinga en omedelbar avstängning.

Denna cmdlet kräver inte PowerShell-fjärrkommunikation om du inte använder parametern **AsJob** .

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

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

`Stop-Computer` använder parametern **computername** för att ange två fjärrdatorer. Parametern **AsJob** kör kommandot som ett bakgrunds jobb. Jobb objekten lagras i `$j` variabeln.

Jobb objekt i `$j` variabeln skickas ned till pipelinen till `Receive-Job` , som hämtar jobb resultatet. Objekten lagras i `$results` variabeln. `$results`Variabeln visar jobb informationen i PowerShell-konsolen.

Eftersom **AsJob** skapar jobbet på den lokala datorn och automatiskt returnerar resultaten till den lokala datorn, kan du köra `Receive-Job` som ett lokalt kommando.

### Exempel 4: Stäng av en fjärran sluten dator

I det här exemplet stängs en fjärrdator med angiven autentisering.

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Stop-Computer` använder parametern **computername** för att ange fjärrdatorn. **Personifiering** -parametern anger en anpassad personifiering och **DcomAuthentication** -parametern anger inställningar på autentiserings nivå.

### Exempel 5: Stäng av datorer i en domän

I det här exemplet tvingar kommandon en omedelbar avstängning av alla datorer i en angiven domän.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

`Get-Content` använder parametern **Path** för att hämta en fil i den aktuella katalogen med listan över domän datorer. Objekten lagras i `$s` variabeln.

`Get-Credential` använder parametern **Credential** för att ange autentiseringsuppgifter för en domän administratör. Autentiseringsuppgifterna lagras i `$c` variabeln.

`Stop-Computer` stänger av datorerna som anges med parametern **computername** i listan över datorer i `$s` variabeln. **Force** -parametern tvingar en omedelbar avstängning. Parametern **ThrottleLimit** begränsar kommandot till 10 samtidiga anslutningar. Parametern **Credential** skickar de autentiseringsuppgifter som sparats i `$c` variabeln.

## PARAMETRAR

### – AsJob

Anger att denna cmdlet körs som ett bakgrunds jobb.

Om du vill använda den här parametern måste lokal och fjärran sluten dator konfigureras för fjärr kommunikation och, i Windows Vista och senare versioner av Windows-operativsystemet, måste du öppna PowerShell med alternativet **Kör som administratör** . Mer information finns i [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md).

När du anger parametern **AsJob** returnerar kommandot omedelbart ett objekt som representerar bakgrunds jobbet. Du kan fortsätta att arbeta i sessionen medan jobbet är klart. Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn. Använd cmdleten för att hämta jobb resultatet `Receive-Job` .

Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) och [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md).

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

### -DcomAuthentication

Anger den autentiseringsnivå som denna cmdlet använder med WMI. `Stop-Computer` använder WMI. Standardvärdet är **paket**.

De acceptabla värdena för den här parametern är:

- **Standard** : Windows-autentisering.
- **Ingen** : ingen com-autentisering.
- **Anslut** : com-autentisering på anslutnings nivå.
- **Anropa** : com-autentisering på anrops nivå.
- **Paket** : com-autentisering på paket nivå.
- **PacketIntegrity** : com-autentisering på paket integritets nivå.
- **PacketPrivacy** : com-autentisering på paket sekretess nivå.
- **Oförändrad** : samma som föregående kommando.

Mer information om värdena för den här parametern finns i [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel).

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
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

### -Personifiering

Anger personifieringsnivån som ska användas när den här cmdleten anropar WMI. Standardvärdet är **personifierat**.

`Stop-Computer` använder WMI. De acceptabla värdena för den här parametern är:

- **Standard** : standard-personifiering.
- **Anonym** : döljer anroparens identitet.
- **Identifiera** : tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.
- **Personifiera** : tillåter att objekt använder autentiseringsuppgifterna för anroparen.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Anger vilket protokoll som ska användas för att starta om datorerna. De acceptabla värdena för den här parametern är: **WSMan** och **DCOM**. Standardvärdet är **DCOM**.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.

Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet. Standardvärdet är **default**.

De acceptabla värdena för den här parametern är:

- Basic
- CredSSP
- Default
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

### Ingen eller system. Management. Automation. RemotingJob

Cmdleten returnerar ett **system. Management. Automation. RemotingJob** -objekt om du anger parametern **AsJob** . Annars genererar den inga utdata.

## ANTECKNINGAR

Denna cmdlet använder metoden **Win32Shutdown** i klassen **Win32_OperatingSystem** WMI. Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.

## RELATERADE LÄNKAR

[Lägg till dator](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Ta bort dator](Remove-Computer.md)

[Byt namn – dator](Rename-Computer.md)

[Starta om datorn](Restart-Computer.md)

[Återställa-dator](Restore-Computer.md)

[Test-Connection](Test-Connection.md)
