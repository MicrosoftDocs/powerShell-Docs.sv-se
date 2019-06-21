---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Nya och uppdaterade cmdletar
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298659"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="4fb88-103">Nya och uppdaterade cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fb88-103">New and updated cmdlets</span></span>

<span data-ttu-id="4fb88-104">Vi har lagt till nya och uppdaterade befintliga cmdletar baserade på feedback från diskussionsgruppen.</span><span class="sxs-lookup"><span data-stu-id="4fb88-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="4fb88-105">Arkiv-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fb88-105">Archive cmdlets</span></span>

<span data-ttu-id="4fb88-106">Två nya cmdletar `Compress-Archive` och `Expand-Archive`, kan du komprimera och expandera ZIP-filer.</span><span class="sxs-lookup"><span data-stu-id="4fb88-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="4fb88-107">Mer information finns i den [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) modulen dokumentation.</span><span class="sxs-lookup"><span data-stu-id="4fb88-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="4fb88-108">Katalog-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fb88-108">Catalog Cmdlets</span></span>

<span data-ttu-id="4fb88-109">Två nya cmdletar har lagts till i modulen Microsoft.PowerShell.Security.</span><span class="sxs-lookup"><span data-stu-id="4fb88-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="4fb88-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="4fb88-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="4fb88-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="4fb88-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="4fb88-112">Dessa generera och verifiera filerna för Windows-katalogen.</span><span class="sxs-lookup"><span data-stu-id="4fb88-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="4fb88-113">Urklipps-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fb88-113">Clipboard cmdlets</span></span>

<span data-ttu-id="4fb88-114">`Get-Clipboard` och `Set-Clipboard` gör det enklare att överföra innehåll till och från en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="4fb88-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="4fb88-115">Urklipps-cmdletar har stöd för bilder, ljudfiler, fillistor och text.</span><span class="sxs-lookup"><span data-stu-id="4fb88-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="4fb88-116">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="4fb88-116">For more information, see:</span></span>

- [<span data-ttu-id="4fb88-117">Get-Urklipp</span><span class="sxs-lookup"><span data-stu-id="4fb88-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="4fb88-118">Set-Urklipp</span><span class="sxs-lookup"><span data-stu-id="4fb88-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="4fb88-119">Cryptographic Message Syntax CMS-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fb88-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="4fb88-120">Syntaxen Cryptographic Message Syntax-cmdletarna har stöd för kryptering och dekryptering av innehåll med hjälp av IETF standardformat för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="4fb88-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="4fb88-121">Standard CMS krypteringen implementerar kryptering med offentlig nyckel, där nyckeln används för att kryptera innehållet (den *offentlig nyckel*) och den nyckel som används för att dekryptera innehåll (den *privata nyckeln*) är separata.</span><span class="sxs-lookup"><span data-stu-id="4fb88-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="4fb88-122">Din offentliga nyckel kan delas brett och är inte känsliga data.</span><span class="sxs-lookup"><span data-stu-id="4fb88-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="4fb88-123">Allt innehåll som krypterats med den offentliga nyckeln kan endast dekrypteras med den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="4fb88-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="4fb88-124">Mer information finns i [kryptografi med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="4fb88-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="4fb88-125">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="4fb88-125">For more information see:</span></span>

- [<span data-ttu-id="4fb88-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="4fb88-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="4fb88-127">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="4fb88-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="4fb88-128">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="4fb88-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="4fb88-129">Certifikat krävs en identifierare för unika nyckelanvändning (EKU), som ”kodsignering” eller ”krypterad Mail', för att identifiera dem som certifikat för kryptering av data i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4fb88-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="4fb88-130">Om du vill visa dokumentet krypteringscertifikat i certifikatleverantör, du kan använda den **DocumentEncryptionCert** dynamisk parameter för `Get-ChildItem`:</span><span class="sxs-lookup"><span data-stu-id="4fb88-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="4fb88-131">Extrahera och parsa strukturerade objekt från sträng innehåll</span><span class="sxs-lookup"><span data-stu-id="4fb88-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="4fb88-132">ConvertFrom-sträng</span><span class="sxs-lookup"><span data-stu-id="4fb88-132">ConvertFrom-String</span></span>

<span data-ttu-id="4fb88-133">Den nya `ConvertFrom-String` cmdleten stöder två lägen:</span><span class="sxs-lookup"><span data-stu-id="4fb88-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="4fb88-134">Basic avgränsade parsning</span><span class="sxs-lookup"><span data-stu-id="4fb88-134">Basic delimited parsing</span></span>
- <span data-ttu-id="4fb88-135">Autogenererad dold exempel-drivna parsning</span><span class="sxs-lookup"><span data-stu-id="4fb88-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="4fb88-136">Avgränsad parsning, som standard delar upp inmatningen vid blanksteg och tilldelar egenskapsnamn till grupperna.</span><span class="sxs-lookup"><span data-stu-id="4fb88-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="4fb88-137">Den **UpdateTemplate** parametern sparar resultatet av Inlärningsalgoritmen till en kommentar i mallfilen.</span><span class="sxs-lookup"><span data-stu-id="4fb88-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="4fb88-138">Detta gör learning bearbeta (långsammaste scenen) en engångskostnad.</span><span class="sxs-lookup"><span data-stu-id="4fb88-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="4fb88-139">Kör `ConvertFrom-String` med en mall som innehåller kodade Inlärningsalgoritmen är nu nästan omedelbart.</span><span class="sxs-lookup"><span data-stu-id="4fb88-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="4fb88-140">Mer information finns i [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="4fb88-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="4fb88-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="4fb88-141">Convert-String</span></span>

<span data-ttu-id="4fb88-142">`Convert-String` kan du tillhandahålla före och efter exempel på hur du vill att texten ska se ut.</span><span class="sxs-lookup"><span data-stu-id="4fb88-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="4fb88-143">Cmdlet: en format texten automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4fb88-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="4fb88-144">Mer information finns i [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="4fb88-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="4fb88-145">Uppdateringar till FileInfo-objektet</span><span class="sxs-lookup"><span data-stu-id="4fb88-145">Updates to FileInfo object</span></span>

<span data-ttu-id="4fb88-146">Kan vilseledande filversionsinformation speciellt i fall där filen var korrigeras.</span><span class="sxs-lookup"><span data-stu-id="4fb88-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="4fb88-147">WMF 5.0 lägger till nya **FileVersionRaw** och **ProductVersionRaw** skript egenskaper så att **FileInfo** objekt.</span><span class="sxs-lookup"><span data-stu-id="4fb88-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="4fb88-148">Här är egenskaperna som visas för powershell.exe (förutsatt att $pid är ID för PowerShell-process):</span><span class="sxs-lookup"><span data-stu-id="4fb88-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="4fb88-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="4fb88-149">Format-Hex</span></span>

<span data-ttu-id="4fb88-150">`Format-Hex` kan du visa text eller binära data i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="4fb88-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="4fb88-151">Mer information finns i [hexadecimalt Format](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="4fb88-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="4fb88-152">Get-ChildItem har parametern - Depth</span><span class="sxs-lookup"><span data-stu-id="4fb88-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="4fb88-153">`Get-ChildItem` har nu en **djup** parametern för användning med **Recurse** att begränsa rekursion:</span><span class="sxs-lookup"><span data-stu-id="4fb88-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="4fb88-154">Modulstöd för att deklarera versionsintervall (1.\*, osv)</span><span class="sxs-lookup"><span data-stu-id="4fb88-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="4fb88-155">Nu kan du kombinera **MinimumVersion** och **MaximumVersion** importera modul inom specifika intervall.</span><span class="sxs-lookup"><span data-stu-id="4fb88-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="4fb88-156">Parametrarna har också stöd för jokertecken.</span><span class="sxs-lookup"><span data-stu-id="4fb88-156">The parameters also support wildcards.</span></span>

```powershell
Import-Module psreadline -Verbose -MinimumVersion 1.0 -MaximumVersion 1.2.*
```

```Output
VERBOSE: Loading module from path 'C:\Program Files\WindowsPowerShell\Modules\psreadline\1.1\psreadline.psd1'.
VERBOSE: Importing cmdlet 'Get-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Get-PSReadlineOption'.
VERBOSE: Importing cmdlet 'Remove-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineKeyHandler'.
VERBOSE: Importing cmdlet 'Set-PSReadlineOption'.
VERBOSE: Importing function 'PSConsoleHostReadline'.
```

## <a name="new-guid"></a><span data-ttu-id="4fb88-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="4fb88-157">New-Guid</span></span>

<span data-ttu-id="4fb88-158">Det finns många scenarier där youneed för unik identifierare.</span><span class="sxs-lookup"><span data-stu-id="4fb88-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="4fb88-159">Den `New-GUID` cmdlet ger ett enkelt sätt att skapa en ny GUID.</span><span class="sxs-lookup"><span data-stu-id="4fb88-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="4fb88-160">NoNewLine-parametern</span><span class="sxs-lookup"><span data-stu-id="4fb88-160">NoNewLine parameter</span></span>

<span data-ttu-id="4fb88-161">`Out-File`, `Add-Content`, och `Set-Content` har nu en ny **NoNewline** växeln som utesluter en ny rad efter utdatan.</span><span class="sxs-lookup"><span data-stu-id="4fb88-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="4fb88-162">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fb88-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="4fb88-163">Utan **NoNewline** anges varje fragment är på en separat rad:</span><span class="sxs-lookup"><span data-stu-id="4fb88-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt
"a single " | Add-Content -Path Example.txt
"sentence." | Add-Content -Path Example.txt
Get-Content .\Example.txt
```

```Output
This is
a single
sentence.
```

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="4fb88-164">Interagera med symboliska länkar med förbättrad artikel-cmdletar</span><span class="sxs-lookup"><span data-stu-id="4fb88-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="4fb88-165">Objekt-cmdlet och några relaterade cmdlets har utökats för att stödja symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="4fb88-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="4fb88-166">Symbolisk länk filer</span><span class="sxs-lookup"><span data-stu-id="4fb88-166">Symbolic link files</span></span>

<span data-ttu-id="4fb88-167">I det här exemplet skapar vi en ny symbolisk länk-fil med namnet MySymLinkFile.txt i C:\Temp som länkar till $pshome\profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="4fb88-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="4fb88-168">Alla tre exempel ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="4fb88-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="4fb88-169">Symbolisk länk kataloger</span><span class="sxs-lookup"><span data-stu-id="4fb88-169">Symbolic link directories</span></span>

<span data-ttu-id="4fb88-170">I det här exemplet skapar vi en ny symbolisk länk-katalog med namnet MySymLinkDir i C:\Temp som länkar till mappen $pshome.</span><span class="sxs-lookup"><span data-stu-id="4fb88-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="4fb88-171">Alla tre exempel ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="4fb88-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="4fb88-172">Hårda länkar</span><span class="sxs-lookup"><span data-stu-id="4fb88-172">Hard links</span></span>

<span data-ttu-id="4fb88-173">Samma kombinationer av **sökväg** och **namn** tillåts enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="4fb88-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="4fb88-174">Directory vägkorsningar</span><span class="sxs-lookup"><span data-stu-id="4fb88-174">Directory junctions</span></span>

<span data-ttu-id="4fb88-175">Samma kombinationer av **sökväg** och **namn** tillåts enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="4fb88-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="4fb88-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4fb88-176">Get-ChildItem</span></span>

<span data-ttu-id="4fb88-177">`Get-ChildItem` Nu visar en l i den **läge** egenskap som anger en symbolisk länkfil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="4fb88-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

```powershell
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode       LastWriteTime Length Name
----       ------------- ------ ----
-a---- 6/13/2014 3:00 PM     16 File.txt
d----- 6/13/2014 3:00 PM        Directory
-a---l 6/13/2014 3:21 PM      0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM        MySymLinkDir
-a---l 6/13/2014 3:23 PM  23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM        MyJunctionDir
```

### <a name="remove-item"></a><span data-ttu-id="4fb88-178">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="4fb88-178">Remove-Item</span></span>

<span data-ttu-id="4fb88-179">Ta bort symboliska länkar fungerar som att ta bort någon annan objekttyp av.</span><span class="sxs-lookup"><span data-stu-id="4fb88-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="4fb88-180">Använd den **kraft** parametern för att ta bort filer i målkatalogen och den symboliska länken.</span><span class="sxs-lookup"><span data-stu-id="4fb88-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="4fb88-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="4fb88-181">New-TemporaryFile</span></span>

<span data-ttu-id="4fb88-182">Ibland måste du skapa en temporär fil i ett skript.</span><span class="sxs-lookup"><span data-stu-id="4fb88-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="4fb88-183">Du kan nu göra detta med den `New-TemporaryFile` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="4fb88-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="4fb88-184">Hantering av nätverksväxling med PowerShell</span><span class="sxs-lookup"><span data-stu-id="4fb88-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="4fb88-185">Nätverksswitch-cmdlets med WMF 5.0, kan du använda växeln, virtuellt LAN (VLAN) och grundläggande nivå 2-portkonfiguration av nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar.</span><span class="sxs-lookup"><span data-stu-id="4fb88-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="4fb88-186">Med dessa cmdletar kan du utföra:</span><span class="sxs-lookup"><span data-stu-id="4fb88-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="4fb88-187">Global växla konfiguration, till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fb88-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="4fb88-188">Set-värdnamn</span><span class="sxs-lookup"><span data-stu-id="4fb88-188">Set host name</span></span>
  - <span data-ttu-id="4fb88-189">Ange växeln banderoll</span><span class="sxs-lookup"><span data-stu-id="4fb88-189">Set switch banner</span></span>
  - <span data-ttu-id="4fb88-190">Spara konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4fb88-190">Persist configuration</span></span>
  - <span data-ttu-id="4fb88-191">Aktivera eller inaktivera funktionen</span><span class="sxs-lookup"><span data-stu-id="4fb88-191">Enable or disable feature</span></span>

- <span data-ttu-id="4fb88-192">VLAN-konfiguration:</span><span class="sxs-lookup"><span data-stu-id="4fb88-192">VLAN configuration:</span></span>
  - <span data-ttu-id="4fb88-193">Skapa eller ta bort VLAN</span><span class="sxs-lookup"><span data-stu-id="4fb88-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="4fb88-194">Aktivera eller inaktivera VLAN</span><span class="sxs-lookup"><span data-stu-id="4fb88-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="4fb88-195">Räkna upp VLAN</span><span class="sxs-lookup"><span data-stu-id="4fb88-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="4fb88-196">Ange eget namn som ett VLAN</span><span class="sxs-lookup"><span data-stu-id="4fb88-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="4fb88-197">Portkonfiguration för Layer 2:</span><span class="sxs-lookup"><span data-stu-id="4fb88-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="4fb88-198">Räkna upp portar</span><span class="sxs-lookup"><span data-stu-id="4fb88-198">Enumerate ports</span></span>
  - <span data-ttu-id="4fb88-199">Aktivera eller inaktivera portar</span><span class="sxs-lookup"><span data-stu-id="4fb88-199">Enable or disable ports</span></span>
  - <span data-ttu-id="4fb88-200">Ange port lägen och egenskaper</span><span class="sxs-lookup"><span data-stu-id="4fb88-200">Set port modes and properties</span></span>
  - <span data-ttu-id="4fb88-201">Lägga till eller associera VLAN till segment eller åtkomst på port</span><span class="sxs-lookup"><span data-stu-id="4fb88-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="4fb88-202">Mer information finns i den [NetworkSwitchManager](/powershell/module/networkswitchmanager/) dokumentation.</span><span class="sxs-lookup"><span data-stu-id="4fb88-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="4fb88-203">Skapa PowerShell-cmdletar baserade på en OData-slutpunkt med ODataUtils</span><span class="sxs-lookup"><span data-stu-id="4fb88-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="4fb88-204">Modulen ODataUtils kan generation av PowerShell-cmdletar från REST-slutpunkter som har stöd för OData.</span><span class="sxs-lookup"><span data-stu-id="4fb88-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="4fb88-205">Modulen Microsoft.PowerShell.ODataUtils innehåller följande funktioner:</span><span class="sxs-lookup"><span data-stu-id="4fb88-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="4fb88-206">Kanal för ytterligare information från serversidan slutpunkten till klienten.</span><span class="sxs-lookup"><span data-stu-id="4fb88-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="4fb88-207">Stöd för klientsidan växling</span><span class="sxs-lookup"><span data-stu-id="4fb88-207">Client-side paging support</span></span>
- <span data-ttu-id="4fb88-208">Serversidan filtrering med hjälp av väljer parametern -</span><span class="sxs-lookup"><span data-stu-id="4fb88-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="4fb88-209">Stöd för web-begärandehuvuden</span><span class="sxs-lookup"><span data-stu-id="4fb88-209">Support for web request headers</span></span>

<span data-ttu-id="4fb88-210">Proxy-cmdletar som genererats av den `Export-ODataEndPointProxy` cmdleten ger ytterligare information från serversidan OData-slutpunkten på den **Information** stream.</span><span class="sxs-lookup"><span data-stu-id="4fb88-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="4fb88-211">I följande exempel vi hämtar topprodukt och samla in utdata i den `$infoStream` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4fb88-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="4fb88-212">Genom att ange **IncludeTotalResponseCount** parameter, vi får det totala antalet av alla de **produkten** poster som är tillgängliga på servern.</span><span class="sxs-lookup"><span data-stu-id="4fb88-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="4fb88-213">Du kan hämta poster från servern i batchar med stöd för klientsidan sidindelning.</span><span class="sxs-lookup"><span data-stu-id="4fb88-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="4fb88-214">Detta är användbart när du måste hämta en stor mängd data från servern via nätverket.</span><span class="sxs-lookup"><span data-stu-id="4fb88-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="4fb88-215">Genererade proxy-cmdletarna har stöd för den **Välj** parameter som används som ett filter för att ta emot endast postegenskaperna som klienten behöver.</span><span class="sxs-lookup"><span data-stu-id="4fb88-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="4fb88-216">Den filtrering utförs på servern, vilket minskar mängden data som överförs över nätverket.</span><span class="sxs-lookup"><span data-stu-id="4fb88-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="4fb88-217">Den `Export-ODataEndpointProxy` cmdlet och proxy-cmdletar som genereras av det, stöder nu den **rubriker** parametern.</span><span class="sxs-lookup"><span data-stu-id="4fb88-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="4fb88-218">Rubriken kan användas på channel ytterligare information som förväntas av OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="4fb88-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="4fb88-219">I följande exempel visas en hash-tabell som innehåller en prenumerationsnyckel som har angetts för den **rubriker** parametern.</span><span class="sxs-lookup"><span data-stu-id="4fb88-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="4fb88-220">Det här är ett typexempel för tjänster som väntar en prenumerationsnyckel för autentisering.</span><span class="sxs-lookup"><span data-stu-id="4fb88-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
