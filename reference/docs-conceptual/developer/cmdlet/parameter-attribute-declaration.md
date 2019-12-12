---
title: Deklaration av parameter-attribut | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356177"
---
# <a name="parameter-attribute-declaration"></a><span data-ttu-id="5053a-102">Deklaration av attributet Parameter</span><span class="sxs-lookup"><span data-stu-id="5053a-102">Parameter Attribute Declaration</span></span>

<span data-ttu-id="5053a-103">Attributet parameter identifierar en offentlig egenskap för cmdlet-klassen som en cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-103">The Parameter attribute identifies a public property of the cmdlet class as a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="5053a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5053a-104">Syntax</span></span>

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="5053a-105">Parametrar</span><span class="sxs-lookup"><span data-stu-id="5053a-105">Parameters</span></span>

<span data-ttu-id="5053a-106">`Mandatory` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-106">`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5053a-107">`True` anger att cmdlet-parametern krävs.</span><span class="sxs-lookup"><span data-stu-id="5053a-107">`True` indicates the cmdlet parameter is required.</span></span> <span data-ttu-id="5053a-108">Om en obligatorisk parameter inte anges när cmdleten anropas, uppmanas användaren att ange ett parameter värde i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5053a-108">If a required parameter is not provided when the cmdlet is invoked, Windows PowerShell prompts the user for a parameter value.</span></span> <span data-ttu-id="5053a-109">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="5053a-109">The default is `false`.</span></span>

<span data-ttu-id="5053a-110">`ParameterSetName` ([system. String](/dotnet/api/System.String)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-110">`ParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="5053a-111">Anger den parameter uppsättning som denna cmdlet-parameter tillhör.</span><span class="sxs-lookup"><span data-stu-id="5053a-111">Specifies the parameter set that this cmdlet parameter belongs to.</span></span> <span data-ttu-id="5053a-112">Om ingen parameter uppsättning anges tillhör parametern alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="5053a-112">If no parameter set is specified, the parameter belongs to all parameter sets.</span></span>

<span data-ttu-id="5053a-113">`Position` ([system. Int32](/dotnet/api/System.Int32)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-113">`Position` ([System.Int32](/dotnet/api/System.Int32)) Optional named parameter.</span></span> <span data-ttu-id="5053a-114">Anger positionen för parametern i ett Windows PowerShell-kommando.</span><span class="sxs-lookup"><span data-stu-id="5053a-114">Specifies the position of the parameter within a Windows PowerShell command.</span></span>

<span data-ttu-id="5053a-115">`ValueFromPipeline` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-115">`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5053a-116">`True` anger att cmdlet-parametern tar sitt värde från ett pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="5053a-116">`True` indicates that the cmdlet parameter takes its value from a pipeline object.</span></span> <span data-ttu-id="5053a-117">Ange det här nyckelordet om cmdleten har åtkomst till det fullständiga objektet, inte bara en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="5053a-117">Specify this keyword if the cmdlet accesses the complete object, not just a property of the object.</span></span> <span data-ttu-id="5053a-118">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="5053a-118">The default is `false`.</span></span>

<span data-ttu-id="5053a-119">`ValueFromPipelineByPropertyName` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-119">`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5053a-120">`True` anger att cmdlet-parametern tar värdet från en egenskap för ett pipeline-objekt som har antingen samma namn eller samma alias som denna parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-120">`True` indicates that the cmdlet parameter takes its value from a property of a pipeline object that has either the same name or the same alias as this parameter.</span></span> <span data-ttu-id="5053a-121">Om till exempel cmdleten har en `Name`-parameter och pipelinen också har en `Name` egenskap, tilldelas värdet för egenskapen `Name` till `Name`-parametern för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5053a-121">For example, if the cmdlet has a `Name` parameter and the pipeline object also has a `Name` property, the value of the `Name` property is assigned to the `Name` parameter of the cmdlet.</span></span> <span data-ttu-id="5053a-122">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="5053a-122">The default is `false`.</span></span>

<span data-ttu-id="5053a-123">`ValueFromRemainingArguments` ([system. Boolean](/dotnet/api/System.Boolean)) valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-123">`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5053a-124">`True` anger att cmdlet-parametern accepterar alla återstående argument som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5053a-124">`True` indicates that the cmdlet parameter accepts all remaining arguments that are passed to the cmdlet.</span></span> <span data-ttu-id="5053a-125">Standardvärdet är `false`.</span><span class="sxs-lookup"><span data-stu-id="5053a-125">The default is `false`.</span></span>

<span data-ttu-id="5053a-126">`HelpMessage` valfri namngiven parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-126">`HelpMessage` Optional named parameter.</span></span> <span data-ttu-id="5053a-127">Anger en kort beskrivning av parametern.</span><span class="sxs-lookup"><span data-stu-id="5053a-127">Specifies a short description of the parameter.</span></span> <span data-ttu-id="5053a-128">Windows PowerShell visar det här meddelandet när en cmdlet körs och en obligatorisk parameter inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="5053a-128">Windows PowerShell displays this message when a cmdlet is run and a mandatory parameter is not specified.</span></span>

<span data-ttu-id="5053a-129">`HelpMessageBaseName` valfri namngiven parameter. Anger den plats där resurs identifierare finns.</span><span class="sxs-lookup"><span data-stu-id="5053a-129">`HelpMessageBaseName` Optional named parameter.Specifies the location where resource identifiers reside.</span></span> <span data-ttu-id="5053a-130">Den här parametern kan till exempel ange en resurs sammansättning som innehåller hjälp meddelanden som du vill lokalisera.</span><span class="sxs-lookup"><span data-stu-id="5053a-130">For example, this parameter could specify a resource assembly that contains Help messages that you want to localize.</span></span>

<span data-ttu-id="5053a-131">`HelpMessageResourceId` valfri namngiven parameter. Anger resurs-ID för ett hjälp meddelande.</span><span class="sxs-lookup"><span data-stu-id="5053a-131">`HelpMessageResourceId` Optional named parameter.Specifies the resource identifier for a Help message.</span></span>

## <a name="remarks"></a><span data-ttu-id="5053a-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5053a-132">Remarks</span></span>

- <span data-ttu-id="5053a-133">Mer information om hur du deklarerar det här attributet finns i [så här deklarerar du cmdlet-parametrar](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="5053a-133">For more information about how to declare this attribute, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="5053a-134">En cmdlet kan ha valfritt antal parametrar.</span><span class="sxs-lookup"><span data-stu-id="5053a-134">A cmdlet can have any number of parameters.</span></span> <span data-ttu-id="5053a-135">För en bättre användar upplevelse begränsar du dock antalet parametrar.</span><span class="sxs-lookup"><span data-stu-id="5053a-135">However, for a better user experience, limit the number of parameters.</span></span>

- <span data-ttu-id="5053a-136">Parametrar måste deklareras för offentliga fält eller egenskaper som inte är statiska.</span><span class="sxs-lookup"><span data-stu-id="5053a-136">Parameters must be declared on public non-static fields or properties.</span></span> <span data-ttu-id="5053a-137">Parametrar ska deklareras för egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5053a-137">Parameters should be declared on properties.</span></span> <span data-ttu-id="5053a-138">Egenskapen måste ha en offentlig set-accessor och om nyckelordet `ValueFromPipeline` eller `ValueFromPipelineByPropertyName` har angetts måste egenskapen ha en offentlig get-accessor.</span><span class="sxs-lookup"><span data-stu-id="5053a-138">The property must have a public set accessor, and if the `ValueFromPipeline` or `ValueFromPipelineByPropertyName` keyword is specified, the property must have a public get accessor.</span></span>

- <span data-ttu-id="5053a-139">Om du anger positions parametrar begränsar du antalet positions parametrar i en parameter till mindre än fem.</span><span class="sxs-lookup"><span data-stu-id="5053a-139">When you specify positional parameters,  limit the number of positional parameters in a parameter set to less than five.</span></span> <span data-ttu-id="5053a-140">Positions parametrar behöver inte vara sammanhängande.</span><span class="sxs-lookup"><span data-stu-id="5053a-140">And, positional parameters do not have to be contiguous.</span></span> <span data-ttu-id="5053a-141">Positionerna 5, 100 och 250 fungerar på samma sätt som positionerna 0, 1 och 2.</span><span class="sxs-lookup"><span data-stu-id="5053a-141">Positions 5, 100, and 250 work the same as positions 0, 1, and 2.</span></span>

- <span data-ttu-id="5053a-142">Om nyckelordet `Position` inte anges måste cmdlet-parametern refereras till med dess namn.</span><span class="sxs-lookup"><span data-stu-id="5053a-142">When the `Position` keyword is not specified, the cmdlet parameter must be referenced by its name.</span></span>

- <span data-ttu-id="5053a-143">Tänk på följande när du använder parameter uppsättningar:</span><span class="sxs-lookup"><span data-stu-id="5053a-143">When you use parameter sets, note the following:</span></span>

    - <span data-ttu-id="5053a-144">Varje parameter uppsättning måste ha minst en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="5053a-144">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="5053a-145">Design av lämplig cmdlet anger att den här unika parametern också bör vara obligatorisk om möjligt.</span><span class="sxs-lookup"><span data-stu-id="5053a-145">Good cmdlet design indicates this unique parameter should also be mandatory if possible.</span></span> <span data-ttu-id="5053a-146">Om cmdleten har utformats för att köras utan parametrar kan den unika parametern inte vara obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="5053a-146">If your cmdlet is designed to be run without parameters, the unique parameter cannot be mandatory.</span></span>

    - <span data-ttu-id="5053a-147">Ingen parameter uppsättning måste innehålla mer än en positions parameter med samma position.</span><span class="sxs-lookup"><span data-stu-id="5053a-147">No parameter set should contain more than one positional parameter with the same position.</span></span>

    - <span data-ttu-id="5053a-148">Endast en parameter i en parameter uppsättning bör deklarera `ValueFromPipeline = true`.</span><span class="sxs-lookup"><span data-stu-id="5053a-148">Only one parameter in a parameter set should declare `ValueFromPipeline = true`.</span></span> <span data-ttu-id="5053a-149">Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="5053a-149">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

    - <span data-ttu-id="5053a-150">Flera parametrar kan definiera `ValueFromPipelineByPropertyName = true`.</span><span class="sxs-lookup"><span data-stu-id="5053a-150">Multiple parameters can define `ValueFromPipelineByPropertyName = true`.</span></span>

- <span data-ttu-id="5053a-151">Mer information om rikt linjerna för parameter namn finns i [cmdlet parameter Names](standard-cmdlet-parameter-names-and-types.md).</span><span class="sxs-lookup"><span data-stu-id="5053a-151">For more information about the guidelines for parameter names, see [Cmdlet Parameter Names](standard-cmdlet-parameter-names-and-types.md).</span></span>

- <span data-ttu-id="5053a-152">Attributet parameter definieras av klassen [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) .</span><span class="sxs-lookup"><span data-stu-id="5053a-152">The parameter attribute is defined by the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5053a-153">Se även</span><span class="sxs-lookup"><span data-stu-id="5053a-153">See Also</span></span>

[<span data-ttu-id="5053a-154">System. Management. Automation. Parameterattribute</span><span class="sxs-lookup"><span data-stu-id="5053a-154">System.Management.Automation.Parameterattribute</span></span>](/dotnet/api/System.Management.Automation.ParameterAttribute)

[<span data-ttu-id="5053a-155">Parameter namn för cmdlet</span><span class="sxs-lookup"><span data-stu-id="5053a-155">Cmdlet Parameter Names</span></span>](standard-cmdlet-parameter-names-and-types.md)

[<span data-ttu-id="5053a-156">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5053a-156">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
