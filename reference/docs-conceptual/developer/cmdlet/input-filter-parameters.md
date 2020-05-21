---
title: Indataparametrar för filter | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 7a1582031d27f78bad069f5539408312ccabb3f2
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563879"
---
# <a name="input-filter-parameters"></a>Lägga till filterparametrar

En cmdlet kan definiera `Filter` , `Include` , och `Exclude` parametrar som filtrerar uppsättningen med inobjekt som cmdleten påverkar.

Normalt anges insamlings objekt av en `InputObject` , `Path` -eller- `Name` parameter. En cmdlet kan till exempel ha en `Path` parameter som accepterar flera sökvägar med hjälp av jokertecken och varje sökväg pekar på ett inobjekt. Används tillsammans, `Filter` parametrarna, `Include` och för `Exclude` att ytterligare kvalificera Sök vägarna som cmdleten fungerar vid varje gång den anropas.

## <a name="include-and-exclude-parameters"></a>Inkludera och exkludera parametrar

`Include`Parametrarna och `Exclude` identifierar de objekt som ingår i eller undantas från den uppsättning indataportar som skickas till cmdleten. Använd de här parametrarna när filtret kan uttryckas i standard språket jokertecken. (Mer information om jokertecken finns i [stödjande jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include`Parametern innehåller alla objekt vars namn matchar inkluderings filtret. `Exclude`Parametern utesluter alla objekt vars namn matchar filtret.

## <a name="filter-parameter"></a>Filter parameter

`Filter`Parametern anger ett filter som inte uttrycks i standard språket jokertecken. Till exempel kan Active Directory Service Interfaces (ADSI) eller SQL-filter skickas till cmdleten via dess `Filter` parameter. I de cmdlets som tillhandahålls av Windows PowerShell anges dessa filter av de Windows PowerShell-leverantörer som använder cmdleten för att få åtkomst till ett data lager. Varje provider definierar vanligt vis sitt eget filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrera om ingen uppsättning med inmatade objekt har angetts

Om ingen uppsättning med inobjekt har angetts innebär det vanligt vis att filtrera mot alla objekt. Mer information finns i[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
