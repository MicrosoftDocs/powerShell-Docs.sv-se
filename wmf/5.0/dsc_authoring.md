---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 555e01e88647b40717417360fb74bb6554a9c122
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="authoring-improvements-using-powershell-ise"></a>Redigering av förbättringar som använder PowerShell ISE

Redigering av DSC-konfigurationer i Windows PowerShell ISE är mycket enklare, tack till följande förbättringar:

- Visa en lista med alla DSC resurser inom en **configuration** block eller **nod** block genom att ange **Ctrl + blanksteg** på en tom rad i den.
- Automatisk komplettering på resursegenskaper av den **uppräkningen** typen.
- Automatisk komplettering på den **DependsOn** -egenskapen för DSC-resurser, baserat på andra resurs-instanser i konfigurationen.
- Bättre flikavslutande egenskapsvärden för resurs.

**Obs:** du måste ha en tom sträng för egenskapsvärden för resurs innan du kan använda Ctrl + blanksteg för att visa en lista med alternativen. När du trycker på **fliken** växlar mellan alternativ.

