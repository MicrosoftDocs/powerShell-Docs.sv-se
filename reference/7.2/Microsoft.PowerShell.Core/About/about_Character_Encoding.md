---
description: Beskriver hur PowerShell använder tecken kodning för indata och utdata av sträng data.
Locale: en-US
ms.date: 10/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_character_encoding?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Character_Encoding
ms.openlocfilehash: 3b47a528b0beae5e8142157454cbc676ffd7e795
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349826"
---
# <a name="about_character_encoding"></a><span data-ttu-id="b61c9-103">about_Character_Encoding</span><span class="sxs-lookup"><span data-stu-id="b61c9-103">about_Character_Encoding</span></span>

## <a name="short-description"></a><span data-ttu-id="b61c9-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b61c9-104">Short description</span></span>
<span data-ttu-id="b61c9-105">Beskriver hur PowerShell använder tecken kodning för indata och utdata av sträng data.</span><span class="sxs-lookup"><span data-stu-id="b61c9-105">Describes how PowerShell uses character encoding for input and output of string data.</span></span>

## <a name="long-description"></a><span data-ttu-id="b61c9-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b61c9-106">Long description</span></span>

<span data-ttu-id="b61c9-107">Unicode är en global tecken kodnings standard.</span><span class="sxs-lookup"><span data-stu-id="b61c9-107">Unicode is a worldwide character-encoding standard.</span></span> <span data-ttu-id="b61c9-108">Systemet använder Unicode enbart för tecken-och sträng manipulation.</span><span class="sxs-lookup"><span data-stu-id="b61c9-108">The system uses Unicode exclusively for character and string manipulation.</span></span> <span data-ttu-id="b61c9-109">En detaljerad beskrivning av alla aspekter av Unicode finns i Unicode- [standarden](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="b61c9-109">For a detailed description of all aspects of Unicode, refer to [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>

<span data-ttu-id="b61c9-110">Windows stöder Unicode och traditionella teckenuppsättningar.</span><span class="sxs-lookup"><span data-stu-id="b61c9-110">Windows supports Unicode and traditional character sets.</span></span> <span data-ttu-id="b61c9-111">Traditionella teckenuppsättningar, t. ex. Windows tecken tabeller, använder 8-bitars värden eller kombinationer av 8-bitars värden för att representera de tecken som används i ett särskilt språk eller geografiskt regions inställningar.</span><span class="sxs-lookup"><span data-stu-id="b61c9-111">Traditional character sets, such as Windows code pages, use 8-bit values or combinations of 8-bit values to represent the characters used in a specific language or geographical region settings.</span></span>

<span data-ttu-id="b61c9-112">I PowerShell används Unicode-tecken som standard.</span><span class="sxs-lookup"><span data-stu-id="b61c9-112">PowerShell uses a Unicode character set by default.</span></span> <span data-ttu-id="b61c9-113">Flera cmdlets har dock en **encoding** -parameter som kan ange encoding för en annan teckenuppsättning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-113">However, several cmdlets have an **Encoding** parameter that can specify encoding for a different character set.</span></span> <span data-ttu-id="b61c9-114">Med den här parametern kan du välja den speciella tecken kodning som du behöver för att samverka med andra system och program.</span><span class="sxs-lookup"><span data-stu-id="b61c9-114">This parameter allows you to choose the specific the character encoding you need for interoperability with other systems and applications.</span></span>

<span data-ttu-id="b61c9-115">Följande cmdletar har parametern **encoding** :</span><span class="sxs-lookup"><span data-stu-id="b61c9-115">The following cmdlets have the **Encoding** parameter:</span></span>

- <span data-ttu-id="b61c9-116">Microsoft. PowerShell. Management</span><span class="sxs-lookup"><span data-stu-id="b61c9-116">Microsoft.PowerShell.Management</span></span>
  - <span data-ttu-id="b61c9-117">Add-Content</span><span class="sxs-lookup"><span data-stu-id="b61c9-117">Add-Content</span></span>
  - <span data-ttu-id="b61c9-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="b61c9-118">Get-Content</span></span>
  - <span data-ttu-id="b61c9-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="b61c9-119">Set-Content</span></span>
- <span data-ttu-id="b61c9-120">Microsoft.PowerShell.Utility</span><span class="sxs-lookup"><span data-stu-id="b61c9-120">Microsoft.PowerShell.Utility</span></span>
  - <span data-ttu-id="b61c9-121">Export-Clixml</span><span class="sxs-lookup"><span data-stu-id="b61c9-121">Export-Clixml</span></span>
  - <span data-ttu-id="b61c9-122">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="b61c9-122">Export-Csv</span></span>
  - <span data-ttu-id="b61c9-123">Export-PSSession</span><span class="sxs-lookup"><span data-stu-id="b61c9-123">Export-PSSession</span></span>
  - <span data-ttu-id="b61c9-124">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="b61c9-124">Format-Hex</span></span>
  - <span data-ttu-id="b61c9-125">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="b61c9-125">Import-Csv</span></span>
  - <span data-ttu-id="b61c9-126">Out-File</span><span class="sxs-lookup"><span data-stu-id="b61c9-126">Out-File</span></span>
  - <span data-ttu-id="b61c9-127">Select-String</span><span class="sxs-lookup"><span data-stu-id="b61c9-127">Select-String</span></span>
  - <span data-ttu-id="b61c9-128">Send-MailMessage</span><span class="sxs-lookup"><span data-stu-id="b61c9-128">Send-MailMessage</span></span>

## <a name="the-byte-order-mark"></a><span data-ttu-id="b61c9-129">Byte-ordning-markering</span><span class="sxs-lookup"><span data-stu-id="b61c9-129">The byte-order-mark</span></span>

<span data-ttu-id="b61c9-130">Byte-order-markering (BOM) är en _Unicode-signatur_ i de första byten i en fil eller text ström som anger vilken Unicode-kodning som används för data.</span><span class="sxs-lookup"><span data-stu-id="b61c9-130">The byte-order-mark (BOM) is a _Unicode signature_ in the first few bytes of a file or text stream that indicate which Unicode encoding used for the data.</span></span> <span data-ttu-id="b61c9-131">Mer information finns i dokumentationen [för byte-ordnings märkning](/globalization/encoding/byte-order-mark) .</span><span class="sxs-lookup"><span data-stu-id="b61c9-131">For more information, see the [Byte order mark](/globalization/encoding/byte-order-mark) documentation.</span></span>

<span data-ttu-id="b61c9-132">I Windows PowerShell skapar Unicode-kodning, förutom `UTF7` , alltid en struktur.</span><span class="sxs-lookup"><span data-stu-id="b61c9-132">In Windows PowerShell, any Unicode encoding, except `UTF7`, always creates a BOM.</span></span> <span data-ttu-id="b61c9-133">PowerShell-kärnan är standardvärdet `utf8NoBOM` för alla text utdata.</span><span class="sxs-lookup"><span data-stu-id="b61c9-133">PowerShell Core defaults to `utf8NoBOM` for all text output.</span></span>

<span data-ttu-id="b61c9-134">Undvik att använda strukturer i UTF-8-filer för bästa möjliga kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="b61c9-134">For best overall compatibility, avoid using BOMs in UTF-8 files.</span></span> <span data-ttu-id="b61c9-135">UNIX-plattformar och UNIX-arvs verktyg som också används på Windows-plattformar stöder inte strukturer.</span><span class="sxs-lookup"><span data-stu-id="b61c9-135">Unix platforms and Unix-heritage utilities also used on Windows Platforms don't support BOMs.</span></span>

<span data-ttu-id="b61c9-136">`UTF7`Kodningen bör också undvikas.</span><span class="sxs-lookup"><span data-stu-id="b61c9-136">Similarly, `UTF7` encoding should be avoided.</span></span> <span data-ttu-id="b61c9-137">UTF-7 är inte en standard Unicode-kodning och skrivs utan någon struktur i alla versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b61c9-137">UTF-7 is not a standard Unicode encoding and is written without a BOM in all versions of PowerShell.</span></span>

<span data-ttu-id="b61c9-138">Att skapa PowerShell-skript på en UNIX-liknande plattform eller med ett plattforms oberoende redigerare i Windows, till exempel Visual Studio Code, resulterar i en fil som kodas med `UTF8NoBOM` .</span><span class="sxs-lookup"><span data-stu-id="b61c9-138">Creating PowerShell scripts on a Unix-like platform or using a cross-platform editor on Windows, such as Visual Studio Code, results in a file encoded using `UTF8NoBOM`.</span></span> <span data-ttu-id="b61c9-139">De här filerna fungerar bra på PowerShell-kärnan, men kan brytas i Windows PowerShell om filen innehåller icke-ASCII-tecken.</span><span class="sxs-lookup"><span data-stu-id="b61c9-139">These files work fine on PowerShell Core, but may break in Windows PowerShell if the file contains non-Ascii characters.</span></span>

<span data-ttu-id="b61c9-140">Om du behöver använda icke-ASCII-tecken i skripten kan du spara dem som UTF-8 med BOM.</span><span class="sxs-lookup"><span data-stu-id="b61c9-140">If you need to use non-Ascii characters in your scripts, save them as UTF-8 with BOM.</span></span> <span data-ttu-id="b61c9-141">Utan strukturen tolkar Windows PowerShell ditt skript som kodat i den äldre "ANSI"-tecken tabellen.</span><span class="sxs-lookup"><span data-stu-id="b61c9-141">Without the BOM, Windows PowerShell misinterprets your script as being encoded in the legacy "ANSI" codepage.</span></span> <span data-ttu-id="b61c9-142">Filer som har UTF-8-strukturen kan däremot vara problematiska på UNIX-liknande plattformar.</span><span class="sxs-lookup"><span data-stu-id="b61c9-142">Conversely, files that do have the UTF-8 BOM can be problematic on Unix-like platforms.</span></span> <span data-ttu-id="b61c9-143">Många UNIX-verktyg som `cat` , `sed` , `awk` och vissa redigerare, till exempel `gedit` inte vet hur du ska behandla strukturen.</span><span class="sxs-lookup"><span data-stu-id="b61c9-143">Many Unix tools such as `cat`, `sed`, `awk`, and some editors such as `gedit` don't know how to treat the BOM.</span></span>

## <a name="character-encoding-in-windows-powershell"></a><span data-ttu-id="b61c9-144">Tecken kodning i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b61c9-144">Character encoding in Windows PowerShell</span></span>

<span data-ttu-id="b61c9-145">I PowerShell 5,1 stöder **encoding** -parametern följande värden:</span><span class="sxs-lookup"><span data-stu-id="b61c9-145">In PowerShell 5.1, the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="b61c9-146">`Ascii` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="b61c9-146">`Ascii` Uses Ascii (7-bit) character set.</span></span>
- <span data-ttu-id="b61c9-147">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="b61c9-147">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="b61c9-148">`BigEndianUTF32` Använder UTF-32 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="b61c9-148">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="b61c9-149">`Byte` Kodar en uppsättning tecken i en sekvens med byte.</span><span class="sxs-lookup"><span data-stu-id="b61c9-149">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="b61c9-150">`Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="b61c9-150">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="b61c9-151">`Oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="b61c9-151">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="b61c9-152">`String` Samma som `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="b61c9-152">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="b61c9-153">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="b61c9-153">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="b61c9-154">`Unknown` Samma som `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="b61c9-154">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="b61c9-155">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="b61c9-155">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>
- <span data-ttu-id="b61c9-156">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="b61c9-156">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="b61c9-157">`UTF8` Använder UTF-8 (med struktur).</span><span class="sxs-lookup"><span data-stu-id="b61c9-157">`UTF8` Uses UTF-8 (with BOM).</span></span>

<span data-ttu-id="b61c9-158">I allmänhet använder Windows PowerShell Unicode [UTF-16LE-](https://wikipedia.org/wiki/UTF-16) kodning som standard.</span><span class="sxs-lookup"><span data-stu-id="b61c9-158">In general, Windows PowerShell uses the Unicode [UTF-16LE](https://wikipedia.org/wiki/UTF-16) encoding by default.</span></span> <span data-ttu-id="b61c9-159">Standard kodningen som används av cmdlets i Windows PowerShell är dock inte konsekvent.</span><span class="sxs-lookup"><span data-stu-id="b61c9-159">However, the default encoding used by cmdlets in Windows PowerShell is not consistent.</span></span>

> [!NOTE]
> <span data-ttu-id="b61c9-160">Om Unicode-kodning används, förutom `UTF7` , skapas alltid en struktur.</span><span class="sxs-lookup"><span data-stu-id="b61c9-160">Using any Unicode encoding, except `UTF7`, always creates a BOM.</span></span>

<span data-ttu-id="b61c9-161">För cmdletar som skriver utdata till filer:</span><span class="sxs-lookup"><span data-stu-id="b61c9-161">For cmdlets that write output to files:</span></span>

- <span data-ttu-id="b61c9-162">`Out-File` och omdirigerings operatörerna `>` och `>>` skapar UTF-16LE, som särskilt skiljer sig från `Set-Content` och `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="b61c9-162">`Out-File` and the redirection operators `>` and `>>` create UTF-16LE, which notably differs from `Set-Content` and `Add-Content`.</span></span>

- <span data-ttu-id="b61c9-163">`New-ModuleManifest``Export-CliXml`Dessutom skapar du UTF-16LE-filer.</span><span class="sxs-lookup"><span data-stu-id="b61c9-163">`New-ModuleManifest` and `Export-CliXml` also create UTF-16LE files.</span></span>

- <span data-ttu-id="b61c9-164">När målfilen är tom eller inte finns, `Set-Content` och `Add-Content` Använd `Default` encoding.</span><span class="sxs-lookup"><span data-stu-id="b61c9-164">When the target file is empty or doesn't exist, `Set-Content` and `Add-Content` use `Default` encoding.</span></span> <span data-ttu-id="b61c9-165">`Default` är den kodning som anges av den aktiva system språket för den gamla ANSI-kodsidan.</span><span class="sxs-lookup"><span data-stu-id="b61c9-165">`Default` is the encoding specified by the active system locale's ANSI legacy code page.</span></span>

- <span data-ttu-id="b61c9-166">`Export-Csv` skapar `Ascii` filer men använder olika kodning när du använder parametern **APPEND** (se nedan).</span><span class="sxs-lookup"><span data-stu-id="b61c9-166">`Export-Csv` creates `Ascii` files but uses different encoding when using **Append** parameter (see below).</span></span>

- <span data-ttu-id="b61c9-167">`Export-PSSession` skapar UTF-8-filer med struktur som standard.</span><span class="sxs-lookup"><span data-stu-id="b61c9-167">`Export-PSSession` creates UTF-8 files with BOM by default.</span></span>

- <span data-ttu-id="b61c9-168">`New-Item -Type File -Value` skapar en struktur lös UTF-8-fil.</span><span class="sxs-lookup"><span data-stu-id="b61c9-168">`New-Item -Type File -Value` creates a BOM-less UTF-8 file.</span></span>

- <span data-ttu-id="b61c9-169">`Send-MailMessage` använder `Default` kodning som standard.</span><span class="sxs-lookup"><span data-stu-id="b61c9-169">`Send-MailMessage` uses `Default` encoding by default.</span></span>

- <span data-ttu-id="b61c9-170">`Start-Transcript` skapar `Utf8` filer med en struktur.</span><span class="sxs-lookup"><span data-stu-id="b61c9-170">`Start-Transcript` creates `Utf8` files with a BOM.</span></span> <span data-ttu-id="b61c9-171">När parametern **APPEND** används kan kodningen vara olika (se nedan).</span><span class="sxs-lookup"><span data-stu-id="b61c9-171">When the **Append** parameter is used, the encoding can be different (see below).</span></span>

<span data-ttu-id="b61c9-172">För kommandon som lägger till i en befintlig fil:</span><span class="sxs-lookup"><span data-stu-id="b61c9-172">For commands that append to an existing file:</span></span>

- <span data-ttu-id="b61c9-173">`Out-File -Append` och `>>` omdirigerings operatorn inte gör något försök att matcha kodningen för den befintliga mål filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="b61c9-173">`Out-File -Append` and the `>>` redirection operator make no attempt to match the encoding of the existing target file's content.</span></span> <span data-ttu-id="b61c9-174">I stället använder de standard kodningen om inte **encoding** -parametern används.</span><span class="sxs-lookup"><span data-stu-id="b61c9-174">Instead, they use the default encoding unless the **Encoding** parameter is used.</span></span> <span data-ttu-id="b61c9-175">Du måste använda filens ursprungliga kodning när du lägger till innehåll.</span><span class="sxs-lookup"><span data-stu-id="b61c9-175">You must use the files original encoding when appending content.</span></span>

- <span data-ttu-id="b61c9-176">Om en explicit **encoding** -parameter saknas `Add-Content` identifierar den befintliga kodningen och tillämpar den automatiskt på det nya innehållet.</span><span class="sxs-lookup"><span data-stu-id="b61c9-176">In the absence of an explicit **Encoding** parameter, `Add-Content` detects the existing encoding and automatically applies it to the new content.</span></span> <span data-ttu-id="b61c9-177">Om det befintliga innehållet saknar struktur `Default` används ANSI-kodning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-177">If the existing content has no BOM, `Default` ANSI encoding is used.</span></span> <span data-ttu-id="b61c9-178">Beteendet i `Add-Content` är detsamma i PowerShell Core (V6 och högre) förutom standard kodningen `Utf8` .</span><span class="sxs-lookup"><span data-stu-id="b61c9-178">The behavior of `Add-Content` is the same in PowerShell Core (v6 and higher) except the default encoding is `Utf8`.</span></span>

- <span data-ttu-id="b61c9-179">`Export-Csv -Append` matchar den befintliga kodningen när mål filen innehåller en struktur.</span><span class="sxs-lookup"><span data-stu-id="b61c9-179">`Export-Csv -Append` matches the existing encoding when the target file contains a BOM.</span></span> <span data-ttu-id="b61c9-180">Om en struktur saknas används `Utf8` kodning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-180">In the absence of a BOM, it uses `Utf8` encoding.</span></span>

- <span data-ttu-id="b61c9-181">`Start-Transcript -Append` matchar den befintliga kodningen av filer som innehåller en struktur.</span><span class="sxs-lookup"><span data-stu-id="b61c9-181">`Start-Transcript -Append` matches the existing encoding of files that include a BOM.</span></span> <span data-ttu-id="b61c9-182">Om det inte finns någon struktur är standardvärdet `Ascii` kodning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-182">In the absence of a BOM, it defaults to `Ascii` encoding.</span></span> <span data-ttu-id="b61c9-183">Den här kodningen kan leda till data förlust eller tecken skada när data i avskriften innehåller flera byte-tecken.</span><span class="sxs-lookup"><span data-stu-id="b61c9-183">This encoding can result in data loss or character corruption when the data in the transcript contains multibyte characters.</span></span>

<span data-ttu-id="b61c9-184">För cmdletar som läser sträng data i avsaknad av en struktur:</span><span class="sxs-lookup"><span data-stu-id="b61c9-184">For cmdlets that read string data in the absence of a BOM:</span></span>

- <span data-ttu-id="b61c9-185">`Get-Content` och `Import-PowerShellDataFile` använder `Default` ANSI-kodning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-185">`Get-Content` and `Import-PowerShellDataFile` uses the `Default` ANSI encoding.</span></span> <span data-ttu-id="b61c9-186">ANSI är också vad PowerShell-motorn använder när den läser käll koden från filer.</span><span class="sxs-lookup"><span data-stu-id="b61c9-186">ANSI is also what the PowerShell engine uses when it reads source code from files.</span></span>

- <span data-ttu-id="b61c9-187">`Import-Csv`, `Import-CliXml` och `Select-String` anta `Utf8` att ingen struktur saknas.</span><span class="sxs-lookup"><span data-stu-id="b61c9-187">`Import-Csv`, `Import-CliXml`, and `Select-String` assume `Utf8` in the absence of a BOM.</span></span>

## <a name="character-encoding-in-powershell-core"></a><span data-ttu-id="b61c9-188">Tecken kodning i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b61c9-188">Character encoding in PowerShell Core</span></span>

<span data-ttu-id="b61c9-189">I PowerShell Core (V6 och högre) stöder **encoding** -parametern följande värden:</span><span class="sxs-lookup"><span data-stu-id="b61c9-189">In PowerShell Core (v6 and higher), the **Encoding** parameter supports the following values:</span></span>

- <span data-ttu-id="b61c9-190">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="b61c9-190">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="b61c9-191">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-191">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="b61c9-192">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="b61c9-192">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="b61c9-193">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-193">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="b61c9-194">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="b61c9-194">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="b61c9-195">`utf8`: Kodar i UTF-8-format (ingen struktur).</span><span class="sxs-lookup"><span data-stu-id="b61c9-195">`utf8`: Encodes in UTF-8 format (no BOM).</span></span>
- <span data-ttu-id="b61c9-196">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="b61c9-196">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="b61c9-197">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="b61c9-197">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="b61c9-198">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="b61c9-198">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="b61c9-199">PowerShell-kärnan är standardvärdet `utf8NoBOM` för alla utdata.</span><span class="sxs-lookup"><span data-stu-id="b61c9-199">PowerShell Core defaults to `utf8NoBOM` for all output.</span></span>

<span data-ttu-id="b61c9-200">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="b61c9-200">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="b61c9-201">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage).</span><span class="sxs-lookup"><span data-stu-id="b61c9-201">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage).</span></span>

## <a name="changing-the-default-encoding"></a><span data-ttu-id="b61c9-202">Ändra standard kodning</span><span class="sxs-lookup"><span data-stu-id="b61c9-202">Changing the default encoding</span></span>

<span data-ttu-id="b61c9-203">PowerShell har två standardvariabler som kan användas för att ändra standard kodnings beteendet.</span><span class="sxs-lookup"><span data-stu-id="b61c9-203">PowerShell has two default variables that can be used to change the default encoding behavior.</span></span>

- `$PSDefaultParameterValues`
- `$OutputEncoding`

<span data-ttu-id="b61c9-204">Mer information finns i [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b61c9-204">For more information, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

<span data-ttu-id="b61c9-205">Från och med PowerShell 5,1 anropar omdirigerings operatörerna ( `>` och `>>` ) `Out-File` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="b61c9-205">Beginning in PowerShell 5.1, the redirection operators (`>` and `>>`) call the `Out-File` cmdlet.</span></span> <span data-ttu-id="b61c9-206">Därför kan du ange standard kodningen för dem med hjälp av `$PSDefaultParameterValues` Preference-variabeln som visas i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="b61c9-206">Therefore, you can set the default encoding of them using the `$PSDefaultParameterValues` preference variable as shown in this example:</span></span>

```powershell
$PSDefaultParameterValues['Out-File:Encoding'] = 'utf8'
```

<span data-ttu-id="b61c9-207">Använd följande instruktion för att ändra standard kodningen för alla cmdletar som har **kodnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="b61c9-207">Use the following statement to change the default encoding for all cmdlets that have the **Encoding** parameter.</span></span>

```powershell
$PSDefaultParameterValues['*:Encoding'] = 'utf8'
```

> [!IMPORTANT]
> <span data-ttu-id="b61c9-208">Genom att lägga till det här kommandot i din PowerShell-profil blir inställningen en session – global inställning som påverkar alla kommandon och skript som inte uttryckligen anger en kodning.</span><span class="sxs-lookup"><span data-stu-id="b61c9-208">Putting this command in your PowerShell profile makes the preference a session-global setting that affects all commands and scripts that do not explicitly specify an encoding.</span></span>
>
> <span data-ttu-id="b61c9-209">På samma sätt bör du inkludera sådana kommandon i dina skript eller moduler som du vill använda på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="b61c9-209">Similarly, you should include such commands in your scripts or modules that you want to behave the same way.</span></span> <span data-ttu-id="b61c9-210">Med dessa kommandon ser du till att cmdletar fungerar på samma sätt även när de körs av en annan användare, på en annan dator eller i en annan version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b61c9-210">Using these commands ensure that cmdlets behave the same way even when run by another user, on a different computer, or in a different version of PowerShell.</span></span>

<span data-ttu-id="b61c9-211">Den automatiska variabeln `$OutputEncoding` påverkar kodnings-PowerShell-användningen för att kommunicera med externa program.</span><span class="sxs-lookup"><span data-stu-id="b61c9-211">The automatic variable `$OutputEncoding` affects the encoding PowerShell uses to communicate with external programs.</span></span> <span data-ttu-id="b61c9-212">Det har ingen effekt på kodningen att operatörerna för utgående omdirigering och PowerShell-cmdlet: ar använder för att spara filer.</span><span class="sxs-lookup"><span data-stu-id="b61c9-212">It has no effect on the encoding that the output redirection operators and PowerShell cmdlets use to save to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="b61c9-213">Se även</span><span class="sxs-lookup"><span data-stu-id="b61c9-213">See also</span></span>

- [<span data-ttu-id="b61c9-214">Introduktion till tecken kodning i .NET</span><span class="sxs-lookup"><span data-stu-id="b61c9-214">Introduction to character encoding in .NET</span></span>](/dotnet/standard/base-types/character-encoding-introduction)
- [<span data-ttu-id="b61c9-215">Tecken tabeller – Win32-appar</span><span class="sxs-lookup"><span data-stu-id="b61c9-215">Code Pages - Win32 apps</span></span>](/windows/win32/intl/code-pages)
- [<span data-ttu-id="b61c9-216">Unicode-standarden</span><span class="sxs-lookup"><span data-stu-id="b61c9-216">The Unicode Standard</span></span>](https://www.unicode.org/standard/standard.html)
- [<span data-ttu-id="b61c9-217">Encoding. CodePage</span><span class="sxs-lookup"><span data-stu-id="b61c9-217">Encoding.CodePage</span></span>](/dotnet/api/system.text.encoding.codepage)
- [<span data-ttu-id="b61c9-218">UTF-16LE</span><span class="sxs-lookup"><span data-stu-id="b61c9-218">UTF-16LE</span></span>](https://wikipedia.org/wiki/UTF-16)
- [<span data-ttu-id="b61c9-219">Markering av byte ordning</span><span class="sxs-lookup"><span data-stu-id="b61c9-219">Byte order mark</span></span>](https://wikipedia.org/wiki/Byte_order_mark)
- [<span data-ttu-id="b61c9-220">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="b61c9-220">about_Preference_Variables</span></span>](about_Preference_Variables.md)
