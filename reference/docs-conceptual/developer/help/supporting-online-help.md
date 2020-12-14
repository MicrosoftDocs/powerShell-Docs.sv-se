---
ms.date: 09/13/2016
ms.topic: reference
title: Stöd för onlinehjälp
description: Stöd för onlinehjälp
ms.openlocfilehash: 0164b5e6c6c8d66a6ab2467a8adfb7efffe0fe17
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645424"
---
# <a name="supporting-online-help"></a>Stöd för onlinehjälp

Från och med PowerShell 3,0 finns det två sätt att stödja `Get-Help` funktionen online för PowerShell-kommandon. I det här avsnittet beskrivs hur du implementerar den här funktionen för olika kommando typer.

## <a name="about-online-help"></a>Om onlinehjälp

Direkt hjälpen har alltid varit en viktig del av PowerShell. Även om `Get-Help` cmdlet: en visar hjälp avsnitt i kommando tolken, föredrar många användare upplevelsen av att läsa online, inklusive färg kodning, hyperlänkar och dela idéer i Community-innehåll och wiki-baserade dokument. För det viktigaste, före ankomsten av den uppdaterings bara hjälpen, tillhandahöll online-hjälpen den senaste versionen av hjälpfilerna.

Med ankomsten för uppdaterings bar hjälp i PowerShell 3,0 spelar onlinehjälpen fortfarande en viktig roll. Förutom den flexibla användar upplevelsen ger online-hjälpen hjälp till användare som inte kan använda uppdaterings bara hjälp för att hämta hjälp ämnen.

## <a name="how-get-help--online-works"></a>Så här fungerar Get-Help – online

För att hjälpa användarna att hitta Onlines hjälp avsnitt för kommandon, `Get-Help` har kommandot en online-version som öppnar online-versionen av hjälp avsnittet för ett kommando i användarens standard webbläsare.

Följande kommando öppnar till exempel hjälp avsnittet online för `Invoke-Command` cmdleten.

```powershell
Get-Help Invoke-Command -Online
```

För att implementera `Get-Help -Online` `Get-Help` söker cmdleten efter en Uniform Resource Identifier (URI) för hjälp avsnittet online-version på följande platser.

- Den första länken i avsnittet **relaterade länkar** i hjälp avsnittet för kommandot. Hjälp avsnittet måste vara installerat på användarens dator. Den här funktionen introducerades i PowerShell 2,0.

- Egenskapen **HelpUri** för ett kommando. Egenskapen **HelpUri** är tillgänglig även om hjälp avsnittet för kommandot inte är installerat på användarens dator. Den här funktionen introducerades i PowerShell 3,0.

  `Get-Help` söker efter en URI i den första posten i avsnittet **relaterade länkar** innan du hämtar värdet för egenskapen **HelpUri** . Om egenskap svärdet är felaktigt eller har ändrats kan du åsidosätta det genom att ange ett annat värde i den första relaterade länken. Den första relaterade länken fungerar dock bara när hjälp avsnitten är installerade på användarens dator.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Lägga till en URI till den första relaterade länken i ett kommando hjälp avsnitt

Du kan använda `Get-Help -Online` ett kommando genom att lägga till en giltig URI i den första posten i **avsnittet relaterade länkar** i det XML-baserade hjälp avsnittet för kommandot. Det här alternativet är endast giltigt i XML-baserade hjälp avsnitt och fungerar bara när hjälp avsnittet är installerat på användarens dator. När hjälp avsnittet är installerat och URI fylls i, prioriteras det här värdet framför kommandots **HelpUri** -egenskap.

För att stödja den här funktionen måste URI: n visas i `maml:uri` elementet under det första `maml:relatedLinks/maml:navigationLink` elementet i `maml:relatedLinks` elementet.

Följande XML visar rätt placering av URI: n. `Online version:`Texten i `maml:linkText` elementet är bästa praxis, men det är inget krav.

```xml
<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Lägga till egenskapen HelpUri i ett kommando

I det här avsnittet visas hur du lägger till egenskapen HelpUri i kommandon av olika typer.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Lägga till en HelpUri-egenskap till en cmdlet

För cmdletar skrivna i C# lägger du till ett **HelpUri** -attribut i **cmdlet** -klassen. Värdet för attributet måste vara en URI som börjar med `http` eller `https` .

Följande kod visar **HelpUri** -attributet för cmdlet- `Get-History` klassen.

```csharp
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Lägga till en HelpUri-egenskap i en avancerad funktion

För avancerade funktioner lägger du till en **HelpUri** -egenskap till attributet **CmdletBinding** . Värdet för egenskapen måste vara en URI som börjar med "http" eller "https".

Följande kod visar **HelpUri** -attributet för `New-Calendar` funktionen

```powershell
function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Lägga till ett HelpUri-attribut till ett CIM-kommando

För CIM-kommandon lägger du till ett **HelpUri** -attribut till **CmdletMetadata** -elementet i cdxlm-filen.
Värdet för attributet måste vara en URI som börjar med `http` eller `https` .

Följande kod visar attributet HelpUri för `Start-Debug` CIM-kommandot

```xml
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Lägga till ett HelpUri-attribut i ett arbets flöde

För arbets flöden som är skrivna på PowerShell-språket lägger du till en **. ExternalHelp** kommentars direktiv till arbets flödes koden. Värdet för direktivet måste vara en URI som börjar med `http` eller `https` .

> [!NOTE]
> Egenskapen HelpUri stöds inte för XAML-baserade arbets flöden i PowerShell.

Följande kod visar. ExternalHelp-direktiv i en arbets flödes fil.

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
