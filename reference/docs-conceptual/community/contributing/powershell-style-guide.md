---
title: Stilguide för PowerShell-Docs
description: Den här artikeln innehåller regler för format för att skriva PowerShell-dokumentation.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352679"
---
# <a name="powershell-docs-style-guide"></a>Stilguide för PowerShell-Docs

Den här artikeln innehåller rikt linjer som är speciella för PowerShell-Docs innehållet. Den bygger på den information som beskrivs i [översikten](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Produktterminologi

Det finns flera varianter av PowerShell.

- **PowerShell** – Det här är standardinställningen. Vi betraktar PowerShell 7 och bortom det som är den sanna PowerShell.
- **PowerShell Core** – PowerShell som bygger på .net Core. Användning av termen **Core** bör begränsas till fall där det är nödvändigt att skilja den från Windows PowerShell.
- **Windows PowerShell** – PowerShell som bygger på .NET Framework. Windows PowerShell-fartyg endast på Windows och kräver hela ramverket.

  I allmänhet kan referenser till "Windows PowerShell" i dokumentationen ändras till _PowerShell_.
  "Windows PowerShell" ska användas när _Windows PowerShell_-ett enskilt beteende diskuteras.

Relaterade produkter

- **Visual Studio Code (vs Code)** – det här är Microsofts kostnads fria redigerare med öppen källkod. I första omnämnandet ska det fullständiga namnet användas. Efter det kan du använda **vs Code**. Använd inte "VSCode".
- **PowerShell-tillägg för Visual Studio Code** – tillägget FÖRVANDLAr vs-kod till önskad IDE för PowerShell. I första omnämnandet ska det fullständiga namnet användas. Efter det kan du använda **PowerShell-tillägget**.
- **Azure PowerShell** – det här är en samling PowerShell-moduler som används för att hantera Azure-tjänster.
- **Azure Stack PowerShell** – det här är samlingen av PowerShell-moduler som används för att hantera Microsofts hybrid moln lösning.

## <a name="markdown-specifics"></a>Markdown-information

Microsoft Open Publishing system (OPS) som bygger vår dokumentation använder [markdig][] för att bearbeta markdown-dokumenten. Markdig analyserar dokumenten baserat på reglerna för den senaste [CommonMark][] -specifikationen.

Den nya CommonMark-specifikationen är mycket strängare om konstruktion av vissa markdown-element. Var uppmärksam på de uppgifter som anges i det här dokumentet.

### <a name="blank-lines-spaces-and-tabs"></a>Tomma rader, blanksteg och tabbar

Tomma rader indikerar också slutet av ett block i Markdown. Det måste finnas ett tomt värde mellan Markdown-block av olika typer (till exempel mellan ett stycke och en lista eller rubrik).

Flera tomma rader i följd återges som en enda tom rad i HTML. De tjänar inget syfte.
I ett kodblock bryts kod blocket i löpande tomma rader.

Ta bort extra blanksteg i slutet av rader.

> [!NOTE]
> Avståndet har betydelse i Markdown. Använd alltid blanksteg i stället för hårda tabbar. Avslutande blank steg kan ändra hur markdown återges.

### <a name="titles-and-headings"></a>Rubriker

Använd bara [ATX-rubriker][atx] (# style, i stället för `=` eller `-` stilrubriker).

- Använd bara inledande versal i meningar, och den första bokstaven i en rubrik skrivas med versal
- Det måste finnas ett blanksteg mellan `#` och den första bokstaven i rubriken
- Rubriker ska omges av en enda tom rad
- Endast en H1 per dokument
- Rubrik nivåerna bör ökas med ett. Hoppa inte över nivåer
- Använd inte fetstil eller andra markeringar i sidhuvuden

### <a name="limit-line-length-to-100-characters"></a>Begränsa radlängden till 100 tecken

Detta gäller för konceptuella artiklar och cmdlet-referens. Att begränsa rad längden ger bättre läsbarhet i git-differenser och historik. Det gör det också enklare för andra skrivare att göra bidrag.

Använd tillägget [Flow markdown][reflow] i Visual Studio Code för att enkelt ommontera stycken för att passa den angivna rad längden.

About_topics är begränsade till 80 tecken. Mer detaljerad information finns i [formatera About_ filer](#formatting-about_-files).

### <a name="lists"></a>Listor

Om listan innehåller flera meningar eller stycken bör du överväga att använda ett under rubrik i stället för en lista.

Listan ska omges av en enda tom rad.

#### <a name="unordered-lists"></a>Osorterade listor

Avsluta inte List objekt med en punkt om de inte innehåller flera meningar. Använd bindestreck (`-`) som punkter för listobjekt. På så sätt undviker du sammanblandning med markeringen för fetstil eller kursiv stil, som använder asterisk [`*`]. Om du vill lägga till ett stycke eller andra element under ett objekt i en punktlista infogar du en radbrytning och justerar indraget efter det första tecknet efter punkten.

Exempel:

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

Det här är en lista som innehåller underordnade element under ett punkt objekt.

- Första objektet i punktlistan

  Mening som beskriver den första punkten.

  - Underordnat punkt objekt

    Mening som förklarar den underordnade punkten.

- Andra objektet i punktlistan
- Tredje objektet i punktlistan

#### <a name="ordered-lists"></a>Sorterade listor

Om du vill lägga till ett stycke eller andra element under ett numrerat objekt, justerar du indraget efter det första tecknet som följer efter objektets nummer. Alla objekt i en numrerad lista ska använda talet i `1.` stället för att öka varje objekt. Med Markdown-rendering ökar värdet automatiskt. Det här gör det enklare att ändra ordning på objekt och standardiserar indrag för underordnat innehåll.

Exempel:

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

Den resulterande markdown återges på följande sätt:

1. För det första elementet infogar du ett blanksteg efter siffran 1. Långa meningar ska omslutas till nästa rad, och måste anpassas efter det första tecknet efter markören för den numrerade listan.

   Vill du lägga till ett andra element (som det här) infogar du en radbrytning efter det första och justerar indragen. Indraget för det andra elementet måste anpassas efter det första tecknet efter markören för den numrerade listan. För ensiffriga objekt, som det här, gör du indrag till kolumn 4. För tvåsiffriga objekt, till exempel objekt nummer 10, gör du indrag till kolumn 5.

1. Nästa numrerade objekt börjar här.

### <a name="images"></a>Avbildningar

Syntax för att infoga en bild:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

`alt text` är en kort beskrivning av bilden och `<folder path>` är en relativ sökväg till bilden. Alternativ text krävs för skärmläsare för personer med nedsatt syn.

Avbildningar ska lagras i en `media/<article-name>` mapp i den mapp som innehåller artikeln.
Dela inte bilder mellan artiklar. Skapa en mapp som matchar filnamnet för din artikel under mappen `media`. Kopiera bilderna till artikeln till den nya mappen. Om en bild används av flera artiklar måste varje bildmapp innehålla en kopia av bildfilen. Den här metoden förhindrar att en ändring av en bild i en artikel påverkar en annan artikel.

Följande bild fil typer stöds:,, `*.png` , `*.gif` `*.jpeg` `*.jpg` , `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Markdown-tillägg stöds av Open Publishing

[Microsoft docs redigerings paketet](/contribute/how-to-write-docs-auth-pack) innehåller verktyg som stöder funktioner som är unika för vårt publicerings system. Aviseringar är ett markdown-tillägg för att skapa blockquotes som återger på docs.microsoft.com med färger och ikoner som markerar innehållets omfattning. Följande aviseringstyper stöds:

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

Dessa aviseringar ser ut så här på docs.microsoft.com:

Antecknings block

> [!NOTE]
> Information som användaren ska kunna se även vid snabbläsning.

Tip-block

> [!TIP]
> Valfri information som hjälper användaren.

Viktigt block

> [!IMPORTANT]
> Viktig information som användaren behöver.

Varnings block

> [!CAUTION]
> Potentiella negativa konsekvenser av en åtgärd.

Varnings block

> [!WARNING]
> Farliga konsekvenser av en åtgärd.

### <a name="hyperlinks"></a>Hyperlänkar

- Hyperlänkar måste använda markdown-syntax `[friendlyname](url-or-path)` . [Länk referenser][linkref] stöds.
- Publicerings systemet har stöd för tre typer av länkar:
  - URL-länkar
  - Fil länkar
  - Kors referens länkar
- Länkar till andra artiklar på docs.microsoft.com måste vara plats relativa sökvägar
- Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen.
- Länkar måste ha ett eget namn, vanligt vis rubriken för den länkade artikeln
- Alla objekt i avsnittet _relaterade länkar_ längst ned ska vara hyperlänkade
- Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.
- Bare-URL: er kan användas när du har dokumenterat en angiven URI. URI måste omges av baktick. Exempel:

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a>Länka till annat innehåll på docs.microsoft.com

- **URL-länkar** till andra artiklar på docs.Microsoft.com måste vara plats relativa sökvägar. Det enklaste sättet att skapa en relativ länk är att kopiera URL: en från webbläsaren och sedan ta bort `https://docs.microsoft.com/en-us` den från det värde som du klistrar in i markdown. Ta inte med språk i URL: er för Microsoft-egenskaper (ta bort `/en-us` från URL). Ta bort alla onödiga frågeparametrar från URL: en. Exempel som ska tas bort:

  - `?view=powershell-5.1` – används för att länka till en angiven version av PowerShell
  - `?redirectedfrom=MSDN` – läggs till i URL: en när du omdirigeras från en gammal artikel till en ny plats

  Om du behöver länka till en speciell version av ett dokument måste du lägga till `&preserve_view=true` parametern i frågesträngen. Exempel: `?view=powershell-5.1&preserve_view=true`

- En **fil länk** används för att länka från en referens artikel till en annan, eller från en konceptuell artikel till en annan. Om du behöver länka till en referens artikel för en viss version av PowerShell måste du använda en URL-länk.

  - Fil länkar innehåller en relativ fil Sök väg (till exempel: `../folder/file.md` )
  - Alla fil Sök vägar använder snedstreck ( `/` )-tecken

- **Länkar mellan referenser** är en särskild funktion som stöds av publicerings systemet. Du kan använda kors referens länkar i konceptuella artiklar för att länka till .NET API eller cmdlet-referens.

  Länkar till .NET API-referens finns i [använda länkar i dokumentation](/contribute/how-to-write-links#xref-cross-reference-links) i Central Contributor-guiden.

  Länkar till cmdlet-referensen har följande format: `xref:<module-name>.<cmdlet-name>` . Till exempel för att länka till- `Get-Content` cmdlet: en i modulen **Microsoft. PowerShell. Management** .

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

Djup länkning tillåts för både URL-adresser och fil länkar. Lägg till fäst punkten i slutet av mål Sök vägen.
Exempel:

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Mer information finns i [använda länkar i dokumentation](/contribute/how-to-write-links).

## <a name="formatting-command-syntax-elements"></a>Formatera element i kommandosyntax

- Använd alltid det fullständiga namnet för cmdletar och parametrar. Undvik att använda alias om du inte specifikt demonstrerar aliaset.

- Egenskap, parameter, objekt, typ namn, klass namn, klass metoder ska vara **fetstil**.
  - Egenskaps-och parameter värden ska omslutas i baktick ( `` ` `` ).
  - När du refererar till typer med hjälp av den hakparentesa stilen använder du baktick. Exempel: `[System.Io.FileInfo]`

- Språk nyckelord, cmdlet-namn, funktioner, variabler, interna EXEs, fil Sök vägar och infogade syntaxer ska omslutas av tecken i text Ticket ( `` ` `` ).

  Exempel:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - När du refererar till en parameter med namnet ska det skrivas med **fetstil**. När du illustrerar användningen av en parameter med avstavningsprefixet ska parametern omslutas av grava accenter. Exempel:

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - När du visar exempel på användning av ett externt kommando ska exemplet omslutas av grava accenter.
    Ta alltid med fil tillägget i det inbyggda kommandot. Exempel:

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    Inklusive fil tillägget säkerställer att rätt kommando körs enligt PowerShell: s kommando prioritet.

- När du skriver en konceptuell artikel (till skillnad från referensinnehåll) ska den första förekomsten av ett cmdlet-namn hyperlänkas till cmdlet-dokumentationen. Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.

  Exempel:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Mer information finns i avsnittet [hyperlinks](#hyperlinks) i den här artikeln.

## <a name="markdown-for-code-samples"></a>Markdown för kod exempel

Markdown stöder två olika kodformat:

- **Kod sträcker sig över (infogade)** – markerade med ett enda baktick ( `` ` `` )-tecken. Används inom ett stycke i stället för som ett fristående block.
- **Kodblock** – ett block med flera rader som omges av tredubbel-bakticket ( `` ``` `` )-strängar. Kod block kan också ha en språk etikett efter bakstrecken. Språk etiketten aktiverar syntax för innehållet i kod blocket.

Alla kodblock ska finnas i en kodavgränsning. Använd aldrig indrag för kodblock. Markdown tillåter det här mönstret, men det kan vara problematiskt och bör undvikas.

Ett kodblock är en eller flera kodrader som omges av en kod gräns för tredubbelt skal streck ( `` ``` `` ).
Kodavgränsningsmarkörerna måste finnas på en egen rad före och efter kodexemplet. Markören i början av kodblocket kan ha en valfri språketikett. Microsofts Open Publishing System (OPS) använder språketiketten för att stödja markeringsfunktionen för syntax.

En fullständig lista över språk koder som stöds finns i [avgränsade kodblock](/contribute/code-in-docs#fenced-code-blocks) i den centraliserade deltagar guiden.

OPS lägger också till knappen **Kopiera**, som kopierar innehållet i kodblocket till Urklipp. På så sätt kan du snabbt klistra in koden i ett skript för att testa kod exemplet. Men inte alla exempel i vår dokumentation är avsedda att köras i befintligt skick. Vissa kod block är enkla illustrationer av ett PowerShell-begrepp.

Det finns tre typer av kod block som används i vår dokumentation:

1. Kommandosyntax
1. Illustrerande exempel
1. Körbara exempel

### <a name="syntax-code-blocks"></a>Kod block för syntax

Syntax Code block används för att beskriva en kommandos syntaktiska struktur. Använd inte en språk tagg på kod avgränsningen. Det här exemplet illustrerar alla möjliga parametrar för cmdleten `Get-Command`.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

I det här exemplet beskrivs satsen `for` i generaliserade villkor:

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Illustrerande exempel

Illustrerande exempel används för att förklara ett PowerShell-begrepp. De är inte avsedda att kopieras till Urklipp för körning. Dessa används vanligt vis för enkla exempel som är lätta att skriva och som är lätta att förstå. Kod blocket kan innehålla PowerShell-prompten och exempel på utdata.

Här är ett enkelt exempel som illustrerar PowerShell-jämförelse operatorer. I det här fallet förväntar vi oss inte att läsaren ska kopiera och köra exemplet.

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a>Körbara exempel

Avancerade exempel eller exempel som är avsedda att kopieras och köras ska använda följande block-Style-markering:

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

De utdata som visas av PowerShell-kommandon måste anges i ett kodblock för **utdata** för att förhindra markering av syntax. Exempel:

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

Den **resulterande** kod etiketten är inte ett officiellt språk som stöds av syntaxens markerings system.
Den här etiketten är dock användbar eftersom OPS lägger till etiketten "utdata" i rutan med kod rutan på webb sidan. Kod rutan "utdata" har ingen markering av syntax.

## <a name="coding-style-rules"></a>Regler för kodningsformat

### <a name="avoid-line-continuation-in-code-samples"></a>Undvik radfortsättning i kodexempel

Undvik att använda radfortsättningstecken (`` ` ``) i PowerShell-kodexempel. De är svåra att se och kan orsaka problem om det finns extra blanksteg i slutet av raden.

- Använd PowerShell-ihopbuntning för att minska rad längden för cmdletar som har flera parametrar.
- Dra nytta av PowerShell: s naturliga rad brytnings möjligheter, till exempel efter pipe ( `|` )-tecken, öppna klammerparenteser ( `{` ), parenteser ( `(` ) och hakparenteser ( `[` ).

### <a name="avoid-using-powershell-prompts-in-examples"></a>Undvik att använda PowerShell-prompter i exempel

Användning av LED text strängen rekommenderas inte och bör begränsas till scenarier som är avsedda att illustrera användningen av kommando raden. I de flesta av dessa exempel bör LED text strängen vara `PS>` . Den här frågan är oberoende av OS-/regionsspecifika indikatorer.

Det krävs i exempel för att illustrera kommandon som ändrar prompten eller när den angivna sökvägen är viktig för scenariot. I följande exempel visas hur frågan ändras när du använder registerprovidern.

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="dont-use-aliases-in-examples"></a>Använd inte alias i exempel

Använd det fullständiga namnet på alla cmdletar och parametrar om du inte uttryckligen har dokumenterat aliaset.
Cmdlet-och parameter namn måste ha rätt [Pascal-bokstäver][] namn.

### <a name="using-parameters-in-examples"></a>Använda parametrar i exempel

Undvik att använda positionsparametrar. I allmänhet bör du alltid inkludera parameter namnet i ett exempel, även om parametern är i position. På så sätt minskar du risken för förvirring i exemplen.

## <a name="formatting-cmdlet-reference-articles"></a>Formatera cmdlet Reference-artiklar

Artiklar med cmdlet-referenser har en speciell struktur. Strukturen definieras av [PlatyPS][].
PlatyPS genererar cmdlet-hjälpen för PowerShell-moduler i markdown. När du har redigerat Markdown-filerna används PlatyPS för att skapa MAML-hjälpfiler som används av cmdleten `Get-Help`.

PlatyPS har ett hårdkodat schema för cmdlet-referenser som skrivs in i koden. Dokumentet [platyPS.schema.md][] är ett försök att beskriva strukturen. Schemaöverträdelser orsakar build-fel som måste åtgärdas innan vi kan acceptera ditt bidrag.

- Ta inte bort någon av ATX-huvud strukturerna. PlatyPS förväntar sig en specifik uppsättning rubriker.
- Rubrikerna **Indatatyp** och **Utdatatyp** måste ha en typ. Om cmdleten inte tar emot eller returnerar ett värde använder du värdet `None` .
- Infogade kodomfång kan användas i alla stycken.
- Block med inhägnade kod är endast tillåtna i avsnittet **exempel** .

I PlatyPS-schemat är **exempel** en H2-rubrik. Varje exempel är ett H3-huvud. I ett exempel tillåter schemat inte att kodblock separeras av stycken. Schemat tillåter följande struktur:

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

Numrera varje exempel och lägg till en kort rubrik.

Exempel:

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a>Formatera About_-filer

`About_*` filerna skrivs i markdown men levereras som oformaterade textfiler. Vi använder [pandoc][] för att konvertera markdown till oformaterad text. `About_*` filerna är formaterade för bästa kompatibilitet i alla versioner av PowerShell och med publicerings verktygen.

Riktlinjer för grundläggande formatering:

- Begränsa normala rader till 80 tecken
- Kodblock är begränsade till 76 tecken
- Blockquotes (och aviseringar) är begränsade 78 tecken
- När du använder dessa särskilda meta-tecken `\` , `$` , och `<` :
  - I en rubrik måste dessa tecken föregås av ett inledande `\` tecken eller omges av kod intervall med hjälp av baktick ( `` ` `` )
  - I ett stycke ska de här tecknen placeras i kod intervall. Exempel:

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- Tabeller måste rymmas inom 76 tecken
  - Radbryt innehållet i celler manuellt över flera rader
  - Använd inledande och avslutande `|`-tecken på varje rad
  - I följande exempel visas hur du skapar en tabell som innehåller information som radbryts på flera rader i en cell.

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > Begränsningen 76-kolumn gäller endast för `About_*` ämnen. Du kan använda breda kolumner i konceptuella eller cmdlet Reference-artiklar.

## <a name="next-steps"></a>Nästa steg

[Checklista för redigering](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Pascal-bokstäver]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
