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
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849030"
---
# <a name="security-parameters"></a>Säkerhetsparametrar

I följande tabell visas de rekommenderade namn och funktioner för parametrar som används för att ange säkerhetsinformation för en åtgärd, till exempel parametrar som anger certifikatinformationen för nyckeln och behörigheten.

ACL-datatyp: Sträng

Implementera den här parametern om du vill ange åtkomstnivå för kontroll av skydd för en katalog eller för en identifierare URI (Uniform Resource).

Certifikatfil datatyp: Sträng

Implementera den här parametern så att användaren kan ange namnet på en fil som innehåller något av följande:

- En Base64- eller DER Distinguished Encoding Rules ()-kodad x.509-certifikat

- En offentlig Key Cryptography Standards (PKCS) #12-fil som innehåller minst ett certifikat och nyckel

CertIssuerName datatyp: Sträng

Implementera den här parametern så att användaren kan ange ett namn för utfärdaren av ett certifikat eller så att användaren kan ange en delsträng.

CertRequestFile datatyp: Sträng

Implementera den här parametern om du vill ange namnet på en fil som innehåller en Base64- eller DER-kodad PKCS #10-certifikatbegäran.

CertSerialNumber datatyp: Sträng

Implementera den här parametern om du vill ange serienumret som har utfärdats av certifikatutfärdaren.

CertStoreLocation datatyp: Sträng

Implementera den här parametern så att användaren kan ange platsen för arkivet. Platsen är vanligtvis en sökväg till filen.

CertSubjectName datatyp: Sträng

Implementera den här parametern så att användaren kan ange utfärdaren av ett certifikat eller så att användaren kan ange en delsträng.

CertUsage datatyp: Sträng

Implementera den här parametern om du vill ange nyckelanvändningen eller avancerad nyckelanvändning. Nyckeln kan representeras som en aning maskera, en aning objektidentifierare (OID) eller en sträng.

Autentiseringsuppgifterna skriver du: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)

Implementera den här parametern så att cmdleten ska automatiskt frågar användaren om ett användarnamn eller lösenord. Ett meddelande för både visas om en fullständig autentiseringsuppgift anges direkt.

Kryptografiprovider datatyp: Sträng

Implementera den här parametern så att användaren kan ange namnet på certifikatet service provider (CSP).

CSPType datatyp: Heltal

Implementera den här parametern så att användaren kan ange vilken typ av CSP.

Gruppera Data skriver du: Sträng

Implementera den här parametern så att användaren kan ange en samling av säkerhetsobjekt för åtkomst. Mer information finns i beskrivningen av den `Principal` parametern.

KeyAlgorithm datatyp: Sträng

Implementera den här parametern så att användaren kan ange nyckelgenerering-algoritm som ska användas för säkerhet.

Nyckelbehållare datatyp: Sträng

Implementera den här parametern så att användaren kan ange namnet på nyckelbehållaren.

Nyckellängd datatyp: Heltal

Implementera den här parametern så att användaren kan ange längden på nyckeln i bitar.

Åtgärden datatyp: Sträng

Implementera den här parametern så att användaren kan ange en åtgärd som kan utföras på ett skyddat objekt.

Huvudnamn datatyp: Sträng

Implementera den här parametern så att användaren kan ange en unik identifierbar entitet för åtkomst.

Behörighet datatyp: Sträng

Implementera den här parametern så att användaren kan ange höger en cmdlet måste utföra en åtgärd för en viss enhet.

Privilegier datatyp: Matris med privilegier

Implementera den här parametern så att användaren kan ange de rättigheter som en cmdlet behöver för att utföra åtgärden för en viss post.

Datatypen för rollen: Sträng

Implementera den här parametern så att användaren kan ange en uppsättning åtgärder som kan utföras av en annan entitet.

SaveCred datatyp: SwitchParameter

Implementera den här parametern så att autentiseringsuppgifter som tidigare sparades av användaren kommer att användas när parametern anges.

Scope-datatyp: Sträng

Implementera den här parametern så att användaren kan ange gruppen för skyddade objekt för cmdleten.

Typ av SID Data: Sträng

Implementera den här parametern så att användaren kan ange en unik identifierare som representerar ett huvudnamn.

Betrodda datatyp: SwitchParameter

Implementera den här parametern så att förtroendenivåer stöds när parametern anges.

TrustLevel datatyp: Nyckelord

Implementera den här parametern så att användaren kan ange förtroendenivå som stöds. Möjliga värden omfattar till exempel internet och intranätet fulltrust.

## <a name="see-also"></a>Se även

[Cmdlet-parametrarna](./cmdlet-parameters.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
