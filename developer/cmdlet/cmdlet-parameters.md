---
title: Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.assetid: 3f1cca5f-5b95-4bce-94a6-a22db1aefd47
caps.latest.revision: 23
ms.openlocfilehash: 914a10907bcf980eed8d7e2f819c382fe6b341ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068410"
---
# <a name="cmdlet-parameters"></a>Cmdlet-parametrar

Cmdlet-parametrarna tillhandahåller den mekanism som gör att en cmdlet för att acceptera indata. Parametrar kan acceptera indata direkt från kommandoraden eller från objekt som överförs till cmdleten genom pipelinen och argumenten (även kallat *värden*) för dessa parametrar kan ange indata som cmdleten godtar hur cmdleten bör utföra sina åtgärder och de data som cmdleten returnerar till pipelinen.

## <a name="in-this-section"></a>I detta avsnitt

[Deklarerar egenskaper som parametrar](./declaring-properties-as-parameters.md) innehåller grundläggande information som du måste förstå innan du deklarera parametrarna för en cmdlet.

[Typer av Cmdlet-parametrarna](./types-of-cmdlet-parameters.md) beskriver de olika typerna av parametrar som du kan deklarera i cmdlet: ar.

[Cmdlet parameternamnet och funktioner riktlinjer](./standard-cmdlet-parameter-names-and-types.md) diskusar namn, datatyp och funktionerna i standardparametrar.

[Parameteralias](./parameter-aliases.md) beskrivs alias som du kan definiera för parametrar.

[Vanliga parameternamn](./common-parameter-names.md) det här avsnittet beskrivs de parametrar som Windows PowerShell lägger till cmdlet: ar.

[Cmdlet: en Parameter anger](./cmdlet-parameter-sets.md) diskuterar hur parameteruppsättningar gör att du kan skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.

[Dynamiska parametrar för cmdleten](./cmdlet-dynamic-parameters.md) beskriver parametrar som är tillgängliga för användare under särskilda villkor.

[Stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md) beskriver hur du ger stöd för jokertecken när du utformar en cmdlet som ska köras mot en grupp med resurser.

[Verifierar indata för parametern](./validating-parameter-input.md) beskriver hur Windows PowerShell verifierar argumenten som skickades till cmdlet-parametrarna.

[Ange filterparametrar](./input-filter-parameters.md) Discusses den `Filter`, `Include`, och `Exclude` parametrar som filtrera en uppsättning inkommande objekt som påverkas av cmdlet: en.

## <a name="related-sections"></a>Relaterade avsnitt

[Hur du verifierar indata för parametern](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Se även

[Attributet parameterdeklaration](./parameter-attribute-declaration.md)

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)
