---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CmsMessage
ms.openlocfilehash: b90059cd735e26eceb66d211533abbe25894d0ec
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93261987"
---
# <span data-ttu-id="c6814-103">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c6814-103">Get-CmsMessage</span></span>

## <span data-ttu-id="c6814-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c6814-104">SYNOPSIS</span></span>
<span data-ttu-id="c6814-105">Hämtar innehåll som har krypterats med hjälp av formatet kryptografiskt meddelande-syntax.</span><span class="sxs-lookup"><span data-stu-id="c6814-105">Gets content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="c6814-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c6814-106">SYNTAX</span></span>

### <span data-ttu-id="c6814-107">ByContent</span><span class="sxs-lookup"><span data-stu-id="c6814-107">ByContent</span></span>

```
Get-CmsMessage [-Content] <String> [<CommonParameters>]
```

### <span data-ttu-id="c6814-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="c6814-108">ByPath</span></span>

```
Get-CmsMessage [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="c6814-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="c6814-109">ByLiteralPath</span></span>

```
Get-CmsMessage [-LiteralPath] <String> [<CommonParameters>]
```

## <span data-ttu-id="c6814-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c6814-110">DESCRIPTION</span></span>

<span data-ttu-id="c6814-111">`Get-CmsMessage`Cmdleten hämtar innehåll som har krypterats med formatet CMS (Encryption Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="c6814-111">The `Get-CmsMessage` cmdlet gets content that has been encrypted using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="c6814-112">CMS-cmdletarna stöder kryptering och dekryptering av innehåll med hjälp av IETF-formatet för kryptografiskt skydd av meddelanden, enligt vad som dokumenterats av [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="c6814-112">The CMS cmdlets support encryption and decryption of content using the IETF format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="c6814-113">CMS-standarden för standard använder kryptering med offentliga nycklar, där nycklarna som används för att kryptera innehåll (den offentliga nyckeln) och de nycklar som används för att dekryptera innehållet (den privata nyckeln) är separata.</span><span class="sxs-lookup"><span data-stu-id="c6814-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="c6814-114">Din offentliga nyckel kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="c6814-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="c6814-115">Om något innehåll krypteras med den här offentliga nyckeln kan bara den privata nyckeln dekryptera den.</span><span class="sxs-lookup"><span data-stu-id="c6814-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="c6814-116">Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="c6814-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="c6814-117">`Get-CmsMessage` hämtar innehåll som har krypterats i CMS-format.</span><span class="sxs-lookup"><span data-stu-id="c6814-117">`Get-CmsMessage` gets content that has been encrypted in CMS format.</span></span> <span data-ttu-id="c6814-118">Det varken dekrypterar eller tar bort skyddet av innehåll.</span><span class="sxs-lookup"><span data-stu-id="c6814-118">It does not decrypt or unprotect content.</span></span> <span data-ttu-id="c6814-119">Du kan köra denna cmdlet för att hämta innehåll som du har krypterat genom att köra `Protect-CmsMessage` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c6814-119">You can run this cmdlet to get content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="c6814-120">Du kan ange innehåll som du vill dekryptera som en sträng eller med sökvägen till det krypterade innehållet.</span><span class="sxs-lookup"><span data-stu-id="c6814-120">You can specify content that you want to decrypt as a string, or by path to the encrypted content.</span></span> <span data-ttu-id="c6814-121">Du kan skicka vidare resultatet av `Get-CmsMessage` till för `Unprotect-CmsMessage` att dekryptera innehållet, förutsatt att du har information om det dokument krypterings certifikat som användes för att kryptera innehållet.</span><span class="sxs-lookup"><span data-stu-id="c6814-121">You can pipe the results of `Get-CmsMessage` to `Unprotect-CmsMessage` to decrypt the content, provided that you have information about the document encryption certificate that was used to encrypt the content.</span></span>

> [!NOTE]
> <span data-ttu-id="c6814-122">Den här cmdleten är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="c6814-122">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="c6814-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c6814-123">EXAMPLES</span></span>

### <span data-ttu-id="c6814-124">Exempel 1: Hämta krypterat innehåll</span><span class="sxs-lookup"><span data-stu-id="c6814-124">Example 1: Get encrypted content</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg.Content
```

```Output
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMBFWxlZWhv
bG1AbGljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYP5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNXmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPRwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84AHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1AtDj7nSJc=
-----END CMS-----
```

<span data-ttu-id="c6814-125">Det här kommandot hämtar krypterat innehåll som finns på C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span><span class="sxs-lookup"><span data-stu-id="c6814-125">This command gets encrypted content located at C:\Users\Test\Documents\PowerShell\Future_Plans.txt.</span></span>

### <span data-ttu-id="c6814-126">Exempel 2: pipe-krypterat innehåll till Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c6814-126">Example 2: Pipe encrypted content to Unprotect-CmsMessage</span></span>

```powershell
$Msg = Get-CmsMessage -Path "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
$Msg | Unprotect-CmsMessage -To "cn=youralias@emailaddress.com"
```

```Output
Try the new Break All command
```

<span data-ttu-id="c6814-127">Det här kommandot rör resultatet av `Get-CmsMessage` cmdleten från exempel 1 till `Unprotect-CmsMessage` , för att dekryptera meddelandet och läsa det i oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="c6814-127">This command pipes the results of the `Get-CmsMessage` cmdlet from Example 1 to `Unprotect-CmsMessage`, to decrypt the message and read it in plain text.</span></span> <span data-ttu-id="c6814-128">I det här fallet är värdet för parametern **till** värdet för certifikatets ämnes rad för kryptering.</span><span class="sxs-lookup"><span data-stu-id="c6814-128">In this case, the value of the **To** parameter is the value of the encrypting certificate's Subject line.</span></span> <span data-ttu-id="c6814-129">Det dekrypterade meddelandet "testa kommandot ny Break alla" är resultatet.</span><span class="sxs-lookup"><span data-stu-id="c6814-129">The decrypted message, "Try the new Break All command," is the result.</span></span>

## <span data-ttu-id="c6814-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c6814-130">PARAMETERS</span></span>

### <span data-ttu-id="c6814-131">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="c6814-131">-Content</span></span>

<span data-ttu-id="c6814-132">Anger en krypterad sträng eller en variabel som innehåller en krypterad sträng.</span><span class="sxs-lookup"><span data-stu-id="c6814-132">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c6814-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c6814-133">-LiteralPath</span></span>

<span data-ttu-id="c6814-134">Anger sökvägen till krypterat innehåll som du vill hämta.</span><span class="sxs-lookup"><span data-stu-id="c6814-134">Specifies the path to encrypted content that you want to get.</span></span> <span data-ttu-id="c6814-135">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c6814-135">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="c6814-136">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c6814-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="c6814-137">Om sökvägen innehåller escape-tecken, omger du var och en med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c6814-137">If the path includes escape characters, enclose each one in single quotation marks.</span></span>
<span data-ttu-id="c6814-138">Enkla citat tecken instruerar PowerShell att inte tolka omslutna tecken som escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="c6814-138">Single quotation marks tell PowerShell not to interpret enclosed characters as escape characters.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6814-139">-Path</span><span class="sxs-lookup"><span data-stu-id="c6814-139">-Path</span></span>

<span data-ttu-id="c6814-140">Anger sökvägen till krypterat innehåll som du vill dekryptera.</span><span class="sxs-lookup"><span data-stu-id="c6814-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6814-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6814-141">CommonParameters</span></span>

<span data-ttu-id="c6814-142">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c6814-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6814-143">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c6814-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6814-144">INDATA</span><span class="sxs-lookup"><span data-stu-id="c6814-144">INPUTS</span></span>

## <span data-ttu-id="c6814-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c6814-145">OUTPUTS</span></span>

## <span data-ttu-id="c6814-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c6814-146">NOTES</span></span>

## <span data-ttu-id="c6814-147">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c6814-147">RELATED LINKS</span></span>

[<span data-ttu-id="c6814-148">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c6814-148">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="c6814-149">Skydda – CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c6814-149">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)

[<span data-ttu-id="c6814-150">Ta bort skydd-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="c6814-150">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
