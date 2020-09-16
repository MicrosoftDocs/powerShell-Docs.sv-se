---
title: Fel rapportering för Windows PowerShell | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7f7afcf5186732734976304c8e58e4d940156e1e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783967"
---
# <a name="windows-powershell-error-reporting"></a>Windows PowerShell-felrapportering

Ämnena i det här avsnittet beskriver hur cmdlets rapporterar fel.

## <a name="in-this-section"></a>I det här avsnittet

[Fel rapporterings begrepp](./error-reporting-concepts.md) Beskriver de två mekanismer som cmdletar kan använda för att rapportera fel.

[Fel avslutas](./terminating-errors.md) Beskriver den metod som används för att rapportera avslutande fel, där den metoden kan anropas från cmdleten och undantag som kan returneras av Windows PowerShell-körningsmiljön när metoden anropas.

[Icke-avslutande fel](./non-terminating-errors.md) Beskriver den metod som används för att rapportera icke-avslutande fel och där metoden kan anropas inifrån cmdleten.

[Visa fel information per kategori](./displaying-error-information.md) Beskriver hur användarna kan visa fel.

[Windows PowerShell-felposter](./windows-powershell-error-records.md) Beskriver komponenterna i en felpost.

[Tolka ErrorRecord-objekt](./interpreting-errorrecord-objects.md) Beskriver hur ErrorRecord-objekt tolkas.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
