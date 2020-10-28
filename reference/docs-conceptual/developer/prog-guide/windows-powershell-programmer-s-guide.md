---
ms.date: 09/13/2016
ms.topic: reference
title: Guide för Windows PowerShell-programmerare&#39;s
description: Guide för Windows PowerShell-programmerare&#39;s
ms.openlocfilehash: d390b15e49f7558fb7dfd766d50d5be68ef347d2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661778"
---
# <a name="windows-powershell-programmer39s-guide"></a>Guide för Windows PowerShell-programmerare&#39;s

Den här Programmer ' s guide är avsedd för utvecklare som är intresserade av att tillhandahålla en kommando rads hanterings miljö för system administratörer. Windows PowerShell är ett enkelt sätt för dig att skapa hanterings kommandon som visar .NET-objekt, samtidigt som Windows PowerShell kan utföra det mesta av arbetet åt dig.

I traditionell kommando utveckling måste du skriva en parameter tolkare, en parameter bindning, filter och alla andra funktioner som exponeras av varje kommando. Windows PowerShell innehåller följande för att göra det enkelt för dig att skriva kommandon:

- En kraftfull Windows PowerShell-körning (körnings motor) med en egen parser och en mekanism för automatisk bindning av kommando parametrar.

- Verktyg för att formatera och Visa kommando resultat med hjälp av kommando rads tolken (CLI).

- Stöd för höga funktions nivåer (via Windows PowerShell-providers) som gör det enkelt att komma åt lagrade data.

  Med lite kostnad kan du representera ett .NET-objekt med ett omfattande kommando eller en uppsättning kommandon som ger en fullständig kommando rads upplevelse till administratören.

  I nästa avsnitt beskrivs viktiga begrepp och villkor för Windows PowerShell. Bekanta dig med dessa begrepp och villkor innan du börjar utveckla.

## <a name="about-windows-powershell"></a>Om Windows PowerShell

Windows PowerShell definierar flera typer av kommandon som du kan använda under utveckling. Dessa kommandon omfattar: funktioner, filter, skript, alias och körbara filer (program). Huvud kommando typen som beskrivs i den här guiden är ett enkelt, litet kommando som kallas "cmdlet". Windows PowerShell tillhandahåller en uppsättning cmdlets och har fullt stöd för cmdlet-anpassning för att passa din miljö. Windows PowerShell-körningen bearbetar alla kommando typer precis som den gör-cmdlets med hjälp av pipeliner.

Förutom-kommandon stöder Windows PowerShell olika anpassningsbara Windows PowerShell-leverantörer som gör tillgängliga uppsättningar med cmdletar. Gränssnittet fungerar i Windows PowerShell-värdbaserade program (Windows PowerShell.exe), men är även tillgängligt från ett anpassat värd program som du kan utveckla för att uppfylla specifika krav. Mer information finns i [så här fungerar Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-cmdlets"></a>Windows PowerShell-cmdletar

En cmdlet är ett lättviktigt kommando som används i Windows PowerShell-miljön. Windows PowerShell-körningen anropar dessa cmdlets inom kontexten för Automation-skript som anges på kommando raden och Windows PowerShell-körningen anropar också dem program mässigt via API: er för Windows PowerShell.

Mer information om cmdlets finns i [skriva en Windows PowerShell-cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).

### <a name="windows-powershell-providers"></a>Windows PowerShell-leverantörer

När du utför administrativa uppgifter kan användaren behöva undersöka data som lagras i ett data lager (till exempel fil systemet, Windows-registret eller ett certifikat Arkiv). För att göra dessa åtgärder enklare definierar Windows PowerShell en modul som kallas en Windows PowerShell-provider som kan användas för att få åtkomst till ett speciellt data lager, till exempel Windows-registret. Varje provider stöder en uppsättning relaterade cmdlets för att ge användaren en symmetrisk vy över data i butiken.

Windows PowerShell tillhandahåller flera Windows PowerShell-Standardleverantörer. Registry-providern stöder till exempel navigering och manipulering av Windows-registret. Register nycklar visas som-objekt och register värden behandlas som egenskaper.

Om du exponerar ett data lager som användaren behöver åtkomst till kan du behöva skriva en egen Windows PowerShell-Provider enligt beskrivningen i [skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md). Mer information aboutWindows PowerShell-leverantörer finns i [hur Windows PowerShell fungerar](/previous-versions//ms714658(v=vs.85)).

### <a name="host-application"></a>Värd program

Windows PowerShell innehåller standard värd programmet powershell.exe, vilket är ett konsol program som interagerar med användaren och som är värd för Windows PowerShell-körningsmiljön med hjälp av ett konsol fönster.

Det är bara sällan att du behöver skriva ditt eget värd program för Windows PowerShell, även om anpassning stöds. Ett fall där du kan behöva ditt eget program är om du har ett krav för ett GUI-gränssnitt som är bättre än det gränssnitt som tillhandahålls av standard värd programmet. Du kanske också vill ha ett anpassat program när du baserar ditt användar gränssnitt på kommando raden. Mer information finns i [så här skapar du ett Windows PowerShell-värdprogram](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application).

### <a name="windows-powershell-runtime"></a>Windows PowerShell-körningsmiljön

Windows PowerShell-körningsmiljön är körnings motorn som implementerar kommando bearbetning. Den innehåller de klasser som tillhandahåller gränssnittet mellan värd programmet och Windows PowerShell-kommandon och-providers. Windows PowerShell-körningsmiljön implementeras som ett körnings utrymme-objekt för den aktuella Windows PowerShell-sessionen, som är den drifts miljö där gränssnittet och kommandona körs. För drift information, se [hur Windows PowerShell fungerar](/previous-versions//ms714658(v=vs.85)).

### <a name="windows-powershell-language"></a>Windows PowerShell-språk

Windows PowerShell-språket tillhandahåller skript funktioner och-mekanismer för att anropa kommandon. Fullständig skript information finns i språk referens för Windows PowerShell som levererades med Windows PowerShell.

### <a name="extended-type-system-ets"></a>ETS (Extended Type System)

Windows PowerShell ger till gång till en rad olika objekt, till exempel .NET-och XML-objekt. Till följd av detta, för att presentera en gemensam abstraktion för alla objekt typer, använder gränssnittet dess utökat typ system (ETS). De flesta ETS-funktionerna är transparenta för användaren, men skriptet eller .NET-utvecklare använder det i följande syfte:

- Visa en delmängd av medlemmarna i vissa objekt. Windows PowerShell innehåller en "anpassad" vy över flera olika objekt typer.

- Lägga till medlemmar i befintliga objekt.

- Åtkomst till serialiserade objekt.

- Skriva anpassade objekt.

  Med hjälp av ETS kan du skapa flexibla nya "typer" som är kompatibla med Windows PowerShell-språket. Om du är .NET-utvecklare kan du arbeta med objekt med samma semantik som Windows PowerShell-språket gäller för skript, till exempel för att avgöra om ett objekt utvärderas till `true` .

  Mer information om ETS och hur Windows PowerShell använder objekt finns i [begrepp för Windows PowerShell-objekt](/powershell/scripting/learn/understanding-important-powershell-concepts?view=powershell-6).

## <a name="programming-for-windows-powershell"></a>Programmering för Windows PowerShell

Windows PowerShell definierar koden för kommandon, providers och andra programmoduler med hjälp av .NET Framework. Du är inte begränsad till användningen av Microsoft Visual Studio i skapa anpassade moduler för Windows PowerShell, men exemplen i den här guiden är kända för att köras i det här verktyget. Du kan använda valfritt .NET-språk som stöder klass arv och användningen av attribut. I vissa fall kräver Windows PowerShell-API: er programmeringsspråk för att kunna komma åt generiska typer.

## <a name="programmers-reference"></a>Programmer ' s reference

Information om hur du utvecklar för Windows PowerShell finns i [Windows POWERSHELL SDK](../windows-powershell-reference.md).

## <a name="getting-started-using-windows-powershell"></a>Komma igång med Windows PowerShell

Mer information om hur du börjar använda Windows PowerShell-gränssnittet finns i [komma igång med Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) som levereras med Windows PowerShell. Ett Tri-vikning-dokument med en snabb referens tillhandahålls också som en introduktion för cmdlet-användning.

## <a name="contents-of-this-guide"></a>Innehåll i den här guiden

|Avsnitt|Definition|
|-----------|----------------|
|[Skapa en Windows PowerShell-provider](./how-to-create-a-windows-powershell-provider.md)|I det här avsnittet beskrivs hur du skapar en Windows PowerShell-Provider för Windows PowerShell.|
|[Så här skapar du ett Windows PowerShell-värdprogram](/powershell/scripting/developer/hosting/writing-a-windows-powershell-host-application)|I det här avsnittet beskrivs hur du skriver ett värd program som manipulerar en körnings utrymme och hur du skriver ett värd program som implementerar en egen anpassad värd.|
|[Skapa en Windows PowerShell-snapin-modul](../cmdlet/how-to-create-a-windows-powershell-snap-in.md)|I det här avsnittet beskrivs hur du skapar en snapin-modul som används för att registrera alla cmdletar och providrar i en sammansättning och hur du skapar en anpassad snapin-modul.|
|[Skapa ett konsolgränssnitt](./how-to-create-a-console-shell.md)|I det här avsnittet beskrivs hur du skapar ett konsol gränssnitt som inte är utöknings Bart.|
|[Begrepp relaterade till Windows PowerShell](./windows-powershell-concepts.md)|Det här avsnittet innehåller konceptuell information som hjälper dig att förstå Windows PowerShell från en utvecklares synvinkel.|

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)
