---
title: Förstå Filkodning i VSCode och PowerShell
description: Konfigurera Filkodning i VSCode och PowerShell
ms.date: 02/28/2019
ms.openlocfilehash: f3b133b4bee7688821a5960429e2f26b69b01e12
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251729"
---
# <a name="understanding-file-encoding-in-vscode-and-powershell"></a><span data-ttu-id="252d0-103">Förstå Filkodning i VSCode och PowerShell</span><span class="sxs-lookup"><span data-stu-id="252d0-103">Understanding file encoding in VSCode and PowerShell</span></span>

<span data-ttu-id="252d0-104">När du använder VS Code för att skapa och redigera PowerShell-skript, är det viktigt att dina filer sparas med Kodningsformatet för rätt tecken.</span><span class="sxs-lookup"><span data-stu-id="252d0-104">When using VS Code to create and edit PowerShell scripts, it is important that your files are saved using the correct character encoding format.</span></span>

## <a name="what-is-file-encoding-and-why-is-it-important"></a><span data-ttu-id="252d0-105">Vad är Filkodning och varför är det viktigt?</span><span class="sxs-lookup"><span data-stu-id="252d0-105">What is file encoding and why is it important?</span></span>

<span data-ttu-id="252d0-106">VSCode hanterar gränssnittet mellan en mänsklig anger teckensträngar till en buffert och läsning/skrivning block byte i filsystemet.</span><span class="sxs-lookup"><span data-stu-id="252d0-106">VSCode manages the interface between a human entering strings of characters into a buffer and reading/writing blocks of bytes to the filesystem.</span></span> <span data-ttu-id="252d0-107">När en fil sparas i VSCode används en textkodning för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="252d0-107">When VSCode saves a file, it uses a text encoding to do this.</span></span>

<span data-ttu-id="252d0-108">När PowerShell körs ett skript konvertera den på samma sätt kan byte i en fil till tecken att rekonstruera filen i ett PowerShell-program.</span><span class="sxs-lookup"><span data-stu-id="252d0-108">Similarly, when PowerShell runs a script it must convert the bytes in a file to characters to reconstruct the file into a PowerShell program.</span></span> <span data-ttu-id="252d0-109">Eftersom VSCode skriver filen och PowerShell läser filen, måste de använda samma kodning system.</span><span class="sxs-lookup"><span data-stu-id="252d0-109">Since VSCode writes the file and PowerShell reads the file, they need to use the same encoding system.</span></span> <span data-ttu-id="252d0-110">Den här processen för att tolka ett PowerShell-skript slutar: *byte* -> *tecken* -> *token*  ->   *abstrakt syntax trädet* -> *körning*.</span><span class="sxs-lookup"><span data-stu-id="252d0-110">This process of parsing a PowerShell script goes: *bytes* -> *characters* -> *tokens* -> *abstract syntax tree* -> *execution*.</span></span>

<span data-ttu-id="252d0-111">Både VSCode och PowerShell installeras med en användningstyperna kodning standardkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="252d0-111">Both VSCode and PowerShell are installed with a sensible default encoding configuration.</span></span> <span data-ttu-id="252d0-112">Standardkodning som används av PowerShell har dock ändrats med lanseringen av PowerShell Core (v6.x).</span><span class="sxs-lookup"><span data-stu-id="252d0-112">However, the default encoding used by PowerShell has changed with the release of PowerShell Core (v6.x).</span></span> <span data-ttu-id="252d0-113">Om du vill kontrollera att du har inga problem med PowerShell eller PowerShell-tillägget i VSCode, måste du konfigurera inställningarna för VSCode och PowerShell korrekt.</span><span class="sxs-lookup"><span data-stu-id="252d0-113">To ensure you have no problems using PowerShell or the PowerShell extension in VSCode, you need to configure your VSCode and PowerShell settings properly.</span></span>

## <a name="common-causes-of-encoding-issues"></a><span data-ttu-id="252d0-114">Vanliga orsaker till kodningsproblem</span><span class="sxs-lookup"><span data-stu-id="252d0-114">Common causes of encoding issues</span></span>

<span data-ttu-id="252d0-115">Kodning problem vid kodning av VSCode eller skriptfilen inte matchar den förväntade kodningen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252d0-115">Encoding problems occur when the encoding of VSCode or your script file does not match the expected encoding of PowerShell.</span></span> <span data-ttu-id="252d0-116">Det finns inget sätt för PowerShell för att automatiskt avgöra Filkodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-116">There is no way for PowerShell to automatically determine the file encoding.</span></span>

<span data-ttu-id="252d0-117">Det är mer sannolikt att ha kodning problem när du använder tecken som inte finns i den [7-bitars ASCII-teckenuppsättningen](https://ascii.cl/).</span><span class="sxs-lookup"><span data-stu-id="252d0-117">You're more likely to have encoding problems when you're using characters not in the [7-bit ASCII character set](https://ascii.cl/).</span></span> <span data-ttu-id="252d0-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="252d0-118">For example:</span></span>

- <span data-ttu-id="252d0-119">Accent över latinska tecken (`É`, `ü`)</span><span class="sxs-lookup"><span data-stu-id="252d0-119">Accented latin characters (`É`, `ü`)</span></span>
- <span data-ttu-id="252d0-120">Icke-latinska tecken som Kyrillisk (`Д`, `Ц`)</span><span class="sxs-lookup"><span data-stu-id="252d0-120">Non-latin characters like Cyrillic (`Д`, `Ц`)</span></span>
- <span data-ttu-id="252d0-121">Han kinesiska (`脚`, `本`)</span><span class="sxs-lookup"><span data-stu-id="252d0-121">Han Chinese (`脚`, `本`)</span></span>

<span data-ttu-id="252d0-122">Vanliga orsaker till kodningsproblem är:</span><span class="sxs-lookup"><span data-stu-id="252d0-122">Common reasons for encoding issues are:</span></span>

- <span data-ttu-id="252d0-123">Kodningar av VSCode och PowerShell har inte ändrats från standardvärdena.</span><span class="sxs-lookup"><span data-stu-id="252d0-123">The encodings of VSCode and PowerShell have not been changed from their defaults.</span></span> <span data-ttu-id="252d0-124">För PowerShell 5.1 och under standard skiljer kodning sig från Vscode's.</span><span class="sxs-lookup"><span data-stu-id="252d0-124">For PowerShell 5.1 and below, the default encoding is different from VSCode's.</span></span>
- <span data-ttu-id="252d0-125">Någon annan redigerare som har öppnat och skriva över filen i en ny kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-125">Another editor has opened and overwritten the file in a new encoding.</span></span> <span data-ttu-id="252d0-126">Detta händer ofta med ISE.</span><span class="sxs-lookup"><span data-stu-id="252d0-126">This often happens with the ISE.</span></span>
- <span data-ttu-id="252d0-127">Filen checkas in källkontroll i en kodning som skiljer sig från vilka VSCode eller PowerShell förväntas.</span><span class="sxs-lookup"><span data-stu-id="252d0-127">The file is checked into source control in an encoding that is different from what VSCode or PowerShell expects.</span></span> <span data-ttu-id="252d0-128">Detta kan inträffa när medarbetare använder redigerare med olika konfigurationer för kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-128">This can happen when collaborators use editors with different encoding configurations.</span></span>

### <a name="how-to-tell-when-you-have-encoding-issues"></a><span data-ttu-id="252d0-129">Så här avgör du när du har kodningsproblem</span><span class="sxs-lookup"><span data-stu-id="252d0-129">How to tell when you have encoding issues</span></span>

<span data-ttu-id="252d0-130">Ofta kodningsfel uppträder som parsa fel i skript.</span><span class="sxs-lookup"><span data-stu-id="252d0-130">Often encoding errors present themselves as parse errors in scripts.</span></span> <span data-ttu-id="252d0-131">Om du hittar onormalt teckensekvenser i skriptet kan vara detta problemet.</span><span class="sxs-lookup"><span data-stu-id="252d0-131">If you find strange character sequences in your script, this can be the problem.</span></span> <span data-ttu-id="252d0-132">I exemplet nedan ett tankstreck (`–`) visas som tecknen `â€“`:</span><span class="sxs-lookup"><span data-stu-id="252d0-132">In the example below, an en-dash (`–`) appears as the characters `â€“`:</span></span>

```Output
Send-MailMessage : A positional parameter cannot be found that accepts argument 'Testing FuseMail SMTP...'.
At C:\Users\<User>\<OneDrive>\Development\PowerShell\Scripts\Send-EmailUsingSmtpRelay.ps1:6 char:1
+ Send-MailMessage â€“From $from â€“To $recipient1 â€“Subject $subject  ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Send-MailMessage], ParameterBindingException
    + FullyQualifiedErrorId : PositionalParameterNotFound,Microsoft.PowerShell.Commands.SendMailMessage
```

<span data-ttu-id="252d0-133">Det här problemet uppstår eftersom VSCode kodar tecknet `–` i UTF-8 som byte `0xE2 0x80 0x93`.</span><span class="sxs-lookup"><span data-stu-id="252d0-133">This problem occurs because VSCode encodes the character `–` in UTF-8 as the bytes `0xE2 0x80 0x93`.</span></span>
<span data-ttu-id="252d0-134">När dessa byte avkodas som Windows-1252, de tolkas som tecknen `â€“`.</span><span class="sxs-lookup"><span data-stu-id="252d0-134">When these bytes are decoded as Windows-1252, they are interpreted as the characters `â€“`.</span></span>

<span data-ttu-id="252d0-135">Vissa onormalt teckensekvenser som kan visas är:</span><span class="sxs-lookup"><span data-stu-id="252d0-135">Some strange character sequences that you might see include:</span></span>

- <span data-ttu-id="252d0-136">`â€“` Istället för `–`</span><span class="sxs-lookup"><span data-stu-id="252d0-136">`â€“` instead of `–`</span></span>
- <span data-ttu-id="252d0-137">`â€”` Istället för `—`</span><span class="sxs-lookup"><span data-stu-id="252d0-137">`â€”` instead of `—`</span></span>
- <span data-ttu-id="252d0-138">`Ã„2` Istället för `Ä`</span><span class="sxs-lookup"><span data-stu-id="252d0-138">`Ã„2` instead of `Ä`</span></span>
- <span data-ttu-id="252d0-139">`Â` i stället för ` ` (ett hårt blanksteg)</span><span class="sxs-lookup"><span data-stu-id="252d0-139">`Â` instead of ` `  (a non-breaking space)</span></span>
- <span data-ttu-id="252d0-140">`Ã©` Istället för `é`</span><span class="sxs-lookup"><span data-stu-id="252d0-140">`Ã©` instead of `é`</span></span>

<span data-ttu-id="252d0-141">Det här praktiska [referens](https://www.i18nqa.com/debug/utf8-debug.html) visar en lista över vanliga mönster som indikerar att en UTF-8/Windows-1252 kodningsproblem.</span><span class="sxs-lookup"><span data-stu-id="252d0-141">This handy [reference](https://www.i18nqa.com/debug/utf8-debug.html) lists the common patterns that indicate a UTF-8/Windows-1252 encoding problem.</span></span>

## <a name="how-the-powershell-extension-in-vscode-interacts-with-encodings"></a><span data-ttu-id="252d0-142">Hur PowerShell-tillägget i VSCode interagerar med kodningar</span><span class="sxs-lookup"><span data-stu-id="252d0-142">How the PowerShell extension in VSCode interacts with encodings</span></span>

<span data-ttu-id="252d0-143">Tillägget PowerShell samverkar med skript i ett antal olika sätt:</span><span class="sxs-lookup"><span data-stu-id="252d0-143">The PowerShell extension interacts with scripts in a number of ways:</span></span>

1. <span data-ttu-id="252d0-144">När skript redigeras i VSCode, skickas innehållet från VSCode till tillägget.</span><span class="sxs-lookup"><span data-stu-id="252d0-144">When scripts are edited in VSCode, the contents are sent by VSCode to the extension.</span></span> <span data-ttu-id="252d0-145">Den [Språk Server-protokoll][] innehåller principer för att den här innehåll som överförs i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="252d0-145">The [Language Server Protocol][] mandates that this content is transferred in UTF-8.</span></span> <span data-ttu-id="252d0-146">Det är därför inte möjligt för tillägget att hämta fel kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-146">Therefore, it is not possible for the extension to get the wrong encoding.</span></span>
2. <span data-ttu-id="252d0-147">När skript körs direkt i integrerad konsol, är de läsa från filen med PowerShell direkt.</span><span class="sxs-lookup"><span data-stu-id="252d0-147">When scripts are executed directly in the Integrated Console, they're read from the file by PowerShell directly.</span></span> <span data-ttu-id="252d0-148">TF PowerShell kodning skiljer sig från Vscode's, något går fel här.</span><span class="sxs-lookup"><span data-stu-id="252d0-148">Tf PowerShell's encoding differs from VSCode's, something can go wrong here.</span></span>
3. <span data-ttu-id="252d0-149">När ett skript som är öppen i VSCode refererar till ett annat skript som inte är öppen i VSCode, använder tillägget till att läsa in den skriptet innehåll från filsystemet.</span><span class="sxs-lookup"><span data-stu-id="252d0-149">When a script that is open in VSCode references another script that is not open in VSCode, the extension falls back to loading that script's content from the file system.</span></span> <span data-ttu-id="252d0-150">Tillägget PowerShell UTF-8-kodning som standard, men använder [byte-ordningsmarkering][], eller BOM, identifiering för att välja rätt kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-150">The PowerShell extension defaults to UTF-8 encoding, but uses [byte-order mark][], or BOM, detection to select the correct encoding.</span></span>

<span data-ttu-id="252d0-151">Problemet uppstår när förutsatt att kodning av BOM mindre format (t.ex. [UTF-8][] utan BOM och [Windows-1252][]).</span><span class="sxs-lookup"><span data-stu-id="252d0-151">The problem occurs when assuming the encoding of BOM-less formats (like [UTF-8][] with no BOM and [Windows-1252][]).</span></span>
<span data-ttu-id="252d0-152">PowerShell-tillägget som standard UTF-8.</span><span class="sxs-lookup"><span data-stu-id="252d0-152">The PowerShell extension defaults to UTF-8.</span></span> <span data-ttu-id="252d0-153">Tillägget kan inte ändra Vscodes kodningsinställningar.</span><span class="sxs-lookup"><span data-stu-id="252d0-153">The extension cannot change VSCode's encoding settings.</span></span>
<span data-ttu-id="252d0-154">Mer information finns i [utfärda #824](https://github.com/Microsoft/vscode/issues/824).</span><span class="sxs-lookup"><span data-stu-id="252d0-154">For more information, see [issue #824](https://github.com/Microsoft/vscode/issues/824).</span></span>

## <a name="choosing-the-right-encoding"></a><span data-ttu-id="252d0-155">Välja rätt kodning</span><span class="sxs-lookup"><span data-stu-id="252d0-155">Choosing the right encoding</span></span>

<span data-ttu-id="252d0-156">Olika system och program kan använda olika kodningar:</span><span class="sxs-lookup"><span data-stu-id="252d0-156">Different systems and applications can use different encodings:</span></span>

- <span data-ttu-id="252d0-157">I .NET Standard är på webben och i Linux-världen UTF-8 nu den dominerande kodningen.</span><span class="sxs-lookup"><span data-stu-id="252d0-157">In .NET Standard, on the web, and in the Linux world, UTF-8 is now the dominant encoding.</span></span>
- <span data-ttu-id="252d0-158">Många .NET Framework-program använder [UTF-16][].</span><span class="sxs-lookup"><span data-stu-id="252d0-158">Many .NET Framework applications use [UTF-16][].</span></span> <span data-ttu-id="252d0-159">Historiska skäl, kallas ibland ”Unicode”, en term där du nu refererar till den mest omfattande [standard](https://en.wikipedia.org/wiki/Unicode) som innehåller både UTF-8 och UTF-16.</span><span class="sxs-lookup"><span data-stu-id="252d0-159">For historical reasons, this is sometimes called "Unicode", a term that now refers to a broad [standard](https://en.wikipedia.org/wiki/Unicode) that includes both UTF-8 and UTF-16.</span></span>
- <span data-ttu-id="252d0-160">På Windows fortsätta många interna program som skrevs innan Unicode att använda Windows-1252 som standard.</span><span class="sxs-lookup"><span data-stu-id="252d0-160">On Windows, many native applications that predate Unicode continue to use Windows-1252 by default.</span></span>

<span data-ttu-id="252d0-161">Unicode-kodningar har också konceptet med en byte-ordning markera (BOM).</span><span class="sxs-lookup"><span data-stu-id="252d0-161">Unicode encodings also have the concept of a byte-order mark (BOM).</span></span> <span data-ttu-id="252d0-162">Strukturer inträffa i början av texten som talar om för en avkodare vilken kodning med hjälp av texten.</span><span class="sxs-lookup"><span data-stu-id="252d0-162">BOMs occur at the beginning of text to tell a decoder which encoding the text is using.</span></span> <span data-ttu-id="252d0-163">För multibyte kodningar Strukturen anger även [endianness](https://en.wikipedia.org/wiki/Endianness) för kodningen.</span><span class="sxs-lookup"><span data-stu-id="252d0-163">For multi-byte encodings, the BOM also indicates [endianness](https://en.wikipedia.org/wiki/Endianness) of the encoding.</span></span> <span data-ttu-id="252d0-164">Strukturer är avsedda att vara byte som skrivfel uppstår i icke-Unicode-text, vilket gör att en rimlig gissning att texten är Unicode när det finns en struktur.</span><span class="sxs-lookup"><span data-stu-id="252d0-164">BOMs are designed to be bytes that rarely occur in non-Unicode text, allowing a reasonable guess that text is Unicode when a BOM is present.</span></span>

<span data-ttu-id="252d0-165">Strukturer är valfria och antagandet är inte lika populära Linux över hela världen eftersom en pålitlig konvention UTF-8 används överallt.</span><span class="sxs-lookup"><span data-stu-id="252d0-165">BOMs are optional and their adoption isn't as popular in the Linux world because a dependable convention of UTF-8 is used everywhere.</span></span> <span data-ttu-id="252d0-166">De flesta Linux-program förutsätter att mata in text är kodat i UTF-8.</span><span class="sxs-lookup"><span data-stu-id="252d0-166">Most Linux applications presume that text input is encoded in UTF-8.</span></span> <span data-ttu-id="252d0-167">Även om många program i Linux identifierar och hanterar en struktur, ett tal inte, vilket leder till artefakter i texten ändras med dessa program.</span><span class="sxs-lookup"><span data-stu-id="252d0-167">While many Linux applications will recognize and correctly handle a BOM, a number do not, leading to artifacts in text manipulated with those applications.</span></span>

<span data-ttu-id="252d0-168">**Därför**:</span><span class="sxs-lookup"><span data-stu-id="252d0-168">**Therefore**:</span></span>

- <span data-ttu-id="252d0-169">Om du arbetar huvudsakligen med Windows-program och Windows PowerShell, bör du föredrar en kodning som UTF-8 med BOM eller UTF-16.</span><span class="sxs-lookup"><span data-stu-id="252d0-169">If you work primarily with Windows applications and Windows PowerShell, you should prefer an encoding like UTF-8 with BOM or UTF-16.</span></span>
- <span data-ttu-id="252d0-170">Om du arbetar på olika plattformar, bör du föredrar UTF-8 med BOM.</span><span class="sxs-lookup"><span data-stu-id="252d0-170">If you work across platforms, you should prefer UTF-8 with BOM.</span></span>
- <span data-ttu-id="252d0-171">Om du arbetar huvudsakligen i Linux-associerade kontexter bör du föredrar UTF-8 utan BOM.</span><span class="sxs-lookup"><span data-stu-id="252d0-171">If you work mainly in Linux-associated contexts, you should prefer UTF-8 without BOM.</span></span>
- <span data-ttu-id="252d0-172">Windows-1252 och latin 1 är i stort sett äldre kodningar som du bör undvika att om möjligt.</span><span class="sxs-lookup"><span data-stu-id="252d0-172">Windows-1252 and latin-1 are essentially legacy encodings that you should avoid if possible.</span></span>
  <span data-ttu-id="252d0-173">Men kan vissa äldre Windows-program bero på dem.</span><span class="sxs-lookup"><span data-stu-id="252d0-173">However, some older Windows applications may depend on them.</span></span>
- <span data-ttu-id="252d0-174">Det är också värt att skriptet är att registrera [encoding-beroende](https://github.com/PowerShell/PowerShell/issues/3466), vilket innebär att en ändring av kodning på ett signerade skript kräver uppsägning.</span><span class="sxs-lookup"><span data-stu-id="252d0-174">It's also worth noting that script signing is [encoding-dependent](https://github.com/PowerShell/PowerShell/issues/3466), meaning a change of encoding on a signed script will require resigning.</span></span>

## <a name="configuring-vscode"></a><span data-ttu-id="252d0-175">Konfigurera VSCode</span><span class="sxs-lookup"><span data-stu-id="252d0-175">Configuring VSCode</span></span>

<span data-ttu-id="252d0-176">Vscodes standardkodning är UTF-8 utan BOM.</span><span class="sxs-lookup"><span data-stu-id="252d0-176">VSCode's default encoding is UTF-8 without BOM.</span></span>

<span data-ttu-id="252d0-177">Ange [Vscodes kodning][]går du till inställningar för VSCode (<kbd>Ctrl<kbd>+</kbd>,</kbd>) och ange den `"files.encoding"` inställningen:</span><span class="sxs-lookup"><span data-stu-id="252d0-177">To set [VSCode's encoding][], go to the VSCode settings (<kbd>Ctrl<kbd>+</kbd>,</kbd>) and set the `"files.encoding"` setting:</span></span>

```json
"files.encoding": "utf8bom"
```

<span data-ttu-id="252d0-178">Några möjliga värden är:</span><span class="sxs-lookup"><span data-stu-id="252d0-178">Some possible values are:</span></span>

- <span data-ttu-id="252d0-179">`utf8`: [UTF-8] utan BOM</span><span class="sxs-lookup"><span data-stu-id="252d0-179">`utf8`: [UTF-8] without BOM</span></span>
- <span data-ttu-id="252d0-180">`utf8bom`: [UTF-8] med BOM</span><span class="sxs-lookup"><span data-stu-id="252d0-180">`utf8bom`: [UTF-8] with BOM</span></span>
- <span data-ttu-id="252d0-181">`utf16le`: Little endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="252d0-181">`utf16le`: Little endian [UTF-16]</span></span>
- <span data-ttu-id="252d0-182">`utf16be`: Big endian [UTF-16]</span><span class="sxs-lookup"><span data-stu-id="252d0-182">`utf16be`: Big endian [UTF-16]</span></span>
- <span data-ttu-id="252d0-183">`windows1252`: [Windows-1252]</span><span class="sxs-lookup"><span data-stu-id="252d0-183">`windows1252`: [Windows-1252]</span></span>

<span data-ttu-id="252d0-184">Du bör få en listruta för detta i vyn GUI eller visa Completion-händelser för den i JSON.</span><span class="sxs-lookup"><span data-stu-id="252d0-184">You should get a dropdown for this in the GUI view, or completions for it in the JSON view.</span></span>

<span data-ttu-id="252d0-185">Du kan också lägga till följande Autodetect kodning när det är möjligt:</span><span class="sxs-lookup"><span data-stu-id="252d0-185">You can also add the following to autodetect encoding when possible:</span></span>

```json
"files.autoGuessEncoding": true
```

<span data-ttu-id="252d0-186">Om du inte vill att dessa inställningar påverkar alla filtyper, kan VSCode också konfigurationer per språk.</span><span class="sxs-lookup"><span data-stu-id="252d0-186">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="252d0-187">Skapa en språkspecifik inställning genom att ange inställningar i en `[<language-name>]` fält.</span><span class="sxs-lookup"><span data-stu-id="252d0-187">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="252d0-188">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="252d0-188">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

## <a name="configuring-powershell"></a><span data-ttu-id="252d0-189">Konfigurera PowerShell</span><span class="sxs-lookup"><span data-stu-id="252d0-189">Configuring PowerShell</span></span>

<span data-ttu-id="252d0-190">PowerShell-standardkodning varierar beroende på version:</span><span class="sxs-lookup"><span data-stu-id="252d0-190">PowerShell's default encoding varies depending on version:</span></span>

- <span data-ttu-id="252d0-191">I PowerShell 6 + är standardkodning UTF-8 utan BOM på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="252d0-191">In PowerShell 6+, the default encoding is UTF-8 without BOM on all platforms.</span></span>
- <span data-ttu-id="252d0-192">Windows PowerShell, standardkodning är vanligtvis Windows-1252, en utökning av [latin 1][], även kallad ISO 8859-1.</span><span class="sxs-lookup"><span data-stu-id="252d0-192">In Windows PowerShell, the default encoding is usually Windows-1252, an extension of [latin-1][], also known as ISO 8859-1.</span></span>

<span data-ttu-id="252d0-193">Du kan hitta din standardkodning med detta i PowerShell 5 +:</span><span class="sxs-lookup"><span data-stu-id="252d0-193">In PowerShell 5+ you can find your default encoding with this:</span></span>

```powershell
[psobject].Assembly.GetTypes() | Where-Object { $_.Name -eq 'ClrFacade'} |
  ForEach-Object {
    $_.GetMethod('GetDefaultEncoding', [System.Reflection.BindingFlags]'nonpublic,static').Invoke($null, @())
  }
```

<span data-ttu-id="252d0-194">Följande [skriptet](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) kan användas för att fastställa vad kodning PowerShell-sessionen härleder för ett skript utan en struktur.</span><span class="sxs-lookup"><span data-stu-id="252d0-194">The following [script](https://gist.github.com/rjmholt/3d8dd4849f718c914132ce3c5b278e0e) can be used to determine what encoding your PowerShell session infers for a script without a BOM.</span></span>

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

<span data-ttu-id="252d0-195">Det är möjligt att konfigurera PowerShell för att använda en viss kodning som vanligtvis med profilinställningar.</span><span class="sxs-lookup"><span data-stu-id="252d0-195">It's possible to configure PowerShell to use a given encoding more generally using profile settings.</span></span> <span data-ttu-id="252d0-196">Se följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="252d0-196">See the following articles:</span></span>

- <span data-ttu-id="252d0-197">[@mklement0]'s [svar om PowerShell kodning på StackOverflow](https://stackoverflow.com/a/40098904).</span><span class="sxs-lookup"><span data-stu-id="252d0-197">[@mklement0]'s [answer about PowerShell encoding on StackOverflow](https://stackoverflow.com/a/40098904).</span></span>
- <span data-ttu-id="252d0-198">[@rkeithhill]'s [blogginlägget om hantering av BOM utan UTF-8 indata i PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span><span class="sxs-lookup"><span data-stu-id="252d0-198">[@rkeithhill]'s [blog post about dealing with BOM-less UTF-8 input in PowerShell](https://rkeithhill.wordpress.com/2010/05/26/handling-native-exe-output-encoding-in-utf8-with-no-bom/).</span></span>

<span data-ttu-id="252d0-199">Det går inte att tvinga PowerShell för att använda en specifik inkommande kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-199">It's not possible to force PowerShell to use a specific input encoding.</span></span> <span data-ttu-id="252d0-200">PowerShell 5.1 och under Windows-1252-kodning när det finns inga BOM som standard.</span><span class="sxs-lookup"><span data-stu-id="252d0-200">PowerShell 5.1 and below default to Windows-1252 encoding when there's no BOM.</span></span> <span data-ttu-id="252d0-201">Det är bäst att spara skript i en Unicode-format med en struktur för samverkan skäl.</span><span class="sxs-lookup"><span data-stu-id="252d0-201">For interoperability reasons, it's best to save scripts in a Unicode format with a BOM.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="252d0-202">Verktyg från någon annan har den touch PowerShell skript kan påverkas av valen kodning eller koda om skripten till en annan kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-202">Any other tools you have that touch PowerShell scripts may be affected by your encoding choices or re-encode your scripts to another encoding.</span></span>

### <a name="existing-scripts"></a><span data-ttu-id="252d0-203">Befintliga skript</span><span class="sxs-lookup"><span data-stu-id="252d0-203">Existing scripts</span></span>

<span data-ttu-id="252d0-204">Skript redan i filsystemet kan behöva kodas igen till din nya valda kodning.</span><span class="sxs-lookup"><span data-stu-id="252d0-204">Scripts already on the file system may need to be re-encoded to your new chosen encoding.</span></span> <span data-ttu-id="252d0-205">I det nedre fältet för VSCode visas etiketten UTF-8.</span><span class="sxs-lookup"><span data-stu-id="252d0-205">In the bottom bar of VSCode, you'll see the label UTF-8.</span></span> <span data-ttu-id="252d0-206">Klicka om du vill öppna Åtgärdsfältet och välj **spara med kodning**.</span><span class="sxs-lookup"><span data-stu-id="252d0-206">Click it to open the action bar and select **Save with encoding**.</span></span> <span data-ttu-id="252d0-207">Du kan nu välja en ny kodning för filen.</span><span class="sxs-lookup"><span data-stu-id="252d0-207">You can now pick a new encoding for that file.</span></span> <span data-ttu-id="252d0-208">Se [Vscodes kodning][] fullständiga instruktioner.</span><span class="sxs-lookup"><span data-stu-id="252d0-208">See [VSCode's encoding][] for full instructions.</span></span>

<span data-ttu-id="252d0-209">Om du vill koda om flera filer kan använda du följande skript:</span><span class="sxs-lookup"><span data-stu-id="252d0-209">If you need to re-encode multiple files, you can use the following script:</span></span>

```powershell
Get-ChildItem *.ps1 -Recurse | ForEach-Object {
    $content = Get-Content -Path $_
    Set-Content -Path $_.Fullname -Value $content -Encoding UTF8 -PassThru -Force
}
```

### <a name="the-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="252d0-210">PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="252d0-210">The PowerShell Integrated Scripting Environment (ISE)</span></span>

<span data-ttu-id="252d0-211">Du behöver synkronisera dina kodning inställningar om du också redigera skript med hjälp av PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="252d0-211">If you also edit scripts using the PowerShell ISE, you need to synchronize your encoding settings there.</span></span>

<span data-ttu-id="252d0-212">ISE bör respektera en struktur, men det är också möjligt att använda reflektion till [Ange kodning](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span><span class="sxs-lookup"><span data-stu-id="252d0-212">The ISE should honor a BOM, but it's also possible to use reflection to [set the encoding](https://bensonxion.wordpress.com/2012/04/25/powershell-ise-default-saveas-encoding/).</span></span>
<span data-ttu-id="252d0-213">Observera att detta skulle sparas mellan omstarter.</span><span class="sxs-lookup"><span data-stu-id="252d0-213">Note that this wouldn't be persisted between startups.</span></span>

### <a name="source-control-software"></a><span data-ttu-id="252d0-214">Program för källkontroll</span><span class="sxs-lookup"><span data-stu-id="252d0-214">Source control software</span></span>

<span data-ttu-id="252d0-215">Vissa verktyg för källa kontroll, till exempel git, Ignorera kodningar; Git spårar bara byte.</span><span class="sxs-lookup"><span data-stu-id="252d0-215">Some source control tools, such as git, ignore encodings; git just tracks the bytes.</span></span>
<span data-ttu-id="252d0-216">Andra, kanske t.ex. TFS eller Mercurial, inte.</span><span class="sxs-lookup"><span data-stu-id="252d0-216">Others, like TFS or Mercurial, may not.</span></span> <span data-ttu-id="252d0-217">Även vissa git-baserade verktyg är beroende av avkodning text.</span><span class="sxs-lookup"><span data-stu-id="252d0-217">Even some git-based tools rely on decoding text.</span></span>

<span data-ttu-id="252d0-218">När så är fallet kontrollerar du:</span><span class="sxs-lookup"><span data-stu-id="252d0-218">When this is the case, make sure you:</span></span>

- <span data-ttu-id="252d0-219">Konfigurera textkodning i din källkontroll för att matcha din VSCode-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="252d0-219">Configure the text encoding in your source control to match your VSCode configuration.</span></span>
- <span data-ttu-id="252d0-220">Se till att alla filer är markerade i källkontrollen i den relevanta kodningen.</span><span class="sxs-lookup"><span data-stu-id="252d0-220">Ensure all your files are checked into source control in the relevant encoding.</span></span>
- <span data-ttu-id="252d0-221">Vara försiktig med ändringar i kodningen emot via källkontroll.</span><span class="sxs-lookup"><span data-stu-id="252d0-221">Be wary of changes to the encoding received through source control.</span></span> <span data-ttu-id="252d0-222">Ett nyckel tecken på detta är en diff som anger ändringar men där ingenting verkar har ändrats (eftersom byte har men har inte).</span><span class="sxs-lookup"><span data-stu-id="252d0-222">A key sign of this is a diff indicating changes but where nothing seems to have changed (because bytes have but characters have not).</span></span>

### <a name="collaborators-environments"></a><span data-ttu-id="252d0-223">Medarbetare-miljöer</span><span class="sxs-lookup"><span data-stu-id="252d0-223">Collaborators' environments</span></span>

<span data-ttu-id="252d0-224">Se till att dina medarbetare på alla filer som du delar inte har inställningar som åsidosätter kodningen genom att behöva koda PowerShell-filer på konfigurerar källkontroll.</span><span class="sxs-lookup"><span data-stu-id="252d0-224">On top of configuring source control, ensure that your collaborators on any files you share don't have settings that override your encoding by re-encoding PowerShell files.</span></span>

### <a name="other-programs"></a><span data-ttu-id="252d0-225">Andra program</span><span class="sxs-lookup"><span data-stu-id="252d0-225">Other programs</span></span>

<span data-ttu-id="252d0-226">Alla andra program som läser eller skriver ett PowerShell-skript kan koda om den.</span><span class="sxs-lookup"><span data-stu-id="252d0-226">Any other program that reads or writes a PowerShell script may re-encode it.</span></span>

<span data-ttu-id="252d0-227">Några exempel är:</span><span class="sxs-lookup"><span data-stu-id="252d0-227">Some examples are:</span></span>

- <span data-ttu-id="252d0-228">Du kan använda Urklipp för att kopiera och klistra in ett skript.</span><span class="sxs-lookup"><span data-stu-id="252d0-228">Using the clipboard to copy and paste a script.</span></span> <span data-ttu-id="252d0-229">Detta är vanligt i scenarier som:</span><span class="sxs-lookup"><span data-stu-id="252d0-229">This is common in scenarios like:</span></span>
  - <span data-ttu-id="252d0-230">Kopierar ett skript till en virtuell dator</span><span class="sxs-lookup"><span data-stu-id="252d0-230">Copying a script into a VM</span></span>
  - <span data-ttu-id="252d0-231">Kopierar ett skript från ett e-postmeddelande eller en webbsida</span><span class="sxs-lookup"><span data-stu-id="252d0-231">Copying a script out of an email or webpage</span></span>
  - <span data-ttu-id="252d0-232">Kopierar ett skript till eller från ett Microsoft Word- eller PowerPoint-dokument</span><span class="sxs-lookup"><span data-stu-id="252d0-232">Copying a script into or out of a Microsoft Word or PowerPoint document</span></span>
- <span data-ttu-id="252d0-233">Andra textredigerare, till exempel:</span><span class="sxs-lookup"><span data-stu-id="252d0-233">Other text editors, such as:</span></span>
  - <span data-ttu-id="252d0-234">Anteckningar</span><span class="sxs-lookup"><span data-stu-id="252d0-234">Notepad</span></span>
  - <span data-ttu-id="252d0-235">vim</span><span class="sxs-lookup"><span data-stu-id="252d0-235">vim</span></span>
  - <span data-ttu-id="252d0-236">Alla andra PowerShell-Skriptredigeraren</span><span class="sxs-lookup"><span data-stu-id="252d0-236">Any other PowerShell script editor</span></span>
- <span data-ttu-id="252d0-237">Redigera verktyg, som text:</span><span class="sxs-lookup"><span data-stu-id="252d0-237">Text editing utilities, like:</span></span>
  - `Get-Content`/`Set-Content`/`Out-File`
  - <span data-ttu-id="252d0-238">PowerShell-omdirigering operatörer som `>` och `>>`</span><span class="sxs-lookup"><span data-stu-id="252d0-238">PowerShell redirection operators like `>` and `>>`</span></span>
  - `sed`/`awk`
- <span data-ttu-id="252d0-239">Filen överföringsprogram, t.ex.:</span><span class="sxs-lookup"><span data-stu-id="252d0-239">File transfer programs, like:</span></span>
  - <span data-ttu-id="252d0-240">En webbläsare, när du laddar ned skript</span><span class="sxs-lookup"><span data-stu-id="252d0-240">A web browser, when downloading scripts</span></span>
  - <span data-ttu-id="252d0-241">En filresurs</span><span class="sxs-lookup"><span data-stu-id="252d0-241">A file share</span></span>

<span data-ttu-id="252d0-242">Vissa av verktygen kan hantera i byte i stället för text, men andra erbjuder kodning konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="252d0-242">Some of these tools deal in bytes rather than text, but others offer encoding configurations.</span></span> <span data-ttu-id="252d0-243">I de fall där du behöver konfigurera en kodning kan behöva du blir samma som redigeringsprogram kodning för att förhindra problem.</span><span class="sxs-lookup"><span data-stu-id="252d0-243">In those cases where you need to configure an encoding, you need to make it the same as your editor encoding to prevent problems.</span></span>

## <a name="other-resources-on-encoding-in-powershell"></a><span data-ttu-id="252d0-244">Andra resurser på kodning i PowerShell</span><span class="sxs-lookup"><span data-stu-id="252d0-244">Other resources on encoding in PowerShell</span></span>

<span data-ttu-id="252d0-245">Det finns några andra bra inlägg på kodning och konfigurera kodning i PowerShell som är värda att en läsning:</span><span class="sxs-lookup"><span data-stu-id="252d0-245">There are a few other nice posts on encoding and configuring encoding in PowerShell that are worth a read:</span></span>

- <span data-ttu-id="252d0-246">[@mklement0]'s [sammanfattning av PowerShell kodning på StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span><span class="sxs-lookup"><span data-stu-id="252d0-246">[@mklement0]'s [summary of PowerShell encoding on StackOverflow](https://stackoverflow.com/questions/40098771/changing-powershells-default-output-encoding-to-utf-8)</span></span>
- <span data-ttu-id="252d0-247">Tidigare problem öppnas på vscode-PowerShell för kodning problem:</span><span class="sxs-lookup"><span data-stu-id="252d0-247">Previous issues opened on vscode-PowerShell for encoding problems:</span></span>
  - [<span data-ttu-id="252d0-248">#1308</span><span class="sxs-lookup"><span data-stu-id="252d0-248">#1308</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1308)
  - [<span data-ttu-id="252d0-249">#1628</span><span class="sxs-lookup"><span data-stu-id="252d0-249">#1628</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1628)
  - [<span data-ttu-id="252d0-250">#1680</span><span class="sxs-lookup"><span data-stu-id="252d0-250">#1680</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1680)
  - [<span data-ttu-id="252d0-251">#1744</span><span class="sxs-lookup"><span data-stu-id="252d0-251">#1744</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1744)
  - [<span data-ttu-id="252d0-252">#1751</span><span class="sxs-lookup"><span data-stu-id="252d0-252">#1751</span></span>](https://github.com/PowerShell/vscode-powershell/issues/1751)
- [<span data-ttu-id="252d0-253">Klassiskt *Johan på programvara* Skriv upp om Unicode</span><span class="sxs-lookup"><span data-stu-id="252d0-253">The classic *Joel on Software* write up about Unicode</span></span>](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)
- [<span data-ttu-id="252d0-254">Kodning i .NET Standard</span><span class="sxs-lookup"><span data-stu-id="252d0-254">Encoding in .NET Standard</span></span>](https://github.com/dotnet/standard/issues/260#issuecomment-289549508)


[@mklement0]: https://github.com/mklement0
[@rkeithhill]: https://github.com/rkeithhill
[Windows-1252]: https://wikipedia.org/wiki/Windows-1252
[latin 1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[latin-1]: https://wikipedia.org/wiki/ISO/IEC_8859-1
[UTF-8]: https://wikipedia.org/wiki/UTF-8
[byte-ordningsmarkering]: https://wikipedia.org/wiki/Byte_order_mark
[byte-order mark]: https://wikipedia.org/wiki/Byte_order_mark
[UTF-16]: https://wikipedia.org/wiki/UTF-16
[Språk Server-protokoll]: https://microsoft.github.io/language-server-protocol/
[Language Server Protocol]: https://microsoft.github.io/language-server-protocol/
[Vscodes kodning]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support
[VSCode's encoding]: https://code.visualstudio.com/docs/editor/codebasics#_file-encoding-support