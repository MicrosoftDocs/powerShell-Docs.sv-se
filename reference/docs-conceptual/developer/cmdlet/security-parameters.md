---
title: Säkerhets parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359354"
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
|**Autentiseringsuppgifter**<br>Datatyp: [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementera den här parametern så att cmdleten automatiskt kommer att uppmana användaren att ange ett användar namn eller lösen ord. En prompt för båda visas om en fullständig autentiseringsuppgift inte anges direkt.|
|**CSPName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på certifikat tjänst leverantören (CSP).|
|**CSPType**<br>Datatyp: heltal|Implementera den här parametern så att användaren kan ange typen av CSP.|
|**Grupp**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en samling med huvud konton för åtkomst. Mer information finns i beskrivningen av **huvud** parametern.|
|**Nyckelalgoritm**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange vilken algoritm för nyckel skapande som ska användas för säkerhet.|
|**KeyContainerName**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange namnet på nyckel behållaren.|
|**Nyckel längd**<br>Datatyp: heltal|Implementera den här parametern så att användaren kan ange längden på nyckeln i bitar.|
|**Åtgärd**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en åtgärd som kan utföras på ett skyddat objekt.|
|**Viktigaste**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange en unik identifierbar entitet för åtkomst.|
|**Grupperna**<br>Datatyp: sträng|Implementera den här parametern så att användaren kan ange rätt en cmdlet måste utföra en åtgärd för en viss entitet.|
|**Privilegier**<br>Datatyp: matris med privilegier|Implementera den här parametern så att användaren kan ange de rättigheter som en cmdlet måste utföra för att utföra åtgärden för en viss post.|
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
