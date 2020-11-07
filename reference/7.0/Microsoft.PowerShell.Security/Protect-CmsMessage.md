---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 02/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/protect-cmsmessage?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Protect-CmsMessage
ms.openlocfilehash: de72454f4c50746ca22853dd51e2ec0447bed101
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347643"
---
# <span data-ttu-id="23bcd-103">Protect-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="23bcd-103">Protect-CmsMessage</span></span>

## <span data-ttu-id="23bcd-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="23bcd-104">SYNOPSIS</span></span>
<span data-ttu-id="23bcd-105">Krypterar innehåll med hjälp av formatet kryptografiskt meddelande-syntax.</span><span class="sxs-lookup"><span data-stu-id="23bcd-105">Encrypts content by using the Cryptographic Message Syntax format.</span></span>

## <span data-ttu-id="23bcd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23bcd-106">SYNTAX</span></span>

### <span data-ttu-id="23bcd-107">ByContent (standard)</span><span class="sxs-lookup"><span data-stu-id="23bcd-107">ByContent (Default)</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <PSObject> [[-OutFile] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="23bcd-108">ByPath</span><span class="sxs-lookup"><span data-stu-id="23bcd-108">ByPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <String> [[-OutFile] <String>] [<CommonParameters>]
```

### <span data-ttu-id="23bcd-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="23bcd-109">ByLiteralPath</span></span>

```
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <String> [[-OutFile] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="23bcd-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="23bcd-110">DESCRIPTION</span></span>

<span data-ttu-id="23bcd-111">`Protect-CmsMessage`Cmdleten krypterar innehåll med hjälp av CMS-formatet (Encryption Message Syntax).</span><span class="sxs-lookup"><span data-stu-id="23bcd-111">The `Protect-CmsMessage` cmdlet encrypts content by using the Cryptographic Message Syntax (CMS) format.</span></span>

<span data-ttu-id="23bcd-112">CMS-cmdletarna stöder kryptering och dekryptering av innehåll med hjälp av IETF-formatet som dokumenteras av [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span><span class="sxs-lookup"><span data-stu-id="23bcd-112">The CMS cmdlets support encryption and decryption of content using the IETF format as documented by [RFC5652](https://tools.ietf.org/html/rfc5652.html).</span></span>

<span data-ttu-id="23bcd-113">CMS-standarden för standard använder kryptering med offentliga nycklar, där nycklarna som används för att kryptera innehåll (den offentliga nyckeln) och de nycklar som används för att dekryptera innehållet (den privata nyckeln) är separata.</span><span class="sxs-lookup"><span data-stu-id="23bcd-113">The CMS encryption standard uses public key cryptography, where the keys used to encrypt content (the public key) and the keys used to decrypt content (the private key) are separate.</span></span> <span data-ttu-id="23bcd-114">Din offentliga nyckel kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="23bcd-114">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="23bcd-115">Om något innehåll krypteras med den här offentliga nyckeln kan bara den privata nyckeln dekryptera den.</span><span class="sxs-lookup"><span data-stu-id="23bcd-115">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="23bcd-116">Mer information finns i [kryptering med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="23bcd-116">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="23bcd-117">Innan du kan köra `Protect-CmsMessage` cmdleten måste du konfigurera ett krypterings certifikat.</span><span class="sxs-lookup"><span data-stu-id="23bcd-117">Before you can run the `Protect-CmsMessage` cmdlet, you must have an encryption certificate set up.</span></span>
<span data-ttu-id="23bcd-118">För att kunna identifieras i PowerShell kräver krypterings certifikat ett unikt ID för utökad nyckel användning ([EKU](/windows/desktop/SecCrypto/eku)) för att identifiera dem som data krypterings certifikat (till exempel ID: n för kod signering och krypterad e-post).</span><span class="sxs-lookup"><span data-stu-id="23bcd-118">To be recognized in PowerShell, encryption certificates require a unique extended key usage ([EKU](/windows/desktop/SecCrypto/eku)) ID to identify them as data encryption certificates (such as the IDs for Code Signing and Encrypted Mail).</span></span> <span data-ttu-id="23bcd-119">Ett exempel på ett certifikat som skulle fungera för dokument kryptering finns i exempel 1 i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="23bcd-119">For an example of a certificate that would work for document encryption, see Example 1 in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="23bcd-120">Den här cmdleten är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="23bcd-120">This cmdlet is only available on Windows.</span></span>

## <span data-ttu-id="23bcd-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="23bcd-121">EXAMPLES</span></span>

### <span data-ttu-id="23bcd-122">Exempel 1: skapa ett certifikat för kryptering av innehåll</span><span class="sxs-lookup"><span data-stu-id="23bcd-122">Example 1: Create a certificate for encrypting content</span></span>

<span data-ttu-id="23bcd-123">Innan du kan köra `Protect-CmsMessage` cmdleten måste du skapa ett krypterings certifikat.</span><span class="sxs-lookup"><span data-stu-id="23bcd-123">Before you can run the `Protect-CmsMessage` cmdlet, you must create an encryption certificate.</span></span> <span data-ttu-id="23bcd-124">Använd följande text och ändra namnet på ämnes raden till ditt namn, din e-postadress eller annan identifierare och spara certifikatet i en fil (till exempel `DocumentEncryption.inf` , som visas i det här exemplet).</span><span class="sxs-lookup"><span data-stu-id="23bcd-124">Using the following text, change the name in the Subject line to your name, email, or other identifier, and save the certificate in a file (such as `DocumentEncryption.inf`, as shown in this example).</span></span>

```powershell
# Create .INF file for certreq
{[Version]
Signature = "$Windows NT$"

[Strings]
szOID_ENHANCED_KEY_USAGE = "2.5.29.37"
szOID_DOCUMENT_ENCRYPTION = "1.3.6.1.4.1.311.80.1"

[NewRequest]
Subject = "cn=youralias@emailaddress.com"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT_KEY_ENCIPHERMENT_KEY_USAGE | CERT_DATA_ENCIPHERMENT_KEY_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"

[Extensions]
%szOID_ENHANCED_KEY_USAGE% = "{text}%szOID_DOCUMENT_ENCRYPTION%"
} | Out-File -FilePath DocumentEncryption.inf

# After you have created your certificate file, run the following command to add
# the certificate file to the certificate store. Now you are ready to encrypt and
# decrypt content with the next two examples.
certreq.exe -new DocumentEncryption.inf DocumentEncryption.cer
```

### <span data-ttu-id="23bcd-125">Exempel 2: kryptera ett meddelande som skickas via e-post</span><span class="sxs-lookup"><span data-stu-id="23bcd-125">Example 2: Encrypt a message sent by email</span></span>

```powershell
$Protected = "Hello World" | Protect-CmsMessage -To "*youralias@emailaddress.com*"
```

<span data-ttu-id="23bcd-126">I följande exempel krypterar du ett meddelande, "Hello World", genom att skicka det till `Protect-CmsMessage` cmdleten och sedan spara det krypterade meddelandet i en variabel.</span><span class="sxs-lookup"><span data-stu-id="23bcd-126">In the following example, you encrypt a message, "Hello World", by piping it to the `Protect-CmsMessage` cmdlet, and then save the encrypted message in a variable.</span></span> <span data-ttu-id="23bcd-127">Parametern **to** använder värdet för ämnes raden i certifikatet.</span><span class="sxs-lookup"><span data-stu-id="23bcd-127">The **To** parameter uses the value of the Subject line in the certificate.</span></span>

### <span data-ttu-id="23bcd-128">Exempel 3: Visa dokument krypterings certifikat</span><span class="sxs-lookup"><span data-stu-id="23bcd-128">Example 3: View document encryption certificates</span></span>

```
PS C:\> cd Cert:\CurrentUser\My
PS Cert:\CurrentUser\My> Get-ChildItem -DocumentEncryptionCert
```

<span data-ttu-id="23bcd-129">Om du vill visa dokument krypterings certifikat i certifikat leverantören kan du lägga till den dynamiska parametern **DocumentEncryptionCert** för [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), som är tillgänglig endast när certifikat leverantören har lästs in.</span><span class="sxs-lookup"><span data-stu-id="23bcd-129">To view document encryption certificates in the certificate provider, you can add the **DocumentEncryptionCert** dynamic parameter of [Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md), available only when the certificate provider is loaded.</span></span>

## <span data-ttu-id="23bcd-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="23bcd-130">PARAMETERS</span></span>

### <span data-ttu-id="23bcd-131">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="23bcd-131">-Content</span></span>

<span data-ttu-id="23bcd-132">Anger en **PSObject** som innehåller innehåll som du vill kryptera.</span><span class="sxs-lookup"><span data-stu-id="23bcd-132">Specifies a **PSObject** that contains content that you want to encrypt.</span></span> <span data-ttu-id="23bcd-133">Du kan till exempel kryptera innehållet i ett händelse meddelande och sedan använda variabeln som innehåller meddelandet ( `$Event` i det här exemplet) som värde för **innehålls** parametern: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1` .</span><span class="sxs-lookup"><span data-stu-id="23bcd-133">For example, you can encrypt the content of an event message, and then use the variable containing the message (`$Event`, in this example) as the value of the **Content** parameter: `$event = Get-WinEvent -ProviderName "PowerShell" -MaxEvents 1`.</span></span> <span data-ttu-id="23bcd-134">Du kan också använda `Get-Content` cmdleten för att hämta innehållet i en fil, till exempel ett Microsoft Word-dokument, och spara innehållet i en variabel som du använder som värde för **innehålls** parametern.</span><span class="sxs-lookup"><span data-stu-id="23bcd-134">You can also use the `Get-Content` cmdlet to get the contents of a file, such as a Microsoft Word document, and save the content in a variable that you use as the value of the **Content** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByContent
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="23bcd-135">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="23bcd-135">-LiteralPath</span></span>

<span data-ttu-id="23bcd-136">Anger sökvägen till det innehåll som du vill kryptera.</span><span class="sxs-lookup"><span data-stu-id="23bcd-136">Specifies the path to content that you want to encrypt.</span></span> <span data-ttu-id="23bcd-137">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="23bcd-137">Unlike **Path** , the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="23bcd-138">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="23bcd-138">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="23bcd-139">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="23bcd-139">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="23bcd-140">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="23bcd-140">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="23bcd-141">-Fil</span><span class="sxs-lookup"><span data-stu-id="23bcd-141">-OutFile</span></span>

<span data-ttu-id="23bcd-142">Anger sökvägen och fil namnet för en fil som du vill skicka det krypterade innehållet till.</span><span class="sxs-lookup"><span data-stu-id="23bcd-142">Specifies the path and file name of a file to which you want to send the encrypted content.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23bcd-143">-Path</span><span class="sxs-lookup"><span data-stu-id="23bcd-143">-Path</span></span>

<span data-ttu-id="23bcd-144">Anger sökvägen till det innehåll som du vill kryptera.</span><span class="sxs-lookup"><span data-stu-id="23bcd-144">Specifies the path to content that you want to encrypt.</span></span>

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

### <span data-ttu-id="23bcd-145">-Till</span><span class="sxs-lookup"><span data-stu-id="23bcd-145">-To</span></span>

<span data-ttu-id="23bcd-146">Anger ett eller flera CMS-meddelanden som har identifierats i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="23bcd-146">Specifies one or more CMS message recipients, identified in any of the following formats:</span></span>

- <span data-ttu-id="23bcd-147">Ett faktiskt certifikat (som hämtats från certifikat leverantören).</span><span class="sxs-lookup"><span data-stu-id="23bcd-147">An actual certificate (as retrieved from the certificate provider).</span></span>
- <span data-ttu-id="23bcd-148">Sökväg till filen som innehåller certifikatet.</span><span class="sxs-lookup"><span data-stu-id="23bcd-148">Path to the file containing the certificate.</span></span>
- <span data-ttu-id="23bcd-149">Sökväg till en katalog som innehåller certifikatet.</span><span class="sxs-lookup"><span data-stu-id="23bcd-149">Path to a directory containing the certificate.</span></span>
- <span data-ttu-id="23bcd-150">Tumavtryck för certifikatet (används för att söka i certifikat arkivet).</span><span class="sxs-lookup"><span data-stu-id="23bcd-150">Thumbprint of the certificate (used to look in the certificate store).</span></span>
- <span data-ttu-id="23bcd-151">Certifikatets ämnes namn (används för att söka i certifikat arkivet).</span><span class="sxs-lookup"><span data-stu-id="23bcd-151">Subject name of the certificate (used to look in the certificate store).</span></span>

```yaml
Type: System.Management.Automation.CmsMessageRecipient[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23bcd-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23bcd-152">CommonParameters</span></span>

<span data-ttu-id="23bcd-153">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="23bcd-153">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="23bcd-154">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="23bcd-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="23bcd-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="23bcd-155">INPUTS</span></span>

## <span data-ttu-id="23bcd-156">UTDATA</span><span class="sxs-lookup"><span data-stu-id="23bcd-156">OUTPUTS</span></span>

## <span data-ttu-id="23bcd-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="23bcd-157">NOTES</span></span>

<span data-ttu-id="23bcd-158">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="23bcd-158">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="23bcd-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="23bcd-159">RELATED LINKS</span></span>

[<span data-ttu-id="23bcd-160">about_Providers</span><span class="sxs-lookup"><span data-stu-id="23bcd-160">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="23bcd-161">Get-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="23bcd-161">Get-CmsMessage</span></span>](Get-CmsMessage.md)

[<span data-ttu-id="23bcd-162">Ta bort skydd-CmsMessage</span><span class="sxs-lookup"><span data-stu-id="23bcd-162">Unprotect-CmsMessage</span></span>](Unprotect-CmsMessage.md)
