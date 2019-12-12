---
title: Så här lägger du till dynamiska parametrar till en leverantörs hjälp avsnitt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353307"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="3e6aa-102">Lägga till dynamiska parametrar i ett hjälpavsnitt för providers</span><span class="sxs-lookup"><span data-stu-id="3e6aa-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="3e6aa-103">I det här avsnittet beskrivs hur du fyller i avsnittet **dynamiska parametrar** i en providers hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="3e6aa-104">*Dynamiska parametrar* är parametrar för en cmdlet eller funktion som endast är tillgängliga under angivna villkor.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="3e6aa-105">De dynamiska parametrar som dokumenteras i ett hjälp avsnitt om providern är de dynamiska parametrar som providern lägger till i cmdleten eller funktionen när-cmdleten eller-funktionen används i leverantörs enheten.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="3e6aa-106">Dynamiska parametrar kan också dokumenteras i anpassad cmdlet-hjälp för en provider.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="3e6aa-107">När du skriver både hjälpen för Provider och anpassad cmdlet-hjälp för en provider, inkluderar du den dynamiska parameter dokumentationen i båda dokumenten.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="3e6aa-108">Om en provider inte implementerar några dynamiska parametrar innehåller hjälp avsnittet Provider ett tomt `DynamicParameters`-element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="3e6aa-109">Lägga till dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="3e6aa-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="3e6aa-110">Lägg till ett `DynamicParameters`-element i `providerHelp`-elementet i filen *AssemblyName*. dll-Help. xml.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="3e6aa-111">`DynamicParameters`-elementet ska visas efter `Tasks`-elementet och före `RelatedLinks`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="3e6aa-112">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="3e6aa-112">For example:</span></span>

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

   <span data-ttu-id="3e6aa-113">Om providern inte implementerar några dynamiska parametrar kan `DynamicParameters`-elementet vara tomt.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="3e6aa-114">Lägg till ett `DynamicParameter`-element för varje dynamisk parameter i `DynamicParameters`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="3e6aa-115">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="3e6aa-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="3e6aa-116">I varje `DynamicParameter`-element lägger du till ett `Name`-och `CmdletSupported`-element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="3e6aa-117">Elementnamn</span><span class="sxs-lookup"><span data-stu-id="3e6aa-117">Element Name</span></span>|<span data-ttu-id="3e6aa-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3e6aa-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="3e6aa-119">Namn</span><span class="sxs-lookup"><span data-stu-id="3e6aa-119">Name</span></span>|<span data-ttu-id="3e6aa-120">Anger parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="3e6aa-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="3e6aa-121">CmdletSupported</span></span>|<span data-ttu-id="3e6aa-122">Anger cmdletarna där parametern är giltig.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="3e6aa-123">Ange en kommaavgränsad lista med cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="3e6aa-124">Till exempel är följande XML-dokument `Encoding` dynamiska parametern som Windows PowerShell-providern lägger till i `Add-Content``Get-Content``Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="3e6aa-125">I varje `DynamicParameter`-element lägger du till ett `Type`-element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="3e6aa-126">`Type`-elementet är en behållare för det `Name`-element som innehåller .NET-typen för den dynamiska parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="3e6aa-127">Följande XML visar till exempel att .NET-typen för parametern `Encoding` Dynamic är [Microsoft. PowerShell. commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -uppräkning.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="3e6aa-128">Lägg till `Description`-elementet som innehåller en kort beskrivning av den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="3e6aa-129">När du skriver beskrivningen använder du rikt linjerna för alla cmdlet-parametrar i [så här lägger du till parameter information](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="3e6aa-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="3e6aa-130">Följande XML innehåller till exempel en beskrivning av parametern `Encoding` Dynamic.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="3e6aa-131">Lägg till `PossibleValues`-elementet och dess underordnade element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="3e6aa-132">Tillsammans beskriver de här elementen värdena för den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="3e6aa-133">Det här elementet är utformat för uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="3e6aa-134">Om den dynamiska parametern inte tar ett värde, t. ex. är fallet med en växlings parameter, eller om värdena inte kan räknas upp, lägger du till ett tomt `PossibleValues`-element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="3e6aa-135">I följande tabell visas och beskrivs `PossibleValues`-elementet och dess underordnade element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="3e6aa-136">Elementnamn</span><span class="sxs-lookup"><span data-stu-id="3e6aa-136">Element Name</span></span>|<span data-ttu-id="3e6aa-137">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3e6aa-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="3e6aa-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="3e6aa-138">PossibleValues</span></span>|<span data-ttu-id="3e6aa-139">Det här elementet är en behållare.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-139">This element is a container.</span></span> <span data-ttu-id="3e6aa-140">De underordnade elementen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-140">Its child elements are described below.</span></span> <span data-ttu-id="3e6aa-141">Lägg till ett `PossibleValues`-element i varje leverantörs hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="3e6aa-142">Elementet kan vara tomt.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-142">The element can be empty.</span></span>|
   |<span data-ttu-id="3e6aa-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="3e6aa-143">PossibleValue</span></span>|<span data-ttu-id="3e6aa-144">Det här elementet är en behållare.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-144">This element is a container.</span></span> <span data-ttu-id="3e6aa-145">De underordnade elementen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-145">Its child elements are described below.</span></span> <span data-ttu-id="3e6aa-146">Lägg till ett `PossibleValue`-element för varje värde för den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="3e6aa-147">Värde</span><span class="sxs-lookup"><span data-stu-id="3e6aa-147">Value</span></span>|<span data-ttu-id="3e6aa-148">Anger värde namnet.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="3e6aa-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3e6aa-149">Description</span></span>|<span data-ttu-id="3e6aa-150">Det här elementet innehåller ett `Para`-element.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-150">This element contains a `Para` element.</span></span> <span data-ttu-id="3e6aa-151">Texten i `Para`-elementet beskriver det värde som namnges i `Value`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="3e6aa-152">Följande XML visar till exempel ett `PossibleValue`-element i parametern `Encoding` dynamisk.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="3e6aa-153">Exempel</span><span class="sxs-lookup"><span data-stu-id="3e6aa-153">Example</span></span>

<span data-ttu-id="3e6aa-154">I följande exempel visas `DynamicParameters`-elementet i parametern `Encoding` dynamisk.</span><span class="sxs-lookup"><span data-stu-id="3e6aa-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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