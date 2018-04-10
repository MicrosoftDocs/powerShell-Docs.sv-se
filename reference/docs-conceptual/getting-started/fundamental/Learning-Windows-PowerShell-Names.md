---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Läs mer om Windows PowerShell-namn
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 381aa619a41ccacb2ff3a4cdbc2b75b7f04282d1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="learning-windows-powershell-names"></a>Läs mer om Windows PowerShell-namn
Learning namnen på kommandon och parametrar för kommandot är en betydande tid investering med de flesta kommandoradsverktyget gränssnitt. Problemet är att det finns mycket få mönster, så det enda sättet att lära dig om du lär dig varje kommando och varje parameter som du behöver använda regelbundet.

När du arbetar med ett nytt kommando eller en parameter använda du normalt inte vad du redan vet; Du måste ta och lär dig ett nytt namn. Om du tittar på hur gränssnitt växa från en liten uppsättning verktyg med inkrementell tillägg till funktioner är det enkelt att se varför strukturen är inte är standard. Med kommandonamn i synnerhet är det här kan låta logiska eftersom varje kommando är ett fristående verktyg, men det finns ett bättre sätt att hantera kommandonamn.

De flesta kommandon skapas för att hantera element av operativsystem och program, till exempel tjänster eller processer. Kommandona har olika namn som kanske eller kanske inte får plats i en familj. Till exempel på Windows-System kan du använda den **net start** och **net stop** kommandon för att starta och stoppa en tjänst. Det finns en annan mer generaliserade service control verktyg för Windows som har ett fullständigt namn, **sc**, som inte passar i namngivningsmönster för den **net** tjänsten kommandon. För hanteringen, Windows har det **tasklist** kommando till listan processer och **taskkill** kommando för att avsluta processer.

Kommandon som parametrar har oregelbundna parametern specifikationer. Du kan inte använda den **net start** kommando för att starta en tjänst på en fjärrdator. Den **sc** kommando startar en tjänst på en fjärrdator, men om du vill ange fjärrdatorn måste du ange prefixet dess namn med ett dubbelt omvänt snedstreck. Till exempel om du vill starta utskriftshanteraren på en fjärrdator med namnet DC01, skriver du **sc \\ \\DC01 starta utskriftshanterarens**. Listan aktiviteter som körs på DC01, måste du använda den **/S** parametern (för ”system”) och ange namnet DC01 utan omvända snedstreck så här: **tasklist /S DC01**.

Även om det finns viktiga tekniska skillnader mellan en tjänst och en process, är de båda exempel hanterbara elementen på en dator som har en väldefinierad livscykel. Du kanske vill starta eller stoppa en tjänst eller en process eller hämta en lista över alla tjänster eller processer som körs. Med andra ord men en tjänst och en process är olika saker, är de åtgärder som vi utföra på en tjänst eller en process ofta begreppsmässigt samma. Dessutom kanske val vi kan göra att anpassa en åtgärd genom att ange parametrar begreppsmässigt samt.

Windows PowerShell utnyttjar dessa likheter för att minska antalet distinkta namn som du behöver veta för att förstå och använda cmdlets.

### <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Använd cmdlet: ar Verb-substantiv namn att minska kommandot memorera
Windows PowerShell använder ett ”verb-substantiv” naming system där varje cmdlet-namn består av ett verb som standard med bindestreck med en specifik substantiv. Windows PowerShell-verb är inte alltid engelska verb, men de express specifika åtgärder i Windows PowerShell. Substantiv är mycket lik substantiv på alla språk, de beskriver specifika typer av objekt som är viktiga i systemadministration. Det är enkelt att demonstrera hur dessa två delnamn minska learning arbete genom att titta på några exempel på verb och substantiv.

Substantiv begränsas mindre, men de bör alltid beskriver ett kommando agerar på. Windows PowerShell har kommandon som **Get-Process**, **stoppa processen**, **Get-Service**, och **Stop-Service**.

När det gäller två substantiv och två verb förenkla konsekvenskontroll inte learning mycket. Om du tittar på en standarduppsättning 10 verb och substantiv 10 sedan har du bara 20 ord att förstå, men dessa ord som kan användas för att bilda 100 distinkta kommandonamn.

Ofta kan du kan identifiera ett kommando har genom att läsa dess namn och är vanligtvis tydligt vilket namn som ska användas för ett nytt kommando. Till exempel en dator avstängningskommandot kanske **Stop-Computer**. Ett kommando som visar alla datorer i ett nätverk kan vara **Get-dator**. Kommandot som hämtar systemdatumet är **Get-Date**.

Du kan visa en lista över alla kommandon som innehåller ett visst verb med den **-Verb** parameter för **Get-Command** (diskuteras **Get-Command** i detalj i nästa avsnitt). Till exempel för att se alla cmdletar som använder verbet **hämta**, typ:

```
PS> Get-Command -Verb Get
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Den **-substantiv** parameter är ännu mer användbar eftersom du kan se en familj av kommandon som påverkar samma typ av objekt. Till exempel om du vill se vilka kommandon som finns för att hantera tjänster, Skriv följande kommando:

```
PS> Get-Command -Noun Service
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

Kommandot är inte nödvändigtvis en cmdlet bara eftersom den har ett verb-substantiv namngivningsschema. Ett exempel på en intern Windows PowerShell-kommando som inte är en cmdlet men har ett verb-substantiv-namn är kommandot för att rensa konsolfönstret rensa värden. Kommandot Rensa värden är faktiskt en intern funktion som du kan se om du kör Get-Command mot den:

```
PS> Get-Command -Name Clear-Host

CommandType     Name                            Definition
-----------     ----                            ----------
Function        Clear-Host                      $spaceType = [System.Managem...
```

### <a name="cmdlets-use-standard-parameters"></a>Använd cmdlet: ar standardparametrar
Som tidigare nämnts kommandon som används i traditionella kommandoradsverktyget gränssnitt vanligtvis inte konsekventa parameternamn. Ibland har parametrar inte namnen på alla. När de gör det gäller ofta tecken eller förkortas ord som kan skrivas snabbt men inte enkelt tolkas av nya användare.

Windows PowerShell bearbetar parametrar direkt till skillnad från de flesta andra traditionella kommandoradsverktyget gränssnitt, och den använder den här direkt åtkomst till parametrarna tillsammans med guide för utvecklare för att standardisera parameternamn. Även om det inte garanterar att varje cmdlet kommer alltid överensstämmer med standarden, det uppmuntra den.

> [!NOTE]
> Parameternamn alltid ha en '-' till dem före när du använder dem, så att Windows PowerShell att identifiera dem som parametrar. I den **Get-Command - namn, rensa värd** exempelvis parameternamnet är **namn**, men anges den som -**namn**.

Här följer några av de allmänna egenskaperna för standard parameternamn och användningsområden.

#### <a name="the-help-parameter-"></a>Parametern hjälp (?)
När du anger den **-?** Parametern till alla cmdlet cmdleten körs inte. I stället visar Windows PowerShell-hjälpen för cmdleten.

#### <a name="common-parameters"></a>Gemensamma parametrar
Windows PowerShell har flera parametrar som kallas *gemensamma parametrar*. Eftersom dessa parametrar styrs av Windows PowerShell-motorn när de implementeras med en cmdlet, fungerar de alltid på samma sätt. De gemensamma parametrarna är **WhatIf**, **Bekräfta**, **utförlig**, **felsöka**, **Varna**, **ErrorAction**, **ErrorVariable**, **OutVariable**, och **OutBuffer**.

#### <a name="suggested-parameters"></a>Föreslagna parametrar
Windows PowerShell core-cmdletarna använder standard namn liknande parametrar. Användning av parameternamn inte tillämpas, finns det uttrycklig vägledning för användning att uppmuntra standardisering.

Till exempel riktlinjerna rekommenderar namn en parameter som refererar till en dator med namnet som **ComputerName**, i stället för Server, värd, System, nod eller andra vanliga alternativa ord. Bland parametern viktiga föreslagna namn är **kraft**, **undanta**, **inkludera**, **PassThru**, **sökvägen**, och **CaseSensitive**.