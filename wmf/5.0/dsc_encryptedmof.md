---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 9af931a1a2b545ba36826246c4155f42052a16bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085720"
---
# <a name="mof-documents-are-encrypted-by-default"></a>MOF-dokument krypteras som standard

Av konfigurationsdokument innehåller känslig information. I tidigare versioner av DSC tvungen att distribuera och hantera certifikat för att skydda autentiseringsuppgifterna i en konfiguration. Detta var en betydande hanteringsbelastning för många, och även med allt arbete som det tog för att göra det du har fortfarande kvar med vissa konfigurationsinformation som fanns inte och kan inte skyddas.

Det behövs inte längre är fallet eftersom **all konfiguration som MOF-filer är skyddade som standard**. Inga certifikat eller meta-konfigurationsinställningar behövs. Varje gång en konfiguration som MOF sparas disk av den lokala Configuration Manager (LCM) på en målnod, det är krypterat. De MOF: ar krypteras med hjälp av [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Obs:** Som inte är krypterade MOF: ar som genererats av ett konfigurationsskript.

**Exempel:** Kryptering i push-läget ![MOF-kryptering](../images/MOF_Encryption.jpg)

Om du redan använder metoden certifikat för att kryptera lösenord eller om du behöver ytterligare säkerhet för ditt lösenord, den [befintliga metoden för certifikatbaserad kryptering](https://msdn.microsoft.com/powershell/dsc/securemof) fortsätter att fungera. Resultatet kommer vara en MOF-dokument som är helt krypterad med hjälp av DPAPIs och dessutom ha lösenord krypteras i den.

Den här krypteringen gäller endast för configuration MOF-dokument (pending.mof, current.mof, previous.mof och partiella MOF: ar). Meta-konfiguration MOF: ar sparas fortfarande i oformaterad text eftersom de innehåller mindre troligt hemligheter.
