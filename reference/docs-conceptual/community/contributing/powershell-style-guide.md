---
title: Stilguide för PowerShell-Docs
description: Den här artikeln innehåller regler för format för att skriva PowerShell-dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 90dc93d608440ce7388614b552c0cd873a385cd9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624796"
---
# <a name="powershell-docs-style-guide"></a>Stilguide för PowerShell-Docs

Den här artikeln innehåller rikt linjer som är speciella för innehållet i PowerShell-dok. Detta bygger på den information som beskrivs i [översikten](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Produktterminologi

Det finns flera varianter av PowerShell.

- **PowerShell** – Det här är standardinställningen. Vi rekommenderar att du använder PowerShell 7 och senare för att bli den som är den sanna PowerShell som går framåt.
- **PowerShell Core** – PowerShell som bygger på .net Core. Användning av termen **Core** bör begränsas till fall där det är nödvändigt att skilja den från Windows PowerShell.
- **Windows PowerShell** – PowerShell som bygger på .NET Framework. Windows PowerShell-fartyg endast på Windows och kräver hela ramverket.

  Generellt sett kan referenser till "Windows PowerShell" i dokumentationen ändras till "PowerShell".
  "Windows PowerShell" ska användas när Windows PowerShell-det aktuella beteendet diskuteras.

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

Ta bort dubbletter av tomma rader. Flera tomma rader återges som en enda tom rad i HTML så det finns inget ändamål för flera tomma rader. Flera tomma rader i ett kodblock bryter kod blocket.

Ta bort extra blanksteg i slutet av rader.

> [!NOTE]
> Avståndet har betydelse i Markdown. Använd alltid blanksteg i stället för hårda tabbar. Avslutande blank steg kan ändra hur markdown återges.

### <a name="titles-and-headings"></a>Rubriker

Använd bara [ATX-rubriker][atx] (# style, i stället för `=` eller `-` stilrubriker).

- Använd bara inledande versal i meningar, och den första bokstaven i en rubrik skrivas med versal
- Det måste finnas ett blanksteg mellan `#` och den första bokstaven i rubriken
- Rubriker ska omges av en enda tom rad
- Endast en H1 per dokument
- Rubrik nivåerna bör ökas med ett. Hoppa över nivåer
- Använd inte fetstil eller andra markeringar i sidhuvuden

### <a name="limit-line-length-to-100-characters"></a>Begränsa radlängden till 100 tecken

Detta gäller för konceptuella artiklar och cmdlet-referens. Att begränsa rad längden ger bättre läsbarhet i git-differenser och historik. Det gör det också enklare för andra skrivare att göra bidrag.

Använd tillägget [Flow markdown][reflow] i Visual Studio Code för att enkelt ommontera stycken för att passa den angivna rad längden.

About_topics är begränsade till 80 tecken. Mer detaljerad information finns i [Redigera referens artiklar](./editing-cmdlet-ref.md#formatting-about_-files).

### <a name="lists"></a>Listor

Om din lista innehåller flera meningar eller stycken kan du överväga att använda en underordnad rubrik i stället för en lista.

Listan ska omges av en enda tom rad.

#### <a name="unordered-lists"></a>Osorterade listor

Avsluta aldrig listobjekt med punkt om de inte innehåller flera meningar. Använd bindestreck (`-`) som punkter för listobjekt. På så sätt undviker du sammanblandning med markeringen för fetstil eller kursiv stil, som använder asterisk [`*`]. Om du vill lägga till ett stycke eller andra element under ett objekt i en punktlista infogar du en radbrytning och justerar indraget efter det första tecknet efter punkten.

Ett exempel:

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

Det här är en lista som innehåller underordnade element under ett objekt i en punktlista.

- Första objektet i punktlistan

  Mening som beskriver den första punkten.

  - Underordnat objekt i punktlista

    Mening som beskriver den första underordnade punkten.

- Andra objektet i punktlistan
- Tredje objektet i punktlistan

#### <a name="ordered-lists"></a>Sorterade listor

Om du vill lägga till ett stycke eller andra element under ett numrerat objekt, justerar du indraget efter det första tecknet som följer efter objektets nummer. Alla objekt i en numrerad lista ska använda talet `1.` i stället för att öka varje objekt. Med Markdown-rendering ökar värdet automatiskt. Det här gör det enklare att ändra ordning på objekt och standardiserar indrag för underordnat innehåll.

Ett exempel:

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

`alt text` är en kort beskrivning av bilden och `<folder path>` är en relativ sökväg till bilden. Alternativ text krävs för skärmläsare för personer med nedsatt syn. Det är också användbart om det har uppstått ett fel på webbplatsen och bilden inte kan återges.

Avbildningar ska lagras i en `media/<article-name>` mapp i den mapp som innehåller artikeln.
Bilder ska inte delas mellan artiklar. Skapa en mapp som matchar filnamnet för din artikel under mappen `media`. Kopiera bilderna till artikeln till den nya mappen. Om en bild används av flera artiklar måste varje bildmapp innehålla en kopia av bildfilen. Den här metoden förhindrar att en ändring av en bild i en artikel påverkar en annan artikel.

Följande bild fil typer stöds `*.png`:, `*.gif` `*.jpeg`,,, `*.jpg``*.svg`

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

- Hyperlänkar måste använda markdown-syntax`[friendlyname](url-or-path)`
- Länkar bör vara HTTPS när det är möjligt.
- Länkar måste ha ett användarvänligt namn, vanligtvis rubriken för det länkade ämnet
- Alla objekt i avsnittet "relaterade länkar" längst ned ska vara hyperlänkade
- Använd inte grava accenter, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.
- Bare-URL: er kan användas när du pratar om en angiven URI. URI måste omges av baktick. Ett exempel:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a>Länka till annat innehåll

Det finns två typer av hyperlänkar som stöds av publicerings systemet:

En **URL-länk** kan vara en URL-sökväg som är relativ till roten i docs.Microsoft.com. Eller en absolut URL som innehåller fullständig URL-syntax. Exempelvis: `https:/github.com/MicrosoftDocs/PowerShell-Docs`

- Använd URL-länkar när du länkar till innehåll utanför PowerShell-dokument eller mellan cmdlet-referenser och konceptuella artiklar i PowerShell-dokument. Det enklaste sättet att skapa en relativ länk är att kopiera URL: en från webbläsaren och sedan `https://docs.microsoft.com/en-us` ta bort den från det värde som du klistrar in i markdown.
- Ta inte med språk i URL: er för Microsoft-egenskaper (t. ex. ta `/en-us` bort från URL).
- Ta bort alla onödiga frågeparametrar från URL-adressen om du inte behöver länka till en viss version av en artikel. Exempel:
  - `?view=powershell-5.1`– Detta används för att länka till en angiven version av PowerShell
  - `?redirectedfrom=MSDN`– Detta läggs till i URL: en när du omdirigeras från en gammal artikel till en ny plats
- Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen.

En **fil länk** används för att länka från en referens artikel till en annan, eller från en konceptuell artikel till en annan. Om du behöver länka till en referens artikel för en viss version av PowerShell måste du använda en URL-länk.

- Fil länkar innehåller en relativ fil Sök väg (till exempel `../folder/file.md`:)
- Alla fil Sök vägar använder snedstreck (`/`)-tecken

Djup länkning tillåts för både URL-adresser och fil länkar. Lägg till fäst punkten i slutet av mål Sök vägen.
Ett exempel:

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

Mer information finns i [använda länkar i dokumentation](https://docs.microsoft.com/contribute/how-to-write-links).

## <a name="formatting-command-syntax-elements"></a>Formatera element i kommandosyntax

- Använd alltid det fullständiga namnet för cmdletar och parametrar. Undvik att använda alias om du inte specifikt demonstrerar aliaset.

- Egenskap, parameter, objekt, typ namn, klass namn, klass metoder ska vara **fetstil**.
  - Egenskaps-och parameter värden ska omslutas i baktick (`` ` ``).
  - När du refererar till typer med hjälp av den hakparentesa stilen använder du baktick. Exempelvis: `[System.Io.FileInfo]`

- Språk nyckelord, cmdlet-namn, funktioner, variabler, interna EXEs, fil Sök vägar och infogade syntaxer ska omslutas av tecken`` ` ``i text Ticket ().

  Ett exempel:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - När du refererar till en parameter med namnet ska det skrivas med **fetstil**. När du illustrerar användningen av en parameter med avstavningsprefixet ska parametern omslutas av grava accenter. Ett exempel:

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - När du visar exempel på användning av ett externt kommando ska exemplet omslutas av grava accenter.
    Ta alltid med fil tillägget i det inbyggda kommandot. Ett exempel:

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    Inklusive fil tillägget säkerställer att rätt kommando körs enligt PowerShell: s kommando prioritet.

- När du skriver en konceptuell artikel (till skillnad från referensinnehåll) ska den första förekomsten av ett cmdlet-namn hyperlänkas till cmdlet-dokumentationen. Använd inte grava accenter, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.

  Ett exempel:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Mer information finns i avsnittet [hyperlinks](#hyperlinks) i den här artikeln.

## <a name="markdown-for-code-samples"></a>Markdown för kod exempel

Markdown stöder två olika kodformat:

- **Kod sträcker sig över (infogade)** – markerade med ett enda`` ` ``baktick ()-tecken. Används inom ett stycke i stället för som ett fristående block.
- **Kodblock** – ett block med flera rader som omges av tredubbel-bakticket (`` ``` ``)-strängar. Kod block kan också ha en språk etikett efter bakstrecken. Språk etiketten aktiverar syntax för innehållet i kod blocket.

Alla kodblock ska finnas i en kodavgränsning. Använd aldrig indrag för kodblock. Markdown tillåter det här mönstret, men det kan vara problematiskt och bör undvikas.

Ett kodblock är en eller flera kodrader som omges av en kod gräns för tredubbelt skal`` ``` ``streck ().
Kodavgränsningsmarkörerna måste finnas på en egen rad före och efter kodexemplet. Markören i början av kodblocket kan ha en valfri språketikett. Microsofts Open Publishing System (OPS) använder språketiketten för att stödja markeringsfunktionen för syntax.

En fullständig lista över språk koder som stöds finns i [avgränsade kodblock](/contribute/code-in-docs#fenced-code-blocks) i den centraliserade deltagar guiden.

OPS lägger också till knappen **Kopiera**, som kopierar innehållet i kodblocket till Urklipp. På så sätt kan du snabbt klistra in koden i ett skript för att testa kod exemplet. Men inte alla exempel i vår dokumentation är avsedda att köras i befintligt skick. Vissa kod block är enkla illustrationer av ett PowerShell-begrepp.

Det finns tre typer av kod block som används i vår dokumentation:

1. Kommandosyntax
1. Illustrerande exempel
1. Körbara exempel

### <a name="syntax-code-blocks"></a>Kod block för syntax

Syntax Code block används för att beskriva en kommandos syntaktiska struktur. Använd inte en språktagg på kod avgränsningen. Det här exemplet illustrerar alla möjliga parametrar för cmdleten `Get-Command`.

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

PS>  1,2,3 -eq 2
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

De utdata som visas av PowerShell-kommandon måste anges i ett kodblock för **utdata** för att förhindra markering av syntax. Ett exempel:

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

Kodetiketten **Utdata** är inte ett officiellt ”språk” som stöds av syntaxens markeringssystem.
Den här etiketten är dock användbar eftersom OPS lägger till etiketten "utdata" i rutan med kod rutan på webb sidan. Kod rutan "utdata" har ingen markering av syntax.

## <a name="coding-style-rules"></a>Regler för kodningsformat

### <a name="avoid-line-continuation-in-code-samples"></a>Undvik radfortsättning i kodexempel

Undvik att använda radfortsättningstecken (`` ` ``) i PowerShell-kodexempel. De är svåra att se och kan orsaka problem om det finns extra blanksteg i slutet av raden.

- Använd PowerShell-ihopbuntning för att minska radlängden för cmdletar som har många parametrar.
- Dra nytta av PowerShells naturliga radbrytningsmöjligheter, t.ex. efter pipe-tecken (`|`), inledande klammerparentes, parenteser och hakparenteser.

### <a name="avoid-using-powershell-prompts-in-examples"></a>Undvik att använda PowerShell-prompter i exempel

Användning av frågesträngen rekommenderas inte och bör begränsas till scenarier som är avsedda att illustrera användning av kommandoraden. I de flesta av dessa exempel bör LED text strängen vara `PS>`. Den här frågan är oberoende av OS-/regionsspecifika indikatorer.

Frågor krävs för exempel som illustrerar kommandon som förändrar frågan, eller när sökvägen som visas är viktig för scenariot som illustreras. I följande exempel visas hur frågan ändras när du använder registerprovidern.

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

### <a name="do-not-use-aliases-in-examples"></a>Använd inte alias i exempel

Du bör alltid använda det fullständiga namnet på alla cmdletar och parametrar om du inte diskuterar aliaset specifikt. Cmdlet-och parameter namn måste ha rätt Pascal-bokstäver namn.

### <a name="using-parameters-in-examples"></a>Använda parametrar i exempel

Undvik att använda positionsparametrar. I allmänhet bör du alltid inkludera parameter namnet i ett exempel, även om parametern är i position. På så sätt minskar du risken för förvirring i exemplen.

## <a name="next-steps"></a>Nästa steg

[Redigera cmdlet-referens](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
