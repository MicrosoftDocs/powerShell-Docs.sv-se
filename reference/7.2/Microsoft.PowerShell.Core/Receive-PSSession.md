---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 4bc7ba3a8129dd332b13bee30e386dd459d92226
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710464"
---
# Receive-PSSession

## SAMMANFATTNING

Hämtar resultat från kommandon i frånkopplade sessioner

## SYNTAX

### Session (standard)

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### Id

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ComputerSessionName

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerInstanceId

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriSessionName

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### SessionName

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Receive-PSSession`Cmdlet: en hämtar resultatet av kommandon som körs i PowerShell-sessioner (**PSSession**) som kopplades från. Om sessionen är ansluten `Receive-PSSession` hämtar resultatet från kommandon som kördes när sessionen kopplades från. Om sessionen fortfarande kopplas från `Receive-PSSession` ansluter du till sessionen, återupptar alla kommandon som har pausats och hämtar resultatet av kommandon som körs i sessionen.

Denna cmdlet introducerades i PowerShell 3,0.

Du kan använda en `Receive-PSSession` förutom eller i stället för ett `Connect-PSSession` kommando.
`Receive-PSSession` kan ansluta till en frånkopplad eller Återansluten session som startades i andra sessioner eller på andra datorer.

`Receive-PSSession` fungerar på **PSSessions** som kopplades bort avsiktligt med hjälp av `Disconnect-PSSession` cmdleten eller `Invoke-Command` parametern **InDisconnectedSession** . Eller frånkopplad oavsiktligt av ett nätverks avbrott.

Om du använder `Receive-PSSession` cmdleten för att ansluta till en session där inga kommandon körs eller pausas, `Receive-PSSession` ansluter till sessionen, men returnerar inga utdata eller fel.

Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).

Några exempel använder ihopbuntning för att minska rad längden och förbättra läsbarheten. Mer information finns i [about_Splatting](./About/about_Splatting.md).

## EXEMPEL

### Exempel 1: Anslut till en PSSession

Det här exemplet ansluter till en session på en fjärrdator och hämtar resultatet från kommandon som körs i en session.

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

`Receive-PSSession`Anger den fjärranslutna datorn med parametern **computername** . Parametern **Name** identifierar ITTask-sessionen på Server01-datorn. Exemplet hämtar resultatet från kommandon som kördes i ITTask-sessionen.

Eftersom kommandot inte använder **mål** parametern, visas resultaten på kommando raden.

### Exempel 2: få resultat från alla kommandon på frånkopplade sessioner

I det här exemplet hämtas resultatet av alla kommandon som körs i alla frånkopplade sessioner på två fjärrdatorer.

Om någon session inte är frånkopplad eller inte körs, `Receive-PSSession` ansluter inte till sessionen och returnerar inga utdata eller fel.

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

`Get-PSSession` använder parametern **computername** för att ange fjärrdatorer. Objekten skickas ned pipelinen till `Receive-PSSession` .

### Exempel 3: Hämta resultatet av ett skript som körs i en session

I det här exemplet används `Receive-PSSession` cmdleten för att hämta resultatet av ett skript som kördes i en fjärrdators session.

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

Kommandot använder parametrarna **computername** och **Name** för att identifiera den frånkopplade sessionen.
Den använder en **mål** parameter med ett värde för jobbet att dirigera `Receive-PSSession` för att returnera resultaten som ett jobb. Parametern **JobName** anger ett namn för jobbet i den återanslutna sessionen.
Parametern **Credential** kör `Receive-PSSession` kommandot med behörigheterna för en domän administratör.

Utdata visar att `Receive-PSSession` de returnerade resultaten som ett jobb i den aktuella sessionen. Hämta jobb resultatet med ett `Receive-Job` kommando

### Exempel 4: få resultat efter ett nätverks avbrott

I det här exemplet används `Receive-PSSession` cmdleten för att hämta resultatet av ett jobb när ett nätverks avbrott stör en session-anslutning. PowerShell försöker automatiskt återansluta sessionen en gång per sekund under de närmaste fyra minuterna och överger bara arbets insatsen om alla försök i fyra minuter Miss lyckas.

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

`New-PSSession`Cmdleten skapar en session på Server01-datorn och sparar sessionen i `$s` variabeln. `$s`Variabeln visar att **statusen** är öppen och **att tillgängligheten** är tillgänglig. Dessa värden anger att du är ansluten till sessionen och att du kan köra kommandon i sessionen.

`Invoke-Command`Cmdleten kör ett skript i sessionen i `$s` variabeln. Skriptet börjar köra och returnera data, men ett nätverks avbrott inträffar som avbryter sessionen. Användaren måste avsluta sessionen och starta om den lokala datorn.

När datorn startas om startar användaren PowerShell och kör ett `Get-PSSession` kommando för att hämta sessioner på Server01-datorn. Utdata visar att **AD** -sessionen fortfarande finns på Server01-datorn. **Statusen** anger att **AD** -sessionen är frånkopplad. **Tillgänglighet** svärdet none innebär att sessionen inte är ansluten till några klientsessioner.

`Receive-PSSession`Cmdleten återansluter till **AD** -sessionen och hämtar resultatet från skriptet som kördes i sessionen. Kommandot använder **mål** parametern för att begära resultatet i ett jobb med namnet **ADJob**. Kommandot returnerar ett jobb objekt och utdata indikerar att skriptet fortfarande körs.

`Get-PSSession`Cmdleten används för att kontrol lera jobb status. Utdata bekräftar att `Receive-PSSession` cmdleten återansluter till **AD** -sessionen, som nu är öppen och tillgänglig för kommandon. Och skriptet återupptog körningen och hämtar skript resultatet.

### Exempel 5: Återanslut till frånkopplade sessioner

I det här exemplet används `Receive-PSSession` cmdleten för att återansluta till sessioner som avsiktligt kopplats från och hämta resultatet av jobb som kördes i sessionerna.

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

`Invoke-Command`Cmdleten kör ett skript på tre fjärrdatorer. Eftersom skriptet samlar in och sammanfattar data från flera databaser, tar det ofta skriptet en längre tid att slutföra. Kommandot använder parametern **InDisconnectedSession** som startar skripten och kopplar sedan omedelbart från sessionerna. Parametern **SessionOption** utökar **idleTimeout** -värdet för den frånkopplade sessionen. Frånkopplade sessioner anses vara inaktiva från det ögonblick då de är frånkopplade. Det är viktigt att ange tids gränsen för inaktivitet för tillräckligt länge så att kommandona kan slutföras och du kan återansluta till sessionen. Du kan bara ange **idleTimeout** när du skapar **PSSession** och bara ändrar den när du kopplar från den. Du kan inte ändra **idleTimeout** -värdet när du ansluter till en **PSSession** eller tar emot resultatet. När du har kört kommandot avslutar användaren PowerShell och stänger datorn.

Nästa dag återupptar användaren Windows, startar PowerShell och använder `Get-PSSession` för att hämta de sessioner där skripten kördes. Kommandot identifierar sessionerna med dator namnet, sessionsnamnet och namnet på sessionen och sparar sessionerna i `$s` variabeln. Värdet för `$s` variabeln visas och visar att sessionerna är frånkopplade, men inte är upptagna.

`Receive-PSSession`Cmdleten ansluter till sessionerna i `$s` variabeln och hämtar resultatet.
Kommandot sparar resultatet i `$Results` variabeln. `$s`Variabeln visas och visar att sessionerna är anslutna och tillgängliga för kommandon.

Skript resultatet i `$Results` variabeln visas i PowerShell-konsolen. Om något av resultaten är oväntat kan användaren köra kommandon i sessionerna för att undersöka rotor saken.

### Exempel 6: köra ett jobb i en frånkopplad session

Det här exemplet visar vad som händer med ett jobb som körs i en frånkopplad session.

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

`New-PSSession`Cmdleten skapar Testsessionen på Server01-datorn. Kommandot sparar sessionen i `$s` variabeln.

`Invoke-Command`Cmdleten kör ett kommando i sessionen i `$s` variabeln. Kommandot använder parametern **AsJob** för att köra kommandot som ett jobb och skapar jobbobjektet i den aktuella sessionen.
Kommandot returnerar ett jobb objekt som har sparats i `$j` variabeln. `$j`Variabeln visar jobbobjektet.

Session-objektet i `$s` variabeln skickas till pipelinen till `Disconnect-PSSession` och sessionen kopplas från.

`$j`Variabeln visas och visar effekterna av att koppla bort jobbobjektet i `$j` variabeln. Jobbets tillstånd är nu frånkopplat.

`Receive-Job`Körs på jobbet i `$j` variabeln. Utdata visar att jobbet började returnera utdata innan sessionen och jobbet kopplades från.

`Connect-PSSession`Cmdleten körs i samma klient-session. Kommandot återansluter till Testsessionen på Server01-datorn och sparar sessionen i `$s2` variabeln.

`Receive-PSSession`Cmdlet: en hämtar resultatet av jobbet som kördes i sessionen. Eftersom kommandot körs i samma session `Receive-PSSession` returnerar resultatet som ett jobb som standard och återanvänder samma jobb objekt. Kommandot sparar jobbet i `$j2` variabeln. `Receive-Job`Cmdlet: en hämtar resultatet av jobbet i `$j` variabeln.

## PARAMETRAR

### -AllowRedirection

Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).

När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI. Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern för att aktivera den för att omdirigera anslutningen.

Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session. Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln. Standardvärdet är 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Anger ett program. Denna cmdlet ansluter bara till sessioner som använder det angivna programmet.

Ange program namns segmentet för anslutnings-URI: n. Till exempel är WSMan i följande anslutnings-URI program namnet: `http://localhost:5985/WSMAN` .

Program namnet för en session lagras i egenskapen **körnings utrymme. ConnectionInfo. APPNAME** för sessionen.

Parameterns värde används för att välja och filtrera sessioner. Den ändrar inte det program som används av sessionen.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Autentisering

Anger mekanismen som används för att autentisera användarautentiseringsuppgifter i kommandot för att återansluta till en frånkopplad session. De acceptabla värdena för den här parametern är:

- Standardvärde
- Grundläggande
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Standardvärdet är default.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!CAUTION]
> CredSSP-autentisering (Credential Security Support Provider), där användarautentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att ansluta till den frånkopplade sessionen. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. Certifikat kan endast mappas till lokala användar konton och fungerar inte med domän konton.

Om du vill hämta ett tumavtryck för certifikatet använder du ett `Get-Item` eller- `Get-ChildItem` kommando i PowerShell- `Cert:` enheten.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger den dator där den frånkopplade sessionen lagras. Sessioner lagras på den dator som finns på Server sidan eller tar emot en anslutning till slutet. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en dator.
Jokertecken är inte tillåtna. Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ), `$env:COMPUTERNAME` eller localhost.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – ConfigurationName

Anger namnet på en konfiguration av sessionen. Denna cmdlet ansluter bara till sessioner som använder den angivna sessionen.

Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen. Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix:

`http://schemas.microsoft.com/powershell`.

Konfigurations namnet för en session lagras i sessionens **ConfigurationName** -egenskap.

Parameterns värde används för att välja och filtrera sessioner. Den ändrar inte den sessionsinformation som sessionen använder.

För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](./About/about_Session_Configurations.md).

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Anger en URI som definierar den anslutnings slut punkt som används för att återansluta till den frånkopplade sessionen.

URI: n måste vara fullständigt kvalificerad. Strängens format är följande:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

Standardvärdet är följande:

`http://localhost:5985/WSMAN`

Om du inte anger en anslutnings-URI kan du använda parametrarna **UseSSL**, **computername**, **port** och **ApplicationName** för att ange anslutnings-URI-värden.

Giltiga värden för URI: n i **transport** segmentet är http och https. Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.

Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att ansluta till den frånkopplade sessionen. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger ID för en frånkopplad session. **ID-** parametern fungerar bara när den frånkopplade sessionen tidigare var ansluten till den aktuella sessionen.

Den här parametern är giltig, men inte effektiv, när sessionen lagras på den lokala datorn, men inte var ansluten till den aktuella sessionen.

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID för den frånkopplade sessionen. Instans-ID är ett GUID som unikt identifierar en **PSSession** på en lokal eller fjärran sluten dator. Instans-ID: t lagras i egenskapen **InstanceID** i **PSSession**.

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – JobName

Anger ett eget namn för jobbet som `Receive-PSSession` returneras.

`Receive-PSSession` Returnerar ett jobb när värdet för **mål** parametern är Job eller jobbet som körs i den frånkopplade sessionen startades i den aktuella sessionen.

Om jobbet som körs i den frånkopplade sessionen startades i den aktuella sessionen återanvänder PowerShell det ursprungliga jobbobjektet i sessionen och ignorerar värdet för parametern **JobName** .

Om jobbet som körs i den frånkopplade sessionen startades i en annan session, skapar PowerShell ett nytt jobb objekt. Ett standard namn används, men du kan använda den här parametern för att ändra namnet.

Om standardvärdet eller det explicita värdet för **mål** parametern inte är jobb, lyckas kommandot, men parametern **JobName** har ingen påverkan.

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

### -Name

Anger det egna namnet på den frånkopplade sessionen.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Mål

Anger hur sessionens resultat returneras. De acceptabla värdena för den här parametern är:

- **Jobb**. Returnerar resultatet asynkront i ett jobb objekt. Du kan använda parametern **JobName** för att ange ett namn eller ett nytt namn för jobbet.
- **Värd**. Returnerar resultaten till kommando raden (synkront). Om kommandot återupptas eller om resultatet består av ett stort antal objekt, kan svaret vara försenat.

Standardvärdet för **mål** parametern är Host. Om kommandot som tas emot i en frånkopplad session startades i den aktuella sessionen, är standardvärdet för **mål** parametern det formulär där kommandot startades. Om kommandot startades som ett jobb returneras det som standard som ett jobb. Annars returneras de till värd programmet som standard.

Normalt visar värd programmet returnerade objekt på kommando raden utan fördröjning, men det här beteendet kan variera.

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger fjärrdatorns nätverks port som används för att återansluta till sessionen. Om du vill ansluta till en fjärrdator måste den lyssna på porten som anslutningen använder. Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten. Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Använd inte **port** parametern om det inte behövs. Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger den frånkopplade sessionen. Ange en variabel som innehåller **PSSession** eller ett kommando som skapar eller hämtar **PSSession**, till exempel ett `Get-PSSession` kommando.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Anger avancerade alternativ för sessionen. Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.

Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.

En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` . Information om variabeln **$PSSessionOption** finns i [about_Preference_Variables](./About/about_Preference_Variables.md). För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](./About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerSessionName, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Anger att denna cmdlet använder Secure Sockets Layer (SSL)-protokollet för att ansluta till den frånkopplade sessionen. Som standard används inte SSL.

WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket. **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.

Om du använder den här parametern och SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerSessionName
Aliases:

Required: False
Position: Named
Default value: False
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

### System. Management. Automation. körnings utrymmen. PSSession

Du kan skicka pipe-sessionsobjekt till denna cmdlet, till exempel objekt som returneras av `Get-PSSession` cmdleten.

### System. Int32

Du kan skicka pipe-sessions-ID: n till denna cmdlet.

### System. GUID

Du kan skicka vidare instans-ID för sessioner denna cmdlet.

### System. String

Du kan skicka pipe-sessionsnamn till denna cmdlet.

## UTDATA

### System. Management. Automation. job eller PSObject

Den här cmdleten returnerar resultatet av kommandon som kördes i den frånkopplade sessionen, om det finns några. Om värdet eller standardvärdet för **mål** parametern är Job, `Receive-PSSession` returnerar ett Job-objekt. Annars returneras objekt som representerar kommando resultatet.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

`Receive-PSSession` hämtar endast resultat från sessioner som kopplats från. Endast sessioner som är anslutna till eller avslutas på datorer som kör PowerShell 3,0 eller senare versioner kan kopplas från och återanslutas.

Om kommandona som kördes i den frånkopplade sessionen inte genererade resultat eller om resultatet redan returnerades till en annan session, `Receive-PSSession` genererar inga utdata.

En sessions buffer buffer-läge avgör hur kommandon i sessionen hanterar utdata när sessionen kopplas från. När värdet för **OutputBufferingMode** -alternativet för sessionen släpps och utdatabufferten är full börjar kommandot Ta bort utdata. `Receive-PSSession` Det går inte att återställa utdata. Mer information om alternativet utdata buffation mode finns i hjälp artiklarna för cmdletarna [New-PSSessionOption](New-PSSessionOption.md) och [New-PSTransportOption](New-PSTransportOption.md) .

Du kan inte ändra timeout-värdet för inaktivitet för en **PSSession** när du ansluter till **PSSession** eller ta emot resultat. Parametern **SessionOption** för `Receive-PSSession` använder ett **SessionOption** -objekt som har ett **idleTimeout** -värde. Men **idleTimeout** -värdet för objektet **SessionOption** och **idleTimeout** -värdet för `$PSSessionOption` variabeln ignoreras när det ansluter till en **PSSession** eller tar emot resultat.

- Du kan ange och ändra tids gränsen för inaktivitet i en **PSSession** när du skapar **PSSession**, genom att använda `New-PSSession` `Invoke-Command` cmdletarna eller och när du kopplar bort från **PSSession**.
- Egenskapen **idleTimeout** för en **PSSession** är kritisk för frånkopplade sessioner eftersom den fastställer hur länge en frånkopplad session ska bevaras på fjärrdatorn. Frånkopplade sessioner anses vara inaktiva från det ögonblick då de kopplas från, även om kommandon körs i den frånkopplade sessionen.

Om du startar ett jobb i en fjärrsession med hjälp av parametern **AsJob** i `Invoke-Command` cmdleten, skapas jobbobjektet i den aktuella sessionen, även om jobbet körs i fjärrsessionen. Om du kopplar från fjärrsessionen kopplas jobbobjektet i den aktuella sessionen bort från jobbet. Jobbobjektet innehåller alla resultat som returnerades till det, men som inte får nya resultat från jobbet i den frånkopplade sessionen.

Om en annan klient ansluter till sessionen som innehåller det jobb som körs är de resultat som levererades till det ursprungliga jobbobjektet i den ursprungliga sessionen inte tillgängliga i den nyligen anslutna sessionen. Endast resultat som inte levererades till det ursprungliga jobbobjektet är tillgängliga i den återanslutna sessionen.

På samma sätt, om du startar ett skript i en session och sedan kopplar bort från sessionen, kommer alla resultat som skriptet levererar till sessionen innan från koppling inte är tillgängliga för en annan klient som ansluter till sessionen.

Använd parametern **InDisconnectedSession** för cmdleten för att förhindra data förlust i sessioner som du vill koppla från `Invoke-Command` . Eftersom den här parametern förhindrar att resultat returneras till den aktuella sessionen, är alla resultat tillgängliga när sessionen återansluts.

Du kan även förhindra data förlust genom att använda `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i fjärrsessionen. I det här fallet skapas jobbobjektet i fjärrsessionen. Du kan inte använda `Receive-PSSession` cmdlet: en för att hämta jobb resultatet. Använd i stället cmdlet: en `Connect-PSSession` för att ansluta till sessionen och Använd sedan `Invoke-Command` cmdleten för att köra ett `Receive-Job` kommando i sessionen.

När en session som innehåller ett jobb som körs är frånkopplad och sedan ansluts igen återanvänds det ursprungliga jobbobjektet endast om jobbet är frånkopplat och återanslutits till samma session, och kommandot för att återansluta inte anger ett nytt jobbnamn. Om sessionen återansluts till en annan klientsession eller om ett nytt jobbnamn anges, skapar PowerShell ett nytt jobb objekt för den nya sessionen.

När du kopplar från en **PSSession** kopplas sessionstillståndet ned och tillgängligheten är ingen.

- Värdet för egenskapen **State** är i förhållande till den aktuella sessionen. Värdet frånkopplat innebär att **PSSession** inte är ansluten till den aktuella sessionen. Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner. Den kan vara ansluten till en annan session.
  Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.
- **Tillgänglighet** svärdet none anger att du kan ansluta till sessionen. Värdet upptagen anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.
- Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate).
- Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

## RELATERADE LÄNKAR

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Session_Configurations](./About/about_Session_Configurations.md)

[Anslut – PSSession](Connect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Remove-PSSession](Remove-PSSession.md)
