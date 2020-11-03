---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 65f6544835562e4006319b5bd8d9fc9404f75e1a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268634"
---
# Connect-PSSession

## SAMMANFATTNING
Återansluter till frånkopplade sessioner.

## SYNTAX

### Namn (standard)

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Session

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameGuid

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Connect-PSSession -ComputerName <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriGuid

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ConnectionUri

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Connect-PSSession** återansluter till användare-hanterade PowerShell-sessioner ( **PSSessions** ) som kopplades från.
Den fungerar på sessioner som är frånkopplade, t. ex. genom att använda Disconnect-PSSession-cmdlet eller parametern *InDisconnectedSession* i Invoke-Command-cmdleten, och de som frånkopplats oavsiktligt, till exempel vid ett tillfälligt nätverks avbrott.

**Connect-PSSession** kan ansluta till en frånkopplad session som har startats av samma användare.
Detta inkluderar de som startades av eller frånkopplats från andra sessioner på andra datorer.

**Connect-PSSession** kan dock inte ansluta till brutna eller stängda sessioner, eller interaktiva sessioner som startats med hjälp av Enter-PSSession-cmdleten.
Du kan inte heller ansluta sessioner till sessioner som har startats av andra användare, om du inte kan ange autentiseringsuppgifterna för den användare som skapade sessionen.

Mer information om funktionen frånkopplade sessioner finns about_Remote_Disconnected_Sessions.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Återanslut till en session

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

Det här kommandot återansluter till ITTask-sessionen på Server01-datorn.

Resultatet visar att kommandot har slutförts.
Sessionens **tillstånd** öppnas och **tillgängligheten** är tillgänglig, vilket innebär att du kan köra kommandon i sessionen.

### Exempel 2: påverkan från från koppling och åter anslutning

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

Det här exemplet visar hur du kopplar från och sedan återansluter till en session.

Det första kommandot använder Get-PSSession-cmdleten.
Utan parametern *computername* , hämtar kommandot endast sessioner som har skapats i den aktuella sessionen.

Utdata visar att kommandot hämtar sessionen för säkerhets kopiering på den lokala datorn.
Sessionens **tillstånd** öppnas **och tillgängligheten är tillgänglig** .

Det andra kommandot använder cmdleten **Get-PSSession** för att hämta de **PSSession** -objekt som skapades i den aktuella sessionen och från cmdleten **disconnect-PSSession** för att koppla från sessionerna.
Utdata visar att säkerhets kopierings sessionen kopplades från.
Sessionens **status** är frånkopplad och **tillgängligheten** är ingen.

Det tredje kommandot använder cmdleten **Get-PSSession** för att hämta de **PSSession** -objekt som skapades i den aktuella sessionen och **Connect-PSSession-** cmdleten för att återansluta sessionerna.
Utdata visar att säkerhets kopierings sessionen har återanslutits.
Sessionens **tillstånd** öppnas **och tillgängligheten är tillgänglig** .

Om du använder cmdleten **Connect-PSSession** i en session som inte är frånkopplad, påverkar inte kommandot sessionen och det genererar inga fel.

### Exempel 3: serie kommandon i ett företags scenario

```
The administrator starts by creating a sessions on a remote computer and running a script in the session.The first command uses the **New-PSSession** cmdlet to create the ITTask session on the Server01 remote computer. The command uses the *ConfigurationName* parameter to specify the ITTasks session configuration. The command saves the sessions in the $s variable.
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks

 The second command **Invoke-Command** cmdlet to start a background job in the session in the $s variable. It uses the *FilePath* parameter to run the script in the background job.
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

The third command uses the Disconnect-PSSession cmdlet to disconnect from the session in the $s variable. The command uses the *OutputBufferingMode* parameter with a value of Drop to prevent the script from being blocked by having to deliver output to the session. It uses the *IdleTimeoutSec* parameter to extend the session time-out to 15 hours.When the command is completed, the administrator locks her computer and goes home for the evening.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

Later that evening, the administrator starts her home computer, logs on to the corporate network, and starts PowerShell. The fourth command uses the Get-PSSession cmdlet to get the sessions on the Server01 computer. The command finds the ITTask session.The fifth command uses the **Connect-PSSession** cmdlet to connect to the ITTask session. The command saves the session in the $s variable.
PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

The sixth command uses the **Invoke-Command** cmdlet to run a Get-Job command in the session in the $s variable. The output shows that the job finished successfully.The seventh command uses the **Invoke-Command** cmdlet to run a Receive-Job command in the session in the $s variable in the session. The command saves the results in the $BackupSpecs variable.The eighth command uses the **Invoke-Command** cmdlet to runs another script in the session. The command uses the value of the $BackupSpecs variable in the session as input to the script.


PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

The ninth command disconnects from the session in the $s variable.The administrator closes PowerShell and closes the computer. She can reconnect to the session on the next day and check the script status from her work computer.
PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

Den här serien med kommandon visar hur cmdleten **Connect-PSSession** kan användas i ett företags scenario.
I det här fallet startar en system administratör ett långvarigt jobb i en session på en fjärran sluten dator.
När jobbet har startats kopplas administratören bort från sessionen och går sedan hemma.
Senare på kvällen loggar administratören in på sin hem dator och kontrollerar att jobbet kördes tills det har slutförts.

## PARAMETRAR

### -AllowRedirection

Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ URI.

När du använder *ConnectionURI* -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI.
Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.

Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session.
Använd parametern *MaximumRedirection* i New-PSSessionOption-cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för variabeln **$PSSessionOption** Preference.
Standardvärdet är 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Anger namnet på ett program.
Denna cmdlet ansluter bara till sessioner som använder det angivna programmet.

Ange program namns segmentet för anslutnings-URI: n.
I följande anslutnings-URI är till exempel program namnet WSMan: `http://localhost:5985/WSMAN` .
Program namnet för en session lagras i egenskapen **körnings utrymme. ConnectionInfo. APPNAME** för sessionen.

Värdet för den här parametern används för att välja och filtrera sessioner.
Den ändrar inte det program som används av sessionen.

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Autentisering

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter i kommandot för att återansluta till den frånkopplade sessionen. De acceptabla värdena för den här parametern är:

- Default
- Basic
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Standardvärdet är default.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) i MSDN-biblioteket.

Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.
Den här mekanismen ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att ansluta till den frånkopplade sessionen. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering.
De kan endast mappas till lokala användar konton.
De fungerar inte med domän konton.

Använd ett Get-Item-eller Get-ChildItem kommando i PowerShell-certifikatet för att hämta ett tumavtryck för certifikatet: enhet.

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger de datorer där de frånkopplade sessionerna lagras.
Sessioner lagras på den dator som finns på Server sidan eller tar emot en anslutning.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en dator.
Jokertecken tillåts inte.
Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.)

```yaml
Type: System.String[]
Parameter Sets: ComputerNameGuid, ComputerName
Aliases: Cn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – ConfigurationName

Ansluter endast till sessioner som använder den angivna konfigurationen.

Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen.
Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` .
Konfigurations namnet för en session lagras i sessionens **ConfigurationName** -egenskap.

Värdet för den här parametern används för att välja och filtrera sessioner.
Den ändrar inte den sessionsinformation som sessionen använder.

För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

```yaml
Type: System.String
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Anger URI: erna för anslutningens slut punkter för de frånkopplade sessionerna.

URI: n måste vara fullständigt kvalificerad.
Formatet för den här strängen är följande:

`\<Transport\>://\<ComputerName\>:\<Port\>/\<ApplicationName\>`

Standardvärdet är följande:

`http://localhost:5985/WSMAN`

Om du inte anger en anslutnings-URI kan du använda parametrarna *UseSSL* och *port* för att ange anslutnings-URI-värden.

Giltiga värden för URI: n i **transport** segmentet är http och https.
Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS.
Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.

Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern *AllowRedirection* i kommandot.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriGuid, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att ansluta till den frånkopplade sessionen.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger ID: n för de frånkopplade sessionerna.
*ID-* parametern fungerar bara när den frånkopplade sessionen tidigare var ansluten till den aktuella sessionen.

Den här parametern är giltig, men inte effektiv, när sessionen lagras på den lokala datorn, men inte var ansluten till den aktuella sessionen.

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

Anger instans-ID: n för de frånkopplade sessionerna.

Instans-ID är ett GUID som unikt identifierar en **PSSession** på en lokal eller fjärran sluten dator.

Instans-ID: t lagras i egenskapen **InstanceID** i **PSSession**.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger de egna namnen på de frånkopplade sessionerna.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger nätverks porten på den fjärrdator som används för att återansluta till sessionen.
Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder.
Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten.
Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Använd inte *port* parametern om du inte behöver.
Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs.
En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

```yaml
Type: System.Int32
Parameter Sets: ComputerNameGuid, ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger de frånkopplade sessionerna.
Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett Get-PSSession-kommando.

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

### -SessionOption

Anger avancerade alternativ för sessionen.
Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av New-PSSessionOption-cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.

Standardvärdena för alternativen bestäms av värdet för variabeln $PSSessionOption, om det har angetts.
Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i variabeln $PSSessionOption och i konfigurationen av sessionen.
De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.

En beskrivning av de sessionsinformation som innehåller standardvärdena finns i New-PSSessionOption.
Information om variabeln **$PSSessionOption** finns i [about_Preference_Variables](About/about_Preference_Variables.md).
För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerNameGuid, ComputerName, ConnectionUriGuid, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
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

### -UseSSL

Anger att denna cmdlet använder Secure Sockets Layer (SSL)-protokollet för att ansluta till den frånkopplade sessionen. Som standard används inte SSL.

WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.
Parametern *UseSSL* är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.

Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameGuid, ComputerName
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

### System. Management. Automation. körnings utrymmen. PSSession

Du kan skicka en session ( **PSSession** ) till denna cmdlet.

## UTDATA

### System. Management. Automation. körnings utrymmen. PSSession

Den här cmdleten returnerar ett objekt som representerar den session som den återanslutet till.

## ANTECKNINGAR

* **Connect-PSSession** återansluter endast till sessioner som är frånkopplade, det vill säga sessioner som har värdet frånkopplat för egenskapen **State** . Endast sessioner som är anslutna till, eller slutar på, datorer som kör Windows PowerShell 3,0 eller senare versioner kan kopplas från och återanslutas.
* Om du använder **Connect-PSSession** på en session som inte är frånkopplad, påverkar inte kommandot sessionen och genererar inga fel.
* Frånkopplade loopback-sessioner med interaktiva tokens, som skapas med hjälp av parametern *EnableNetworkAccess* , kan bara återanslutas från den dator där sessionen skapades. Den här begränsningen skyddar datorn från skadlig åtkomst.
* Värdet för egenskapen **State** för en **PSSession** är i förhållande till den aktuella sessionen.
Därför innebär värdet **frånkopplat** att **PSSession** inte är ansluten till den aktuella sessionen. Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner. Den kan vara ansluten till en annan session. Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.

  **Tillgänglighet** svärdet none anger att du kan ansluta till sessionen.
Värdet upptagen anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session.

  Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState-UPPräkning](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate) i MSDN-biblioteket.

  Mer information om värdena för egenskapen **tillgänglighet** för sessioner finns i [RunspaceAvailability-UPPräkning](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability) i MSDN-biblioteket.

* Du kan inte ändra timeout-värdet för inaktivitet för en **PSSession** när du ansluter till **PSSession**. *SessionOption* -parametern för **Connect-PSSession** tar ett **SessionOption** -objekt med ett **idleTimeout** -värde. Men **idleTimeout** -värdet för **SessionOption** -objektet och **idleTimeout** -värdet för variabeln $PSSessionOption ignoreras vid anslutning till en **PSSession**.

  Du kan ställa in och ändra tids gränsen för inaktivitet i en **PSSession** när du skapar **PSSession** med hjälp av cmdletarna **New-PSSession** eller **Invoke-Command** och när du kopplar bort från **PSSession**.

  Egenskapen **idleTimeout** för en **PSSession** är viktig för frånkopplade sessioner, eftersom den fastställer hur länge en frånkopplad session ska behållas på fjärrdatorn.
Frånkopplade sessioner anses vara inaktiva från det ögonblick då de kopplas från, även om kommandon körs i den frånkopplade sessionen.

## RELATERADE LÄNKAR

[Koppla från-PSSession](Disconnect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Ta emot – PSSession](Receive-PSSession.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)

