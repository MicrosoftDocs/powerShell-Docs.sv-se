---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/unprotect-cmsmessage?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unprotect-CmsMessage
ms.openlocfilehash: 794ff376c11d6956b71b3feb48f058c92a2e7d17
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265214"
---
# <span data-ttu-id="769f6-103">Unprotect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="769f6-103">Unprotect-CmsMessage</span></span>

## <span data-ttu-id="769f6-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="769f6-104">SYNOPSIS</span></span>
<span data-ttu-id="769f6-105">Dekrypterar innehåll som har krypterats med hjälp av formatet kryptografiskt meddelande-syntax.</span><span class="sxs-lookup"><span data-stu-id="769f6-105">Decrypts content that has been encrypted by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="769f6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="769f6-106">SYNTAX</span></span>

### <span data-ttu-id="769f6-107">ByWinEvent (standard)</span><span class="sxs-lookup"><span data-stu-id="769f6-107">ByWinEvent (Default)</span></span>

```
Unprotect-CmsMessage [-EventLogRecord] <PSObject> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="769f6-108">ByContent</span><span class="sxs-lookup"><span data-stu-id="769f6-108">ByContent</span></span>

```
Unprotect-CmsMessage [-Content] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="769f6-109">ByPath</span><span class="sxs-lookup"><span data-stu-id="769f6-109">ByPath</span></span>

```
Unprotect-CmsMessage [-Path] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>] [<CommonParameters>]
```

### <span data-ttu-id="769f6-110">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="769f6-110">ByLiteralPath</span></span>

```
Unprotect-CmsMessage [-LiteralPath] <String> [-IncludeContext] [[-To] <CmsMessageRecipient[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="769f6-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="769f6-111">DESCRIPTION</span></span>

<span data-ttu-id="769f6-112">`Unprotect-CmsMessage`Cmdleten dekrypterar innehåll som har krypterats med formatet CMS (Cryptographic Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="769f6-112">The `Unprotect-CmsMessage` cmdlet decrypts content that has been encrypted by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="769f6-113">CMS-cmdletarna stöder kryptering och dekryptering av innehåll med hjälp av IETF-standardformatet för kryptografiskt skydd av meddelanden, enligt beskrivningen i [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="769f6-113">The CMS cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages, as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

<span data-ttu-id="769f6-114">CMS-standarden för standard använder kryptering med offentliga nycklar, där nycklarna som används för att kryptera innehåll (den offentliga nyckeln) och de nycklar som används för att dekryptera innehållet (den privata nyckeln) är separata.</span><span class="sxs-lookup"><span data-stu-id="769f6-114">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="769f6-115">Din offentliga nyckel kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="769f6-115">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="769f6-116">Om något innehåll krypteras med den här offentliga nyckeln kan bara den privata nyckeln dekryptera den.</span><span class="sxs-lookup"><span data-stu-id="769f6-116">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="769f6-117">Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="769f6-117">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="769f6-118">`Unprotect-CmsMessage` dekrypterar innehåll som har krypterats i CMS-format.</span><span class="sxs-lookup"><span data-stu-id="769f6-118">`Unprotect-CmsMessage` decrypts content that has been encrypted in CMS format.</span></span> <span data-ttu-id="769f6-119">Du kan köra denna cmdlet för att dekryptera innehåll som du har krypterat genom att köra `Protect-CmsMessage` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="769f6-119">You can run this cmdlet to decrypt content that you have encrypted by running the `Protect-CmsMessage` cmdlet.</span></span> <span data-ttu-id="769f6-120">Du kan ange innehåll som du vill dekryptera som en sträng, genom att ange ID-numret för krypterings händelse logg posten eller med sökvägen till det krypterade innehållet.</span><span class="sxs-lookup"><span data-stu-id="769f6-120">You can specify content that you want to decrypt as a string, by the encryption event log record ID number, or by path to the encrypted content.</span></span> <span data-ttu-id="769f6-121">`Unprotect-CmsMessage`Cmdleten returnerar det dekrypterade innehållet.</span><span class="sxs-lookup"><span data-stu-id="769f6-121">The `Unprotect-CmsMessage` cmdlet returns the decrypted content.</span></span>

## <span data-ttu-id="769f6-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="769f6-122">EXAMPLES</span></span>

### <span data-ttu-id="769f6-123">Exempel 1: dekryptera ett meddelande</span><span class="sxs-lookup"><span data-stu-id="769f6-123">Example 1: Decrypt a message</span></span>

<span data-ttu-id="769f6-124">I följande exempel dekrypterar du innehåll som finns på den litterala sökvägen `C:\Users\Test\Documents\PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="769f6-124">In the following example, you decrypt content that is located at the literal path `C:\Users\Test\Documents\PowerShell`.</span></span> <span data-ttu-id="769f6-125">För värdet **för parametern som** krävs, använder det här exemplet tumavtrycket för det certifikat som användes för att utföra krypteringen.</span><span class="sxs-lookup"><span data-stu-id="769f6-125">For the value of the required **To** parameter, this example uses the thumbprint of the certificate that was used to perform the encryption.</span></span> <span data-ttu-id="769f6-126">Det dekrypterade meddelandet "testa kommandot ny Break alla" är resultatet.</span><span class="sxs-lookup"><span data-stu-id="769f6-126">The decrypted message, "Try the new Break All command," is the result.</span></span>

```powershell
$parameters = @{
  LiteralPath = "C:\Users\Test\Documents\PowerShell\Future_Plans.txt"
  To = '0f 8j b1 ab e0 ce 35 1d 67 d2 f2 6f a2 d2 00 cl 22 z9 m9 85'
}
Unprotect-CmsMessage -LiteralPath @parameters
```

```Output
Try the new Break All command
```

## <span data-ttu-id="769f6-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="769f6-127">PARAMETERS</span></span>

### <span data-ttu-id="769f6-128">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="769f6-128">-Content</span></span>

<span data-ttu-id="769f6-129">Anger en krypterad sträng eller en variabel som innehåller en krypterad sträng.</span><span class="sxs-lookup"><span data-stu-id="769f6-129">Specifies an encrypted string, or a variable containing an encrypted string.</span></span>

```yaml
Type: System.String
Parameter Sets: ByContent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="769f6-130">-EventLogRecord</span><span class="sxs-lookup"><span data-stu-id="769f6-130">-EventLogRecord</span></span>

<span data-ttu-id="769f6-131">Anger ett post-ID för händelse loggen som representerar en CMS-krypterings åtgärd.</span><span class="sxs-lookup"><span data-stu-id="769f6-131">Specifies an event log record ID that represents a CMS encryption operation.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByWinEvent
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="769f6-132">-IncludeContext</span><span class="sxs-lookup"><span data-stu-id="769f6-132">-IncludeContext</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="769f6-133">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="769f6-133">-LiteralPath</span></span>

<span data-ttu-id="769f6-134">Anger sökvägen till krypterat innehåll som du vill dekryptera.</span><span class="sxs-lookup"><span data-stu-id="769f6-134">Specifies the path to encrypted content that you want to decrypt.</span></span> <span data-ttu-id="769f6-135">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="769f6-135">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="769f6-136">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="769f6-136">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="769f6-137">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="769f6-137">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="769f6-138">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="769f6-138">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="769f6-139">-Path</span><span class="sxs-lookup"><span data-stu-id="769f6-139">-Path</span></span>

<span data-ttu-id="769f6-140">Anger sökvägen till krypterat innehåll som du vill dekryptera.</span><span class="sxs-lookup"><span data-stu-id="769f6-140">Specifies the path to encrypted content that you want to decrypt.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="769f6-141">-Till</span><span class="sxs-lookup"><span data-stu-id="769f6-141">-To</span></span>

<span data-ttu-id="769f6-142">Anger ett eller flera CMS-meddelanden som har identifierats i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="769f6-142">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="769f6-143">Ett faktiskt certifikat (som hämtats från certifikat leverantören).</span><span class="sxs-lookup"><span data-stu-id="769f6-143">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="769f6-144">Sökväg till en fil som innehåller certifikatet.</span><span class="sxs-lookup"><span data-stu-id="769f6-144">Path to the a file containing the certificate.</span></span>
- <span data-ttu-id="769f6-145">Sökväg till en katalog som innehåller certifikatet.</span><span class="sxs-lookup"><span data-stu-id="769f6-145">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="769f6-146">Tumavtryck för certifikatet (används för att söka i certifikat arkivet).</span><span class="sxs-lookup"><span data-stu-id="769f6-146">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="769f6-147">Certifikatets ämnes namn (används för att söka i certifikat arkivet).</span><span class="sxs-lookup"><span data-stu-id="769f6-147">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="769f6-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="769f6-148">CommonParameters</span></span>

<span data-ttu-id="769f6-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="769f6-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="769f6-150">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="769f6-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="769f6-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="769f6-151">INPUTS</span></span>

### <span data-ttu-id="769f6-152">System. Diagnostics. Eventing. Reader. EventLogRecord eller system. String</span><span class="sxs-lookup"><span data-stu-id="769f6-152">System.Diagnostics.Eventing.Reader.EventLogRecord or System.String</span></span>

<span data-ttu-id="769f6-153">Du kan skicka vidare ett objekt som innehåller krypterat innehåll till `Unprotect-CmsMessage` .</span><span class="sxs-lookup"><span data-stu-id="769f6-153">You can pipe an object containing encrypted content to `Unprotect-CmsMessage`.</span></span>

## <span data-ttu-id="769f6-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="769f6-154">OUTPUTS</span></span>

### <span data-ttu-id="769f6-155">System. String</span><span class="sxs-lookup"><span data-stu-id="769f6-155">System.String</span></span>

<span data-ttu-id="769f6-156">Det okrypterade meddelandet.</span><span class="sxs-lookup"><span data-stu-id="769f6-156">The unencrypted message.</span></span>

## <span data-ttu-id="769f6-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="769f6-157">NOTES</span></span>

## <span data-ttu-id="769f6-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="769f6-158">RELATED LINKS</span></span>

[<span data-ttu-id="769f6-159">about_Providers</span><span class="sxs-lookup"><span data-stu-id="769f6-159">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="769f6-160">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="769f6-160">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="769f6-161">Skydda – CmsMessage</span><span class="sxs-lookup"><span data-stu-id="769f6-161">Protect-CmsMessage</span></span>](Protect-CmsMessage.md)
