---
title: Parametrar för | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057137"
---
# <a name="security-parameters"></a>Säkerhetsparametrar

I följande tabell visas de rekommenderade namn och funktioner för parametrar som används för att ange säkerhetsinformation för en åtgärd, till exempel parametrar som anger certifikatinformationen för nyckeln och behörigheten.

|Parameter|Funktioner|
|---|---|
|**ACL**<br>Datatyp: Sträng|Implementera den här parametern om du vill ange åtkomstnivå för kontroll av skydd för en katalog eller för en identifierare URI (Uniform Resource).|
|**CertFile**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange namnet på en fil som innehåller något av följande:<br>-En Base64- eller DER Distinguished Encoding Rules ()-kodad x.509-certifikat<br>– En offentlig Key Cryptography Standards (PKCS) #12-fil som innehåller minst ett certifikat och nyckel|
|**CertIssuerName**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange ett namn för utfärdaren av ett certifikat eller så att användaren kan ange en delsträng.|
|**CertRequestFile**<br>Datatyp: Sträng|Implementera den här parametern om du vill ange namnet på en fil som innehåller en Base64- eller DER-kodad PKCS #10-certifikatbegäran.|
|**CertSerialNumber**<br>Datatyp: Sträng|Implementera den här parametern om du vill ange serienumret som har utfärdats av certifikatutfärdaren.|
|**CertStoreLocation**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange platsen för arkivet. Platsen är vanligtvis en sökväg till filen.|
|**CertSubjectName**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange utfärdaren av ett certifikat eller så att användaren kan ange en delsträng.|
|**CertUsage**<br>Datatyp: Sträng|Implementera den här parametern om du vill ange nyckelanvändningen eller avancerad nyckelanvändning. Nyckeln kan representeras som en aning maskera, en aning objektidentifierare (OID) eller en sträng.|
|**Autentiseringsuppgifter**<br>Datatyp: [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementera den här parametern så att cmdleten ska automatiskt frågar användaren om ett användarnamn eller lösenord. Ett meddelande för både visas om en fullständig autentiseringsuppgift anges direkt.|
|**CSPName**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange namnet på certifikatet service provider (CSP).|
|**CSPType**<br>Datatyp: Heltal|Implementera den här parametern så att användaren kan ange vilken typ av CSP.|
|**Grupp**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en samling av säkerhetsobjekt för åtkomst. Mer information finns i beskrivningen av den **huvudnamn** parametern.|
|**KeyAlgorithm**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange nyckelgenerering-algoritm som ska användas för säkerhet.|
|**Nyckelbehållare**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange namnet på nyckelbehållaren.|
|**KeyLength**<br>Datatyp: Heltal|Implementera den här parametern så att användaren kan ange längden på nyckeln i bitar.|
|**Åtgärd**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en åtgärd som kan utföras på ett skyddat objekt.|
|**Principal**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en unik identifierbar entitet för åtkomst.|
|**Behörighet**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange höger en cmdlet måste utföra en åtgärd för en viss enhet.|
|**Privilegier**<br>Datatyp: Matris med privilegier|Implementera den här parametern så att användaren kan ange de rättigheter som en cmdlet behöver för att utföra åtgärden för en viss post.|
|**Rollen**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en uppsättning åtgärder som kan utföras av en annan entitet.|
|**SaveCred**<br>Datatyp: SwitchParameter|Implementera den här parametern så att autentiseringsuppgifter som tidigare sparades av användaren kommer att användas när parametern anges.|
|**Omfång**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange gruppen för skyddade objekt för cmdleten.|
|**SID**<br>Datatyp: Sträng|Implementera den här parametern så att användaren kan ange en unik identifierare som representerar ett huvudnamn.|
|**Betrodda**<br>Datatyp: SwitchParameter|Implementera den här parametern så att förtroendenivåer stöds när parametern anges.|
|**TrustLevel**<br>Datatyp: Nyckelord|Implementera den här parametern så att användaren kan ange förtroendenivå som stöds. Möjliga värden omfattar till exempel internet och intranätet fulltrust.|

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
