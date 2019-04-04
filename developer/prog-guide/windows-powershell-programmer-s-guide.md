---
title: Windows PowerShell-programmerare&#39;s Guide | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell Programmer's Guide
ms.assetid: f3aaf667-af84-4ea8-a5ad-d454d0d700b8
caps.latest.revision: 9
ms.openlocfilehash: 75425fbd38141fc82dd834835912c357ecfa6d2b
ms.sourcegitcommit: 0ca836d1044e46d3a7dcbc69fa93d84f74848559
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920398"
---
# <a name="windows-powershell-programmer39s-guide"></a>Windows PowerShell-programmerare&#39;s Guide

Den här Programmeringsguide är riktad mot utvecklare som är intresserade av att tillhandahålla en miljö för hantering av kommandoradsverktyget för administratörer. Windows PowerShell gör det enkelt för dig att skapa kommandon för hantering som visar .NET-objekt, samtidigt som Windows PowerShell för att utföra de flesta av arbetet åt dig.

I traditionella kommandot utveckling krävs att skriva en parameter-parser, binder en parameter, filter och andra funktioner som exponeras av varje kommando. Windows PowerShell innehåller följande för att göra det enkelt för dig att skriva kommandon:

- En kraftfulla Windows PowerShell-körning (motorn för körning av) med sin egen parser och en mekanism för automatiskt bindande parametrar.

- Verktyg för att formatera och visa kommandoresultat med hjälp av en kommandoradstolken (CLI).

- Stöd för stora möjligheter till funktioner (via Windows PowerShell-leverantörer) som gör det enkelt att komma åt lagrade data.

  Liten kostnad intygar du en .NET-objekt med ett omfattande kommando eller en uppsättning kommandon som kommer att erbjuda en fullständig kommandoradsmiljö till administratören.

  Nästa avsnitt beskriver de viktiga Windows PowerShell-koncept och villkor. Bekanta dig med dessa begrepp och termer innan du startar utveckling.

## <a name="about-windows-powershell"></a>Om Windows PowerShell

Windows PowerShell finns flera typer av kommandon som du kan använda under utveckling. Dessa kommandon omfattar: funktioner, filter, skript, alias och körbara filer (program). Den huvudsakliga kommandotypen som beskrivs i den här guiden är ett enkelt, liten kommando kallas en ”cmdlet”. Windows PowerShell tillhandahåller en uppsättning cmdlets för och stöd fullständigt för cmdleten anpassning så att de passar din miljö. Windows PowerShell-runtime bearbetar alla kommandotyper precis som cmdlet: ar med pipelines.

Förutom kommandon stöder olika anpassningsbara Windows PowerShell-leverantörer som gör tillgängliga specifika uppsättningar av cmdlets i Windows PowerShell. Gränssnittet fungerar i Windows PowerShell-angivna värdprogrammet (Windows PowerShell.exe), men den kan även nås från ett anpassat program som du kan utveckla för att uppfylla specifika krav. Mer information finns i [hur Windows PowerShell fungerar](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell-Cmdlets

En cmdlet är ett enkelt kommando som används i Windows PowerShell-miljö. Windows PowerShell-runtime anropar dessa cmdletar inom ramen för automatiseringsskript som finns på kommandoraden och Windows PowerShell-runtime anropar också dem programmässigt via Windows PowerShell APIs.

Läs mer om cmdlet: ar, [skriva en Windows PowerShell-Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell-Providers

Utföra administrativa uppgifter, kan användaren behöva granska data som lagras i ett datalager (till exempel filsystemet, Windows-registret eller ett certifikatarkiv). Du kan förenkla dessa åtgärder definierar en modul som kallas en Windows PowerShell-providern som kan användas för att få åtkomst till en specifik datalager, till exempel Windows-registret i Windows PowerShell. Varje provider stöder en uppsättning relaterade cmdlets för att ge användaren en symmetrisk vy över data i arkivet.

Windows PowerShell innehåller flera leverantörer av Windows PowerShell. Register-provider stöder till exempel navigering och hantering av Windows-registret. Registernycklar visas i form av objekt och registervärden behandlas som egenskaper.

Om du exponerar ett datalager som användaren ska kunna komma åt, du kan behöva skriva en egen Windows PowerShell-providern enligt beskrivningen i [skapar Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md). Mer information aboutWindows PowerShell-providers, se [hur Windows PowerShell fungerar](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="host-application"></a>Värdprogrammet

Windows PowerShell innehåller standard värd programmet powershell.exe, vilket är ett konsolprogram som samverkar med användare och är värd för Windows PowerShell-körningen med hjälp av ett konsolfönster.

Bara sällan behöver du skriva din egen värdprogram för Windows PowerShell, även om det finns stöd för anpassning. Ett fall där du kanske behöver ditt eget program är när du har ett krav för ett GUI-gränssnitt som är större än gränssnittet tillhandahålls av standard värdprogrammet. Vill du kanske också ett anpassat program när du baserar din GUI på kommandoraden. Mer information finns i [så här skapar du en Windows PowerShell-Värdapp](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07).

### <a name="windows-powershell-runtime"></a>Windows PowerShell-Runtime

Windows PowerShell-runtime är motorn för körning som implementerar kommandot bearbetning. Den innehåller de klasser som tillhandahåller gränssnittet mellan program och Windows PowerShell-kommandon och leverantörer. Windows PowerShell-runtime implementeras som ett körningsutrymme-objekt för den aktuella Windows PowerShell-sessionen, vilket är den driftsmiljö som gränssnittet och kommandon kör. Information, se [hur Windows PowerShell fungerar](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="windows-powershell-language"></a>Windows PowerShell-språket

Windows PowerShell-språket innehåller skript funktioner och mekanismer för att anropa kommandon. Fullständig scripting information finns i Windows PowerShell-Språkreferens levereras med Windows PowerShell.

### <a name="extended-type-system-ets"></a>Utökad typ System (ETS)

Windows PowerShell ger åtkomst till en mängd olika objekt, till exempel .NET och XML-objekt. Det betyder använder gränssnittet för att presentera en abstraktion som är gemensamma för alla typer av objekt dess utökade typsystemet (ETS). De flesta ETS funktioner är transparent för användaren, men det skript eller en .NET-utvecklare använder du för följande ändamål:

- Visar en delmängd av medlemmar i specifika objekt. Windows PowerShell tillhandahåller en ”anpassad” vy över flera specifika objekt av typen.

- Lägga till medlemmar i befintliga objekt.

- Åtkomst till serialiserade objekt.

- Skriva anpassade objekt.

  Med ETS kan du skapa nya flexibla ”typer” som är kompatibla med Windows PowerShell-språket. Om du är en .NET-utvecklare kan du kan arbeta med objekt med samma semantik som Windows PowerShell-språket gäller för skript, till exempel, för att avgöra om ett objekt utvärderas till `true`.

  Läs mer om ETS och hur Windows PowerShell använder objekt [Windows PowerShell-objektet koncept](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353).

## <a name="programming-for-windows-powershell"></a>Programmera för Windows PowerShell

Windows PowerShell definierar dess koden för kommandon, leverantörer och andra program-moduler med .NET Framework. Du är inte begränsad till användning av Microsoft Visual Studio skapar anpassade moduler för Windows PowerShell, även om exemplen i den här guiden är kända för att köra i det här verktyget. Du kan använda valfritt .NET-språk som stöder klassarv och användning av attribut. I vissa fall kräver Windows PowerShell APIs programmeringsspråk för att kunna komma åt generiska typer.

## <a name="programmers-reference"></a>Programmeringsreferens

Referenser när du utvecklar för Windows PowerShell finns i den [Windows PowerShell SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Komma igång med Windows PowerShell

Mer information om hur du börjar använda Windows PowerShell-gränssnittet finns i den [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) levereras med Windows PowerShell. En snabbreferens Tredubbel vikning dokumentet tillhandahålls också som en introduktion till cmdlet-användning.

## <a name="contents-of-this-guide"></a>Den här guiden innehåller

|Ämne|Definition|
|-----------|----------------|
|[Skapa en Windows PowerShell-provider](./how-to-create-a-windows-powershell-provider.md)|Det här avsnittet beskrivs hur du skapar en Windows PowerShell-providern för Windows PowerShell.|
|[Så här skapar du ett program för Windows PowerShell-värd](http://msdn.microsoft.com/en-us/d31355c9-a270-4b09-8f0c-35a7392a7d07)|Det här avsnittet beskrivs hur du skriver ett program som manipulerar ett körningsutrymme och hur du skriver ett program som implementerar sin egen anpassade värden.|
|[Skapa en Windows PowerShell-snapin-modul](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|Det här avsnittet beskrivs hur du skapar en snapin-modul som används för att registrera alla cmdletar och providers i en sammansättning och hur du skapar en anpassad snapin-modul.|
|[Skapa ett konsolgränssnitt](./how-to-create-a-console-shell.md)|Det här avsnittet beskriver hur du skapar ett konsol-gränssnitt som inte kan utökas.|
|[Begrepp relaterade till Windows PowerShell](./windows-powershell-concepts.md)|Det här avsnittet innehåller begreppsrelaterad information som hjälper dig förstå Windows PowerShell med hänsyn till utvecklare.|

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
