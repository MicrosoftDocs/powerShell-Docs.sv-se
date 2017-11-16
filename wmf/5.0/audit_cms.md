---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 60055b6755a31397c49686ea9ee1a69ada3516de
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="feafe-102">Cryptographic Message Syntax (CMS) cmdlets</span><span class="sxs-lookup"><span data-stu-id="feafe-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="feafe-103">Syntax för kryptografiska meddelanden-cmdlets stöd för kryptering och dekryptering av innehåll med hjälp av format för IETF-standard för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](https://tools.ietf.org/html/rfc5652).</span><span class="sxs-lookup"><span data-stu-id="feafe-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

<span data-ttu-id="feafe-104">CMS-kryptering standard implementerar kryptering med offentlig nyckel, där nycklar används för att kryptera innehållet (den *offentliga nyckel*) och nycklar som används för att dekryptera innehållet (den *privat nyckel*) är separat.</span><span class="sxs-lookup"><span data-stu-id="feafe-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="feafe-105">Din offentliga nyckel kan delas brett och är inte känsliga data.</span><span class="sxs-lookup"><span data-stu-id="feafe-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="feafe-106">Om allt innehåll krypteras med den här offentliga nyckeln kan kan bara din privata nyckel dekryptera den.</span><span class="sxs-lookup"><span data-stu-id="feafe-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="feafe-107">Mer information finns i [offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="feafe-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="feafe-108">Om du vill för att identifiera i PowerShell kräver krypteringscertifikat en identifierare för unik nyckelanvändning (EKU) att identifiera dem som data krypteringscertifikat (till exempel identifierare för ”kodsignering”, krypterade e).</span><span class="sxs-lookup"><span data-stu-id="feafe-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="feafe-109">Här är ett exempel på hur du skapar ett certifikat som är bra för kryptering av dokument:</span><span class="sxs-lookup"><span data-stu-id="feafe-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

<span data-ttu-id="feafe-110">Kör sedan:</span><span class="sxs-lookup"><span data-stu-id="feafe-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="feafe-111">Och du kan nu kryptera och dekryptera innehåll:</span><span class="sxs-lookup"><span data-stu-id="feafe-111">And you can now encrypt and decrypt content:</span></span>

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

<span data-ttu-id="feafe-112">En parameter av typen **CMSMessageRecipient** stöder identifierare i följande format:</span><span class="sxs-lookup"><span data-stu-id="feafe-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="feafe-113">Ett faktiska certifikat (som hämtades från providern certifikat)</span><span class="sxs-lookup"><span data-stu-id="feafe-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="feafe-114">Sökvägen till i en fil som innehåller certifikatet</span><span class="sxs-lookup"><span data-stu-id="feafe-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="feafe-115">Sökvägen till en katalog som innehåller certifikat</span><span class="sxs-lookup"><span data-stu-id="feafe-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="feafe-116">Tumavtrycket för certifikatet (används för att leta i certifikatarkivet)</span><span class="sxs-lookup"><span data-stu-id="feafe-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="feafe-117">Ämnesnamnet för certifikatet (används för att leta i certifikatarkivet)</span><span class="sxs-lookup"><span data-stu-id="feafe-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="feafe-118">Du kan använda för att visa dokumentet krypteringscertifikat i providern certifikatet, den **- DocumentEncryptionCert** dynamic-parametern:</span><span class="sxs-lookup"><span data-stu-id="feafe-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```

