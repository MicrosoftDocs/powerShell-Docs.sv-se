---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 60abe525ca1bdcebca570f2ef3656f32dca3747f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="mof-documents-are-encrypted-by-default"></a>MOF dokument krypteras automatiskt

Av konfigurationsdokument innehåller känslig information. I tidigare versioner av DSC var du tvungen att distribuera och hantera certifikat för att säkra autentiseringsuppgifter i en konfiguration. Detta var en stor arbetsbörda för många, och även med allt arbete som det tog för att göra detta du fortfarande har lämnat med vissa konfigurationsinformation som inte och kan inte skyddas. 

Som inte längre fallet eftersom **all konfiguration av MOF-filer skyddas som standard**. Inga certifikat eller meta-konfigurationsinställningar krävs. Varje gång en konfiguration som MOF sparas disk av den lokala Configuration Manager (MGM) på Målnoden är krypterad. De MOF-filer krypteras med [DPAPI](https://msdn.microsoft.com/library/ms995355.aspx). **Obs:** MOF-filer som genererats av ett konfigurationsskript krypteras inte.

**Exempel:** kryptering i push-läge ![MOF-kryptering](../images/MOF_Encryption.jpg)

Om du redan använder metoden certifikat för kryptering av lösenord eller om du behöver ytterligare säkerhet för ditt lösenord, den [befintlig metod certifikatbaserad kryptering](https://msdn.microsoft.com/powershell/dsc/securemof) fortsätter att fungera. Resultatet kommer att vara MOF som krypteras fullständigt med DPAPIs och dessutom ha lösenord krypteras i den.

Krypteringsnycklar gäller endast configuration MOF-dokument (pending.mof, current.mof, previous.mof och partiella MOF-filer). Meta configuration MOF-filer sparas i klartext fortfarande eftersom de innehåller mindre troligt hemligheter.

