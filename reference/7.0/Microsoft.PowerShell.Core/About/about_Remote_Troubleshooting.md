---
description: Beskriver hur du felsöker fjärråtgärder i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: acf4f86d8c20f5a8059be48623255696afabbefb
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/29/2020
ms.locfileid: "93273489"
---
# <a name="about-remote-troubleshooting"></a>Om fjärrfelsökning

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du felsöker fjärråtgärder i PowerShell.

## <a name="long-description"></a>Lång beskrivning

I det här avsnittet beskrivs några av de problem som du kan stöta på när du använder funktionerna för fjärr kommunikation i PowerShell som baseras på WS-Management teknik och det föreslår lösningar för dessa problem.

Innan du använder PowerShell-fjärrkommunikation, se [about_Remote](about_remote.md) och [about_Remote_Requirements](about_Remote_Requirements.md) för vägledning om konfiguration och grundläggande användning. Hjälp avsnitten för var och en av de olika cmdletarna för fjärr kommunikation, särskilt parameter beskrivningar, har också användbar information som är utformad för att hjälpa dig att undvika problem.

> [!NOTE]
> Om du vill visa eller ändra inställningarna för den lokala datorn i WSMan:-enheten, inklusive ändringar i sessionens konfigurationer, betrodda värdar, portar eller lyssnare, startar du PowerShell med alternativet **Kör som administratör** .

## <a name="troubleshooting-permission-and-authentication-issues"></a>Fel sökning av problem med behörighet och autentisering

I det här avsnittet beskrivs fjärrstyrda problem som är relaterade till användar-och dator behörigheter och krav för fjärr kommunikation.

### <a name="how-to-run-as-administrator"></a>Så här kör du som administratör

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

Om du vill starta en fjärrsession på den lokala datorn eller Visa eller ändra inställningarna för den lokala datorn i WSMan: Drive, inklusive ändringar i sessionsinställningar, betrodda värdar, portar eller lyssnare, startar du Windows PowerShell med alternativet **Kör som administratör** .

Starta Windows PowerShell med alternativet **Kör som administratör** :

- Högerklicka på en Windows PowerShell-ikon (eller Windows PowerShell ISE) och klicka sedan på **Kör som administratör**.

  Starta Windows PowerShell med alternativet **Kör som administratör** i Windows 7 och Windows Server 2008 R2.

- Högerklicka på Windows PowerShell-ikonen i aktivitets fältet i Windows och klicka sedan på **Kör som administratör**.

  I Windows Server 2008 R2 fästs Windows PowerShell-ikonen i aktivitets fältet som standard.

### <a name="how-to-enable-remoting"></a>Så här aktiverar du fjärr kommunikation

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

Ingen konfiguration krävs för att en dator ska kunna skicka fjärrkommandon.
Men för att ta emot fjärrkommandon måste PowerShell-fjärrkommunikation vara aktiverat på datorn. Genom att aktivera kan du starta WinRM-tjänsten, ange start typen för WinRM-tjänsten till automatisk, skapa lyssnare för HTTP-och HTTPS-anslutningar och skapa standardkonfigurationer för sessioner.

Windows PowerShell-fjärrkommunikation är aktiverat på Windows Server 2012 och senare versioner av Windows Server som standard. Kör cmdleten på alla andra system `Enable-PSRemoting` för att aktivera fjärr kommunikation. Du kan också köra `Enable-PSRemoting` cmdleten för att återaktivera fjärr kommunikation på Windows server 2012 och nyare versioner av Windows Server om fjärr kommunikation är inaktive rad.

Använd cmdleten om du vill konfigurera en dator för att ta emot fjärrkommandon `Enable-PSRemoting` . Följande kommando aktiverar alla nödvändiga Fjärrinställningar, aktiverar sessionsinställningar och startar om WinRM-tjänsten för att ändringarna ska börja gälla.

`Enable-PSRemoting`

Om du vill utelämna alla användar meddelanden skriver du:

`Enable-PSRemoting -Force`

Mer information finns i [enable-psremoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting).

### <a name="how-to-enable-remoting-in-an-enterprise"></a>Så här aktiverar du fjärr kommunikation i ett företag

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Använd cmdleten om du vill göra det möjligt för en enstaka dator att ta emot PowerShell-kommandon för fjärrkörning och acceptera anslutningar `Enable-PSRemoting` .

Om du vill aktivera fjärr kommunikation för flera datorer i ett företag kan du använda följande skalade alternativ.

- Om du vill konfigurera lyssnare för fjärr kommunikation aktiverar du grup principen **Tillåt automatisk konfiguration av lyssnare** .

- Använd cmdleten för att ange starttyp för Windows Remote Management (WinRM) till automatiskt på flera datorer `Set-Service` .

- Om du vill aktivera ett brand Väggs undantag använder du **Windows-brand väggen: Tillåt lokala port undantag** grup principer.

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a>Så här aktiverar du lyssnare med hjälp av en grup princip

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Om du vill konfigurera lyssnarna för alla datorer i en domän aktiverar du inställningen **Tillåt automatisk konfiguration av Listener** i följande grupprincip sökväg:

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

Aktivera principen och ange IPv4-och IPv6-filter. Jokertecken ( `*` ) är tillåtna.

### <a name="how-to-enable-remoting-on-public-networks"></a>Så här aktiverar du fjärr kommunikation i offentliga nätverk

```
ERROR:  Unable to check the status of the firewall
```

`Enable-PSRemoting`Cmdleten returnerar det här felet när det lokala nätverket är offentligt och **SkipNetworkProfileCheck** -parametern inte används i kommandot.

På Server versioner av Windows `Enable-PSRemoting` lyckas alla typer av nätverks platser. Den skapar brand Väggs regler som tillåter fjärråtkomst till privata nätverk och domän nätverk ("hem" och "arbets"). För offentliga nätverk skapas brand Väggs regler som tillåter fjärråtkomst från samma lokala undernät.

På klient versioner av Windows fungerar `Enable-PSRemoting` i privata nätverk och domän nätverk. Som standard Miss lyckas det på offentliga nätverk, men om du använder parametern **SkipNetworkProfileCheck** `Enable-PSRemoting` slutförs och skapas en brand Väggs regel som tillåter trafik från samma lokala undernät.

Om du vill ta bort begränsningen för lokal undernät i offentliga nätverk och tillåta fjärråtkomst från vilken plats som helst, kör du följande kommando:

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

`Set-NetFirewallRule`Cmdleten exporteras av Netsecurity-modulen.

> [!NOTE]
> På datorer som kör Server versioner av Windows i Windows PowerShell 2,0 `Enable-PSRemoting` skapar brand Väggs regler som tillåter fjärråtkomst i privata, domän-och offentliga nätverk. På datorer som kör klient versioner av Windows `Enable-PSRemoting` skapar brand Väggs regler som endast tillåter fjärråtkomst i privata nätverk och domän nätverk.

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a>Så här aktiverar du ett brand Väggs undantag med en grup princip

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Aktivera ett brand Väggs undantag för på alla datorer i en domän genom att aktivera **Windows-brand väggen: Tillåt lokal port undantags** princip i följande grupprincip sökväg:

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

Med den här principen kan medlemmar i gruppen Administratörer på datorn använda **Windows-brandväggen** i **kontroll panelen** för att skapa ett brand Väggs undantag för tjänsten Windows Remote Management.

Om princip konfigurationen är felaktig kan följande fel meddelande visas:

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

Ett konfigurations fel i principen resulterar i ett tomt värde för egenskapen **ListeningOn** . Använd följande kommando för att kontrol lera värdet.

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a>Ange starttyp för WinRM-tjänsten

```
ERROR:  ACCESS IS DENIED
```

PowerShell-fjärrkommunikation beror på WinRM-tjänsten (Windows Remote Management).
Tjänsten måste köras för att stödja fjärrkommandon.

I Server versioner av Windows är start typen för WinRM-tjänsten (Windows Remote Management) automatisk.

I klient versioner av Windows är WinRM-tjänsten dock inaktive rad som standard.

Använd cmdleten om du vill ange starttyp för en tjänst på en fjärrdator `Set-Service` .

Om du vill köra kommandot på flera datorer kan du skapa en textfil eller en CSV-fil med dator namnen.

Följande kommandon får till exempel en lista över dator namn från `Servers.txt` filen och anger sedan start typen för WinRM-tjänsten på alla datorer till **Automatisk**.

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

Om du vill se resultatet använder du- `Get-WMIObject` cmdleten med **Win32_Service** -objektet. Mer information finns i [set-service](xref:Microsoft.PowerShell.Management.Set-Service).

### <a name="how-to-recreate-the-default-session-configurations"></a>Återskapa standardkonfigurationerna för sessioner

```
ERROR:  ACCESS IS DENIED
```

För att ansluta till den lokala datorn och köra kommandon via fjärr anslutning måste den lokala datorn innehålla konfigurationer för fjärrkommandon.

När du använder `Enable-PSRemoting` skapas standardkonfigurationer för sessioner på den lokala datorn. Fjärranslutna användare använder dessa sessionsinställningar när ett fjärrkommando inte innehåller parametern **ConfigurationName** .

Om standard konfigurationerna på en dator är oregistrerade eller borttagna använder du `Enable-PSRemoting` cmdleten för att återskapa dem. Du kan använda den här cmdleten upprepade gånger. Det genererar inga fel om en funktion redan har kon figurer ATS.

Om du ändrar standardkonfigurationerna för sessioner och vill återställa de ursprungliga standardsessionerna, använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort de ändrade sessionerna och använder sedan `Enable-PSRemoting` cmdlet: en för att återställa dem.
`Enable-PSRemoting` ändrar inte befintliga konfigurationer för sessioner.

> [!NOTE]
> När `Enable-PSRemoting` återställer standardsessionens konfiguration, skapar den inte uttryckliga säkerhets beskrivningar för konfigurationerna. I stället ärver konfigurationerna säkerhets beskrivningen för RootSDDL, som är säker som standard.

Om du vill se säkerhets beskrivningen RootSDDL skriver du:

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

Om du vill ändra RootSDDL använder du `Set-Item` cmdleten i kommandot WSMan: Drive. Om du vill ändra säkerhets beskrivningen för en sessions konfiguration använder du `Set-PSSessionConfiguration` cmdleten med parametrarna **SecurityDescriptorSDDL** eller **ShowSecurityDescriptorUI** .

Mer information om WSMan:-enheten finns i hjälp avsnittet för WSMan-providern ("Get-Help WSMan").

### <a name="how-to-provide-administrator-credentials"></a>Ange administratörsautentiseringsuppgifter

```
ERROR:  ACCESS IS DENIED
```

Om du vill skapa en PSSession eller köra kommandon på en fjärrdator, som standard, måste den aktuella användaren vara medlem i gruppen Administratörer på fjärrdatorn. Autentiseringsuppgifter krävs ibland även när den aktuella användaren är inloggad på ett konto som är medlem i gruppen Administratörer.

Om den aktuella användaren är medlem i gruppen Administratörer på fjärrdatorn, eller om du kan ange autentiseringsuppgifter för en medlem i gruppen Administratörer, använder du parametern **Credential** för `New-PSSession` - `Enter-PSSession` eller-cmdlet: `Invoke-Command` ar för att fjärrans luta.

Följande kommando innehåller till exempel autentiseringsuppgifterna för en administratör.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

Mer information om parametern för **autentiseringsuppgifter** finns i [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [RETUR-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) eller [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command).

### <a name="how-to-enable-remoting-for-non-administrative-users"></a>Så här aktiverar du fjärr kommunikation för icke-administrativa användare

```
ERROR:  ACCESS IS DENIED
```

Om du vill upprätta en PSSession eller köra ett kommando på en fjärrdator måste användaren ha behörighet att använda sessionens konfigurationer på fjärrdatorn.

Som standard har bara medlemmar i gruppen Administratörer på en dator behörighet att använda standardkonfigurationerna för sessioner. Därför kan endast medlemmar i gruppen Administratörer fjärrans luta till datorn.

Om du vill att andra användare ska kunna ansluta till den lokala datorn ger du användaren körnings behörighet till standardkonfigurationerna för sessioner på den lokala datorn.

Följande kommando öppnar en egenskaps sida där du kan ändra säkerhets beskrivningen för standard konfigurationen av Microsoft. PowerShell-sessionen på den lokala datorn.

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

Mer information finns i [about_Session_Configurations](about_Session_Configurations.md).

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a>Så här aktiverar du fjärr kommunikation för administratörer i andra domäner

```
ERROR:  ACCESS IS DENIED
```

När en användare i en annan domän är medlem i gruppen Administratörer på den lokala datorn kan användaren inte fjärrans luta till den lokala datorn med administratörs behörighet. Som standard körs fjärr anslutningar från andra domäner med bara standard-token för användar behörighet.

Du kan dock använda register posten **LocalAccountTokenFilterPolicy** för att ändra standard beteendet och tillåta att fjärran vändare som är medlemmar i gruppen Administratörer kan köra med administratörs behörighet.

> [!CAUTION]
> **LocalAccountTokenFilterPolicy** -posten inaktiverar fjärrbegränsningar för User Account Control (UAC) för alla användare av alla berörda datorer. Ta hänsyn till konsekvenserna av den här inställningen noggrant innan du ändrar principen.

Om du vill ändra principen använder du följande kommando för att ange värdet för register posten **LocalAccountTokenFilterPolicy** till 1.

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a>Använda en IP-adress i ett fjärran slutet kommando

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

Parametern **computername** för `New-PSSession` `Enter-PSSession` `Invoke-Command` CMDLETarna och accepterar en IP-adress som ett giltigt värde. Men eftersom Kerberos-autentisering inte stöder IP-adresser används NTLM-autentisering som standard när du anger en IP-adress.

När du använder NTLM-autentisering krävs följande procedur för fjärr kommunikation.

1. Konfigurera datorn för HTTPS-transport eller Lägg till IP-adresserna för fjärrdatorerna i listan TrustedHosts på den lokala datorn.

1. Använd parametern **Credential** i alla fjärrkommandon.

   Detta krävs även när du skickar in autentiseringsuppgifterna för den aktuella användaren.

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a>Fjärrans luta från en arbets grupps dator

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

Om den lokala datorn inte finns i en domän krävs följande procedur för fjärr kommunikation.

1. Konfigurera datorn för HTTPS-transport eller Lägg till namnen på fjärrdatorerna i listan TrustedHosts på den lokala datorn.

1. Kontrol lera att ett lösen ord har angetts på den arbets grupps dator. Om inget lösen ord har angetts eller om lösen ordet är tomt kan du inte köra fjärrkommandon.

   Ange lösen ordet för ditt användar konto med hjälp av användar konton på kontroll panelen.

1. Använd parametern **Credential** i alla fjärrkommandon.

   Detta krävs även när du skickar in autentiseringsuppgifterna för den aktuella användaren.

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a>Så här lägger du till en dator i listan över betrodda värdar

Objektet TrustedHosts kan innehålla en kommaavgränsad lista med dator namn, IP-adresser och fullständigt kvalificerade domän namn. Jokertecken är tillåtna.

Om du vill visa eller ändra listan över betrodda värdar använder du kommandot WSMan: Drive. TrustedHost-objektet finns i `WSMan:\localhost\Client` noden.

Endast medlemmar i gruppen Administratörer på datorn har behörighet att ändra listan över betrodda värdar på datorn.

Varning! det värde som du anger för objektet TrustedHosts påverkar alla användare av datorn.

Använd följande kommando om du vill visa en lista över betrodda värdar:

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

Du kan också använda `Set-Location` cmdleten (alias = CD) för att navigera om WSMan: enheten till platsen. Ett exempel:

```powershell
cd WSMan:\localhost\Client; dir
```

Om du vill lägga till alla datorer i listan över betrodda värdar använder du följande kommando, som placerar värdet * (alla) i ComputerName

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

Du kan också använda ett jokertecken ( `*` ) för att lägga till alla datorer i en viss domän i listan över betrodda värdar. Följande kommando lägger till exempel till alla datorer i domänen fabrikam i listan över betrodda värdar.

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

Om du vill lägga till namnen på vissa datorer i listan över betrodda värdar, använder du följande kommando format:

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

där varje värde `<ComputerName>` måste ha följande format:

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

Ett exempel:

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

Om du vill lägga till ett dator namn i en befintlig lista över betrodda värdar sparar du först det aktuella värdet i en variabel och anger sedan värdet till en kommaavgränsad lista som innehåller de aktuella och nya värdena.

Om du till exempel vill lägga till Server01-datorn i en befintlig lista över betrodda värdar, använder du följande kommando

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

Om du vill lägga till IP-adresserna för särskilda datorer i listan över betrodda värdar, använder du följande kommando format:

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

Ett exempel:

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

Om du vill lägga till en dator i listan TrustedHosts för en fjärrdator använder du `Connect-WSMan` cmdleten för att lägga till en nod för fjärrdatorn på enheten WSMan: på den lokala datorn. Använd sedan ett `Set-Item` kommando för att lägga till datorn.

Mer information om `Connect-WSMan` cmdleten finns i [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan).

## <a name="troubleshooting-computer-configuration-issues"></a>Felsöka problem med dator konfiguration

I det här avsnittet beskrivs fjärrproblem som är relaterade till särskilda konfigurationer av en dator, domän eller företag.

### <a name="how-to-configure-remoting-on-alternate-ports"></a>Konfigurera fjärr kommunikation på alternativa portar

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

PowerShell-fjärrkommunikation använder port 80 för HTTP-transport som standard. Standard porten används när användaren inte anger **ConnectionURI** eller **port** parametrar i ett fjärran slutet kommando.

Om du vill ändra standard porten som PowerShell använder använder `Set-Item` du cmdleten i WSMan: Drive för att ändra Portvärdet i noden lyssnare.

Följande kommando ändrar till exempel standard porten till 8080.

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a>Konfigurera fjärr kommunikation med en proxyserver

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

Eftersom PowerShell-fjärrkommunikation använder HTTP-protokollet, påverkas det av HTTP-proxyinställningarna. I företag som har proxyservrar kan användarna inte komma åt en PowerShell-fjärrdator direkt.

Lös problemet genom att använda alternativen för proxyservern i fjärrkommandon. Följande inställningar är tillgängliga:

- ProxyAccessType
- ProxyAuthentication
- ProxyCredential

Använd följande procedur för att ange de här alternativen för ett visst kommando:

1. Använd **ProxyAccessType** -, **ProxyAuthentication** -och **ProxyCredential** -parametrarna för `New-PSSessionOption` cmdlet: en för att skapa ett session-objekt med proxyinställningarna för ditt företag. Spara objektet alternativ är en variabel.

1. Använd variabeln som innehåller option-objektet som värdet för **SessionOption** -parametern för ett `New-PSSession` , `Enter-PSSession` -eller- `Invoke-Command` kommando.

Följande kommando skapar till exempel objektet Session-alternativ med alternativ för proxyautentisering och använder sedan objektet för att skapa en fjärrsession.

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

Mer information om `New-PSSessionOption` cmdleten finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

Om du vill ange de här alternativen för alla fjärrkommandon i den aktuella sessionen använder du alternativet objekt som `New-PSSessionOption` skapar i värdet för `$PSSessionOption` variabeln Preference. Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).

Om du vill ange de här alternativen för alla fjärrkommandon alla PowerShell-sessioner på den lokala datorn lägger du till `$PSSessionOption` preferens-variabeln i din PowerShell-profil. Mer information om PowerShell-profiler finns [about_Profiles](about_Profiles.md).

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a>Så här identifierar du en 32-bitars session på en 64-bitars dator

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Om fjärrdatorn kör en 64-bitars version av Windows och fjärrkommandot använder en 32-bitars konfiguration av sessionen, till exempel Microsoft. PowerShell32, Windows Remote Management (WinRM) läser in en WOW64-process och Windows omdirigerar automatiskt alla referenser till katalogen `$env:Windir\System32` till `$env:Windir\SysWOW64` katalogen.

Det innebär att om du försöker använda verktyg i katalogen System32 som inte har motsvarigheter i katalogen SysWow64, till exempel `Defrag.exe` , går det inte att hitta verktygen i katalogen.

Om du vill hitta den processor arkitektur som används i sessionen använder du värdet för variabeln **PROCESSOR_ARCHITECTURE** . Följande kommando hittar processor arkitekturen för sessionen i `$s` variabeln.

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](about_Session_Configurations.md).

## <a name="troubleshooting-policy-and-preference-issues"></a>Fel sökning av princip-och inställnings problem

I det här avsnittet beskrivs fjärrstyrda problem som är relaterade till principer och inställningar som anges på lokala datorer och fjärrdatorer.

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a>Ändra körnings principen för Import-PSSession och Import-Module

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

`Import-PSSession` `Export-PSSession` Cmdletarna och skapar moduler som innehåller osignerade skriptfiler och formaterar filer.

Om du vill importera moduler som skapats av dessa cmdlets, antingen med hjälp av `Import-PSSession` eller `Import-Module` , kan inte körnings principen i den aktuella sessionen vara begränsad eller AllSigned. Information om körnings principer för PowerShell finns i [about_Execution_Policies](about_Execution_Policies.md).

Om du vill importera modulerna utan att ändra körnings principen för den lokala datorn som anges i registret, använder du **omfattnings** parametern för `Set-ExecutionPolicy` att ange en mindre begränsande körnings princip för en enda process.

Följande kommando startar till exempel en process med `RemoteSigned` körnings principen. Ändringen av körnings principen påverkar endast den aktuella processen och ändrar inte register inställningen för PowerShell- **ExecutionPolicy** .

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

Du kan också använda **ExecutionPolicy** -parametern för `PowerShell.exe` för att starta en enskild session med en mindre begränsande körnings princip.

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

Mer information om körnings principer finns [about_Execution_Policies](about_Execution_Policies.md). För mer information ange `PowerShell.exe -?`.

### <a name="how-to-set-and-change-quotas"></a>Ange och ändra kvoter

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

Du kan använda kvoter för att skydda den lokala datorn och fjärrdatorn från överdriven resursanvändning, både av misstag och skadlig.

Följande kvoter är tillgängliga i den grundläggande konfigurationen.

- WSMan-providern (WSMan:) innehåller flera kvot inställningar, till exempel inställningarna **MaxEnvelopeSizeKB** och **MaxProviderRequests** i `WSMan:<ComputerName>` noden och inställningarna **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** och **MaxConnections** i `WSMan:<ComputerName>\Service` noden.

- Du kan skydda den lokala datorn med hjälp av parametrarna **MaximumReceivedDataSizePerCommand** och **MaximumReceivedObjectSize** för `New-PSSessionOption` cmdleten och `$PSSessionOption` variabeln Preference.

- Du kan skydda fjärrdatorn genom att lägga till begränsningar i sessionens konfigurationer, till exempel genom att använda parametrarna **MaximumReceivedDataSizePerCommandMB** och **MaximumReceivedObjectSizeMB** för `Register-PSSessionConfiguration` cmdleten.

När kvoter står i konflikt med ett kommando genererar PowerShell ett fel.

Lös felet genom att ändra fjärrkommandot så att det följer kvoten. Eller Bestäm kvotens källa och öka sedan kvoten för att tillåta att kommandot slutförs.

Följande kommando ökar till exempel kvoten för objekt storlek i konfigurationen av Microsoft. PowerShell-sessionen på fjärrdatorn från 10 MB (standardvärdet) till 11 MB.

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

Mer information om `New-PSSessionOption` cmdleten finns i `New-PSSessionOption` .

Mer information om WS-Management kvoter finns [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md).

### <a name="how-to-resolve-timeout-errors"></a>Så här löser du timeout-fel

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

Du kan använda tids gränser för att skydda den lokala datorn och fjärrdatorn från överdriven resursanvändning, både av misstag och skadlig. När timeout anges på både den lokala datorn och fjärrdatorn använder PowerShell de kortaste timeout-inställningarna.

Följande tids gränser är tillgängliga i den grundläggande konfigurationen.

- WSMan-providern (WSMan:) innehåller flera tids gräns inställningar på klient sidan och på tjänst sidan, till exempel **MaxTimeoutms** -inställningen i `WSMan:<ComputerName>` noden och inställningarna **EnumerationTimeoutms** och **MaxPacketRetrievalTimeSeconds** i `WSMan:<ComputerName>\Service` noden.

- Du kan skydda den lokala datorn med hjälp av parametrarna **CancelTimeout** , **idleTimeout** , **opentimey** och **OperationTimeout** för `New-PSSessionOption` cmdleten och `$PSSessionOption` variabeln Preference.

- Du kan också skydda fjärrdatorn genom att ange tids gräns värden program mässigt i sessionens konfiguration.

När ett timeout-värde inte tillåter att en åtgärd slutförs, avslutar PowerShell åtgärden och genererar ett fel.

Lös felet genom att ändra kommandot till slutfört inom timeout-intervallet eller bestämma källan för tids gränsen och öka tids gränsen för att tillåta att kommandot slutförs.

Följande kommandon använder exempelvis `New-PSSessionOption` cmdleten för att skapa ett session-objekt med ett **OperationTimeout** -värde på 4 minuter (i MS) och använder sedan objektet session för att skapa en fjärrsession.

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

Mer information om WS-Management timeout finns i hjälp avsnittet för WSMan-providern (typ `Get-Help WSMan` ).

Mer information om `New-PSSessionOption` cmdleten finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).

## <a name="troubleshooting-unresponsive-behavior"></a>Felsöka beteende som slutar svara

I det här avsnittet beskrivs fjärrstyrda problem som förhindrar att ett kommando slutförs och förhindrar eller skjuter tillbaka resultatet av PowerShell-prompten.

### <a name="how-to-interrupt-a-command"></a>Avbryta ett kommando

Vissa inbyggda Windows-program, till exempel program med ett användar gränssnitt, konsol program som efterfrågar indata och konsol program som använder Win32-konsolens API fungerar inte korrekt i PowerShell-Fjärrvärdet.

När du använder dessa program kan du se oväntade beteenden, t. ex. inga utdata, delvis utdata eller ett fjärrkommando som inte slutförs.

Om du vill avsluta ett program som inte svarar skriver du <kbd>CTRL</kbd> + <kbd>C</kbd>. Om du vill visa eventuella fel som rapporteras, skriver `$error` du in den lokala värden och fjärrsessionen.

## <a name="how-to-recover-from-an-operation-failure"></a>Återställa från ett åtgärds fel

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

Det här felet returneras när en åtgärd avslutas innan den har slutförts.
Vanligt vis inträffar det när WinRM-tjänsten stoppar eller startar om medan andra WinRM-åtgärder pågår.

Lös problemet genom att kontrol lera att WinRM-tjänsten körs och försök igen.

1. Starta PowerShell med alternativet **Kör som administratör** .
1. Kör följande kommando:

   `Start-Service WinRM`

1. Kör kommandot som genererade felet igen.

## <a name="linux-and-macos-limitations"></a>Begränsningar för Linux och macOS

### <a name="authentication"></a>Autentisering

Endast grundläggande autentisering fungerar på macOS och försöker använda andra autentiseringsscheman kan leda till att processen kraschar.

Se anvisningarna för [OMI-autentisering](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) .

## <a name="see-also"></a>SE ÄVEN

[Importera – PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[Exportera – PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[Importera-modul](xref:Microsoft.PowerShell.Core.Import-Module)

[about_Remote](about_Remote.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_Variables](about_Remote_Variables.md)
