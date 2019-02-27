---
title: Felrapportering begrepp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846167"
---
# <a name="error-reporting-concepts"></a>Begrepp relaterade till felrapportering

Windows PowerShell innehåller två mekanismer för rapporterat fel: en mekanism för *avslutande fel* och en annan mekanism för *icke-avslutande fel*. Det är viktigt för din cmdlet för att rapportera fel korrekt så att värdprogrammet som kör dina cmdlets kan reagera på lämpligt sätt.

Cmdlet: ska anropa den [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metoden när ett fel som inte eller bör inte tillåta att cmdleten ska fortsätta att bearbeta dess inkommande objekt. Cmdlet: ska anropa den [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod för att rapportera icke-avslutande fel när cmdlet: en kan fortsätta att bearbeta inkommande objekt. Båda metoderna ger en Felpost värdprogrammet kan använda för att undersöka orsaken till felet.

Använd följande riktlinjer för att fastställa om ett fel är avslutande eller icke-avslutande fel.

- Ett fel är ett avslutande fel om det förhindrar att cmdlet: fortsätter att bearbeta det aktuella objektet eller bearbetar eventuella ytterligare indata objekt, oavsett deras innehåll.

- Ett fel är ett avslutande fel om du inte vill cmdlet: fortsätta att bearbeta det aktuella objektet eller eventuella ytterligare indata objekt, oavsett deras innehåll.

- Ett fel är ett avslutande fel om det inträffar i en cmdlet som inte acceptera eller returneras ett objekt eller om det förekommer i en cmdlet som godkänner eller returnerar endast ett objekt.

- Ett fel är ett icke-avslutande fel om cmdlet: vill du fortsätta att bearbeta det aktuella objektet och alla objekt som är ytterligare indata.

- Ett fel är ett icke-avslutande fel om den är kopplad till en specifik indataobjektet eller en delmängd av indata-objekt.

## <a name="see-also"></a>Se även

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
