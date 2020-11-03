---
description: Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 838e142fe39260b759e9a44c6d69b80d3c5b293e
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2020
ms.locfileid: "93272997"
---
# <a name="about-jobs"></a>Om jobb

## <a name="short-description"></a>Kort beskrivning
Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.

## <a name="long-description"></a>Lång beskrivning

PowerShell kör kommandon och skript via jobb samtidigt. Det finns tre jobbbaserade lösningar som tillhandahålls av PowerShell för att stödja samtidighet.

|Jobb            |Beskrivning                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |Kommando och skript körs på en fjärrdator.                 |
|`BackgroundJob`|Kommando och skript körs i en separat process på den lokala    |
|               |datorspecifika.                                                     |
|`ThreadJob`    |Kommando och skript körs i en separat tråd inom samma  |
|               |processen på den lokala datorn.                                |

Varje typ av jobb har fördelar och nack delar. Att köra skript på en annan dator eller i en separat process har en bra isolering. Eventuella fel påverkar inte andra jobb som körs eller klienten som startade jobbet. Men Remoting-lagret lägger till overhead, inklusive objekt serialisering. Alla objekt som skickas till och från fjärrsessionen måste serialiseras och sedan avserialiseras i takt med att den passerar mellan klienten och mål sessionen. Serialiserings åtgärden kan använda många beräknings-och minnes resurser för stora komplexa data objekt.

I det här avsnittet beskrivs hur du kör bakgrunds jobb i PowerShell på en lokal dator. Information om hur du kör bakgrunds jobb på fjärrdatorer finns [about_Remote_Jobs](about_Remote_Jobs.md). Mer information om tråd jobb finns i [about_Thread_Jobs](about_Thread_Jobs.md).

När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart, även om jobbet tar en längre tid att slutföra. Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.

## <a name="the-job-cmdlets"></a>Jobb-cmdletar

|Cmdlet          |Beskrivning                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |Startar ett bakgrunds jobb på en lokal dator.           |
|`Get-Job`       |Hämtar bakgrunds jobben som startades i      |
|                |aktuell session.                                       |
|`Receive-Job`   |Hämtar resultatet av bakgrunds jobb.                   |
|`Stop-Job`      |Stoppar ett bakgrunds jobb.                                |
|`Wait-Job`      |Ignorerar kommando tolken tills ett eller flera jobb|
|                |full.                                              |
|`Remove-Job`    |Tar bort ett bakgrunds jobb.                              |
|`Invoke-Command`|Parametern **AsJob** skapar ett bakgrunds jobb på en  |
|                |Fjärran sluten dator. Du kan använda `Invoke-Command` för att köra   |
|                |valfritt jobb kommando, inklusive `Start-Job` .       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>Starta ett jobb på den lokala datorn

Om du vill starta ett bakgrunds jobb på den lokala datorn använder du `Start-Job` cmdleten.

Om du vill skriva ett `Start-Job` kommando omger du kommandot som jobbet kör inom klammerparenteser ( `{}` ). Använd parametern **script block** för att ange kommandot.

Följande kommando startar ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.

```powershell
Start-Job -ScriptBlock {Get-Process}
```

`Start-Job`Kommandot returnerar ett objekt som representerar jobbet. Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.

Spara jobbobjektet i en variabel och Använd sedan det med andra jobb-cmdletar för att hantera bakgrunds jobbet. Följande kommando startar ett jobb objekt och sparar det resulterande jobbobjektet i `$job` variabeln.

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

Från och med PowerShell 6,0 kan du använda en amersand ( `&` ) i slutet av en pipeline för att starta ett bakgrunds jobb. Följande kommando fungerar som likvärdigt med kommandot ovan.

```powershell
$job = Get-Process &
```

Et-tecknet ( `&` ) kallas för bakgrunds operatorn. Mer information finns i [bakgrunds operator](about_Operators.md#background-operator-).

Du kan också använda `Get-Job` cmdleten för att hämta objekt som representerar de jobb som startats i den aktuella sessionen. `Get-Job` returnerar samma jobb objekt som `Start-Job` returnerar.

## <a name="getting-job-objects"></a>Hämtar jobb objekt

Använd cmdleten för att hämta objektet som representerar bakgrunds jobben som startades i den aktuella sessionen `Get-Job` . Utan parametrar `Get-Job` returnerar alla jobb som startades i den aktuella sessionen.

Följande kommando hämtar till exempel jobben i den aktuella sessionen.

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

Du kan också spara jobbobjektet i en variabel och använda det för att representera jobbet i ett senare kommando. Följande kommando hämtar jobbet med ID 1 och sparar det i `$job` variabeln.

```powershell
$job = Get-Job -Id 1
```

Jobbobjektet innehåller jobbets tillstånd, vilket indikerar om jobbet har avslut ATS. Ett slutfört jobb har statusen **slutförd** eller **misslyckad**. Ett jobb kan också **blockeras** eller **köras**.

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a>Hämta resultatet av ett jobb

När du kör ett bakgrunds jobb visas inte resultaten direkt. I stället `Start-Job` returnerar cmdleten ett jobb objekt som representerar jobbet, men det innehåller inte resultatet. Använd cmdleten för att hämta resultatet av ett bakgrunds jobb `Receive-Job` .

Följande kommando använder `Receive-Job` cmdleten för att hämta resultatet av jobbet. Det använder ett jobb objekt som sparats i `$job` variabeln för att identifiera jobbet.

```powershell
Receive-Job -Job $job
```

`Receive-Job`Cmdleten returnerar resultatet från jobbet.

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

Du kan också spara resultatet av ett jobb i en variabel. Följande kommando sparar resultatet av jobbet i `$job` variabeln till `$results` variabeln.

```powershell
$results = Receive-Job -Job $job
```

Du kan också spara resultatet av jobbet i en fil med hjälp av omdirigerings operatorn ( `>` ) eller `Out-File` cmdleten. Följande kommando använder operatorn för omdirigering för att spara resultatet av jobbet i `$job` variabeln i `Results.txt` filen.

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a>Hämta och behålla del jobbs resultat

`Receive-Job`Cmdlet: en hämtar resultatet av ett bakgrunds jobb. Om jobbet har slutförts, `Receive-Job` hämtas alla jobb resultat. Om jobbet fortfarande körs `Receive-Job` hämtar de resultat som har genererats hittills. Du kan köra `Receive-Job` kommandon igen för att få återstående resultat.

När `Receive-Job` returnerar resultat tas dessa resultat som standard bort från cachen där jobb resultat lagras. Om du kör ett annat `Receive-Job` kommando får du bara de resultat som ännu inte har tagits emot.

Följande kommandon visar resultatet av kommandon som `Receive-Job` körs innan jobbet har slutförts.

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

Om du inte vill `Receive-Job` ta bort jobb resultatet som det har returnerat använder du parametern **Keep** . Därför `Receive-Job` returneras alla resultat som har genererats fram till den tiden.

Följande kommandon visar effekterna av att använda parametern **Keep** i ett jobb som inte har slutförts än.

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

## <a name="waiting-for-the-results"></a>Väntar på resultaten

Om du kör ett kommando som tar lång tid att slutföra kan du använda egenskaperna för jobbobjektet för att fastställa när jobbet har slutförts. Följande kommando använder `Get-Job` objektet för att hämta alla bakgrunds jobb i den aktuella sessionen.

```powershell
Get-Job
```

Resultaten visas i en tabell. Jobbets status visas i kolumnen **status** .

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

I det här fallet visar egenskapen State att jobb 2 fortfarande körs. Om du vill använda `Receive-Job` cmdleten för att hämta jobb resultaten nu skulle resultaten vara ofullständiga. Du kan använda `Receive-Job` cmdleten upprepade gånger för att hämta alla resultat. Som standard får du bara de resultat som inte redan tagits emot, varje gång du använder den, men du kan använda parametern **Keep** för `Receive-Job` cmdlet: en för att behålla resultaten, även om de redan har tagits emot.

Du kan skriva de partiella resultaten till en fil och sedan lägga till nya resultat när de tas emot eller vänta och kontrol lera jobbets tillstånd senare.

Du kan använda parametern **wait** för `Receive-Job` cmdleten, som inte returnerar kommando tolken förrän jobbet har slutförts och alla resultat är tillgängliga.

Du kan också använda `Wait-Job` cmdleten för att vänta på ett eller alla resultat av jobbet. `Wait-Job` Du kan vänta på ett visst jobb, för alla jobb eller för att utföra slutförda jobb.

Följande kommando använder `Wait-Job` cmdleten för att vänta på ett jobb med **ID**
10.

```powershell
Wait-Job -ID 10
```

Därför ignoreras PowerShell-prompten tills jobbet har slutförts.

Du kan också vänta en fördefinierad tids period. Det här kommandot använder **timeout** -parametern för att begränsa vänte tiden till 120 sekunder. När tiden går ut returneras kommando tolken, men jobbet fortsätter att köras i bakgrunden.

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>Stoppa ett jobb

Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten. Följande kommando startar ett jobb för att hämta varje post i system händelse loggen. Objektet sparas i `$job` variabeln.

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

Följande kommando stoppar jobbet. En pipeline-operator () används `|` för att skicka jobbet i `$job` variabeln till `Stop-Job` .

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>Ta bort ett jobb

Om du vill ta bort ett bakgrunds jobb använder du `Remove-Job` cmdleten. Följande kommando tar bort jobbet i `$job` variabeln.

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>Undersöka ett misslyckat jobb

Om du vill ta reda på varför ett jobb misslyckades, Använd egenskapen **orsak** för jobbobjektet.

Följande kommando startar ett jobb utan de autentiseringsuppgifter som krävs. Objektet sparas i `$job` variabeln.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

Följande kommando använder egenskapen orsak för att hitta felet som gjorde att jobbet inte kunde köras.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

I det här fallet misslyckades jobbet eftersom fjärrdatorn krävde explicita autentiseringsuppgifter för att köra kommandot. Värdet för egenskapen **orsak** är:

Det gick inte att ansluta till fjärrservern. följande fel meddelande visas: "åtkomst nekad".

## <a name="see-also"></a>Se även

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start – jobb](xref:Microsoft.PowerShell.Core.Start-Job)
- [Hämta jobb](xref:Microsoft.PowerShell.Core.Get-Job)
- [Mottagning – jobb](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stoppa – jobb](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Ta bort – jobb](xref:Microsoft.PowerShell.Core.Remove-Job)
- [Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)
