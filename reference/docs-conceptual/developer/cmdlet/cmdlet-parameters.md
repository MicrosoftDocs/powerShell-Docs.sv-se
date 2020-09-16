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
# <a name="cmdlet-parameters"></a><span data-ttu-id="59392-102">Cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="59392-102">Cmdlet Parameters</span></span>

<span data-ttu-id="59392-103">Cmdlet-parametrar tillhandahåller mekanismen som tillåter att en cmdlet accepterar ininformation.</span><span class="sxs-lookup"><span data-stu-id="59392-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="59392-104">Parametrar kan acceptera indata direkt från kommando raden eller från objekt som skickas till cmdleten via pipelinen. argumenten (även kallade *värden*) för dessa parametrar kan ange de indata som cmdleten accepterar, hur cmdleten ska utföra sina åtgärder och vilka data som cmdleten returnerar till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="59392-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="59392-105">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="59392-105">In This Section</span></span>

<span data-ttu-id="59392-106">[Deklarera egenskaper som parametrar](./declaring-properties-as-parameters.md) Innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59392-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="59392-107">[Typer av cmdlet-parametrar](./types-of-cmdlet-parameters.md) Beskriver de olika typerna av parametrar som du kan deklarera i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="59392-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="59392-108">[Rikt linjer för cmdlet-parameter namn och funktioner](./standard-cmdlet-parameter-names-and-types.md) Diskuterar namn, rekommenderad datatyp och funktioner i standard parametrar.</span><span class="sxs-lookup"><span data-stu-id="59392-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="59392-109">[Parameter-alias](./parameter-aliases.md) Beskriver de alias som du kan definiera för parametrar.</span><span class="sxs-lookup"><span data-stu-id="59392-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="59392-110">[Vanliga parameter namn](./common-parameter-names.md) I det här avsnittet beskrivs de parametrar som Windows PowerShell lägger till i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="59392-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="59392-111">[Cmdlet-parameter uppsättningar](./cmdlet-parameter-sets.md) Beskriver hur parameter uppsättningar gör det möjligt att skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="59392-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="59392-112">[Dynamiska cmdlet-parametrar](./cmdlet-dynamic-parameters.md) Beskriver de parametrar som är tillgängliga för användaren under särskilda villkor.</span><span class="sxs-lookup"><span data-stu-id="59392-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="59392-113">[Stöd för jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md) Beskriver hur du ger stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.</span><span class="sxs-lookup"><span data-stu-id="59392-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="59392-114">[Verifierar parameter Indatatyp](./validating-parameter-input.md) Beskriver hur Windows PowerShell validerar argumenten som skickas till cmdlet-parametrar.</span><span class="sxs-lookup"><span data-stu-id="59392-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="59392-115">[Parametrar för inparametrar](./input-filter-parameters.md) Beskriver `Filter` parametrarna, `Include` och `Exclude` som filtrerar uppsättningen inobjekt som cmdleten påverkar.</span><span class="sxs-lookup"><span data-stu-id="59392-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="59392-116">Närliggande avsnitt</span><span class="sxs-lookup"><span data-stu-id="59392-116">Related Sections</span></span>

[<span data-ttu-id="59392-117">Verifiera parameterindata</span><span class="sxs-lookup"><span data-stu-id="59392-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="59392-118">Se även</span><span class="sxs-lookup"><span data-stu-id="59392-118">See Also</span></span>

[<span data-ttu-id="59392-119">Deklaration av attributet Parameter</span><span class="sxs-lookup"><span data-stu-id="59392-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="59392-120">Windows PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="59392-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
