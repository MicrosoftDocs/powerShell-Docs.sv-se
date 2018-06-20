---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd bekanta kommandonamn
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 37fc6dfad5a2f1363254744141dcab1e13aa5066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952689"
---
# <a name="using-familiar-command-names"></a>Använd bekanta kommandonamn
Med hjälp av en mekanism kallas *alias*, Windows PowerShell kan du referera till kommandon med alternativa namn. Alias kan användare upplevelse i andra tankar återanvända vanliga kommandonamn som de redan känner till att utföra samma åtgärder i Windows PowerShell. Även om vi inte upp Windows PowerShell-alias i detalj, kan du fortfarande använda dem när du kommer igång med Windows PowerShell.

Alias associerar ett kommandonamn som du skriver med ett annat kommando. Windows PowerShell har till exempel en intern funktion med namnet **rensa värden** som rensar utdatafönstret. Om du skriver en den **cls** eller **Rensa** kommando i Kommandotolken Windows PowerShell tolkar att detta är ett alias för den **rensa värden** fungerar och körs på  **Rensa värden** funktion.

Den här funktionen hjälper användarna att lära sig Windows PowerShell. Först och de flesta Cmd.exe- och UNIX-användare har en stor kan representeras av kommandon som användare redan känner till namnet och även om Windows PowerShell-motsvarigheter inte kanske ger samma resultat, de är nära i formuläret som användarna kan använda dem till fungerar utan att behöva först ska du komma ihåg Windows PowerShell-namn. Andra är viktiga källan för genomförande Lär dig ett nytt gränssnitt när användaren redan är bekant med en annan shell de fel som orsakas av ”fingeravtrycksläsare minne”. Om du har använt Cmd.exe år när du har en skärm fullständig av utdata och vill rensa den, skriver du reflexively den **cls** kommando och tryck på Enter. Utan alias till den **rensa värden** funktion i Windows PowerShell kan du bara skulle få felmeddelandet ”**'cls-identifieras inte som en cmdlet, funktion, körbart program eller en skriptfil.**” och lämnas med ingen uppfattning om vad du gör att rensa utdata.

Här följer en kort lista över vanliga Cmd.exe- och UNIX-kommandon som du kan använda i Windows PowerShell:

|||||
|-|-|-|-|
|cat|dir|Montera|RM|
|cd|echo|Flytta|rmdir|
|chdir|Radera|popd|strömsparläge|
|Rensa|h|ps|sort|
|CLS|Historik|pushd|Tee|
|Kopiera|Avsluta|pwd|typ|
|del|LP|r|skriva|
|diff|Ls|ren||

Om du använder något av följande kommandon reflexively och vill veta det verkliga namnet på det interna Windows PowerShell-kommandot kan du använda den **Get-Alias** kommando:

```
PS> Get-Alias cls

CommandType     Name                            Definition
-----------     ----                            ----------
Alias           cls                             Clear-Host
```

Om du vill göra exempel mer lättläst undviker i användarhandboken för Windows PowerShell vanligtvis använder alias. Om du vet mer om alias kan detta tidigt dock fortfarande vara användbart om du arbetar med godtycklig kodavsnitt för Windows PowerShell-kod från en annan källa eller om du vill definiera egna alias. Resten av det här avsnittet innehåller information om standard alias och hur du definierar din egen alias.

### <a name="interpreting-standard-aliases"></a>Tolka Standard alias
Till skillnad från de alias som beskrivs ovan, och som har utformats för namn-kompatibilitet med andra gränssnitt, är de alias som är inbyggd i Windows PowerShell vanligtvis utformade för planeringsaspekter. Dessa kortare namn kan skrivas snabbt, men det är omöjligt att läsa om du inte vet vad de refererar till.

Windows PowerShell försöker att kompromissa mellan tydlighetens skull och planeringsaspekter genom att tillhandahålla en uppsättning standard alias som är baserade på shorthand namn för vanliga verb och substantiv. På så sätt kan en grundläggande uppsättning alias för vanliga cmdletar som är läsbart när du vet shorthand namn. Till exempel i standard alias verbet **hämta** är förkortas **g**, verbet **ange** är förkortas **s**, substantiv **Objektet** är förkortas **jag**, substantivet **plats** är förkortas **l**, och substantiv kommandot är förkortas **cm**.

Här är ett exempel som illustrerar hur det fungerar. Standard-alias för Get-objekt som kommer från kombinera **g** för Get och **jag** för objektet: **gi**. Standard-alias för Set-objekt som kommer från kombinera **s** för och **jag** för objektet: **si**. Standard-alias för Get-plats som kommer från kombinera **g** för Get och **l** för plats **huvudbok**. Standard-alias för Set-Location kommer från kombinera **s** för och **l** för plats **sl**. Standard-alias för Get-Command kommer från kombinera **g** för Get och **cm** för kommandot **gcm**. Det finns inga kommandot Set-cmdlet, men om det fanns det skulle kunna tror att aliaset som standard kommer från **s** för och **cm** för kommandot: **scm**. Dessutom personer bekant med Windows PowerShell-alias som uppstår **scm** skulle kunna gissa som alias refererar till kommandot Set.

### <a name="creating-new-aliases"></a>Skapa nytt alias
Du kan skapa egna alias med cmdlet Set-Alias. Till exempel skapa följande påståenden standard cmdlet-alias som beskrivs i tolka Standard alias:

```
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internt Windows PowerShell använder kommandon som dessa under starten, men dessa alias är inte kan ändras. Om du försöker att köra något av följande kommandon får du ett felmeddelande om att aliaset som inte kan ändras. Till exempel:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```