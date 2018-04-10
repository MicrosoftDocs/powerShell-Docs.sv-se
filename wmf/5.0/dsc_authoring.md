---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a>Redigeringsförbättringar med PowerShell ISE

Redigering av DSC-konfigurationer i Windows PowerShell ISE är mycket enklare, tack till följande förbättringar:

- Visa en lista med alla DSC resurser inom en **configuration** block eller **nod** block genom att ange **Ctrl + blanksteg** på en tom rad i den.
- Automatisk komplettering på resursegenskaper av den **uppräkningen** typen.
- Automatisk komplettering på den **DependsOn** -egenskapen för DSC-resurser, baserat på andra resurs-instanser i konfigurationen.
- Bättre flikavslutande egenskapsvärden för resurs.

**Obs:** du måste ha en tom sträng för egenskapsvärden för resurs innan du kan använda Ctrl + blanksteg för att visa en lista med alternativen. När du trycker på **fliken** växlar mellan alternativ.