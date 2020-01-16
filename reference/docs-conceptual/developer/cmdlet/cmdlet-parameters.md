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
ms.openlocfilehash: c1d8984f4aad7bae6f9be66a2222e2c74c8afa3d
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022206"
---
# <a name="cmdlet-parameters"></a><span data-ttu-id="6a97e-102">Cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="6a97e-102">Cmdlet Parameters</span></span>

<span data-ttu-id="6a97e-103">Cmdlet-parametrar tillhandahåller mekanismen som tillåter att en cmdlet accepterar ininformation.</span><span class="sxs-lookup"><span data-stu-id="6a97e-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="6a97e-104">Parametrar kan acceptera indata direkt från kommando raden eller från objekt som skickas till cmdleten via pipelinen. argumenten (även kallade *värden*) för dessa parametrar kan ange de indata som cmdleten accepterar, hur cmdleten ska utföra sina åtgärder och vilka data som cmdleten returnerar till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6a97e-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6a97e-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="6a97e-105">In This Section</span></span>

<span data-ttu-id="6a97e-106">[Deklarera egenskaper som parametrar](./declaring-properties-as-parameters.md) Innehåller grundläggande information som du måste förstå innan du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a97e-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="6a97e-107">[Typer av cmdlet-parametrar](./types-of-cmdlet-parameters.md) Beskriver de olika typerna av parametrar som du kan deklarera i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="6a97e-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="6a97e-108">[Rikt linjer för cmdlet-parameter namn och funktioner](./standard-cmdlet-parameter-names-and-types.md) Diskuterar namn, rekommenderad datatyp och funktioner i standard parametrar.</span><span class="sxs-lookup"><span data-stu-id="6a97e-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discusses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="6a97e-109">[Parameter-alias](./parameter-aliases.md) Beskriver de alias som du kan definiera för parametrar.</span><span class="sxs-lookup"><span data-stu-id="6a97e-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="6a97e-110">[Vanliga parameter namn](./common-parameter-names.md) I det här avsnittet beskrivs de parametrar som Windows PowerShell lägger till i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="6a97e-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="6a97e-111">[Cmdlet-parameter uppsättningar](./cmdlet-parameter-sets.md) Beskriver hur parameter uppsättningar gör det möjligt att skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="6a97e-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="6a97e-112">[Dynamiska cmdlet-parametrar](./cmdlet-dynamic-parameters.md) Beskriver de parametrar som är tillgängliga för användaren under särskilda villkor.</span><span class="sxs-lookup"><span data-stu-id="6a97e-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="6a97e-113">[Stöd för jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md) Beskriver hur du ger stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.</span><span class="sxs-lookup"><span data-stu-id="6a97e-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="6a97e-114">[Verifierar parameter Indatatyp](./validating-parameter-input.md) Beskriver hur Windows PowerShell validerar argumenten som skickas till cmdlet-parametrar.</span><span class="sxs-lookup"><span data-stu-id="6a97e-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="6a97e-115">[Parametrar för inparametrar](./input-filter-parameters.md) Beskriver parametrarna `Filter`, `Include`och `Exclude` som filtrerar uppsättningen inobjekt som cmdleten påverkar.</span><span class="sxs-lookup"><span data-stu-id="6a97e-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="6a97e-116">Relaterade avsnitt</span><span class="sxs-lookup"><span data-stu-id="6a97e-116">Related Sections</span></span>

[<span data-ttu-id="6a97e-117">Verifiera parameter ingångar</span><span class="sxs-lookup"><span data-stu-id="6a97e-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="6a97e-118">Se även</span><span class="sxs-lookup"><span data-stu-id="6a97e-118">See Also</span></span>

[<span data-ttu-id="6a97e-119">Deklaration av parameter attribut</span><span class="sxs-lookup"><span data-stu-id="6a97e-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="6a97e-120">Windows PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="6a97e-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
