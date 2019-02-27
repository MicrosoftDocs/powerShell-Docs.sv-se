---
title: Hur du lägger till parameterinformation | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851942"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="12e0b-102">Lägga till parameterinformation</span><span class="sxs-lookup"><span data-stu-id="12e0b-102">How to Add Parameter Information</span></span>

<span data-ttu-id="12e0b-103">Det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet parametrar i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="12e0b-104">Parameteravsnittet i hjälpavsnittet visar var och en av parametrarna för cmdleten och innehåller en detaljerad beskrivning av varje parameter.</span><span class="sxs-lookup"><span data-stu-id="12e0b-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="12e0b-105">Innehållet i avsnittet parametrar ska stämma överens med innehållet i avsnittet SYNTAX i hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="12e0b-106">Det är ansvar i hjälpfilen för att se till att både Syntax och parametrar noden innehåller liknande XML-element.</span><span class="sxs-lookup"><span data-stu-id="12e0b-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="12e0b-107">För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12e0b-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="12e0b-108">Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="12e0b-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="12e0b-109">Lägga till parametrar</span><span class="sxs-lookup"><span data-stu-id="12e0b-109">To Add Parameters</span></span>

1. <span data-ttu-id="12e0b-110">Öppna cmdlet-hjälpfilen och leta rätt på kommando-noden för cmdleten du dokumenterar.</span><span class="sxs-lookup"><span data-stu-id="12e0b-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="12e0b-111">Om du lägger till en ny cmdlet behöver du skapa en ny nod i kommandot.</span><span class="sxs-lookup"><span data-stu-id="12e0b-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="12e0b-112">Hjälp-filen innehåller en kommando-nod för varje cmdlet som du tillhandahåller hjälpinnehållet för.</span><span class="sxs-lookup"><span data-stu-id="12e0b-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="12e0b-113">Här är ett exempel på en tom kommando-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="12e0b-114">Leta upp noden beskrivning i noden kommando och lägger till en nod för parametrar som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="12e0b-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="12e0b-115">Endast en nod för parametrar tillåts och det omedelbart ska följa noden Syntax.</span><span class="sxs-lookup"><span data-stu-id="12e0b-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="12e0b-116">I noden parametrar lägger du till en Parameter-nod för varje parameter för cmdlet: en som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="12e0b-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="12e0b-117">I det här exemplet läggs en Parameter-nod för tre parametrar.</span><span class="sxs-lookup"><span data-stu-id="12e0b-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="12e0b-118">Eftersom dessa är de samma XML-taggar som används i noden Syntax och eftersom parametrarna som anges här måste matcha parametrarna som anges av noden Syntax, kan du kopiera parametern-noder från noden Syntax och klistrar in den i noden parametrar.</span><span class="sxs-lookup"><span data-stu-id="12e0b-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="12e0b-119">Dock måste du kopiera endast en instans av en Parameter-nod, även om parametern har angetts i flera parameteruppsättningar i syntax.</span><span class="sxs-lookup"><span data-stu-id="12e0b-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="12e0b-120">Ange de attributvärden som definierar egenskaperna för varje parameter för varje Parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="12e0b-121">Dessa attribut inkluderar följande: krävdes globbing, pipelineinput och position.</span><span class="sxs-lookup"><span data-stu-id="12e0b-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="12e0b-122">Lägg till namnet på parametern för varje Parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="12e0b-123">Här är ett exempel på parameternamnet läggs till parametern-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="12e0b-124">Lägg till beskrivning av parametern för varje Parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="12e0b-125">Här är ett exempel på Parameterbeskrivning som lagts till i parametern-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="12e0b-126">Lägg till .NET Framework-typen för parametern för varje Parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="12e0b-127">Parametertypen visas tillsammans med parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="12e0b-128">Här är ett exempel på .NET Framework parametertypen läggs till parametern-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="12e0b-129">Lägg till standardvärdet för parametern för varje Parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="12e0b-130">Följande mening läggs till i Parameterbeskrivning när innehållet visas: Standardvärdet är ”DefaultValue”.</span><span class="sxs-lookup"><span data-stu-id="12e0b-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="12e0b-131">Här är ett exempel på standardvärdet för parametern har lagts till i parametern-nod.</span><span class="sxs-lookup"><span data-stu-id="12e0b-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="12e0b-132">Lägg till en nod för möjliga värden för varje Parameter som har flera värden.</span><span class="sxs-lookup"><span data-stu-id="12e0b-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="12e0b-133">Här är ett exempel på den för en nod för möjliga värden som definierar två möjliga värden för parametern</span><span class="sxs-lookup"><span data-stu-id="12e0b-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="12e0b-134">Här följer några saker att komma ihåg när du lägger till parametrar.</span><span class="sxs-lookup"><span data-stu-id="12e0b-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="12e0b-135">Attribut för parametern visas inte i alla vyer i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="12e0b-136">Men de visas i en tabell efter Parameterbeskrivning när användaren ombeds att ange fullständiga (Get-Help \<cmdletname > – fullständig) eller Parameter (Get-Help \<cmdletname >-parametern) vy av avsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="12e0b-137">Beskrivning av parameter är en av de viktigaste delarna av en cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="12e0b-138">Beskrivningen bör vara kort, samt omfattande.</span><span class="sxs-lookup"><span data-stu-id="12e0b-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="12e0b-139">Tänk också på att om Parameterbeskrivning blir för lång, till exempel när två parametrar interagerar med varandra, du kan lägga till mer innehåll i avsnittet information i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="12e0b-140">Parametern-beskrivningen innehåller två typer av information.</span><span class="sxs-lookup"><span data-stu-id="12e0b-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="12e0b-141">Vad cmdleten gör när parametern används.</span><span class="sxs-lookup"><span data-stu-id="12e0b-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="12e0b-142">Det är ett giltigt värde för parametern.</span><span class="sxs-lookup"><span data-stu-id="12e0b-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="12e0b-143">Eftersom parametervärdena som är uttryckt i .NET Framework-objekt, måste användarna mer information om dessa värden än de skulle göra i en traditionell hjälpen.</span><span class="sxs-lookup"><span data-stu-id="12e0b-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="12e0b-144">Meddela användaren vilken typ av data som parametern har utformats för att acceptera och innehåller exempel.</span><span class="sxs-lookup"><span data-stu-id="12e0b-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="12e0b-145">Standardvärdet för parametern är det värde som används om parametern inte anges på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="12e0b-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="12e0b-146">Observera att standardvärdet är valfritt och krävs inte för vissa parametrar, till exempel obligatoriska parametrar.</span><span class="sxs-lookup"><span data-stu-id="12e0b-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="12e0b-147">Dock bör du ange ett standardvärde för de flesta valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="12e0b-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="12e0b-148">Standardvärdet hjälper användare att förstå effekten av att inte använda parametern.</span><span class="sxs-lookup"><span data-stu-id="12e0b-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="12e0b-149">Beskriv standardvärdet särskilt, till exempel ”den aktuella katalogen” eller ”Windows PowerShell installationskatalogen ($pshome)” för en valfri sökväg.</span><span class="sxs-lookup"><span data-stu-id="12e0b-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="12e0b-150">Du kan också skriva en mening som beskriver standard, till exempel följande mening som används för den `PassThru` parameter: ”Om PassThru anges cmdlet: en skickar inte objekt av pipelinen”.</span><span class="sxs-lookup"><span data-stu-id="12e0b-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="12e0b-151">Dessutom eftersom värdet visas motsatt fältnamnet ”**standardvärde**”, du behöver inte inkludera termen ”standardvärdet” i posten.</span><span class="sxs-lookup"><span data-stu-id="12e0b-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="12e0b-152">Standardvärdet för parametern visas inte i alla vyer i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="12e0b-153">Men den visas i en tabell (tillsammans med parameterattribut) efter Parameterbeskrivning när användaren ombeds att ange fullständiga (Get-Help \<cmdletname > – fullständig) eller Parameter (Get-Help \<cmdletname >-parametern) visa i avsnittet.</span><span class="sxs-lookup"><span data-stu-id="12e0b-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="12e0b-154">Följande XML visar ett par `<dev:defaultValue>` taggar som lagts till i den `<command:parameter>` noden.</span><span class="sxs-lookup"><span data-stu-id="12e0b-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="12e0b-155">Observera att standardvärdet följer direkt efter avslutande `</command:parameterValue>` tagg (när värdet för parametern har angetts) eller avslutande `</maml:description>` taggen för Parameterbeskrivning.</span><span class="sxs-lookup"><span data-stu-id="12e0b-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="12e0b-156">Namn.</span><span class="sxs-lookup"><span data-stu-id="12e0b-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="12e0b-157">Lägg till värdena för uppräknade typer</span><span class="sxs-lookup"><span data-stu-id="12e0b-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="12e0b-158">Om parametern har flera värden eller värdena för en uppräknade typ, kan du använda en valfri \<dev:possibleValues > noden.</span><span class="sxs-lookup"><span data-stu-id="12e0b-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="12e0b-159">Den här noden kan du ange ett namn och beskrivning för flera värden.</span><span class="sxs-lookup"><span data-stu-id="12e0b-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="12e0b-160">Tänk på att beskrivningarna för uppräknade värden inte visas i någon av standard hjälp vyer som visas i den `Get-Help` cmdleten, men andra hjälp användarna kan visa det här innehållet i sina synpunkter.</span><span class="sxs-lookup"><span data-stu-id="12e0b-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="12e0b-161">I följande XML-visas en `<dev:possibleValues>` nod med två värden anges.</span><span class="sxs-lookup"><span data-stu-id="12e0b-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```