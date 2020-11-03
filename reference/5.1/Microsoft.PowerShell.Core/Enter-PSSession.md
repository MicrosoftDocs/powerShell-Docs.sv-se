---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 40d9da7d2e7e3233608b893b026c2b89c7155ab1
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2020
ms.locfileid: "93268737"
---
# Enter-PSSession

## SAMMANFATTNING
Startar en interaktiv session med en fjärran sluten dator.

## SYNTAX

### ComputerName (standard)

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### Session

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### URI

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [-Credential <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### InstanceId

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### Id

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### Name

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### VMId

```
Enter-PSSession [-VMId] <Guid> -Credential <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### VMName

```
Enter-PSSession [-VMName] <String> -Credential <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### Hålla

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## BESKRIVNING

`Enter-PSSession`Cmdleten startar en interaktiv session med en enda fjärrdator. Under sessionen, de kommandon som du skriver körs på fjärrdatorn, precis som om du skrev direkt på fjärrdatorn. Du kan bara ha en interaktiv session åt gången.

Normalt använder du parametern **computername** för att ange namnet på fjärrdatorn.
Du kan dock även använda en session som du skapar med hjälp av `New-PSSession` cmdleten för den interaktiva sessionen. Du kan dock inte använda `Disconnect-PSSession` `Connect-PSSession` cmdletarna, eller `Receive-PSSession` för att koppla från eller återansluta till en interaktiv session.

Om du vill avsluta den interaktiva sessionen och koppla från fjärrdatorn använder du `Exit-PSSession` cmdleten eller typen `exit` .

## EXEMPEL

### Exempel 1: starta en interaktiv session

```
PS C:\> Enter-PSSession
[localhost]: PS C:\>
```

Det här kommandot startar en interaktiv session på den lokala datorn. Kommando tolken ändras för att visa att du nu kör kommandon i en annan session.

De kommandon som du anger körs i den nya sessionen och resultatet returneras till Standardsessionen som text.

### Exempel 2: arbeta med en interaktiv session

Det första kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01, en fjärrdator. När sessionen startar ändras kommando tolken så att den inkluderar dator namnet.
Det andra kommandot hämtar Windows PowerShell-processen och dirigerar om utdata till Process.txt-filen. Kommandot skickas till fjärrdatorn och filen sparas på fjärrdatorn.
Det tredje kommandot använder nyckelordet **exit** för att avsluta den interaktiva sessionen och stänga anslutningen.
Det fjärde kommandot bekräftar att Process.txt-filen finns på fjärrdatorn. Ett `Get-ChildItem` ("dir")-kommando på den lokala datorn kan inte hitta filen.

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

Det här kommandot visar hur du arbetar i en interaktiv session med en fjärran sluten dator.

### Exempel 3: Använd parametern session

```powershell
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
[Server01]: PS C:\>
```

Dessa kommandon använder parametern **session** för `Enter-PSSession` för att köra den interaktiva sessionen i en befintlig Windows PowerShell-session ( **PSSession** ).

### Exempel 4: starta en interaktiv session och ange port-och Credential-parametrarna

```powershell
PS C:\> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS C:\>
```

Det här kommandot startar en interaktiv session med Server01-datorn. Den använder **port** parametern för att ange porten och parametern **Credential** för att ange kontot för en användare som har behörighet att ansluta till fjärrdatorn.

### Exempel 5: stoppa en interaktiv session

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS C:\> Exit-PSSession
PS C:\>
```

Det här exemplet visar hur du startar och stoppar en interaktiv session. Det första kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01-datorn.

Det andra kommandot använder `Exit-PSSession` cmdleten för att avsluta sessionen. Du kan också använda nyckelordet **exit** för att avsluta den interaktiva sessionen. `Exit-PSSession` och **Avsluta** har samma resultat.

## PARAMETRAR

### -AllowRedirection

Tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI). Omdirigering tillåts inte som standard.

När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI. Som standard omdirigerar Windows PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.

Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session. Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln. Standardvärdet är 5.

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

**WinRM** -tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran. Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.

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

Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter. De acceptabla värdena för den här parametern är:

- Default
- Basic
- CredSSP
- Sammandrag
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Standardvärdet är default.

CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

Varning! CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

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

Hämta ett certifikat med hjälp av `Get-Item` kommandot eller `Get-ChildItem` i Windows PowerShell-certifikatet: enhet.

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

Anger ett dator namn. Den här cmdleten startar en interaktiv session med den angivna fjärrdatorn. Ange bara ett dator namn. Standard är den lokala datorn.

Ange NetBIOS-namnet, IP-adressen eller det fullständigt kvalificerade domän namnet för datorn. Du kan också skicka ett dator namn till `Enter-PSSession` .

Om du vill använda en IP-adress i värdet för parametern **computername** måste kommandot innehålla parametern **Credential** . Dessutom måste datorn konfigureras för HTTPS-transport eller fjärrdatorns IP-adress måste ingå i listan WinRM TrustedHosts på den lokala datorn. Instruktioner för att lägga till ett dator namn i listan TrustedHosts finns i avsnittet om hur du lägger till en dator i listan över betrodda värdar i [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).

Obs! i Windows Vista och senare versioner av operativ systemet Windows, för att inkludera den lokala datorn i värdet för parametern **computername** , måste du starta Windows PowerShell med alternativet Kör som administratör.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – ConfigurationName

Anger den sessionsinformation som används för den interaktiva sessionen.

Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen. Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/powershell` .

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

Giltiga värden för URI: n i transport segmentet är HTTP och HTTPS. Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med hjälp av standard portar: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för Windows PowerShell-fjärrkommunikation, anger du Port 5985 för HTTP eller 5986 för HTTPS.

Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar Windows PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Anger ID för en behållare.

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner. Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer. Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.

En loopback-session är en **PSSession** som kommer från och slutar på samma dator. Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet till. (punkt), localhost eller namnet på den lokala datorn.

Som standard skapas loopback-sessioner med hjälp av en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.

Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner. Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.

Du kan också tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger ID för en befintlig session. `Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.

Använd cmdleten för att hitta ID: t för en session `Get-PSSession` .

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID för en befintlig session. `Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.

Instans-ID: t är ett GUID. Använd cmdleten för att hitta instans-ID för en session `Get-PSSession` . Du kan också använda parametrarna **session** , **Name** eller **ID** för att ange en befintlig session. Du kan också använda parametern **computername** för att starta en tillfällig session.

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger det egna namnet på en befintlig session. `Enter-PSSession` använder den angivna sessionen för den interaktiva sessionen.

Kommandot Miss lyckas om det namn som du anger matchar mer än en session. Du kan också använda parametrarna **session** , **InstanceID** eller **ID** för att ange en befintlig session. Du kan också använda parametern **computername** för att starta en tillfällig session.

Om du vill skapa ett eget namn för en session använder du parametern **Name** i `New-PSSession` cmdleten.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Anger nätverks porten på den fjärrdator som används för det här kommandot. Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder. Standard portarna är 5985, som är WinRM-porten för HTTP och 5986, som är WinRM-porten för HTTPS.

Innan du använder en annan port måste du konfigurera WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten. Använd följande kommandon för att konfigurera lyssnaren:

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Använd inte **port** parametern om du inte behöver. Port inställningen i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

```yaml
Type: System.Int32
Parameter Sets: ComputerName
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

Anger en Windows PowerShell-session ( **PSSession** ) som ska användas för den interaktiva sessionen. Den här parametern tar ett sessionsobjekt. Du kan också använda parametrarna **Name** , **InstanceID** eller **ID** för att ange en **PSSession**.

Ange en variabel som innehåller ett session-objekt eller ett kommando som skapar eller hämtar ett sessionsobjekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando. Du kan också skicka ett sessionsobjekt till `Enter-PSSession` . Du kan bara skicka en **PSSession** med hjälp av den här parametern. Om du anger en variabel som innehåller mer än en **PSSession** Miss lyckas kommandot.

När du använder `Exit-PSSession` eller **avslutar** -nyckelordet avslutas den interaktiva sessionen, men **PSSession** som du skapade förblir öppen och tillgänglig för användning.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Ställer in avancerade alternativ för sessionen. Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.

Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.

En beskrivning av sessions alternativen, inklusive standardvärdena, finns i `New-PSSessionOption` .
Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md). För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

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

### -UseSSL

Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn. Som standard används inte SSL.

WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket. Parametern **UseSSL** är ett ytterligare skydd som skickar data via en HTTPS-anslutning i stället för en HTTP-anslutning.

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

Anger ID för en virtuell dator.

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – VMName

Anger namnet på en virtuell dator.

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, system. Management. Automation. körnings utrymmen. PSSession

Du kan skicka vidare ett dator namn, som en sträng eller ett sessionsobjekt till denna cmdlet.

## UTDATA

### Inget

Cmdleten returnerar inga utdata.

## ANTECKNINGAR

Om du vill ansluta till en fjärrdator måste du vara medlem i gruppen Administratörer på fjärrdatorn. Om du vill starta en interaktiv session på den lokala datorn måste du starta PowerShell med alternativet **Kör som administratör** .

När du använder `Enter-PSSession` används din användar profil på fjärrdatorn för den interaktiva sessionen. Kommandona i fjärran sluten användar profil, inklusive kommandon för att lägga till PowerShell-moduler och ändra kommando tolken, körs innan fjärrprompten visas.

`Enter-PSSession` använder inställningen för användar gränssnitts kulturen på den lokala datorn för den interaktiva sessionen. Använd den automatiska variabeln för att hitta den lokala användar gränssnitts kulturen `$UICulture` .

`Enter-PSSession` kräver `Get-Command` `Out-Default` cmdletarna,, och `Exit-PSSession` . Om dessa cmdletar inte ingår i konfigurationen av sessionen på fjärrdatorn `Enter-PSSession` Miss lyckas kommandona.

Till skillnad från `Invoke-Command` , som tolkar och tolkar kommandon innan de skickar dem till fjärrdatorn, `Enter-PSSession` skickar kommandona direkt till fjärrdatorn utan tolkning.

Om sessionen som du vill ange är upptagen med bearbetningen av ett kommando kan det uppstå en fördröjning innan PowerShell svarar på `Enter-PSSession` kommandot. Du är ansluten så snart sessionen är tillgänglig. `Enter-PSSession`Tryck på <kbd>CTRL</kbd> + <kbd>C</kbd>om du vill avbryta kommandot.

## RELATERADE LÄNKAR

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Anslut – PSSession](Connect-PSSession.md)

[Koppla från-PSSession](Disconnect-PSSession.md)

[Ta emot – PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
