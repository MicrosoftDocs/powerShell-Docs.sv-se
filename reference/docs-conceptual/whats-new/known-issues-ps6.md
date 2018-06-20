---
ms.date: 05/17/2018
keywords: PowerShell, kärnor
title: Kända problem för PowerShell 6.0
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309584"
---
# <a name="known-issues-for-powershell-60"></a>Kända problem för PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Kända problem för PowerShell på Windows-plattformar

Alpha versioner av PowerShell på Linux- och macOS är främst funktionella men har några viktiga begränsningar och problem med användningen. Beta versioner av PowerShell på Linux- och macOS är mer stabilt och än alfanumeriska versioner, men fortfarande saknas vissa uppsättning funktioner och kan innehålla buggar. I vissa fall kan är problemen helt enkelt buggar som ännu inte har åtgärdats. I annat fall (som med standardalias för ls cp etc.) vi letar efter feedback från gemenskapen om de val som vi gör.

Obs: På grund av likheter många underliggande delsystem PowerShell på Linux- och macOS tenderar att dela samma nivå av förfall i både funktioner och programfel. Utöver vad som anges nedan problem i det här avsnittet gäller för båda operativsystemen.

### <a name="case-sensitivity-in-powershell"></a>Skiftlägeskänslighet i PowerShell

PowerShell har tidigare varit enhetligt skiftlägesoberoende med några undantag. Filsystemet är skiftlägeskänsligt huvudsakligen på UNIX-liknande operativsystem och PowerShell följer standard för filsystemet. Detta är åtkomlig via en mängd sätt, tydligare och icke-uppenbara.

#### <a name="directly"></a>direkt

- När du anger en fil i PowerShell måste gemener användas.

#### <a name="indirectly"></a>Indirekt

- Om ett skript som försöker läsa in en modul och modulens namn är inte alltid i korrekt belastningen modulen kommer att misslyckas. Detta kan orsaka problem med befintliga skript om namnet som modulen refereras inte matchar det faktiska filnamnet.
- Fliken slutförande kommer inte automatisk komplettering om gemener filen är felaktig. Fragment ska slutföras måste alltid korrekt. (Slutförande är skiftlägeskänsliga för typnamn och typ medlem slutföranden.)

### <a name="ps1-file-extensions"></a>. Ps1 Filnamnstillägg

PowerShell-skript måste sluta med `.ps1` för tolken att förstå hur du ladda och köra dem i den aktuella processen. Köra skript i den aktuella processen är den vanliga förväntat för PowerShell. Den `#!` Magiskt tal kan läggas till ett skript som inte har en `.ps1` tillägget, men det gör att skriptet ska köras i en ny PowerShell-instans som förhindrar att skriptet fungerar korrekt när märkningar objekt. (Obs: Detta kan vara önskvärt beteendet när du kör ett PowerShell-skript från `bash` eller en annan shell.)

### <a name="missing-command-aliases"></a>Saknas kommandot alias

På Linux/macOS ”bekvämlighet alias” för de grundläggande kommandona `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` har tagits bort. För Windows innehåller PowerShell en uppsättning alias som mappas till Linux kommandonamn för användaren. Dessa alias har tagits bort från standard PowerShell på Linux/macOS distributioner, så att den interna körbara filen kan köras utan att ange en sökväg.

Det finns för- och nackdelar i den här. Ta bort alias exponerar interna kommando-upplevelse för PowerShell-användare, men minskar funktioner i gränssnittet eftersom kommandona interna returnerar strängar i stället för objekt.

> [!NOTE]
> Detta är ett område där PowerShell-teamet är ute efter feedback.
> Vad är den bästa lösningen? Vi lämna den som den är eller lägga till alias bekvämlighet tillbaka? Se [utfärda #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Saknas (globbing) stöd för jokertecken

För närvarande stöder PowerShell endast jokertecken expandering (globbing) för inbyggda cmdlet: ar i Windows och externa kommandon eller binärfiler samt på Linux-cmdlets. Det innebär att ett kommando som `ls
*.txt` kommer att misslyckas eftersom asterisken inte kommer att expanderas för att matcha namn. Du kan undvika detta genom att göra `ls (gci *.txt | % name)` eller fler bara `gci *.txt` med hjälp av PowerShell inbyggda motsvarar `ls`.

Se [#954](https://github.com/PowerShell/PowerShell/issues/954) gärna ge oss feedback på hur vi kan förbättra upplevelsen globbing på Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework vs .NET Core Framework

PowerShell på Linux/macOS använder .NET Core, som är en delmängd av fullständig .NET Framework i Microsoft Windows. Detta är viktig eftersom PowerShell ger direktåtkomst till det underliggande framework-typer, metoder och så vidare. Därför kan skript som körs på Windows inte köras på Windows-plattformar på grund av skillnader i ramverk. Läs mer om .NET Core Framework <https://dotnetfoundation.org/net-core>

Med ankomsten av [.NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 kommer att få tillbaka många av de traditionella typer och metoder som finns i fullständig .NET Framework. Det innebär att PowerShell Core kommer att kunna läsa in flera traditionella Windows PowerShell-moduler utan modifiering. Du kan följa våra .NET Standard 2.0 relaterat arbete [här](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Omdirigering av problem

Omdirigering av indata stöds inte i PowerShell på valfri plattform.
[Problemet #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Använd `Get-Content` att skriva innehållet i en fil till pipeline.

Omdirigerade utdata innehåller Unicode-byte-ordningsmarkering (BOM) när standard UTF-8-kodning används. Strukturen medför problem när du arbetar med verktyg som du inte räknar eller bifoga en fil. Använd `-Encoding Ascii` att skriva ASCII-text (som inte är Unicode, inte har en struktur). (Observera: se [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) gärna ge oss feedback om förbättring kodning upplevelsen för PowerShell Core alla plattformar. Vi är arbetar till stöd för UTF-8 utan en struktur och vilket kan påverka kodning standardvärdena för olika cmdlet: ar för olika plattformar.)

### <a name="job-control"></a>Jobbkontroll

Det finns inget stöd för jobb-kontroll i PowerShell på Linux/macOS.
Den `fg` och `bg` kommandon är inte tillgängliga.

För närvarande kan du använda [PowerShell jobb](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) som fungerar på alla plattformar.

### <a name="remoting-support"></a>Stöd för fjärrkommunikation

För närvarande stöder PowerShell Core PowerShell fjärrkommunikation (PSRP) via WSMan med grundläggande autentisering i macOS och Linux, samt med NTLM-autentisering på Linux. (Kerberos-autentisering stöds inte.)

Arbetet för WSMan-baserad fjärrkörning utförs den [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) lagringsplatsen.

PowerShell Core stöder även PowerShell fjärrkommunikation (PSRP) via SSH på alla plattformar (Windows, Linux och macOS). När detta inte stöds för närvarande i produktion, kan du läsa mer om hur du konfigurerar detta [här](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Stöd för just-tillräckligt-Administration (JEA)

Möjligheten att skapa begränsad administration (JEA)-fjärrkommunikation slutpunkter är inte tillgängliga i PowerShell på Linux/macOS. Den här funktionen är för närvarande inte i omfånget för 6.0 och något som vi beaktas post 6.0 eftersom den kräver betydande arbete.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`, och PowerShell

Eftersom de flesta kommandon körs i PowerShell i minnet (till exempel Python eller Ruby), kan du inte använda sudo direkt med PowerShell built-ins. (Du kan naturligtvis köra `powershell` från sudo.) Om det är nödvändigt att köra en PowerShell-cmdlet i PowerShell med sudo, till exempel `sudo Set-Date 8/18/2016`, och sedan gör du `sudo powershell Set-Date 8/18/2016`. På samma sätt du kan inte exec en inbyggd PowerShell direkt. I stället skulle du behöva göra `exec powershell item_to_exec`.

Det här problemet spåras som en del av #3232.

### <a name="missing-cmdlets"></a>Cmdlet: ar som saknas

Ett stort antal (cmdlets) normalt tillgängliga kommandon i PowerShell är inte tillgängliga på Linux/macOS. I många fall gör dessa kommandon meningslös på dessa plattformar (t.ex. Windows-specifika funktioner som registret). Andra kommandon som service control-kommandon (Get/Start/Stop-Service) finns, men fungerar inte. Kommande versioner kan korrigera problemen korrigerat brutna cmdlet: ar och lägger till nya över tid.

### <a name="command-availability"></a>Tillgängliga kommandon

I följande tabell visas kommandon som inte fungerar i PowerShell på Linux/macOS.

<table>
<th>Kommandon</th><th>Användningsstatus</th><th>Obs!</th>
<tr>
<td>Get-Service, ny tjänst, starta om tjänsten, återuppta tjänsten, Set-tjänst, Start-Service, Stop-Service, pausa tjänsten
<td>Inte tillgänglig.
<td>Dessa kommandon känns inte igen. Detta bör åtgärdas i en framtida version.
</tr>
<tr>
<td>Get-Acl, Set-Acl
<td>Inte tillgänglig.
<td>Dessa kommandon känns inte igen. Detta bör åtgärdas i en framtida version.
</tr>
<tr>
<td>Get-AuthenticodeSignature, Set-AuthenticodeSignature
<td>Inte tillgänglig.
<td>Dessa kommandon känns inte igen. Detta bör åtgärdas i en framtida version.
</tr>
<tr>
<td>Vänta-Process
<td>Tillgänglig, fungerar inte korrekt. <td>Till exempel `Start-Process gvim -PassThru | Wait-Process` fungerar inte; det inte går att vänta tills processen.
</tr>
<tr>
<td>Register-PSSessionConfiguration, avregistrera-PSSessionConfiguration, Get-PSSessionConfiguration
<td>Tillgängliga men fungerar inte.
<td>Skriver ett felmeddelande om att kommandona inte fungerar. Dessa bör åtgärdas i en framtida version.
</tr>
<tr>
<td>Get-händelse, ny händelse, registrera EngineEvent, Register-WmiEvent, ta bort händelsen avregistrera händelse
<td>Det finns tillgänglig men ingen händelsekällor.
<td>PowerShell eventing-kommandon finns men de flesta av de händelsekällor som används med kommandon (till exempel System.Timers.Timer) är inte tillgängliga på Linux gör kommandona oanvändbar i Alpha-versionen.
</tr>
<tr>
<td>Set-ExecutionPolicy
<td>Tillgängliga men fungerar inte.
<td>Returnerar meddelandet stöds inte på den här plattformen. Utförandepolicyn är en användare fokuserar ”inbyggd” som förhindrar att användaren gör dyra misstag. Det är inte en säkerhetsgräns.
</tr>
<tr>
<td>Ny PSSessionOption, nya PSTransportOption
<td>Tillgänglig men New-PSSession fungerar inte.
<td>Ny PSSessionOption och ny PSTransportOption verifieras inte för närvarande fungerar nu när New-PSSession fungerar.
</tr>
</table>
