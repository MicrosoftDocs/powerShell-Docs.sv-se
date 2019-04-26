---
title: Stöd för onlinehjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082149"
---
# <a name="supporting-online-help"></a>Stöd för onlinehjälp

Från och med Windows PowerShell 3.0, det finns två sätt att stödja den `Get-Help` Online funktionen för Windows PowerShell-kommandon. Det här avsnittet förklarar hur du implementerar den här funktionen för olika kommandotyper.

## <a name="about-online-help"></a>Om onlinehjälp

Onlinehjälp har alltid varit en viktig del av Windows PowerShell. Även om den `Get-Help` cmdlet visar hjälpavsnitt i Kommandotolken, många användare föredrar upplevelsen läsa online, inklusive färgkodning, hyperlänkar och dela idéer i Community-innehåll och wiki-baserade dokument. Innan du ankomsten av uppdateringsbar hjälp tillhandahålls onlinehjälp viktigast av allt, den senaste versionen av hjälpfilerna.

Med ankomsten av uppdateringsbar hjälp i Windows PowerShell 3.0 spelar fortfarande en viktig roll i onlinehjälpen. Förutom den flexibla användarupplevelsen hjälper onlinehjälp användare som inte vill eller kan inte använda uppdateringsbar hjälp för att hämta hjälpavsnitt.

## <a name="how-get-help--online-works"></a>Hur Get-Help-Online fungerar

Att hjälpa användarna att hitta online hjälpavsnitt för kommandon i `Get-Help` kommandot har en Online-parameter som öppnar onlineversionen av hjälpavsnittet för ett kommando i användarens standardwebbläsare.

Till exempel följande kommando öppnar hjälpen för den `Invoke-Command` cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Att implementera `Get-Help` -Online, den `Get-Help` cmdlet ser ut för en identifierare URI (Uniform Resource) för onlineversion hjälpavsnitt på följande platser.

- Den första länken i avsnittet med länkar i hjälpavsnittet för kommandot. Hjälpavsnittet måste installeras på användarens dator. Den här funktionen introducerades i Windows PowerShell 2.0.

- HelpUri-egenskapen för alla kommandon. HelpUri-egenskapen är tillgänglig även när hjälpavsnittet för kommandot inte är installerad på användarens dator. Den här funktionen introducerades i Windows PowerShell 3.0.

  `Get-Help` söker efter en URI i den första posten i avsnittet länkarna innan du hämtar värdet för HelpUri-egenskapen. Du kan åsidosätta den genom att ange ett annat värde i den första relaterad länk om egenskapens värde är felaktig eller har ändrats. Den första relaterade länken fungerar dock bara när hjälpavsnitten installeras på användarens dator.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Att lägga till en URI för första relaterade länken i ett hjälpavsnitt för kommandot

Du kan använda `Get-Help` -Online för alla kommandon genom att lägga till en giltig URI till den första posten i avsnittet med länkar i XML-baserade hjälpavsnittet för kommandot. Det här alternativet är endast giltig i XML-baserade hjälpavsnitt och fungerar bara när hjälpavsnittet installeras på användarens dator. När hjälpavsnittet är installerad och URI: N har fyllts i det här värdet har företräde framför den **HelpUri** egenskapen för kommandot. Information om XML-baserade hjälpavsnitt för kommandon finns i [Writing XML-Based hjälpavsnitt för kommandon](../help/writing-xml-based-help-topics-for-commands.md).

För att stödja den här funktionen, URI: N måste finnas i den `maml:uri` elementet under först `maml:relatedLinks/maml:navigationLink` elementet i den `maml:relatedLinks` element.

Följande XML visar korrekt placering av URI: N. Den ”onlineversion”: texten i den `maml:linkText` element är en bra idé, men det är inte obligatoriskt.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Att lägga till HelpUri-egenskapen till ett kommando

Det här avsnittet visar hur du lägger till HelpUri-egenskapen till kommandon för olika typer.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Att lägga till HelpUri-egenskapen för en Cmdlet

För cmdletar som skrivits i C#, lägga till en **HelpUri** attributet till Cmdlet-klassen. Värdet för attributet måste vara en URI som börjar med ”http” eller ”https”.

Följande kod visar HelpUri-attributet för den `Get-History` cmdlet-klass.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Att lägga till HelpUri-egenskapen i en avancerad funktion

För avancerade funktioner, lägger du till en **HelpUri** egenskap enligt den **CmdletBinding** attribut. Värdet på egenskapen måste vara en URI som börjar med ”http” eller ”https”.

Följande kod visar HelpUri-attributet för funktionen New-kalender

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Att lägga till HelpUri-attributet i en CIM-kommando

CIM-kommandon, lägger du till en **HelpUri** attributet den **CmdletMetadata** elementet i filen CDXLM. Värdet för attributet måste vara en URI som börjar med ”http” eller ”https”.

Följande kod visar HelpUri-attributet Start-Debug CIM-kommandot

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Att lägga till HelpUri-attributet i ett arbetsflöde

Arbetsflöden som är skrivna i Windows PowerShell-språket, lägger du till en **. ExternalHelp** kommentar direktiv i arbetsflödet-koden. Värdet för direktivet måste vara en URI som börjar med ”http” eller ”https”.

> [!NOTE]
> HelpUri-egenskapen stöds inte för XAML-baserade arbetsflöden i Windows PowerShell.

Följande kod visar den. ExternalHelp direktiv i en arbetsflödesfil.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```