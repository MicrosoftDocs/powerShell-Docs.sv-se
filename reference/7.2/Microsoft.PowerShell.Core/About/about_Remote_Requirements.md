---
description: Beskriver system krav och konfigurations krav för att köra fjärrkommandon i PowerShell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: 4a994ded51195e5932af7bb4af0b2e6fb3a67857
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708418"
---
# <a name="about-remote-requirements"></a>Om fjär krav

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver system krav och konfigurations krav för att köra fjärrkommandon i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

I det här avsnittet beskrivs system kraven, användar kraven och resurs kraven för att upprätta fjärr anslutningar och köra fjärrkommandon i PowerShell. Den innehåller också instruktioner för att konfigurera fjärråtgärder.

Obs! många cmdletar (inklusive get-service, get-process, get-WMIObject, get-EventLog och Get-WinEvent cmdlets) hämtar objekt från fjärrdatorer genom att använda Microsoft .NET Ramverks metoder för att hämta objekten. De använder inte PowerShell-infrastrukturen för fjärr kommunikation. Kraven i det här dokumentet gäller inte för dessa cmdletar.

Om du vill hitta de cmdlet: ar som har en ComputerName-parameter men inte använda PowerShell-fjärrkommunikation läser du beskrivningen av ComputerName-parametern för cmdletarna.

## <a name="system-requirements"></a>SYSTEM KRAV

Om du vill köra fjärrsessioner på Windows PowerShell 3,0 måste lokala och fjärranslutna datorer ha följande:

- Windows PowerShell 3,0 eller senare
- Microsoft .NET Framework 4 eller senare
- Windows Remote Management 3,0

Om du vill köra fjärrsessioner på Windows PowerShell 2,0 måste lokala och fjärranslutna datorer ha följande:

- Windows PowerShell 2,0 eller senare
- Microsoft .NET Framework 2,0 eller senare
- Windows Remote Management 2,0

Du kan skapa fjärrsessioner mellan datorer som kör Windows PowerShell 2,0 och Windows PowerShell 3,0. Funktioner som bara körs på Windows PowerShell 3,0, till exempel möjligheten att koppla från och återansluta till sessioner, är bara tillgängliga när båda datorerna kör Windows PowerShell 3,0.

Du hittar versions numret för en installerad version av PowerShell med hjälp av den automatiska variabeln $PSVersionTable.

Windows Remote Management (WinRM) 3,0 och Microsoft .NET Framework 4 ingår i Windows 8, Windows Server 2012 och senare versioner av Windows operativ system. WinRM 3,0 ingår i Windows Management Framework 3,0 för äldre operativ system. Installationen Miss lyckas om datorn inte har den version av WinRM eller Microsoft .NET Framework som krävs.

## <a name="user-permissions"></a>ANVÄNDARBEHÖRIGHETER

Om du vill skapa fjärrsessioner och köra fjärrkommandon måste den aktuella användaren som standard vara medlem i gruppen Administratörer på fjärrdatorn eller ange autentiseringsuppgifter för en administratör. Annars Miss lyckas kommandot.

De behörigheter som krävs för att skapa sessioner och köra kommandon på en fjärrdator (eller i en fjärran sluten session på den lokala datorn) upprättas av konfigurationen av sessionen (även kallat "slut punkt") på den fjärrdator som sessionen ansluter till. Mer specifikt bestämmer säkerhets beskrivningen i konfigurationen vem som har åtkomst till sessionen och vem som kan använda den för att ansluta.

Säkerhets beskrivarna på standardkonfigurationerna för sessioner, Microsoft. PowerShell, Microsoft. PowerShell32 och Microsoft. PowerShell. workflow, tillåter endast åtkomst till medlemmar i gruppen Administratörer.

Om den aktuella användaren inte har behörighet att använda-sessionen, kan kommandot för att köra ett kommando (som använder en tillfällig session) eller skapa en beständig session på fjärrdatorn Miss lyckas. Användaren kan använda parametern ConfigurationName för cmdletar som skapar sessioner för att välja en annan sessionsinformation, om en sådan finns tillgänglig.

Medlemmar i gruppen Administratörer på en dator kan bestämma vem som har behörighet att fjärrans luta till datorn genom att ändra säkerhets beskrivarna på standardkonfigurationerna för sessioner och genom att skapa nya sessionsinställningar med olika säkerhets beskrivningar.

För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](about_Session_Configurations.md).

## <a name="windows-network-locations"></a>WINDOWS NÄTVERKS PLATSER

Från och med Windows PowerShell 3,0 kan Enable-PSRemoting cmdlet aktivera fjärr kommunikation på klient-och Server versioner av Windows i privata, domän och offentliga nätverk.

I Server versioner av Windows med privata nätverk och domän nätverk skapar cmdleten Enable-PSRemoting brand Väggs regler som tillåter obegränsad fjärråtkomst. Det skapar också en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät. Den här brand Väggs regeln för lokalt undernät är aktive rad som standard på Server versioner av Windows i offentliga nätverk, men Enable-PSRemoting tillämpar regeln på om den har ändrats eller tagits bort.

I klient versioner av Windows med privata nätverk och domän nätverk, skapar Enable-PSRemoting-cmdlet som standard brand Väggs regler som tillåter obegränsad fjärråtkomst.

Om du vill aktivera fjärr kommunikation på klient versioner av Windows med offentliga nätverk använder du parametern SkipNetworkProfileCheck i Enable-PSRemoting-cmdleten. Den skapar en brand Väggs regel som endast tillåter fjärråtkomst från datorer i samma lokala undernät.

Om du vill ta bort begränsningen för lokal undernät i offentliga nätverk och tillåta fjärråtkomst från alla platser på klient-och Server versioner av Windows, använder du Set-NetFirewallRule cmdlet i modulen netsecurity. Kör följande kommando:

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

I Windows PowerShell 2,0, i Server versioner av Windows, skapar Enable-PSRemoting brand Väggs regler som tillåter fjärråtkomst i alla nätverk.

I Windows PowerShell 2,0 skapar Enable-PSRemoting brand Väggs regler endast för privata nätverk och domän nätverk på klient versioner av Windows. Om nätverks platsen är offentlig Enable-PSRemoting Miss lyckas.

## <a name="run-as-administrator"></a>KÖR SOM ADMINISTRATÖR

Administratörs behörighet krävs för följande fjärr kommunikations åtgärder:

- Upprätta en fjärr anslutning till den lokala datorn. Detta kallas ofta "loopback"-scenario.

- Hantera sessionsinställningar på den lokala datorn.

- Visa och ändra WS-Management inställningar på den lokala datorn. Detta är inställningarna i noden LocalHost för kommandot WSMAN: Drive.

Om du vill utföra dessa uppgifter måste du starta PowerShell med alternativet "kör som administratör" även om du är medlem i gruppen Administratörer på den lokala datorn.

Starta Windows PowerShell med alternativet "kör som administratör" i Windows 7 och Windows Server 2008 R2:

1. Klicka på Start, klicka på alla program, klicka på tillbehör och klicka sedan på Windows PowerShell-mappen.
2. Högerklicka på Windows PowerShell och klicka sedan på Kör som administratör.

Starta Windows PowerShell med alternativet "kör som administratör":

1. Klicka på Start, klicka på alla program och klicka sedan på Windows PowerShell-mappen.
2. Högerklicka på Windows PowerShell och klicka sedan på Kör som administratör.

Alternativet "kör som administratör" är också tillgängligt i andra Windows Explorer-poster för Windows PowerShell, inklusive genvägar. Högerklicka bara på objektet och klicka sedan på Kör som administratör.

När du startar Windows PowerShell från ett annat program, till exempel Cmd.exe, använder du alternativet "kör som administratör" för att starta programmet.

## <a name="how-to-configure-your-computer-for-remoting"></a>SÅ HÄR KONFIGURERAR DU DIN DATOR FÖR FJÄRR KOMMUNIKATION

Datorer som kör alla Windows-versioner som stöds kan upprätta fjärr anslutningar till och köra fjärrkommandon i PowerShell utan någon konfiguration. Men om du vill ta emot anslutningar och tillåta användare att skapa lokala och fjärranslutna användar hanterade PowerShell-sessioner ("PSSessions") och köra kommandon på den lokala datorn måste du aktivera PowerShell-fjärrkommunikation på datorn.

Windows Server 2012 och nyare versioner av Windows Server är aktiverade för PowerShell-fjärrkommunikation som standard. Om inställningarna har ändrats kan du återställa standardinställningarna genom att köra cmdleten Enable-PSRemoting.

I alla andra versioner av Windows som stöds måste du köra cmdleten Enable-PSRemoting för att aktivera PowerShell-fjärrkommunikation.

Funktionerna för fjärr kommunikation i PowerShell stöds av WinRM-tjänsten, som är Microsofts implementering av protokollet webb tjänster för hantering (WS-Management). När du aktiverar PowerShell-fjärrkommunikation ändrar du standard konfigurationen för WS-Management och lägger till system konfiguration som tillåter användare att ansluta till WS-Management.

Så här konfigurerar du PowerShell för att ta emot fjärrkommandon:

1. Starta PowerShell med alternativet "kör som administratör".
2. Skriv `Enable-PSRemoting` i kommandotolken

Kontrol lera att fjärr kommunikation är korrekt konfigurerad genom att köra ett test kommando, till exempel följande kommando, som skapar en fjärrsession på den lokala datorn.

```powershell
New-PSSession
```

Om fjärr kommunikation har kon figurer ATS korrekt skapar kommandot en session på den lokala datorn och returnerar ett objekt som representerar sessionen. Utdata bör likna följande exempel på utdata:

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

Om kommandot Miss lyckas finns mer information i [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md).

## <a name="understand-policies"></a>FÖRSTÅ PRINCIPER

När du arbetar på distans använder du två instanser av PowerShell, en på den lokala datorn och en på fjärrdatorn. Resultatet blir att ditt arbete påverkas av Windows-principerna och PowerShell-principerna på lokala datorer och fjärrdatorer.

I allmänhet gäller att innan du ansluter och när du upprättar anslutningen, gäller principerna på den lokala datorn. När du använder anslutningen gäller principerna på fjärrdatorn.

## <a name="basic-authentication-limitations-on-linux-and-macos"></a>Grundläggande begränsningar för autentisering på Linux och macOS

Vid anslutning från ett Linux-eller macOS-system till Windows stöds inte grundläggande autentisering över HTTP. Grundläggande autentisering kan användas över HTTPS genom att installera ett certifikat på mål servern. Certifikatet måste ha ett CN-namn som matchar värd namnet, har inte gått ut eller återkallats. Ett självsignerat certifikat kan användas i test syfte.

Mer information finns i [så här gör du: Konfigurera WINRM för https](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) .

Följande kommando, som körs från en upphöjd kommando tolk, konfigurerar HTTPS-lyssnaren på Windows med det installerade certifikatet.

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

På Linux-eller macOS-sidan väljer du Basic för autentisering och-UseSSl.

> Obs! grundläggande autentisering kan inte användas med domän konton. ett lokalt konto krävs och kontot måste vara i gruppen Administratörer.

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

Ett alternativ till grundläggande autentisering över HTTPS är Negotiate. Detta resulterar i att NTLM-autentisering mellan klienten och servern och nytto lasten krypteras över HTTP.

Följande exempel visar hur du använder Negotiate med New-PSSession:

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> Windows Server kräver ytterligare en register inställning för att göra det möjligt för administratörer, förutom den inbyggda administratören, att ansluta med hjälp av NTLM.
> Läs register inställningen LocalAccountTokenFilterPolicy under förhandla autentisering i [autentisering för fjärr anslutningar](/windows/win32/winrm/authentication-for-remote-connections)

## <a name="see-also"></a>SE ÄVEN

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

