---
ms.date: 08/24/2018
keywords: PowerShell cmdlet
title: Learning PowerShell kommandonamn
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 8d50ca03f98ed4ca8f9c09c83ae57afbf0d7888d
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623729"
---
# <a name="learning-powershell-command-names"></a>Learning PowerShell kommandonamn

Learning namnen på kommandon och parametrar kräver en betydande tid investering med de flesta command-line gränssnitt. Problemet är att det inte finns några mönster. Memorera är det enda sättet att lära dig kommandon och parametrar som du behöver använda regelbundet.

När du arbetar med ett nytt kommando eller en parameter, det går inte att du alltid använda det du redan kan. Du måste ta och lär dig ett nytt namn. Traditionellt command-line gränssnitt börja med en liten uppsättning verktyg och växa med inkrementell tillägg. Det är enkelt att se varför det är ingen standard struktur.
Det ser ut logiska efter kommandonamn eftersom varje kommando är ett separat verktyg. PowerShell har ett bättre sätt att hantera kommandonamn.

## <a name="learning-command-names-in-traditional-shells"></a>Learning kommandonamn i traditionella gränssnitt

De flesta kommandon är utformat för att hantera element av operativsystem eller program, till exempel tjänster eller processer. Kommandon har namn som kanske eller kanske inte passar i en serie. Till exempel på Windows-System, du kan använda den `net start` och `net stop` kommandon för att starta och stoppa en tjänst. **SC.exe** är ett annat service control-verktyg för Windows. Det namnet inte passar i namngivningsmönstret för den **net.exe** tjänsten kommandon. För hantering av affärsprocesser, Windows har det **tasklist.exe** för att lista processer och **taskkill.exe** kommando för att avsluta processer.

De här kommandona kräver dessutom oregelbunden parametern specifikationer. Du kan inte använda den `net start` kommando för att starta en tjänst på en fjärrdator. Den **sc.exe** kommando kan starta en tjänst på en fjärrdator. Men om du vill ange fjärrdatorn måste du ange prefixet dess namn med två omvända snedstreck. Om du vill starta tjänsten spooler på en fjärrdator med namnet DC01, skriver du `sc.exe \\DC01 start spooler`.
Listan aktiviteter som körs på DC01, som du använder den **/S** parametern och namnet på datorn utan omvända snedstreck. Till exempel `tasklist /S DC01`.

> [!NOTE]
> Innan du PowerShell v6 `sc` har ett alias för den `Set-Content` cmdlet. Därför att köra den **sc.exe** kommandot i en version av PowerShell före v6, måste du inkludera det fullständiga filnamnet **sc.exe** inklusive filtillägget **exe**.

Tjänster och processer är exempel på hanterbara element på en dator som har väldefinierade supportlivscykel. Du kan starta eller stoppa tjänster och processer eller hämta en lista över alla tjänster eller processer som körs. Även om det finns viktiga tekniska skillnader mellan dem, är de åtgärder du kan utföra på tjänster och processer begreppsmässigt samma. Dessutom är kan de val som vi gör att anpassa en åtgärd genom att ange parametrar vara begreppsmässigt liknas samt.

PowerShell utnyttjar dessa likheter för att minska antalet distinkta namn som du behöver veta för att förstå och använda cmdlets.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlet: ar använda verb-substantiv namn för att minska kommandot memorera

PowerShell använder ett namngivning system för ”verb-substantiv”. Varje cmdlet-namn som består av ett standard verb som ska ha bindestreck med en specifik substantiv. PowerShell-verb är inte alltid engelska verb, men de express specifika åtgärder i PowerShell. Substantiv är ungefär samma sätt som substantiv på valfritt språk. De beskriver vissa typer av objekt som är viktiga för systemadministration. Det är enkelt att demonstrera hur dessa två delnamn minska learning arbete genom att titta på några exempel.

PowerShell har en rekommenderad uppsättning standardverb. Substantiv är mindre begränsade men alltid beskriver verb agerar på. PowerShell har kommandon som `Get-Process`, `Stop-Process`, `Get-Service`, och `Stop-Service`.

I det här exemplet på två substantiv och verb förenkla konsekvens inte lära dig mycket. Utöka listan för att en uppsättning 10 verb och substantiv 10. Nu har du bara 20 ord att förstå.
Men orden kan kombineras för att skapa 100 distinkta kommandonamn.

Det är lätt att förstå vad ett PowerShell-kommando gör genom att läsa dess namn. Kommandot för att stänga av datorn är `Stop-Computer`. Kommando för att lista alla datorer i ett nätverk är `Get-Computer`. Kommando för att hämta systemdatumet är `Get-Date`.

Du kan lista alla kommandon som innehåller ett visst verb med den **Verb** parametern för `Get-Command`. Till exempel vill se alla cmdletar med verbet `Get`, typ:

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

Använd den **substantiv** parametern för att se en familj av kommandon som påverkar samma typ av objekt. Till exempel köra följande kommando för att se kommandona som är tillgängliga för att hantera tjänster:

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

## <a name="cmdlets-use-standard-parameters"></a>Cmdletar använder standardparametrar

Som tidigare nämnts har kommandon som används i traditionella command-line gränssnitt inte alltid konsekventa parameternamn. Parametrarna är ofta tecken eller förkortas ord som är lätta att skriva men som inte är lätt att förstå genom att nya användare.

Till skillnad från de flesta andra traditionella command-line gränssnitt PowerShell bearbetar parametrar direkt och den använder den här direkt åtkomst till parametrarna tillsammans med vägledning för utvecklare för att standardisera parameternamn. Den här vägledningen uppmuntrar men garanterar inte att alla cmdlets som följer standard.

PowerShell standardiserar också parametern avgränsare. Parameternamn har alltid en '-' tillagt för dem med ett PowerShell-kommando. Överväg följande exempel:

```powershell
Get-Command -Name Clear-Host
```

Parameternamnet är **namn**, men det skrivs som `-Name` när de används på kommandoraden som en parameter.

Här är några av de allmänna egenskaperna hos standard parameternamn och användningsområden.

### <a name="the-help-parameter-"></a>Hjälp-parametern (?)

När du anger den `-?` parametern på alla cmdletar PowerShell visar hjälpen för cmdleten.
Cmdleten körs inte.

### <a name="common-parameters"></a>Gemensamma parametrar

PowerShell har flera *gemensamma parametrar*. Dessa parametrar styrs av PowerShell-motorn. Gemensamma parametrar fungerar alltid på samma sätt. De gemensamma parametrarna är **WhatIf**, **Bekräfta**, **utförlig**, **felsöka**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable**, och **OutBuffer**.

### <a name="recommended-parameter-names"></a>Rekommenderade parameternamn

PowerShell core-cmdletarna använda standardnamn för liknande parametrar. Användningen av dessa standardnamn tillämpas inte, men det finns explicita vägledning för att uppmuntra standardisering.

Till exempel rekommenderade namnet för en parameter som refererar till en dator är **ComputerName**, i stället för Server, värden, System, noden eller andra vanliga alternativ. Andra viktiga rekommenderade parameternamn är **kraft**, **undanta**, **inkludera**, **PassThru**, **sökväg**, och **CaseSensitive**.
