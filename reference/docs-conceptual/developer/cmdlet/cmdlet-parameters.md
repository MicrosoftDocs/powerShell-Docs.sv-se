---
title: Cmdlet-parametrar | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- optional parameters [PowerShell SDK]
- aliases [PowerShell SDK]
- parameter sets [PowerShell SDK]
- parameters [PowerShell SDK]
- mandatory parameters [PowerShell SDK]
- positional parameters [PowerShell SDK]
- cmdlets [PowerShell SDK], parameters
ms.openlocfilehash: 98b1d5fd0e7ffbf2d4d161f1bed73fb96a737bd4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774770"
---
# <a name="cmdlet-parameters"></a>Cmdlet-parametrar

Cmdlet-parametrar tillhandahåller mekanismen som tillåter att en cmdlet accepterar ininformation. Parametrar kan acceptera indata direkt från kommando raden eller från objekt som skickas till cmdleten via pipelinen. argumenten (även kallade *värden*) för dessa parametrar kan ange de indata som cmdleten accepterar, hur cmdleten ska utföra sina åtgärder och vilka data som cmdleten returnerar till pipelinen.

## <a name="in-this-section"></a>I det här avsnittet

[Deklarera egenskaper som parametrar](./declaring-properties-as-parameters.md) Innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.

[Typer av cmdlet-parametrar](./types-of-cmdlet-parameters.md) Beskriver de olika typerna av parametrar som du kan deklarera i-cmdletar.

[Rikt linjer för cmdlet-parameter namn och funktioner](./standard-cmdlet-parameter-names-and-types.md) Diskuterar namn, rekommenderad datatyp och funktioner i standard parametrar.

[Parameter-alias](./parameter-aliases.md) Beskriver de alias som du kan definiera för parametrar.

[Vanliga parameter namn](./common-parameter-names.md) I det här avsnittet beskrivs de parametrar som Windows PowerShell lägger till i-cmdletar.

[Cmdlet-parameter uppsättningar](./cmdlet-parameter-sets.md) Beskriver hur parameter uppsättningar gör det möjligt att skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.

[Dynamiska cmdlet-parametrar](./cmdlet-dynamic-parameters.md) Beskriver de parametrar som är tillgängliga för användaren under särskilda villkor.

[Stöd för jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md) Beskriver hur du ger stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.

[Verifierar parameter Indatatyp](./validating-parameter-input.md) Beskriver hur Windows PowerShell validerar argumenten som skickas till cmdlet-parametrar.

[Parametrar för inparametrar](./input-filter-parameters.md) Beskriver `Filter` parametrarna, `Include` och `Exclude` som filtrerar uppsättningen inobjekt som cmdleten påverkar.

## <a name="related-sections"></a>Närliggande avsnitt

[Verifiera parameterindata](./how-to-validate-parameter-input.md)

## <a name="see-also"></a>Se även

[Deklaration av attributet Parameter](./parameter-attribute-declaration.md)

[Windows PowerShell-cmdletar](./cmdlet-overview.md)
