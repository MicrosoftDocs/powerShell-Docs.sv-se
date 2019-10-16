---
title: Så här lägger du till syntax i ett hjälp avsnitt för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353272"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="7ccd6-102">Lägga till syntax till ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="7ccd6-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7ccd6-103">Innan du börjar koda XML för syntax-diagrammet i cmdlet-hjälpen läser du det här avsnittet för att få en tydlig bild av den typ av data som du behöver ange, till exempel parameter-attribut och hur dessa data visas i syntax diagrammet.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="7ccd6-104">Parameter-attribut</span><span class="sxs-lookup"><span data-stu-id="7ccd6-104">Parameter Attributes</span></span>

- <span data-ttu-id="7ccd6-105">Obligatorisk</span><span class="sxs-lookup"><span data-stu-id="7ccd6-105">Required</span></span>

  - <span data-ttu-id="7ccd6-106">Om värdet är true måste parametern visas i alla kommandon som använder parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="7ccd6-107">Om värdet är false är parametern valfri i alla kommandon som använder parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="7ccd6-108">Position</span><span class="sxs-lookup"><span data-stu-id="7ccd6-108">Position</span></span>

  - <span data-ttu-id="7ccd6-109">Parameter namnet krävs om det har angetts.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="7ccd6-110">Parameter namnet är valfritt om det är placerat.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="7ccd6-111">När den utelämnas måste parametervärdet vara i den angivna positionen i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="7ccd6-112">Om värdet till exempel är position = "1" måste parametervärdet vara det första eller enda parameter värde som inte är namn i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="7ccd6-113">Pipeline-inmatade</span><span class="sxs-lookup"><span data-stu-id="7ccd6-113">Pipeline Input</span></span>

  - <span data-ttu-id="7ccd6-114">Om värdet är true (ByValue) kan du skicka pipe-information till-parametern.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="7ccd6-115">Indatamängden är associerad med ("bind till") parametern även om egenskaps namnet och objekt typen inte matchar den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="7ccd6-116">Windows PowerShell? med parameter bindnings komponenter försöker du konvertera inmatarna till rätt typ och växlar kommandot endast när det inte går att konvertera typen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="7ccd6-117">Endast en parameter i en parameter uppsättning kan associeras med värde.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="7ccd6-118">Om värdet är true (ByPropertyName) kan du skicka pipe-information till-parametern.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="7ccd6-119">Inmatarna är dock bara kopplade till parametern när parameter namnet matchar namnet på en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="7ccd6-120">Om parameter namnet till exempel är `Path`, associeras objekt skickas till cmdleten endast när objektet har en egenskap med namnet Path.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="7ccd6-121">Om det här värdet är sant (ByValue, ByPropertyName) kan du skicka pipe-värden till-parametern med egenskaps namn eller värde.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="7ccd6-122">Endast en parameter i en parameter uppsättning kan associeras med värde.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="7ccd6-123">Om det här värdet är falskt kan du inte skicka vidare inmatade parametrar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="7ccd6-124">Globbing</span><span class="sxs-lookup"><span data-stu-id="7ccd6-124">Globbing</span></span>

  - <span data-ttu-id="7ccd6-125">Om det här värdet är sant kan texten som användar typerna för parametervärdet innehålla jokertecken.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="7ccd6-126">Om värdet är false får inte texten som användar typerna för parametervärdet innehålla jokertecken.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="7ccd6-127">Attribut för parameter värde</span><span class="sxs-lookup"><span data-stu-id="7ccd6-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="7ccd6-128">Obligatorisk</span><span class="sxs-lookup"><span data-stu-id="7ccd6-128">Required</span></span>

  - <span data-ttu-id="7ccd6-129">Om värdet är true måste det angivna värdet användas när parametern i ett kommando används.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="7ccd6-130">Om värdet är false är parametervärdet valfritt.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="7ccd6-131">Normalt är ett värde bara valfritt när det är ett av flera giltiga värden för en parameter, till exempel i en uppräknings typ.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="7ccd6-132">Attributet som krävs för ett parameter värde skiljer sig från det obligatoriska attributet för en parameter.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="7ccd6-133">Attributet som krävs för en parameter anger om parametern (och dess värde) måste tas med vid anrop av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="7ccd6-134">Däremot används det obligatoriska attributet för ett parameter värde bara när parametern ingår i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="7ccd6-135">Det anger om detta specifika värde måste användas med parametern.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="7ccd6-136">Vanligt vis krävs parameter värden som är plats hållare och parameter värden som är literala krävs inte, eftersom de är ett av flera värden som kan användas med parametern.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="7ccd6-137">Samlar in Syntaxs information</span><span class="sxs-lookup"><span data-stu-id="7ccd6-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="7ccd6-138">Börja med cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="7ccd6-139">Visa en lista med alla parametrar för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="7ccd6-140">Skriv ett bindestreck (kallas även "bindestreck" eller "minus tecken" (ASCII 45) före varje parameter namn.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="7ccd6-141">Avgränsa parametrarna i parameter uppsättningar (vissa cmdletar får bara ha en parameter uppsättning).</span><span class="sxs-lookup"><span data-stu-id="7ccd6-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="7ccd6-142">I det här exemplet har get-Tech-cmdleten två parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="7ccd6-143">Starta varje parameter uppsättning med cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="7ccd6-144">Visa en lista med standard parameter uppsättningen först.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-144">List the default parameter set first.</span></span> <span data-ttu-id="7ccd6-145">Standard parametern anges av cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="7ccd6-146">För varje parameter uppsättning måste du först ange en unik parameter, såvida det inte finns några positions parametrar som måste visas först.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="7ccd6-147">I föregående exempel är namn-och ID-parametrarna unika parametrar för de två parameter uppsättningarna (varje parameter uppsättning måste ha en parameter som är unik för den parameter uppsättningen).</span><span class="sxs-lookup"><span data-stu-id="7ccd6-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="7ccd6-148">Detta gör det enklare för användarna att identifiera vilken parameter de behöver ange för parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="7ccd6-149">Visa en lista med parametrarna i den ordning som de ska visas i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="7ccd6-150">Om ordningen inte spelar någon roll, visar en lista över relaterade parametrar tillsammans eller listar de mest använda parametrarna först.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="7ccd6-151">Se till att ange parametrarna WhatIf och Confirm om cmdleten stöder ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="7ccd6-152">Visa inte vanliga parametrar (till exempel verbose, debug och ErrorAction) i ditt syntax-diagram.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="7ccd6-153">@No__t-0-cmdleten lägger till den informationen åt dig när hjälp avsnittet visas.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="7ccd6-154">Lägg till parameter värden.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-154">Add the parameter values.</span></span> <span data-ttu-id="7ccd6-155">I Windows PowerShell? representeras parameter värden av deras .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="7ccd6-156">Typ namnet kan dock förkortas, till exempel "String" för system. String.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="7ccd6-157">Förkorta typer så länge deras innebörd är klar, till exempel "String" för system. String och "int" för system. Int32.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="7ccd6-158">Lista alla värden för uppräkningar, till exempel parametern-type i föregående exempel, som kan anges till "Basic" eller "Advanced".</span><span class="sxs-lookup"><span data-stu-id="7ccd6-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="7ccd6-159">Växla parametrar, t. ex. en lista i föregående exempel, saknar värden.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="7ccd6-160">Lägg till vinkelparenteser i parameter värden som är plats hållare, jämfört med parameter värden som är litteraler.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="7ccd6-161">Omge valfria parametrar och deras Vales inom hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="7ccd6-162">Omge valfria parameter namn (för positions parametrar) inom hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="7ccd6-163">Namnet på parametrar som är placerat, till exempel parametern name i följande exempel, behöver inte inkluderas i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="7ccd6-164">Om ett parameter värde kan innehålla flera värden, till exempel en lista med namn i parametern name, lägger du till ett par hakparenteser direkt efter parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="7ccd6-165">Om användaren kan välja bland parametrar eller parameter värden, t. ex. typ parameter, omger du valen i hakparenteser och avgränsar dem med den exklusiva eller symbolen (;).</span><span class="sxs-lookup"><span data-stu-id="7ccd6-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="7ccd6-166">Om parametervärdet måste använda en speciell formatering, t. ex. citat tecken eller parenteser, visar du formatet i syntaxen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="7ccd6-167">Koda XML för syntax diagram</span><span class="sxs-lookup"><span data-stu-id="7ccd6-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="7ccd6-168">Nodens syntax i XML-koden börjar omedelbart efter noden Description, som slutar med taggen \</MAML: Beskrivning >.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="7ccd6-169">Information om hur du samlar in data som används i syntax-diagrammet finns i [samla in syntax information](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="7ccd6-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="7ccd6-170">Lägga till en syntax-nod</span><span class="sxs-lookup"><span data-stu-id="7ccd6-170">Adding a Syntax Node</span></span>

<span data-ttu-id="7ccd6-171">Det syntax diagram som visas i hjälp avsnittet om cmdleten genereras från data i noden syntax i XML-koden.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="7ccd6-172">Noden syntax omges av ett par om \<command: syntax > taggar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="7ccd6-173">Med varje parameter uppsättning i cmdleten som anges i ett par med \<command: syntaxitem >-taggar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="7ccd6-174">Det finns ingen gräns för antalet \<command: syntaxitem >-taggar som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="7ccd6-175">I följande exempel visas en syntax-nod som innehåller noder för syntaxfel för två parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="7ccd6-176">Lägga till cmdlet-namnet i parameter uppsättnings data</span><span class="sxs-lookup"><span data-stu-id="7ccd6-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="7ccd6-177">Varje parameter uppsättning i cmdleten anges i en nod för ett syntax-objekt.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="7ccd6-178">Varje syntax-Artikelnod börjar med ett par med \<maml: Name >-taggar som innehåller namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="7ccd6-179">I följande exempel finns en syntax-nod som innehåller noder för kommandosyntaxen för två parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="7ccd6-180">Parametrar läggs till</span><span class="sxs-lookup"><span data-stu-id="7ccd6-180">Adding Parameters</span></span>

<span data-ttu-id="7ccd6-181">Varje parameter som läggs till i syntax-noden anges i ett par med \<command: parameter > taggar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="7ccd6-182">Du behöver ett par med \<command: parameter > taggar för varje parameter som ingår i parameter uppsättningen, med undantag för de gemensamma parametrar som tillhandahålls av Windows PowerShell?.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="7ccd6-183">Attributen för den inledande \<command: parametern > tag anger hur parametern visas i syntax-diagrammet.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="7ccd6-184">Information om parameter-attribut finns i [parameter-attribut](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="7ccd6-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="7ccd6-185">Parametern \<command: parameter > stöder ett underordnat element \<maml: Description > vars innehåll aldrig visas.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="7ccd6-186">Parameter beskrivningar anges i noden parameter i XML-filen.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="7ccd6-187">Undvik inkonsekvenser mellan informationen i Bodes och noden parameter genom att utelämna (\<maml: Description > eller lämna det tomt.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="7ccd6-188">I följande exempel finns en nod för sökobjekt för en parameter uppsättning med två parametrar.</span><span class="sxs-lookup"><span data-stu-id="7ccd6-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
