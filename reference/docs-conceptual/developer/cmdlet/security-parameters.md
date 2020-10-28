---
ms.date: 09/13/2016
ms.topic: reference
title: Säkerhetsparametrar
description: Säkerhetsparametrar
ms.openlocfilehash: 2c73a3372fa719ea436d4a3ae1223d4cbaaf9108
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650257"
---
# <a name="security-parameters"></a>Säkerhetsparametrar

I följande tabell visas rekommenderade namn och funktioner för parametrar som används för att ange säkerhets information för en åtgärd, till exempel parametrar som anger information om certifikat nyckel och privilegier.

|Parameter|Funktioner|
|---|---|
|**ACL**<br>Datatyp: sträng|Implementera den här parametern för att ange skydds nivån för åtkomst kontroll för en katalog eller för en Uniform Resource Identifier (URI).|
|**Certifikat fil**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på en fil som innehåller något av följande:<br>– Ett base64-kodat (base64) eller Distinguished Encoding Rules-kodat x. 509-certifikat<br>– En PKCS (Public Key Cryptography Standards) #12-fil som innehåller minst ett certifikat och en nyckel|
|**CertIssuerName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på utfärdaren av ett certifikat eller så att användaren kan ange en under sträng.|
|**CertRequestFile**<br>Datatyp: sträng|Implementera den här parametern för att ange namnet på en fil som innehåller en Base64-eller DER-kodad PKCS #10-certifikatbegäran.|
|**CertSerialNumber**<br>Datatyp: sträng|Implementera den här parametern för att ange det serie nummer som utfärdades av certifikat utfärdaren.|
|**CertStoreLocation**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange platsen för certifikat arkivet. Platsen är vanligt vis en fil Sök väg.|
|**CertSubjectName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange utfärdaren av ett certifikat eller så att användaren kan ange en under sträng.|
|**CertUsage**<br>Datatyp: sträng|Implementera den här parametern för att ange nyckel användningen eller den förbättrade nyckel användningen. Nyckeln kan representeras som en bitmask, en bit, en objekt identifierare (OID) eller en sträng.|
|**Autentiseringsuppgift**<br>Datatyp: [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementera den här parametern så att cmdleten automatiskt kommer att uppmana användaren att ange ett användar namn eller lösen ord. En prompt för båda visas om en fullständig autentiseringsuppgift inte anges direkt.|
|**CSPName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på certifikat tjänst leverantören (CSP).|
|**CSPType**<br>Datatyp: Heltal|Implementera den här parametern så att användaren kan ange typen av CSP.|
|**Grupper**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en samling med huvud konton för åtkomst. Mer information finns i beskrivningen av **huvud** parametern.|
|**KeyAlgorithm**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange vilken algoritm för nyckel skapande som ska användas för säkerhet.|
|**KeyContainerName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på nyckel behållaren.|
|**Nyckellängd**<br>Datatyp: Heltal|Implementera den här parametern så att användaren kan ange längden på nyckeln i bitar.|
|**Åtgärd**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en åtgärd som kan utföras på ett skyddat objekt.|
|**Viktigaste**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en unik identifierbar entitet för åtkomst.|
|**Grupperna**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange rätt en cmdlet måste utföra en åtgärd för en viss entitet.|
|**Behörigheter**<br>Datatyp: matris med privilegier|Implementera den här parametern så att användaren kan ange de rättigheter som en cmdlet måste utföra för att utföra åtgärden för en viss post.|
|**Role**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en uppsättning åtgärder som kan utföras av en entitet.|
|**SaveCred**<br>Datatyp: SwitchParameter|Implementera den här parametern så att autentiseringsuppgifterna som tidigare sparades av användaren används när parametern anges.|
|**Omfång**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange gruppen med skyddade objekt för cmdleten.|
|**SID**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en unik identifierare som representerar ett huvud konto.|
|**Pålitlig**<br>Datatyp: SwitchParameter|Implementera den här parametern så att förtroende nivåer stöds när parametern anges.|
|**TrustLevel**<br>Datatyp: nyckelord|Implementera den här parametern så att användaren kan ange den förtroende nivå som stöds. Exempel: möjliga värden är Internet, intranät och FullTrust.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrar](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
