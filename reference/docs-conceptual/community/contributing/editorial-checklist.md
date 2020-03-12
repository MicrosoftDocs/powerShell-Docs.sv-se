---
title: Redaktionell check lista
description: Det här är en sammanfattande lista med regler för redigering av PowerShell-dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078579"
---
# <a name="editors-checklist"></a>Redaktörens check lista

Det här är en sammanfattning av regler som ska gälla när du skriver nya eller uppdaterar befintliga artiklar. Se andra artiklar i bidrags hand boken för detaljerade förklaringar och exempel på dessa regler.

## <a name="metadata"></a>Metadata

- `ms.date`: måste vara i formatet **mm/dd/åååå**
  - Ändra datumet då det finns en betydande eller saklig uppdatering
    - Organisera om artikeln
    - Åtgärda faktiska fel
    - Lägger till ny information
  - Ändra inte datumet om uppdateringen är obetydlig
    - Korrigera skrivfel och formatering
- `title`: unik sträng med 43-59 tecken inklusive blank steg
  - Ta inte med plats identifierare (den genereras automatiskt)
  - Använd menings fall – Inled bara det första ordet och alla korrekta Substantiv
- `description`: 115-145 tecken inklusive blank steg – denna abstrakt visas i Sök resultatet

## <a name="formatting"></a>Formatering

- Element för bakticks-syntax som visas, infogade, i ett stycke
  - Cmdlet-namn `Verb-Noun`
  - Variabel `$counter`
  - Exempel på syntaktiska `Verb-Noun -Parameter`
  - Fil Sök vägar `C:\Program Files\PowerShell``/usr/bin/pwsh`
  - URL: er som inte är avsedda att vara klickade i dokumentet
- Använd fetstil för egenskaps namn, parameter värden, parameter namn, klass namn, Modulnamn, entitetsnamn, namn på objekt eller typnamn
  - Fetstil används för semantisk markering, inte betoning
  - Fet – Använd asterisker `**`
- Kursiv – Använd under streck `_`
  - Används endast för betoning, inte för semantisk markering
- Rad brytningar vid 100 kolumner (eller vid 80 för **about_Topics**)
- Inga hårda flikar – Använd bara blank steg
- Inga avslutande blank steg på rader

### <a name="headers"></a>Rubriker

- H1 är endast första ett H1 per artikel
- Använd endast [ATX-rubriker](https://github.github.com/gfm/#atx-headings)
- Använd menings fall för alla sidhuvuden
- Hoppa inte över nivåer – inget H3 utan H2
- Max djup på H3 eller H4
- Tom rad före och efter
- PlatyPS tillämpar vissa huvuden i schemat – Lägg inte till eller ta bort huvuden

### <a name="code-blocks"></a>Kodblock

- Tom rad före och efter
- Använd taggade kod avgränsningar – **PowerShell**, **utdata**eller annat lämpligt språk-ID
- Otaggade block för staket eller andra gränssnitt
- Lägg till **utdata** i ett separat kodblock förutom enkla exempel där du inte har för avsikt att läsa in läsaren för att använda **kopierings** knappen
- Se listan över [språk som stöds](/contribute/code-in-docs#supported-languages)

### <a name="lists"></a>Listor

- Indraget korrekt
- Tom rad före första objektet och efter sista posten
- Punkt-Använd bindestreck (`-`) inte asterisk (`*`) – för lätt att förväxla med betoning
- För numrerade listor är alla siffror "1".

## <a name="terminology"></a>Terminologi

- PowerShell jämfört med Windows PowerShell vs. PowerShell Core
- Se [produkt terminologi](powershell-style-guide.md#product-terminology)

## <a name="cmdlet-reference-examples"></a>Exempel på cmdlet-referenser

- Måste ha minst ett exempel i cmdlet-referensen
- Exempel bör vara tillräckligt många kod för att demonstrera användningen
- PowerShell-syntax
  - Använd fullständiga namn på cmdletar och parametrar-inga alias
  - Använda ihopbuntning för parametrar när kommando raden blir för lång
  - Undvik att använda rad fortsättnings omskalning – Använd bara vid behov
- Ta bort eller förenkla PowerShell-prompten (`PS>`), förutom om det krävs för exemplet
- Exempel på cmdlet-referens måste följa följande PlatyPS-schema

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- Lägg inte till några stycken mellan kod blocken. Allt beskrivande innehåll måste komma före eller efter kod blocken.

## <a name="linking-to-other-documents"></a>Länka till andra dokument

- Länka utanför dokument uppsättning eller mellan cmdlet-referens och konceptuell
  - Använd relativa URL: er vid länkning till docs.microsoft.com (ta bort `https://docs.microsoft.com/en-us`)
  - Ta inte med språk i URL: er för Microsoft-egenskaper (t. ex. ta bort `/en-us` från URL)
  - Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen
- Inom dokument uppsättning
  - Länk till fil Sök väg (t. ex. `../folder/file.md`)
  - Alla fil Sök vägar använder snedstreck (`/`) tecken
- Bild länkar måste ha en unik alternativ text
