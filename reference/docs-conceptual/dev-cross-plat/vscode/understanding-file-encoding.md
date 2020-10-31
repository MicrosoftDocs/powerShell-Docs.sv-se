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
# <a name="understanding-file-encoding-in-vs-code-and-powershell"></a><span data-ttu-id="f379a-103">Förstå filkodning i VS Code och PowerShell</span><span class="sxs-lookup"><span data-stu-id="f379a-103">Understanding file encoding in VS Code and PowerShell</span></span>

<span data-ttu-id="f379a-104">När du använder VS Code för att skapa och redigera PowerShell-skript är det viktigt att filerna sparas med rätt tecken kodnings format.</span><span class="sxs-lookup"><span data-stu-id="f379a-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="f379a-105">Vad är fil kodning och varför är det viktigt?</span><span class="sxs-lookup"><span data-stu-id="f379a-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="f379a-106">VS Code hanterar gränssnittet mellan en mänsklig genom att ange tecken strängar i en buffert och läsning/skrivning av byte till fil systemet.</span><span class="sxs-lookup"><span data-stu-id="f379a-106">VS Code manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="f379a-107">När VS Code sparar en fil, används en text kodning för att avgöra vilka byte som varje tecken blir.</span><span class="sxs-lookup"><span data-stu-id="f379a-107">When VS Code saves a file, it uses a text encoding to decide what bytes each character becomes.</span></span> <span data-ttu-id="f379a-108">Mer information finns i [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding).</span><span class="sxs-lookup"><span data-stu-id="f379a-108">For more information, see [about_Character_Encoding](/powershell/module/microsoft.powershell.core/about/about_character_encoding).</span></span>

<span data-ttu-id="f379a-109">När PowerShell kör ett skript måste det på samma sätt konvertera byte i en fil till tecken för att återskapa filen till ett PowerShell-program.</span><span class="sxs-lookup"><span data-stu-id="f379a-109">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="f379a-110">Eftersom VS Code skriver filen och PowerShell läser filen, måste de använda samma kodnings system.</span><span class="sxs-lookup"><span data-stu-id="f379a-110">Since VS Code writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="f379a-111">Den här processen för att parsa ett PowerShell-skript går: _byte_ -  ->  _tecken_  ->  _token-token_ för  ->  _abstrakt syntax_  ->  _execution_ .</span><span class="sxs-lookup"><span data-stu-id="f379a-111">This process of parsing a PowerShell script goes: _bytes_ -> _characters_ -> _tokens_ -> _abstract syntax tree_ -> _execution_ .</span></span>

<span data-ttu-id="f379a-112">Både VS Code och PowerShell installeras med en lämpliga standard kodnings konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f379a-112">Both VS Code and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="f379a-113">Den standard kodning som används av PowerShell har dock ändrats med versionen av PowerShell Core (V6. x).</span><span class="sxs-lookup"><span data-stu-id="f379a-113">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="f379a-114">För att se till att du inte har några problem med PowerShell eller PowerShell-tillägget i VS Code, måste du konfigurera dina VS-kod-och PowerShell-inställningar korrekt.</span><span class="sxs-lookup"><span data-stu-id="f379a-114">To ensure you have no problems using PowerShell or the PowerShell extension in VS Code, you need to configure your VS Code and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="f379a-115">Vanliga orsaker till kodnings problem</span><span class="sxs-lookup"><span data-stu-id="f379a-115">Common causes of encoding issues</span></span>

<span data-ttu-id="f379a-116">Kodnings problem inträffar när kodningen för VS Code eller skript filen inte matchar den förväntade kodningen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f379a-116">Encoding problems occur when the encoding of VS Code or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="f379a-117">Det finns inget sätt för PowerShell att automatiskt avgöra fil kodningen.</span><span class="sxs-lookup"><span data-stu-id="f379a-117">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="f379a-118">Det är mer troligt att du har problem med kodningen när du använder tecken som inte är i [ASCII-teckenuppsättningen med sju bitar](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="f379a-118">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="f379a-119">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f379a-119">For example:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="f379a-120">Utökade tecken som inte är bokstäver, t. ex. tank streck ( `—` ), hårt blank steg ( ` ` ) eller vänster dubbel citat tecken ( `"` )</span><span class="sxs-lookup"><span data-stu-id="f379a-120">Extended non-letter characters like em-dash (`—`), non-breaking space (` `) or left double quotation mark (`"`)</span></span>
- <span data-ttu-id="f379a-121">Accenttecken med latinska tecken ( `É` , `ü` )</span><span class="sxs-lookup"><span data-stu-id="f379a-121">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="f379a-122">Icke-latinska tecken som kyrilliska ( `Д` , `Ц` )</span><span class="sxs-lookup"><span data-stu-id="f379a-122">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="f379a-123">CJK-tecken ( `本` , `화` , `が` )</span><span class="sxs-lookup"><span data-stu-id="f379a-123">CJK characters (`本`, `화`, `が`)</span></span>

<span data-ttu-id="f379a-124">Vanliga orsaker till kodnings problem är:</span><span class="sxs-lookup"><span data-stu-id="f379a-124">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="f379a-125">Kodningarna för VS Code och PowerShell har inte ändrats från sina standardvärden.</span><span class="sxs-lookup"><span data-stu-id="f379a-125">The encodings of VS Code and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="f379a-126">För PowerShell 5,1 och nedan skiljer sig standard kodningen från VS Code.</span><span class="sxs-lookup"><span data-stu-id="f379a-126">For PowerShell 5.1 and below, the default encoding is different from VS Code's.</span></span>
- <span data-ttu-id="f379a-127">En annan redigerare har öppnat och överskrivit filen i en ny kodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-127">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="f379a-128">Detta händer ofta med ISE.</span><span class="sxs-lookup"><span data-stu-id="f379a-128">This often happens with the ISE.</span></span>
- <span data-ttu-id="f379a-129">Filen checkas in i käll kontroll i en kodning som skiljer sig från vad VS Code eller PowerShell förväntar sig.</span><span class="sxs-lookup"><span data-stu-id="f379a-129">The file is checked into source control in an encoding that is different from what VS Code or PowerShell expects.</span></span> <span data-ttu-id="f379a-130">Detta kan inträffa när medarbetare använder redigerare med olika kodnings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="f379a-130">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="f379a-131">Så här ser du när du har kodnings problem</span><span class="sxs-lookup"><span data-stu-id="f379a-131">How to tell when you have encoding issues</span></span>

<span data-ttu-id="f379a-132">Kodnings fel visas ofta som tolknings fel i skript.</span><span class="sxs-lookup"><span data-stu-id="f379a-132">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="f379a-133">Om du hittar konstig teckensekvens i skriptet kan det vara problemet.</span><span class="sxs-lookup"><span data-stu-id="f379a-133">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="f379a-134">I exemplet nedan visas ett kort streck ( `–` ) som tecken `â&euro;"` :</span><span class="sxs-lookup"><span data-stu-id="f379a-134">In the example below, an en-dash (`–`) appears as the characters `â&euro;"`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â&euro;"From $from â&euro;"To $recipient1 â&euro;"Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="f379a-135">Det här problemet uppstår eftersom VS Code kodar tecknen `–` i UTF-8 som byte `0xE2 0x80 0x93` .</span><span class="sxs-lookup"><span data-stu-id="f379a-135">This problem occurs because VS Code encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span> <span data-ttu-id="f379a-136">När dessa byte avkodas som Windows-1252 tolkas de som tecknen `â&euro;"` .</span><span class="sxs-lookup"><span data-stu-id="f379a-136">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â&euro;"`.</span></span>

<span data-ttu-id="f379a-137">Några konstig teckensekvens som du kan se är:</span><span class="sxs-lookup"><span data-stu-id="f379a-137">Some strange character sequences that you might see include:</span></span>

<!-- markdownlint-disable MD038 -->
- <span data-ttu-id="f379a-138">`â&euro;"` Istället för `–`</span><span class="sxs-lookup"><span data-stu-id="f379a-138">`â&euro;"` instead of `–`</span></span>
- <span data-ttu-id="f379a-139">`â&euro;"` Istället för `—`</span><span class="sxs-lookup"><span data-stu-id="f379a-139">`â&euro;"` instead of `—`</span></span>
- <span data-ttu-id="f379a-140">`Ã„2` Istället för `Ä`</span><span class="sxs-lookup"><span data-stu-id="f379a-140">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="f379a-141">`Â` i stället för ` `  (ett hårt blank steg)</span><span class="sxs-lookup"><span data-stu-id="f379a-141">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="f379a-142">`Ã&copy;` Istället för `é`</span><span class="sxs-lookup"><span data-stu-id="f379a-142">`Ã&copy;` instead of `é`</span></span>
<!-- markdownlint-enable MD038 -->

<span data-ttu-id="f379a-143">Den här praktiska [referensen](https://www.i18nqa.com/debug/utf8-debug.html) listar vanliga mönster som indikerar ett kodnings problem med UTF-8/Windows-1252.</span><span class="sxs-lookup"><span data-stu-id="f379a-143">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vs-code-interacts-with-encodings"></a><span data-ttu-id="f379a-144">Hur PowerShell-tillägget i VS-kod interagerar med kodningar</span><span class="sxs-lookup"><span data-stu-id="f379a-144">How the PowerShell extension in VS Code interacts with encodings</span></span>

<span data-ttu-id="f379a-145">PowerShell-tillägget samverkar med skript på flera olika sätt:</span><span class="sxs-lookup"><span data-stu-id="f379a-145">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="f379a-146">När skript redige ras i VS Code skickas innehållet av VS Code till tillägget.</span><span class="sxs-lookup"><span data-stu-id="f379a-146">When scripts are edited in VS Code, the contents are sent by VS Code to the extension.</span></span> <span data-ttu-id="f379a-147">[Språk Server protokollet][] bestämmer att det här innehållet överförs i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f379a-147">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="f379a-148">Därför är det inte möjligt för tillägget att få fel kodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-148">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
1. <span data-ttu-id="f379a-149">När skript körs direkt i den integrerade konsolen läses de in från filen med PowerShell direkt.</span><span class="sxs-lookup"><span data-stu-id="f379a-149">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="f379a-150">Om PowerShell-kodning skiljer sig från VS Code ' kan något gå fel här.</span><span class="sxs-lookup"><span data-stu-id="f379a-150">If PowerShell's encoding differs from VS Code's, something can go wrong here.</span></span>
1. <span data-ttu-id="f379a-151">När ett skript som är öppet i VS Code refererar till ett annat skript som inte är öppet i VS Code, återgår tillägget till att läsa in skriptets innehåll från fil systemet.</span><span class="sxs-lookup"><span data-stu-id="f379a-151">When a script that is open in VS Code references another script that is not open in VS Code, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="f379a-152">PowerShell-tillägget är standardvärdet UTF-8-kodning, men använder [byte-ordnings markering][], eller struktur, identifiering för att välja rätt kodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-152">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="f379a-153">Problemet inträffar när du antar kodningen för BOM-mindre format (t. ex. [UTF-8][] utan strukturliste och [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="f379a-153">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span> <span data-ttu-id="f379a-154">PowerShell-tillägget är standardvärdet UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f379a-154">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="f379a-155">Tillägget kan inte ändra VS Codes kodnings inställningar.</span><span class="sxs-lookup"><span data-stu-id="f379a-155">The extension cannot change VS Code's encoding settings.</span></span> <span data-ttu-id="f379a-156">Mer information finns i avsnittet om [problem #824](https://github.com/Microsoft/VSCode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="f379a-156">For more information, see [issue #824](https://github.com/Microsoft/VSCode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="f379a-157">Välja rätt kodning</span><span class="sxs-lookup"><span data-stu-id="f379a-157">Choosing the right encoding</span></span>

<span data-ttu-id="f379a-158">Olika system och program kan använda olika kodningar:</span><span class="sxs-lookup"><span data-stu-id="f379a-158">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="f379a-159">I .NET standard, på webben och i Linux-världen är UTF-8 nu den dominerande kodningen.</span><span class="sxs-lookup"><span data-stu-id="f379a-159">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="f379a-160">I många .NET Framework program används [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="f379a-160">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="f379a-161">Av historiska skäl kallas detta ibland "Unicode", en term som nu refererar till en bred [standard](https://en.wikipedia.org/wiki/Unicode) som innehåller både UTF-8 och UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f379a-161">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="f379a-162">I Windows fortsätter många inbyggda program som i förväg med Unicode att använda Windows-1252 som standard.</span><span class="sxs-lookup"><span data-stu-id="f379a-162">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="f379a-163">Unicode-kodningar har också begreppet ett byte-ordnings tecken (BOM).</span><span class="sxs-lookup"><span data-stu-id="f379a-163">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="f379a-164">Strukturer sker i början av texten för att ange en avkodare som kodar texten.</span><span class="sxs-lookup"><span data-stu-id="f379a-164">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="f379a-165">För kodningar med flera byte anger strukturen också [endian](https://en.wikipedia.org/wiki/Endianness) -koden.</span><span class="sxs-lookup"><span data-stu-id="f379a-165">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="f379a-166">Strukturer är utformade för att vara byte som sällan förekommer i icke-Unicode-text, vilket ger en rimlig gissning att texten är Unicode när en struktur finns.</span><span class="sxs-lookup"><span data-stu-id="f379a-166">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="f379a-167">Strukturer är valfria och deras införande är inte lika populärt i Linux-världen, eftersom en pålitlig konvention av UTF-8 används överallt.</span><span class="sxs-lookup"><span data-stu-id="f379a-167">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="f379a-168">De flesta Linux-program förutsätter att text ingången kodas i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f379a-168">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="f379a-169">Många Linux-program kommer att känna igen och hantera en struktur korrekt, men en siffra gör inte, vilket leder till artefakter i text som manipuleras med dessa program.</span><span class="sxs-lookup"><span data-stu-id="f379a-169">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="f379a-170">**Därför** :</span><span class="sxs-lookup"><span data-stu-id="f379a-170">**Therefore** :</span></span>

- <span data-ttu-id="f379a-171">Om du arbetar i första hand med Windows-program och Windows PowerShell bör du föredra en kodning som UTF-8 med BOM eller UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f379a-171">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="f379a-172">Om du arbetar på olika plattformar bör du hellre använda UTF-8 med BOM.</span><span class="sxs-lookup"><span data-stu-id="f379a-172">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="f379a-173">Om du arbetar huvudsakligen i Linux-associerade kontexter bör du hellre UTF-8 utan struktur.</span><span class="sxs-lookup"><span data-stu-id="f379a-173">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="f379a-174">Windows-1252 och Latin-1 är i princip äldre kodningar som du bör undvika om möjligt.</span><span class="sxs-lookup"><span data-stu-id="f379a-174">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="f379a-175">Vissa äldre Windows-program kan dock vara beroende av dem.</span><span class="sxs-lookup"><span data-stu-id="f379a-175">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="f379a-176">Det är också värt att notera att skript signering är [kodnings beroende](https://github.com/PowerShell/PowerShell/issues/3466), vilket innebär att en ändring av kodningen på ett signerat skript kräver omregistrering.</span><span class="sxs-lookup"><span data-stu-id="f379a-176">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vs-code"></a><span data-ttu-id="f379a-177">Konfigurera VS-kod</span><span class="sxs-lookup"><span data-stu-id="f379a-177">Configuring VS Code</span></span>

<span data-ttu-id="f379a-178">VS Codes standard encoding är UTF-8 utan struktur.</span><span class="sxs-lookup"><span data-stu-id="f379a-178">VS Code's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="f379a-179">Om du vill ange [vs Codes encoding][]går du till vs Code-inställningarna (<kbd>CTRL</kbd> + <kbd>,</kbd>) och anger `"files.encoding"` inställningen:</span><span class="sxs-lookup"><span data-stu-id="f379a-179">To set [VS Code's encoding][], go to the VS Code settings (<kbd>Ctrl</kbd>+<kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="f379a-180">Några möjliga värden är:</span><span class="sxs-lookup"><span data-stu-id="f379a-180">Some possible values are:</span></span>

- <span data-ttu-id="f379a-181">`utf8`: [UTF-8] utan struktur</span><span class="sxs-lookup"><span data-stu-id="f379a-181">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="f379a-182">`utf8bom`: [UTF-8] med struktur</span><span class="sxs-lookup"><span data-stu-id="f379a-182">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="f379a-183">`utf16le`: Lite endian [-UTF-16]</span><span class="sxs-lookup"><span data-stu-id="f379a-183">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="f379a-184">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="f379a-184">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="f379a-185">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="f379a-185">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="f379a-186">Du bör få en listruta för detta i vyn grafiskt eller om du har slutfört den i JSON-vyn.</span><span class="sxs-lookup"><span data-stu-id="f379a-186">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="f379a-187">Du kan också lägga till följande för att automatiskt identifiera kodning när det är möjligt:</span><span class="sxs-lookup"><span data-stu-id="f379a-187">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="f379a-188">Om du inte vill att de här inställningarna ska påverka alla filtyper, kan du även använda olika språk konfigurationer i VS Code.</span><span class="sxs-lookup"><span data-stu-id="f379a-188">If you don't want these settings to affect all files types, VS Code also allows per-language configurations.</span></span> <span data-ttu-id="f379a-189">Skapa en språkspecifik inställning genom att placera inställningarna i ett `[<language-name>]` fält.</span><span class="sxs-lookup"><span data-stu-id="f379a-189">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="f379a-190">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f379a-190">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="f379a-191">Du kanske också vill överväga att installera [Gremlins-spåraren][] för Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f379a-191">You may also want to consider installing the [Gremlins tracker][] for Visual Studio Code.</span></span> <span data-ttu-id="f379a-192">Det här tillägget visar vissa Unicode-tecken som är lätta att skada eftersom de är osynliga eller ser ut som andra normala tecken.</span><span class="sxs-lookup"><span data-stu-id="f379a-192">This extension reveals certain Unicode characters that easily corrupted because they are invisible or look like other normal characters.</span></span>

## <a name="configuring-powershell"></a><span data-ttu-id="f379a-193">Konfigurera PowerShell</span><span class="sxs-lookup"><span data-stu-id="f379a-193">Configuring PowerShell</span></span>

<span data-ttu-id="f379a-194">PowerShell: s standard kodning varierar beroende på version:</span><span class="sxs-lookup"><span data-stu-id="f379a-194">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="f379a-195">I PowerShell 6 + är standard kodningen UTF-8 utan struktur på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="f379a-195">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="f379a-196">I Windows PowerShell är standard kodningen vanligt vis Windows-1252, ett tillägg på [Latin-1][], även kallat ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="f379a-196">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="f379a-197">I PowerShell 5 + kan du hitta din standard kodning med följande:</span><span class="sxs-lookup"><span data-stu-id="f379a-197">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="f379a-198">Följande [skript](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan användas för att avgöra vilken kodning din PowerShell-session härleds för ett skript utan en struktur.</span><span class="sxs-lookup"><span data-stu-id="f379a-198">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="f379a-199">Det är möjligt att konfigurera PowerShell för att använda en specifik kodning som oftare använder profil inställningar.</span><span class="sxs-lookup"><span data-stu-id="f379a-199">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span>
<span data-ttu-id="f379a-200">Se följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="f379a-200">See the following articles:</span></span>

- <span data-ttu-id="f379a-201">[@mklement0]är ett [svar på PowerShell-kodning på StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="f379a-201">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="f379a-202">[@rkeithhill]s [blogg inlägg om att hantera strukturbaserade UTF-8-indata i PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="f379a-202">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="f379a-203">Det går inte att tvinga PowerShell att använda en speciell kodning för inkodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-203">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="f379a-204">PowerShell 5,1 och tidigare, som körs på Windows med språkvarianten inställd på en-US, är som standard Windows-1252-kodning när det inte finns någon struktur.</span><span class="sxs-lookup"><span data-stu-id="f379a-204">PowerShell 5.1 and below, running on Windows with the locale set to en-US, defaults to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="f379a-205">Andra nationella inställningar kan använda en annan kodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-205">Other locale settings may use a different encoding.</span></span> <span data-ttu-id="f379a-206">För att säkerställa samverkan är det bäst att spara skript i Unicode-format med en struktur.</span><span class="sxs-lookup"><span data-stu-id="f379a-206">To ensure interoperability, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f379a-207">Andra verktyg som du kan använda för att trycka PowerShell-skript kan påverkas av kodnings alternativen eller koda om skripten till en annan kodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-207">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="f379a-208">Befintliga skript</span><span class="sxs-lookup"><span data-stu-id="f379a-208">Existing scripts</span></span>

<span data-ttu-id="f379a-209">Skript som redan finns i fil systemet kan behöva kodas om till den nya valda kodningen.</span><span class="sxs-lookup"><span data-stu-id="f379a-209">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="f379a-210">I det nedre fältet VS Code ser du etiketten UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f379a-210">In the bottom bar of VS Code, you'll see the label UTF-8.</span></span> <span data-ttu-id="f379a-211">Klicka på den för att öppna åtgärds fältet och välj **Spara med kodning** .</span><span class="sxs-lookup"><span data-stu-id="f379a-211">Click it to open the action bar and select **Save with encoding** .</span></span> <span data-ttu-id="f379a-212">Nu kan du välja en ny kodning för filen.</span><span class="sxs-lookup"><span data-stu-id="f379a-212">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="f379a-213">Se [kod för vs Code][] för fullständiga instruktioner.</span><span class="sxs-lookup"><span data-stu-id="f379a-213">See [VS Code's encoding][] for full instructions.</span></span>

<span data-ttu-id="f379a-214">Om du behöver Omkoda flera filer kan du använda följande skript:</span><span class="sxs-lookup"><span data-stu-id="f379a-214">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="f379a-215">PowerShell (Integrated Scripting Environment)</span><span class="sxs-lookup"><span data-stu-id="f379a-215">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="f379a-216">Om du också redigerar skript med hjälp av PowerShell ISE måste du synkronisera dina kodnings inställningar där.</span><span class="sxs-lookup"><span data-stu-id="f379a-216">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="f379a-217">ISE bör svara på en struktur, men det är också möjligt att använda reflektion för att [Ange kodningen](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="f379a-217">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="f379a-218">Observera att detta inte behålls mellan starter.</span><span class="sxs-lookup"><span data-stu-id="f379a-218">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="f379a-219">Käll kontroll program vara</span><span class="sxs-lookup"><span data-stu-id="f379a-219">Source control software</span></span>

<span data-ttu-id="f379a-220">Vissa käll kontroll verktyg, till exempel git, ignorera kodningar; git spårar bara bytena.</span><span class="sxs-lookup"><span data-stu-id="f379a-220">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span> <span data-ttu-id="f379a-221">Andra, som Azure DevOps eller Mercurial, kanske inte.</span><span class="sxs-lookup"><span data-stu-id="f379a-221">Others, like Azure DevOps or Mercurial, may not.</span></span> <span data-ttu-id="f379a-222">Även vissa git-baserade verktyg är beroende av avkodning av text.</span><span class="sxs-lookup"><span data-stu-id="f379a-222">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="f379a-223">I så fall måste du se till att:</span><span class="sxs-lookup"><span data-stu-id="f379a-223">When this is the case, make sure you:</span></span>

- <span data-ttu-id="f379a-224">Konfigurera text kodningen i käll kontrollen så att den matchar din VS Code-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f379a-224">Configure the text encoding in your source control to match your VS Code configuration.</span></span>
- <span data-ttu-id="f379a-225">Se till att alla filer är markerade med käll kontroll i relevant kodning.</span><span class="sxs-lookup"><span data-stu-id="f379a-225">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="f379a-226">Försiktig ändringar i kodningen som tagits emot via käll kontroll.</span><span class="sxs-lookup"><span data-stu-id="f379a-226">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="f379a-227">Ett nyckel tecken på detta är en skillnad som indikerar ändringar men där inget verkar ha ändrats (eftersom byte har tecken, men inte).</span><span class="sxs-lookup"><span data-stu-id="f379a-227">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="f379a-228">Samarbets miljöer</span><span class="sxs-lookup"><span data-stu-id="f379a-228">Collaborators' environments</span></span>

<span data-ttu-id="f379a-229">Se till att dina medarbetare på alla filer som du delar inte har några inställningar som åsidosätter din kodning genom att koda om PowerShell-filer om du vill konfigurera käll kontroll.</span><span class="sxs-lookup"><span data-stu-id="f379a-229">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="f379a-230">Andra program</span><span class="sxs-lookup"><span data-stu-id="f379a-230">Other programs</span></span>

<span data-ttu-id="f379a-231">Alla andra program som läser eller skriver ett PowerShell-skript kan koda det igen.</span><span class="sxs-lookup"><span data-stu-id="f379a-231">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="f379a-232">Några exempel är:</span><span class="sxs-lookup"><span data-stu-id="f379a-232">Some examples are:</span></span>

- <span data-ttu-id="f379a-233">Använd Urklipp för att kopiera och klistra in ett skript.</span><span class="sxs-lookup"><span data-stu-id="f379a-233">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="f379a-234">Detta är vanligt i scenarier som:</span><span class="sxs-lookup"><span data-stu-id="f379a-234">This is common in scenarios like:</span></span>
  - <span data-ttu-id="f379a-235">Kopiera ett skript till en virtuell dator</span><span class="sxs-lookup"><span data-stu-id="f379a-235">Copying a script into a VM</span></span>
  - <span data-ttu-id="f379a-236">Kopiera ett skript från ett e-postmeddelande eller en webb sida</span><span class="sxs-lookup"><span data-stu-id="f379a-236">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="f379a-237">Kopiera ett skript till eller från ett Microsoft Word-eller PowerPoint-dokument</span><span class="sxs-lookup"><span data-stu-id="f379a-237">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="f379a-238">Andra text redigerare, till exempel:</span><span class="sxs-lookup"><span data-stu-id="f379a-238">Other text editors, such as:</span></span>
  - <span data-ttu-id="f379a-239">Anteckningar</span><span class="sxs-lookup"><span data-stu-id="f379a-239">Notepad</span></span>
  - <span data-ttu-id="f379a-240">vim</span><span class="sxs-lookup"><span data-stu-id="f379a-240">vim</span></span>
  - <span data-ttu-id="f379a-241">Andra PowerShell-skript redigerare</span><span class="sxs-lookup"><span data-stu-id="f379a-241">Any other PowerShell script editor</span></span>
- <span data-ttu-id="f379a-242">Text redigerings verktyg, t. ex.:</span><span class="sxs-lookup"><span data-stu-id="f379a-242">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="f379a-243">Operatorer för PowerShell-omdirigering som `>` och `>>`</span><span class="sxs-lookup"><span data-stu-id="f379a-243">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="f379a-244">Fil överförings program, t. ex.:</span><span class="sxs-lookup"><span data-stu-id="f379a-244">File transfer programs, like:</span></span>
  - <span data-ttu-id="f379a-245">En webbläsare, vid hämtning av skript</span><span class="sxs-lookup"><span data-stu-id="f379a-245">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="f379a-246">En fil resurs</span><span class="sxs-lookup"><span data-stu-id="f379a-246">A file share</span></span>

<span data-ttu-id="f379a-247">Några av dessa verktyg behandlar byte i stället för text, men andra erbjuder kodnings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="f379a-247">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="f379a-248">I de fall där du behöver konfigurera en kodning måste du göra den densamma som din redigerings kodning för att förhindra problem.</span><span class="sxs-lookup"><span data-stu-id="f379a-248">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="f379a-249">Andra resurser för kodning i PowerShell</span><span class="sxs-lookup"><span data-stu-id="f379a-249">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="f379a-250">Det finns några andra bra inlägg på kodning och konfigurering av kodning i PowerShell som är värda en läsning:</span><span class="sxs-lookup"><span data-stu-id="f379a-250">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- [<span data-ttu-id="f379a-251">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="f379a-251">about_Character_Encoding</span></span>](/powershell/module/microsoft.powershell.core/about/about_character_encoding)
- <span data-ttu-id="f379a-252">[@mklement0][sammanfattande av PowerShell-kodning på StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="f379a-252">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="f379a-253">Tidigare problem som öppnats vid VS-Code-PowerShell för kodnings problem:</span><span class="sxs-lookup"><span data-stu-id="f379a-253">Previous issues opened on VS Code-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="f379a-254">#1308</span><span class="sxs-lookup"><span data-stu-id="f379a-254">#1308</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1308)
  - [<span data-ttu-id="f379a-255">#1628</span><span class="sxs-lookup"><span data-stu-id="f379a-255">#1628</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1628)
  - [<span data-ttu-id="f379a-256">#1680</span><span class="sxs-lookup"><span data-stu-id="f379a-256">#1680</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1680)
  - [<span data-ttu-id="f379a-257">#1744</span><span class="sxs-lookup"><span data-stu-id="f379a-257">#1744</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1744)
  - [<span data-ttu-id="f379a-258">#1751</span><span class="sxs-lookup"><span data-stu-id="f379a-258">#1751</span></span>](https://github.com/PowerShell/VSCode-powershell/issues/1751)
- [<span data-ttu-id="f379a-259">Den klassiska _Joel om program vara_ skriver upp om Unicode</span><span class="sxs-lookup"><span data-stu-id="f379a-259">The classic _Joel on Software_ write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="f379a-260">Kodning i .NET standard</span><span class="sxs-lookup"><span data-stu-id="f379a-260">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)

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
[VS Code-kodning]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VS Code's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[Gremlins-Spårare]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
[Gremlins tracker]: https://marketplace.visualstudio.com/items?itemName=nhoizey.gremlins
