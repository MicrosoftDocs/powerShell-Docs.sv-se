---
title: Attributet parameterdeklaration | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: 81b1ed95669f51ba554f6f99031d098e239f02e0
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735132"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="35eda-102">Deklaration av attributet Parameter</span><span class="sxs-lookup"><span data-stu-id="35eda-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="35eda-103">Parameterattributet identifierar en offentlig egenskap för klassen cmdlet som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="35eda-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="35eda-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="35eda-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="35eda-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="35eda-105">Parameters</span></span>

<span data-ttu-id="35eda-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="35eda-107">`True` Visar den cmdlet-parametern krävs.</span><span class="sxs-lookup"><span data-stu-id="35eda-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="35eda-108">Om en obligatorisk parameter inte anges när cmdleten har anropats, frågar Windows PowerShell användaren om ett parametervärde.</span><span class="sxs-lookup"><span data-stu-id="35eda-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="35eda-109">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="35eda-109">The default is `false`.</span></span>

<span data-ttu-id="35eda-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="35eda-111">Anger parametern anger att den här cmdlet-parameter som tillhör.</span><span class="sxs-lookup"><span data-stu-id="35eda-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="35eda-112">Om inga parameteruppsättningen anges tillhör parametern alla parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="35eda-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="35eda-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="35eda-114">Anger positionen för parameter i ett Windows PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="35eda-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="35eda-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="35eda-116">`True` Anger att cmdlet-parameter tar dess värde från ett pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="35eda-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="35eda-117">Ange det här nyckelordet om cmdlet: en har åtkomst till hela objektet, inte bara en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="35eda-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="35eda-118">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="35eda-118">The default is `false`.</span></span>

<span data-ttu-id="35eda-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="35eda-120">`True` Anger att cmdlet-parameter tar dess värde från en egenskap för en pipeline-objekt som har samma namn eller samma alias som den här parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="35eda-121">Om cmdleten har till exempel en `Name` parametern och pipeline-objektet har också en `Name` egenskap, värdet för den `Name` egenskapen tilldelas den `Name` parametern för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="35eda-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="35eda-122">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="35eda-122">The default is `false`.</span></span>

<span data-ttu-id="35eda-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="35eda-124">`True` Anger att cmdlet-parameter godkänner alla återstående argument som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="35eda-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="35eda-125">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="35eda-125">The default is `false`.</span></span>

<span data-ttu-id="35eda-126">`HelpMessage` Valfritt med namnet parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="35eda-127">Anger en kort beskrivning av parametern.</span><span class="sxs-lookup"><span data-stu-id="35eda-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="35eda-128">Windows PowerShell visar det här meddelandet när en cmdlet körs och en obligatorisk parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="35eda-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="35eda-129">`HelpMessageBaseName` Valfritt med namnet parametern. Anger den plats där resursidentifierare finns.</span><span class="sxs-lookup"><span data-stu-id="35eda-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="35eda-130">Den här parametern kan till exempel ange en resurs sammansättning som innehåller hjälpmeddelanden som du vill lokalisera.</span><span class="sxs-lookup"><span data-stu-id="35eda-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="35eda-131">`HelpMessageResourceId` Valfritt med namnet parametern. Anger resurs-ID för ett hjälpmeddelande.</span><span class="sxs-lookup"><span data-stu-id="35eda-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="35eda-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="35eda-132">Remarks</span></span>

- <span data-ttu-id="35eda-133">Läs mer om hur du deklarera det här attributet [så deklarera Cmdlet-parametrarna](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="35eda-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="35eda-134">En cmdlet kan ha valfritt antal parametrar.</span><span class="sxs-lookup"><span data-stu-id="35eda-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="35eda-135">Dock begränsa antalet parametrar för en bättre användarupplevelse.</span><span class="sxs-lookup"><span data-stu-id="35eda-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="35eda-136">Parametrar måste deklareras i offentliga icke-statiska fält eller egenskaper.</span><span class="sxs-lookup"><span data-stu-id="35eda-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="35eda-137">Parametrar måste deklareras i egenskaper.</span><span class="sxs-lookup"><span data-stu-id="35eda-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="35eda-138">Egenskapen måste ha en offentlig uppsättning accessor och om den `ValueFromPipeline` eller `ValueFromPipelineByPropertyName` nyckelord har angetts, egenskapen måste ha en offentlig läsaccessor.</span><span class="sxs-lookup"><span data-stu-id="35eda-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="35eda-139">När du anger namngivna parametrar kan du begränsa antalet namngivna parametrar i en parameteruppsättning på mindre än fem.</span><span class="sxs-lookup"><span data-stu-id="35eda-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="35eda-140">Och namngivna parametrar behöver inte vara sammanhängande.</span><span class="sxs-lookup"><span data-stu-id="35eda-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="35eda-141">Positioner 5, 100 och 250 fungerar på samma sätt som positioner 0, 1 och 2.</span><span class="sxs-lookup"><span data-stu-id="35eda-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="35eda-142">När den `Position` nyckelordet inte anges, cmdlet-parameter måste refereras av dess namn.</span><span class="sxs-lookup"><span data-stu-id="35eda-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="35eda-143">När du använder parameteruppsättningar, Tänk på följande:</span><span class="sxs-lookup"><span data-stu-id="35eda-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="35eda-144">Varje parameteruppsättningen måste ha minst en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="35eda-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="35eda-145">Cmdlet: en bra design anger den här unika parametern också vara obligatorisk om möjligt.</span><span class="sxs-lookup"><span data-stu-id="35eda-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="35eda-146">Om din cmdlet: en är avsedd att köras utan parametrar, får inte unika parametern vara obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="35eda-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="35eda-147">Inga parameteruppsättningen ska innehålla mer än en namngivna parametern med samma plats.</span><span class="sxs-lookup"><span data-stu-id="35eda-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="35eda-148">Endast en parameter i en parameteruppsättning bör deklarera `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="35eda-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="35eda-149">Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="35eda-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="35eda-150">Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="35eda-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="35eda-151">Läs mer om riktlinjerna för parameternamn, [Cmdlet parameternamn](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="35eda-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="35eda-152">Parameterattributet definieras av den [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="35eda-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="35eda-153">Se även</span><span class="sxs-lookup"><span data-stu-id="35eda-153">See Also</span></span>

[<span data-ttu-id="35eda-154">System.Management.Automation.Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="35eda-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="35eda-155">Cmdlet-parameternamn</span><span class="sxs-lookup"><span data-stu-id="35eda-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="35eda-156">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="35eda-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
