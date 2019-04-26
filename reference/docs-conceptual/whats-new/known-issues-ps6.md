---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Kända problem för PowerShell 6.0
ms.openlocfilehash: ce40a1925e564fbd2c661e70ec36d3842d915dfe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085974"
---
# <a name="known-issues-for-powershell-60"></a>Kända problem för PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Kända problem för PowerShell på icke-Windows-plattformar

Alpha versioner av PowerShell på Linux och macOS använder huvudsakligen funktionella men har några viktiga begränsningar och användningsproblem. Beta-versioner av PowerShell på Linux och macOS är mer stabilt och än alpha versioner, men fortfarande saknas vissa uppsättning funktioner och kan innehålla buggar. I vissa fall kan är dessa problem helt enkelt buggar som ännu inte har åtgärdats. I annat fall (som med standardalias för ls, cp osv) vi söker efter feedback från diskussionsgruppen om de val som vi gör.

Anm På grund av likheter med många underliggande undersystemen PowerShell på Linux och macOS tenderar att dela samma nivå av mognad vid både funktioner och buggar. Förutom enligt nedan problem i det här avsnittet gäller för båda operativsystemen.

### <a name="case-sensitivity-in-powershell"></a>Skiftlägeskänslighet i PowerShell

Historiskt sett har PowerShell enhetligt skiftlägeskänslig med några undantag. Filsystemet är skiftlägeskänsligt främst på UNIX-liknande operativsystem och PowerShell följer standard för filsystemet. Detta är tillgängliga via en mängd sätt, tydligare och icke-uppenbara.

#### <a name="directly"></a>direkt

- När du anger en fil i PowerShell, måste du använda rätt skiftläge.

#### <a name="indirectly"></a>Indirekt

- Om ett skript som försöker läsa in en modul och modulnamnet är inte alltid i korrekt, och sedan läsa in fjärrhanteringsmodulen misslyckas. Detta kan orsaka ett problem med befintliga skript om de namn som modulen refereras inte matchar det faktiska filnamnet.
- Tabbifyllning kommer inte automatisk komplettering om den versaler och gemener är felaktig. Vara måste bokstäver fragment ska slutföras korrekt. (Slutförande är skiftlägeskänsliga för namn och typ av medlem slutföranden.)

### <a name="ps1-file-extensions"></a>. Ps1 Filnamnstillägg

PowerShell-skript måste sluta med `.ps1` för vilken tolk som vill lära dig att läsa in och kör dem i den aktuella processen. Köra skript i den aktuella processen är förväntat vanligt beteende för PowerShell. Den `#!` Magiskt tal kan läggas till i ett skript som inte har en `.ps1` tillägget, men det leder till skriptet som ska köras i en ny PowerShell-instans som förhindrar att skriptet fungerar korrekt när märkningar objekt. (Obs: Detta kan vara önskvärt beteendet när du kör ett PowerShell-skript från `bash` eller en annan gränssnittet.)

### <a name="missing-command-aliases"></a>Saknas kommando-alias

För Linux/macOS, ”bekvämlighet alias” för de grundläggande kommandona `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` har tagits bort. På Windows innehåller PowerShell en uppsättning av alias som mappas till Linux kommandonamn för att underlätta för användaren. Dessa alias har tagits bort från standard PowerShell på Linux/Mac OS-distributioner, så att den inbyggda körbara filen som ska köras utan att ange en sökväg.

Det finns för- och nackdelar i den här. Ta bort alias visar upplevelsen interna kommando till PowerShell-användare, men minskar funktioner i gränssnittet eftersom inbyggda kommandona returnerar strängar i stället för objekt.

> [!NOTE]
> Det här är ett område där PowerShell-teamet är ute efter feedback.
> Vad är det en bättre lösningen? Ska lämna det som är eller lägga till alias bekvämlighet tillbaka? Se [utfärda #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Jokertecken (globbing) Support som saknas

För närvarande har PowerShell endast jokertecken expansion (globbing) för inbyggda cmdlets på Windows och för externa kommandon eller binärfiler samt cmdletar i Linux. Det innebär att ett kommando som `ls
*.txt` misslyckas eftersom asterisken inte kommer att expanderas för att matcha filnamn. Du kan undvika detta genom att göra `ls (gci *.txt | % name)` eller rättare sagt `gci *.txt` med hjälp av den inbyggda PowerShell-motsvarigheten till `ls`.

Se [#954](https://github.com/PowerShell/PowerShell/issues/954) att ge oss feedback om hur du förbättrar globbing upplevelsen för Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework vs .NET Core Framework

PowerShell för Linux/macOS använder .NET Core som är en delmängd av fullständiga .NET Framework på Microsoft Windows. Det här är viktiga eftersom PowerShell ger direktåtkomst till det underliggande framework-typer, metoder, osv. Därför kan skript som körs på Windows inte köras i icke-Windows-plattformar på grund av skillnader i ramverk. Mer information om .NET Core Framework finns i <https://dotnetfoundation.org/net-core>

Med ankomsten av [.NET Standard2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 kommer att få tillbaka många av de traditionella typer och metoder finns i fullständiga .NET Framework. Det innebär att PowerShell Core kommer att kunna läsa in många traditionella Windows PowerShell-moduler utan modifiering. Du kan följa våra .NET Standard 2.0 motsvarande arbete [här](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Omdirigering av problem

Omdirigering av indata stöds inte i PowerShell på valfri plattform.
[Problemet #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Använd `Get-Content` att innehållet i en fil i pipelinen.

Omdirigerade utdata innehåller Unicode-byte-ordningsmarkering (BOM) när den standard UTF-8-kodning används. Strukturen medför problem när du arbetar med verktyg som inte förväntade det. eller när lägga till en fil. Använd `-Encoding Ascii` att skriva ASCII-text (som inte är Unicode, inte kommer att ha en struktur).

> [!Note]
> Se [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) att ge oss feedback med att förbättra upplevelsen kodning för PowerShell Core på alla plattformar. Vi arbetar på att stöd för UTF-8 utan en struktur och vilket kan påverka kodning standardinställningarna för olika cmdletar mellan plattformar.

### <a name="job-control"></a>Jobbkontroll

Det finns inget stöd för jobb-kontroll i PowerShell på Linux/macOS.
Den `fg` och `bg` kommandon är inte tillgängliga.

För närvarande kan du använda [PowerShell-jobb](/powershell/module/microsoft.powershell.core/about/about_jobs) som fungerar på alla plattformar.

### <a name="remoting-support"></a>Stöd för fjärrkommunikation

PowerShell Core stöder för närvarande PowerShell fjärrkommunikation (PSRP) via WSMan med grundläggande autentisering på macOS och Linux och NTLM-autentisering i Linux. (Kerberos-autentisering stöds inte.)

Arbetet för WSMan-baserad fjärrkörning utförs den [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) lagringsplatsen.

PowerShell Core stöder också PowerShell fjärrkommunikation (PSRP) via SSH på alla plattformar (Windows, macOS och Linux). När detta inte stöds för närvarande i produktion, kan du läsa mer om hur du konfigurerar detta [här](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Stöd för JIT-tillräckligt-Administration (JEA)

Möjligheten att skapa begränsad administration (jea JUST) fjärrkommunikation slutpunkter är inte tillgängliga i PowerShell på Linux/macOS. Den här funktionen är för närvarande inte i omfånget för 6.0 och något betraktar vi post 6.0 eftersom den kräver betydande arbete.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`, och PowerShell

Eftersom de flesta kommandon körs i PowerShell i minnet (till exempel Python eller Ruby) kan använda du inte sudo direkt med PowerShell built-ins. (Du kan naturligtvis köra `pwsh` från sudo.) Om det är nödvändigt att köra en PowerShell-cmdlet i PowerShell med sudo, till exempel `sudo Set-Date 8/18/2016`, och du skulle göra `sudo pwsh Set-Date 8/18/2016`. På samma sätt kan du inte exec en inbyggd PowerShell direkt. I stället skulle du behöva göra `exec pwsh item_to_exec`.

Det här problemet spåras för närvarande som en del av [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Cmdlet: ar som saknas

Ett stort antal (cmdlets) normalt tillgängliga kommandon i PowerShell är inte tillgängliga på Linux/macOS. I många fall meningsfullt kommandona inga för dessa plattformar (t.ex. Windows-specifika funktioner som registret). Andra kommandon som tjänsten kontroll kommandona (Get/Start/Stop-Service) finns, men fungerar inte. Framtida versioner kommer åtgärda dessa problem, Åtgärda bruten cmdlet: ar och lägger till nya över tid.

### <a name="command-availability"></a>Tillgängliga kommandon

I följande tabell visas kommandon som är känt att inte fungerar i PowerShell på Linux/macOS.

|Kommandon|Användningsstatus|Obs!|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Inte tillgängligt.|De här kommandona känns inte igen. Detta bör korrigeras i en framtida version.|
|`Get-Acl`, `Set-Acl`|Inte tillgänglig.|De här kommandona känns inte igen. Detta bör korrigeras i en framtida version.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Inte tillgänglig.|De här kommandona känns inte igen. Detta bör korrigeras i en framtida version.|
|`Wait-Process`|Tillgänglig, fungerar inte korrekt. |Till exempel `Start-Process gvim -PassThru | Wait-Process` fungerar inte; det inte går att vänta tills processen.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Tillgängliga men fungerar inte.|Skriver ett felmeddelande om att kommandona inte fungerar. Dessa bör åtgärdas i en framtida version.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Det finns tillgänglig men inga händelsekällor.|Eventing PowerShell-kommandon finns men de flesta av de händelsekällor används med hjälp av kommandon (till exempel System.Timers.Timer) är inte tillgängligt i Linux gör kommandona oanvändbara i version Alpha.|
|`Set-ExecutionPolicy`|Tillgängliga men fungerar inte.|Returnerar ett meddelande som säger stöds inte på den här plattformen. Utförandepolicyn är en användare designmiljöer ”inbyggd” som hjälper till att förhindra att användaren att dyra misstag. Det är inte en säkerhetsgräns.|
|`New-PSSessionOption`, `New-PSTransportOption`|Tillgängliga men `New-PSSession` fungerar inte.|`New-PSSessionOption` och `New-PSTransportOption` inte för närvarande verifierat för att fungerar som `New-PSSession` fungerar.|
