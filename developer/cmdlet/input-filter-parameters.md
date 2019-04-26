---
title: Ange filterparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067696"
---
# <a name="input-filter-parameters"></a>Lägga till filterparametrar

En cmdlet kan definiera `Filter`, `Include`, och `Exclude` parametrar som filtrera en uppsättning inkommande objekt som påverkas av cmdlet: en.

Normalt en uppsättning inkommande objekt anges av en `InputObject`, `Path`, eller `Name` parametern. En cmdlet kan till exempel ha en `Path` parameter som accepterar flera sökvägar genom att använda jokertecken och varje sökväg pekar på ett inkommande objekt. Används tillsammans, den `Filter`, `Include`, och `Exclude` ytterligare parametrar kvalificera sökvägarna cmdlet fungerar på varje gång den anropas.

## <a name="include-and-exclude-parameters"></a>Inkludera och exkludera parametrar

Den `Include` och `Exclude` parametrar definieras objekt som inkluderas eller uteslutas från uppsättningen med inkommande objekt som överförs till cmdleten. Använd dessa parametrar när filtret kan uttryckas på språket som standard med jokertecken. (Läs mer om jokertecken [stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Den `Include` parametern innehåller de objekt vars namn matchar filtret inkludering. Den `Exclude` parametern omfattar inte de objekt vars namn matchar filtret.

## <a name="filter-parameter"></a>Filter-parametern

Den `Filter` parametern anger ett filter som inte uttrycks på språket som standard med jokertecken. Till exempel tjänsten gränssnitt ADSI (Active Directory) eller SQL-filter kan skickas till cmdleten via dess `Filter` parametern. I dessa cmdlets som tillhandahålls av Windows PowerShell, anges filtren av Windows PowerShell-providrarna som använder cmdlet: en för att få åtkomst till ett datalager. Varje leverantör definierar vanligtvis sitt eget filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrering om ingen uppsättning inkommande objekt har angetts

Om ingen uppsättning inkommande objekt anges innebär detta oftast att filtrera mot alla objekt. Mer information finns i[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)