---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Nya och uppdaterade cmdletar
ms.openlocfilehash: ffd5db2d4fc9bf8f67ef5e352633ad3209f72c87
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145028"
---
# <a name="new-and-updated-cmdlets"></a><span data-ttu-id="b7eb3-103">Nya och uppdaterade cmdletar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-103">New and updated cmdlets</span></span>

<span data-ttu-id="b7eb3-104">Vi har lagt till nya och uppdaterade befintliga cmdlets baserade på feedback från communityn.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-104">We have added new and updated existing cmdlets based on feedback from the community.</span></span>

## <a name="archive-cmdlets"></a><span data-ttu-id="b7eb3-105">Arkiv-cmdletar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-105">Archive cmdlets</span></span>

<span data-ttu-id="b7eb3-106">Två nya cmdletar, `Compress-Archive` och `Expand-Archive`låter dig komprimera och expandera zip-filer.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-106">Two new cmdlets, `Compress-Archive` and `Expand-Archive`, let you compress and expand ZIP files.</span></span>

<span data-ttu-id="b7eb3-107">Mer information finns i dokumentationen för modulen [Microsoft. PowerShell. Archive](/powershell/module/microsoft.powershell.archive/) .</span><span class="sxs-lookup"><span data-stu-id="b7eb3-107">For more information, see the [Microsoft.Powershell.Archive](/powershell/module/microsoft.powershell.archive/) module documentation.</span></span>

## <a name="catalog-cmdlets"></a><span data-ttu-id="b7eb3-108">Katalog-cmdletar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-108">Catalog Cmdlets</span></span>

<span data-ttu-id="b7eb3-109">Två nya cmdletar har lagts till i modulen Microsoft. PowerShell. Security.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-109">Two new cmdlets have been added in the Microsoft.PowerShell.Security module.</span></span>

- [<span data-ttu-id="b7eb3-110">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b7eb3-110">New-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/New-FileCatalog)
- [<span data-ttu-id="b7eb3-111">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="b7eb3-111">Test-FileCatalog</span></span>](/powershell/module/microsoft.powershell.security/Test-FileCatalog)

<span data-ttu-id="b7eb3-112">Dessa genererar och validerar Windows Catalog-filer.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-112">These generate and validate Windows catalog files.</span></span>

## <a name="clipboard-cmdlets"></a><span data-ttu-id="b7eb3-113">Urklipps-cmdletar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-113">Clipboard cmdlets</span></span>

<span data-ttu-id="b7eb3-114">`Get-Clipboard`och `Set-Clipboard` gör det enklare för dig att överföra innehåll till och från en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-114">`Get-Clipboard` and `Set-Clipboard` make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="b7eb3-115">Urklipps-cmdletarna stöder bilder, ljudfiler, fil listor och text.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-115">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

<span data-ttu-id="b7eb3-116">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-116">For more information, see:</span></span>

- [<span data-ttu-id="b7eb3-117">Hämta Urklipp</span><span class="sxs-lookup"><span data-stu-id="b7eb3-117">Get-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Clipboard)
- [<span data-ttu-id="b7eb3-118">Ange Urklipp</span><span class="sxs-lookup"><span data-stu-id="b7eb3-118">Set-Clipboard</span></span>](/powershell/module/Microsoft.PowerShell.Management/Set-Clipboard)

## <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="b7eb3-119">Cmdletar för kryptografiskt meddelande syntax (CMS)</span><span class="sxs-lookup"><span data-stu-id="b7eb3-119">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="b7eb3-120">Cmdletarna för kryptografisk meddelandesyntax stöder kryptering och dekryptering av innehåll med hjälp av IETFs standardformat för kryptografiskt skydd av meddelanden som dokumenteras av [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="b7eb3-120">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="b7eb3-121">Standardvärdet för CMS-kryptering implementerar kryptering med offentliga nycklar, där nyckeln som används för att kryptera innehåll (den *offentliga nyckeln*) och den nyckel som används för att dekryptera innehållet (den *privata nyckeln*) är separata.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-121">The CMS encryption standard implements public key cryptography, where the key used to encrypt content (the *public key*) and the key used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="b7eb3-122">Din offentliga nyckel kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-122">Your public key can be shared widely and is not sensitive data.</span></span> <span data-ttu-id="b7eb3-123">Alla innehåll som krypteras med den offentliga nyckeln kan bara dekrypteras med den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-123">Any content encrypted with the public key can only be decrypted using the private key.</span></span> <span data-ttu-id="b7eb3-124">Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="b7eb3-124">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="b7eb3-125">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-125">For more information see:</span></span>

- [<span data-ttu-id="b7eb3-126">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b7eb3-126">Get-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Get-CmsMessage)
- [<span data-ttu-id="b7eb3-127">Skydda – CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b7eb3-127">Protect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)
- [<span data-ttu-id="b7eb3-128">Ta bort skydd-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="b7eb3-128">Unprotect-CmsMessage</span></span>](/powershell/module/Microsoft.PowerShell.Security/unprotect-CmsMessage)

<span data-ttu-id="b7eb3-129">Certifikat kräver en unik nyckel användnings identifierare (EKU), t. ex. kod signering eller krypterad e-post, för att identifiera dem som data krypterings certifikat i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-129">Certificates require a unique key usage identifier (EKU), such as 'Code Signing' or 'Encrypted Mail', to identify them as data encryption certificates in PowerShell.</span></span> <span data-ttu-id="b7eb3-130">Om du vill visa dokument krypterings certifikat i certifikat leverantören kan du använda den dynamiska **DocumentEncryptionCert** - `Get-ChildItem`parametern för:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-130">To view document encryption certificates in the certificate provider, you can use the **DocumentEncryptionCert** dynamic parameter of `Get-ChildItem`:</span></span>

```powershell
Get-ChildItem Cert:\CurrentUser -DocumentEncryptionCert -Recurse
```

## <a name="extract-and-parse-structured-objects-from-string-content"></a><span data-ttu-id="b7eb3-131">Extrahera och parsa strukturerade objekt från sträng innehåll</span><span class="sxs-lookup"><span data-stu-id="b7eb3-131">Extract and parse structured objects from string content</span></span>

### <a name="convertfrom-string"></a><span data-ttu-id="b7eb3-132">ConvertFrom-sträng</span><span class="sxs-lookup"><span data-stu-id="b7eb3-132">ConvertFrom-String</span></span>

<span data-ttu-id="b7eb3-133">Den nya `ConvertFrom-String` cmdleten stöder två lägen:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-133">The new `ConvertFrom-String` cmdlet supports two modes:</span></span>

- <span data-ttu-id="b7eb3-134">Grundläggande avgränsad parsning</span><span class="sxs-lookup"><span data-stu-id="b7eb3-134">Basic delimited parsing</span></span>
- <span data-ttu-id="b7eb3-135">Automatiskt genererad exempel-driven parsning</span><span class="sxs-lookup"><span data-stu-id="b7eb3-135">Auto generated example-driven parsing</span></span>

<span data-ttu-id="b7eb3-136">Delimited parsing, som standard, delar in indatamängden med blank steg och tilldelar de resulterande grupperna egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-136">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="b7eb3-137">Parametern **UpdateTemplate** sparar resultatet av inlärningen i en kommentar i mallfilen.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-137">The **UpdateTemplate** parameter saves the results of the learning algorithm into a comment in the template file.</span></span> <span data-ttu-id="b7eb3-138">Detta gör inlärnings processen (den långsammaste fasen) till en engångs kostnad.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-138">This makes the learning process (the slowest stage) a one-time cost.</span></span> <span data-ttu-id="b7eb3-139">Att `ConvertFrom-String` köra med en mall som innehåller den kodade inlärnings algoritmen är nu nästan momentant.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-139">Running `ConvertFrom-String` with a template that contains the encoded learning algorithm is now nearly instantaneous.</span></span>

<span data-ttu-id="b7eb3-140">Mer information finns i [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span><span class="sxs-lookup"><span data-stu-id="b7eb3-140">For more information, see [ConvertFrom-String](/powershell/module/Microsoft.PowerShell.Utility/ConvertFrom-String).</span></span>

### <a name="convert-string"></a><span data-ttu-id="b7eb3-141">Convert-String</span><span class="sxs-lookup"><span data-stu-id="b7eb3-141">Convert-String</span></span>

<span data-ttu-id="b7eb3-142">`Convert-String`gör att du kan ange före och efter exempel på hur du vill att texten ska se ut.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-142">`Convert-String` allows you to provide before and after examples of how you want text to look.</span></span> <span data-ttu-id="b7eb3-143">-Cmdleten formaterar texten automatiskt.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-143">The cmdlet formats your text automatically.</span></span>

<span data-ttu-id="b7eb3-144">Mer information finns i [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span><span class="sxs-lookup"><span data-stu-id="b7eb3-144">For more information, see [Convert-String](/powershell/module/Microsoft.PowerShell.Utility/Convert-String).</span></span>

## <a name="updates-to-fileinfo-object"></a><span data-ttu-id="b7eb3-145">Uppdateringar till FileInfo-objektet</span><span class="sxs-lookup"><span data-stu-id="b7eb3-145">Updates to FileInfo object</span></span>

<span data-ttu-id="b7eb3-146">Fil versions information kan vara missvisande, särskilt i de fall där filen har korrigerats.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-146">File version information can be misleading, especially in cases where the file was patched.</span></span> <span data-ttu-id="b7eb3-147">WMF 5,0 lägger till nya **FileVersionRaw** -och **ProductVersionRaw** -skript egenskaper till **fileinfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-147">WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to **FileInfo** objects.</span></span>
<span data-ttu-id="b7eb3-148">Här följer de egenskaper som visas för PowerShell. exe (förutsatt att $pid är PowerShell-processens ID):</span><span class="sxs-lookup"><span data-stu-id="b7eb3-148">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
Get-Process -Id $pid -FileVersionInfo | Format-List *version*
```

```Output
FileVersionRaw    : 10.0.17763.1
ProductVersionRaw : 10.0.17763.1
FileVersion       : 10.0.17763.1 (WinBuild.160101.0800)
ProductVersion    : 10.0.17763.1
```

## <a name="format-hex"></a><span data-ttu-id="b7eb3-149">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="b7eb3-149">Format-Hex</span></span>

<span data-ttu-id="b7eb3-150">`Format-Hex`gör att du kan visa text eller binära data i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-150">`Format-Hex` lets you view text or binary data in hexadecimal format.</span></span>

<span data-ttu-id="b7eb3-151">Mer information finns i [format-hex](/powershell/module/microsoft.powershell.utility/format-hex).</span><span class="sxs-lookup"><span data-stu-id="b7eb3-151">For more information, see [Format-Hex](/powershell/module/microsoft.powershell.utility/format-hex).</span></span>

## <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="b7eb3-152">Get-ChildItem har-djupgående-parameter</span><span class="sxs-lookup"><span data-stu-id="b7eb3-152">Get-ChildItem has -Depth parameter</span></span>

<span data-ttu-id="b7eb3-153">`Get-ChildItem`har nu en **djup** parameter som används med **rekursivt** för att begränsa den rekursion:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-153">`Get-ChildItem` now has a **Depth** parameter for use with **Recurse** to limit the recursion:</span></span>

## <a name="modules-support-for-declaring-version-ranges-1-etc"></a><span data-ttu-id="b7eb3-154">Moduler har stöd för att deklarera versions intervall (1. \* osv.)</span><span class="sxs-lookup"><span data-stu-id="b7eb3-154">Modules support for declaring version ranges (1.\*, etc)</span></span>

<span data-ttu-id="b7eb3-155">Nu kan du kombinera **MinimumVersion** och **MaximumVersion** för att importera modulen inom ett angivet intervall.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-155">You can now combine **MinimumVersion** and **MaximumVersion** to import module within specific range.</span></span> <span data-ttu-id="b7eb3-156">Parametrarna stöder också jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-156">The parameters also support wildcards.</span></span>

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

## <a name="new-guid"></a><span data-ttu-id="b7eb3-157">New-Guid</span><span class="sxs-lookup"><span data-stu-id="b7eb3-157">New-Guid</span></span>

<span data-ttu-id="b7eb3-158">Det finns många scenarier där Youneed för unik identifierare.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-158">There are many scenarios where youneed for unique identifier.</span></span> <span data-ttu-id="b7eb3-159">`New-GUID` Cmdleten är ett enkelt sätt att skapa ett nytt GUID.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-159">The `New-GUID` cmdlet provides a simple way to create a new GUID.</span></span>

```powershell
New-Guid
```

```Output
Guid
----
e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
```

## <a name="nonewline-parameter"></a><span data-ttu-id="b7eb3-160">NoNewLine-parameter</span><span class="sxs-lookup"><span data-stu-id="b7eb3-160">NoNewLine parameter</span></span>

<span data-ttu-id="b7eb3-161">`Out-File`, `Add-Content`och `Set-Content` har nu en ny **NoNewline** -växel som utelämnar en ny rad efter utdata.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-161">`Out-File`, `Add-Content`, and `Set-Content` now have a new **NoNewline** switch which omits a new line after the output.</span></span> <span data-ttu-id="b7eb3-162">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-162">For example:</span></span>

```powershell
"This is " | Out-File -FilePath Example.txt -NoNewline
"a single " | Add-Content -Path Example.txt -NoNewline
"sentence." | Add-Content -Path Example.txt -NoNewline
Get-Content .\Example.txt
```

```Output
This is a single sentence.
```

<span data-ttu-id="b7eb3-163">Om inget **NoNewline** anges så finns varje fragment på en separat rad:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-163">Without **NoNewline** specified, each fragment would be on a separate line:</span></span>

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

## <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="b7eb3-164">Interagera med symboliska länkar med förbättrade objekt-cmdletar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-164">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="b7eb3-165">Objekt-cmdleten och några relaterade cmdlets har utökats för att stödja symboliska länkar.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-165">The Item cmdlet and a few related cmdlets have been extended to support symbolic links.</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="b7eb3-166">Symboliska länkade filer</span><span class="sxs-lookup"><span data-stu-id="b7eb3-166">Symbolic link files</span></span>

<span data-ttu-id="b7eb3-167">I det här exemplet skapar vi en ny symbolisk länk fil med namnet MySymLinkFile. txt i C:\Temp som länkar till $pshome \profile.ps1.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-167">In this example, we create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1.</span></span> <span data-ttu-id="b7eb3-168">Alla tre exempel ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-168">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="b7eb3-169">Symboliska länk kataloger</span><span class="sxs-lookup"><span data-stu-id="b7eb3-169">Symbolic link directories</span></span>

<span data-ttu-id="b7eb3-170">I det här exemplet skapar vi en ny symbolisk länk katalog med namnet MySymLinkDir i C:\Temp som länkar till mappen $pshome.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-170">In this example, we create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder.</span></span> <span data-ttu-id="b7eb3-171">Alla tre exempel ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-171">All three examples produce the same result.</span></span>

```powershell
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="b7eb3-172">Hårda länkar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-172">Hard links</span></span>

<span data-ttu-id="b7eb3-173">Samma kombination av **sökväg** och **namn** som tillåts enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-173">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="directory-junctions"></a><span data-ttu-id="b7eb3-174">Katalog Knut punkter</span><span class="sxs-lookup"><span data-stu-id="b7eb3-174">Directory junctions</span></span>

<span data-ttu-id="b7eb3-175">Samma kombination av **sökväg** och **namn** som tillåts enligt beskrivningen ovan.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-175">The same combinations of **Path** and **Name** allowed as described above.</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
```

### <a name="get-childitem"></a><span data-ttu-id="b7eb3-176">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="b7eb3-176">Get-ChildItem</span></span>

<span data-ttu-id="b7eb3-177">`Get-ChildItem`visar nu en "l" i egenskapen **mode** för att ange en symbolisk länk fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-177">`Get-ChildItem` now displays an 'l' in the **Mode** property to indicate a symbolic link file or directory.</span></span>

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

### <a name="remove-item"></a><span data-ttu-id="b7eb3-178">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="b7eb3-178">Remove-Item</span></span>

<span data-ttu-id="b7eb3-179">Borttagning av symboliska länkar fungerar som att ta bort alla andra objekt typer.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-179">Removing symbolic links works like removing any other item type.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkDir
```

<span data-ttu-id="b7eb3-180">Använd parametern **Force** för att ta bort filerna i mål katalogen och den symboliska länken.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-180">Use the **Force** parameter to remove the files in the target directory and the symbolic link.</span></span>

```powershell
Remove-Item C:\Temp\MySymLinkDir -Force
```

## <a name="new-temporaryfile"></a><span data-ttu-id="b7eb3-181">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="b7eb3-181">New-TemporaryFile</span></span>

<span data-ttu-id="b7eb3-182">Ibland måste du skapa en temporär fil i dina skript.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-182">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="b7eb3-183">Nu kan du göra detta med `New-TemporaryFile` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-183">You can now do this with the `New-TemporaryFile` cmdlet:</span></span>

```powershell
$tempFile = New-TemporaryFile
$tempFile.FullName
```

```Output
C:\Users\user1\AppData\Local\Temp\tmp375.tmp
```

## <a name="network-switch-management-with-powershell"></a><span data-ttu-id="b7eb3-184">Hantering av nätverksväxling med PowerShell</span><span class="sxs-lookup"><span data-stu-id="b7eb3-184">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="b7eb3-185">Nätverks växel-cmdletar, som introducerades i WMF 5,0, gör att du kan använda Switch, virtuellt LAN (VLAN) och grundläggande Layer 2 nätverks växel port konfiguration för Windows Server 2012 R2 logo typ-certifierade nätverks växlar.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-185">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="b7eb3-186">Med dessa cmdlet: ar kan du utföra:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-186">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="b7eb3-187">Konfiguration av global växel, till exempel:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-187">Global switch configuration, such as:</span></span>
  - <span data-ttu-id="b7eb3-188">Ange värdnamn</span><span class="sxs-lookup"><span data-stu-id="b7eb3-188">Set host name</span></span>
  - <span data-ttu-id="b7eb3-189">Ange växel banderoll</span><span class="sxs-lookup"><span data-stu-id="b7eb3-189">Set switch banner</span></span>
  - <span data-ttu-id="b7eb3-190">Beständig konfiguration</span><span class="sxs-lookup"><span data-stu-id="b7eb3-190">Persist configuration</span></span>
  - <span data-ttu-id="b7eb3-191">Aktivera eller inaktivera funktion</span><span class="sxs-lookup"><span data-stu-id="b7eb3-191">Enable or disable feature</span></span>

- <span data-ttu-id="b7eb3-192">VLAN-konfiguration:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-192">VLAN configuration:</span></span>
  - <span data-ttu-id="b7eb3-193">Skapa eller ta bort VLAN</span><span class="sxs-lookup"><span data-stu-id="b7eb3-193">Create or remove VLAN</span></span>
  - <span data-ttu-id="b7eb3-194">Aktivera eller inaktivera VLAN</span><span class="sxs-lookup"><span data-stu-id="b7eb3-194">Enable or disable VLAN</span></span>
  - <span data-ttu-id="b7eb3-195">Räkna upp VLAN</span><span class="sxs-lookup"><span data-stu-id="b7eb3-195">Enumerate VLAN</span></span>
  - <span data-ttu-id="b7eb3-196">Ange ett eget namn på ett VLAN</span><span class="sxs-lookup"><span data-stu-id="b7eb3-196">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="b7eb3-197">Nivå 2-port konfiguration:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-197">Layer 2 port configuration:</span></span>
  - <span data-ttu-id="b7eb3-198">Räkna upp portar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-198">Enumerate ports</span></span>
  - <span data-ttu-id="b7eb3-199">Aktivera eller inaktivera portar</span><span class="sxs-lookup"><span data-stu-id="b7eb3-199">Enable or disable ports</span></span>
  - <span data-ttu-id="b7eb3-200">Ange port lägen och egenskaper</span><span class="sxs-lookup"><span data-stu-id="b7eb3-200">Set port modes and properties</span></span>
  - <span data-ttu-id="b7eb3-201">Lägg till eller koppla VLAN till trunk eller åtkomst på porten</span><span class="sxs-lookup"><span data-stu-id="b7eb3-201">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="b7eb3-202">Mer information finns i [NetworkSwitchManager](/powershell/module/networkswitchmanager/) -dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-202">For more information, see the [NetworkSwitchManager](/powershell/module/networkswitchmanager/) documentation.</span></span>

## <a name="generate-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="b7eb3-203">Generera PowerShell-cmdletar baserade på en OData-slutpunkt med ODataUtils</span><span class="sxs-lookup"><span data-stu-id="b7eb3-203">Generate PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="b7eb3-204">Med modulen ODataUtils kan du skapa PowerShell-cmdlets från REST-slutpunkter som stöder OData.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-204">The ODataUtils module allows generation of PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="b7eb3-205">Modulen Microsoft. PowerShell. ODataUtils innehåller följande funktioner:</span><span class="sxs-lookup"><span data-stu-id="b7eb3-205">The Microsoft.PowerShell.ODataUtils module includes the following features:</span></span>

- <span data-ttu-id="b7eb3-206">Kanal ytterligare information från slut punkten på Server sidan till klient sidan.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-206">Channel additional information from server-side endpoint to client side.</span></span>
- <span data-ttu-id="b7eb3-207">Stöd för sid indelning på klient Sidan</span><span class="sxs-lookup"><span data-stu-id="b7eb3-207">Client-side paging support</span></span>
- <span data-ttu-id="b7eb3-208">Filtrering på Server sidan med hjälp av parametern-Select</span><span class="sxs-lookup"><span data-stu-id="b7eb3-208">Server-side filtering by using the -Select parameter</span></span>
- <span data-ttu-id="b7eb3-209">Stöd för webb begär ande rubriker</span><span class="sxs-lookup"><span data-stu-id="b7eb3-209">Support for web request headers</span></span>

<span data-ttu-id="b7eb3-210">Proxy-cmdletarna som genereras av `Export-ODataEndPointProxy` cmdleten ger ytterligare information från OData-slutpunkten på Server sidan i **informations** data strömmen.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-210">The proxy cmdlets generated by the `Export-ODataEndPointProxy` cmdlet provide additional information from the server-side OData endpoint on the **Information** stream.</span></span>

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
```

<span data-ttu-id="b7eb3-211">I följande exempel hämtar vi den översta produkten och fångar in utdata i `$infoStream` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-211">In the following example, we are retrieving top product and capturing the output in the `$infoStream` variable.</span></span>

<span data-ttu-id="b7eb3-212">Genom att ange parametern **IncludeTotalResponseCount** får vi det totala antalet tillgängliga **produkt** poster på servern.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-212">By specifying **IncludeTotalResponseCount** parameter, we get the total count of all the **Product** records available on the server.</span></span>

```powershell
Import-Module $generatedProxyModuleDir -Force
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
$additionalInfo['odata.count']
```

<span data-ttu-id="b7eb3-213">Du kan hämta poster från servern i batchar med stöd för växling vid fel på klient sidan.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-213">You can get the records from the server in batches using client-side paging support.</span></span> <span data-ttu-id="b7eb3-214">Detta är användbart när du måste få en stor mängd data från servern över nätverket.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-214">This is useful when you must get a large amount of data from the server over the network.</span></span>

```powershell
$skipCount = 0
$batchSize = 3
while($skipCount -le $additionalInfo['odata.count'])
{
  Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
  $skipCount += $batchSize
}
```

<span data-ttu-id="b7eb3-215">De genererade proxy-cmdletarna stöder **Select** -parametern som används som ett filter för att endast ta emot de post egenskaper som klienten behöver.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-215">The generated proxy cmdlets support the **Select** parameter that is used as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="b7eb3-216">Filtreringen sker på servern, vilket minskar mängden data som överförs via nätverket.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-216">The filtering occurs on the server, which reduces the amount of data that is transferred over the network.</span></span>

```powershell
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="b7eb3-217">`Export-ODataEndpointProxy` Cmdleten och proxy-cmdletarna som genereras av den, stöder nu parametern **headers** .</span><span class="sxs-lookup"><span data-stu-id="b7eb3-217">The `Export-ODataEndpointProxy` cmdlet, and the proxy cmdlets generated by it, now support the **Headers** parameter.</span></span> <span data-ttu-id="b7eb3-218">Sidhuvudet kan användas för att kanal ytterligare information som förväntas av OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-218">The header can be used to channel additional information expected by the OData endpoint.</span></span>

<span data-ttu-id="b7eb3-219">I följande exempel anges en hash-tabell som innehåller en prenumerations nyckel för parametern **headers** .</span><span class="sxs-lookup"><span data-stu-id="b7eb3-219">In the following example, a hash table containing a Subscription key is provided to the **Headers** parameter.</span></span> <span data-ttu-id="b7eb3-220">Detta är ett typiskt exempel för tjänster som förväntar sig en prenumerations nyckel för autentisering.</span><span class="sxs-lookup"><span data-stu-id="b7eb3-220">This is a typical example for services that are expecting a Subscription key for authentication.</span></span>

```powershell
Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
