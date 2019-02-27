---
title: Förstå en Windows PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: 77d328bc1cb8cb42d5a10f107a149c05ab270ce3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851529"
---
# <a name="understanding-a-windows-powershell-module"></a>Förstå en Windows PowerShell-modul

En *modulen* är en uppsättning relaterade funktioner i Windows PowerShell, grupperas tillsammans som en praktisk enhet (vanligtvis sparas i en enskild katalog). Genom att definiera en uppsättning relaterade skriptfiler, sammansättningar och relaterade resurser som en modul kan du referera till, läsa in, spara och dela koden är mycket enklare än du annars skulle behöva.

Det huvudsakliga syftet med en modul är att modulariseringstekniker (återanvändning och abstraktion) av Windows PowerShell-kod. Det enklaste sättet att skapa en modul är till exempel att bara spara ett Windows PowerShell-skript som en .psm1-fil. Detta så kan du ange (d.v.s., kontrollera offentliga eller privata) funktions- och variabler i skriptet. Spara skriptet som en .psm1-fil kan du också styra omfattningen av vissa variabler. Slutligen kan du kan också använda cmdlet: ar som [Install-Module](/powershell/module/PowershellGet/Install-Module) för att organisera, installera och använda ett skript som byggblock för större lösningar.

## <a name="module-components-and-types"></a>Modulen komponenter och typer

En modul består av fyra grundläggande komponenter:

1. Vissa sortera av kodfil – vanligtvis ett PowerShell-skript eller en hanterad cmdlet-sammansättning.

2. Allt annat som ovan kodfilen kanske behöver, till exempel ytterligare sammansättningar hjälp-filer eller skript.

3. En manifestfil som beskriver ovanstående filer, samt lagrar metadada som författare och versionshantering information...

4. En katalog som innehåller alla ovanstående innehållet och om det finns där PowerShell rimligen hittar den.

   Observera att ingen av dessa komponenter, fristående, är faktiskt behövs. En modul kan till exempel tekniskt sett vara ett skript som lagras i en .psm1-fil. Du kan också ha en modul som är något annat än en manifestfil som används huvudsakligen för att organisera. Du kan också skriva ett skript som skapar en modul dynamiskt och därför inte verkligen behöver en katalog kan lagras i. I följande avsnitt beskrivs typerna av moduler som du kan få genom att blanda och matcha olika möjliga delar av en modul tillsammans.

### <a name="script-modules"></a>Skriptmoduler

Som namnet antyder en *skriptmodul* är en fil (.psm1) som innehåller alla giltiga Windows PowerShell-kod. Skriptet utvecklare och administratörer kan använda den här typen av modulen för att skapa moduler vars medlemmar inkludera funktioner och variabler. I hjärtat är en skriptmodul helt enkelt ett Windows PowerShell-skript med ett annat tillägg, där administratörer kan använda funktioner för import, export och hantering på den.

Du kan dessutom använda en manifestfil för att inkludera andra resurser i din modul som datafiler, andra beroende moduler eller runtime-skript. Manifestfiler är också användbara för att spåra metadata, till exempel information om redigering och versionshantering.

Slutligen måste en skriptmodul som andra moduler som inte är dynamiskt skapade, sparas i en mapp som PowerShell rimligen kan identifiera. Detta är vanligtvis, på PowerShell-modulens sökväg; men om det behövs kan uttryckligen beskriver där din modulen är installerad. Mer information finns i [hur du skriver en PowerShell-skript-modul](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Binära moduler

En *binära modulen* är en .NET Framework-sammansättning (.dll) som innehåller kompilerad kod som C#. Cmdlet-utvecklare kan använda den här typen av modulen för att dela cmdlets och providers. (Befintliga snapin-moduler kan också användas som binära moduler.) Jämfört med en skriptmodul, en binär modul kan du skapa cmdletar som är snabbare eller använda funktioner (till exempel flertrådsteknik) som inte är lika enkelt att koden i Windows PowerShell-skript.

Med skriptmoduler, kan som innehålla en manifestfil som beskriver ytterligare resurser som din modul använder och för att spåra metadata om din modul. På samma sätt kan bör förmodligen du installera din binära modul i en mapp någonstans längs PowerShell-modulens sökväg. Läs mer om hur du [hur du skriver en binär PowerShell-modul](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Manifest-moduler

En *manifest modulen* är en modul som använder en manifestfil för att beskriva alla dess komponenter, men inte har någon slags core sammansättningen eller skript. (Kallades tidigare, en manifest modul lämnar den `ModuleToProcess` eller `RootModule` element i manifestet tom.) Du kan fortfarande använda andra funktioner i en modul, till exempel möjligheten att ladda upp beroende sammansättningar eller automatiskt köra vissa förväg bearbetnings-skript. Du kan också använda en manifest modul som ett enkelt sätt att packa upp resurser som andra moduler ska använda, till exempel kapslade moduler, sammansättningar, typer och format. Mer information finns i [hur du skriver en PowerShell-modulen Manifest](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Dynamiska moduler

En *dynamisk modul* är en modul har inte lästs in från eller sparas till en fil. I stället de skapas dynamiskt av ett skript med hjälp av den [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. Den här typen av modulen gör det möjligt för ett skript för att skapa en modul på begäran som inte behöver läsas in eller spara till beständig lagring. Av sin natur, en dynamisk modul är avsedd att vara kortlivade och därför inte kan nås av den `Get-Module` cmdlet. På samma sätt kan de inte behöver vanligtvis modulmanifest eller sannolikt behöver de permanent mappar för att lagra sina relaterade sammansättningar.

## <a name="module-manifests"></a>Modulmanifest

En *modulmanifestet* är en .psd1-fil som innehåller en hash-tabell. Gör du följande nycklar och värden i hash-tabellen:

- Beskriv innehållet och attribut i modulen.

- Definiera kraven.

- Avgör hur komponenterna bearbetas.

  Manifest krävs inte för en modul. Moduler kan referera till skriptfiler (.ps1), skriptfiler modulen (.psm1), manifestfiler (.psd1), formatering och Skriv filer (.ps1xml), cmdlet och providern sammansättningar (.dll), resursfiler, hjälpfiler, lokalisering filer eller någon annan typ av fil eller resurs som finns som en del av modulen. För en internationaliserade skript innehåller modulmappen också en uppsättning meddelandefiler i katalogen. Om du lägger till en manifestfil modulmappen kan referera du flera filer som en enhet genom att referera till manifestet.

  Manifestet själva beskriver följande typer av information:

- Metadata om modulen, exempelvis modulen versionsnummer, författare och beskrivningen.

- Förutsättningar som krävs för att importera modulen, exempelvis Windows PowerShell-version, common language runtime (CLR) version och modulerna som krävs.

- Bearbetning av direktiv, till exempel skript, format och typer att bearbeta.

- Begränsningar för medlemmar av modulen för att exportera, till exempel alias, funktioner, variabler och cmdletar för att exportera.

  Mer information finns i [hur du skriver en PowerShell-modulen Manifest](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Lagra och installerar en modul

När du har skapat ett skript, binär eller manifest-modulen kan spara du ditt arbete på en plats att andra kan komma åt den. Din modul kan till exempel lagras i systemmappen där Windows PowerShell är installerat eller den kan lagras i en användarmapp.

Generellt sett kan du fastställa där bör du installera din modul med hjälp av en av sökvägarna som lagras i den `$ENV:PSModulePath` variabeln. Med hjälp av någon av dessa sökvägar innebär att PowerShell automatiskt kan hitta och läsa in din modul när en användare gör ett anrop till den i koden. Om du sparar din modul någon annanstans, kan du uttryckligen låta PowerShell vet genom att ange platsen för din modul som en parameter när du anropar `Install-Module`.

Oavsett sökvägen till den här mappen kallas den *grundläggande* av modulen (ModuleBase) och namnet på skriptet, binär eller manifest-modulfilen ska vara samma som modulen mappens namn, med följande undantag:

- Dynamiska moduler som skapas av den `New-Module` cmdlet kan namnges med den `Name` parametern för cmdlet.

- Moduler som importeras från sammansättningsobjekt efter den  **`Import-Module` -sammansättningen** kommandot namnges enligt följande syntax: `"dynamic_code_module_" + assembly.GetName()`.

  Mer information finns i [installerar ett PowerShell-modulen](./installing-a-powershell-module.md) och [ändra installationssökvägen PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Modul-cmdlet: ar och variabler

Följande cmdlet: ar och variabler tillhandahålls av Windows PowerShell för skapande och hantering av moduler.

[Ny modul](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet denna cmdlet skapar en ny dynamisk modul finns bara i minnet. Modulen har skapats från ett skriptblock och exporterade medlemmar, till exempel dess funktioner och variabler, är omedelbart tillgängliga i sessionen och är tillgänglig tills sessionen är stängd.

[Ny ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet denna cmdlet skapar en ny fil i modulen manifestfilen (.psd1), fylls dess värden och sparar manifestfilen för den angivna sökvägen. Denna cmdlet kan också användas för att skapa en modul manifest-mall som kan fyllas i manuellt.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet denna cmdlet lägger till en eller flera moduler i den aktuella sessionen.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet denna cmdlet hämtar information om de moduler som har importerats eller som kan importeras till den aktuella sessionen.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet denna cmdlet anger modulen medlemmar (till exempel-cmdlet: ar, funktioner, variabler och alias) som exporteras från en skriptfil för modulen (.psm1) eller från en dynamisk modul som skapats med hjälp av den `New-Module` cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet denna cmdlet tar bort modulerna från den aktuella sessionen.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet denna cmdlet verifierar att ett modulmanifest korrekt beskriver komponenterna i en modul genom att verifiera att de filer som anges i modulen manifestfilen (.psd1) faktiskt finns i de angivna sökvägarna.

$PSScriptRoot den här variabeln innehåller katalogen där skriptet modulen körs. Det kan du använda modulsökväg för att komma åt andra resurser.

$env: PSModulePath den här miljövariabeln innehåller en lista över de kataloger i vilka Windows PowerShell-moduler lagras. Windows PowerShell använder värdet för den här variabeln när du importerar moduler automatiskt och uppdatera hjälpavsnitt för moduler.

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
