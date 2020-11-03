---
description: Innehåller frågor och svar om att köra fjärrkommandon i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: db3b7b554096c0cee6f13365dd8b2fbacb498282
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271695"
---
# <a name="about-remote-faq"></a>Om vanliga frågor och svar om fjärr anslutning

## <a name="short-description"></a>Kort beskrivning
Innehåller frågor och svar om att köra fjärrkommandon i PowerShell.

## <a name="long-description"></a>Lång beskrivning

När du arbetar fjärran slutet, skriver du kommandon i PowerShell på en dator (kallas "lokal dator"), men kommandona körs på en annan dator (kallas "fjärrdatorn"). Upplevelsen av fjärr anslutning bör vara så mycket som att fungera direkt på fjärrdatorn som möjligt.

Obs: om du vill använda PowerShell-fjärrkommunikation måste fjärrdatorn konfigureras för fjärr kommunikation. Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).

### <a name="must-both-computers-have-powershell-installed"></a>Måste båda datorerna ha PowerShell installerat?

Ja. För att kunna arbeta på distans måste lokala och fjärranslutna datorer ha PowerShell, Microsoft .NET Framework och protokollet för hantering av webb tjänster (WS-Management). Alla filer och andra resurser som behövs för att köra ett visst kommando måste finnas på fjärrdatorn.

Datorer som kör Windows PowerShell 3,0 och datorer som kör Windows PowerShell 2,0 kan fjärrans luta till varandra och köra fjärrkommandon.
Men vissa funktioner, till exempel möjligheten att koppla från en session och återansluta till den, fungerar endast när båda datorerna kör Windows PowerShell 3,0.

Du måste ha behörighet att ansluta till fjärrdatorn, tillåtelse att köra PowerShell och behörighet att komma åt data lager (till exempel filer och mappar) och registret på fjärrdatorn.

Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).

### <a name="how-does-remoting-work"></a>Hur fungerar fjärr kommunikation?

När du skickar ett fjärrkommando skickas kommandot över nätverket till PowerShell-motorn på fjärrdatorn och körs i PowerShell-klienten på fjärrdatorn. Kommando resultatet skickas tillbaka till den lokala datorn och visas i PowerShell-sessionen på den lokala datorn.

För att skicka kommandon och ta emot utdata använder PowerShell WS-Management-protokollet. Information om WS-Management-protokollet finns i [WS-Management-protokollet](/windows/win32/winrm/ws-management-protocol) i Windows-dokumentationen.

Från och med Windows PowerShell 3,0 lagras fjärrsessioner på fjärrdatorn. På så sätt kan du koppla från sessionen och återansluta från en annan session eller en annan dator utan att avbryta kommandona eller förlora tillstånd.

### <a name="is-powershell-remoting-secure"></a>Är PowerShell-fjärrkommunikation säker?

När du ansluter till en fjärrdator använder systemet användar namn och lösen ord för att logga in på den lokala datorn eller de autentiseringsuppgifter som du anger i kommandot för att logga in dig på fjärrdatorn. Autentiseringsuppgifterna och resten av överföringen är krypterade.

Om du vill lägga till ytterligare skydd kan du konfigurera fjärrdatorn att använda Secure Sockets Layer (SSL) i stället för HTTP för att lyssna efter WinRM-begäranden (Windows Remote Management). Sedan kan användarna använda parametern **UseSSL** i `Invoke-Command` `New-PSSession` cmdletarna, och för att `Enter-PSSession` upprätta en anslutning. Det här alternativet använder den säkrare HTTPS-kanalen i stället för HTTP.

### <a name="do-all-remote-commands-require-powershell-remoting"></a>Kräver alla fjärrkommandon PowerShell-fjärrkommunikation?

Nej. Flera cmdlets har en **computername** -parameter som låter dig hämta objekt från fjärrdatorn.

Dessa cmdletar använder inte PowerShell-fjärrkommunikation. Så du kan använda dem på alla datorer som kör PowerShell, även om datorn inte har kon figurer ATS för PowerShell-fjärrkommunikation eller om datorn inte uppfyller kraven för PowerShell-fjärrkommunikation.

Dessa cmdletar innehåller följande:

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

Om du vill hitta alla cmdletar med parametern **computername** skriver du:

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

För att avgöra om parametern **computername** för en viss cmdlet kräver PowerShell-fjärrkommunikation, se parameter beskrivningen. Om du vill visa parameter beskrivningen skriver du:

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

Ett exempel:

```powershell
Get-Help Get-Process -Parameter ComputerName
```

Använd cmdleten för alla andra kommandon `Invoke-Command` .

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a>Hur gör jag för att du köra ett kommando på en fjärrdator?

Använd cmdleten om du vill köra ett kommando på en fjärrdator `Invoke-Command` .

Sätt ditt kommando i klammerparenteser ( `{}` ) för att göra det till ett skript block. Använd parametern **script block** för `Invoke-Command` för att ange kommandot.

Du kan använda parametern **computername** för `Invoke-Command` för att ange en fjärrdator. Du kan också skapa en permanent anslutning till en fjärrdator (en session) och sedan använda parametern **session** för `Invoke-Command` att köra kommandot i sessionen.

Följande kommandon kör till exempel ett- `Get-Process` kommando via fjärr anslutning.

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

Om du vill avbryta ett fjärrkommando skriver du <kbd>CTRL</kbd> + <kbd>C</kbd>. Avbrotts förfrågan skickas till fjärrdatorn, där den avslutar fjärrkommandot.

Mer information om fjärrkommandon finns i about_Remote och hjälp avsnitten för de cmdletar som stöder fjärr kommunikation.

### <a name="can-i-just-telnet-into-a-remote-computer"></a>Kan jag bara Telnet till en fjärrdator?

Du kan använda `Enter-PSSession` cmdleten för att starta en interaktiv session med en fjärran sluten dator.

I PowerShell-prompten skriver du:

```powershell
Enter-PSSession <ComputerName>
```

Kommando tolken ändras för att visa att du är ansluten till fjärrdatorn.

```
<ComputerName>\C:>
```

Nu kan de kommandon som du skriver köra på fjärrdatorn precis som om du skrev dem direkt på fjärrdatorn.

Om du vill avsluta den interaktiva sessionen skriver du:

```powershell
Exit-PSSession
```

En interaktiv session är en beständig session som använder WS-Management-protokollet. Det är inte samma sak som att använda Telnet, men det ger samma upplevelse.

Mer information finns i `Enter-PSSession`.

### <a name="can-i-create-a-persistent-connection"></a>Kan jag skapa en permanent anslutning?

Ja. Du kan köra fjärrkommandon genom att ange namnet på fjärrdatorn, dess NetBIOS-namn eller dess IP-adress. Du kan också köra fjärrkommandon genom att ange en PowerShell-session (PSSession) som är ansluten till fjärrdatorn.

När du använder parametern **computername** för `Invoke-Command` eller `Enter-PSSession` , upprättar PowerShell en tillfällig anslutning. PowerShell använder anslutningen för att bara köra det aktuella kommandot och sedan stängs anslutningen. Det här är en mycket effektiv metod för att köra ett enda kommando eller flera orelaterade kommandon, även på många fjärrdatorer.

När du använder `New-PSSession` cmdleten för att skapa en PSSession upprättar PowerShell en permanent anslutning för PSSession. Sedan kan du köra flera kommandon i PSSession, inklusive kommandon som delar data.

Normalt skapar du en PSSession för att köra en serie relaterade kommandon som delar data. Annars räcker den tillfälliga anslutningen som skapas av parametern **computername** för de flesta kommandon.

Mer information om sessioner finns about_PSSessions.

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a>Kan jag köra kommandon på fler än en dator åt gången?

Ja. Parametern **computername** för `Invoke-Command` cmdleten accepterar flera dator namn och parametern **session** accepterar flera PSSessions.

När du kör ett `Invoke-Command` kommando kör PowerShell kommandona på alla angivna datorer eller i alla angivna PSSessions.

PowerShell kan hantera hundratals samtidiga fjärr anslutningar. Antalet fjärrkommandon som du kan skicka kan dock begränsas av resurserna på din dator och dess kapacitet att upprätta och underhålla flera nätverks anslutningar.

Mer information finns i exemplet i `Invoke-Command` Hjälp avsnittet.

### <a name="where-are-my-profiles"></a>Var finns mina profiler?

PowerShell-profiler körs inte automatiskt i fjärrsessioner, så de kommandon som profilen lägger till finns inte i sessionen. Dessutom `$profile` är den automatiska variabeln inte ifylld i fjärrsessioner.

Använd cmdleten för att köra en profil i en session `Invoke-Command` .

Följande kommando kör till exempel CurrentUserCurrentHost-profilen från den lokala datorn i sessionen i `$s` .

```
Invoke-Command -Session $s -FilePath $profile
```

Följande kommando kör CurrentUserCurrentHost-profilen från fjärrdatorn i sessionen i `$s` . Eftersom `$profile` variabeln inte är ifylld använder kommandot den explicita sökvägen till profilen.

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

När du har kört det här kommandot är de kommandon som profilen lägger till i sessionen tillgängliga i `$s` .

Du kan också använda ett start skript i en sessionshantering för att köra en profil i varje fjärrsession som använder-sessionen.

Mer information om PowerShell-profiler finns about_Profiles.
Mer information om sessionsdata finns i `Register-PSSessionConfiguration` .

### <a name="how-does-throttling-work-on-remote-commands"></a>Hur fungerar begränsningen på fjärrkommandona?

För att hjälpa dig att hantera resurserna på den lokala datorn innehåller PowerShell en funktion för begränsning av varje kommando som gör att du kan begränsa antalet samtidiga fjärr anslutningar som upprättas för varje kommando.

Standardvärdet är 32 samtidiga anslutningar, men du kan använda parametern **ThrottleLimit** för cmdletarna för att ange en anpassad begränsnings gräns för vissa kommandon.

När du använder begränsnings funktionen måste du komma ihåg att den tillämpas på varje kommando, inte i hela sessionen eller på datorn. Om du kör kommandon samtidigt i flera sessioner eller PSSessions är antalet samtidiga anslutningar summan av samtidiga anslutningar i alla sessioner.

Om du vill hitta cmdletar med en **ThrottleLimit** -parameter skriver du:

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a>Skiljer sig utdata från fjärrkommandon från lokala utdata?

När du använder PowerShell lokalt kan du skicka och ta emot "Live" .NET Framework objekt; "Live"-objekt är objekt som är associerade med faktiska program eller system komponenter. När du anropar metoderna eller ändrar egenskaperna för Live-objekt påverkar ändringarna det faktiska programmet eller den aktuella komponenten. När egenskaperna för ett program eller en komponent ändras, ändras även egenskaperna för objektet som representerar dem.

Men eftersom de flesta Live-objekt inte kan överföras via nätverket, serialiserar PowerShell "de flesta objekt som skickas i fjärrkommandon, det vill säga varje objekt till en serie med XML (begränsnings språk i XML [CLiXML]) data element för överföring.

När PowerShell tar emot ett serialiserat objekt, konverterar det XML till en avserialiserad objekt typ. Det avserialiserade objektet är en korrekt post för programmets eller komponentens egenskaper vid en tidigare tidpunkt, men är inte längre "Live", det vill säga att det inte längre är direkt kopplat till komponenten. Och metoderna tas bort eftersom de inte längre gäller.

Normalt kan du använda avserialiserade objekt på samma sätt som du använder Live-objekt, men du måste vara medveten om deras begränsningar. Dessutom har de objekt som returneras av cmdlet: en `Invoke-Command` Ytterligare egenskaper som hjälper dig att fastställa kommandots ursprung.

Vissa objekt typer, till exempel DirectoryInfo-objekt och GUID, konverteras tillbaka till aktiva objekt när de tas emot. Dessa objekt behöver inte någon särskild hantering eller formatering.

Information om hur du tolkar och formaterar fjärrutdata finns i [about_Remote_Output](about_Remote_Output.md).

### <a name="can-i-run-background-jobs-remotely"></a>Kan jag köra bakgrunds jobb på distans?

Ja. Ett PowerShell-bakgrunds jobb är ett PowerShell-kommando som körs asynkront utan att samverka med sessionen. När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart och du kan fortsätta att arbeta i sessionen medan jobbet körs även om det körs under en längre tid.

Du kan starta ett bakgrunds jobb även om andra kommandon körs eftersom bakgrunds jobb alltid körs asynkront i en tillfällig session.

Du kan köra bakgrunds jobb på en lokal dator eller fjärrdator. Som standard körs ett bakgrunds jobb på den lokala datorn. Du kan dock använda **AsJob** -parametern för `Invoke-Command` cmdleten för att köra ett fjärrkommando som bakgrunds jobb. Du kan också använda `Invoke-Command` för att köra ett `Start-Job` kommando via fjärr anslutning.

Mer information om bakgrunds jobb i PowerShell finns i [about_Jobs (about_Jobs. MD)] och [about_Remote_Jobs (about_Remote_Jobs. MD)].

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a>Kan jag köra Windows-program på en fjärran sluten dator?

Du kan använda PowerShell-fjärrkommandon för att köra Windows-baserade program på fjärrdatorer. Du kan till exempel köra `Shutdown.exe` eller `Ipconfig.exe` på en fjärran sluten dator.

Du kan dock inte använda PowerShell-kommandon för att öppna användar gränssnittet för alla program på en fjärrdator.

När du startar ett Windows-program på en fjärrdator slutförs inte kommandot och kommando tolken i PowerShell returnerar inte förrän programmet är klart eller tills du trycker på <kbd>CTRL</kbd> + <kbd>C</kbd> för att avbryta kommandot. Om du till exempel kör `Ipconfig.exe` programmet på en fjärrdator returneras inte kommando tolken förrän `Ipconfig.exe` har slutförts.

Om du använder fjärrkommandon för att starta ett program som har ett användar gränssnitt startar program processen, men användar gränssnittet visas inte. PowerShell-kommandot slutförs inte och kommando tolken returneras inte förrän du stoppar program processen eller tills du trycker på <kbd>CTRL</kbd> + <kbd>C</kbd>, som avbryter kommandot och stoppar processen.

Om du till exempel använder ett PowerShell-kommando för att köra `Notepad` på en fjärrdator, startar anteckningar-processen på fjärrdatorn, men användar gränssnittet i anteckningar visas inte. Tryck på <kbd>CTRL</kbd>C om du vill avbryta kommandot och återställa kommando tolken + <kbd>C</kbd>.

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a>Kan jag begränsa de kommandon som användarna kan köra via fjärr anslutning på datorn?

Ja. Varje fjärran sluten session måste använda en av sessionens konfigurationer på fjärrdatorn. Du kan hantera sessionsinställningar på din dator (och behörigheterna för dessa sessioner) för att fastställa vem som kan köra kommandon på en annan dator och vilka kommandon de kan köra.

En konfiguration av sessionen konfigurerar miljön för sessionen. Du kan definiera konfigurationen genom att använda en sammansättning som implementerar en ny konfigurations klass eller genom att använda ett skript som körs i sessionen. Konfigurationen kan avgöra vilka kommandon som är tillgängliga i sessionen.
Konfigurationen kan dessutom innehålla inställningar som skyddar datorn, till exempel inställningar som begränsar mängden data som sessionen kan ta emot via fjärr anslutning i ett enda objekt eller kommando. Du kan också ange en säkerhets beskrivning som avgör vilka behörigheter som krävs för att använda konfigurationen.

`Enable-PSRemoting`Cmdleten skapar standardkonfigurationerna för sessioner på datorn: Microsoft. PowerShell, Microsoft. PowerShell. Workflow och Microsoft. PowerShell32 (endast 64-bitars operativ system). `Enable-PSRemoting` anger säkerhets beskrivningen för konfigurationen så att endast medlemmar i gruppen Administratörer på datorn kan använda dem.

Du kan använda konfigurations-cmdletar för sessioner för att redigera standardkonfigurationerna för sessioner, skapa nya sessionsinställningar och ändra säkerhets beskrivare för alla sessioner.

Från och med Windows PowerShell 3,0 `New-PSSessionConfigurationFile` kan du skapa anpassade sessionsnycklar med hjälp av en textfil. Filen innehåller alternativ för att ställa in språk läget och för att ange de cmdletar och moduler som är tillgängliga i sessioner som använder sessionen.

När användarna använder `Invoke-Command` `New-PSSession` cmdletarna, eller, `Enter-PSSession` kan de använda **ConfigurationName** -parametern för att ange den sessionsinformation som används för sessionen. Dessutom kan de ändra standard konfigurationen som deras sessioner använder genom att ändra värdet för `$PSSessionConfigurationName` variabeln Preference i sessionen.

Mer information om sessionsbaserade finns i hjälpen för cmdletarna för session konfiguration. Om du vill hitta sessionens konfigurations-cmdletar skriver du:

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a>Vad är fläkt i och fläktiga konfigurationer?

Det vanligaste scenariot för PowerShell-fjärrkommunikation som omfattar flera datorer är en-till-många-konfiguration, där en lokal dator (administratörens dator) kör PowerShell-kommandon på flera fjärrdatorer. Detta kallas för "fläkt ut"-scenariot.

I vissa företag är konfigurationen emellertid många-till-en, där många klient datorer ansluter till en enda fjärrdator som kör PowerShell, till exempel en fil server eller en kiosk. Detta kallas för "fläkt-in"-konfigurationen.

PowerShell-fjärrkommunikation stöder både fläkt-och fläkt konfiguration.

För fläkt konfigurationen använder PowerShell protokollet webb tjänster för hantering (WS-Management) och den WinRM-tjänst som stöder Microsoft-implementeringen av WS-Management. När en lokal dator ansluter till en fjärrdator upprättar WS-Management en anslutning och använder ett plugin-program för PowerShell för att starta PowerShell-värd processen (Wsmprovhost.exe) på fjärrdatorn. Användaren kan ange en alternativ port, en alternativ konfiguration av sessionen och andra funktioner för att anpassa fjärr anslutningen.

För att stödja "fläkt-in"-konfigurationen använder PowerShell IIS (Internet Information Services) för att hantera WS-Management, läsa in PowerShell-plugin-programmet och starta PowerShell. I det här scenariot, i stället för att starta varje PowerShell-session i en separat process, körs alla PowerShell-sessioner i samma värd process.

IIS-värd och fläkt-in-fjärrhantering stöds inte i Windows XP eller Windows Server 2003.

I en fläkt konfiguration kan användaren ange en anslutnings-URI och en HTTP-slutpunkt, inklusive transport, dator namn, port och program namn.
IIS vidarebefordrar alla förfrågningar med ett angivet program namn till programmet. Standardvärdet är WS-Management, som kan vara värd för PowerShell.

Du kan också ange en autentiseringsmekanism och förhindra eller tillåta omdirigering från HTTP-och HTTPS-slutpunkter.

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a>Kan jag testa fjärr kommunikation på en enskild dator som inte är i en domän?

Ja. PowerShell-fjärrkommunikation är tillgängligt även när den lokala datorn inte finns i en domän. Du kan använda funktionerna för fjärr anslutning för att ansluta till sessioner och för att skapa sessioner på samma dator. Funktionerna fungerar på samma sätt som när du ansluter till en fjärran sluten dator.

Om du vill köra fjärrkommandon på en dator i en arbets grupp ändrar du följande Windows-inställningar på datorn.

Varning! de här inställningarna påverkar alla användare i systemet och de kan göra systemet mer sårbart för angrepp. Var försiktig när du gör dessa ändringar.

- Windows Vista, Windows 7, Windows 8:

  Skapa följande register post och ange värdet till 1: LocalAccountTokenFilterPolicy i ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

  Du kan använda följande PowerShell-kommando för att lägga till följande post:

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:

  Inga ändringar krävs eftersom standardinställningen för principen "nätverks åtkomst: delning och säkerhets modell för lokala konton" är "klassisk". Kontrol lera inställningen om den har ändrats.

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a>Kan jag köra fjärrkommandon på en dator i en annan domän?

Ja. Vanligt vis körs kommandona utan fel, men du kan behöva använda parametern **Credential** för `Invoke-Command` `New-PSSession` `Enter-PSSession` cmdletarna, eller för att ange autentiseringsuppgifter för en medlem i gruppen Administratörer på fjärrdatorn. Detta krävs ibland även om den aktuella användaren är medlem i gruppen Administratörer på den lokala datorn och fjärrdatorn.

Men om fjärrdatorn inte finns i en domän som den lokala datorn litar på, kanske inte fjärrdatorn kan autentisera användarens autentiseringsuppgifter.

Om du vill aktivera autentisering använder du följande kommando för att lägga till fjärrdatorn i listan över betrodda värdar för den lokala datorn i WinRM. Skriv kommandot vid PowerShell-prompten.

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

Om du till exempel vill lägga till Server01-datorn i listan över betrodda värdar på den lokala datorn skriver du följande kommando i PowerShell-prompten:

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a>Stöder PowerShell fjärr kommunikation via SSH?

Ja. Mer information finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="see-also"></a>Se även

[about_Remote](about_Remote.md)

[about_Profiles](about_Profiles.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote_Jobs](about_Remote_Jobs.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
