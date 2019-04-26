---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085651"
---
# <a name="authoring-improvements-using-powershell-ise"></a>Redigeringsförbättringar med PowerShell ISE

Redigering av DSC-konfigurationer i Windows PowerShell ISE är mycket enklare, tack vare följande förbättringar:

- Lista över alla DSC-resurser i en **configuration** block eller **nod** block genom att ange **Ctrl + blanksteg** på en tom rad i den.
- Automatisk komplettering på resursegenskaper som är av den **uppräkning** typen.
- Automatisk komplettering på den **DependsOn** egenskapen för DSC-resurser, baserat på andra resursinstanser i konfigurationen.
- Bättre tabbifyllning för egenskapsvärden för resurs.

**Obs:** Du måste ha en tom sträng för egenskapsvärden för resurs innan du kan använda Ctrl + blanksteg för att visa alternativen. Att trycka på **fliken** växlar mellan alternativ.
