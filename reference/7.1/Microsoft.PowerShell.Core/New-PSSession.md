---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: e5dedf3d161f2687bddfbd09740812d8c5cbaa77
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268616"
---
# New-PSSession

## SAMMANFATTNING
Skapar en permanent anslutning till en lokal dator eller fjärrdator.

## SYNTAX

### ComputerName (standard)

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### Session

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### Hålla

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### UseWindowsPowerShellParameterSet

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### SSHHost

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>]
 [-KeyFilePath <String>] [-SSHTransport] [-Subsystem <String>] [<CommonParameters>]
```

### SSHHostHashParam

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## BESKRIVNING

`New-PSSession`Cmdleten skapar en PowerShell-session ( **PSSession** ) på en lokal eller fjärran sluten dator. När du skapar en **PSSession** upprättar PowerShell en permanent anslutning till fjärrdatorn.

Använd en **PSSession** för att köra flera kommandon som delar data, till exempel en funktion eller värdet för en variabel. Om du vill köra kommandon i en **PSSession** använder du `Invoke-Command` cmdleten. Använd cmdleten om du vill använda **PSSession** för att interagera direkt med en fjärrdator `Enter-PSSession` . Mer information finns i [about_PSSessions](about/about_PSSessions.md).

Du kan köra kommandon på en fjärrdator utan att skapa en **PSSession** med hjälp av **computername** -parametrarna för `Enter-PSSession` eller `Invoke-Command` . När du använder parametern **computername** skapar PowerShell en tillfällig anslutning som används för kommandot och stängs sedan.

Från och med PowerShell 6,0 kan du använda SSH (Secure Shell) för att upprätta en anslutning till och skapa en session på en fjärrdator, om SSH är tillgängligt på den lokala datorn och fjärrdatorn har kon figurer ATS med en PowerShell SSH-slutpunkt. Fördelen med en SSH-baserad PowerShell-fjärrsession är att den kan fungera på flera plattformar (Windows, Linux och macOS). För SSH-baserade sessioner använder du parametern **hostname** eller **SSHConnection** för att ange fjärrdatorn och relevant anslutnings information. Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> När du använder WSMan-fjärrkommunikation från en Linux-eller macOS-klient med en HTTPS-slutpunkt där Server certifikatet inte är betrott (t. ex. ett självsignerat certifikat). Du måste ange en `PSSessionOption` som inkluderar `-SkipCACheck` och `-SkipCNCheck` för att kunna upprätta anslutningen. Gör bara detta om du är i en miljö där du kan vara säker på Server certifikatet och nätverks anslutningen till mål systemet.

## EXEMPEL

### Exempel 1: skapa en session på den lokala datorn

```powershell
$s = New-PSSession
```

Det här kommandot skapar en ny **PSSession** på den lokala datorn och sparar **PSSession** i `$s` variabeln.

Nu kan du använda den här **PSSession** för att köra kommandon på den lokala datorn.

### Exempel 2: skapa en session på en fjärran sluten dator

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

Det här kommandot skapar en ny **PSSession** på Server01-datorn och sparar det i `$Server01` variabeln.

När du skapar flera **PSSession** -objekt tilldelar du dem till variabler med användbara namn. Detta hjälper dig att hantera **PSSession** -objekt i efterföljande kommandon.

### Exempel 3: skapa sessioner på flera datorer

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

Det här kommandot skapar tre **PSSession** -objekt, ett på varje dator som anges av parametern **computername** .

Kommandot använder tilldelnings operatorn (=) för att tilldela de nya **PSSession** -objekten till variabler: `$s1` , `$s2` , `$s3` . Den tilldelar Server01- **PSSession** till `$s1` , Server02 **PSSession** till `$s2` och Server03 **PSSession** till `$s3` .

När du tilldelar flera objekt till en serie med variabler tilldelar PowerShell varje objekt till en variabel i serien. Om det finns fler objekt än variabler tilldelas alla återstående objekt den sista variabeln. Om det finns fler variabler än objekt är de återstående variablerna tomma (null).

### Exempel 4: skapa en session med en angiven port

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

Det här kommandot skapar en ny **PSSession** på Server01-datorn som ansluter till server port 8081 och använder SSL-protokollet. Den nya **PSSession** använder en alternativ sessionsinformation med namnet E12.

Innan du anger porten måste du konfigurera WinRM-lyssnaren på fjärrdatorn så att den lyssnar på port 8081. Mer information finns i beskrivningen av **port** parametern.

### Exempel 5: skapa en session baserad på en befintlig session

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

Det här kommandot skapar en **PSSession** med samma egenskaper som en befintlig **PSSession**. Du kan använda det här kommando formatet när resurserna för en befintlig **PSSession** är uttömda och en ny **PSSession** krävs för att avlasta en del av behovet.

Kommandot använder parametern **session** för `New-PSSession` för att ange **PSSession** som sparats i `$s` variabeln. Den använder Domain1\Admin01-användarens autentiseringsuppgifter för att slutföra kommandot.

### Exempel 6: skapa en session med en global omfattning i en annan domän

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

Det här exemplet visar hur du skapar en **PSSession** med ett globalt omfång på en dator i en annan domän.

Som standard skapas **PSSession** -objekt som skapas på kommando raden med lokala scope-och **PSSession** -objekt som skapats i ett skript som har skript omfattning.

Skapa en **PSSession** med global omfattning genom att skapa en ny **PSSession** och sedan lagra **PSSession** i en variabel som är Cast till en global omfattning. I det här fallet `$s` omvandlas variabeln till en global omfattning.

Kommandot använder parametern **computername** för att ange fjärrdatorn. Eftersom datorn finns i en annan domän än användar kontot, anges det fullständiga namnet på datorn tillsammans med autentiseringsuppgifterna för användaren.

### Exempel 7: skapa sessioner för många datorer

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

Det här kommandot skapar en **PSSession** på var och en av de 200 datorer som anges i Servers.txt-filen och lagrar den resulterande **PSSession** i `$rs` variabeln. **PSSession** -objekten har en begränsnings gräns på 50.

Du kan använda det här kommando formatet när namnen på datorerna lagras i en databas, ett kalkyl blad, i en textfil eller i ett annat format som kan konverteras.

### Exempel 8: skapa en session med en URI

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

Det här kommandot skapar en **PSSession** på Server01-datorn och lagrar den i `$s` variabeln. Den använder **URI** -parametern för att ange transport protokollet, fjärrdatorn, porten och en alternativ konfiguration av sessionen. Den använder också parametern **Credential** för att ange ett användar konto som har behörighet att skapa en session på fjärrdatorn.

### Exempel 9: köra ett bakgrunds jobb i en uppsättning sessioner

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

Dessa kommandon skapar en uppsättning **PSSession** -objekt och kör sedan ett bakgrunds jobb i vart och ett av **PSSession** -objekten.

Det första kommandot skapar en ny **PSSession** på var och en av de datorer som anges i Servers.txt-filen. Den använder `New-PSSession` cmdleten för att skapa **PSSession**. Värdet för parametern **computername** är ett kommando som använder `Get-Content` cmdleten för att hämta listan över dator namn Servers.txt-filen.

Kommandot använder parametern **Credential** för att skapa **PSSession** -objekt som har behörighet för en domän administratör och använder parametern **ThrottleLimit** för att begränsa kommandot till 16 samtidiga anslutningar. Kommandot sparar **PSSession** -objekten i `$s` variabeln.

Det andra kommandot använder **AsJob** -parametern för `Invoke-Command` cmdleten för att starta ett bakgrunds jobb som kör ett `Get-Process PowerShell` kommando i varje **PSSession** -objekt i `$s` .

Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](About/about_Jobs.md) och [about_Remote_Jobs](About/about_Remote_Jobs.md).

### Exempel 10: skapa en session för en dator med hjälp av dess URI

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

Det här kommandot skapar ett **PSSession** -objekt som ansluter till en dator som anges av en URI i stället för ett dator namn.

### Exempel 11: skapa ett session-alternativ

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

I det här exemplet visas hur du skapar ett sessionsobjekt-objekt och använder parametern **SessionOption** .

Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session-alternativ. Det sparar det resulterande **SessionOption** -objektet i `$so` variabeln.

Det andra kommandot använder alternativet i en ny session. Kommandot använder `New-PSSession` cmdleten för att skapa en ny session. Värdet för parametern SessionOption är **SessionOption** -objektet i `$so` variabeln.

### Exempel 12: skapa en session med SSH

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

Det här exemplet visar hur du skapar en ny **PSSession** med hjälp av SSH (Secure Shell). Om SSH har kon figurer ATS på fjärrdatorn för att uppmanas att ange lösen ord får du en prompt. Annars kommer du att behöva använda SSH-nyckelbaserad användarautentisering.

### Exempel 13: skapa en session med SSH och ange nyckel för port och användarautentisering

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

Det här exemplet visar hur du skapar en **PSSession** med hjälp av SSH (Secure Shell). Den använder **port** parametern för att ange vilken port som ska användas och parametern för nyckel **Sök** vägar för att ange en RSA-nyckel som används för att identifiera och autentisera användaren på fjärrdatorn.

### Exempel 14: skapa flera sessioner med SSH

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

Det här exemplet visar hur du skapar flera sessioner med hjälp av SSH (Secure Shell) och **SSHConnection** -parameter uppsättningen. Parametern **SSHConnection** tar en matris med hash-tabeller som innehåller anslutnings information för varje session. Observera att det här exemplet kräver att de mål datorerna har SSH konfigurerat för att stödja nyckelbaserad användarautentisering.

## PARAMETRAR

### -AllowRedirection

Anger att denna cmdlet tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).

När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI. Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern för att aktivera den för att omdirigera anslutningen.

Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session. Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för variabeln **$PSSessionOption** . Standardvärdet är 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Anger program namns segmentet för anslutnings-URI: n. Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.

Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn. Om den här preferens variabeln inte definieras är standardvärdet WSMAN. Det här värdet är lämpligt för de flesta användnings områden. Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).

WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.
Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Autentisering

Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter.
De acceptabla värdena för den här parametern är:

- Default
- Basic
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
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Hämta ett certifikat med hjälp av `Get-Item` kommandot eller `Get-ChildItem` i PowerShell-certifikatet: enhet.

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger en matris med namn på datorer. Denna cmdlet skapar en permanent anslutning ( **PSSession** ) till den angivna datorn. Om du anger flera dator namn `New-PSSession` skapas flera **PSSession** -objekt, ett för varje dator. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera fjärrdatorer. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt (.). När datorn finns i en annan domän än användaren, krävs det fullständigt kvalificerade domän namnet. Du kan också skicka ett dator namn inom citat tecken till `New-PSSession` .

Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** . Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn. Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).

Om du vill inkludera den lokala datorn i värdet för parametern **computername** startar du Windows PowerShell med alternativet Kör som administratör.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – ConfigurationName

Anger den sessionsinformation som används för den nya **PSSession**.

Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen. Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/PowerShell` .

Sessionens konfiguration för en session finns på fjärrdatorn. Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.

Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn. Om den här preferens variabeln inte anges är standardvärdet Microsoft. PowerShell. Mer information finns i [about_Preference_Variables](About/about_Preference_Variables.md).

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Anger en URI som definierar anslutnings slut punkten för sessionen. URI: n måste vara fullständigt kvalificerad. Formatet för den här strängen är följande:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

Standardvärdet är följande:

`http://localhost:5985/WSMAN`

Om du inte anger en **ConnectionURI** kan du använda parametrarna **UseSSL** , **computername** , **port** och **ApplicationName** för att ange **ConnectionURI** -värden.

Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS. Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portar: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.

Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Anger en matris med ID: n för behållare. Den här cmdleten startar en interaktiv session med var och en av de angivna behållarna. Använd `docker ps` kommandot för att hämta en lista över behållar-ID: n. Mer information finns i hjälpen för kommandot [Docker PS](https://docs.docker.com/engine/reference/commandline/ps/) .

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

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner. Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer. Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.

En loopback-session är en **PSSession** som kommer från och slutar på samma dator. Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet för punkt (.), localhost eller namnet på den lokala datorn.

Som standard skapar denna cmdlet loopback-sessioner med hjälp av en nätverks-token som kanske inte ger tillräcklig behörighet att autentisera till fjärrdatorer.

Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner. Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.

Du kan också aktivera fjärråtkomst i en loopback-session med hjälp av CredSSP-värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.

För att skydda datorn från skadlig åtkomst kan frånkopplade loopback-sessioner med interaktiva token, som är de som skapats med hjälp av parametern **EnableNetworkAccess** , bara återanslutas från den dator där sessionen skapades. Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer. Mer information finns i `Disconnect-PSSession`.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Anger en matris med dator namn för en SSH-baserad (Secure Shell) anslutning. Detta liknar parametern ComputerName, förutom att anslutningen till fjärrdatorn görs med SSH i stället för Windows WinRM.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fil Sök väg

Anger en nyckel fil Sök väg som används av SSH (Secure Shell) för att autentisera en användare på en fjärrdator.

SSH tillåter att användarautentisering utförs via privata/offentliga nycklar som ett alternativ till grundläggande lösenordsautentisering. Om fjärrdatorn har kon figurer ATS för nyckel autentisering kan du använda den här parametern för att ange den nyckel som identifierar användaren.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger ett eget namn för **PSSession**.

Du kan använda namnet för att referera till **PSSession** när du använder andra cmdlets, till exempel `Get-PSSession` och `Enter-PSSession` . Namnet måste inte vara unikt för datorn eller den aktuella sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger nätverks porten på den fjärrdator som används för den här anslutningen. Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder. Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten. Använd följande kommandon för att konfigurera lyssnaren:

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Använd inte **port** parametern om du inte behöver. Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Anger att **PSSession** körs som administratör.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger en matris med **PSSession** -objekt som denna cmdlet använder som en modell för den nya **PSSession**. Den här parametern skapar nya **PSSession** -objekt som har samma egenskaper som de angivna **PSSession** -objekten.

Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett- `New-PSSession` eller- `Get-PSSession` kommando.

De resulterande **PSSession** -objekten har samma dator namn, program namn, ANSLUTNINGS-URI, port, konfigurations namn, begränsnings gräns och Secure SOCKETS Layer (SSL)-värde som original, men de har olika visnings namn, ID och instans-ID (GUID).

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Anger avancerade alternativ för sessionen. Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.

Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.

En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` . Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md). För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

Den här parametern tar en matris med hash där varje hash innehåller en eller flera anslutnings parametrar som behövs för att upprätta en SSH-anslutning (Secure Shell) (värdnamn, port, användar namn, sökväg).

Anslutnings parametrarna för hash-tabellen är desamma som definieras för parametern **hostname** .

Parametern **SSHConnection** är användbar för att skapa flera sessioner där varje session kräver annan anslutnings information.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

Anger att fjärr anslutningen upprättas med hjälp av SSH (Secure Shell).

Som standard använder PowerShell Windows WinRM för att ansluta till en fjärrdator. Den här växeln tvingar PowerShell att använda HostName-parametern som angetts för att upprätta en SSH-baserad fjärr anslutning.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Om du utelämnar den här parametern eller anger värdet 0 (noll) används standardvärdet 32.

Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

Anger användar namnet för det konto som används för att skapa en session på fjärrdatorn. Metoden för användarautentisering beror på hur Secure Shell (SSH) är konfigurerat på fjärrdatorn.

Om SSH har kon figurer ATS för grundläggande lösenordsautentisering uppmanas du att ange användar lösen ordet.

Om SSH har kon figurer ATS för nyckelbaserad användarautentisering kan en nyckel fil Sök väg tillhandahållas via parametern för nyckel Sök väg och inget lösen ord visas. Observera att om klientens användar nyckel finns på en känd SSH-plats behövs inte parametern för nyckel Sök vägar för nyckelbaserad autentisering, och användarautentisering sker automatiskt baserat på användar namnet. Mer information finns i SSH-dokumentationen om nyckelbaserad användarautentisering.

Detta är inte en obligatorisk parameter. Om ingen användar namns parameter anges används den aktuella inloggnings användar namnet för anslutningen.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Anger att denna cmdlet använder SSL-protokollet för att upprätta en anslutning till fjärrdatorn.
Som standard används inte SSL.

WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket. Parametern **UseSSL** erbjuder ytterligare ett skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.

Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Anger en matris med ID för virtuella datorer. Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna. Använd följande kommando för att se de virtuella datorer som är tillgängliga för dig:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – VMName

Anger en matris med namn på virtuella datorer. Den här cmdleten startar en interaktiv session med var och en av de angivna virtuella datorerna. Använd cmdleten för att se de virtuella datorer som är tillgängliga för dig `Get-VM` .

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

### -Under system

Anger det SSH-undersystem som används för den nya **PSSession**.

Detta anger under systemet som ska användas på målet som det definieras i sshd_config.
Under systemet startar en angiven version av PowerShell med fördefinierade parametrar.
Om det angivna under systemet inte finns på fjärrdatorn Miss lyckas kommandot.

Om den här parametern inte används är standard under systemet "PowerShell".

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseWindowsPowerShell

{{Fill UseWindowsPowerShell-Beskrivning}}

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .

## INDATA

### System. String, system. URI, system. Management. Automation. körnings utrymmen. PSSession

Du kan skicka en sträng, en URI eller ett sessionsobjekt till denna cmdlet.

## UTDATA

### System. Management. Automation. körnings utrymmen. PSSession

## ANTECKNINGAR

- Denna cmdlet använder PowerShell-infrastrukturen för fjärr kommunikation. Om du vill använda den här cmdleten måste den lokala datorn och alla fjärrdatorer konfigureras för PowerShell-fjärrkommunikation. Mer information finns i [about_Remote_Requirements](About/about_Remote_Requirements.md).
- Om du vill skapa en **PSSession** på den lokala datorn startar du PowerShell med alternativet Kör som administratör.
- När du är färdig med **PSSession** kan du använda `Remove-PSSession` cmdleten för att ta bort **PSSession** och släppa dess resurser.
- Parameter uppsättningarna **hostname** och **SSHConnection** inkluderades från och med PowerShell 6,0.
  De lades till för att tillhandahålla PowerShell-fjärrkommunikation utifrån SSH (Secure Shell). Både SSH och PowerShell stöds på flera plattformar (Windows, Linux, macOS) och PowerShell-fjärrkommunikationen fungerar över dessa plattformar där PowerShell och SSH har installerats och kon figurer ATS. Detta skiljer sig från den tidigare Windows-fjärrkommunikation som baseras på WinRM och mycket av de särskilda WinRM-funktionerna och begränsningarna gäller inte. Till exempel kan WinRM-baserade kvoter, sessions alternativ, anpassad slut punkts konfiguration och funktionerna för att koppla från/återansluta inte användas för närvarande. Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## RELATERADE LÄNKAR

[Anslut – PSSession](Connect-PSSession.md)

[Koppla från-PSSession](Disconnect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[Ta emot – PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

