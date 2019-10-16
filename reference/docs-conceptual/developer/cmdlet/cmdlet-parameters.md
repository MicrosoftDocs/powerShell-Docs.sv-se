---
title: Cmdlet-parametrar | Microsoft Docs
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356576"
---
# <a name="cmdlet-parameters"></a>Cmdlet-parametrar

Cmdlet-parametrar tillhandahåller mekanismen som tillåter att en cmdlet accepterar ininformation. Parametrar kan acceptera inmatade objekt direkt från kommando raden eller från objekt som skickas till cmdleten via pipelinen, men argumenten (även kallade *värden*) för dessa parametrar kan ange vilka indatatyper som cmdleten accepterar, hur cmdleten ska utföra åtgärder och de data som cmdleten returnerar till pipelinen.

## <a name="in-this-section"></a>I detta avsnitt

[Deklarera egenskaper som parametrar](./declaring-properties-as-parameters.md) Innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.

[Typer av cmdlet-parametrar](./types-of-cmdlet-parameters.md) Beskriver de olika typerna av parametrar som du kan deklarera i-cmdletar.

[Rikt linjer för cmdlet-parameter namn och funktioner](./standard-cmdlet-parameter-names-and-types.md) Discuses namn, rekommenderad datatyp och funktioner i standard parametrar.

[Parameter-alias](./parameter-aliases.md) Beskriver de alias som du kan definiera för parametrar.

[Vanliga parameter namn](./common-parameter-names.md) I det här avsnittet beskrivs de parametrar som Windows PowerShell lägger till i-cmdletar.

[Cmdlet-parameter uppsättningar](./cmdlet-parameter-sets.md) Beskriver hur parameter uppsättningar gör det möjligt att skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.

[Dynamiska cmdlet-parametrar](./cmdlet-dynamic-parameters.md) Beskriver de parametrar som är tillgängliga för användaren under särskilda villkor.

[Stöd för jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md) Beskriver hur du ger stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.

[Verifierar parameter Indatatyp](./validating-parameter-input.md) Beskriver hur Windows PowerShell validerar argumenten som skickas till cmdlet-parametrar.

[Parametrar för inparametrar](./input-filter-parameters.md) Beskriver `Filter`-, `Include`-och `Exclude`-parametrar som filtrerar uppsättningen inobjekt som cmdleten påverkar.

## <a name="related-sections"></a>Relaterade avsnitt

[Verifiera parameter ingångar](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Se även

[Deklaration av parameter attribut](./parameter-attribute-declaration.md)

[Windows PowerShell-cmdletar](./cmdlet-overview.md)
