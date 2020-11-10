---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: cee14ce93af87d33b4d9d9665c3ef5aaa2aec1d5
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387455"
---
# Get-PSSession

## SAMMANFATTNING
Hämtar PowerShell-sessioner på lokala och fjärranslutna datorer.

## SYNTAX

### Namn (standard)

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### ComputerInstanceId

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ComputerName

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-ThrottleLimit <Int32>] [-State <SessionFilterState>]
 [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUri

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-ThrottleLimit <Int32>] [-State <SessionFilterState>]
 [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### VMName

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### Hålla

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### ContainerIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### VMId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -VMId <Guid[]> [<CommonParameters>]
```

### VMIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMId <Guid[]> [<CommonParameters>]
```

### VMNameInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### InstanceId

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### Id

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## BESKRIVNING

`Get-PSSession`Cmdleten hämtar de användare-hanterade PowerShell-sessionerna ( **PSSessions** ) på lokala datorer och fjärrdatorer.

Från och med Windows PowerShell 3,0 lagras sessioner på datorerna i fjärrparten för varje anslutning. Du kan använda parametrarna **computername** eller **ConnectionUri** för `Get-PSSession` för att hämta de sessioner som ansluter till den lokala datorn eller fjärrdatorer, även om de inte har skapats i den aktuella sessionen.

Utan parametrar `Get-PSSession` hämtar alla sessioner som har skapats i den aktuella sessionen.

Använd filtrerings parametrarna, inklusive **namn** , **ID** , **InstanceID** , **State** , **ApplicationName** och **ConfigurationName** för att välja bland de sessioner som `Get-PSSession` returneras.

Använd de återstående parametrarna för att konfigurera den tillfälliga anslutning där `Get-PSSession` kommandot körs när du använder parametrarna **computername** eller **ConnectionUri** .

Obs: i Windows PowerShell 2,0, utan parametrar, `Get-PSSession` hämtas alla sessioner som har skapats i den aktuella sessionen. Parametern **computername** hämtar sessioner som har skapats i den aktuella sessionen och anslutit till den angivna datorn.

Mer information om PowerShell-sessioner finns [about_PSSessions](about/about_PSSessions.md).

## EXEMPEL

### Exempel 1: Hämta sessioner som skapats i den aktuella sessionen

```powershell
Get-PSSession
```

Det här kommandot hämtar alla **PSSessions** som skapades i den aktuella sessionen. Den hämtar inte **PSSessions** som har skapats i andra sessioner eller på andra datorer, även om de ansluter till den här datorn.

### Exempel 2: Hämta sessioner som är anslutna till den lokala datorn

```powershell
Get-PSSession -ComputerName "localhost"
```

Det här kommandot hämtar **PSSessions** som är anslutna till den lokala datorn. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.)

Kommandot returnerar alla sessioner på den lokala datorn, även om de har skapats i olika sessioner eller på olika datorer.

### Exempel 3: Hämta sessioner som är anslutna till en dator

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

Det här kommandot hämtar **PSSessions** som är anslutna till Server02-datorn.

Kommandot returnerar alla sessioner på Server02, även om de har skapats i olika sessioner eller på olika datorer.

Utdata visar att två av sessionerna har ett frånkopplat tillstånd och en upptagen tillgänglighet. De skapades i olika sessioner och används för närvarande. ScheduledJobs-sessionen, som öppnas och är tillgänglig, har skapats i den aktuella sessionen.

### Exempel 4: Spara resultatet av det här kommandot

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

Det här exemplet visar hur du sparar resultatet av ett `Get-PSSession` kommando i flera variabler.

Det första kommandot använder `New-PSSession` cmdleten för att skapa **PSSessions** på tre fjärrdatorer.

Det andra kommandot använder en `Get-PSSession` cmdlet för att hämta de tre **PSSessions**. Sedan sparas varje **PSSessions** i en separat variabel.

När PowerShell tilldelar en matris med objekt till en matris med variabler tilldelas det första objektet till den första variabeln, det andra objektet till den andra variabeln, och så vidare. Om det finns fler objekt än variabler tilldelas alla återstående objekt till den sista variabeln i matrisen. Om det finns fler variabler än objekt används inte de extra variablerna.

### Exempel 5: ta bort en session med ett instans-ID

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

Det här exemplet visar hur du hämtar en **PSSession** genom att använda dess instans-ID och sedan ta bort **PSSession**.

Det första kommandot hämtar alla **PSSessions** som skapades i den aktuella sessionen. Den skickar **PSSessions** till Format-Table-cmdlet, som visar **computername** -och **InstanceID** -egenskaperna för varje **PSSession**.

Det andra kommandot använder `Get-PSSession` cmdleten för att hämta en viss **PSSession** och för att spara den i `$s` variabeln. Kommandot använder **InstanceID** -parametern för att identifiera **PSSession**.

Det tredje kommandot använder cmdleten Remove-PSSession för att ta bort **PSSession** i `$s` variabeln.

### Exempel 6: Hämta en session med ett visst namn

Kommandona i det här exemplet söker efter en session med ett visst namn format och använder en viss sessionsinformation och ansluter sedan till sessionen. Du kan använda ett kommando som det här för att hitta en session där en kollega startade en uppgift och ansluta för att slutföra uppgiften.

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

Det första kommandot hämtar sessioner på Server02-och Server12-fjärrdatorer som har namn som börjar med BackupJob och använder ITTasks-sessionen. Kommandot använder **Name** -parametern för att ange namn mönstret och parametern **ConfigurationName** för att ange konfigurationen för sessionen. Värdet för parametern **SessionOption** är en hash-tabell som anger värdet för **OperationTimeout** till 240000 millisekunder (4 minuter). Den här inställningen ger kommandot mer tid att slutföra. Parametrarna **ConfigurationName** och **SessionOption** används för att konfigurera de tillfälliga sessioner där `Get-PSSession` cmdleten körs på varje dator. Utdata visar att kommandot returnerar BackupJob04-sessionen. Sessionen är frånkopplad och **tillgängligheten** är ingen, vilket anger att den inte används.

Det andra kommandot använder `Get-PSSession` cmdleten för att komma till BackupJob04-sessionen och Connect-PSSession cmdlet för att ansluta till sessionen. Kommandot sparar sessionen i variabeln $s.

Det tredje kommandot hämtar sessionen i variabeln $s. Resultatet visar att `Connect-PSSession` kommandot har slutförts. Sessionen är i ett **öppet** tillstånd och kan användas.

### Exempel 7: Hämta en session med hjälp av dess ID

```powershell
Get-PSSession -Id 2
```

Det här kommandot hämtar **PSSession** med ID 2. Eftersom värdet för egenskapen **ID** endast är unikt i den aktuella sessionen, är **ID-** parametern endast giltig för lokala kommandon.

## PARAMETRAR

### -AllowRedirection

Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI). Som standard omdirigerar PowerShell inte anslutningar.

Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **ConnectionUri** .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Anger namnet på ett program. Denna cmdlet ansluter bara till sessioner som använder det angivna programmet.

Ange program namns segmentet för anslutnings-URI: n. I följande anslutnings-URI är till exempel program namnet WSMan: `http://localhost:5985/WSMAN` . Program namnet för en session lagras i egenskapen **körnings utrymme. ConnectionInfo. APPNAME** för sessionen.

Värdet för den här parametern används för att välja och filtrera sessioner. Den ändrar inte det program som används av sessionen.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Autentisering

Anger den mekanism som används för att autentisera autentiseringsuppgifter för den session där `Get-PSSession` kommandot körs.

Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .

De acceptabla värdena för den här parametern är:

- Standard
- Grundläggande
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential.

Standardvärdet är default.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skapa sessionen där `Get-PSSession` kommandot körs. Ange certifikatets tumavtryck.

Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .

Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Använd ett Get-Item-eller Get-ChildItem kommando i PowerShell-certifikatet för att hämta ett tumavtryck för certifikatet: enhet.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger en matris med namn på datorer. Hämtar de sessioner som ansluter till de angivna datorerna.
Jokertecken tillåts inte. Det finns inget standardvärde.

Från och med Windows PowerShell 3,0 lagras **PSSession** -objekt på datorerna i Fjärrslutpunkten för varje anslutning. För att hämta sessionerna på de angivna datorerna skapar PowerShell en tillfällig anslutning till varje dator och kör ett `Get-PSSession` kommando.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.).

OBS! den här parametern hämtar endast sessioner från datorer som kör Windows PowerShell 3,0 eller senare versioner av PowerShell. Tidigare versioner lagrar inte sessioner.

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – ConfigurationName

Anger namnet på en konfiguration. Denna cmdlet får endast användas för sessioner som använder den angivna konfigurationen för sessionen.

Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen. Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` . Konfigurations namnet för en session lagras i sessionens **ConfigurationName** -egenskap.

Värdet för den här parametern används för att välja och filtrera sessioner. Den ändrar inte den sessionsinformation som sessionen använder.

För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Anger en URI som definierar anslutnings slut punkten för den tillfälliga sessionen där `Get-PSSession` kommandot körs. URI: n måste vara fullständigt kvalificerad.

Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **ConnectionUri** .

Formatet för den här strängen är:

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

Standardvärdet är: `http://localhost:5985/WSMAN` .

Om du inte anger en **ConnectionUri** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionUri** -värden. Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS. Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.

Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.

Den här parametern introducerades i Windows PowerShell 3,0.

Den här parametern hämtar endast sessioner från datorer som kör Windows PowerShell 3,0 eller senare versioner av Windows PowerShell. Tidigare versioner lagrar inte sessioner.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Anger en matris med ID: n för behållare. Den här cmdleten startar en interaktiv session med var och en av de angivna behållarna. Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n. Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger autentiseringsuppgifter för användare. Denna cmdlet kör kommandot med behörigheterna för den angivna användaren. Ange ett användar konto som har behörighet att ansluta till fjärrdatorn och kör ett `Get-PSSession` kommando. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

Den här parametern konfigurerar till den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger en matris med sessions-ID: n. Denna cmdlet hämtar bara sessionerna med de angivna ID: na. Skriv ett eller flera ID: n, avgränsade med kommatecken eller Använd intervall operatorn (..) för att ange ett intervall med ID: n. Du kan inte använda ID-parametern tillsammans med parametern **computername** .

Ett ID är ett heltal som unikt identifierar de användar hanterade sessionerna i den aktuella sessionen. Det är enklare att komma ihåg och skriva än **InstanceID** , men det är endast unikt inom den aktuella sessionen. ID: t för en session lagras i sessionens ID-egenskap.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger en matris med instans-ID: n för sessioner. Denna cmdlet hämtar bara sessionerna med de angivna instans-ID: na.

Instans-ID är ett GUID som unikt identifierar en session på en lokal dator eller fjärrdator. **InstanceID** är unikt, även om du har flera sessioner som körs i PowerShell.

Instans-ID: t för en session lagras i sessionens **InstanceID** -egenskap.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, VMNameInstanceId, ContainerIdInstanceId, VMIdInstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger en matris med sessionsnamn. Denna cmdlet hämtar bara de sessioner som har angivna egna namn. Jokertecken är tillåtna.

Det egna namnet på en session lagras i sessionens **namn** -egenskap.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Port

Anger den angivna nätverks porten som används för den tillfälliga anslutning där `Get-PSSession` kommandot körs. Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder. Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten. Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Den här parametern konfigurerar till den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** eller **ConnectionUri** .

Använd inte **port** parametern om du inte behöver. **Porten** som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Anger avancerade alternativ för sessionen. Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av New-PSSessionOption-cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.

Standardvärdena för alternativen bestäms av värdet för variabeln $PSSessionOption, om det har angetts. Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i variabeln $PSSessionOption och i konfigurationen av sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.

En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .
Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md). För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tillstånd

Anger ett sessionstillstånd. Denna cmdlet hämtar endast sessioner i det angivna läget. De acceptabla värdena för den här parametern är: alla, öppna, frånkopplade, stängda och brutna. Standardvärdet är Alla.

Värdet för sessionstillstånd är i förhållande till de aktuella sessionerna. Sessioner som inte har skapats i de aktuella sessionerna och som inte är anslutna till den aktuella sessionen har statusen Frånkopplad även om de är anslutna till en annan session.

Status för en session lagras i sessionens **tillstånds** egenskap.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, VMNameInstanceId, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra `Get-PSSession` kommandot. Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet 32. Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Anger att denna cmdlet använder Secure Sockets Layer (SSL)-protokollet för att upprätta anslutningen där `Get-PSSession` kommandot körs. Som standard används inte SSL. Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

Den här parametern konfigurerar den tillfälliga anslutning som skapas för att köra ett `Get-PSSession` kommando med parametern **computername** .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Anger en matris med ID för virtuella datorer. Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna. Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – VMName

Anger en matris med namn på virtuella datorer. Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna. Använd cmdleten för att se de virtuella datorer som är tillgängliga för dig `Get-VM` .

```yaml
Type: System.String[]
Parameter Sets: VMNameInstanceId, VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. körnings utrymmen. PSSession

## ANTECKNINGAR

- Med den här cmdleten får du **PSSession** objekt som skapats med hjälp av cmdletarna New-PSSession, `Enter-PSSession` och Invoke-Command. Den får inte den systemhanterade sessionen som skapas när du startar PowerShell.
- Från och med Windows PowerShell 3,0 lagras **PSSession** -objekt på den dator som finns på Server sidan eller tar emot en anslutning. För att hämta de sessioner som lagras på den lokala datorn eller en fjärrdator, upprättar PowerShell en tillfällig session till den angivna datorn och kör fråga-kommandon i sessionen.
- Om du vill hämta sessioner som ansluter till en fjärrdator använder du parametrarna **computername** eller **ConnectionUri** för att ange fjärrdatorn. Om du vill filtrera de sessioner som `Get-PSSession` hämtar använder du parametrarna **namn** , **ID** , **InstanceID** och **tillstånd** . Använd de återstående parametrarna för att konfigurera den tillfälliga sessionen som `Get-PSSession` använder.
- När du använder parametrarna **computername** eller **ConnectionUri** `Get-PSSession` hämtar endast sessioner från datorer som kör Windows PowerShell 3,0 och senare versioner av PowerShell.
- Värdet för egenskapen **State** för en **PSSession** är i förhållande till den aktuella sessionen.
  Därför innebär värdet **frånkopplat** att **PSSession** inte är ansluten till den aktuella sessionen. Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner. Den kan vara ansluten till en annan session. Använd egenskapen **Availability** för att avgöra om du kan ansluta eller återansluta till **PSSession** från den aktuella sessionen.

**Tillgänglighet** svärdet **none** anger att du kan ansluta till sessionen. Värdet **upptagen** anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.

Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState-uppräkning](/dotnet/api/system.management.automation.runspaces.runspacestate).

Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability-uppräkning](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

## RELATERADE LÄNKAR

[Anslut – PSSession](Connect-PSSession.md)

[Koppla från-PSSession](Disconnect-PSSession.md)

[Ta emot – PSSession](Receive-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
