---
title: Fel rapportering för Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355414"
---
# <a name="windows-powershell-error-reporting"></a>Windows PowerShell-felrapportering

Ämnena i det här avsnittet beskriver hur cmdlets rapporterar fel.

## <a name="in-this-section"></a>I detta avsnitt

[Fel rapporterings begrepp](./error-reporting-concepts.md) Beskriver de två mekanismer som cmdletar kan använda för att rapportera fel.

[Fel avslutas](./terminating-errors.md) Beskriver den metod som används för att rapportera avslutande fel, där den metoden kan anropas från cmdleten och undantag som kan returneras av Windows PowerShell-körningsmiljön när metoden anropas.

[Icke-avslutande fel](./non-terminating-errors.md) Beskriver den metod som används för att rapportera icke-avslutande fel och där metoden kan anropas inifrån cmdleten.

[Visa fel information per kategori](./displaying-error-information.md) Beskriver hur användarna kan visa fel.

[Windows PowerShell-felposter](./windows-powershell-error-records.md) Beskriver komponenterna i en felpost.

[Tolka ErrorRecord-objekt](./interpreting-errorrecord-objects.md) Beskriver hur ErrorRecord-objekt tolkas.

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
