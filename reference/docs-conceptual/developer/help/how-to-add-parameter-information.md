---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till parameterinformation
description: Lägga till parameterinformation
ms.openlocfilehash: 8f4fc46ef256a77b058df4ba506124f80732cb39
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663055"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="52fc0-103">Lägga till parameterinformation</span><span class="sxs-lookup"><span data-stu-id="52fc0-103">How to Add Parameter Information</span></span>

<span data-ttu-id="52fc0-104">I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet **parametrar** i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52fc0-104">This section describes how to add content that is displayed in the **PARAMETERS** section of the cmdlet Help topic.</span></span> <span data-ttu-id="52fc0-105">I avsnittet **parametrar** i hjälp avsnittet visas var och en av parametrarna för cmdleten och en detaljerad beskrivning av varje parameter.</span><span class="sxs-lookup"><span data-stu-id="52fc0-105">The **PARAMETERS** section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="52fc0-106">Innehållet i **parameter** avsnittet ska överensstämma med innehållet i **syntax** -avsnittet i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="52fc0-106">The content of the **PARAMETERS** section should be consistent with the content of the **SYNTAX** section of the Help topic.</span></span> <span data-ttu-id="52fc0-107">Det åligger hjälp författaren att se till att både noden **syntax** och **parametrar** innehåller liknande XML-element.</span><span class="sxs-lookup"><span data-stu-id="52fc0-107">It is the responsibility of the Help author to make sure that both the **Syntax** and **Parameters** node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="52fc0-108">Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52fc0-108">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="52fc0-109">Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="52fc0-109">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="52fc0-110">Lägga till parametrar</span><span class="sxs-lookup"><span data-stu-id="52fc0-110">To Add Parameters</span></span>

1. <span data-ttu-id="52fc0-111">Öppna cmdlet-hjälpen och leta upp kommando-noden för den cmdlet som du dokumenterar.</span><span class="sxs-lookup"><span data-stu-id="52fc0-111">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="52fc0-112">Om du lägger till en ny cmdlet måste du skapa en ny kommando-nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-112">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="52fc0-113">Hjälp filen innehåller en kommando-nod för varje cmdlet som du tillhandahåller hjälp innehåll för.</span><span class="sxs-lookup"><span data-stu-id="52fc0-113">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="52fc0-114">Här är ett exempel på en tom kommando-nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-114">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

1. <span data-ttu-id="52fc0-115">Leta upp noden beskrivning i noden kommando och Lägg till noden parametrar enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="52fc0-115">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span>
   <span data-ttu-id="52fc0-116">Endast en parameter-nod tillåts och den ska omedelbart följa noden syntax.</span><span class="sxs-lookup"><span data-stu-id="52fc0-116">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. <span data-ttu-id="52fc0-117">I noden parametrar lägger du till en **parameter** -nod för varje parameter i cmdleten enligt vad som visas nedan.</span><span class="sxs-lookup"><span data-stu-id="52fc0-117">Within the Parameters node, add a **Parameter** node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="52fc0-118">I det här exemplet läggs en **parametriserad** nod till för tre parametrar.</span><span class="sxs-lookup"><span data-stu-id="52fc0-118">In this example, a **Parameter** node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="52fc0-119">Eftersom dessa är samma XML-taggar som används i noden syntax, och eftersom parametrarna som anges här måste matcha de parametrar som anges av noden syntax, kan du kopiera parametervärdena från noden syntax och klistra in dem i noden parametrar.</span><span class="sxs-lookup"><span data-stu-id="52fc0-119">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="52fc0-120">Men var noga med att bara kopiera en instans av en parameter-nod, även om parametern anges i flera parameter uppsättningar i syntaxen.</span><span class="sxs-lookup"><span data-stu-id="52fc0-120">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

1. <span data-ttu-id="52fc0-121">Ange attributvärden som definierar egenskaperna för varje parameter för varje parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-121">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="52fc0-122">Dessa attribut innehåller följande: required, globbing, pipelineinput och position.</span><span class="sxs-lookup"><span data-stu-id="52fc0-122">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

1. <span data-ttu-id="52fc0-123">Lägg till namnet på parametern för varje parameter-nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-123">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="52fc0-124">Här är ett exempel på parameter namnet som har lagts till i noden parameter.</span><span class="sxs-lookup"><span data-stu-id="52fc0-124">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. <span data-ttu-id="52fc0-125">Lägg till en beskrivning av parametern för varje **parameter** -nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-125">For each **Parameter** node, add the description of the parameter.</span></span> <span data-ttu-id="52fc0-126">Här är ett exempel på parameter beskrivningen som läggs till i noden **parameter** .</span><span class="sxs-lookup"><span data-stu-id="52fc0-126">Here is an example of the parameter description added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="52fc0-127">Lägg till parameterns .NET-typ för varje **parameter** -nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-127">For each **Parameter** node, add the .NET type of the parameter.</span></span> <span data-ttu-id="52fc0-128">Parameter typen visas tillsammans med parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="52fc0-128">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="52fc0-129">Här är ett exempel på den parameter-.NET-typ som har lagts till i noden **parameter** .</span><span class="sxs-lookup"><span data-stu-id="52fc0-129">Here is an example of the parameter .NET type added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="52fc0-130">Lägg till standardvärdet för parametern för varje **parameter** -nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-130">For each **Parameter** node, add the default value of the parameter.</span></span> <span data-ttu-id="52fc0-131">Följande mening läggs till i parameter beskrivningen när innehållet visas: **Standardvärde** är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="52fc0-131">The following sentence is added to the parameter description when the content is displayed: **DefaultValue** is the default.</span></span>

   <span data-ttu-id="52fc0-132">Här är ett exempel på standardvärdet för parametern läggs till i noden **parameter** .</span><span class="sxs-lookup"><span data-stu-id="52fc0-132">Here is an example of the parameter default value is added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="52fc0-133">Lägg till en nod för möjliga värden för varje parameter som har flera värden.</span><span class="sxs-lookup"><span data-stu-id="52fc0-133">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="52fc0-134">Här är ett exempel på en nod med möjliga värden som definierar två möjliga värden för parametern</span><span class="sxs-lookup"><span data-stu-id="52fc0-134">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="52fc0-135">Här är några saker att komma ihåg när du lägger till parametrar.</span><span class="sxs-lookup"><span data-stu-id="52fc0-135">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="52fc0-136">Attributen för parametern visas inte i alla vyer i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52fc0-136">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="52fc0-137">De visas dock i en tabell som följer parameter beskrivningen när användaren ombeds använda vyn **fullständig** ( `Get-Help <cmdletname> -full` ) eller **parameter** ( `Get-Help <cmdletname> -parameter` ) för ämnet.</span><span class="sxs-lookup"><span data-stu-id="52fc0-137">However, they are displayed in a table following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help <cmdletname> -parameter`) view of the topic.</span></span>

- <span data-ttu-id="52fc0-138">Parameter beskrivningen är en av de viktigaste delarna i ett cmdlet-hjälp ämne.</span><span class="sxs-lookup"><span data-stu-id="52fc0-138">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="52fc0-139">Beskrivningen måste vara kortfattad, samt grundlig.</span><span class="sxs-lookup"><span data-stu-id="52fc0-139">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="52fc0-140">Kom också ihåg att om parameter beskrivningen blir för lång, t. ex. När två parametrar interagerar med varandra, kan du lägga till mer innehåll i avsnittet anteckningar i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52fc0-140">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="52fc0-141">Parameter beskrivningen innehåller två typer av information.</span><span class="sxs-lookup"><span data-stu-id="52fc0-141">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="52fc0-142">Vad cmdleten gör när parametern används.</span><span class="sxs-lookup"><span data-stu-id="52fc0-142">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="52fc0-143">Det juridiska värdet för parametern.</span><span class="sxs-lookup"><span data-stu-id="52fc0-143">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="52fc0-144">Eftersom parametervärdena uttrycks som .NET-objekt, behöver användarna mer information om dessa värden än de skulle ha i en traditionell kommando rads hjälp.</span><span class="sxs-lookup"><span data-stu-id="52fc0-144">Because the parameter values are expressed as .NET objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="52fc0-145">Berätta för användaren vilken typ av data som parametern är avsedd att godkänna och inkludera exempel.</span><span class="sxs-lookup"><span data-stu-id="52fc0-145">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="52fc0-146">Standardvärdet för parametern är det värde som används om parametern inte anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="52fc0-146">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="52fc0-147">Observera att standardvärdet är valfritt och att det inte behövs för vissa parametrar, till exempel obligatoriska parametrar.</span><span class="sxs-lookup"><span data-stu-id="52fc0-147">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="52fc0-148">Du bör dock ange ett standardvärde för de flesta valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="52fc0-148">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="52fc0-149">Standardvärdet hjälper användaren att förstå effekterna av att inte använda-parametern.</span><span class="sxs-lookup"><span data-stu-id="52fc0-149">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="52fc0-150">Beskriv standardvärdet särskilt, till exempel "aktuell katalog" eller "PowerShell installations katalog ( `$PSHOME` )" för en valfri sökväg.</span><span class="sxs-lookup"><span data-stu-id="52fc0-150">Describe the default value very specifically, such as the "Current directory" or the "PowerShell installation directory (`$PSHOME`)" for an optional path.</span></span> <span data-ttu-id="52fc0-151">Du kan också skriva en mening som beskriver standard, till exempel följande mening som används för parametern **Passthru** : "om Passthru inte har angetts, skickar inte cmdleten objekt nedåt i pipelinen."</span><span class="sxs-lookup"><span data-stu-id="52fc0-151">You can also write a sentence that describes the default, such as the following sentence used for the **PassThru** parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span> <span data-ttu-id="52fc0-152">Eftersom värdet visas mittemot **standardvärdet** för fält namn, behöver du inte heller ta med termen "standardvärde" i posten.</span><span class="sxs-lookup"><span data-stu-id="52fc0-152">Also, because the value is displayed opposite the field name **Default value**, you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="52fc0-153">Standardvärdet för parametern visas inte i alla vyer i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52fc0-153">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="52fc0-154">Den visas dock i en tabell (tillsammans med parametervärdena) efter parameter beskrivningen när användaren ställer en **fullständig** ( `Get-Help <cmdletname> -full` ) eller **parameter** ( `Get-Help
<cmdletname> -parameter` ) vy av ämnet.</span><span class="sxs-lookup"><span data-stu-id="52fc0-154">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help
<cmdletname> -parameter`) view of the topic.</span></span>

<span data-ttu-id="52fc0-155">Följande XML visar ett par med `<dev:defaultValue>` taggar som har lagts till i `<command:parameter>` noden.</span><span class="sxs-lookup"><span data-stu-id="52fc0-155">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span>
<span data-ttu-id="52fc0-156">Observera att standardvärdet följer omedelbart efter den avslutande `</command:parameterValue>` taggen (när parametervärdet har angetts) eller den avslutande `</maml:description>` taggen för parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="52fc0-156">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="52fc0-157">Namn.</span><span class="sxs-lookup"><span data-stu-id="52fc0-157">name.</span></span>

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

<span data-ttu-id="52fc0-158">Lägg till värden för uppräknade typer</span><span class="sxs-lookup"><span data-stu-id="52fc0-158">Add Values for Enumerated Types</span></span>

<span data-ttu-id="52fc0-159">Om parametern har flera värden eller värden för en uppräknings typ kan du använda en valfri \<dev:possibleValues> nod.</span><span class="sxs-lookup"><span data-stu-id="52fc0-159">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="52fc0-160">Med den här noden kan du ange ett namn och en beskrivning för flera värden.</span><span class="sxs-lookup"><span data-stu-id="52fc0-160">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="52fc0-161">Observera att beskrivningarna av de uppräknade värdena inte visas i någon av de standard visnings lägen som visas av `Get-Help` cmdleten, men andra hjälp visnings program kan visa det här innehållet i sina vyer.</span><span class="sxs-lookup"><span data-stu-id="52fc0-161">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="52fc0-162">Följande XML visar en `<dev:possibleValues>` nod med två angivna värden.</span><span class="sxs-lookup"><span data-stu-id="52fc0-162">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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
