---
description: Förklarar hur du kopplar från och återansluter till en PowerShell-session (PSSession).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_disconnected_sessions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Disconnected_Sessions
ms.openlocfilehash: 68903485ce92a692453bfba4aa5097dd062437f9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271701"
---
# <a name="about-remote-disconnected-sessions"></a>Om fjärranslutna sessioner

## <a name="short-description"></a>Kort beskrivning

Förklarar hur du kopplar från och återansluter till en PowerShell-session (PSSession).

## <a name="long-description"></a>Lång beskrivning

Från och med PowerShell 3,0 kan du koppla från en PSSession och återansluta till PSSession på samma dator eller en annan dator. Sessionstillståndet upprätthålls och kommandon i PSSession fortsätter att köras medan sessionen kopplas från.

Funktionen frånkopplade sessioner är bara tillgänglig när fjärrdatorn kör PowerShell 3,0 eller en senare version.

Med funktionen frånkopplade sessioner kan du stänga sessionen där en PSSession skapades, och till och med stänga PowerShell och stänga av datorn, utan att avbryta kommandon som körs i PSSession. Frånkopplade sessioner är användbara för att köra kommandon som tar lång tid att slutföra och ger den tid och den flexibilitet som IT-proffs kräver.

Du kan inte koppla från en interaktiv session som har startats med hjälp av `Enter-PSSession` cmdleten.

Du kan använda frånkopplade sessioner för att hantera PSSessions som frånkopplats oavsiktligt på grund av en dators eller ett nätverks avbrott.

I verkligheten kan du använda funktionen frånkopplade sessioner för att lösa ett problem, förvandla din uppmärksamhet till ett problem med högre prioritet och sedan återuppta arbetet med lösningen, även på en annan dator på en annan plats.

## <a name="disconnected-session-cmdlets"></a>Cmdletar för frånkopplade sessioner

Följande cmdletar stöder funktionen frånkopplade sessioner:

- `Connect-PSSession`: Ansluter till en frånkopplad PSSession.
- `Disconnect-PSSession`: Kopplar från en PSSession.
- `Get-PSSession`: Hämtar PSSessions på den lokala datorn eller på fjärrdatorer.
- `Receive-PSSession`: Hämtar resultatet från kommandon som kördes i frånkopplade sessioner.
- `Invoke-Command`: **InDisconnectedSession** -parametern skapar en PSSession och kopplar från omedelbart.

## <a name="how-the-disconnected-sessions-feature-works"></a>Så här fungerar funktionen frånkopplade sessioner

Från och med PowerShell 3,0 är PSSessions oberoende av de sessioner som de har skapats i. Aktiva PSSessions underhålls på fjärrdatorn eller **Server sidan** av anslutningen, även om sessionen där PSSession skapades är stängd och den ursprungliga datorn stängs av eller kopplas från nätverket.

I PowerShell 2,0 tas PSSession bort från fjärrdatorn när den kopplas bort från den ursprungliga sessionen eller den session där den skapades.

När du kopplar från en PSSession förblir PSSession aktiv och bevaras på fjärrdatorn. Sessionstillståndet ändras från att **köras** till **frånkopplat**. Du kan återansluta till en frånkopplad PSSession från den aktuella sessionen eller från en annan session på samma dator, eller från en annan dator. Den fjärrdator som underhåller sessionen måste köras och vara ansluten till nätverket.

Kommandon i en frånkopplad PSSession fortsätter att köras utan avbrott på fjärrdatorn tills kommandot har slutförts eller när utdatabufferten fylls. Om du vill förhindra att en fullständig utdatabuffert pausar ett kommando använder du parametern **OutputBufferingMode** i `Disconnect-PSSession` `New-PSSessionOption` cmdletarna,, eller `New-PSTransportOption` .

Frånkopplade sessioner underhålls i frånkopplat läge på fjärrdatorn. De är tillgängliga så att du kan återansluta tills du tar bort PSSession, till exempel med hjälp av `Remove-PSSession` cmdleten eller tills tids gränsen för inaktivitet för PSSession går ut. Du kan ändra tids gränsen för inaktivitet för en PSSession med hjälp av **IdleTimeoutSec** -eller **idleTimeout** -parametrarna för `Disconnect-PSSession` -, `New-PSSessionOption` -eller- `New-PSTransportOption` cmdlet: arna.

En annan användare kan ansluta till PSSessions som du har skapat, men endast om de kan ange de autentiseringsuppgifter som användes för att skapa sessionen eller använda `RunAs` autentiseringsuppgifterna för sessionen.

## <a name="how-to-get-pssessions"></a>Så här hämtar du PSSessions

Från och med PowerShell 3,0 `Get-PSSession` hämtar cmdlet: en PSSessions på den lokala datorn och fjärrdatorer. Den kan också hämta PSSessions som har skapats i den aktuella sessionen.

Om du vill hämta PSSessions på den lokala datorn eller fjärrdatorer använder du parametrarna **computername** eller **ConnectionUri** . Utan parametrar `Get-PSSession` hämtar PSSession som skapats i den lokala sessionen, oavsett var de avslutas.

Kom ihåg att leta efter dem på den dator där de befinner sig, det vill säga fjärrdatorn eller **Server sidan** när du hämtar PSSessions.

Om du till exempel skapar en PSSession till Server01-datorn hämtar du sessionen från Server01-datorn. Om du skapar en PSSession från en annan dator till den lokala datorn hämtar du sessionen från den lokala datorn.

Följande kommando sekvens visar hur `Get-PSSession` fungerar.

Det första kommandot skapar en session till Server01-datorn. Sessionen finns på Server01-datorn.

```powershell
New-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

För att hämta sessionen använder du parametern **computername** för `Get-PSSession` med värdet Server01.

```powershell
Get-PSSession -ComputerName Server01
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

Om värdet för parametern **computername** för `Get-PSSession` är localhost, `Get-PSSession` hämtar PSSessions som slutar på och underhålls på den lokala datorn. Den får inte PSSessions på Server01-datorn, även om de startades på den lokala datorn.

```powershell
Get-PSSession -ComputerName localhost
```

Använd cmdleten utan parametrar för att hämta sessioner som har skapats i den aktuella sessionen `Get-PSSession` . I det här exemplet `Get-PSSession` hämtar PSSession som skapades i den aktuella sessionen och ansluter till Server01-datorn.

```powershell
Get-PSSession
```

```Output
Id Name      ComputerName  State    ConfigurationName     Availability
-- ----      ------------  -----    -----------------     ------------
 2 Session2  Server01      Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-disconnect-sessions"></a>Koppla från sessioner

Använd cmdleten om du vill koppla från en PSSession `Disconnect-PSSession` . Om du vill identifiera PSSession använder du parametern **session** eller pipeline a PSSession från `New-PSSession` `Get-PSSession` cmdletarna eller `Disconnect-PSSession` .

Följande kommando kopplar från PSSession till Server01-datorn.
Observera att värdet för egenskapen **State** är **frånkopplat** och att **tillgängligheten** är **ingen**.

```powershell
Get-PSSession -ComputerName Server01 | Disconnect-PSSession
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 2 Session2  Server01      Disconnected  Microsoft.PowerShell          None
```

Använd parametern **InDisconnectedSession** för cmdleten om du vill skapa en frånkopplad session `Invoke-Command` . Den skapar en session, startar kommandot och kopplar från omedelbart, innan kommandot kan returnera utdata.

Följande kommando kör ett `Get-WinEvent` kommando i en frånkopplad session på den fjärranslutna Server02-datorn.

```powershell
Invoke-Command -ComputerName Server02 -InDisconnectedSession -ScriptBlock {
   Get-WinEvent -LogName "*PowerShell*" }
```

```Output
Id Name      ComputerName  State         ConfigurationName     Availability
-- ----      ------------  -----         -----------------     ------------
 4 Session3  Server02      Disconnected  Microsoft.PowerShell          None
```

## <a name="how-to-connect-to-disconnected-sessions"></a>Så här ansluter du till frånkopplade sessioner

Du kan ansluta till alla tillgängliga frånkopplade PSSession från sessionen där du skapade PSSession eller från andra sessioner på den lokala datorn eller på andra datorer.

Du kan skapa en PSSession, köra kommandon i PSSession, koppla från PSSession, stänga PowerShell och stänga av datorn. Timmar senare kan du öppna en annan dator, Hämta PSSession, ansluta till den och hämta resultatet av de kommandon som kördes i PSSession när den kopplades från. Sedan kan du köra fler kommandon i sessionen.

Använd cmdleten för att ansluta en frånkopplad PSSession `Connect-PSSession` . Använd parametrarna **computername** eller **ConnectionUri** för att identifiera PSSession eller pipeline a PSSession från `Get-PSSession` till `Connect-PSSession` .

Följande kommando hämtar sessionerna på den Server02 datorn. Utdata innehåller två frånkopplade sessioner, som båda är tillgängliga.

```powershell
Get-PSSession -ComputerName Server02
```

```Output
Id Name      ComputerName   State         ConfigurationName     Availability
-- ----      ------------   -----         -----------------     ------------
 2 Session2  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
 4 Session3  juneb-srv8320  Disconnected  Microsoft.PowerShell          None
```

Följande kommando ansluter till Session2. PSSession är nu öppen och tillgänglig.

```powershell
Connect-PSSession -ComputerName Server02 -Name Session2
```

```Output
Id Name      ComputerName    State    ConfigurationName     Availability
-- ----      ------------    -----    -----------------     ------------
 2 Session2  juneb-srv8320   Opened   Microsoft.PowerShell     Available
```

## <a name="how-to-get-the-results"></a>Så här hämtar du resultatet

Använd cmdleten för att hämta resultatet av kommandon som kördes i en frånkopplad PSSession `Receive-PSSession` .

Du kan använda `Receive-PSSession` i stället för att använda `Connect-PSSession` cmdleten. Om sessionen redan är ansluten igen `Receive-PSSession` hämtar resultatet från kommandon som kördes när sessionen kopplades från. Om PSSession fortfarande är frånkopplad `Receive-PSSession` ansluter du till den och hämtar sedan resultatet från kommandon som kördes medan den kopplades från.

`Receive-PSSession` kan returnera resultatet i ett jobb (asynkront) eller till värd programmet (synkront). Använd **mål** parametern för att välja **jobb** eller **värd**. Standardvärdet är **Host**. Men om kommandot som tas emot startades i den aktuella sessionen som ett **jobb** , returneras det som ett **jobb** som standard.

Följande kommando använder `Receive-PSSession` cmdleten för att ansluta till PSSession på Server02-datorn och hämta resultatet från `Get-WinEvent` kommandot som kördes i Session3-sessionen. Kommandot använder **mål** parametern för att hämta resultatet i ett **jobb**.

```powershell
Receive-PSSession -ComputerName Server02 -Name Session3 -OutTarget Job
```

```Output
Id   Name   PSJobTypeName   State         HasMoreData     Location
--   ----   -------------   -----         -----------     --------
 3   Job3   RemoteJob       Running       True            Server02
```

Använd cmdleten för att hämta jobbets resultat `Receive-Job` .

```powershell
Get-Job | Receive-Job -Keep
```

```Output
ProviderName: PowerShell

TimeCreated             Id LevelDisplayName Message     PSComputerName
-----------             -- ---------------- -------     --------------
5/14/2012 7:26:04 PM   400 Information      Engine stat Server02
5/14/2012 7:26:03 PM   600 Information      Provider "W Server02
5/14/2012 7:26:03 PM   600 Information      Provider "C Server02
5/14/2012 7:26:03 PM   600 Information      Provider "V Server02
```

## <a name="state-and-availability-properties"></a>Egenskaper för tillstånd och tillgänglighet

Egenskaperna för **tillstånd** och **tillgänglighet** för en frånkopplad PSSession anger om sessionen är tillgänglig för att återansluta till den.

När en PSSession är ansluten till den aktuella sessionen **öppnas** dess tillstånd och dess tillgänglighet är **tillgänglig**. När du kopplar från PSSession är PSSession-läget **frånkopplat** och dess tillgänglighet är **ingen**.

Värdet för egenskapen **State** är i förhållande till den aktuella sessionen. Värdet **frånkopplat** innebär att PSSession inte är ansluten till den aktuella sessionen. Men det betyder inte att PSSession är frånkopplad från alla sessioner. Den kan vara ansluten till en annan session.

Använd egenskapen **Availability** för att avgöra om du kan ansluta eller återansluta till PSSession. Värdet **none** anger att du kan ansluta till sessionen. Värdet **upptagen** anger att du inte kan ansluta till PSSession eftersom det är anslutet till en annan session.

Följande exempel körs i två PowerShell-sessioner på samma dator.
Observera de ändrade värdena för egenskaperna **State** och **Availability** i varje session när PSSession är frånkopplad och Återansluten.

```powershell
# Session 1
New-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30 -Name Test | Disconnect-PSSession
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          None
```

```powershell
# Session 2
Connect-PSSession -ComputerName Server30 -Name Test
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
3 Test    Server30        Opened        Microsoft.PowerShell     Available
```

```powershell
# Session 1
Get-PSSession -ComputerName Server30
```

```Output
Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1 Test    Server30        Disconnected  Microsoft.PowerShell          Busy
```

```Output
# Idle Timeout
```

Frånkopplade sessioner underhålls på fjärrdatorn tills du tar bort dem, till exempel med hjälp av `Remove-PSSession` cmdleten eller tids gränsen. Egenskapen **idleTimeout** för en PSSession bestämmer hur länge en frånkopplad session upprätthålls innan den tas bort.

PSSessions är inaktiva när **pulsslags tråden** inte får något svar.
Om du kopplar från en session blir den inaktiv och startar **idleTimeout** , även om kommandon fortfarande körs i den frånkopplade sessionen. I PowerShell anses frånkopplade sessioner vara aktiva, men inaktiva.

När du skapar och kopplar från sessioner kontrollerar du att tids gränsen för inaktivitet i PSSession är tillräckligt lång för att underhålla sessionen för dina behov, men inte så länge den förbrukar onödiga resurser på fjärrdatorn.

**IdleTimeoutMs** -egenskapen för sessionens konfiguration bestämmer tids gränsen för inaktivitet för sessioner som använder sessionen. Du kan åsidosätta standardvärdet, men det värde som du använder får inte överskrida **MaxIdleTimeoutMs** -egenskapen för sessionens konfiguration.

Använd följande kommando format för att hitta värdet för **IdleTimeoutMs** -och **MaxIdleTimeoutMs** -värden för en konfiguration av sessionen.

```powershell
Get-PSSessionConfiguration |
  Format-Table Name, IdleTimeoutMs, MaxIdleTimeoutMs
```

Du kan åsidosätta standardvärdet i konfigurationen av sessionen och ange tids gränsen för inaktivitet för en PSSession när du skapar en PSSession och när du kopplar från.

Om du är medlem i gruppen Administratörer på fjärrdatorn kan du skapa och ändra egenskaperna **IdleTimeoutMs** och **MaxIdleTimeoutMs** för sessionsinställningar.

## <a name="idle-timeout-values"></a>Timeout-värden för inaktivitet

Timeout-värdet för inaktivitet för sessionsinställningar och sessionsinformation är i millisekunder. Timeout-värdet för inaktivitet i sessioner och konfigurations alternativ för sessioner är i sekunder.

Du kan ange tids gränsen för inaktivitet för en PSSession när du skapar PSSession ( `New-PSSession` , `Invoke-Command` ) och när du kopplar från den ( `Disconnect-PSSession` ). Du kan dock inte ändra **idleTimeout** -värdet när du ansluter till PSSession ( `Connect-PSSession` ) eller hämta resultat ( `Receive-PSSession` ).

`Connect-PSSession` `Receive-PSSession` Cmdletarna och har en **SessionOption** -parameter som tar ett **SessionOption** -objekt, till exempel en som returneras av `New-PSSessionOption` cmdleten. **IdleTimeout** -värdet i **SessionOption** -objektet och **idleTimeout** -värdet i `$PSSessionOption` variabeln Preference ändrar inte värdet för **idleTimeout** för PSSession i ett- `Connect-PSSession` eller- `Receive-PSSession` kommando.

Skapa en inställnings variabel om du vill skapa en PSSession med ett visst tids gräns värde för inaktivitet `$PSSessionOption` . Ange värdet för **idleTimeout** -egenskapen till önskat värde (i millisekunder).

När du skapar PSSessions prioriteras värdena i `$PSSessionOption` variabeln över värdena i konfigurationen för sessionen.

Följande kommando anger till exempel en timeout för inaktivitet på 48 timmar:

```powershell
$PSSessionOption = New-PSSessionOption -IdleTimeoutMSec 172800000
```

Om du vill skapa en PSSession med ett visst tids gräns värde för inaktivitet, använder du parametern **IdleTimeoutMSec** för `New-PSSessionOption` cmdleten. Använd sedan alternativet session i värdet för parametern **SessionOption** i `New-PSSession` `Invoke-Command` cmdletarna eller.

Värdena som anges när du skapar sessionen prioriteras framför de värden som anges i `$PSSessionOption` variabeln Preference och konfigurationen för sessionen.

Ett exempel:

```powershell
$o = New-PSSessionOption -IdleTimeoutMSec 172800000
New-PSSession -SessionOption $o
```

Om du vill ändra tids gränsen för inaktivitet för en PSSession vid från koppling använder du parametern **IdleTimeoutSec** för `Disconnect-PSSession` cmdleten.

Ett exempel:

```powershell
Disconnect-PSSession -IdleTimeoutSec 172800
```

Om du vill skapa en sessionshantering med en viss tids gräns för inaktivitet och maximal tids gräns för inaktivitet använder du cmdleten **IdleTimeoutSec** och **MaxIdleTimeoutSec** `New-PSTransportOption` . Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Register-PSSessionConfiguration` .

Ett exempel:

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

Om du vill ändra standard tids gränsen för inaktivitet och maximal tids gräns för inaktivitet för en session, använder du cmdleten **IdleTimeoutSec** och **MaxIdleTimeoutSec** `New-PSTransportOption` . Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Set-PSSessionConfiguration` .

Ett exempel:

```powershell
$o = New-PSTransportOption -IdleTimeoutSec 172800 -MaxIdleTimeoutSec 259200
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="output-buffering-mode"></a>Läge för buffring av utdata

Utmatnings buffertens läge för en PSSession bestämmer hur kommandoutdata hanteras när utdatabufferten för PSSession är full.

I en frånkopplad session avgör utmatnings buffertens läge om kommandot fortsätter att köras medan sessionen kopplas från.

Giltiga värden enligt följande:

- **Blockera**. När utdatabufferten är full pausas körningen tills bufferten är klar. Standardvärdet.
- **Släpp**. När utdatabufferten är full fortsätter körningen. När nya utdata skapas, ignoreras det äldsta resultatet.

**Blockera** data bevarar data, men kan avbryta kommandot. Ett **Drop** -värde gör att kommandot kan slutföras, men data kan gå förlorade. När du använder **Drop** -värdet dirigerar du om kommandots utdata till en fil på disk. Det här värdet rekommenderas för frånkopplade sessioner.

**OutputBufferingMode** -egenskapen för sessionens konfiguration bestämmer standardutdata för buffring av sessioner som använder sessionen.

Om du vill hitta en konfigurations värde för en **OutputBufferingMode** kan du använda något av följande kommando format:

```powershell
(Get-PSSessionConfiguration <ConfigurationName>).OutputBufferingMode
```

```powershell
Get-PSSessionConfiguration | Format-Table Name, OutputBufferingMode
```

Du kan åsidosätta standardvärdet i konfigurationen av sessionen och ange ett PSSession när du skapar en PSSession när du kopplar från, och när du återansluter.

Om du är medlem i gruppen Administratörer på fjärrdatorn kan du skapa och ändra buffrings läget för utdata i sessioner.

Om du vill skapa en PSSession med ett utmatnings **Buffer-läge** , skapar du en `$PSSessionOption` Preference-variabel där värdet för egenskapen **OutputBufferingMode** är **Drop**.

När du skapar PSSessions prioriteras värdena i `$PSSessionOption` variabeln över värdena i konfigurationen för sessionen.

Ett exempel:

```powershell
$PSSessionOption = New-PSSessionOption -OutputBufferingMode Drop
```

Om du vill skapa en PSSession med ett utmatnings **Buffer-läge** , använder du parametern **OutputBufferingMode** för cmdlet: en för `New-PSSessionOption` att skapa ett session-alternativ med värdet **Drop**. Använd sedan alternativet session i värdet för parametern **SessionOption** i `New-PSSession` `Invoke-Command` cmdletarna eller.

Värdena som anges när du skapar sessionen prioriteras framför de värden som anges i `$PSSessionOption` variabeln Preference och konfigurationen för sessionen.

Ett exempel:

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
New-PSSession -SessionOption $o
```

Om du vill ändra utdata buffer-läget för en PSSession vid från koppling använder du parametern **OutputBufferingMode** för `Disconnect-PSSession` cmdleten.

Ett exempel:

```powershell
Disconnect-PSSession -OutputBufferingMode Drop
```

Om du vill ändra utdata buffer-läget för en PSSession vid åter anslutning använder du parametern **OutputBufferingMode** för cmdlet: en `New-PSSessionOption` för att skapa ett session-alternativ med värdet **Drop**. Använd sedan alternativet session i värdet för parametern **SessionOption** i `Connect-PSSession` eller `Receive-PSSession` .

Ett exempel:

```powershell
$o = New-PSSessionOption -OutputBufferingMode Drop
Connect-PSSession -ComputerName Server01 -Name Test -SessionOption $o
```

Om du vill skapa en konfiguration av sessionen med ett utmatnings sätt **som är** förvalt, använder du parametern **OutputBufferingMode** för `New-PSTransportOption` cmdleten för att skapa ett transport alternativ objekt med värdet **Drop**. Använd sedan alternativet transport i värdet för parametern **TransportOption** i `Register-PSSessionConfiguration` .

Ett exempel:

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Register-PSSessionConfiguration -Name Test -TransportOption $o
```

Om du vill ändra standard läget för buffring av utdata för en session, använder du parametern **OutputBufferingMode** för `New-PSTransportOption` cmdlet: en för att skapa ett transport alternativ med värdet **Drop**. Använd sedan alternativet transport i värdet för parametern **SessionOption** i `Set-PSSessionConfiguration` .

Ett exempel:

```powershell
$o = New-PSTransportOption -OutputBufferingMode Drop
Set-PSSessionConfiguration -Name Test -TransportOption $o
```

## <a name="disconnecting-loopback-sessions"></a>Koppla från loopback-sessioner

Loopback-sessioner, eller lokala sessioner, är PSSessions som kommer från och slutar på samma dator. Precis som andra PSSessions underhålls aktiva loopback-sessioner på datorn i Fjärrslutpunkten av anslutningen (den lokala datorn) så att du kan koppla från och återansluta till loopback-sessioner.

Som standard skapas loopback-sessioner med en nätverks säkerhets-token som inte tillåter att kommandon körs i sessionen för att få åtkomst till andra datorer. Du kan återansluta till loopback-sessioner som har en nätverks säkerhets-token från valfri session på den lokala datorn eller en fjärrdator.

Men om du använder parametern **EnableNetworkAccess** i `New-PSSession` `Enter-PSSession` cmdleten, eller, `Invoke-Command` skapas loopback-sessionen med en interaktiv säkerhetstoken. Den interaktiva token gör det möjligt att köra kommandon som körs i loopback-sessionen för att hämta data från andra datorer.

Du kan koppla från loopback-sessioner med interaktiva token och sedan återansluta till dem från samma session eller en annan session på samma dator.
Men för att förhindra obehörig åtkomst kan du återansluta till loopback-sessioner med interaktiva tokens enbart från den dator där de skapades.

## <a name="waiting-for-jobs-in-disconnected-sessions"></a>Väntar på jobb i frånkopplade sessioner

`Wait-Job`Cmdleten väntar tills ett jobb har slutförts och återgår sedan till kommando tolken eller nästa kommando. Som standard `Wait-Job` returneras om sessionen där ett jobb körs är frånkopplad. Om du vill dirigera `Wait-Job` cmdleten till att vänta tills sessionen har återanslutits använder du parametern **Force** i **öppnings** läge. Mer information finns i [wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job).

## <a name="robust-sessions-and-unintentional-disconnection"></a>Robusta sessioner och oavsiktlig från koppling

En PSSession kan oavsiktligt kopplas från på grund av ett dator haveri eller nätverks avbrott. PowerShell försöker återställa PSSession, men dess framgång beror på orsakens allvarlighets grad och varaktighet.

Statusen för en oavsiktligt frånkopplad PSSession kan vara **bruten** eller **stängd** , men den kan också vara **frånkopplad**. Om värdet för **State** är **frånkopplat** kan du använda samma metoder för att hantera PSSession på samma sätt som om sessionen kopplades från avsiktligt. Du kan till exempel använda `Connect-PSSession` cmdleten för att återansluta till sessionen och `Receive-PSSession` cmdleten för att få resultat från kommandon som kördes medan sessionen kopplades från.

Om du stänger (avslutar) sessionen där en PSSession skapades medan kommandon körs i PSSession, underhåller PowerShell PSSession i **frånkopplat** läge på fjärrdatorn. Om du stänger (avslutar) sessionen där en PSSession skapades men inga kommandon körs i PSSession, försöker inte PowerShell underhålla PSSession.

## <a name="see-also"></a>Se även

[about_Jobs](about_Jobs.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[about_Session_Configurations](about_Session_Configurations.md)

[Anslut – PSSession](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[Koppla från-PSSession](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[Ta emot – PSSession](xref:Microsoft.PowerShell.Core.Receive-PSSession)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

