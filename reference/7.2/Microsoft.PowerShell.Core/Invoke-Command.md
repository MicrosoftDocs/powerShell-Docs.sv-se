---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Command
ms.openlocfilehash: d8f0a8a56792a39371a307166788f047fec99a9a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709588"
---
# Invoke-Command

## SAMMANFATTNING
Kör kommandon på lokala datorer och fjärrdatorer.

## SYNTAX

### InProcess (standard)

```
Invoke-Command [-ScriptBlock] <ScriptBlock> [-NoNewScope] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathRunspace

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Session

```
Invoke-Command [[-Session] <PSSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-FilePath] <String> [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### ComputerName

```
Invoke-Command [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Port <Int32>] [-UseSSL]
 [-ConfigurationName <String>] [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-AsJob]
 [-InDisconnectedSession] [-SessionName <String[]>] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-EnableNetworkAccess] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### FilePathUri

```
Invoke-Command [-Credential <PSCredential>] [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [[-ConnectionUri] <Uri[]>] [-AsJob] [-InDisconnectedSession] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-EnableNetworkAccess] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### VMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### VMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-ScriptBlock] <ScriptBlock> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### FilePathVMId

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [-VMId] <Guid[]> [<CommonParameters>]
```

### FilePathVMName

```
Invoke-Command -Credential <PSCredential> [-ConfigurationName <String>] [-ThrottleLimit <Int32>]
 [-AsJob] [-HideComputerName] [-FilePath] <String> [-RemoteDebug] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] -VMName <String[]> [<CommonParameters>]
```

### SSHHost

```
Invoke-Command [-Port <Int32>] [-AsJob] [-HideComputerName] [-JobName <String>]
 [-ScriptBlock] <ScriptBlock> -HostName <String[]> [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [-Subsystem <String>] [<CommonParameters>]
```

### Hålla

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-ScriptBlock] <ScriptBlock> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### FilePathContainerId

```
Invoke-Command [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-AsJob] [-HideComputerName]
 [-JobName <String>] [-FilePath] <String> [-RunAsAdministrator] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] -ContainerId <String[]> [<CommonParameters>]
```

### SSHHostHashParam

```
Invoke-Command [-AsJob] [-HideComputerName] [-JobName <String>] [-ScriptBlock] <ScriptBlock>
 -SSHConnection <Hashtable[]> [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>]
 [<CommonParameters>]
```

### FilePathSSHHost

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -HostName <String[]>
 [-UserName <String>] [-KeyFilePath <String>] [-SSHTransport] [-RemoteDebug]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### FilePathSSHHostHash

```
Invoke-Command [-AsJob] [-HideComputerName] -FilePath <String> -SSHConnection <Hashtable[]>
 [-RemoteDebug] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## BESKRIVNING

`Invoke-Command`Cmdleten kör kommandon på en lokal eller fjärran sluten dator och returnerar alla utdata från kommandona, inklusive fel. Med ett enda `Invoke-Command` kommando kan du köra kommandon på flera datorer.

Om du vill köra ett enda kommando på en fjärrdator använder du parametern **computername** . Om du vill köra en serie relaterade kommandon som delar data använder du `New-PSSession` cmdleten för att skapa en **PSSession** (en permanent anslutning) på fjärrdatorn och använder sedan parametern **session** för `Invoke-Command` att köra kommandot i **PSSession**. Om du vill köra ett kommando i en frånkopplad session använder du parametern **InDisconnectedSession** . Om du vill köra ett kommando i ett bakgrunds jobb använder du parametern **AsJob** .

Du kan också använda `Invoke-Command` på en lokal dator till ett-skript block som ett kommando. PowerShell kör skript blocket direkt i en underordnad omfattning för det aktuella omfånget.

Innan `Invoke-Command` du använder för att köra kommandon på en fjärrdator läser du [about_Remote](./About/about_Remote.md).

Från och med PowerShell 6,0 kan du använda SSH (Secure Shell) för att upprätta en anslutning till och anropa kommandon på fjärrdatorer. SSH måste vara installerat på den lokala datorn och fjärrdatorn måste konfigureras med en PowerShell SSH-slutpunkt. Fördelen med en SSH-baserad PowerShell-fjärrsession är att den fungerar på flera plattformar (Windows, Linux, macOS). För SSH-baserad session använder du parametrarna **hostname** eller **SSHConnection** för att ange fjärrdatorn och relevant anslutnings information. Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

I vissa kod exempel används ihopbuntning för att minska linje längden. Mer information finns i [about_Splatting](./About/about_Splatting.md).

## EXEMPEL

### Exempel 1: kör ett skript på en server

I det här exemplet körs `Test.ps1` skriptet på Server01-datorn.

```powershell
Invoke-Command -FilePath c:\scripts\test.ps1 -ComputerName Server01
```

Parametern **sökväg** anger ett skript som finns på den lokala datorn. Skriptet körs på fjärrdatorn och resultatet returneras till den lokala datorn.

### Exempel 2: köra ett kommando på en fjärrserver

I det här exemplet körs ett `Get-Culture` kommando på Server01-fjärrdatorn.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\User01 -ScriptBlock { Get-Culture }
```

Parametern **computername** anger namnet på fjärrdatorn. Parametern **Credential** används för att köra kommandot i säkerhets kontexten för Domain01\User01, en användare som har behörighet att köra kommandon. Parametern **script block** anger kommandot som ska köras på fjärrdatorn.

Som svar begär PowerShell lösen ordet och en autentiseringsmetod för user01-kontot.
Den kör sedan kommandot på Server01-datorn och returnerar resultatet.

### Exempel 3: köra ett kommando i en permanent anslutning

I det här exemplet körs samma `Get-Culture` kommando i en session med en beständig anslutning på fjärrdatorn med namnet Server02.

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

`New-PSSession`Cmdleten skapar en session på Server02-fjärrdatorn och sparar den i `$s` variabeln. Normalt skapar du bara en session när du kör en serie kommandon på fjärrdatorn.

`Invoke-Command`Cmdleten kör `Get-Culture` kommandot på Server02. Parametern **session** anger sessionen som sparats i `$s` variabeln.

Som svar kör PowerShell kommandot i sessionen på den Server02 datorn.

### Exempel 4: Använd en session för att köra en serie kommandon som delar data

I det här exemplet jämförs effekterna av att använda **computername** och **sessionscookies** för `Invoke-Command` . Det visar hur du använder en session för att köra en serie kommandon som delar samma data.

```powershell
Invoke-Command -ComputerName Server02 -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -ComputerName Server02 -ScriptBlock {$p.VirtualMemorySize}
$s = New-PSSession -ComputerName Server02
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process PowerShell}
Invoke-Command -Session $s -ScriptBlock {$p.VirtualMemorySize}
```

```Output
17930240
```

De två första kommandona använder parametern **computername** för `Invoke-Command` att köra kommandon på Server02-fjärrdatorn. Det första kommandot använder `Get-Process` cmdleten för att hämta PowerShell-processen på fjärrdatorn och spara den i `$p` variabeln. Det andra kommandot hämtar värdet för **VirtualMemorySize** -egenskapen för PowerShell-processen.

När du använder parametern **computername** skapar PowerShell en ny session för att köra kommandot.
Sessionen stängs när kommandot har slutförts. `$p`Variabeln skapades i en anslutning, men den finns inte i anslutningen som skapats för det andra kommandot.

Problemet löses genom att skapa en beständig session på fjärrdatorn och köra båda kommandona i samma session.

`New-PSSession`Cmdleten skapar en beständig session på datorn Server02 och sparar sessionen i `$s` variabeln. De `Invoke-Command` rader som följer använder parametern **session** för att köra båda kommandona i samma session. Eftersom båda kommandona körs i samma session `$p` är värdet fortfarande aktivt.

### Exempel 5: Ange ett kommando som lagras i en lokal variabel

Det här exemplet visar hur du skapar ett kommando som lagras som ett skript block i en lokal variabel.
När skript blocket sparas i en lokal variabel kan du ange variabeln som värde för parametern **script block** .

```powershell
$command = { Get-WinEvent -LogName PowerShellCore/Operational |
  Where-Object {$_.Message -like "*certificate*"} }
Invoke-Command -ComputerName S1, S2 -ScriptBlock $command
```

`$command`Variabeln lagrar `Get-WinEvent` kommandot som är formaterat som ett skript block. `Invoke-Command`Kör kommandot som lagras på `$command` på datorerna S1 och S2.

### Exempel 6: kör ett enda kommando på flera datorer

Det här exemplet visar hur du kan använda `Invoke-Command` för att köra ett enda kommando på flera datorer.

```powershell
$parameters = @{
  ComputerName = "Server01", "Server02", "TST-0143", "localhost"
  ConfigurationName = 'MySession.PowerShell'
  ScriptBlock = { Get-WinEvent -LogName PowerShellCore/Operational }
}
Invoke-Command @parameters
```

Parametern **computername** anger en kommaavgränsad lista med dator namn. Listan med datorer innehåller värdet localhost, som representerar den lokala datorn. Parametern **ConfigurationName** anger en alternativ konfiguration av sessionen. Parametern **script block** körs `Get-WinEvent` för att hämta de PowerShellCore/operativa händelse loggarna från varje dator.

### Exempel 7: Hämta versionen av värd programmet på flera datorer

I det här exemplet hämtas versionen av PowerShell-värd programmet som körs på 200-fjärrdatorer.

```powershell
$version = Invoke-Command -ComputerName (Get-Content Machines.txt) -ScriptBlock {(Get-Host).Version}
```

Eftersom endast ett kommando körs behöver du inte skapa beständiga anslutningar till var och en av datorerna. I stället använder kommandot **computername** -parametern för att ange datorerna. För att ange datorer använder den `Get-Content` cmdleten för att hämta innehållet i Machine.txt-filen, en fil med dator namn.

`Invoke-Command`Cmdleten kör ett `Get-Host` kommando på fjärrdatorerna. Den använder punkt notation för att hämta **versions** egenskapen för PowerShell-värden.

Kommandona körs en i taget. När kommandona har slutförts sparas utdata från alla datorer i `$version` variabeln. Utdata innehåller namnet på den dator från vilken data kommer.

### Exempel 8: köra ett bakgrunds jobb på flera fjärrdatorer

I det här exemplet körs ett kommando på två fjärrdatorer. `Invoke-Command`Kommandot använder parametern **AsJob** så att kommandot körs som ett bakgrunds jobb. Kommandona körs på fjärrdatorerna, men jobbet finns på den lokala datorn. Resultaten överförs till den lokala datorn.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
Invoke-Command -Session $s -ScriptBlock {Get-EventLog system} -AsJob
```

```Output
Id   Name    State      HasMoreData   Location           Command
---  ----    -----      -----         -----------        ---------------
1    Job1    Running    True          Server01,Server02  Get-EventLog system
```

```powershell
$j = Get-Job
$j | Format-List -Property *
```

```Output
HasMoreData   : True
StatusMessage :
Location      : Server01,Server02
Command       : Get-EventLog system
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : e124bb59-8cb2-498b-a0d2-2e07d4e030ca
Id            : 1
Name          : Job1
ChildJobs     : {Job2, Job3}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
$results = $j | Receive-Job
```

`New-PSSession`Cmdleten skapar sessioner på fjärrdatorerna Server01 och Server02. `Invoke-Command`Cmdleten kör ett bakgrunds jobb i varje session. Kommandot använder parametern **AsJob** för att köra kommandot som ett bakgrunds jobb. Det här kommandot returnerar ett jobb objekt som innehåller två underordnade jobb objekt, ett för varje jobb som körs på de två fjärrdatorerna.

`Get-Job`Kommandot sparar jobbobjektet i `$j` variabeln. `$j`Variabeln skickas sedan till `Format-List` cmdleten för att visa alla egenskaper för jobbobjektet i en lista. Det sista kommandot hämtar resultatet av jobben. Det rör jobbobjektet i- `$j` `Receive-Job` cmdleten och lagrar resultatet i `$results` variabeln.

### Exempel 9: inkludera lokala variabler i en kommando körning på en fjärran sluten dator

Det här exemplet visar hur du tar med värdena för lokala variabler i en kommando körning på en fjärrdator. Kommandot använder `Using` omfångs modifieraren för att identifiera en lokal variabel i ett fjärran slutet kommando. Som standard antas alla variabler definieras i fjärrsessionen. `Using`Omfångs modifieraren introducerades i PowerShell 3,0. Mer information om `Using` omfångs modifieraren finns i [about_Remote_Variables](./About/about_Remote_Variables.md) och [about_Scopes](./about/about_scopes.md).

```powershell
$Log = "PowerShellCore/Operational"
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-WinEvent -LogName $Using:Log -MaxEvents 10}
```

`$Log`Variabeln lagrar namnet på händelse loggen, PowerShellCore/Operational. `Invoke-Command`Cmdleten körs `Get-WinEvent` på Server01 för att hämta de tio senaste händelserna från händelse loggen. Värdet för parametern **LogName** är den `$Log` variabel som föregås av `Using` omfångs modifieraren för att ange att den skapades i den lokala sessionen, inte i fjärrsessionen.

### Exempel 10: Dölj dator namnet

I det här exemplet visas effekterna av att använda **HideComputerName** -parametern i `Invoke-Command` .
**HideComputerName** ändrar inte objektet som denna cmdlet returnerar. Den ändrar bara visningen. Du kan fortfarande använda **format** -cmdletar för att visa egenskapen **PsComputerName** för något av de påverkade objekten.

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell}
```

```Output
PSComputerName    Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
--------------    -------  ------    -----      ----- -----   ------     --   -----------
S1                575      15        45100      40988   200     4.68     1392 PowerShell
S2                777      14        35100      30988   150     3.68     67   PowerShell
```

```powershell
Invoke-Command -ComputerName S1, S2 -ScriptBlock {Get-Process PowerShell} -HideComputerName
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
575      15        45100      40988   200     4.68     1392 PowerShell
777      14        35100      30988   150     3.68     67   PowerShell
```

De två första kommandona använder `Invoke-Command` för att köra ett `Get-Process` kommando för PowerShell-processen. Utdata från det första kommandot innehåller egenskapen **PsComputerName** som innehåller namnet på den dator där kommandot kördes. Utdata från det andra kommandot, som använder **HideComputerName**, inkluderar inte kolumnen **PsComputerName** .

### Exempel 11: Använd nyckelordet param i ett skript block

`Param`Nyckelordet och parametern **argument List** används för att skicka variabel värden till namngivna parametrar i ett-skript block. I det här exemplet visas fil namn som börjar med bokstaven `a` och har `.pdf` fil namns tillägget.

Mer information om `Param` nyckelordet finns [about_Language_Keywords](./about/about_language_keywords.md#param).

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Param ($param1,$param2) Get-ChildItem -Name $param1 -Include $param2 }
    ArgumentList = "a*", "*.pdf"
}
Invoke-Command @parameters
```

```Output
aa.pdf
ab.pdf
ac.pdf
az.pdf
```

`Invoke-Command` använder parametern **script block** som definierar två variabler `$param1` och `$param2` . `Get-ChildItem` använder namngivna parametrar, **namn** och **Inkludera** med variabel namn. **Argument List** skickar värdena till variablerna.

### Exempel 12: Använd $args automatiska variabeln i ett skript block

Den `$args` automatiska variabeln och parametern **argument List** används för att skicka mat ris värden till parameter positioner i ett-skript block. I det här exemplet visas en servers katalog innehåll för `.txt` filer. Parametern `Get-ChildItem` **Path** är position 0 och **filter** parametern är position
1.

Mer information om `$args` variabeln finns i [about_Automatic_Variables](./about/about_automatic_variables.md#args)

```powershell
$parameters = @{
    ComputerName = "Server01"
    ScriptBlock = { Get-ChildItem $args[0] $args[1] }
    ArgumentList = "C:\Test", "*.txt*"
}
Invoke-Command @parameters
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           6/12/2019    15:15            128 alog.txt
-a---           7/27/2019    15:16            256 blog.txt
-a---           9/28/2019    17:10             64 zlog.txt
```

`Invoke-Command` använder en **script block** -parameter och `Get-ChildItem` anger `$args[0]` `$args[1]` mat ris värden och. **Argument List** skickar `$args` mat ris värdena till `Get-ChildItem` parameter positionerna för **sökväg** och **filter**.

### Exempel 13: kör ett skript på alla datorer som anges i en textfil

I det här exemplet används `Invoke-Command` cmdleten för att köra `Sample.ps1` skriptet på alla datorer som anges i `Servers.txt` filen. Kommandot använder parametern **sökväg** för att ange skript filen. Med det här kommandot kan du köra skriptet på fjärrdatorer, även om skript filen inte är tillgänglig för fjärrdatorer.

```powershell
Invoke-Command -ComputerName (Get-Content Servers.txt) -FilePath C:\Scripts\Sample.ps1 -ArgumentList Process, Service
```

När du skickar kommandot kopieras innehållet i `Sample.ps1` filen till ett-skript block och skript blocket körs på varje fjärrdator. Den här proceduren motsvarar att använda parametern **script block** för att skicka innehållet i skriptet.

### Exempel 14: köra ett kommando på en fjärrdator med en URI

Det här exemplet visar hur du kör ett kommando på en fjärrdator som identifieras av en Uniform Resource Identifier (URI). Det här exemplet kör ett `Set-Mailbox` kommando på en fjärran sluten Exchange-Server.

```powershell
$LiveCred = Get-Credential
$parameters = @{
  ConfigurationName = 'Microsoft.Exchange'
  ConnectionUri = 'https://ps.exchangelabs.com/PowerShell'
  Credential = $LiveCred
  Authentication = 'Basic'
  ScriptBlock = {Set-Mailbox Dan -DisplayName "Dan Park"}
}
Invoke-Command @parameters
```

Den första raden använder `Get-Credential` cmdleten för att lagra Windows Live ID-autentiseringsuppgifter i `$LiveCred` variabeln. PowerShell efterfrågar användaren att ange Windows Live ID-autentiseringsuppgifter.

`$parameters`Variabeln är en hash-tabell som innehåller de parametrar som ska skickas till `Invoke-Command` cmdleten. `Invoke-Command`Cmdleten kör ett `Set-Mailbox` kommando med hjälp av konfigurationen för **Microsoft. Exchange** -sessionen. Parametern **ConnectionURI** anger URL: en för Exchange Server-slutpunkten. Parametern **Credential** anger de autentiseringsuppgifter som lagras i `$LiveCred` variabeln. Parametern **AuthenticationMechanism** anger användningen av grundläggande autentisering. Parametern **script block** anger ett skript block som innehåller kommandot.

### Exempel 15: Använd ett session-alternativ

Det här exemplet visar hur du skapar och använder en **SessionOption** -parameter.

```powershell
$so = New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck
Invoke-Command -ComputerName server01 -UseSSL -ScriptBlock { Get-HotFix } -SessionOption $so -Credential server01\user01
```

`New-PSSessionOption`Cmdleten skapar ett sessionsobjekt som gör att Fjärrslutpunkten inte verifierar certifikat utfärdaren, kanoniskt namn och återkallnings listor vid utvärdering av inkommande https-anslutningen. **SessionOption** -objektet sparas i `$so` variabeln.

> [!NOTE]
> Att inaktivera de här kontrollerna är användbart för fel sökning, men uppenbarligen inte säkert.

`Invoke-Command`Cmdlet: en kör ett `Get-HotFix` kommando via fjärr anslutning. **SessionOption** -parametern har fått `$so` variabeln.

### Exempel 16: hantera omdirigering av URI i ett fjärran slutet kommando

Det här exemplet visar hur du använder parametrarna **AllowRedirection** och **SessionOption** för att hantera omdirigering av URI i ett fjärrkommando.

```powershell
$max = New-PSSessionOption -MaximumRedirection 1
$parameters = @{
  ConnectionUri = "https://ps.exchangelabs.com/PowerShell"
  ScriptBlock = { Get-Mailbox dan }
  AllowRedirection = $true
  SessionOption = $max
}
Invoke-Command @parameters
```

`New-PSSessionOption`Cmdleten skapar ett **PSSessionOption** -objekt som sparas i `$max` variabeln. Kommandot använder parametern **MaximumRedirection** för att ange egenskapen **MaximumConnectionRedirectionCount** för **PSSessionOption** -objektet till 1.

`Invoke-Command`Cmdleten kör ett `Get-Mailbox` kommando på en fjärran sluten Microsoft Exchange Server. Parametern **AllowRedirection** ger uttrycklig behörighet att omdirigera anslutningen till en annan slut punkt. Parametern **SessionOption** använder det sessionsobjekt som lagras i `$max` variabeln.

Det innebär att om den fjärranslutna datorn som anges av **ConnectionURI** returnerar ett omdirigerings meddelande, omdirigerar PowerShell anslutningen, men om det nya målet returnerar ett annat omdirigerings meddelande, räknas värdet 1 för omdirigeringen och `Invoke-Command` returnerar ett icke-avslutande fel.

### Exempel 17: få åtkomst till en nätverks resurs i en fjärran sluten session

Det här exemplet visar hur du kommer åt en nätverks resurs från en fjärrsession. Tre datorer används för att demonstrera exemplet. Server01 är den lokala datorn, Server02 är den fjärranslutna datorn och Net03 innehåller nätverks resursen. Server01 ansluter till Server02 och Server02 gör sedan ett andra hopp till Net03 för att få åtkomst till nätverks resursen. Mer information om hur PowerShell-fjärrkommunikation stöder hopp mellan datorer finns i [göra det andra hoppet i PowerShell-fjärrkommunikation](/powershell/scripting/learn/remoting/ps-remoting-second-hop).

Den obligatoriska CredSSP-delegeringen (Security Support Provider) för autentiseringsuppgifter är aktive rad i klient inställningarna på den lokala datorn och i tjänst inställningarna på fjärrdatorn. Om du vill köra kommandona i det här exemplet måste du vara medlem i gruppen **Administratörer** på den lokala datorn och fjärrdatorn.

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer Server02
$s = New-PSSession Server02
Invoke-Command -Session $s -ScriptBlock {Enable-WSManCredSSP -Role Server -Force}
$parameters = @{
  Session = $s
  ScriptBlock = { Get-Item \\Net03\Scripts\LogFiles.ps1 }
  Authentication = "CredSSP"
  Credential = "Domain01\Admin01"
}
Invoke-Command @parameters
```

`Enable-WSManCredSSP`Cmdlet: en aktiverar CredSSP-delegering från den lokala Server01-datorn till Server02-fjärrdatorn. **Roll** parametern anger **klienten** för att konfigurera CredSSP-klient inställningen på den lokala datorn.

`New-PSSession` skapar ett **PSSession** -objekt för Server02 och lagrar objektet i `$s` variabeln.

`Invoke-Command`Cmdlet: en använder `$s` variabeln för att ansluta till fjärrdatorn, Server02. Parametern **script block** körs `Enable-WSManCredSSP` på fjärrdatorn. **Roll** parametern anger **servern** för att konfigurera CredSSP-Server inställningen på fjärrdatorn.

`$parameters`Variabeln innehåller de parameter värden som ska anslutas till nätverks resursen. `Invoke-Command`Cmdleten kör ett `Get-Item` kommando i sessionen i `$s` . Det här kommandot hämtar ett skript från `\\Net03\Scripts` nätverks resursen. Kommandot använder parametern **Authentication** med värdet **CredSSP** och parametern **Credential** med värdet **Domain01\Admin01**.

### Exempel 18: starta skript på många fjärrdatorer

I det här exemplet körs ett skript på fler än hundra datorer. För att minimera påverkan på den lokala datorn ansluter den till varje dator, startar skriptet och kopplar sedan från varje dator.
Skriptet fortsätter att köras i de frånkopplade sessionerna.

```powershell
$parameters = @{
  ComputerName = (Get-Content -Path C:\Test\Servers.txt)
  InDisconnectedSession = $true
  FilePath = "\\Scripts\Public\ConfigInventory.ps1"
  SessionOption = @{OutputBufferingMode="Drop";IdleTimeout=43200000}
}
Invoke-Command @parameters
```

Kommandot använder `Invoke-Command` för att köra skriptet. Värdet för parametern **computername** är ett `Get-Content` kommando som hämtar namnen på fjärrdatorerna från en textfil. Parametern **InDisconnectedSession** kopplar från sessionerna så snart den startar kommandot. Värdet för parametern **sökväg** är det skript som `Invoke-Command` körs på varje dator.

Värdet för **SessionOption** är en hash-tabell. **OutputBufferingMode** -värdet är inställt på **Drop** och **idleTimeout** -värdet är inställt på **43200000** millisekunder (12 timmar).

Använd cmdleten för att hämta resultatet av kommandon och skript som körs i frånkopplade sessioner `Receive-PSSession` .

### Exempel 19: köra ett kommando på en fjärrdator med SSH

Det här exemplet visar hur du kör ett kommando på en fjärrdator med hjälp av SSH (Secure Shell). Om SSH konfigureras på fjärrdatorn för att fråga efter lösen ord får du en fråga om lösen ord.
Annars måste du använda SSH-nyckelbaserad användarautentisering.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * }
```

### Exempel 20: kör ett kommando på en fjärrdator med SSH och ange en användar verifierings nyckel

Det här exemplet visar hur du kör ett kommando på en fjärrdator med SSH och anger en nyckel fil för användarautentisering. Du uppmanas inte att ange ett lösen ord om inte autentiseringen Miss lyckas och fjärrdatorn har kon figurer ATS för att tillåta grundläggande lösenordsautentisering.

```powershell
Invoke-Command -HostName UserA@LinuxServer01 -ScriptBlock { Get-MailBox * } -KeyFilePath /UserA/UserAKey_rsa
```

### Exempel 21: kör en skript fil på flera fjärranslutna datorer med SSH som ett jobb

Det här exemplet visar hur du kör en skript fil på flera fjärrdatorer med SSH och **SSHConnection** -parameter uppsättningen. Parametern **SSHConnection** tar en matris med hash-tabeller som innehåller anslutnings information för varje dator. Det här exemplet kräver att mål datorerna har SSH konfigurerat för att stödja nyckelbaserad användarautentisering.

```powershell
$sshConnections =
@{ HostName="WinServer1"; UserName="Domain\UserA"; KeyFilePath="C:\Users\UserA\id_rsa" },
@{ HostName="UserB@LinuxServer5"; KeyFilePath="/Users/UserB/id_rsa" }
$results = Invoke-Command -FilePath c:\Scripts\CollectEvents.ps1 -SSHConnection $sshConnections
```

## PARAMETRAR

### -AllowRedirection

Tillåter omdirigering av anslutningen till en alternativ Uniform Resource Identifier (URI).

När du använder **ConnectionURI** -parametern kan fjärrdestinationen returnera en instruktion för att omdirigera till en annan URI. Som standard omdirigerar PowerShell inte anslutningar, men du kan använda den här parametern om du vill att den ska kunna omdirigera anslutningen.

Du kan också begränsa hur många gånger anslutningen omdirigeras genom att ändra värdet för alternativet **MaximumConnectionRedirectionCount** session. Använd parametern **MaximumRedirection** för `New-PSSessionOption` cmdleten eller ange egenskapen **MaximumConnectionRedirectionCount** för `$PSSessionOption` Preference-variabeln. Standardvärdet är 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Anger program namns segmentet för anslutnings-URI: n. Använd den här parametern för att ange program namnet när du inte använder parametern **ConnectionURI** i kommandot.

Standardvärdet är värdet för Preference- `$PSSessionApplicationName` variabeln på den lokala datorn. Om den här preferens variabeln inte har definierats är standardvärdet WSMAN. Det här värdet är lämpligt för de flesta användnings områden. Mer information finns i [about_Preference_Variables](./About/about_Preference_Variables.md).

WinRM-tjänsten använder program namnet för att välja en lyssnare som ska betjäna anslutningsbegäran.
Värdet för den här parametern ska matcha värdet på egenskapen **URLPrefix** för en lyssnare på fjärrdatorn.

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: $PSSessionApplicationName if set on the local computer, otherwise WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Argument List

Tillhandahåller värdena för lokala variabler i kommandot. Variablerna i kommandot ersätts av de här värdena innan kommandot körs på fjärrdatorn. Ange värdena i en kommaavgränsad lista. Värdena är associerade med variabler i den ordning som de visas. Aliaset för **argument List** är argument.

Värdena i **argument List** -parametern kan vara faktiska värden, till exempel 1024, eller så kan de vara referenser till lokala variabler, till exempel `$max` .

Använd följande kommando format om du vill använda lokala variabler i ett kommando:

`{param($<name1>[, $<name2>]...) <command-with-local-variables>} -ArgumentList <value>` eller `<local-variable>`

Nyckelordet **param** listar de lokala variabler som används i kommandot. **Argument List** tillhandahåller värdena för variablerna i den ordning som de visas. Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – AsJob

Anger att denna cmdlet kör kommandot som ett bakgrunds jobb på en fjärrdator. Använd den här parametern för att köra kommandon som tar lång tid att slutföra.

När du använder parametern **AsJob** , returnerar kommandot ett objekt som representerar jobbet och visar sedan kommando tolken. Du kan fortsätta att arbeta i sessionen medan jobbet är klart. Använd cmdletarna för att hantera jobbet `*-Job` . Använd cmdleten för att hämta jobb resultatet `Receive-Job` .

Parametern **AsJob** påminner om `Invoke-Command` att använda cmdleten för att köra en `Start-Job` cmdlet via en fjärr anslutning. Men med **AsJob** skapas jobbet på den lokala datorn även om jobbet körs på en fjärrdator. Resultatet av fjärrjobbet returneras automatiskt till den lokala datorn.

Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](About/about_Jobs.md) och [about_Remote_Jobs](About/about_Remote_Jobs.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering

Anger den mekanism som används för att autentisera användarens autentiseringsuppgifter. CredSSP-autentisering är endast tillgängligt i Windows Vista, Windows Server 2008 och senare versioner av Windows operativ system.

De acceptabla värdena för den här parametern är följande:

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
> CredSSP-autentisering (Credential Security Support Provider), där användarens autentiseringsuppgifter skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen. Mer information finns i [Credential Security Support Provider](/windows/win32/secauthn/credential-security-support-provider).

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:
Accepted values: Basic, Default, Credssp, Digest, Kerberos, Negotiate, NegotiateWithImplicitCredential

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att ansluta till den frånkopplade sessionen. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton och de fungerar inte med domän konton.

Om du vill hämta ett tumavtryck för certifikatet använder du ett `Get-Item` eller- `Get-ChildItem` kommando i PowerShell-certifikatet: enhet.

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

Anger de datorer där kommandot körs. Standard är den lokala datorn.

När du använder parametern **computername** skapar PowerShell en tillfällig anslutning som bara används för att köra det angivna kommandot och sedan stängs. Om du behöver en permanent anslutning använder du parametern **session** .

Ange NETBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en eller flera datorer i en kommaavgränsad lista. Om du vill ange den lokala datorn skriver du datorns namn, localhost eller en punkt ( `.` ).

Om du vill använda en IP-adress i värdet för **computername** måste kommandot innehålla parametern **Credential** . Datorn måste vara konfigurerad för HTTPS-transporten eller fjärrdatorns IP-adress måste ingå i den lokala datorns WinRM **TrustedHosts** -lista. Instruktioner för att lägga till ett dator namn i listan **TrustedHosts** finns i [så här lägger du till en dator i listan över betrodda värden](./about/about_remote_troubleshooting.md#how-to-add-a-computer-to-the-trusted-hosts-list).

I Windows Vista och senare versioner av operativ systemet Windows måste du köra PowerShell med alternativet **Kör som administratör** för att kunna inkludera den lokala datorn i värdet för **computername**.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases: Cn

Required: False
Position: 0
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### – ConfigurationName

Anger den sessionsinformation som används för den nya **PSSession**.

Ange ett konfigurations namn eller den fullständigt kvalificerade resurs-URI: n för en konfiguration av sessionen. Om du bara anger konfigurations namnet är följande schema-URI anpassningsprefix: `http://schemas.microsoft.com/PowerShell` .

När den används med SSH anger den här parametern under systemet som ska användas på målet enligt definitionen i `sshd_config` . Standardvärdet för SSH är under `powershell` systemet.

Sessionens konfiguration för en session finns på fjärrdatorn. Om den angivna konfigurationen av sessionen inte finns på fjärrdatorn Miss lyckas kommandot.

Standardvärdet är värdet för Preference- `$PSSessionConfigurationName` variabeln på den lokala datorn. Om den här preferens variabeln inte har angetts är standardvärdet **Microsoft. PowerShell**. Mer information finns i [about_Preference_Variables](about/about_Preference_Variables.md).

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: $PSSessionConfigurationName if set on the local computer, otherwise Microsoft.PowerShell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Anger en Uniform Resource Identifier (URI) som definierar sessionens anslutnings slut punkt.
URI: n måste vara fullständigt kvalificerad.

Formatet för den här strängen är följande:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

Standardvärdet är följande:

`http://localhost:5985/WSMAN`

Om du inte anger en anslutnings-URI kan du använda parametrarna **UseSSL** och **port** för att ange anslutnings-URI-värden.

Giltiga värden för URI: n i **transport** segmentet är http och https. Om du anger en anslutnings-URI med ett transport segment, men inte anger någon port, skapas sessionen med standard portarna: 80 för HTTP och 443 för HTTPS. Om du vill använda standard portarna för PowerShell-fjärrkommunikation anger du Port 5985 för HTTP eller 5986 för HTTPS.

Om mål datorn omdirigerar anslutningen till en annan URI, förhindrar PowerShell omdirigeringen om du inte använder parametern **AllowRedirection** i kommandot.

```yaml
Type: System.Uri[]
Parameter Sets: Uri, FilePathUri
Aliases: URI, CU

Required: False
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: False
Accept wildcard characters: False
```

### -ContainerId

Anger en matris med container-ID: n.

```yaml
Type: System.String[]
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName
Aliases:

Required: True (VMId, VMName, FilePathVMId, FilePathVMName), False (ComputerName, FilePathComputerName, Uri, FilePathUri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Anger att denna cmdlet lägger till en interaktiv säkerhetstoken till loopback-sessioner. Med den interaktiva token kan du köra kommandon i loopback-sessionen som hämtar data från andra datorer. Du kan till exempel köra ett kommando i sessionen som kopierar XML-filer från en fjärrdator till den lokala datorn.

En loopback-session är en **PSSession** som kommer från och slutar på samma dator. Om du vill skapa en loopback-session utelämnar du parametern **computername** eller anger värdet till punkt ( `.` ), localhost eller namnet på den lokala datorn.

Som standard skapas loopback-sessioner med en nätverks-token som kanske inte ger behörighet att autentisera till fjärrdatorer.

Parametern **EnableNetworkAccess** är endast effektiv i loopback-sessioner. Om du använder **EnableNetworkAccess** när du skapar en-session på en fjärrdator, lyckas kommandot, men parametern ignoreras.

Du kan tillåta fjärråtkomst i en loopback-session med hjälp av **CredSSP** -värdet för parametern **Authentication** , som delegerar autentiseringsuppgifterna för sessionen till andra datorer.

För att skydda datorn från skadlig åtkomst kan frånkopplade loopback-sessioner som har interaktiva tokens, som är de som skapats med **EnableNetworkAccess**, bara återanslutas från den dator där sessionen skapades. Frånkopplade sessioner som använder CredSSP-autentisering kan återanslutas från andra datorer. Mer information finns i `Disconnect-PSSession`.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger ett lokalt skript som denna cmdlet körs på en eller flera fjärrdatorer. Ange sökvägen och fil namnet för skriptet eller skicka en sökväg till en skript Sök väg till `Invoke-Command` . Skriptet måste finnas på den lokala datorn eller i en katalog som den lokala datorn kan komma åt. Använd **argument List** för att ange värden för parametrarna i skriptet.

När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block, skickar skript blocket till fjärrdatorn och kör det på fjärrdatorn.

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, FilePathComputerName, FilePathUri, FilePathVMId, FilePathVMName, FilePathContainerId, FilePathSSHHost, FilePathSSHHostHash
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HideComputerName

Anger att denna cmdlet utelämnar dator namnet för varje objekt från visningen av utdata. Som standard visas namnet på den dator som skapade objektet i visningen.

Den här parametern påverkar endast visningen av utdata. Objektet ändras inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases: HCN

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Anger en matris med dator namn för en SSH-baserad (Secure Shell) anslutning. Detta liknar parametern **computername** , förutom att anslutningen till fjärrdatorn görs med SSH i stället för Windows WinRM.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String[]
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InDisconnectedSession

Anger att denna cmdlet kör ett kommando eller skript i en frånkopplad session.

När du använder parametern **InDisconnectedSession** `Invoke-Command` skapar en beständig session på varje fjärrdator, startar kommandot som anges av parametern **script block** eller **sökväg** och kopplar sedan från sessionen. Kommandona fortsätter att köras i de frånkopplade sessionerna. Med **InDisconnectedSession** kan du köra kommandon utan att ha en anslutning till fjärrsessionerna. Eftersom sessionen kopplas bort innan ett resultat returneras, ser **InDisconnectedSession** till att alla kommando resultat returneras till den återanslutna sessionen, i stället för att delas mellan sessioner.

Du kan inte använda **InDisconnectedSession** med parametern **session** eller parametern **AsJob** .

Kommandon som använder **InDisconnectedSession** returnerar ett **PSSession** -objekt som representerar den frånkopplade sessionen. De returnerar inte kommandoutdata. Använd cmdletarna eller för att ansluta till den frånkopplade `Connect-PSSession` sessionen `Receive-PSSession` . Använd cmdleten för att hämta resultatet av de kommandon som kördes i sessionen `Receive-PSSession` . Om du vill köra kommandon som genererar utdata i en frånkopplad session anger du värdet för alternativet **OutputBufferingMode** session som du vill **ta bort**. Om du vill ansluta till den frånkopplade sessionen ställer du in tids gränsen för inaktivitet i sessionen så att den ger tillräckligt med tid för att ansluta innan sessionen tas bort.

Du kan ställa in buffrings läget för utdata och tids gränsen för inaktivitet i parametern **SessionOption** eller i `$PSSessionOption` variabeln Preference. Mer information om sessions alternativ finns i `New-PSSessionOption` och [about_Preference_Variables](./about/about_preference_variables.md).

Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md).

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases: Disconnected

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ininformation till kommandot. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

När du använder **InputObject** -parametern använder du den `$Input` automatiska variabeln i värdet för parametern **script block** för att representera de ingående objekten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – JobName

Anger ett eget namn för bakgrunds jobbet. Som standard namnges jobb `Job<n>` , där `<n>` är ett ordnings tal.

Om du använder parametern **JobName** i ett kommando körs kommandot som ett jobb och `Invoke-Command` returnerar ett jobb objekt, även om du inte inkluderar **AsJob** i kommandot.

Mer information om PowerShell-bakgrunds jobb finns [about_Jobs](./About/about_Jobs.md).

```yaml
Type: System.String
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam
Aliases:

Required: False
Position: Named
Default value: Job<n>
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fil Sök väg

Anger en nyckel fil Sök väg som används av SSH (Secure Shell) för att autentisera en användare på en fjärrdator.

SSH tillåter att användarautentisering utförs via privata och offentliga nycklar som ett alternativ till grundläggande lösenordsautentisering. Om fjärrdatorn har kon figurer ATS för nyckel autentisering kan du använda den här parametern för att ange den nyckel som identifierar användaren.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewScope

Anger att denna cmdlet kör det angivna kommandot i det aktuella omfånget. Som standard `Invoke-Command` Kör kommandon i deras egna omfång.

Den här parametern är endast giltig i kommandon som körs i den aktuella sessionen, det vill säga kommandon som utelämnar både **computername** -och **session** -parametrarna.

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InProcess
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger nätverks porten på den fjärrdator som används för det här kommandot. Om du vill ansluta till en fjärrdator måste fjärrdatorn Lyssna på porten som anslutningen använder. Standard portarna är 5985 (WinRM-port för HTTP) och 5986 (WinRM-port för HTTPS).

Innan du använder en alternativ port konfigurerar du WinRM-lyssnaren på fjärrdatorn för att lyssna på den porten. Konfigurera lyssnaren genom att skriva följande två kommandon i PowerShell-prompten:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Använd inte **port** parametern om du inte behöver det. Porten som anges i kommandot gäller för alla datorer eller sessioner där kommandot körs. En alternativ port inställning kan hindra kommandot från att köras på alla datorer.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, FilePathComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoteDebug

Används för att köra det anropade kommandot i fel söknings läge i den fjärranslutna PowerShell-sessionen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, SSHHost, ContainerId, FilePathContainerId, SSHHostHashParam, FilePathSSHHost, FilePathSSHHostHash
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Anger att denna cmdlet anropar ett kommando som administratör.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block

Anger vilka kommandon som ska köras. Sätt i kommandona inom klammerparenteser `{ }` för att skapa ett skript block.
Den här parametern är obligatorisk.

Som standard utvärderas alla variabler i kommandot på fjärrdatorn. Använd **argument List** om du vill inkludera lokala variabler i kommandot.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: InProcess, Session, ComputerName, Uri, VMId, VMName, SSHHost, ContainerId, SSHHostHashParam
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Session

Anger en matris med sessioner där denna cmdlet kör kommandot. Ange en variabel som innehåller **PSSession** -objekt eller ett kommando som skapar eller hämtar **PSSession** -objekt, till exempel ett `New-PSSession` eller- `Get-PSSession` kommando.

När du skapar en **PSSession** upprättar PowerShell en permanent anslutning till fjärrdatorn. Använd en **PSSession** för att köra en serie relaterade kommandon som delar data. Om du vill köra ett enda kommando eller en serie med orelaterade kommandon använder du parametern **computername** . Mer information finns i [about_PSSessions](./About/about_PSSessions.md).

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: FilePathRunspace, Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessionsnamn

Anger ett eget namn för en frånkopplad session. Du kan använda namnet för att referera till sessionen i efterföljande kommandon, till exempel ett `Get-PSSession` kommando. Den här parametern är endast giltig med parametern **InDisconnectedSession** .

Den här parametern introducerades i PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Anger avancerade alternativ för sessionen. Ange ett **SessionOption** -objekt, t. ex. ett som du skapar med hjälp av `New-PSSessionOption` cmdleten, eller en hash-tabell där nycklarna är namn på sessionstillstånd och värdena är alternativ värden för session.

Standardvärdena för alternativen bestäms av värdet för `$PSSessionOption` variabeln Preference, om det har angetts. Annars upprättas standardvärdena med alternativ som anges i konfigurationen av sessionen.

Värdena för sessionens alternativ prioriteras framför standardvärden för sessioner som angetts i `$PSSessionOption` variabeln Preference och i konfigurationen för sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen.

En beskrivning av de sessionsinformation som innehåller standardvärdena finns i `New-PSSessionOption` . Information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).
För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, FilePathComputerName, Uri, FilePathUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

Den här parametern tar en matris med hash-tabeller där varje hash-tabell innehåller en eller flera anslutnings parametrar som krävs för att upprätta en SSH-anslutning (Secure Shell). Parametern **SSHConnection** är användbar för att skapa flera sessioner där varje session kräver annan anslutnings information.

Hash-tabellen har följande medlemmar:

- **Computername** (eller **värdnamn**)
- **Port**
- **Användar**
- **Sökväg till fil Sök väg** (eller **IdentityFilePath**)

**Computername** (eller **hostname**) är det enda nyckel/värde-par som krävs.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam, FilePathSSHHostHash
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

Anger att fjärr anslutningen upprättas med hjälp av SSH (Secure Shell).

Som standard använder PowerShell Windows WinRM för att ansluta till en fjärrdator. Den här växeln tvingar PowerShell att använda **hostname** -parametern för att upprätta en SSH-baserad fjärr anslutning.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.

Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: FilePathRunspace, Session, ComputerName, FilePathComputerName, Uri, FilePathUri, VMId, VMName, FilePathVMId, FilePathVMName, ContainerId, FilePathContainerId
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UserName

Anger användar namnet för det konto som används för att köra ett kommando på fjärrdatorn. Metoden för användarautentisering är beroende av hur Secure Shell (SSH) är konfigurerat på fjärrdatorn.

Om SSH har kon figurer ATS för grundläggande lösenordsautentisering uppmanas du att ange användar lösen ordet.

Om SSH har kon figurer ATS för nyckelbaserad användarautentisering kan en nyckel fil Sök väg tillhandahållas via parametern för nyckel **Sök väg** och inget lösen ord visas. Om klientens användar nyckel finns på en känd SSH-plats behövs inte parametern för nyckel **Sök** vägar för nyckelbaserad autentisering, och användarautentisering sker automatiskt baserat på användar namnet. Mer information finns i din plattforms SSH-dokumentation om nyckelbaserad användarautentisering.

Detta är inte en obligatorisk parameter. Om parametern **username** inte anges används det aktuella inloggade användar namnet för anslutningen.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.String
Parameter Sets: SSHHost, FilePathSSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Anger att denna cmdlet använder Secure Sockets Layer-protokollet (SSL) för att upprätta en anslutning till fjärrdatorn. Som standard används inte SSL.

WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket. Parametern **UseSSL** är ett ytterligare skydd som skickar data via https i stället för http.

Om du använder den här parametern, men SSL inte är tillgängligt på den port som används för kommandot, Miss lyckas kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Anger en matris med ID: n för virtuella datorer.

```yaml
Type: System.Guid[]
Parameter Sets: VMId, FilePathVMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – VMName

Anger en matris med namn på virtuella datorer.

```yaml
Type: System.String[]
Parameter Sets: VMName, FilePathVMName
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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. script block

Du kan skicka vidare ett kommando i ett skript block till `Invoke-Command` . Använd den `$Input` automatiska variabeln för att representera inobjekten i kommandot.

## UTDATA

### System. Management. Automation. PSRemotingJob, system. Management. Automation. körnings utrymmen. PSSession eller utdata från det anropade kommandot

Den här cmdleten returnerar ett jobb objekt, om du använder parametern **AsJob** . Om du anger parametern **InDisconnectedSession** `Invoke-Command` returnerar ett **PSSession** -objekt. Annars returnerar den utdata från kommandot som anropades, vilket är värdet för parametern **script block** .

## ANTECKNINGAR

I Windows Vista och senare versioner av operativ systemet Windows, för att använda parametern **computername** för `Invoke-Command` för att köra ett kommando på den lokala datorn, måste du köra PowerShell med alternativet **Kör som administratör** .

När du kör kommandon på flera datorer ansluter PowerShell till datorerna i den ordning som de visas i listan. Men kommandots utdata visas i den ordning som den tas emot från fjärrdatorer, vilket kan vara olika.

Fel som orsakas av kommandot som `Invoke-Command` körs ingår i kommando resultatet.
Fel som avslutar fel i ett lokalt kommando behandlas som icke-avslutande fel i ett fjärrkommando. Den här strategin ser till att avslutande fel på en dator inte stänger kommandot på alla datorer där den körs. Den här metoden används även när ett fjärrkommando körs på en enda dator.

Om fjärrdatorn inte finns i en domän som den lokala datorn litar på, kanske datorn inte kan autentisera användarens autentiseringsuppgifter. Om du vill lägga till fjärrdatorn i listan över betrodda värdar i WS-Management använder du följande kommando i `WSMAN` providern, där `<Remote-Computer-Name>` är namnet på fjärrdatorn:

`Set-Item -Path WSMan:\Localhost\Client\TrustedHosts -Value \<Remote-Computer-Name\>`

När du kopplar från en **PSSession** med hjälp av **InDisconnectedSession** -parametern är sessionstillståndet **frånkopplat** och tillgängligheten är **ingen**. Värdet för egenskapen **State** är i förhållande till den aktuella sessionen. Värdet **frånkopplat** innebär att **PSSession** inte är ansluten till den aktuella sessionen. Det innebär dock inte att **PSSession** är frånkopplad från alla sessioner. Den kan vara ansluten till en annan session. Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.

**Tillgänglighet** svärdet **none** anger att du kan ansluta till sessionen. Värdet **upptagen** anger att du inte kan ansluta till **PSSession** eftersom det är anslutet till en annan session. Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate). Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

**Värd** namnen och **SSHConnection** -parametrarna ingick från och med PowerShell 6,0. De lades till för att tillhandahålla PowerShell-fjärrkommunikation utifrån SSH (Secure Shell). PowerShell och SSH stöds på flera plattformar (Windows, Linux, macOS) och PowerShell-fjärrkommunikation fungerar över dessa plattformar där PowerShell och SSH har installerats och kon figurer ATS. Detta skiljer sig från den tidigare Windows-fjärrkommunikationen som baseras på WinRM och många av de särskilda WinRM-funktionerna och begränsningarna gäller inte. Till exempel kan WinRM-baserade kvoter, sessions alternativ, anpassad slut punkts konfiguration och funktionerna för att koppla från/återansluta inte användas för närvarande. Mer information om hur du konfigurerar PowerShell SSH-fjärrkommunikation finns i [PowerShell-fjärrkommunikation via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## RELATERADE LÄNKAR

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Remote_Troubleshooting](./About/about_remote_troubleshooting.md)

[about_Remote_Variables](./About/about_Remote_Variables.md)

[about_Scopes](./About/about_scopes.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Anropa-objekt](../Microsoft.PowerShell.Management/Invoke-Item.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

