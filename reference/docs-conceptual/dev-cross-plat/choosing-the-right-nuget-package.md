---
title: Välja rätt PowerShell NuGet-paket för ditt .NET-projekt
description: Tillsammans med de körbara paket som publiceras med varje PowerShell-utgåva, innehåller PowerShell-teamet också flera paket som är tillgängliga på NuGet. Med dessa paket kan du använda PowerShell som en API-plattform i .NET.
ms.date: 06/25/2020
ms.custom: rjmholt
ms.openlocfilehash: 39369ed872faa76ad2c41d813da5e0a98cf1c078
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85795452"
---
# <a name="choosing-the-right-powershell-nuget-package-for-your-net-project"></a>Välja rätt PowerShell NuGet-paket för ditt .NET-projekt

Tillsammans `pwsh` med de körbara paket som publiceras med varje PowerShell-utgåva, innehåller PowerShell-teamet också flera paket som är tillgängliga på [NuGet][]. Med dessa paket kan du använda PowerShell som en API-plattform i .NET.

Som ett .NET-program som innehåller API: er och väntar på att läsa in .NET-bibliotek som implementerar egna (binära moduler) är det viktigt att PowerShell är tillgängligt i form av ett NuGet-paket.

För närvarande finns det flera NuGet-paket som ger en del åter givning av området för PowerShell API-ytan. Vilket paket som ska användas med ett visst projekt har inte alltid gjorts klart. Den här artikeln tar en del av några vanliga scenarier för PowerShell-riktade .NET-projekt och hur du väljer rätt NuGet-paket som mål för ditt PowerShell-orienterade .NET-projekt.

## <a name="hosting-vs-referencing"></a>Värd vs-referering

Vissa .NET-projekt söker efter att skriva kod som ska läsas in i en befintlig PowerShell-körning (till exempel `pwsh` , `powershell.exe` den integrerade PowerShell-konsolen eller ISE), medan andra vill köra PowerShell i sina egna program.

- **Referenser** är till för när ett projekt, vanligt vis en modul, är avsett att läsas in i PowerShell.
  Den måste kompileras mot de API: er som PowerShell tillhandahåller för att kunna interagera med den, men PowerShell-implementeringen tillhandahålls av PowerShell-processen som läser in den i. Vid referenser kan ett projekt använda [referens sammansättningar][] eller de faktiska körnings sammansättningarna som ett mål för kompilering, men de måste se till att de inte publicerar någon av dessa med dess build.
- **Värd** är när ett projekt behöver en egen implementering av PowerShell, vanligt vis eftersom det är ett fristående program som behöver köra PowerShell. I det här fallet kan du inte använda rent referens sammansättningar. I stället måste en konkret PowerShell-implementering vara beroende av. Eftersom en konkret PowerShell-implementering måste användas måste du välja en viss version av PowerShell för att vara värd för. ett enda värd program kan inte använda PowerShell-versioner med flera mål.

### <a name="publishing-projects-that-target-powershell-as-a-reference"></a>Publicera projekt som är riktade till PowerShell som en referens

> [!NOTE]
> Vi använder termen **publicera** i den här artikeln för att referera till körning `dotnet publish` , som placerar ett .NET-bibliotek i en katalog med alla dess beroenden, redo för distribution till en viss körning.

För att förhindra publicering av projekt beroenden som bara används som referens mål för kompilering, rekommenderar vi att du anger [attributet PrivateAssets][]:

```xml
<PackageReference Include="PowerShellStandard.Library" Version="5.1.0.0" PrivateAssets="all" />
```

Om du glömmer att göra detta och använda en referens sammansättning som mål kan du se problem som rör användning av referens sammansättningens standard implementering i stället för den faktiska implementeringen. Detta kan ske i form av ett `NullReferenceException` , eftersom referens sammansättningar ofta modellerar implementerings-API: n genom att bara returnera `null` .

## <a name="key-kinds-of-powershell-targeting-net-projects"></a>Viktiga typer av PowerShell-riktade .NET-projekt

Alla .NET-bibliotek eller program kan bädda in PowerShell, men det finns några vanliga scenarier som använder PowerShell-API: er:

- **Implementera en PowerShell-modul för binär**

  PowerShell-binärfiler är .NET-bibliotek som läses in av PowerShell och som måste implementera PowerShell-API: er som [PSCmdlet][] -eller [CmdletProvider][] -typer för att kunna exponera cmdlets eller providers. Eftersom de läses in i söker moduler i syfte att kompilera mot referenser till PowerShell utan att publicera den i sin version. Det är också vanligt för moduler som vill ha stöd för flera PowerShell-versioner och plattformar, helst med ett minimum av disk utrymme, komplexitet eller upprepad implementering. Se [about_Modules][] för mer information om moduler.

- **Implementera en PowerShell-värd**

  En PowerShell-värd tillhandahåller ett interaktions lager för PowerShell-körningsmiljön. Det är en speciell typ av _värd_där en [PSHost][] implementeras som ett nytt användar gränssnitt till PowerShell. PowerShell-ConsoleHost innehåller till exempel ett Terminal-användargränssnitt för körbara PowerShell-filer, medan PowerShell-redigeraren Services-värden och ISE-värden båda ger ett redigerings program integrerat delvis grafiskt användar gränssnitt runt PowerShell. Även om det är möjligt att läsa in en värd på en befintlig PowerShell-process, är det mycket vanligare att en värd implementering fungerar som en fristående PowerShell-implementering som distribuerar om PowerShell-motorn.

- **Anropar PowerShell från ett annat .NET-program**

  Som med alla program kan PowerShell anropas som en under process för att köra arbets belastningar. Men som .NET-program, är det också möjligt att anropa PowerShell i processen för att få tillbaka fullständiga .NET-objekt som ska användas i det anropande programmet. Det här är en mer allmän typ av _värd_där programmet har sin egen PowerShell-implementering för intern användning. Exempel på detta kan vara en tjänst eller daemon som kör PowerShell för att hantera dator tillstånd eller ett webb program som kör PowerShell på begäran för att göra något som till exempel hanterar moln distributioner.

- **Enhets testning PowerShell-moduler från .NET**

  Även om moduler och andra bibliotek som är utformade för att exponera funktioner till PowerShell bör testas i första hand från PowerShell (vi rekommenderar [pester][]), ibland är det nödvändigt att enhets test-API: er skrivs för en PowerShell-modul från .net. Den här situationen innebär att modulens kod försöker rikta in sig på ett antal PowerShell-versioner, medan testningen ska köra den på specifika, konkreta implementeringar.

## <a name="powershell-nuget-packages-at-a-glance"></a>PowerShell NuGet-paket snabbt

I den här artikeln kommer vi att gå igenom följande NuGet-paket som visar PowerShell-API: er:

- [PowerShellStandard. Library][], en referens sammansättning som gör det möjligt att skapa en enda sammansättning som kan läsas in med flera PowerShell-körningar.
- [Microsoft. PowerShell. SDK][], hur du kan rikta in och vara värd för hela PowerShell SDK
- Paketet [system. Management. Automation][] , PowerShell-körningen och motor implementeringen, som kan vara användbara i minimala värdbaserade implementeringar och för versions specifika mål scenarier.
- **Windows PowerShell Reference-sammansättningar**, sätt att rikta och faktiskt vara värd för Windows PowerShell (PowerShell-versioner 5,1 och senare).

> [!NOTE]
> [PowerShell-NuGet][] -paketet är inte ett .NET-bibliotek alls, utan ger i stället PowerShell-verktyget för global användning av PowerShell dotNet. Detta bör inte användas av några projekt eftersom det bara tillhandahåller en körbar fil.

## <a name="powershellstandardlibrary"></a>PowerShellStandard. Library

PowerShell-standardbiblioteket är en referens sammansättning som samlar in skärnings punkten för API: erna i PowerShell-versionerna 7, 6 och 5,1. Detta ger en sammanfattande API-yta för att kompilera .NET-kod mot, vilket gör det möjligt för .NET-projekt att använda PowerShell-versionerna 7, 6 och 5,1 utan att riskera att anropa ett API som inte finns där.

PowerShell-standarden är avsedd för att skriva PowerShell-moduler eller annan kod som endast ska köras när den har lästs in i en PowerShell-process. Eftersom det är en referens sammansättning innehåller PowerShell-standarden ingen implementering, så ingen funktionalitet för fristående program.

### <a name="using-powershell-standard-with-different-net-runtimes"></a>Använda PowerShell-standarden med olika .NET-körningar

PowerShell-standarden riktar sig till [.net standard 2,0][] -mål körning, som är en fasad-körning utformad för att tillhandahålla ett gemensamt ytdiagram som delas av .NET Framework och .net Core. Detta gör att du kan använda en enskild körning för att skapa en enda sammansättning som fungerar med flera PowerShell-versioner, men som har följande konsekvenser:

- PowerShell-inläsningen av modulen eller biblioteket måste köra minst .NET 4.6.1; .NET 4,6 och .NET 4.5.2 stöder inte .NET standard. Observera att en nyare Windows PowerShell-version inte innebär en nyare .NET Framework version; Windows PowerShell 5,1 kan köras på .NET 4.5.2.
- För att kunna arbeta med en PowerShell som kör .NET Framework 4.7.1 eller lägre, krävs .NET 4.6.1 [netstandard. biblioteks][] implementering krävs för att tillhandahålla netstandard.dll och andra shim-sammansättningar i äldre .NET Framework versioner.

PowerShell 6 + tillhandahåller egna shim-sammansättningar för typ vidarebefordring från .NET Framework 4.6.1 (och senare) till .NET Core. Det innebär att så länge en modul endast använder API: er som finns i .NET Core, kan PowerShell 6 + läsa in och köra den när den har skapats för .NET Framework 4.6.1 ( `net461` körnings målet).

Det innebär att binära moduler som använder PowerShell-standarden för att nå flera PowerShell-versioner med en enda publicerad DLL-fil har två alternativ:

1. Publicera en sammansättning som skapats för `net461` mål körningen. Detta omfattar:
   - Publicera projektet för `net461` körning
   - Kompilera även mot `netstandard2.0` körning (utan att använda dess build-utdata) för att säkerställa att alla API: er som används också finns i .net Core.

1. Publicera en sammansättnings version för `netstandard2.0` mål körningen. Detta kräver:
   - Publicera projektet för `netstandard2.0` körning
   - Tar bort `net461` beroenden av netstandard. Library och kopierar dem till projekt sammansättningens publicerings plats så att sammansättningen korrigeras i .NET Framework.

Om du vill bygga PowerShell-moduler eller-bibliotek som är riktade till äldre .NET Framework-versioner kan det vara bättre att använda flera .NET-körningar. Detta publicerar en sammansättning för varje mål körning och rätt sammansättning måste läsas in vid modulens inläsnings tid (till exempel med en liten psm1 som rotnod).

### <a name="testing-powershell-standard-projects-in-net"></a>Testa PowerShell standard-projekt i .NET

När det gäller att testa modulen i .NET-testlöpare som xUnit, kom ihåg att det bara går att utföra kompilerings kontrollerna. Du måste testa modulen mot de relevanta PowerShell-plattformarna.

För att testa API: er som bygger på PowerShell-standarden i .NET, bör du lägga till `Microsoft.Powershell.SDK` som ett test beroende med .net Core (med versionen inställd på att matcha den önskade PowerShell-versionen) och lämpliga referens sammansättningar för Windows PowerShell med .NET Framework.

Mer information om PowerShell-standarden och hur du använder den för att skriva en binär modul som fungerar i flera PowerShell-versioner finns i [det här blogg inlägget][]. Se även [PowerShell-standardlagringsplatsen][] på GitHub.

## <a name="microsoftpowershellsdk"></a>Microsoft. PowerShell. SDK

`Microsoft.PowerShell.SDK` är ett meta-paket som drar samman alla komponenter i PowerShell SDK till ett enda NuGet-paket. Ett fristående .NET-program kan använda Microsoft. PowerShell. SDK för att köra valfria PowerShell-funktioner utan beroende på externa PowerShell-installationer eller bibliotek.

> [!NOTE]
> PowerShell SDK refererar bara till alla komponent paket som utgör PowerShell och som kan användas för .NET-utveckling med PowerShell.

En specifik `Microsoft.Powershell.SDK` version innehåller den konkreta implementeringen av samma version av PowerShell-programmet, version 7,0, som innehåller implementeringen av powershell 7,0 och körning av kommandon eller skript med den fungerar i stort sett likadant som att köra dem i PowerShell 7,0.

Att köra PowerShell-kommandon från SDK: n är huvudsakligen, men inte helt, samma som att köra dem från `pwsh` . Till exempel är [Start-Job][] beroende av att den `pwsh` körbara filen är tillgänglig och fungerar inte med `Microsoft.Powershell.SDK` som standard.

Genom att rikta in `Microsoft.Powershell.SDK` dig på ett .NET-program kan du integrera med alla implementerings sammansättningar i PowerShell, till exempel, `System.Management.Automation` `Microsoft.PowerShell.Management` och andra modul sammansättningar.

Om du publicerar en program mål grupp `Microsoft.Powershell.SDK` ingår alla dessa sammansättningar och alla beroenden PowerShell kräver. Det inkluderar även andra till gångar som PowerShell kräver i dess version, till exempel modulen manifest för `Microsoft.PowerShell.*` moduler och `ref` katalogen som krävs av [Add-Type][].

Med tanke på att `Microsoft.Powershell.SDK` det passar bäst för:

- Implementering av PowerShell-värdar.
- xUnit-testning av bibliotek som riktar sig mot PowerShell Reference-sammansättningar.
- Anropar PowerShell i processen från ett .NET-program.

`Microsoft.PowerShell.SDK` kan också användas som referens mål när ett .NET-projekt är avsett att användas som en modul eller på annat sätt läses in av PowerShell, men är beroende av API: er som bara finns i en viss version av PowerShell. Observera att en sammansättning som publicerats mot en speciell version av `Microsoft.PowerShell.SDK` endast är säker att läsa in och använda i den versionen av PowerShell. För att nå flera PowerShell-versioner med specifika API: er krävs flera versioner, varje mål version av `Microsoft.Powershell.SDK` .

> [!NOTE]
> PowerShell SDK är bara tillgängligt för PowerShell version 6 och senare. Använd referens sammansättningarna för Windows PowerShell som beskrivs nedan för att ge motsvarande funktionalitet med Windows PowerShell.

## <a name="systemmanagementautomation"></a>System. Management. Automation

`System.Management.Automation`Paketet är kärnan i POWERSHELL SDK. Den finns på NuGet, främst som en till gång för `Microsoft.Powershell.SDK` att hämta i. Det kan dock också användas direkt som ett paket för mindre värd scenarier och moduler för versions mål.

Mer specifikt `System.Management.Automation` kan paketet vara en bättre leverantör av PowerShell-funktioner när:

- Du vill bara använda PowerShell-språkfunktioner (i `System.Management.Automation.Language` namn rymden) som PowerShell-parser, AST-och AST-besökets API: er (till exempel för statisk analys av PowerShell).
- Du vill bara köra vissa kommandon från `Microsoft.PowerShell.Core` modulen och köra dem i ett sessionstillstånd som har skapats med [CreateDefault2][] Factory-metoden.

Dessutom `System.Management.Automation` är en användbar referens sammansättning när:

- Du vill ha mål-API: er som bara finns i en angiven PowerShell-version
- Du kommer inte att vara beroende av typer som inträffar utanför `System.Management.Automation` sammansättningen (till exempel typer som exporteras av cmdletar i `Microsoft.PowerShell.*` moduler).

## <a name="windows-powershell-reference-assemblies"></a>Referens sammansättningar för Windows PowerShell

För PowerShell-versionerna 5,1 och äldre (Windows PowerShell) finns det ingen SDK för att tillhandahålla en implementering av PowerShell, eftersom Windows PowerShell-implementeringen är en del av Windows.

I stället tillhandahåller referens sammansättningarna för Windows PowerShell båda referens målen och ett sätt att revara värd för Windows PowerShell, och fungerar på samma sätt som PowerShell SDK för version 6 och senare.

I stället för att differentieras av versionen har Windows PowerShell-referens sammansättningar ett annat paket för varje version av Windows PowerShell:

- [PowerShell 5.1](https://www.nuget.org/packages/Microsoft.PowerShell.5.ReferenceAssemblies/)
- [PowerShell 4](https://www.nuget.org/packages/Microsoft.PowerShell.4.ReferenceAssemblies/)
- [PowerShell 3](https://www.nuget.org/packages/Microsoft.PowerShell.3.ReferenceAssemblies/)

Information om hur du använder Windows PowerShell-referens sammansättningar finns i [Windows POWERSHELL SDK][].

## <a name="real-world-examples-using-these-nuget-packages"></a>Verkliga exempel som använder dessa NuGet-paket

Olika PowerShell-verktyg för projekt riktar sig mot olika PowerShell NuGet-paket beroende på deras behov. Här visas några viktiga exempel.

### <a name="psreadline"></a>PSReadLine

[PSReadLine][], PowerShell-modulen som ger mycket av PowerShell: s omfattande konsol upplevelse, är riktad till PowerShell-standard som ett beroende snarare än en viss PowerShell-version och är riktad `net461` mot .net-körningen i dess [CSPROJ][].

PowerShell 6 + tillhandahåller sina egna shim-sammansättningar som gör att en DLL som riktar `net461` sig mot körningen "fungerar" när den läses in (genom att bindningen dirigeras om till .NET Framework `mscorlib.dll` till den relevanta .net Core-sammansättningen).

Detta fören klar PSReadLine och leveransen av modulen avsevärt, eftersom PowerShell-standarden säkerställer att de enda API: erna som används finns i både PowerShell 5,1 och PowerShell 6 +, samtidigt som modulen också kan leverera med endast en enda sammansättning.

.NET 4.6.1-målet innebär att Windows PowerShell som körs på .NET 4.5.2 och .NET 4,6 inte stöds om.

### <a name="powershell-editor-services"></a>PowerShell-redigerare-tjänster

[PowerShell-redigeraren][] (PSES) är Server delen för [PowerShell-tillägget][] för [Visual Studio Code][], och är i själva verket en form av PowerShell-modul som läses in av en PowerShell-körbar fil och som sedan tar över den processen för att vara värd för PowerShell i sig samtidigt som även tillhandahåller språk tjänst protokoll och fel söknings funktioner.

PSES tillhandahåller konkreta implementerings mål för `netcoreapp2.1` att nå PowerShell 6 + (sedan PowerShell 7 `netcoreapp3.1` : s körning är bakåtkompatibla) och `net461` för att rikta Windows PowerShell 5,1, men innehåller merparten av sin logik i en andra sammansättning som är riktad till `netstandard2.0` PowerShell-standard. Detta gör det möjligt att hämta beroenden som krävs för .NET Core-och .NET Framework-plattformar, samtidigt som det mesta av kodbasen för en enhetlig abstraktion blir enklare.

Eftersom den är byggd för PowerShell-standarden kräver PSES en körnings implementering av PowerShell för att testas korrekt. För att göra detta kan [PSES xUnit][] -tester Hämta `Microsoft.PowerShell.SDK` och `Microsoft.PowerShell.5.ReferenceAssemblies` i syfte att tillhandahålla en PowerShell-implementering i test miljön.

Som med PSReadLine har PSES inte stöd för .NET 4,6 och tidigare, men den [utför en kontroll][] vid körning innan du anropar något av API: erna som kan orsaka en krasch i de lägre .NET Framework körningarna.

### <a name="psscriptanalyzer"></a>PSScriptAnalyzer

[PSScriptAnalyzer][], som är luddfri för PowerShell, måste vara riktade till syntaktiska element som endast introducerats i vissa versioner av PowerShell. Eftersom igenkänning av dessa syntaktiska element uppnås genom att implementera en [AstVisitor2][], går det inte att använda PowerShellStandard och implementerar även AST-besökets metoder för nyare PowerShell-syntax.

I stället är PSScriptAnalyzer [riktad till varje PowerShell-version][] som en build-konfiguration och skapar en separat DLL för var och en av dem. Detta ökar storlek och komplexitet för byggen, men tillåter:

- Version – specifika API-mål
- Versions funktioner som ska implementeras med i princip ingen körnings kostnad
- Totalt stöd för Windows PowerShell hela vägen till .NET Framework 4.5.2

## <a name="summary"></a>Sammanfattning

I den här artikeln har vi listat och diskuterat de NuGet-paket som är tillgängliga för mål när du implementerar ett .NET-projekt som använder PowerShell, och vilka orsaker du kan ha för att använda en över en annan.

Om du har hoppat över sammanfattningen är vissa breda rekommendationer:

- PowerShell- **moduler** bör kompileras mot PowerShell-standarden om de bara kräver API: er som är gemensamma för olika PowerShell-versioner.
- PowerShell- **värdar och program** som behöver köra PowerShell internt bör rikta in sig på PowerShell SDK för PowerShell 6 + eller relevanta Windows PowerShell referens sammansättningar för Windows PowerShell.
- PowerShell-moduler som behöver **versions specifika API: er** bör rikta in sig på referens sammansättningarna för PowerShell SDK eller Windows PowerShell för de nödvändiga PowerShell-versionerna, med hjälp av dem som referens sammansättningar (det vill säga inte publicera PowerShell-beroenden).

<!--link references -->

[.NET standard 2,0]: /dotnet/standard/net-standard
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[Lägg till typ]: /powershell/module/microsoft.powershell.utility/add-type
[AstVisitor2]: /dotnet/api/system.management.automation.language.astvisitor2
[CmdletProvider]: /dotnet/api/system.management.automation.provider.cmdletprovider
[CreateDefault2]: /dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2
[CSPROJ]: https://github.com/PowerShell/PSReadLine/blob/master/PSReadLine/PSReadLine.csproj
[Microsoft. PowerShell. SDK]: https://www.nuget.org/packages/Microsoft.PowerShell.SDK/
[Netstandard. Library]: https://www.nuget.org/packages/NETStandard.Library/
[NuGet]: https://www.nuget.org/
[utför en kontroll]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/src/PowerShellEditorServices.Hosting/EditorServicesLoader.cs#L231-L251
[Pester]: https://github.com/Pester/Pester
[PowerShell-redigerare-tjänster]: https://github.com/PowerShell/PowerShellEditorServices/
[PowerShell-tillägg]: https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[PowerShell-NuGet]: https://www.nuget.org/packages/PowerShell/
[PowerShell standard-lagringsplats]: https://github.com/PowerShell/PowerShellStandard
[PowerShellStandard. Library]: https://www.nuget.org/packages/PowerShellStandard.Library/
[PSCmdlet]: /dotnet/api/system.management.automation.pscmdlet
[PSES-xUnit]: https://github.com/PowerShell/PowerShellEditorServices/blob/8c500ee1752201d3c1cc2e5d90f1a2af3b1eb15d/test/PowerShellEditorServices.Test/PowerShellEditorServices.Test.csproj#L15-L20
[PSHost]: /dotnet/api/system.management.automation.host.pshost
[PrivateAssets-attribut]: /dotnet/core/tools/csproj#packagereference
[PSReadLine]: https://github.com/PowerShell/PSReadLine
[PSScriptAnalyzer]: https://github.com/powershell/psscriptanalyzer
[referens sammansättningar]: https://github.com/dotnet/standard/blob/master/docs/history/evolution-of-design-time-assemblies.md#definitions
[Start – jobb]: /powershell/module/microsoft.powershell.core/start-job
[System. Management. Automation]: https://www.nuget.org/packages/System.Management.Automation/
[riktar mot varje PowerShell-version]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/Engine/Engine.csproj
[blogginlägget]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[Visual Studio Code]: https://code.visualstudio.com/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell
