---
title: Förstå filkodning i VSCode och PowerShell
description: Konfigurera Filkodning i VSCode och PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: ec06d8f5d446a92e6cd9d2d70b11260d1d0afda8
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320412"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a>Förstå filkodning i VSCode och PowerShell

När du använder VS Code för att skapa och redigera PowerShell-skript, är det viktigt att dina filer sparas med Kodningsformatet för rätt tecken.

## <a name="what-is-file-encoding-and-why-is-it-important"></a>Vad är Filkodning och varför är det viktigt?

VSCode hanterar gränssnittet mellan en mänsklig anger teckensträngar till en buffert och läsning/skrivning block byte i filsystemet. När en fil sparas i VSCode används en textkodning för att göra detta.

När PowerShell körs ett skript konvertera den på samma sätt kan byte i en fil till tecken att rekonstruera filen i ett PowerShell-program. Eftersom VSCode skriver filen och PowerShell läser filen, måste de använda samma kodning system. Den här processen för att tolka ett PowerShell-skript slutar: *byte* -> *tecken* -> *token*  ->   *abstrakt syntax trädet* -> *körning*.

Både VSCode och PowerShell installeras med en användningstyperna kodning standardkonfiguration. Standardkodning som används av PowerShell har dock ändrats med lanseringen av PowerShell Core (v6.x). Om du vill kontrollera att du har inga problem med PowerShell eller PowerShell-tillägget i VSCode, måste du konfigurera inställningarna för VSCode och PowerShell korrekt.

## <a name="common-causes-of-encoding-issues"></a>Vanliga orsaker till kodningsproblem

Kodning problem vid kodning av VSCode eller skriptfilen inte matchar den förväntade kodningen av PowerShell. Det finns inget sätt för PowerShell för att automatiskt avgöra Filkodning.

Det är mer sannolikt att ha kodning problem när du använder tecken som inte finns i den [7-bitars ASCII-teckenuppsättningen](https://ascii.cl/). Till exempel:

- Accent över latinska tecken (`É`, `ü`)
- Icke-latinska tecken som Kyrillisk (`Д`, `Ц`)
- Han kinesiska (`脚`, `本`)

Vanliga orsaker till kodningsproblem är:

- Kodningar av VSCode och PowerShell har inte ändrats från standardvärdena. För PowerShell 5.1 och under standard skiljer kodning sig från Vscode's.
- Någon annan redigerare som har öppnat och skriva över filen i en ny kodning. Detta händer ofta med ISE.
- Filen checkas in källkontroll i en kodning som skiljer sig från vilka VSCode eller PowerShell förväntas. Detta kan inträffa när medarbetare använder redigerare med olika konfigurationer för kodning.

### <a name="how-to-tell-when-you-have-encoding-issues"></a>Så här avgör du när du har kodningsproblem

Ofta kodningsfel uppträder som parsa fel i skript. Om du hittar onormalt teckensekvenser i skriptet kan vara detta problemet. I exemplet nedan ett tankstreck (`–`) visas som tecknen `â€“`:

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

Det här problemet uppstår eftersom VSCode kodar tecknet `–` i UTF-8 som byte `0xE2 0x80 0x93`.
När dessa byte avkodas som Windows-1252, de tolkas som tecknen `â€“`.

Vissa onormalt teckensekvenser som kan visas är:

<!-- markdownlint-disable MD038 -->
- `â€“` Istället för `–`
- `â€”` Istället för `—`
- `Ã„2` Istället för `Ä`
- `Â` i stället för ` ` (ett hårt blanksteg)
- `Ã©` Istället för `é`
<!-- markdownlint-enable MD038 -->

Det här praktiska [referens](https://www.i18nqa.com/debug/utf8-debug.html) visar en lista över vanliga mönster som indikerar att en UTF-8/Windows-1252 kodningsproblem.

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a>Hur PowerShell-tillägget i VSCode interagerar med kodningar

Tillägget PowerShell samverkar med skript i ett antal olika sätt:

1. När skript redigeras i VSCode, skickas innehållet från VSCode till tillägget. Den [språk serverprotokoll][] innehåller principer för att den här innehåll som överförs i UTF-8. Det är därför inte möjligt för tillägget att hämta fel kodning.
2. När skript körs direkt i integrerad konsol, är de läsa från filen med PowerShell direkt. Om PowerShell-kodning skiljer sig från Vscodes går något fel här.
3. När ett skript som är öppen i VSCode refererar till ett annat skript som inte är öppen i VSCode, använder tillägget till att läsa in den skriptet innehåll från filsystemet. Tillägget PowerShell UTF-8-kodning som standard, men använder [byte-ordningsmarkering][], eller BOM, identifiering för att välja rätt kodning.

Problemet uppstår när förutsatt att kodning av BOM mindre format (t.ex. [UTF-8][] utan BOM och [Windows-1252][]).
PowerShell-tillägget som standard UTF-8. Tillägget kan inte ändra Vscodes kodningsinställningar.
Mer information finns i [utfärda #824](https://github.com/Microsoft/vscode/issues/824).

## <a name="choosing-the-right-encoding"></a>Välja rätt kodning

Olika system och program kan använda olika kodningar:

- I .NET Standard är på webben och i Linux-världen UTF-8 nu den dominerande kodningen.
- Många .NET Framework-program använder [UTF-16][]. Historiska skäl, kallas ibland ”Unicode”, en term där du nu refererar till den mest omfattande [standard](https://en.wikipedia.org/wiki/Unicode) som innehåller både UTF-8 och UTF-16.
- På Windows fortsätta många interna program som skrevs innan Unicode att använda Windows-1252 som standard.

Unicode-kodningar har också konceptet med en byte-ordning markera (BOM). Strukturer inträffa i början av texten som talar om för en avkodare vilken kodning med hjälp av texten. För multibyte kodningar Strukturen anger även [endianness](https://en.wikipedia.org/wiki/Endianness) för kodningen. Strukturer är avsedda att vara byte som skrivfel uppstår i icke-Unicode-text, vilket gör att en rimlig gissning att texten är Unicode när det finns en struktur.

Strukturer är valfria och antagandet är inte lika populära Linux över hela världen eftersom en pålitlig konvention UTF-8 används överallt. De flesta Linux-program förutsätter att mata in text är kodat i UTF-8. Även om många program i Linux identifierar och hanterar en struktur, ett tal inte, vilket leder till artefakter i texten ändras med dessa program.

**Därför**:

- Om du arbetar huvudsakligen med Windows-program och Windows PowerShell, bör du föredrar en kodning som UTF-8 med BOM eller UTF-16.
- Om du arbetar på olika plattformar, bör du föredrar UTF-8 med BOM.
- Om du arbetar huvudsakligen i Linux-associerade kontexter bör du föredrar UTF-8 utan BOM.
- Windows-1252 och latin 1 är i stort sett äldre kodningar som du bör undvika att om möjligt.
  Men kan vissa äldre Windows-program bero på dem.
- Det är också värt att skriptet är att registrera [encoding-beroende](https://github.com/PowerShell/PowerShell/issues/3466), vilket innebär att en ändring av kodning på ett signerade skript kräver uppsägning.

## <a name="configuring-vscode"></a>Konfigurera VSCode

Vscodes standardkodning är UTF-8 utan BOM.

Ange [Vscodes kodning][]går du till inställningar för VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) och ange den `"files.encoding"` inställningen:

```json
"files.encoding": "utf8bom"
```

Några möjliga värden är:

- `utf8`: [UTF-8] utan BOM
- `utf8bom`: [UTF-8] med BOM
- `utf16le`: Little endian [UTF-16]
- `utf16be`: Big endian [UTF-16]
- `windows1252`: [Windows-1252]

Du bör få en listruta för detta i vyn GUI eller visa Completion-händelser för den i JSON.

Du kan också lägga till följande Autodetect kodning när det är möjligt:

```json
"files.autoGuessEncoding": true
```

Om du inte vill att dessa inställningar påverkar alla filtyper, kan VSCode också konfigurationer per språk. Skapa en språkspecifik inställning genom att ange inställningar i en `[<language-name>]` fält. Till exempel:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a>Konfigurera PowerShell

PowerShell-standardkodning varierar beroende på version:

- I PowerShell 6 + är standardkodning UTF-8 utan BOM på alla plattformar.
- Windows PowerShell, standardkodning är vanligtvis Windows-1252, en utökning av [latin 1][], även kallad ISO 8859-1.

Du kan hitta din standardkodning med detta i PowerShell 5 +:

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

Följande [skriptet](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan användas för att fastställa vad kodning PowerShell-sessionen härleder för ett skript utan en struktur.

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

Det är möjligt att konfigurera PowerShell för att använda en viss kodning som vanligtvis med profilinställningar. Se följande artiklar:

- [@mklement0]'s [svar om PowerShell kodning på StackOverflow](https://stackoverflow.com/a/40098904).
- [@rkeithhill]'s [blogginlägget om hantering av BOM utan UTF-8 indata i PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).

Det går inte att tvinga PowerShell för att använda en specifik inkommande kodning. PowerShell 5.1 och under Windows-1252-kodning när det finns inga BOM som standard. Det är bäst att spara skript i en Unicode-format med en struktur för samverkan skäl.

> [!IMPORTANT]
> Verktyg från någon annan har den touch PowerShell skript kan påverkas av valen kodning eller koda om skripten till en annan kodning.

### <a name="existing-scripts"></a>Befintliga skript

Skript redan i filsystemet kan behöva kodas igen till din nya valda kodning. I det nedre fältet för VSCode visas etiketten UTF-8. Klicka om du vill öppna Åtgärdsfältet och välj **spara med kodning**. Du kan nu välja en ny kodning för filen. Se [Vscodes kodning][] fullständiga instruktioner.

Om du vill koda om flera filer kan använda du följande skript:

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a>PowerShell Integrated Scripting Environment (ISE)

Du behöver synkronisera dina kodning inställningar om du också redigera skript med hjälp av PowerShell ISE.

ISE bör respektera en struktur, men det är också möjligt att använda reflektion till [Ange kodning](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).
Observera att detta skulle sparas mellan omstarter.

### <a name="source-control-software"></a>Program för källkontroll

Vissa verktyg för källa kontroll, till exempel git, Ignorera kodningar; Git spårar bara byte.
Andra, kanske som Azure DevOps- eller Mercurial, inte. Även vissa git-baserade verktyg är beroende av avkodning text.

När så är fallet kontrollerar du:

- Konfigurera textkodning i din källkontroll för att matcha din VSCode-konfiguration.
- Se till att alla filer är markerade i källkontrollen i den relevanta kodningen.
- Vara försiktig med ändringar i kodningen emot via källkontroll. Ett nyckel tecken på detta är en diff som anger ändringar men där ingenting verkar har ändrats (eftersom byte har men har inte).

### <a name="collaborators-environments"></a>Medarbetare-miljöer

Se till att dina medarbetare på alla filer som du delar inte har inställningar som åsidosätter kodningen genom att behöva koda PowerShell-filer på konfigurerar källkontroll.

### <a name="other-programs"></a>Andra program

Alla andra program som läser eller skriver ett PowerShell-skript kan koda om den.

Några exempel är:

- Du kan använda Urklipp för att kopiera och klistra in ett skript. Detta är vanligt i scenarier som:
  - Kopierar ett skript till en virtuell dator
  - Kopierar ett skript från ett e-postmeddelande eller en webbsida
  - Kopierar ett skript till eller från ett Microsoft Word- eller PowerPoint-dokument
- Andra textredigerare, till exempel:
  - Anteckningar
  - vim
  - Alla andra PowerShell-Skriptredigeraren
- Redigera verktyg, som text:
  - `Get-Content`/`Set-Content`/`Out-File`
  - PowerShell-omdirigering operatörer som `>` och `>>`
  - `sed`/`awk`
- Filen överföringsprogram, t.ex.:
  - En webbläsare, när du laddar ned skript
  - En filresurs

Vissa av verktygen kan hantera i byte i stället för text, men andra erbjuder kodning konfigurationer. I de fall där du behöver konfigurera en kodning kan behöva du blir samma som redigeringsprogram kodning för att förhindra problem.

## <a name="other-resources-on-encoding-in-powershell"></a>Andra resurser på kodning i PowerShell

Det finns några andra bra inlägg på kodning och konfigurera kodning i PowerShell som är värda att en läsning:

- [@mklement0]'s [sammanfattning av PowerShell kodning på StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)
- Tidigare problem öppnas på vscode-PowerShell för kodning problem:
  - [#1308](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [#1628](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [#1680](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [#1744](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [#1751](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [Klassiskt *Johan på programvara* Skriv upp om Unicode](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [Kodning i .NET Standard](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-ordningsmarkering]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[språk serverprotokoll]: https://microsoft.github.io/language-server-protocol/
[Vscodes kodning]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
