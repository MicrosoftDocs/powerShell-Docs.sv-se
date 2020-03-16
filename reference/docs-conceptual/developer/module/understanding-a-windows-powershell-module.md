---
title: Förstå en Windows PowerShell-modul | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79406932"
---
# <a name="understanding-a-windows-powershell-module"></a>Förstå en Windows PowerShell-modul

En *modul* är en uppsättning relaterade Windows PowerShell-funktioner, grupperade tillsammans som en lämplig enhet (vanligt vis sparas i en enda katalog). Genom att definiera en uppsättning relaterade skriptfiler, sammansättningar och relaterade resurser som en modul kan du referera, läsa in, Spara och dela din kod mycket enklare än du annars skulle göra.

Huvud syftet med en modul är att tillåta modularization (IE, åter användning och abstraktion) av Windows PowerShell-kod. Det enklaste sättet att skapa en modul är till exempel att bara spara ett Windows PowerShell-skript som en. psm1-fil. På så sätt kan du kontrol lera (IE, göra offentliga eller privata) de funktioner och variabler som finns i skriptet. Genom att spara skriptet som en. psm1-fil kan du också styra omfattningen för vissa variabler. Slutligen kan du också använda cmdlets som [install-module](/powershell/module/PowershellGet/Install-Module) för att ordna, installera och använda ditt skript som bygg stenar för större lösningar.

## <a name="module-components-and-types"></a>Modulens komponenter och typer

En modul består av fyra grundläggande komponenter:

1. Viss sorts kod fil – vanligt vis ett PowerShell-skript eller en hanterad cmdlet-sammansättning.

2. Något annat som ovanstående kod fil kan behöva, till exempel ytterligare sammansättningar, hjälp filer eller skript.

3. En manifest fil som beskriver ovanstående filer, samt lagrar metadata som författare och versions information.

4. En katalog som innehåller allt innehåll som anges ovan och finns där PowerShell kan rimligen hitta den.

   Observera att ingen av dessa komponenter själva är nödvändig. En modul kan till exempel vara tekniskt sett bara ett skript lagrat i en. psm1-fil. Du kan också ha en modul som är Nothing men en manifest fil som används huvudsakligen för organisations syfte. Du kan också skriva ett skript som dynamiskt skapar en modul, och eftersom sådana inte egentligen behöver en katalog för att lagra något i. I följande avsnitt beskrivs de typer av moduler som du kan hämta genom att blanda och matcha de olika möjliga delarna i en modul tillsammans.

### <a name="script-modules"></a>Skript moduler

Som namnet antyder är en- *skriptbaserad modul* en fil (. psm1) som innehåller en giltig Windows PowerShell-kod. Skript utvecklare och administratörer kan använda den här typen av modul för att skapa moduler vars medlemmar innehåller funktioner, variabler med mera. I hjärtat är en modul helt enkelt ett Windows PowerShell-skript med ett annat tillägg, vilket gör att administratörer kan använda funktionerna import, export och hantering på den.

Dessutom kan du använda en manifest fil för att inkludera andra resurser i modulen, till exempel datafiler, andra beroende moduler eller körnings skript. MANIFEST filer är också användbara för att spåra metadata som till exempel redigering och versions information.

Slutligen måste en skript-modul, precis som andra moduler som inte har skapats dynamiskt, sparas i en mapp som PowerShell kan identifiera. Detta är vanligt vis på PowerShell-modulens sökväg. men om det behövs kan du uttryckligen beskriva var modulen är installerad. Mer information finns i [så här skriver du en PowerShell-modul för skript](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Binära moduler

En *binär modul* är en .NET Framework sammansättning (. dll) som innehåller kompilerad kod, till C#exempel. Cmdlet-utvecklare kan använda den här typen av modul för att dela cmdlets, providrar med mera. (Befintliga snapin-moduler kan också användas som binära moduler.) Jämfört med en skript-modul kan du använda en binär modul för att skapa cmdlets som är snabbare eller använder funktioner (till exempel multitrådning) som inte är lika enkla att koda i Windows PowerShell-skript.

Precis som med skript moduler kan du inkludera en manifest fil för att beskriva ytterligare resurser som din modul använder och för att spåra metadata om modulen. På samma sätt bör du förmodligen installera din binära modul i en mapp någonstans i PowerShell-modulens sökväg. Mer information finns i så här [skriver du en PowerShell-modul för binär](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Manifest-moduler

En *manifest modul* är en modul som använder en manifest fil för att beskriva alla dess komponenter, men som inte har någon typ av kärn sammansättning eller skript. (Formellt, en manifest-modul låter `ModuleToProcess` eller `RootModule` element i manifestet vara tomt.) Du kan dock fortfarande använda andra funktioner i en modul, till exempel möjligheten att läsa in beroende sammansättningar eller automatiskt köra vissa för bearbetnings skript. Du kan också använda en manifest modul som ett bekvämt sätt att paketera upp resurser som andra moduler använder, till exempel kapslade moduler, sammansättningar, typer eller format. Mer information finns i [så här skriver du ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dynamiska moduler

En *dynamisk modul* är en modul som inte har lästs in från eller sparas i en fil. De skapas i stället dynamiskt av ett skript med hjälp av cmdleten [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Den här typen av modul gör det möjligt för ett skript att skapa en modul på begäran som inte behöver läsas in eller sparas i beständig lagring. Av sin natur är en dynamisk modul avsedd att vara kort livs längd och kan därför inte användas av `Get-Module`-cmdlet: en. På samma sätt behöver de vanligt vis inte modul manifest, eller behöver de förmodligen permanenta mappar för att lagra sina relaterade sammansättningar.

## <a name="module-manifests"></a>Modul manifest

Ett *modul manifest* är en. psd1-fil som innehåller en hash-tabell. Nycklarna och värdena i hash-tabellen gör följande saker:

- Beskriv modulens innehåll och attribut.

- Definiera kraven.

- Ta reda på hur komponenterna bearbetas.

  Manifest krävs inte för en modul. Moduler kan referera till skriptfiler (. ps1), skriptfiler (. psm1), MANIFEST filer (. psd1), format och typ filer (. ps1xml), cmdlet-och Provider-sammansättningar (. dll), resursfiler, hjälpfiler, lokaliserings filer eller någon annan typ av fil eller resurs som paketeras som en del av modulen. För ett internationellt skript innehåller mappen module även en uppsättning meddelande katalog filer. Om du lägger till en manifest fil i mappen module kan du referera till flera filer som en enda enhet genom att referera till manifestet.

  Själva manifestet beskriver följande informations kategorier:

- Metadata om modulen, till exempel versions nummer för modulen, författaren och beskrivningen.

- Krav som krävs för att importera modulen, till exempel Windows PowerShell-versionen, Common Language Runtime (CLR) och de nödvändiga modulerna.

- Bearbetning av direktiv, till exempel skript, format och typer som ska bearbetas.

- Begränsningar för medlemmarna i modulen att exportera, till exempel alias, funktioner, variabler och cmdlets som ska exporteras.

  Mer information finns i [så här skriver du ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Lagra och installera en modul

När du har skapat en skript-, binär-eller manifest-modul kan du spara arbetet på en plats som andra kan komma åt. Modulen kan till exempel lagras i systemmappen där Windows PowerShell är installerat, eller så kan den lagras i en användardefinierad mapp.

I allmänhet kan du bestämma var du ska installera modulen genom att använda en av Sök vägarna som lagras i variabeln `$ENV:PSModulePath`. Genom att använda någon av dessa sökvägar kan PowerShell automatiskt hitta och läsa in modulen när en användare gör ett anrop till den i sin kod. Om du lagrar modulen någon annan stans kan du uttryckligen meddela PowerShell genom att skicka in platsen för modulen som en parameter när du anropar `Install-Module`.

Oavsett sökvägen kallas sökvägen för mappen (typen modulebase), och namnet på skriptet, den binära eller manifest-modulens fil ska vara samma som mappens mappnamn, med följande undantag:

- Dynamiska moduler som skapas av `New-Module` cmdlet kan namnges med hjälp av parametern `Name` för cmdleten.

- Moduler som importeras från Assembly-objekt med kommandot **`Import-Module` Assembly** namnges enligt följande syntax: `"dynamic_code_module_" + assembly.GetName()`.

  Mer information finns i [installera en PowerShell-modul](./installing-a-powershell-module.md) och [ändra installations Sök vägen för PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Cmdlets och variabler för moduler

Följande cmdletar och variabler tillhandahålls av Windows PowerShell för att skapa och hantera moduler.

Cmdleten [New-module](/powershell/module/Microsoft.PowerShell.Core/New-Module) denna cmdlet skapar en ny dynamisk modul som bara finns i minnet. Modulen skapas från ett skript block och dess exporterade medlemmar, till exempel dess funktioner och variabler, är omedelbart tillgängliga i sessionen och förblir tillgängliga tills sessionen stängs.

[New-ModuleManifest-](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdleten denna cmdlet skapar en ny modul manifest fil (. psd1), fyller i sina värden och sparar manifest filen på den angivna sökvägen. Den här cmdleten kan också användas för att skapa en modul för modul manifest som kan fyllas i manuellt.

[Import-module-](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet denna cmdlet lägger till en eller flera moduler i den aktuella sessionen.

Cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) denna cmdlet hämtar information om de moduler som har varit eller som kan importeras till den aktuella sessionen.

[Export-ModuleMember-](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet denna cmdlet anger de Modulnamn (t. ex. cmdlets, functions, variabler och alias) som exporteras från en skriptfil (. psm1) eller från en dynamisk modul som skapats med hjälp av `New-Module` cmdlet.

Cmdleten [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) denna cmdlet tar bort moduler från den aktuella sessionen.

[Test-ModuleManifest-](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdleten denna cmdlet kontrollerar att en modul manifestet korrekt beskriver komponenterna i en modul genom att kontrol lera att filerna som anges i modulens manifest fil (. psd1) faktiskt finns i angivna sökvägar.

$PSScriptRoot den här variabeln innehåller den katalog som används för att köra modulen. Den gör det möjligt för skript att använda-modulens sökväg för att komma åt andra resurser.

$env:P SModulePath denna miljö variabel innehåller en lista över de kataloger där Windows PowerShell-moduler lagras. Windows PowerShell använder värdet för den här variabeln när du importerar moduler automatiskt och uppdaterar hjälp avsnitt för moduler.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
