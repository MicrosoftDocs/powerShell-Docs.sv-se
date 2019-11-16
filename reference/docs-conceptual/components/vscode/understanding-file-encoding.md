---
title: Förstå filkodning i VSCode och PowerShell
description: Konfigurera fil kodning i VSCode och PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: 3283e1262c8eb26906429ecf195cfa0b122b330f
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117405"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="b845f-103">Förstå filkodning i VSCode och PowerShell</span><span class="sxs-lookup"><span data-stu-id="b845f-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="b845f-104">När du använder VS Code för att skapa och redigera PowerShell-skript är det viktigt att filerna sparas med rätt tecken kodnings format.</span><span class="sxs-lookup"><span data-stu-id="b845f-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="b845f-105">Vad är fil kodning och varför är det viktigt?</span><span class="sxs-lookup"><span data-stu-id="b845f-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="b845f-106">VSCode hanterar gränssnittet mellan en mänsklig genom att ange tecken strängar i en buffert och läsning/skrivning av byte till fil systemet.</span><span class="sxs-lookup"><span data-stu-id="b845f-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="b845f-107">När VSCode sparar en fil använder den en text kodning för att avgöra vilka byte som varje tecken blir.</span><span class="sxs-lookup"><span data-stu-id="b845f-107">When VSCode saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span>

<span data-ttu-id="b845f-108">När PowerShell kör ett skript måste det på samma sätt konvertera byte i en fil till tecken för att återskapa filen till ett PowerShell-program.</span><span class="sxs-lookup"><span data-stu-id="b845f-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="b845f-109">Eftersom VSCode skriver filen och PowerShell läser in filen måste de använda samma kodnings system.</span><span class="sxs-lookup"><span data-stu-id="b845f-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="b845f-110">Den här processen för att parsa ett PowerShell-skript går: *byte* -> *tecken* -> *tokens* -> *abstrakta sökträd* -> *körning*.</span><span class="sxs-lookup"><span data-stu-id="b845f-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="b845f-111">Både VSCode och PowerShell installeras med en lämpliga standard kodnings konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b845f-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="b845f-112">Den standard kodning som används av PowerShell har dock ändrats med versionen av PowerShell Core (V6. x).</span><span class="sxs-lookup"><span data-stu-id="b845f-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="b845f-113">För att se till att du inte har några problem med PowerShell eller PowerShell-tillägget i VSCode, måste du konfigurera dina VSCode-och PowerShell-inställningar korrekt.</span><span class="sxs-lookup"><span data-stu-id="b845f-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="b845f-114">Vanliga orsaker till kodnings problem</span><span class="sxs-lookup"><span data-stu-id="b845f-114">Common causes of encoding issues</span></span>

<span data-ttu-id="b845f-115">Kodnings problem inträffar när kodningen för VSCode eller skript filen inte matchar den förväntade kodningen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b845f-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="b845f-116">Det finns inget sätt för PowerShell att automatiskt avgöra fil kodningen.</span><span class="sxs-lookup"><span data-stu-id="b845f-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="b845f-117">Det är mer troligt att du har problem med kodningen när du använder tecken som inte är i [ASCII-teckenuppsättningen med sju bitar](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="b845f-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="b845f-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="b845f-118">For example:</span></span>

- <span data-ttu-id="b845f-119">Utökade tecken som inte är bokstäver, t. ex. tank streck (`—`), hårt blank steg (` `) eller vänster dubbla citat tecken (`“`)</span><span class="sxs-lookup"><span data-stu-id="b845f-119">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`“`)</span></span>
- <span data-ttu-id="b845f-120">Accenttecken (latinskt) tecken (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="b845f-120">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="b845f-121">Icke-latinska tecken som kyrilliska (`Д``Ц`)</span><span class="sxs-lookup"><span data-stu-id="b845f-121">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="b845f-122">CJK-tecken (`本`, `화`, `が`)</span><span class="sxs-lookup"><span data-stu-id="b845f-122">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="b845f-123">Vanliga orsaker till kodnings problem är:</span><span class="sxs-lookup"><span data-stu-id="b845f-123">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="b845f-124">Kodningarna för VSCode och PowerShell har inte ändrats från sina standardvärden.</span><span class="sxs-lookup"><span data-stu-id="b845f-124">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="b845f-125">För PowerShell 5,1 och lägre är standard kodningen annorlunda än VSCode.</span><span class="sxs-lookup"><span data-stu-id="b845f-125">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="b845f-126">En annan redigerare har öppnat och överskrivit filen i en ny kodning.</span><span class="sxs-lookup"><span data-stu-id="b845f-126">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="b845f-127">Detta händer ofta med ISE.</span><span class="sxs-lookup"><span data-stu-id="b845f-127">This often happens with the ISE.</span></span>
- <span data-ttu-id="b845f-128">Filen checkas in i käll kontroll i en kodning som skiljer sig från vad VSCode eller PowerShell förväntar sig.</span><span class="sxs-lookup"><span data-stu-id="b845f-128">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="b845f-129">Detta kan inträffa när medarbetare använder redigerare med olika kodnings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b845f-129">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="b845f-130">Så här ser du när du har kodnings problem</span><span class="sxs-lookup"><span data-stu-id="b845f-130">How to tell when you have encoding issues</span></span>

<span data-ttu-id="b845f-131">Kodnings fel visas ofta som tolknings fel i skript.</span><span class="sxs-lookup"><span data-stu-id="b845f-131">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="b845f-132">Om du hittar konstig teckensekvens i skriptet kan det vara problemet.</span><span class="sxs-lookup"><span data-stu-id="b845f-132">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="b845f-133">I exemplet nedan visas ett kort streck (`–`) som de tecken `â€“`:</span><span class="sxs-lookup"><span data-stu-id="b845f-133">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="b845f-134">Det här problemet beror på att VSCode kodar tecken `–` i UTF-8 som de byte `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="b845f-134">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="b845f-135">När dessa byte avkodas som Windows-1252 tolkas de som de tecken som `â€“`.</span><span class="sxs-lookup"><span data-stu-id="b845f-135">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="b845f-136">Några konstig teckensekvens som du kan se är:</span><span class="sxs-lookup"><span data-stu-id="b845f-136">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="b845f-137">`â€“` i stället för `–`</span><span class="sxs-lookup"><span data-stu-id="b845f-137">`â€“` instead of `–`</span></span>
- <span data-ttu-id="b845f-138">`â€”` i stället för `—`</span><span class="sxs-lookup"><span data-stu-id="b845f-138">`â€”` instead of `—`</span></span>
- <span data-ttu-id="b845f-139">`Ã„2` i stället för `Ä`</span><span class="sxs-lookup"><span data-stu-id="b845f-139">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="b845f-140">`Â` i stället för ` ` (ett hårt blank steg)</span><span class="sxs-lookup"><span data-stu-id="b845f-140">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="b845f-141">`Ã©` i stället för `é`</span><span class="sxs-lookup"><span data-stu-id="b845f-141">`Ã©` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="b845f-142">Den här praktiska [referensen](https://www.i18nqa.com/debug/utf8-debug.html) listar vanliga mönster som indikerar ett kodnings problem med UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="b845f-142">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="b845f-143">Hur PowerShell-tillägget i VSCode interagerar med kodningar</span><span class="sxs-lookup"><span data-stu-id="b845f-143">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="b845f-144">PowerShell-tillägget samverkar med skript på flera olika sätt:</span><span class="sxs-lookup"><span data-stu-id="b845f-144">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="b845f-145">När skript redige ras i VSCode skickas innehållet av VSCode till tillägget.</span><span class="sxs-lookup"><span data-stu-id="b845f-145">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="b845f-146">[Språk server protokoll][] bestämmer att det här innehållet överförs i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b845f-146">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="b845f-147">Därför är det inte möjligt för tillägget att få fel kodning.</span><span class="sxs-lookup"><span data-stu-id="b845f-147">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="b845f-148">När skript körs direkt i den integrerade konsolen läses de in från filen med PowerShell direkt.</span><span class="sxs-lookup"><span data-stu-id="b845f-148">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="b845f-149">Om PowerShell-kodning skiljer sig från VSCode kan något gå fel här.</span><span class="sxs-lookup"><span data-stu-id="b845f-149">If PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="b845f-150">När ett skript som är öppet i VSCode refererar till ett annat skript som inte är öppet i VSCode, återgår tillägget till att läsa in skriptets innehåll från fil systemet.</span><span class="sxs-lookup"><span data-stu-id="b845f-150">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="b845f-151">PowerShell-tillägget är standardvärdet UTF-8-kodning, men använder [byte-ordnings markering][], eller struktur, identifiering för att välja rätt kodning.</span><span class="sxs-lookup"><span data-stu-id="b845f-151">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="b845f-152">Problemet inträffar när du antar kodningen för BOM-mindre format (t. ex. [UTF-8][] utan strukturliste och [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="b845f-152">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="b845f-153">PowerShell-tillägget är standardvärdet UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b845f-153">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="b845f-154">Tillägget kan inte ändra VSCode kodnings inställningar.</span><span class="sxs-lookup"><span data-stu-id="b845f-154">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="b845f-155">Mer information finns i avsnittet om [problem #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="b845f-155">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="b845f-156">Välja rätt kodning</span><span class="sxs-lookup"><span data-stu-id="b845f-156">Choosing the right encoding</span></span>

<span data-ttu-id="b845f-157">Olika system och program kan använda olika kodningar:</span><span class="sxs-lookup"><span data-stu-id="b845f-157">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="b845f-158">I .NET standard, på webben och i Linux-världen är UTF-8 nu den dominerande kodningen.</span><span class="sxs-lookup"><span data-stu-id="b845f-158">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="b845f-159">I många .NET Framework program används [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="b845f-159">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="b845f-160">Av historiska skäl kallas detta ibland "Unicode", en term som nu refererar till en bred [standard](https://en.wikipedia.org/wiki/Unicode) som innehåller både UTF-8 och UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b845f-160">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="b845f-161">I Windows fortsätter många inbyggda program som i förväg med Unicode att använda Windows-1252 som standard.</span><span class="sxs-lookup"><span data-stu-id="b845f-161">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="b845f-162">Unicode-kodningar har också begreppet ett byte-ordnings tecken (BOM).</span><span class="sxs-lookup"><span data-stu-id="b845f-162">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="b845f-163">Strukturer sker i början av texten för att ange en avkodare som kodar texten.</span><span class="sxs-lookup"><span data-stu-id="b845f-163">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="b845f-164">För kodningar med flera byte anger strukturen också [endian](https://en.wikipedia.org/wiki/Endianness) -koden.</span><span class="sxs-lookup"><span data-stu-id="b845f-164">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="b845f-165">Strukturer är utformade för att vara byte som sällan förekommer i icke-Unicode-text, vilket ger en rimlig gissning att texten är Unicode när en struktur finns.</span><span class="sxs-lookup"><span data-stu-id="b845f-165">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="b845f-166">Strukturer är valfria och deras införande är inte lika populärt i Linux-världen, eftersom en pålitlig konvention av UTF-8 används överallt.</span><span class="sxs-lookup"><span data-stu-id="b845f-166">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="b845f-167">De flesta Linux-program förutsätter att text ingången kodas i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b845f-167">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="b845f-168">Många Linux-program kommer att känna igen och hantera en struktur korrekt, men en siffra gör inte, vilket leder till artefakter i text som manipuleras med dessa program.</span><span class="sxs-lookup"><span data-stu-id="b845f-168">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="b845f-169">**Därför**:</span><span class="sxs-lookup"><span data-stu-id="b845f-169">**Therefore**:</span></span>

- <span data-ttu-id="b845f-170">Om du arbetar i första hand med Windows-program och Windows PowerShell bör du föredra en kodning som UTF-8 med BOM eller UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b845f-170">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="b845f-171">Om du arbetar på olika plattformar bör du hellre använda UTF-8 med BOM.</span><span class="sxs-lookup"><span data-stu-id="b845f-171">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="b845f-172">Om du arbetar huvudsakligen i Linux-associerade kontexter bör du hellre UTF-8 utan struktur.</span><span class="sxs-lookup"><span data-stu-id="b845f-172">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="b845f-173">Windows-1252 och Latin-1 är i princip äldre kodningar som du bör undvika om möjligt.</span><span class="sxs-lookup"><span data-stu-id="b845f-173">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="b845f-174">Vissa äldre Windows-program kan dock vara beroende av dem.</span><span class="sxs-lookup"><span data-stu-id="b845f-174">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="b845f-175">Det är också värt att notera att skript signering är [kodnings beroende](https://github.com/PowerShell/PowerShell/issues/3466), vilket innebär att en ändring av kodningen på ett signerat skript kräver omregistrering.</span><span class="sxs-lookup"><span data-stu-id="b845f-175">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="b845f-176">Konfigurera VSCode</span><span class="sxs-lookup"><span data-stu-id="b845f-176">Configuring VSCode</span></span>

<span data-ttu-id="b845f-177">VSCode standard encoding är UTF-8 utan struktur.</span><span class="sxs-lookup"><span data-stu-id="b845f-177">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="b845f-178">Om du vill ange [VSCode kodning][]går du till VSCode-inställningarna (<kbd>CTRL</kbd>+<kbd>,</kbd>) och anger inställningen `"files.encoding"`:</span><span class="sxs-lookup"><span data-stu-id="b845f-178">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="b845f-179">Några möjliga värden är:</span><span class="sxs-lookup"><span data-stu-id="b845f-179">Some possible values are:</span></span>

- <span data-ttu-id="b845f-180">`utf8`: [UTF-8] utan struktur</span><span class="sxs-lookup"><span data-stu-id="b845f-180">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="b845f-181">`utf8bom`: [UTF-8] med struktur</span><span class="sxs-lookup"><span data-stu-id="b845f-181">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="b845f-182">`utf16le`: lite endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="b845f-182">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="b845f-183">`utf16be`: big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="b845f-183">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="b845f-184">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="b845f-184">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="b845f-185">Du bör få en listruta för detta i vyn grafiskt eller om du har slutfört den i JSON-vyn.</span><span class="sxs-lookup"><span data-stu-id="b845f-185">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="b845f-186">Du kan också lägga till följande för att automatiskt identifiera kodning när det är möjligt:</span><span class="sxs-lookup"><span data-stu-id="b845f-186">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="b845f-187">Om du inte vill att de här inställningarna ska påverka alla filtyper kan VSCode också använda konfigurationer för flera språk.</span><span class="sxs-lookup"><span data-stu-id="b845f-187">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="b845f-188">Skapa en språkspecifik inställning genom att lägga till inställningar i ett `[<language-name>]`s fält.</span><span class="sxs-lookup"><span data-stu-id="b845f-188">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="b845f-189">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="b845f-189">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="b845f-190">Konfigurera PowerShell</span><span class="sxs-lookup"><span data-stu-id="b845f-190">Configuring PowerShell</span></span>

<span data-ttu-id="b845f-191">PowerShell: s standard kodning varierar beroende på version:</span><span class="sxs-lookup"><span data-stu-id="b845f-191">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="b845f-192">I PowerShell 6 + är standard kodningen UTF-8 utan struktur på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="b845f-192">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="b845f-193">I Windows PowerShell är standard kodningen vanligt vis Windows-1252, ett tillägg på [Latin-1][], även kallat ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="b845f-193">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="b845f-194">I PowerShell 5 + kan du hitta din standard kodning med följande:</span><span class="sxs-lookup"><span data-stu-id="b845f-194">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="b845f-195">Följande [skript](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan användas för att avgöra vilken kodning din PowerShell-session härleds för ett skript utan en struktur.</span><span class="sxs-lookup"><span data-stu-id="b845f-195">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="b845f-196">Det är möjligt att konfigurera PowerShell för att använda en specifik kodning som oftare använder profil inställningar.</span><span class="sxs-lookup"><span data-stu-id="b845f-196">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="b845f-197">Se följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="b845f-197">See the following articles:</span></span>

- <span data-ttu-id="b845f-198">[@mklement0s ] [svar om PowerShell-kodning på StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="b845f-198">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="b845f-199">[@rkeithhills ] [blogg inlägg om att hantera STRUKTURLISTE-mindre UTF-8-indata i PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="b845f-199">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="b845f-200">Det går inte att tvinga PowerShell att använda en speciell kodning för inkodning.</span><span class="sxs-lookup"><span data-stu-id="b845f-200">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="b845f-201">PowerShell 5,1 och nedan används som standard för Windows-1252-kodning när det inte finns någon struktur.</span><span class="sxs-lookup"><span data-stu-id="b845f-201">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="b845f-202">Av samverkans orsaker är det bäst att spara skript i Unicode-format med en struktur.</span><span class="sxs-lookup"><span data-stu-id="b845f-202">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b845f-203">Andra verktyg som du kan använda för att trycka PowerShell-skript kan påverkas av kodnings alternativen eller koda om skripten till en annan kodning.</span><span class="sxs-lookup"><span data-stu-id="b845f-203">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="b845f-204">Befintliga skript</span><span class="sxs-lookup"><span data-stu-id="b845f-204">Existing scripts</span></span>

<span data-ttu-id="b845f-205">Skript som redan finns i fil systemet kan behöva kodas om till den nya valda kodningen.</span><span class="sxs-lookup"><span data-stu-id="b845f-205">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="b845f-206">I det nedre fältet i VSCode visas etiketten UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b845f-206">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="b845f-207">Klicka på den för att öppna åtgärds fältet och välj **Spara med kodning**.</span><span class="sxs-lookup"><span data-stu-id="b845f-207">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="b845f-208">Nu kan du välja en ny kodning för filen.</span><span class="sxs-lookup"><span data-stu-id="b845f-208">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="b845f-209">Se [VSCode kodning][] för fullständiga instruktioner.</span><span class="sxs-lookup"><span data-stu-id="b845f-209">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="b845f-210">Om du behöver Omkoda flera filer kan du använda följande skript:</span><span class="sxs-lookup"><span data-stu-id="b845f-210">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="b845f-211">PowerShell (Integrated Scripting Environment)</span><span class="sxs-lookup"><span data-stu-id="b845f-211">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="b845f-212">Om du också redigerar skript med hjälp av PowerShell ISE måste du synkronisera dina kodnings inställningar där.</span><span class="sxs-lookup"><span data-stu-id="b845f-212">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="b845f-213">ISE bör svara på en struktur, men det är också möjligt att använda reflektion för att [Ange kodningen](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="b845f-213">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="b845f-214">Observera att detta inte behålls mellan starter.</span><span class="sxs-lookup"><span data-stu-id="b845f-214">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="b845f-215">Käll kontroll program vara</span><span class="sxs-lookup"><span data-stu-id="b845f-215">Source control software</span></span>

<span data-ttu-id="b845f-216">Vissa käll kontroll verktyg, till exempel git, ignorera kodningar; git spårar bara bytena.</span><span class="sxs-lookup"><span data-stu-id="b845f-216">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="b845f-217">Andra, som Azure DevOps eller Mercurial, kanske inte.</span><span class="sxs-lookup"><span data-stu-id="b845f-217">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="b845f-218">Även vissa git-baserade verktyg är beroende av avkodning av text.</span><span class="sxs-lookup"><span data-stu-id="b845f-218">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="b845f-219">I så fall måste du se till att:</span><span class="sxs-lookup"><span data-stu-id="b845f-219">When this is the case, make sure you:</span></span>

- <span data-ttu-id="b845f-220">Konfigurera text kodningen i käll kontrollen så att den matchar din VSCode-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b845f-220">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="b845f-221">Se till att alla filer är markerade med käll kontroll i relevant kodning.</span><span class="sxs-lookup"><span data-stu-id="b845f-221">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="b845f-222">Försiktig ändringar i kodningen som tagits emot via käll kontroll.</span><span class="sxs-lookup"><span data-stu-id="b845f-222">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="b845f-223">Ett nyckel tecken på detta är en skillnad som indikerar ändringar men där inget verkar ha ändrats (eftersom byte har tecken, men inte).</span><span class="sxs-lookup"><span data-stu-id="b845f-223">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="b845f-224">Samarbets miljöer</span><span class="sxs-lookup"><span data-stu-id="b845f-224">Collaborators' environments</span></span>

<span data-ttu-id="b845f-225">Se till att dina medarbetare på alla filer som du delar inte har några inställningar som åsidosätter din kodning genom att koda om PowerShell-filer om du vill konfigurera käll kontroll.</span><span class="sxs-lookup"><span data-stu-id="b845f-225">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="b845f-226">Andra program</span><span class="sxs-lookup"><span data-stu-id="b845f-226">Other programs</span></span>

<span data-ttu-id="b845f-227">Alla andra program som läser eller skriver ett PowerShell-skript kan koda det igen.</span><span class="sxs-lookup"><span data-stu-id="b845f-227">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="b845f-228">Några exempel är:</span><span class="sxs-lookup"><span data-stu-id="b845f-228">Some examples are:</span></span>

- <span data-ttu-id="b845f-229">Använd Urklipp för att kopiera och klistra in ett skript.</span><span class="sxs-lookup"><span data-stu-id="b845f-229">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="b845f-230">Detta är vanligt i scenarier som:</span><span class="sxs-lookup"><span data-stu-id="b845f-230">This is common in scenarios like:</span></span>
  - <span data-ttu-id="b845f-231">Kopiera ett skript till en virtuell dator</span><span class="sxs-lookup"><span data-stu-id="b845f-231">Copying a script into a VM</span></span>
  - <span data-ttu-id="b845f-232">Kopiera ett skript från ett e-postmeddelande eller en webb sida</span><span class="sxs-lookup"><span data-stu-id="b845f-232">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="b845f-233">Kopiera ett skript till eller från ett Microsoft Word-eller PowerPoint-dokument</span><span class="sxs-lookup"><span data-stu-id="b845f-233">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="b845f-234">Andra text redigerare, till exempel:</span><span class="sxs-lookup"><span data-stu-id="b845f-234">Other text editors, such as:</span></span>
  - <span data-ttu-id="b845f-235">Block</span><span class="sxs-lookup"><span data-stu-id="b845f-235">Notepad</span></span>
  - <span data-ttu-id="b845f-236">vim</span><span class="sxs-lookup"><span data-stu-id="b845f-236">vim</span></span>
  - <span data-ttu-id="b845f-237">Andra PowerShell-skript redigerare</span><span class="sxs-lookup"><span data-stu-id="b845f-237">Any other PowerShell script editor</span></span>
- <span data-ttu-id="b845f-238">Text redigerings verktyg, t. ex.:</span><span class="sxs-lookup"><span data-stu-id="b845f-238">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="b845f-239">Operatorer för PowerShell-omdirigering som `>` och `>>`</span><span class="sxs-lookup"><span data-stu-id="b845f-239">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="b845f-240">Fil överförings program, t. ex.:</span><span class="sxs-lookup"><span data-stu-id="b845f-240">File transfer programs, like:</span></span>
  - <span data-ttu-id="b845f-241">En webbläsare, vid hämtning av skript</span><span class="sxs-lookup"><span data-stu-id="b845f-241">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="b845f-242">En fil resurs</span><span class="sxs-lookup"><span data-stu-id="b845f-242">A file share</span></span>

<span data-ttu-id="b845f-243">Några av dessa verktyg behandlar byte i stället för text, men andra erbjuder kodnings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="b845f-243">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="b845f-244">I de fall där du behöver konfigurera en kodning måste du göra den densamma som din redigerings kodning för att förhindra problem.</span><span class="sxs-lookup"><span data-stu-id="b845f-244">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="b845f-245">Andra resurser för kodning i PowerShell</span><span class="sxs-lookup"><span data-stu-id="b845f-245">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="b845f-246">Det finns några andra bra inlägg på kodning och konfigurering av kodning i PowerShell som är värda en läsning:</span><span class="sxs-lookup"><span data-stu-id="b845f-246">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="b845f-247">[@mklement0] [Sammanfattning av PowerShell-kodning på StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="b845f-247">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="b845f-248">Tidigare problem öppnades på VSCode-PowerShell för kodnings problem:</span><span class="sxs-lookup"><span data-stu-id="b845f-248">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="b845f-249">#1308</span><span class="sxs-lookup"><span data-stu-id="b845f-249">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="b845f-250">#1628</span><span class="sxs-lookup"><span data-stu-id="b845f-250">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="b845f-251">#1680</span><span class="sxs-lookup"><span data-stu-id="b845f-251">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="b845f-252">#1744</span><span class="sxs-lookup"><span data-stu-id="b845f-252">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="b845f-253">#1751</span><span class="sxs-lookup"><span data-stu-id="b845f-253">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="b845f-254">Den klassiska *Joel om program vara* skriver upp om Unicode</span><span class="sxs-lookup"><span data-stu-id="b845f-254">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="b845f-255">Kodning i .NET standard</span><span class="sxs-lookup"><span data-stu-id="b845f-255">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[Latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-ordnings markering]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Språk server protokoll]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[VSCode kodning]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
