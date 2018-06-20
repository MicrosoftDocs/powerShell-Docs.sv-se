---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 14208e3b5d5c2fef80fa42a87cc00aeee81bd042
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189915"
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a>Cryptographic Message Syntax (CMS) cmdlets

Syntax för kryptografiska meddelanden-cmdlets stöd för kryptering och dekryptering av innehåll med hjälp av format för IETF-standard för att skydda kryptografiskt meddelanden som det dokumenterats i [RFC5652](https://tools.ietf.org/html/rfc5652).

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

CMS-kryptering standard implementerar kryptering med offentlig nyckel, där nycklar används för att kryptera innehållet (den *offentliga nyckel*) och nycklar som används för att dekryptera innehållet (den *privat nyckel*) är separat.

Din offentliga nyckel kan delas brett och är inte känsliga data. Om allt innehåll krypteras med den här offentliga nyckeln kan kan bara din privata nyckel dekryptera den. Mer information finns i [offentliga nycklar](https://en.wikipedia.org/wiki/Public-key_cryptography).

Om du vill för att identifiera i PowerShell kräver krypteringscertifikat en identifierare för unik nyckelanvändning (EKU) att identifiera dem som data krypteringscertifikat (till exempel identifierare för ”kodsignering”, krypterade e).

Här är ett exempel på hur du skapar ett certifikat som är bra för kryptering av dokument:

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

Och du kan nu kryptera och dekryptera innehåll:

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

En parameter av typen **CMSMessageRecipient** stöder identifierare i följande format:
- Ett faktiska certifikat (som hämtades från providern certifikat)
- Sökvägen till i en fil som innehåller certifikatet
- Sökvägen till en katalog som innehåller certifikat
- Tumavtrycket för certifikatet (används för att leta i certifikatarkivet)
- Ämnesnamnet för certifikatet (används för att leta i certifikatarkivet)

Du kan använda för att visa dokumentet krypteringscertifikat i providern certifikatet, den **- DocumentEncryptionCert** dynamic-parametern:

```powershell
dir -DocumentEncryptionCert
```
