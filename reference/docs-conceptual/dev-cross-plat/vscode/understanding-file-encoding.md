---
title: Förstå filkodning i VS Code och PowerShell
description: Konfigurera fil kodning i VS Code och PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: afad189ff20a4e73d25f15c48d6c4982b18f29a3
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142556"
---
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a>Förstå filkodning i VS Code och PowerShell

När du använder VS Code för att skapa och redigera PowerShell-skript är det viktigt att filerna sparas med rätt tecken kodnings format.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Vad är fil kodning och varför är det viktigt?

VS Code hanterar gränssnittet mellan en mänsklig genom att ange tecken strängar i en buffert och läsning/skrivning av byte till fil systemet. När VS Code sparar en fil, används en text kodning för att avgöra vilka byte som varje tecken blir. Mer information finns i [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding).

När PowerShell kör ett skript måste det på samma sätt konvertera byte i en fil till tecken för att återskapa filen till ett PowerShell-program. Eftersom VS Code skriver filen och PowerShell läser filen, måste de använda samma kodnings system. Den här processen för att parsa ett PowerShell-skript går: _byte_ -  ->  _tecken_  ->  _token-token_ för  ->  _abstrakt syntax_  ->  _execution_ .

Både VS Code och PowerShell installeras med en lämpliga standard kodnings konfiguration. Den standard kodning som används av PowerShell har dock ändrats med versionen av PowerShell Core (V6. x). För att se till att du inte har några problem med PowerShell eller PowerShell-tillägget i VS Code, måste du konfigurera dina VS-kod-och PowerShell-inställningar korrekt.

## <a name="common-causes-of-encoding-issues"></a>Vanliga orsaker till kodnings problem

Kodnings problem inträffar när kodningen för VS Code eller skript filen inte matchar den förväntade kodningen av PowerShell. Det finns inget sätt för PowerShell att automatiskt avgöra fil kodningen.

Det är mer troligt att du har problem med kodningen när du använder tecken som inte är i [ASCII-teckenuppsättningen med sju bitar](https://ascii.cl/). Exempel:

<!-- markdownlint-disable MD038 -->
- Utökade tecken som inte är bokstäver, t. ex. tank streck ( `—` ), hårt blank steg ( ` ` ) eller vänster dubbel citat tecken ( `"` )
- Accenttecken med latinska tecken ( `É` , `ü` )
- Icke-latinska tecken som kyrilliska ( `Д` , `Ц` )
- CJK-tecken ( `本` , `화` , `が` )

Vanliga orsaker till kodnings problem är:

- Kodningarna för VS Code och PowerShell har inte ändrats från sina standardvärden. För PowerShell 5,1 och nedan skiljer sig standard kodningen från VS Code.
- En annan redigerare har öppnat och överskrivit filen i en ny kodning. Detta händer ofta med ISE.
- Filen checkas in i käll kontroll i en kodning som skiljer sig från vad VS Code eller PowerShell förväntar sig. Detta kan inträffa när medarbetare använder redigerare med olika kodnings konfigurationer.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Så här ser du när du har kodnings problem

Kodnings fel visas ofta som tolknings fel i skript. Om du hittar konstig teckensekvens i skriptet kan det vara problemet. I exemplet nedan visas ett kort streck ( `–` ) som tecken `â&euro;"` :

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â&euro;"From $from â&euro;"To $recipient1 â&euro;"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Det här problemet uppstår eftersom VS Code kodar tecknen `–` i UTF-8 som byte `0xE2 0x80 0x93` . När dessa byte avkodas som Windows-1252 tolkas de som tecknen `â&euro;"` .

Några konstig teckensekvens som du kan se är:

<!-- markdownlint-disable MD038 -->
- `â&euro;"` Istället för `–`
- `â&euro;"` Istället för `—`
- `Ã„2` Istället för `Ä`
- `Â` i stället för ` `  (ett hårt blank steg)
- `Ã&copy;` Istället för `é`
<!-- markdownlint-enable MD038 -->

Den här praktiska [referensen](https://www.i18nqa.com/debug/utf8-debug.html) listar vanliga mönster som indikerar ett kodnings problem med UTF-8/Windows-1252.

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a>Hur PowerShell-tillägget i VS-kod interagerar med kodningar

PowerShell-tillägget samverkar med skript på flera olika sätt:

1. När skript redige ras i VS Code skickas innehållet av VS Code till tillägget. [Språk Server protokollet][] bestämmer att det här innehållet överförs i UTF-8. Därför är det inte möjligt för tillägget att få fel kodning.
1. När skript körs direkt i den integrerade konsolen läses de in från filen med PowerShell direkt. Om PowerShell-kodning skiljer sig från VS Code ' kan något gå fel här.
1. När ett skript som är öppet i VS Code refererar till ett annat skript som inte är öppet i VS Code, återgår tillägget till att läsa in skriptets innehåll från fil systemet. PowerShell-tillägget är standardvärdet UTF-8-kodning, men använder [byte-ordnings markering][], eller struktur, identifiering för att välja rätt kodning.

Problemet inträffar när du antar kodningen för BOM-mindre format (t. ex. [UTF-8][] utan strukturliste och [Windows-1252][]). PowerShell-tillägget är standardvärdet UTF-8. Tillägget kan inte ändra VS Codes kodnings inställningar. Mer information finns i avsnittet om [problem #824](https://github.com/Microsoft/VSCode/issues/824).

## <a name="choosing-the-right-encoding"></a>Välja rätt kodning

Olika system och program kan använda olika kodningar:

- I .NET standard, på webben och i Linux-världen är UTF-8 nu den dominerande kodningen.
- I många .NET Framework program används [UTF-16][]. Av historiska skäl kallas detta ibland "Unicode", en term som nu refererar till en bred [standard](https://en.wikipedia.org/wiki/Unicode) som innehåller både UTF-8 och UTF-16.
- I Windows fortsätter många inbyggda program som i förväg med Unicode att använda Windows-1252 som standard.

Unicode-kodningar har också begreppet ett byte-ordnings tecken (BOM). Strukturer sker i början av texten för att ange en avkodare som kodar texten. För kodningar med flera byte anger strukturen också [endian](https://en.wikipedia.org/wiki/Endianness) -koden. Strukturer är utformade för att vara byte som sällan förekommer i icke-Unicode-text, vilket ger en rimlig gissning att texten är Unicode när en struktur finns.

Strukturer är valfria och deras införande är inte lika populärt i Linux-världen, eftersom en pålitlig konvention av UTF-8 används överallt. De flesta Linux-program förutsätter att text ingången kodas i UTF-8. Många Linux-program kommer att känna igen och hantera en struktur korrekt, men en siffra gör inte, vilket leder till artefakter i text som manipuleras med dessa program.

**Därför** :

- Om du arbetar i första hand med Windows-program och Windows PowerShell bör du föredra en kodning som UTF-8 med BOM eller UTF-16.
- Om du arbetar på olika plattformar bör du hellre använda UTF-8 med BOM.
- Om du arbetar huvudsakligen i Linux-associerade kontexter bör du hellre UTF-8 utan struktur.
- Windows-1252 och Latin-1 är i princip äldre kodningar som du bör undvika om möjligt.
  Vissa äldre Windows-program kan dock vara beroende av dem.
- Det är också värt att notera att skript signering är [kodnings beroende](https://github.com/PowerShell/PowerShell/issues/3466), vilket innebär att en ändring av kodningen på ett signerat skript kräver omregistrering.

## <a name="configuring-vs-code"></a>Konfigurera VS-kod

VS Codes standard encoding är UTF-8 utan struktur.

Om du vill ange [vs Codes encoding][]går du till vs Code-inställningarna (<kbd>CTRL</kbd> + <kbd>,</kbd>) och anger `"files.encoding"` inställningen:

```json
"files.encoding": "utf8bom"
```

Några möjliga värden är:

- `utf8`: [UTF-8] utan struktur
- `utf8bom`: [UTF-8] med struktur
- `utf16le`: Lite endian [-UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Du bör få en listruta för detta i vyn grafiskt eller om du har slutfört den i JSON-vyn.

Du kan också lägga till följande för att automatiskt identifiera kodning när det är möjligt:

```json
"files.autoGuessEncoding": true
```

Om du inte vill att de här inställningarna ska påverka alla filtyper, kan du även använda olika språk konfigurationer i VS Code. Skapa en språkspecifik inställning genom att placera inställningarna i ett `[<language-name>]` fält. Exempel:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Du kanske också vill överväga att installera [Gremlins-spåraren][] för Visual Studio Code. Det här tillägget visar vissa Unicode-tecken som är lätta att skada eftersom de är osynliga eller ser ut som andra normala tecken.

## <a name="configuring-powershell"></a>Konfigurera PowerShell

PowerShell: s standard kodning varierar beroende på version:

- I PowerShell 6 + är standard kodningen UTF-8 utan struktur på alla plattformar.
- I Windows PowerShell är standard kodningen vanligt vis Windows-1252, ett tillägg på [Latin-1][], även kallat ISO 8859-1.

I PowerShell 5 + kan du hitta din standard kodning med följande:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Följande [skript](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan användas för att avgöra vilken kodning din PowerShell-session härleds för ett skript utan en struktur.

```powershell
$badBytes = [byte[]]@(0xC3, 0x80)
$utf8Str = [System.Text.Encoding]::UTF8.GetString($badBytes)
$bytes = [System.Text.Encoding]::ASCII.GetBytes('Write-Output "') + [byte[]]@(0xC3, 0x80) + [byte[]]@(0x22)
$path = Join-Path ([System.IO.Path]::GetTempPath()) 'encodingtest.ps1'

try
{
    [System.IO.File]::WriteAllBytes($path, $bytes)

    switch (& $path)
    {
        $utf8Str
        {
            return 'UTF-8'
            break
        }

        default
        {
            return 'Windows-1252'
            break
        }
    }
}
finally
{
    Remove-Item $path
}
```

Det är möjligt att konfigurera PowerShell för att använda en specifik kodning som oftare använder profil inställningar.
Se följande artiklar:

- [@mklement0]är ett [svar på PowerShell-kodning på StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]s [blogg inlägg om att hantera strukturbaserade UTF-8-indata i PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Det går inte att tvinga PowerShell att använda en speciell kodning för inkodning. PowerShell 5,1 och tidigare, som körs på Windows med språkvarianten inställd på en-US, är som standard Windows-1252-kodning när det inte finns någon struktur. Andra nationella inställningar kan använda en annan kodning. För att säkerställa samverkan är det bäst att spara skript i Unicode-format med en struktur.

> [!IMPORTANT]
> Andra verktyg som du kan använda för att trycka PowerShell-skript kan påverkas av kodnings alternativen eller koda om skripten till en annan kodning.

### <a name="existing-scripts"></a>Befintliga skript

Skript som redan finns i fil systemet kan behöva kodas om till den nya valda kodningen. I det nedre fältet VS Code ser du etiketten UTF-8. Klicka på den för att öppna åtgärds fältet och välj **Spara med kodning** . Nu kan du välja en ny kodning för filen. Se [kod för vs Code][] för fullständiga instruktioner.

Om du behöver Omkoda flera filer kan du använda följande skript:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell (Integrated Scripting Environment)

Om du också redigerar skript med hjälp av PowerShell ISE måste du synkronisera dina kodnings inställningar där.

ISE bör svara på en struktur, men det är också möjligt att använda reflektion för att [Ange kodningen](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Observera att detta inte behålls mellan starter.

### <a name="source-control-software"></a>Käll kontroll program vara

Vissa käll kontroll verktyg, till exempel git, ignorera kodningar; git spårar bara bytena. Andra, som Azure DevOps eller Mercurial, kanske inte. Även vissa git-baserade verktyg är beroende av avkodning av text.

I så fall måste du se till att:

- Konfigurera text kodningen i käll kontrollen så att den matchar din VS Code-konfiguration.
- Se till att alla filer är markerade med käll kontroll i relevant kodning.
- Försiktig ändringar i kodningen som tagits emot via käll kontroll. Ett nyckel tecken på detta är en skillnad som indikerar ändringar men där inget verkar ha ändrats (eftersom byte har tecken, men inte).

### <a name="collaborators-environments"></a>Samarbets miljöer

Se till att dina medarbetare på alla filer som du delar inte har några inställningar som åsidosätter din kodning genom att koda om PowerShell-filer om du vill konfigurera käll kontroll.

### <a name="other-programs"></a>Andra program

Alla andra program som läser eller skriver ett PowerShell-skript kan koda det igen.

Några exempel är:

- Använd Urklipp för att kopiera och klistra in ett skript. Detta är vanligt i scenarier som:
  - Kopiera ett skript till en virtuell dator
  - Kopiera ett skript från ett e-postmeddelande eller en webb sida
  - Kopiera ett skript till eller från ett Microsoft Word-eller PowerPoint-dokument
- Andra text redigerare, till exempel:
  - Anteckningar
  - vim
  - Andra PowerShell-skript redigerare
- Text redigerings verktyg, t. ex.:
  - `Get-Content`/`Set-Content`/`Out-File`
  - Operatorer för PowerShell-omdirigering som `>` och `>>`
  - `sed`/`awk`
- Fil överförings program, t. ex.:
  - En webbläsare, vid hämtning av skript
  - En fil resurs

Några av dessa verktyg behandlar byte i stället för text, men andra erbjuder kodnings konfigurationer. I de fall där du behöver konfigurera en kodning måste du göra den densamma som din redigerings kodning för att förhindra problem.

## <a name="other-resources-on-encoding-in-powershell"></a>Andra resurser för kodning i PowerShell

Det finns några andra bra inlägg på kodning och konfigurering av kodning i PowerShell som är värda en läsning:

- [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding)
- [@mklement0][sammanfattande av PowerShell-kodning på StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Tidigare problem som öppnats vid VS-Code-PowerShell för kodnings problem:
  - [#1308](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [Den klassiska _Joel om program vara_ skriver upp om Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Kodning i .NET standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-ordnings markering]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Språk server protokoll]: https://microsoft.github.io/language-server-protocol/
[VS Code-kodning]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[Gremlins-Spårare]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
