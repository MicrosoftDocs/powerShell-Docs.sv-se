---
title: Lägga till Syntax i en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 947d0c0188df5bba3a9fb617fe5abf0b3b28eb51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848211"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="15534-102">Lägga till syntax till ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="15534-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="15534-103">Parameterattribut</span><span class="sxs-lookup"><span data-stu-id="15534-103">Parameter Attributes</span></span>](#Parameter-Attributes)

- [<span data-ttu-id="15534-104">Parameterattribut värde</span><span class="sxs-lookup"><span data-stu-id="15534-104">Parameter Value Attributes</span></span>](#Parameter-Value-Attributes)

- [<span data-ttu-id="15534-105">Samla Information om Syntax</span><span class="sxs-lookup"><span data-stu-id="15534-105">Gathering Syntax Information</span></span>](#Gathering-Syntax-Information)

- [<span data-ttu-id="15534-106">Koda Syntaxdiagrammet XML</span><span class="sxs-lookup"><span data-stu-id="15534-106">Coding the Syntax Diagram XML</span></span>](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a><span data-ttu-id="15534-107">Att känna till om Syntaxdiagrammet i Cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="15534-107">Things to Know About the Syntax Diagram in Cmdlet Help</span></span>

<span data-ttu-id="15534-108">Innan du börjar koda XML för syntaxdiagrammet i hjälpfilen cmdlet Läs det här avsnittet för att få en tydlig bild av typ av data som du måste ange, till exempel parameterattribut och hur dessa data visas i syntaxdiagrammet...</span><span class="sxs-lookup"><span data-stu-id="15534-108">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="15534-109">Parameterattribut</span><span class="sxs-lookup"><span data-stu-id="15534-109">Parameter Attributes</span></span>

- <span data-ttu-id="15534-110">Obligatorisk</span><span class="sxs-lookup"><span data-stu-id="15534-110">Required</span></span>

  - <span data-ttu-id="15534-111">Om värdet är true måste parametern visas i alla kommandon som använder parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="15534-111">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="15534-112">Parametern är valfri i alla kommandon som använder parameteruppsättningen om värdet är false.</span><span class="sxs-lookup"><span data-stu-id="15534-112">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="15534-113">Position</span><span class="sxs-lookup"><span data-stu-id="15534-113">Position</span></span>

  - <span data-ttu-id="15534-114">Om namnet, krävs parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="15534-114">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="15534-115">Om det namngivna, är parameternamnet valfritt.</span><span class="sxs-lookup"><span data-stu-id="15534-115">If positional, the parameter name is optional.</span></span> <span data-ttu-id="15534-116">Om det utelämnas måste parametervärdet vara i den angivna positionen i kommandot.</span><span class="sxs-lookup"><span data-stu-id="15534-116">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="15534-117">Till exempel om värdet är position = ”1”, parametervärdet måste vara den första eller enda icke namngivna parametervärdet i kommandot.</span><span class="sxs-lookup"><span data-stu-id="15534-117">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="15534-118">Pipeline-indata</span><span class="sxs-lookup"><span data-stu-id="15534-118">Pipeline Input</span></span>

  - <span data-ttu-id="15534-119">Om värdet är true (ByValue), du kan skicka vidare indata till parametern.</span><span class="sxs-lookup"><span data-stu-id="15534-119">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="15534-120">Indata är associerad med (”gränsvärde till”) parametern även om egenskapsnamnet och typen av objekt som inte matchar den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="15534-120">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="15534-121">Windows PowerShell? Parametern bindning komponenter försök att konvertera indata till rätt typ och misslyckas kommandot endast när den inte kan konverteras.</span><span class="sxs-lookup"><span data-stu-id="15534-121">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="15534-122">Endast en parameter i en parameteruppsättning kan associeras med värde.</span><span class="sxs-lookup"><span data-stu-id="15534-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="15534-123">Om värdet är true (ByPropertyName), du kan skicka vidare indata till parametern.</span><span class="sxs-lookup"><span data-stu-id="15534-123">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="15534-124">Indata är associerade med parametern endast när Parameternamnet matchar namnet på en egenskap för indataobjektet.</span><span class="sxs-lookup"><span data-stu-id="15534-124">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="15534-125">Exempel: om parameternamnet är `Path`, objekt som skickas till cmdleten är associerade med parametern endast när objektet har en egenskap med namnet sökväg.</span><span class="sxs-lookup"><span data-stu-id="15534-125">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="15534-126">Om SANT (ByValue, ByPropertyName), som du kan skicka vidare indata till parametern av egenskapsnamn eller av värde.</span><span class="sxs-lookup"><span data-stu-id="15534-126">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="15534-127">Endast en parameter i en parameteruppsättning kan associeras med värde.</span><span class="sxs-lookup"><span data-stu-id="15534-127">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="15534-128">Du kan inte skicka vidare indata till denna parameter om värdet är false.</span><span class="sxs-lookup"><span data-stu-id="15534-128">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="15534-129">Globbing</span><span class="sxs-lookup"><span data-stu-id="15534-129">Globbing</span></span>

  - <span data-ttu-id="15534-130">Om värdet är true kan texten som en användare anger för parametervärdet innehålla jokertecken.</span><span class="sxs-lookup"><span data-stu-id="15534-130">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="15534-131">Om värdet är false får inte texten som en användare anger för parametervärdet innehålla jokertecken.</span><span class="sxs-lookup"><span data-stu-id="15534-131">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="15534-132">Parameterattribut värde</span><span class="sxs-lookup"><span data-stu-id="15534-132">Parameter Value Attributes</span></span>

- <span data-ttu-id="15534-133">Obligatorisk</span><span class="sxs-lookup"><span data-stu-id="15534-133">Required</span></span>

  - <span data-ttu-id="15534-134">Om värdet är true, måste det angivna värdet användas när du använder parametern i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="15534-134">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="15534-135">Om värdet är FALSKT, är värdet för parametern valfri.</span><span class="sxs-lookup"><span data-stu-id="15534-135">If false, the parameter value is optional.</span></span> <span data-ttu-id="15534-136">Ett värde är vanligtvis valfritt endast när det är en av flera giltiga värden för en parameter, till exempel i en uppräknade typen.</span><span class="sxs-lookup"><span data-stu-id="15534-136">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="15534-137">Det obligatoriska attributet för ett parametervärde skiljer sig från det obligatoriska attributet för en parameter.</span><span class="sxs-lookup"><span data-stu-id="15534-137">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="15534-138">Det obligatoriska attributet på en parameter anges om parametern (och dess värde) måste tas med vid cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="15534-138">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="15534-139">Det obligatoriska attributet för ett parametervärde används däremot endast när parametern ingår i kommandot.</span><span class="sxs-lookup"><span data-stu-id="15534-139">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="15534-140">Anger om motsvarande värde måste användas med parametern.</span><span class="sxs-lookup"><span data-stu-id="15534-140">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="15534-141">Normalt parametervärden som fungerar som platshållare krävs och literal parametervärden krävs inte, eftersom de är en av flera värden som kan användas med parametern.</span><span class="sxs-lookup"><span data-stu-id="15534-141">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="15534-142">Samla Information om Syntax</span><span class="sxs-lookup"><span data-stu-id="15534-142">Gathering Syntax Information</span></span>

1. <span data-ttu-id="15534-143">Börja med cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="15534-143">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="15534-144">Lista alla parametrar för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="15534-144">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="15534-145">Skriv ett bindestreck (även kallat ”dash” eller ”minustecken” (ASCII 45) före varje parameternamn.</span><span class="sxs-lookup"><span data-stu-id="15534-145">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="15534-146">Avgränsa parametrarna i parameteruppsättningar (vissa cmdlets kan ha bara en parameteruppsättning).</span><span class="sxs-lookup"><span data-stu-id="15534-146">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="15534-147">I det här exemplet Get-Tech-cmdlet har två parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="15534-147">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="15534-148">Starta varje parameter med cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="15534-148">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="15534-149">Lista över standardparameter Ange först.</span><span class="sxs-lookup"><span data-stu-id="15534-149">List the default parameter set first.</span></span> <span data-ttu-id="15534-150">Standardparametern har angetts av cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="15534-150">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="15534-151">För varje parameter, en lista över dess unika parameter först om det inte finns namngivna parametrar som måste visas först.</span><span class="sxs-lookup"><span data-stu-id="15534-151">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="15534-152">I exemplet ovan är de namn och ID-parametrarna unika parametrar för två parameteruppsättningar (varje parameteruppsättningen måste ha en parameter som är unik för den parameteruppsättningen).</span><span class="sxs-lookup"><span data-stu-id="15534-152">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="15534-153">Detta gör det enklare för användarna att identifiera vilka de måste du ange för parametern parameteruppsättning.</span><span class="sxs-lookup"><span data-stu-id="15534-153">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="15534-154">Lista över parametrarna i den ordning som de ska synas i kommandot.</span><span class="sxs-lookup"><span data-stu-id="15534-154">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="15534-155">Om ordningen ingen spelar roll, visa relaterade parametrar tillsammans eller lista över de mest använda parametrarna först.</span><span class="sxs-lookup"><span data-stu-id="15534-155">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="15534-156">Se till att parametrarna WhatIf och bekräfta om cmdleten stöder ShouldProcess.</span><span class="sxs-lookup"><span data-stu-id="15534-156">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="15534-157">Du får inte ange parametrarna (t.ex utförlig, felsökning och ErrorAction) i syntaxdiagrammet.</span><span class="sxs-lookup"><span data-stu-id="15534-157">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="15534-158">Den `Get-Help` cmdlet lägger till den informationen du när den visas i hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="15534-158">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="15534-159">Lägg till parametervärden.</span><span class="sxs-lookup"><span data-stu-id="15534-159">Add the parameter values.</span></span> <span data-ttu-id="15534-160">I Windows PowerShell?, parametervärden representeras av sina .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="15534-160">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="15534-161">Men kan namnet på förkortas, till exempel ”string” för System.String.</span><span class="sxs-lookup"><span data-stu-id="15534-161">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="15534-162">Förkorta typer så länge som deras innebörd är tydligt, till exempel ”string” för System.String och ”int” för System.Int32.</span><span class="sxs-lookup"><span data-stu-id="15534-162">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="15534-163">Visa alla värden i uppräkningar, till exempel-typparametern i föregående exempel, som kan anges till ”grundläggande” eller ”Avancerat”.</span><span class="sxs-lookup"><span data-stu-id="15534-163">List all values of enumerations, such as the -type parameter in the previous example, wich can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="15534-164">Växla parametrar, till exempel - lista i föregående exempel, har inte värden.</span><span class="sxs-lookup"><span data-stu-id="15534-164">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="15534-165">Lägg till vinkelparenteser i parametervärdena som är platshållare, jämfört med parametervärden litteraler.</span><span class="sxs-lookup"><span data-stu-id="15534-165">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="15534-166">Ange valfria parametrar och deras värdena inom hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="15534-166">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="15534-167">Valfria parametrar namn (för namngivna parametrar) omges av hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="15534-167">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="15534-168">Namn för parametrar som är namngivna, till exempel Name-parametern i exemplet nedan har inte ska ingå i kommandot.</span><span class="sxs-lookup"><span data-stu-id="15534-168">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="15534-169">Om ett parametervärde kan innehålla flera värden, till exempel en lista med namn i Name-parametern lägger du till ett par med hakparenteser direkt efter värdet för parametern.</span><span class="sxs-lookup"><span data-stu-id="15534-169">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="15534-170">Om användaren kan välja mellan parametrar och parametervärden, till exempel parametern Type valen omges av klammerparenteser och avgränsa dem med exklusiv eller symbol(;).</span><span class="sxs-lookup"><span data-stu-id="15534-170">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="15534-171">Om värdet för parametern måste använda specifika formatering, till exempel citattecken eller parenteserna visa formatet i syntax.</span><span class="sxs-lookup"><span data-stu-id="15534-171">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="15534-172">Koda Syntaxdiagrammet XML</span><span class="sxs-lookup"><span data-stu-id="15534-172">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="15534-173">Noden syntax i XML-filen börjar omedelbart efter att noden beskrivning som slutar med den \</maml:description > taggen.</span><span class="sxs-lookup"><span data-stu-id="15534-173">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="15534-174">Läs om hur insamlingen av data som används i syntaxdiagrammet [samla in Syntaxinformationen](#Gathering-Syntax-Information).</span><span class="sxs-lookup"><span data-stu-id="15534-174">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#Gathering-Syntax-Information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="15534-175">Lägger till en Syntax-nod</span><span class="sxs-lookup"><span data-stu-id="15534-175">Adding a Syntax Node</span></span>

<span data-ttu-id="15534-176">Syntaxdiagrammet visas i cmdlet-hjälpavsnittet genereras från data i noden syntax i XML-filen.</span><span class="sxs-lookup"><span data-stu-id="15534-176">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="15534-177">Noden syntax är inom ett par om \<Kommandosyntax: > taggar.</span><span class="sxs-lookup"><span data-stu-id="15534-177">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="15534-178">Med varje parameter för cmdlet: ar inom ett par \<kommandot: syntaxitem > taggar.</span><span class="sxs-lookup"><span data-stu-id="15534-178">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="15534-179">Det finns ingen gräns för hur många \<kommandot: syntaxitem >-taggar som du kan lägga till.</span><span class="sxs-lookup"><span data-stu-id="15534-179">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="15534-180">I följande exempel visas en syntax-nod som har syntax objekt noder för två parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="15534-180">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="15534-181">Lägger till Cmdlet-namn till parametern ange Data</span><span class="sxs-lookup"><span data-stu-id="15534-181">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="15534-182">Varje parameteruppsättning cmdlet: en har angetts i en syntax objekt nod.</span><span class="sxs-lookup"><span data-stu-id="15534-182">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="15534-183">Varje nod för syntax-objekt som börjar med ett par \<maml:name > taggar som innehåller namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="15534-183">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="15534-184">I följande exempel innehåller ett syntax-noden som har syntax objekt noder för två parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="15534-184">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="15534-185">Att lägga till parametrar</span><span class="sxs-lookup"><span data-stu-id="15534-185">Adding Parameters</span></span>

<span data-ttu-id="15534-186">Varje parameter som lagts till i noden syntax objekt har angetts i ett par \<kommandoparameter: > taggar.</span><span class="sxs-lookup"><span data-stu-id="15534-186">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="15534-187">Du behöver ett par \<kommandoparameter: >-taggar för varje parameter som ingår i parameteruppsättningen, med undantag för de gemensamma parametrarna som tillhandahålls av Windows PowerShell?</span><span class="sxs-lookup"><span data-stu-id="15534-187">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="15534-188">Attribut för att öppna \<kommandoparameter: > taggen avgöra hur parametern visas i syntaxdiagrammet.</span><span class="sxs-lookup"><span data-stu-id="15534-188">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="15534-189">Information om parameterattribut finns [Parameterattribut](#Parameter-Attributes).</span><span class="sxs-lookup"><span data-stu-id="15534-189">For information on parameter attributes, see [Parameter Attributes](#Parameter-Attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="15534-190">Den \<kommandoparameter: > taggen har stöd för ett underordnat element \<maml:description > vars innehåll aldrig visas.</span><span class="sxs-lookup"><span data-stu-id="15534-190">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="15534-191">Beskrivningar av parametern har angetts i Parameternoden i XML-filen.</span><span class="sxs-lookup"><span data-stu-id="15534-191">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="15534-192">Att undvika inkonsekvenser mellan informationen i objektet syntax bodes och Parameternoden utelämna den (\<maml:description > eller lämna det tomt.</span><span class="sxs-lookup"><span data-stu-id="15534-192">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="15534-193">I följande exempel innehåller en nod för objekt av syntax för en parameter med två parametrar.</span><span class="sxs-lookup"><span data-stu-id="15534-193">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
