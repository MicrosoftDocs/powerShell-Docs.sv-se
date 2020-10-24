---
ms.date: 02/03/2020
keywords: PowerShell, Core
title: Kända problem för PowerShell 6,0
description: Detta är en sammanfattning av kända problem eller begränsningar i PowerShell 6
ms.openlocfilehash: 528315eff660167513045542227dce335355a7b8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501685"
---
# <a name="known-issues-for-powershell-60"></a>Kända problem för PowerShell 6,0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Kända problem för PowerShell på plattformar som inte kommer från Windows

Alpha-versioner av PowerShell på Linux och macOS är huvudsakligen funktionella men har några viktiga begränsningar och användbarhets problem. Beta versioner av PowerShell på Linux och macOS är mer funktionella och stabila än alpha-versioner, men det kan fortfarande finnas en uppsättning funktioner och kan innehålla buggar. I vissa fall är de här problemen bara buggar som ännu inte har åtgärd ATS. I andra fall (som Standardalias för LS, CP osv.) söker vi efter feedback från communityn angående de val vi gör.

Obs! på grund av likheter av många underliggande under system är PowerShell på Linux och macOS att dela samma nivå av mognad i både funktioner och buggar. Förutom vad som anges nedan gäller problemen i det här avsnittet för båda operativ systemen.

### <a name="case-sensitivity-in-powershell"></a>Skift läges känslighet i PowerShell

Tidigare har PowerShell varit enhetligt Skift läges okänsligt, med några undantag. På UNIX-liknande operativ system är fil systemet främst Skift läges känsligt och PowerShell följer standard i fil systemet. Detta visas på flera olika sätt, uppenbara och icke-uppenbara.

#### <a name="directly"></a>Direkt

- När du anger en fil i PowerShell måste du använda rätt Skift läge.

#### <a name="indirectly"></a>Indirekt

- Om ett skript försöker läsa in en modul och modulnamnet inte bokstäver korrekt, Miss lyckas inläsningen av modulen. Detta kan orsaka ett problem med befintliga skript om namnet som modulen refererar till inte stämmer överens med det faktiska fil namnet.
- Fliken slut för ande slutförs inte automatiskt om fil namns fallet är fel. Fragmentet som ska slutföras måste vara bokstäver korrekt. (Slut för ande är inte Skift läges känsligt för typnamn och typ av medlems komplettering.)

### <a name="ps1-file-extensions"></a>. PS1 fil namns tillägg

PowerShell-skript måste sluta i `.ps1` för att tolkaren ska förstå hur de ska läsas in och köras i den aktuella processen. Att köra skript i den aktuella processen är det förväntade vanliga beteendet för PowerShell. `#!`Magic number kan läggas till i ett skript som inte har något `.ps1` tillägg, men det gör att skriptet kan köras i en ny PowerShell-instans som förhindrar att skriptet fungerar som det ska när de byter objekt. (OBS! detta kan vara det önskvärda beteendet när du kör ett PowerShell `bash` -skript från eller ett annat gränssnitt.)

### <a name="missing-command-aliases"></a>Kommando Ali Aset saknas

På Linux/MacOS är "bekvämlighets Ali Asets" för de grundläggande kommandona,,,,,, `ls` `cp` , som `mv` `rm` `cat` `man` `mount` `ps` har tagits bort. I Windows tillhandahåller PowerShell en uppsättning alias som mappar till Linux-kommando namn för användar bekvämlighet. Dessa alias har tagits bort från standard PowerShell på Linux/macOS-distributioner, vilket gör att den ursprungliga körbara filen kan köras utan att ange en sökväg.

Det finns för-och nack delar med att göra detta. Om du tar bort alias exponeras den inbyggda kommando upplevelsen för PowerShell-användaren, men funktionaliteten i gränssnittet minskas eftersom de interna kommandona returnerar strängar i stället för objekt.

> [!NOTE]
> Det här är ett utrymme där PowerShell-teamet söker efter feedback. Vilken är den bästa lösningen?
> Ska vi lämna den som den är eller lägga till bekvämlighets Ali Aset igen? Se [problem #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Stöd för jokertecken saknas (globbing)

För närvarande stöder PowerShell endast globbing (jokertecken) för inbyggda cmdlets i Windows och för externa kommandon eller binärfiler, samt cmdlets i Linux. Det innebär att ett kommando som till exempel `ls
*.txt` Miss lyckas eftersom asterisken inte är expanderad för att matcha fil namn. Du kan undvika detta genom att göra `ls (gci *.txt | % name)` eller, mer enkelt, `gci *.txt` använda den inbyggda PowerShell-motsvarigheten till `ls` .

Se [#954](https://github.com/PowerShell/PowerShell/issues/954) för att ge oss feedback om hur du kan förbättra globbing-upplevelsen på Linux/MacOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework vs .NET Core Framework

PowerShell på Linux/macOS använder .NET Core som är en del av den fullständiga .NET Framework på Microsoft Windows. Detta är viktigt eftersom PowerShell ger direkt åtkomst till de underliggande Ramverks typerna, metoderna osv. Det innebär att skript som körs på Windows inte kan köras på plattformar som inte är Windows-plattformar på grund av skillnaderna i ramverken. Mer information om .NET Core Framework finns i [dotnetfoundation.org](https://dotnetfoundation.org/).

Med ankomsten av [.net Standard 2,0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)ger .net Core 2,0 tillbaka många av de traditionella typerna och metoderna i den fullständiga .NET Framework. Det innebär att PowerShell Core kan läsa in många traditionella Windows PowerShell-moduler utan ändringar. Du kan följa våra .NET standard 2,0-relaterade arbeten [här](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Problem med omdirigering

Omdirigering av utdata stöds inte i PowerShell på någon plattform.
[Problem #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Används `Get-Content` för att skriva innehållet i en fil till pipelinen.

Omdirigerade utdata innehåller Unicode-bytets ordnings tecken (BOM) när standard kodningen för UTF-8 används. STRUKTUR listan orsakar problem när du arbetar med verktyg som inte förväntar sig eller när du lägger till i en fil. Används `-Encoding Ascii` för att skriva ASCII-text, som inte har en struktur.

> [!Note]
> Se [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) för att ge oss feedback om hur du kan förbättra kodnings upplevelsen för PowerShell Core på alla plattformar. Vi arbetar med att stödja UTF-8 utan en struktur och kan eventuellt ändra standardvärdena för kodning för olika cmdlets på olika plattformar.

### <a name="job-control"></a>Jobb kontroll

Det finns ingen support för jobb kontroll i PowerShell på Linux/macOS.
`fg` `bg` Kommandona och är inte tillgängliga.

Under tiden kan du använda [PowerShell-jobb](/powershell/module/microsoft.powershell.core/about/about_jobs) som fungerar på alla plattformar.

### <a name="remoting-support"></a>Remoting-support

För närvarande stöder PowerShell Core PowerShell-fjärrkommunikation (PSRP) över WSMan med grundläggande autentisering på macOS och Linux och med NTLM-baserad autentisering på Linux. (Kerberos-baserad autentisering stöds inte.)

Arbetet för WSMan-baserad fjärr kommunikation görs i [PSL-OMI-Provider-](https://github.com/PowerShell/psl-omi-provider) lagrings platsen.

PowerShell Core stöder även PowerShell-fjärrkommunikation (PSRP) via SSH på alla plattformar (Windows, macOS och Linux). Även om detta inte stöds i produktion, kan du lära dig mer om att konfigurera detta [här](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md).

### <a name="just-enough-administration-jea-support"></a>JEA-stöd (just-otillräckligt administration)

Möjligheten att skapa Fjärrslutpunkter för fjärran sluten administration (JEA) är för närvarande inte tillgänglig i PowerShell på Linux/macOS. Den här funktionen är för närvarande inte inom omfånget för 6,0 och något vi tar upp efter 6,0 eftersom det kräver betydande design arbete.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` , och PowerShell

Eftersom PowerShell kör de flesta kommandon i minnet (t. ex. python eller ruby) kan du inte använda sudo direkt med inbyggda PowerShell-moduler. (Du kan naturligtvis köra `pwsh` från sudo.) Om det är nödvändigt att köra en PowerShell-cmdlet från PowerShell med sudo, till exempel, `sudo Set-Date 8/18/2016` kan du göra det `sudo pwsh Set-Date 8/18/2016` . På samma sätt kan du inte exekvera en inbyggd PowerShell-modul direkt. I stället måste du göra det `exec pwsh item_to_exec` .

Det här problemet spåras som en del av [#3232](https://github.com/PowerShell/PowerShell/issues/3232).

### <a name="missing-cmdlets"></a>Cmdletar som saknas

Ett stort antal kommandon (cmdlets) som normalt är tillgängliga i PowerShell är inte tillgängliga på Linux/macOS. I många fall är dessa kommandon inte begripliga på dessa plattformar (t. ex. Windows-/regionsspecifika funktioner som registret). Andra kommandon som Service Control-kommandona (Get/Start/Stop-service) finns, men fungerar inte. Framtida versioner kan åtgärda problemen genom att åtgärda de brutna cmdletarna och lägga till nya över tid.

### <a name="command-availability"></a>Kommando tillgänglighet

I följande tabell visas kommandon som är kända för att inte fungera i PowerShell på Linux/macOS.

|Kommandon|Användnings tillstånd|Anteckningar|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Inte tillgängligt.|Dessa kommandon känns inte igen. Detta bör åtgärdas i en framtida version.|
|`Get-Acl`, `Get-AuthenticodeSignature`, `Get-CmsMessage`, `New-FileCatalog`, `Protect-CmsMessage`, `Set-Acl`, `Set-AuthenticodeSignature`, `Test-FileCatalog`, `Unprotect-CmsMessage`|Inte tillgängligt.|Dessa kommandon känns inte igen. Detta bör åtgärdas i en framtida version.|
|`Wait-Process`|Tillgängligt, fungerar inte korrekt. |Till exempel `Start-Process gvim -PassThru | Wait-Process` fungerar inte. det går inte att vänta på processen.|
|`Connect-PSSession`, `Disable-PSRemoting`, `Disable-PSSessionConfiguration`, `Disconnect-PSSession`, `Enable-PSRemoting`, `Enable-PSSessionConfiguration`, `Get-PSSessionCapability`, `Get-PSSessionConfiguration`, `New-PSSessionConfigurationFile`, `Receive-PSSession`, `Register-PSSessionConfiguration`, `Set-PSSessionConfiguration`, `Test-PSSessionConfigurationFile`, `Unregister-PSSessionConfiguration`|Inte tillgängligt.|Dessa kommandon känns inte igen. Detta bör åtgärdas i en framtida version.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Remove-Event`, `Unregister-Event`|Tillgängligt, men inga händelse källor är tillgängliga.|PowerShell Eventing-kommandona finns men de flesta händelse källor som används med kommandona (t. ex. system. timers. timer) är inte tillgängliga i Linux och gör kommandona oanvändbara i alpha-versionen.|
|`Set-ExecutionPolicy`|Tillgängligt men fungerar inte.|Returnerar ett meddelande som säger att det inte stöds på den här plattformen. Körnings principen är en fokuserad "säkerhetsbälte" som hindrar användaren från att göra kostsamma misstag. Det är ingen säkerhets gränser.|
|`New-PSSessionOption`, `New-PSTransportOption`|Tillgängligt men `New-PSSession` fungerar inte.|`New-PSSessionOption` och `New-PSTransportOption` är för närvarande inte verifierade för att fungera nu `New-PSSession` .|
