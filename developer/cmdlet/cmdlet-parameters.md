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
# <a name="cmdlet-parameters"></a><span data-ttu-id="e1e37-102">Cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="e1e37-102">Cmdlet Parameters</span></span>

<span data-ttu-id="e1e37-103">Cmdlet-parametrarna tillhandahåller den mekanism som gör att en cmdlet för att acceptera indata.</span><span class="sxs-lookup"><span data-stu-id="e1e37-103">Cmdlet parameters provide the mechanism that allows a cmdlet to accept input.</span></span> <span data-ttu-id="e1e37-104">Parametrar kan acceptera indata direkt från kommandoraden eller från objekt som överförs till cmdleten genom pipelinen och argumenten (även kallat *värden*) för dessa parametrar kan ange indata som cmdleten godtar hur cmdleten bör utföra sina åtgärder och de data som cmdleten returnerar till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1e37-104">Parameters can accept input directly from the command line, or from objects passed to the cmdlet through the pipeline, The arguments (also known as *values*) of these parameters can specify the input that the cmdlet accepts, how the cmdlet should perform its actions, and the data that the cmdlet returns to the pipeline.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e1e37-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="e1e37-105">In This Section</span></span>

<span data-ttu-id="e1e37-106">[Deklarerar egenskaper som parametrar](./declaring-properties-as-parameters.md) innehåller grundläggande information som du måste förstå innan du deklarera parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e1e37-106">[Declaring Properties as Parameters](./declaring-properties-as-parameters.md) Provides basic information you must understand before you declare the parameters of a cmdlet.</span></span>

<span data-ttu-id="e1e37-107">[Typer av Cmdlet-parametrarna](./types-of-cmdlet-parameters.md) beskriver de olika typerna av parametrar som du kan deklarera i cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="e1e37-107">[Types of Cmdlet Parameters](./types-of-cmdlet-parameters.md) Describes the different types of parameters that you can declare in cmdlets.</span></span>

<span data-ttu-id="e1e37-108">[Cmdlet parameternamnet och funktioner riktlinjer](./standard-cmdlet-parameter-names-and-types.md) diskusar namn, datatyp och funktionerna i standardparametrar.</span><span class="sxs-lookup"><span data-stu-id="e1e37-108">[Cmdlet Parameter Name and Functionality Guidelines](./standard-cmdlet-parameter-names-and-types.md) Discuses the names, recommended data type, and functionality of standard parameters.</span></span>

<span data-ttu-id="e1e37-109">[Parameteralias](./parameter-aliases.md) beskrivs alias som du kan definiera för parametrar.</span><span class="sxs-lookup"><span data-stu-id="e1e37-109">[Parameter Aliases](./parameter-aliases.md) Discusses the aliases that you can define for parameters.</span></span>

<span data-ttu-id="e1e37-110">[Vanliga parameternamn](./common-parameter-names.md) det här avsnittet beskrivs de parametrar som Windows PowerShell lägger till cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="e1e37-110">[Common Parameter Names](./common-parameter-names.md) This topic describes the parameters that Windows PowerShell adds to cmdlets.</span></span>

<span data-ttu-id="e1e37-111">[Cmdlet: en Parameter anger](./cmdlet-parameter-sets.md) diskuterar hur parameteruppsättningar gör att du kan skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="e1e37-111">[Cmdlet Parameter Sets](./cmdlet-parameter-sets.md) Discusses how parameter sets enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span>

<span data-ttu-id="e1e37-112">[Dynamiska parametrar för cmdleten](./cmdlet-dynamic-parameters.md) beskriver parametrar som är tillgängliga för användare under särskilda villkor.</span><span class="sxs-lookup"><span data-stu-id="e1e37-112">[Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md) Discusses parameters that are available to the user under special conditions.</span></span>

<span data-ttu-id="e1e37-113">[Stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md) beskriver hur du ger stöd för jokertecken när du utformar en cmdlet som ska köras mot en grupp med resurser.</span><span class="sxs-lookup"><span data-stu-id="e1e37-113">[Supporting Wildcard Characters in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md) Describes how to provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

<span data-ttu-id="e1e37-114">[Verifierar indata för parametern](./validating-parameter-input.md) beskriver hur Windows PowerShell verifierar argumenten som skickades till cmdlet-parametrarna.</span><span class="sxs-lookup"><span data-stu-id="e1e37-114">[Validating Parameter Input](./validating-parameter-input.md) Describes how Windows PowerShell validates the arguments passed to cmdlet parameters.</span></span>

<span data-ttu-id="e1e37-115">[Ange filterparametrar](./input-filter-parameters.md) Discusses den `Filter`, `Include`, och `Exclude` parametrar som filtrera en uppsättning inkommande objekt som påverkas av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="e1e37-115">[Input Filter Parameters](./input-filter-parameters.md) Discusses the `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e1e37-116">Relaterade avsnitt</span><span class="sxs-lookup"><span data-stu-id="e1e37-116">Related Sections</span></span>

[<span data-ttu-id="e1e37-117">Hur du verifierar indata för parametern</span><span class="sxs-lookup"><span data-stu-id="e1e37-117">How to Validate Parameter Input</span></span>](./how-to-validate-parameter-input.md)

## <a name="see-also"></a><span data-ttu-id="e1e37-118">Se även</span><span class="sxs-lookup"><span data-stu-id="e1e37-118">See Also</span></span>

[<span data-ttu-id="e1e37-119">Attributet parameterdeklaration</span><span class="sxs-lookup"><span data-stu-id="e1e37-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="e1e37-120">Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e1e37-120">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)
