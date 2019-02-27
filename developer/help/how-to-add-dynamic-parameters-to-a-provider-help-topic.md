---
title: Lägga till dynamiska parametrar i ett hjälpavsnitt för providern | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849527"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="030d4-102">Lägga till dynamiska parametrar i ett hjälpavsnitt för providers</span><span class="sxs-lookup"><span data-stu-id="030d4-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="030d4-103">Det här avsnittet beskrivs hur du fyller i **dynamiska parametrar** delen av ett hjälpavsnitt för providern.</span><span class="sxs-lookup"><span data-stu-id="030d4-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="030d4-104">*Dynamiska parametrar* är parametrarna för en cmdlet eller funktion som är tillgängliga endast under angivna villkor.</span><span class="sxs-lookup"><span data-stu-id="030d4-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="030d4-105">De dynamiska parametrar som finns dokumenterade i ett hjälpavsnitt för providern är dynamiska parametrar som providern lägger till cmdlet eller funktion när cmdlet eller funktionen används i provider-enheten.</span><span class="sxs-lookup"><span data-stu-id="030d4-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="030d4-106">Dynamiska parametrar kan också dokumenterade i anpassade cmdlet-hjälpen för en provider.</span><span class="sxs-lookup"><span data-stu-id="030d4-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="030d4-107">När du skriver både providern hjälp och anpassade cmdlet-hjälpen för en provider ska inkludera den dynamiska parameter-dokumentationen i båda dokumenten.</span><span class="sxs-lookup"><span data-stu-id="030d4-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="030d4-108">Mer information om anpassade cmdlet-hjälpen finns i [skriva Windows PowerShell anpassade Cmdlet-hjälp för leverantörer av](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="030d4-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="030d4-109">Om en provider inte implementerar några dynamiska parametrar, provider hjälpavsnitt innehåller en tom `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="030d4-110">Att lägga till dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="030d4-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="030d4-111">I den *AssemblyName*.dll-help.xml filen i den `providerHelp` element, lägga till en `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="030d4-112">Den `DynamicParameters` element visas efter den `Tasks` elementet och innan den `RelatedLinks` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="030d4-113">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="030d4-113">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="030d4-114">Om leverantören inte implementerar alla dynamiska parametrar, den `DynamicParameters` elementet kan vara tomt.</span><span class="sxs-lookup"><span data-stu-id="030d4-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="030d4-115">I den `DynamicParameters` element för varje dynamisk parameter, lägga till en `DynamicParameter` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="030d4-116">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="030d4-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="030d4-117">I varje `DynamicParameter` element, lägga till en `Name` och `CmdletSupported` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="030d4-118">Elementnamn</span><span class="sxs-lookup"><span data-stu-id="030d4-118">Element Name</span></span>|<span data-ttu-id="030d4-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="030d4-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="030d4-120">Namn</span><span class="sxs-lookup"><span data-stu-id="030d4-120">Name</span></span>|<span data-ttu-id="030d4-121">Anger parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="030d4-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="030d4-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="030d4-122">CmdletSupported</span></span>|<span data-ttu-id="030d4-123">Anger de cmdletar som parametern är giltig.</span><span class="sxs-lookup"><span data-stu-id="030d4-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="030d4-124">Ange en kommaavgränsad lista med cmdlet-namnen.</span><span class="sxs-lookup"><span data-stu-id="030d4-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="030d4-125">Till exempel följande XML-dokument i `Encoding` dynamisk parameter som filsystem för Windows PowerShell-providern lägger till i den `Add-Content`, `Get-Content`, `Set-Content` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="030d4-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="030d4-126">I varje `DynamicParameter` element, lägga till en `Type` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="030d4-127">Den `Type` element är en behållare för de `Name` element som innehåller .NET-typ av värdet för den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="030d4-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="030d4-128">Visar till exempel följande XML som .NET-typ av den `Encoding` dynamisk parameter är den [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) uppräkning.</span><span class="sxs-lookup"><span data-stu-id="030d4-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="030d4-129">Lägg till den `Description` element som innehåller en kort beskrivning av den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="030d4-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="030d4-130">När du skriver beskrivningen, Använd riktlinjer föreskrivs för alla cmdlet-parametrarna i [hur du lägger till parameterinformation](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="030d4-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="030d4-131">Följande XML-filen innehåller till exempel en beskrivning av den `Encoding` dynamisk parameter.</span><span class="sxs-lookup"><span data-stu-id="030d4-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="030d4-132">Lägg till den `PossibleValues` elementet och dess underordnade element.</span><span class="sxs-lookup"><span data-stu-id="030d4-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="030d4-133">De här elementen beskrivs tillsammans värden för den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="030d4-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="030d4-134">Det här elementet har utformats för uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="030d4-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="030d4-135">Om den dynamiska parametern inte tar ett värde, som är fallet med en switchparameter eller går inte att räkna upp värdena, lägga till en tom `PossibleValues` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="030d4-136">I följande tabell visas och beskrivs de `PossibleValues` elementet och dess underordnade element.</span><span class="sxs-lookup"><span data-stu-id="030d4-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="030d4-137">Elementnamn</span><span class="sxs-lookup"><span data-stu-id="030d4-137">Element Name</span></span>|<span data-ttu-id="030d4-138">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="030d4-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="030d4-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="030d4-139">PossibleValues</span></span>|<span data-ttu-id="030d4-140">Det här elementet är en behållare.</span><span class="sxs-lookup"><span data-stu-id="030d4-140">This element is a container.</span></span> <span data-ttu-id="030d4-141">De underordnade elementen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="030d4-141">Its child elements are described below.</span></span> <span data-ttu-id="030d4-142">Lägg till en `PossibleValues` elementet så att varje hjälpavsnitt för providern.</span><span class="sxs-lookup"><span data-stu-id="030d4-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="030d4-143">Elementet kan vara tom.</span><span class="sxs-lookup"><span data-stu-id="030d4-143">The element can be empty.</span></span>|
   |<span data-ttu-id="030d4-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="030d4-144">PossibleValue</span></span>|<span data-ttu-id="030d4-145">Det här elementet är en behållare.</span><span class="sxs-lookup"><span data-stu-id="030d4-145">This element is a container.</span></span> <span data-ttu-id="030d4-146">De underordnade elementen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="030d4-146">Its child elements are described below.</span></span> <span data-ttu-id="030d4-147">Lägg till en `PossibleValue` element för varje värde i den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="030d4-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="030d4-148">Värde</span><span class="sxs-lookup"><span data-stu-id="030d4-148">Value</span></span>|<span data-ttu-id="030d4-149">Anger värdenamnet.</span><span class="sxs-lookup"><span data-stu-id="030d4-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="030d4-150">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="030d4-150">Description</span></span>|<span data-ttu-id="030d4-151">Det här elementet innehåller ett `Para` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-151">This element contains a `Para` element.</span></span> <span data-ttu-id="030d4-152">Texten i den `Para` element beskriver värdet med namnet i den `Value` element.</span><span class="sxs-lookup"><span data-stu-id="030d4-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="030d4-153">Följande XML visar exempelvis en `PossibleValue` elementet i den `Encoding` dynamisk parameter.</span><span class="sxs-lookup"><span data-stu-id="030d4-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="030d4-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="030d4-154">Example</span></span>

<span data-ttu-id="030d4-155">I följande exempel visas den `DynamicParameters` elementet i den `Encoding` dynamisk parameter.</span><span class="sxs-lookup"><span data-stu-id="030d4-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```