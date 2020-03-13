---
title: PowerShell – format guide för dokument
description: Den här artikeln innehåller regler för format för att skriva PowerShell-dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 964536c5195c3bb8abd98b5996a96fc7b9362489
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078649"
---
# <a name="powershell-docs-style-guide"></a>PowerShell – format guide för dokument

Den här artikeln innehåller rikt linjer som är speciella för innehållet i PowerShell-dok. Detta bygger på den information som beskrivs i [översikten](overview.md#get-started-writing-docs).

## <a name="product-terminology"></a>Produkt terminologi

Det finns flera varianter av PowerShell.
I den här tabellen definieras några av de olika termer som används för att diskutera PowerShell.

- **PowerShell** – det här är standardinställningen. Vi rekommenderar att du använder PowerShell 7 och senare för att bli den som är den sanna PowerShell som går framåt.

- **PowerShell Core** – PowerShell som bygger på .net Core. Användning av termen **Core** bör begränsas till fall där det är nödvändigt att skilja den från Windows PowerShell.

- **Windows PowerShell** – PowerShell som bygger på .NET Framework. Windows PowerShell-fartyg endast på Windows och kräver hela ramverket.

I allmänhet kan referenser till "Windows PowerShell" i dokumentationen ändras till "PowerShell".
"Windows PowerShell" bör **inte** ändras när en Windows-speciell teknik diskuteras.

## <a name="markdown-specifics"></a>Markdown-information

Microsoft Open Publishing system (OPS) som bygger vår dokumentation använder [markdig][] för att bearbeta markdown-dokumenten. Markdig analyserar dokumenten baserat på reglerna för den senaste [CommonMark][] -specifikationen.

Den nya CommonMark-specifikationen är mycket strängare om konstruktion av vissa markdown-element. Var uppmärksam på de uppgifter som anges i det här dokumentet.

### <a name="blank-lines-spaces-and-tabs"></a>Tomma rader, blank steg och tabbar

Ta bort dubbletter av tomma rader. Flera tomma rader återges som en enda tom rad i HTML så att det inte är något ändamål för flera tomma rader.

Tomma rader signalerar också slutet av ett block i markdown. Det måste finnas ett enda tomt värde mellan markdown-block av olika typer (till exempel mellan ett stycke och en lista eller rubrik).

> [!NOTE]
> Avståndet är signifikant i markdown. Använder alltid blank steg i stället för hårda tabbar. Ta bort extra blank steg i slutet av rader.

### <a name="titles-and-headings"></a>Titlar och rubriker

Använd endast [ATX-rubriker][atx] (# Style, i stället för `=` eller `-` format rubriker).

- Använd endast inledande versal i meningar och den första bokstaven i en rubrik eller rubrik ska kapitaliseras
- Det måste finnas ett enda blank steg mellan `#` och den första bokstaven i rubriken
- Rubriker ska omges av en enda tom linje
- Endast ett H1 per dokument
- Rubrik nivåerna bör ökas med ett. Hoppa över nivåer
- Använd inte fetstil eller andra markeringar i sidhuvuden

### <a name="limit-line-length-to-100-characters"></a>Begränsa rad längden till 100 tecken

Detta gäller för konceptuella artiklar och cmdlet-referens. About_topics är begränsade till 80 tecken.
Genom att begränsa rad längden förbättras git-differenser och historik för läsbarhet. Det gör det också enklare för andra skrivare att göra bidrag.

Använd tillägget [Flow markdown][reflow] i Visual Studio Code för att enkelt ommontera stycken för att passa den angivna rad längden.

### <a name="lists"></a>Listor

Om din lista innehåller flera meningar eller stycken bör du överväga att använda en rubrik på underordnade nivåer i stället för en lista.

Listan ska omges av en enda tom rad.

#### <a name="unordered-lists"></a>Osorterade listor

Avsluta inte List objekt med en punkt om de inte innehåller flera meningar. Använd bindestrecks tecken (`-`) för List objekts punkter. Detta förhindrar förvirring med fet eller kursiv markering som använder asterisken [`*`]. Om du vill inkludera ett stycke eller andra element under ett punkt objekt infogar du en rad brytning och justerar indraget med det första tecknet efter punkten.

Exempel:

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

Det här är en lista som innehåller underordnade element under ett punkt objekt.

- Första punkt objekt

  Mening som förklarar den första punkten.

  - Objekt under punkt

    Mening som förklarar under punkten.

- Andra punkt objekt
- Tredje punkt objekt

#### <a name="ordered-lists"></a>Ordnade listor

Om du vill inkludera ett stycke eller andra element under ett numrerat objekt, justera indrag med det första bokstaven efter objekt numret. Alla objekt i en numrerad lista ska använda antalet `1.` snarare än att öka varje objekt. Markdown renderar ökar värdet automatiskt. Detta gör det enklare att ordna om objekten och standardisera indraget för underordnat innehåll.

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

1. För det första elementet infogar du ett enskilt blank steg efter 1. Långa meningar ska omslutas till nästa rad och måste radas med det första tecknet efter den numrerade List markören.

   Om du vill inkludera ett andra element (t. ex. det här) infogar du en rad brytning efter det första och har justerat indrag. Indraget för det andra elementet måste justeras med det första tecknet efter den numrerade List markören. För ensiffriga objekt, t. ex. det här, kan du dra in dem till kolumn 4. För objekt med dubbla siffror, till exempel objekt nummer 10, indrag till kolumn 5.

1. Nästa numrerade objekt börjar här.

### <a name="formatting-command-syntax-elements"></a>Formaterar kommando element för syntax

- Använd alltid det fullständiga namnet för cmdletar och parametrar. Undvik att använda alias om du inte specifikt demonstrerar aliaset.

- I ett stycke ska språknyckelord, cmdlet-namn, variabler och fil Sök vägar omslutas i`` ` ``-tecken (text). Egenskaps-, parameter-och klass namn ska vara **fetstil**.

  Exempel:

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- När du refererar till en parameter efter namn ska namnet vara **fetstilt**. När du illustrerar användningen av en parameter med avstavnings prefixet ska parametern omslutas med baktick. Exempel:

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- När du refererar till externa kommandon (EXEs, skript osv.) ska kommando namnet vara fetstilt, alla gemener (eller versaler i början av en mening) och inkludera lämpligt fil namns tillägg. Exempel:

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- När du visar exempel användningen av ett externt kommando ska exemplet omslutas med baktick.
  Om det finns en namn konflikt med ett alias måste du inkludera fil tillägget i kommando exemplet. Exempel:

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- När du skriver en konceptuell artikel (till skillnad från referens innehållet) ska den första instansen av ett cmdlet-namn hyperlänkas till cmdlet-dokumentationen. Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.

  Exempel:

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  Mer information finns i avsnittet [hyperlinks](#hyperlinks) i den här artikeln.

### <a name="images"></a>Avbildningar

Syntaxen för att inkludera en avbildning är:

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

Där `alt text` är en kort beskrivning av avbildningen och `<folder path>` är en relativ sökväg till avbildningen. Alternativ text krävs för skärm läsare för synskadade. Det är också användbart om ett plats fel uppstår där avbildningen inte kan återges.

Avbildningar ska lagras i en `media/<article-name>`-mapp i den mapp som innehåller artikeln.
Bilder ska inte delas mellan artiklar. Skapa en mapp som matchar fil namnet för din artikel under mappen `media`. Kopiera avbildningarna för artikeln till den nya mappen. Om en bild används av flera artiklar måste varje mapp i bilden ha en kopia av avbildnings filen. Den här metoden förhindrar en ändring av en bild i en artikel som påverkar en annan artikel.

Följande bild fil typer stöds: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`

### <a name="markdown-extensions-supported-by-open-publishing"></a>Markdown-tillägg stöds av Open Publishing

[Microsoft docs redigerings paketet](/contribute/how-to-write-docs-auth-pack) innehåller verktyg som stöder funktioner som är unika för vårt publicerings system. Aviseringar är ett markdown-tillägg för att skapa block offerter som återger docs.microsoft.com med färger och ikoner som visar innebörden av innehållet. Följande aviserings typer stöds:

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

> [!NOTE]
> Information som användaren bör märka även om skumering.

> [!TIP]
> Valfri information som hjälper en användare att bli mer framgångs rik.

> [!IMPORTANT]
> Nödvändig information krävs för att användaren ska lyckas.

> [!CAUTION]
> Negativa potentiella följder av en åtgärd.

> [!WARNING]
> Farliga vissa följder av en åtgärd.

## <a name="hyperlinks"></a>Hyperlänkar

- Undvik att använda Bare-URL: er. Länkar bör använda markdown syntax `[friendlyname](url-or-path)`
- Bare-URL: er kan användas vid behov, men ska stå inom bakstreck. Exempel:

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- URL-länkar bör vara HTTPS när det är möjligt.
- Länkar måste ha ett eget namn, vanligt vis rubriken för det länkade ämnet
- Alla objekt i avsnittet "relaterade länkar" längst ned ska vara hyperlänkade.
- Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.

### <a name="linking-to-other-content"></a>Länka till annat innehåll

Det finns två typer av hyperlänkar som stöds av publicerings systemet: URL: er och fil länkar.

En URL-länk kan vara en URL-sökväg som är relativ till roten i docs.microsoft.com. Eller en absolut URL som innehåller fullständig URL-syntax. (Till exempel: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)

- Använd URL-länkar när du länkar till innehåll utanför PowerShell-dokument eller mellan cmdlet-referenser och konceptuella artiklar i PowerShell-dokument.
- Det enklaste sättet att länka skapar en relativ länk är att kopiera URL: en från webbläsaren och sedan ta bort `https://docs.microsoft.com/en-us` från det värde som du klistrar in i markdown.
   - Ta inte med språk i URL: er för Microsoft-egenskaper (t. ex. ta bort "/en-US" från URL: en.
- Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen.

En fil länk används för att länka från en referens artikel till en annan, eller från en konceptuell artikel till en annan. Om du behöver länka till en referens artikel för en viss version av PowerShell måste du använda en URL-länk.

- Fil länkar innehåller en relativ fil Sök väg (till exempel: `../folder/file.md`)
- Alla fil Sök vägar använder snedstreck (`/`) tecken

## <a name="formatting-code-samples"></a>Formatera kod exempel

Markdown stöder två olika kod format:

- Kod sträcker sig över (infogade) – markerade med ett enda`` ` ``-tecken. Används inom ett stycke i stället för som ett fristående block.
- Kodblock – ett block med flera rader som omges av tredubbla`` ``` ``-strängar (Triple-Ticket). Kod block kan också ha en språk etikett efter bakstrecken. Språk etiketten aktiverar syntax för innehållet i kod blocket.

### <a name="using-code-blocks"></a>Använda kodblock

Markdown gör att indrag kan använda ett kodblock, men det här mönstret kan vara problematiskt och bör undvikas. Alla kodblock ska finnas i en kod avgränsning. En kod avgränsning är ett kodblock som omges av tredubbel-`` ``` ``-strängar (Triple-Ticket). Kod avgränsnings markörerna måste finnas på en egen rad före och efter kod exemplet. Markören i början av kod blocket kan ha en valfri språk etikett. Microsoft Open Publishing system (OPS) använder språk etiketten för att stödja funktionen för att markera funktioner.

OPS lägger också till en **kopierings** knapp som kopierar innehållet i kod blocket till Urklipp. På så sätt kan du snabbt klistra in koden i ett skript för att testa kod exemplet. Alla exempel i vår dokumentation är dock inte avsedda att köras. Vissa kod block är enkla illustrationer av ett PowerShell-begrepp.

Det finns två typer av kod block som används i vår dokumentation:

1. Exempel på exempel
2. Körbara exempel

### <a name="syntax-code-blocks"></a>Kod block för syntax

Det här exemplet illustrerar alla möjliga parametrar i `Get-Command`-cmdleten.

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

I det här exemplet beskrivs `for`-instruktionen i generaliserade villkor:

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a>Exempel på exempel

Exempel på exempel används för att förklara ett PowerShell-begrepp. De är inte avsedda att kopieras till Urklipp för körning. Dessa används vanligt vis för enkla exempel som är enkla att skriva.
De används också för syntax-exempel där du illustrerar syntaxen för ett kommando. Kod blocket kan innehålla exempel på utdata från kommandot som illustreras.

Här är ett enkelt exempel som illustrerar en PowerShell-jämförelse operatorer:

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

Observera att det här exemplet har den förenklade PowerShell-prompten och visar resultatet. I det här fallet har vi inte förvarat läsaren för att kopiera och köra det här exemplet.

### <a name="executable-examples"></a>Körbara exempel

Mer komplexa exempel eller exempel som är avsedda att vara användbara för att kopiera och köra ska använda följande block/stil-markering:

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

De utdata som visas av PowerShell-kommandon måste omges av ett **utmatnings** kods block för att förhindra markering av syntax. Exempel:

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

Etiketten för den **resulterande** koden är inte ett officiellt språk som stöds av syntaxens markerings system.
Den här etiketten är dock användbar eftersom OPS lägger till etiketten "utdata" i rutan med kod rutan på webb sidan. Kod rutan "utdata" har ingen markering av syntax.

## <a name="coding-style-rules"></a>Regler för kodnings format

### <a name="avoid-line-continuation-in-code-samples"></a>Undvik rad fortsättning i kod exempel

Undvik att använda linje fortsättnings tecken (`` ` ``) i PowerShell-kod exempel. Detta är svårt att se och kan orsaka problem om det finns extra blank steg i slutet av raden.

- Använd PowerShell-ihopbuntning för att minska rad längden för cmdletar som har många parametrar.
- Dra nytta av PowerShell: s naturliga rad brytnings möjligheter, t. ex. efter pipe-tecken (`|`), inledande klammerparentes, parenteser och hakparenteser.

### <a name="avoid-using-powershell-prompts-in-examples"></a>Undvik att använda PowerShell-prompter i exempel

Användning av LED text strängen rekommenderas inte och bör begränsas till scenarier som är avsedda att illustrera kommando linje användningen. I de flesta av de här exemplen ska LED texten vara `PS>`. Den här frågan är oberoende av OS-/regionsspecifika indikatorer.

Prompter krävs för exempel som illustrerar kommandon som ändrar prompten eller när den angivna sökvägen är viktig för scenariot som illustreras. I följande exempel visas hur prompten ändras när du använder Registry-providern.

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

Du bör alltid använda det fullständiga namnet på alla cmdletar och parametrar om du inte specifikt pratar om aliaset. Cmdlet-och parameter namn måste använda rätt stavning som definierats i koden.

### <a name="using-parameters-in-examples"></a>Använda parametrar i exempel

Undvik att använda positions parametrar. I allmänhet bör du använda inkludera alltid parameter namnet i ett exempel, även om parametern position. Detta minskar risken för förvirring i exemplen.

## <a name="next-steps"></a>Nästa steg

[Redigera cmdlet-referens](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
