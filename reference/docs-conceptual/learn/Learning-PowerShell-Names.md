---
ms.date: 08/24/2018
keywords: PowerShell, cmdlet
title: Kommando namn för Learning PowerShell
ms.openlocfilehash: a65ffcdca6510093b0a77234e20546b6cc1f02bf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030427"
---
# <a name="learning-powershell-command-names"></a>Kommando namn för Learning PowerShell

Inlärnings namn för kommandon och parametrar kräver en betydande tids investering med de flesta kommando rads gränssnitt. Problemet är att det finns några mönster. Detta är det enda sättet att lära sig de kommandon och parametrar som du behöver använda regelbundet.

När du arbetar med ett nytt kommando eller parameter kan du inte alltid använda det du redan känner till. Du måste hitta och lära dig ett nytt namn. Traditionellt är kommando rads gränssnitt som börjar med en liten uppsättning verktyg och växer med stegvisa tillägg. Det är enkelt att se varför det inte finns någon standard struktur.
Detta verkar logiskt för kommando namn eftersom varje kommando är ett separat verktyg. PowerShell har ett bättre sätt att hantera kommando namn.

## <a name="learning-command-names-in-traditional-shells"></a>Inlärnings kommando namn i traditionella gränssnitt

De flesta kommandon är utformade för att hantera element i operativ systemet eller program, t. ex. tjänster eller processer. Kommandona har namn som kanske inte passar in i en familj. I Windows-system kan du till exempel använda kommandona `net start` och `net stop` för att starta och stoppa en tjänst. **SC. exe** är ett annat tjänst kontroll verktyg för Windows. Namnet passar inte in i namngivnings mönstret för **net. exe** -tjänstens kommandon. För process hantering har Windows kommandot **Tasklist. exe** för att visa en lista över processer och kommandot **taskkill. exe** för att avsluta processer.

Dessa kommandon har också oregelbundna parameter specifikationer. Du kan inte använda kommandot `net start` för att starta en tjänst på en fjärrdator. Kommandot **SC. exe** kan starta en tjänst på en fjärrdator. Men för att ange fjärrdatorn måste du ange ett prefix för namnet med ett dubbelt omvänt snedstreck. Om du vill starta Spooler-tjänsten på en fjärrdator med namnet DC01 skriver du `sc.exe \\DC01 start spooler`.
Om du vill visa en lista över aktiviteter som körs på DC01 använder du parametern **/s** och dator namnet utan omvänt snedstreck. Till exempel `tasklist /S DC01`.

> [!NOTE]
> Före PowerShell V6 var `sc` ett alias för `Set-Content`-cmdleten. För att köra kommandot **SC. exe** i en version av PowerShell före V6 måste du därför inkludera det fullständiga fil namnet **SC. exe** , inklusive fil namns tillägget **exe**.

Tjänster och processer är exempel på hanterbara element på en dator som har väldefinierade livs cykel cyklar. Du kan starta eller stoppa tjänster och processer eller hämta en lista över alla tjänster eller processer som körs. Även om det finns viktiga tekniska skillnader mellan dem, är de åtgärder som du utför på tjänster och processer konceptuellt desamma. Dessutom kan de val vi gör för att anpassa en åtgärd genom att ange parametrar vara konceptuellt lika bra.

PowerShell utnyttjar dessa likheter för att minska antalet distinkta namn som du behöver känna till för att förstå och använda cmdlets.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Cmdlet: ar använder verb-Substantiv-namn för att minimera kommandots-subst

PowerShell använder namngivnings systemet "verb-Substantiv". Varje cmdlet-namn består av ett standard-verb avstavat med ett bestämt substantiv. PowerShell-verb är inte alltid engelska verb, utan de uttrycker vissa åtgärder i PowerShell. Substantiv är mycket likt Substantiv på valfritt språk. De beskriver vissa typer av objekt som är viktiga för system administration. Det är enkelt att visa hur dessa namn på två delar minskar inlärnings ansträngningen genom att titta på några exempel.

PowerShell har en rekommenderad uppsättning standard-verb. Substantiv är mindre begränsade, men beskriver alltid vad verbet agerar på. PowerShell har kommandon som `Get-Process`, `Stop-Process`, `Get-Service`och `Stop-Service`.

I det här exemplet på två Substantiv och verb fören klar konsekvensen inte inlärningen mycket. Utöka listan till en standardiserad uppsättning med 10 verb och 10 substantiv. Nu har du bara 20 ord att förstå.
Men dessa ord kan kombineras med formatet 100 distinkta kommando namn.

Det är enkelt att förstå vad ett PowerShell-kommando gör genom att läsa dess namn. Kommandot för att stänga av en dator är `Stop-Computer`. Kommandot för att visa en lista över alla datorer i ett nätverk är `Get-Computer`. Kommandot för att hämta system datumet är `Get-Date`.

Du kan visa alla kommandon som innehåller ett visst verb med parametern **verb** för `Get-Command`. Om du till exempel vill visa alla cmdletar som använder verbet `Get`skriver du:

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

Använd parametern **Substantiv** för att se en serie kommandon som påverkar samma typ av objekt. Kör till exempel följande kommando för att se vilka kommandon som är tillgängliga för hantering av tjänster:

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

## <a name="cmdlets-use-standard-parameters"></a>Cmdlets använder standard parametrar

Som tidigare nämnts har kommandon som används i traditionella kommando rads gränssnitt inte alltid konsekventa parameter namn. Parametrar är ofta enkla eller förkortade ord som är lätta att skriva, men som inte är lätta att förstå för nya användare.

Till skillnad från de flesta andra traditionella kommando rads gränssnitt, bearbetar PowerShell parametrar direkt och den använder direkt åtkomst till parametrarna tillsammans med vägledning för utvecklare för att standardisera parameter namn. Den här vägledningen uppmuntrar men garanterar inte att varje cmdlet följer standarden.

PowerShell standardiserar också parameter avgränsaren. Parameter namn har alltid en-anpassningsprefix till dem med ett PowerShell-kommando. Se följande exempel:

```powershell
Get-Command -Name Clear-Host
```

Parameterns namn är **ett namn**, men det anges som `-Name` när det används på kommando raden som en parameter.

Här följer några allmänna egenskaper för standard parameter namn och-användning.

### <a name="the-help-parameter-"></a>Parametern Help (?)

När du anger parametern `-?` för alla cmdletar visar PowerShell hjälp för cmdleten.
Cmdleten körs inte.

### <a name="common-parameters"></a>Vanliga parametrar

PowerShell har flera *vanliga parametrar*. Dessa parametrar styrs av PowerShell-motorn. Vanliga parametrar fungerar alltid på samma sätt. De gemensamma parametrarna är **whatIf**, **Confirm**, **verbose**, **Debug**, **Warning**, **ErrorAction**, **ErrorVariable**, **devariable**och **utbuffer**.

### <a name="recommended-parameter-names"></a>Rekommenderade parameter namn

PowerShell Core-cmdletar använder standard namn för liknande parametrar. Användningen av dessa standard namn är inte tvingande, men det finns uttryckliga rikt linjer för att uppmuntra standardisering.

Till exempel är det rekommenderade namnet för en parameter som refererar till en dator **computername**, i stället för Server, värd, system, nod eller något annat vanligt alternativ. Andra viktiga rekommenderade parameter namn är **Force**, **exclude**, **include**, **Passthru**, **Path**och **caseSensitive**.
