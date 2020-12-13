---
ms.date: 07/09/2020
ms.topic: reference
title: Översikt över utökad typ system
description: Översikt över utökad typ system
ms.openlocfilehash: f4a789f779fa8a52f0fe524abff7ec3311e93b6c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655727"
---
# <a name="extended-type-system-overview"></a>Översikt över utökad typ system

PowerShell använder sitt **PSObject** -objekt för att utöka objekt typerna på två sätt. Först är **PSObject** -objektet ett sätt att visa olika vyer av olika objekt typer. Detta kallas för att visa en anpassad vy av ett objekt. För det andra är **PSObject** -objektet ett sätt att lägga till medlemmar i ett befintligt objekt. Genom att omsluta ett befintligt objekt, som kallas för bas objekt, tillhandahåller **PSObject** -objektet ett utökat typ system (ETS) som skript-och cmdlet-utvecklare kan använda för att manipulera .net-objekt i gränssnittet.

## <a name="cmdlet-and-script-development-issues"></a>Problem med cmdlet-och skript utveckling

ETS löser två grundläggande problem:

För det första har vissa .NET-objekt inte det nödvändiga standard beteendet för att fungera som data mellan cmdletar.

- Vissa .NET-objekt är "meta"-objekt (till exempel: WMI-objekt, ADO-objekt och XML-objekt) vars medlemmar beskriver de data de innehåller. I en skript miljö är det dock de data som är mest intressanta, inte beskrivningen av de data som finns. ETS löser det här problemet genom att introducera begreppet kort som anpassar det underliggande .NET-objektet så att de förväntade standardsemantiken förväntas.
- Vissa .NET-objekt medlemmar är inkonsekventa namngivna, tillhandahåller en otillräcklig uppsättning offentliga medlemmar eller ger otillräcklig funktion. ETS löser det här problemet genom att introducera möjligheten att utöka .NET-objektet med ytterligare medlemmar.

För det andra är PowerShell-skript språket _typ_ lös i att en variabel inte behöver deklareras av en viss typ. Det vill säga att de variabler som en skript utvecklare skapar är av _typen typ_ gräns. PowerShell-systemet är dock "typ driven" i att det är beroende av att ett typnamn används för grundläggande åtgärder, till exempel för att lägga till resultat eller sortera.

Därför måste en skript utvecklare ha möjlighet att ange typen av en av deras variabler och skapa en egen uppsättning av dynamiskt skrivna "objekt" som innehåller egenskaper och metoder och som kan delta i det typ drivna systemet. ETS löser detta problem genom att tillhandahålla ett gemensamt objekt för skript språket som har möjlighet att ange dess typ dynamiskt och lägga till medlemmar dynamiskt.

Dessutom löser ETS det problem som nämnts tidigare genom att tillhandahålla **PSObject** -objektet, som fungerar som underlag för all objekt åtkomst från skript språket och ger en standard abstraktion för cmdlet-utvecklaren.

### <a name="cmdlet-developers"></a>Cmdlet-utvecklare

För cmdlet-utvecklare tillhandahåller ETS följande stöd:

- Abstraktioner som fungerar mot objekt på ett allmänt sätt med hjälp av **PSObject** -objektet. ETS ger också möjlighet att detaljgranska de här abstraktionarna om det behövs.
- Mekanismerna för att skapa ett standard beteende för formatering, sortering, serialisering och andra systemmanipuleringar av objekt typen med hjälp av en välkänd uppsättning utökade medlemmar.
- Innebär att det går att använda ett objekt med samma semantik som skript språket med hjälp av ett LanguagePrimitives-objekt.
- Innebär att du dynamiskt skriver en hash-tabell så att resten av systemet kan hantera dem på ett effektivt sätt.

### <a name="script-developers"></a>Skript utvecklare

För skript utvecklare tillhandahåller ETS följande stöd:

- Möjlighet att referera till en underliggande objekt typ med samma syntax ( `$a.x` ).
- Möjligheten att komma åt bortom abstraktionen som tillhandahålls av **PSObject** -objektet (till exempel åtkomst till anpassade medlemmar eller åtkomst till själva bas objektet).
- Möjlighet att definiera välkända medlemmar som styr formatering, sortering, serialisering och andra modifieringar av en objekt instans eller typ.
- Innebär att du namnger ett objekt som en speciell typ och därmed styr arv av dess typbaserade medlemmar.
- Möjlighet att lägga till, ta bort och ändra utökade medlemmar.
- Möjligheten att ändra själva **PSObject** -objektet om det behövs.

## <a name="the-psobject-class"></a>PSObject-klassen

**PSObject** -objektet är grunden för all objekt åtkomst från skript språket och ger en standard abstraktion för cmdlet-utvecklaren. Det innehåller ett bas objekt (ett .NET-objekt) och alla instans medlemmar (medlemmar, medlemmar som är medlemmar, som finns på en viss objekt instans, men inte nödvändigt vis på andra objekt av samma typ). Beroende på typen av bas objekt kan **PSObject** -objektet även ge implicit och explicit åtkomst till anpassade medlemmar samt alla typbaserade utökade medlemmar.

**PSObject** -objektet har följande mekanismer:

- Möjligheten att skapa en **PSObject** med eller utan ett bas objekt.
- Möjlighet att komma åt alla medlemmar i varje konstruerat **PSObject** -objekt via en gemensam sökalgoritm och möjligheten att åsidosätta algoritmen vid behov.
- Möjlighet att hämta och ange typ namn för de konstruerade **PSObject** -objekten så att skript och cmdlets kan referera till liknande **PSObject** -objekt med samma typ av namn, oavsett typ av grundläggande objekt.

### <a name="how-to-construct-a-psobject"></a>Så här skapar du en PSObject

I följande lista beskrivs hur du skapar ett **PSObject** -objekt:

- Anrop av **PSObject** . #ctor-konstruktorn skapar ett nytt **PSObject** -objekt med ett bas objekt av PSCustomObject. Ett bas objekt av den här typen anger att **PSObject** -objektet saknar meningsfullt bas objekt. Ett **PSObject** -objekt med den här typen av Base-Object tillhandahåller dock en egenskaps uppsättning som cmdlet-utvecklare kan hitta till hjälp genom att lägga till utökade medlemmar.

Utvecklare kan även ange objekt typ namnet, vilket gör att objektet kan dela dess utökade medlemmar med andra **PSObject** -objekt av samma typ-namn.

- Anrop av konstruktorn **PSObject** . #ctor (system. Object) skapar ett nytt **PSObject** -objekt med ett bas objekt av typen system. Object.

  I det här fallet är typ namnet för det skapade objektet en samling av härlednings-hierarkin för bas objekt. Exempelvis innehåller typ namnet för **PSObject** som innehåller ett ProcessInfo Base-objekt följande namn:

  - System. Diagnostics. process
  - System. ComponentModel. Component
  - System. MarshalByRefObject
  - System. Object

- Anropar **PSObject** . AsPSObject (system. Object) skapar ett nytt **PSObject** -objekt baserat på ett angivet objekt.

  Om det angivna objektet är av typen system. Object används det angivna objektet som bas objekt för det nya **PSObject** -objektet. Om det tillhandahållna objektet redan är ett **PSObject** -objekt returneras det angivna objektet som det är.

### <a name="base-adapted-and-extended-members"></a>Bas, anpassade och utökade medlemmar

Med hjälp av ETS används följande villkor för att visa förhållandet mellan de ursprungliga medlemmarna i bas-objektet och de medlemmar som läggs till av PowerShell. Mer information om de olika typerna av medlemmar som används av **PSObject** -objektet finns i PSObject- [klass](/dotnet/api/system.management.automation.psobject).

#### <a name="base-object-members"></a>Bas objekts medlemmar

Om bas-objektet anges när **PSObject** -objekten konstrueras, görs medlemmarna i bas-objektet tillgängligt via egenskapen members.

#### <a name="adapted-members"></a>Anpassade medlemmar

När ett bas objekt är ett meta-objekt, en som innehåller data i ett generiskt sätt vars egenskaper beskriver deras inbäddade data, anpassar ETS objekten till en vy som ger direkt åtkomst till data via de anpassade medlemmarna i **PSObject** -objektet. Anpassade medlemmar och medlemmar i bas objekt nås via egenskapen medlemmar.

#### <a name="extended-members"></a>Utökade medlemmar

Förutom medlemmar som görs tillgängliga från bas-eller anpassnings medlemmar som skapats av PowerShell, kan en **PSObject** också definiera utökade medlemmar som utökar det ursprungliga bas objektet med ytterligare information som är användbar i skript miljön.

Till exempel, alla kärn-cmdletar som tillhandahålls av PowerShell, till exempel Get-Content-och Set-Content-cmdletar, tar du en Sök vägs parameter. För att säkerställa att dessa cmdletar, och andra, kan fungera mot objekt av olika typer, kan en Sök vägs medlem läggas till i dessa objekt så att de anger information på ett vanligt sätt. Den här utökade Sök vägs medlemmen säkerställer att cmdletarna kan fungera mot alla dessa typer även om Bask Lassen kanske inte har en Sök vägs medlem.

Utökade medlemmar, anpassade medlemmar och bas objekts medlemmar kan nås via egenskapen members.
