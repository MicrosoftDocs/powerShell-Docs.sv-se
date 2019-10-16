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
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355498"
---
# <a name="input-filter-parameters"></a>Lägga till filterparametrar

En cmdlet kan definiera `Filter`, `Include`-och `Exclude`-parametrar som filtrerar uppsättningen inobjekt som cmdleten påverkar.

Normalt anges insamlings objekt av en `InputObject`-, `Path`-eller `Name`-parameter. En cmdlet kan till exempel ha en `Path`-parameter som accepterar flera sökvägar med hjälp av jokertecken, och varje sökväg pekar på ett inobjekt. Används tillsammans kvalificerar parametrarna `Filter`, `Include` och @no__t 2 ytterligare de sökvägar som cmdleten fungerar på varje gång den anropas.

## <a name="include-and-exclude-parameters"></a>Inkludera och exkludera parametrar

Parametrarna `Include` och `Exclude` identifierar de objekt som ingår i eller undantas från uppsättningen indatamängder som skickas till cmdleten. Använd de här parametrarna när filtret kan uttryckas i standard språket jokertecken. (Mer information om jokertecken finns i [stödjande jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Parametern `Include` innehåller alla objekt vars namn matchar inkluderings filtret. Parametern `Exclude` utesluter alla objekt vars namn matchar filtret.

## <a name="filter-parameter"></a>Filter parameter

Parametern `Filter` anger ett filter som inte uttrycks i standard språket för jokertecken. Till exempel kan Active Directory Service Interfaces (ADSI) eller SQL-filter skickas till cmdleten via dess `Filter`-parameter. I de cmdlets som tillhandahålls av Windows PowerShell anges dessa filter av de Windows PowerShell-leverantörer som använder cmdleten för att få åtkomst till ett data lager. Varje provider definierar vanligt vis sitt eget filter.

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a>Filtrera om ingen uppsättning med inmatade objekt har angetts

Om ingen uppsättning med inobjekt har angetts innebär det vanligt vis att filtrera mot alla objekt. Mer information finns i[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)