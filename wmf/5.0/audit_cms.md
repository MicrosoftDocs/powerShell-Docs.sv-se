---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: b8940ded189d822a5a2cd40773ef5146353611cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62059006"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cryptographic Message Syntax CMS-cmdletar

Syntaxen Cryptographic Message Syntax-cmdletarna har stöd för kryptering och dekryptering av innehåll med hjälp av IETF standardformat för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](https://tools.ietf.org/html/rfc5652).

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

Standard CMS krypteringen implementerar kryptering med offentlig nyckel, där nycklarna som används för att kryptera innehållet (den *offentlig nyckel*) och alla nycklarna som används för att dekryptera innehåll (den *privata nyckeln*) är separata.

Din offentliga nyckel kan delas brett och är inte känsliga data. Om allt innehåll som är krypterade med den offentliga nyckeln kan kan bara din privata nyckel dekryptera den. Mer information finns i [kryptografi med offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

Om du vill bli uppmärksammad i PowerShell, kräver krypteringscertifikat en identifierare för unika nyckelanvändning (EKU) att identifiera dem som data krypteringscertifikat (t.ex. ID: n för ”kodsignering”, krypterade e).

Här är ett exempel för att skapa ett certifikat som är bra för kryptering av dokument:

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

Kör sedan:
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

Och nu kan kryptera och dekryptera innehåll:

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

Någon parameter av typen **CMSMessageRecipient** stöder identifierare i följande format:
- Ett verkligt certifikat (som hämtas från certifikatleverantör)
- Sökvägen till i en fil som innehåller certifikatet
- Sökvägen till en katalog som innehåller certifikatet
- Tumavtrycket för certifikatet (används för att leta i certifikatarkivet)
- Ämnesnamnet för certifikatet (används för att leta i certifikatarkivet)

Om du vill visa dokumentet krypteringscertifikat i certifikatleverantör, du kan använda den **- DocumentEncryptionCert** dynamisk parameter:

```powershell
dir -DocumentEncryptionCert
```
