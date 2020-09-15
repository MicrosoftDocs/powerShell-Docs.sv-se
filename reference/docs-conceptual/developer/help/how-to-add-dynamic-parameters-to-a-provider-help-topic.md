---
title: Lägga till dynamiska parametrar i ett hjälpavsnitt för providers
ms.date: 09/13/2016
ms.openlocfilehash: ddf964292ee7bf477767a2ca17c717aef84bad51
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893466"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="f4037-102">Lägga till dynamiska parametrar i ett hjälpavsnitt för providers</span><span class="sxs-lookup"><span data-stu-id="f4037-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="f4037-103">I det här avsnittet beskrivs hur du fyller i avsnittet **dynamiska parametrar** i en providers hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="f4037-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="f4037-104">*Dynamiska parametrar* är parametrar för en cmdlet eller funktion som endast är tillgängliga under angivna villkor.</span><span class="sxs-lookup"><span data-stu-id="f4037-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="f4037-105">De dynamiska parametrar som dokumenteras i ett hjälp avsnitt om providern är de dynamiska parametrar som providern lägger till i cmdleten eller funktionen när-cmdleten eller-funktionen används i leverantörs enheten.</span><span class="sxs-lookup"><span data-stu-id="f4037-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="f4037-106">Dynamiska parametrar kan också dokumenteras i anpassad cmdlet-hjälp för en provider.</span><span class="sxs-lookup"><span data-stu-id="f4037-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="f4037-107">När du skriver både hjälpen för Provider och anpassad cmdlet-hjälp för en provider, inkluderar du den dynamiska parameter dokumentationen i båda dokumenten.</span><span class="sxs-lookup"><span data-stu-id="f4037-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="f4037-108">Om en provider inte implementerar några dynamiska parametrar innehåller leverantörens hjälp avsnitt ett tomt `DynamicParameters` element.</span><span class="sxs-lookup"><span data-stu-id="f4037-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="f4037-109">Lägga till dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="f4037-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="f4037-110">`<AssemblyName>.dll-help.xml` `providerHelp` Lägg till ett-element i-filen i-elementet `DynamicParameters` .</span><span class="sxs-lookup"><span data-stu-id="f4037-110">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="f4037-111">`DynamicParameters`Elementet ska visas efter `Tasks` elementet och före `RelatedLinks` elementet.</span><span class="sxs-lookup"><span data-stu-id="f4037-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="f4037-112">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f4037-112">For example:</span></span>

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

   <span data-ttu-id="f4037-113">Om providern inte implementerar några dynamiska parametrar `DynamicParameters` kan elementet vara tomt.</span><span class="sxs-lookup"><span data-stu-id="f4037-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="f4037-114">I `DynamicParameters` elementet lägger du till ett-element för varje dynamisk parameter `DynamicParameter` .</span><span class="sxs-lookup"><span data-stu-id="f4037-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="f4037-115">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f4037-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="f4037-116">I varje `DynamicParameter` element lägger du till ett `Name` och- `CmdletSupported` element.</span><span class="sxs-lookup"><span data-stu-id="f4037-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="f4037-117">Namn – anger parameter namnet</span><span class="sxs-lookup"><span data-stu-id="f4037-117">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="f4037-118">CmdletSupported – anger cmdletarna där parametern är giltig.</span><span class="sxs-lookup"><span data-stu-id="f4037-118">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="f4037-119">Ange en kommaavgränsad lista med cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="f4037-119">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="f4037-120">Till exempel innehåller följande XML-filer den `Encoding` dynamiska parametern som Windows PowerShell-filleverantören lägger till `Add-Content` i `Get-Content` `Set-Content` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="f4037-120">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="f4037-121">I varje `DynamicParameter` element lägger du till ett- `Type` element.</span><span class="sxs-lookup"><span data-stu-id="f4037-121">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="f4037-122">`Type`Elementet är en behållare för det `Name` element som innehåller .net-typen för den dynamiska parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="f4037-122">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="f4037-123">Till exempel visar följande XML att .NET-typen för den `Encoding` dynamiska parametern är [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="f4037-123">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

1. <span data-ttu-id="f4037-124">Lägg till `Description` elementet, som innehåller en kort beskrivning av den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="f4037-124">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="f4037-125">När du skriver beskrivningen använder du rikt linjerna för alla cmdlet-parametrar i [så här lägger du till parameter information](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="f4037-125">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="f4037-126">Till exempel innehåller följande XML en beskrivning av den `Encoding` dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="f4037-126">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

1. <span data-ttu-id="f4037-127">Lägg till `PossibleValues` elementet och dess underordnade element.</span><span class="sxs-lookup"><span data-stu-id="f4037-127">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="f4037-128">Tillsammans beskriver de här elementen värdena för den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="f4037-128">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="f4037-129">Det här elementet är utformat för uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="f4037-129">This element is designed for enumerated values.</span></span> <span data-ttu-id="f4037-130">Om den dynamiska parametern inte tar ett värde, t. ex. är fallet med en växlings parameter, eller om värdena inte kan räknas upp, lägger du till ett tomt `PossibleValues` element.</span><span class="sxs-lookup"><span data-stu-id="f4037-130">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="f4037-131">I följande tabell visas och beskrivs `PossibleValues` elementet och dess underordnade element.</span><span class="sxs-lookup"><span data-stu-id="f4037-131">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="f4037-132">PossibleValues – det här elementet är en behållare.</span><span class="sxs-lookup"><span data-stu-id="f4037-132">PossibleValues - This element is a container.</span></span> <span data-ttu-id="f4037-133">De underordnade elementen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="f4037-133">Its child elements are described below.</span></span> <span data-ttu-id="f4037-134">Lägg till ett `PossibleValues` element i varje leverantörs hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="f4037-134">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="f4037-135">Elementet kan vara tomt.</span><span class="sxs-lookup"><span data-stu-id="f4037-135">The element can be empty.</span></span>
   - <span data-ttu-id="f4037-136">PossibleValue – det här elementet är en behållare.</span><span class="sxs-lookup"><span data-stu-id="f4037-136">PossibleValue - This element is a container.</span></span> <span data-ttu-id="f4037-137">De underordnade elementen beskrivs nedan.</span><span class="sxs-lookup"><span data-stu-id="f4037-137">Its child elements are described below.</span></span> <span data-ttu-id="f4037-138">Lägg till ett- `PossibleValue` element för varje värde för den dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="f4037-138">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="f4037-139">Value-anger värde namnet.</span><span class="sxs-lookup"><span data-stu-id="f4037-139">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="f4037-140">Beskrivning – Det här elementet innehåller ett- `Para` element.</span><span class="sxs-lookup"><span data-stu-id="f4037-140">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="f4037-141">Texten i `Para` elementet beskriver det värde som namnges i `Value` elementet.</span><span class="sxs-lookup"><span data-stu-id="f4037-141">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="f4037-142">I följande XML visas till exempel ett `PossibleValue` element i den `Encoding` dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="f4037-142">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="f4037-143">Exempel</span><span class="sxs-lookup"><span data-stu-id="f4037-143">Example</span></span>

<span data-ttu-id="f4037-144">I följande exempel visas `DynamicParameters` elementet i den `Encoding` dynamiska parametern.</span><span class="sxs-lookup"><span data-stu-id="f4037-144">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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
