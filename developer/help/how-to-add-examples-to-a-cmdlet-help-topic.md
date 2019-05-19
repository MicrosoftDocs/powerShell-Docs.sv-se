---
title: Hur du lägger till exempel att en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855121"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="9ea4d-102">Lägga till exempel i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="9ea4d-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="9ea4d-103">Att känna till om exemplen i Cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="9ea4d-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="9ea4d-104">Lista över alla parameternamn i kommandot, även om parameternamn är valfria.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="9ea4d-105">Detta hjälper användare att tolka kommandot enkelt.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="9ea4d-106">Undvik att alias och partiella parameternamn, även om de fungerar med Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="9ea4d-107">I exempel-beskrivning, förklara rationella för kommandot.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="9ea4d-108">Förklara varför du har valt viss parametrar och värden och hur du använder variabler.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="9ea4d-109">Om kommandot använder uttryck, förklarar du dem i detalj.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="9ea4d-110">Om kommandot använder egenskaper och metoder för objekt, särskilt de egenskaper som inte visas i standardvisningen, Använd exemplet som en möjlighet att meddela användaren om objektet.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="9ea4d-111">Hjälp-vyer som visar exempel</span><span class="sxs-lookup"><span data-stu-id="9ea4d-111">Help Views that Display Examples</span></span>

<span data-ttu-id="9ea4d-112">Exempel visas bara i detaljerat och fullständig vyer i cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="9ea4d-113">Lägga till en exempel-nod</span><span class="sxs-lookup"><span data-stu-id="9ea4d-113">Adding an Examples Node</span></span>

<span data-ttu-id="9ea4d-114">Följande XML-koden visar hur du lägger till en exempel-nod som innehåller en exempel-nod.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="9ea4d-115">Lägga till ytterligare exempel noder för varje exempel som du vill ska ingå i avsnittet.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="9ea4d-116">Att lägga till en exempel-rubrik</span><span class="sxs-lookup"><span data-stu-id="9ea4d-116">Adding an Example Title</span></span>

<span data-ttu-id="9ea4d-117">Följande XML-koden visar hur du lägger till en rubrik för det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="9ea4d-118">Rubriken används för att ange exemplet förutom andra exempel.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="9ea4d-119">Windows PowerShell® använder ett standard-huvud som innehåller en rad för sekventiella exempel.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="9ea4d-120">Att lägga till föregående tecken</span><span class="sxs-lookup"><span data-stu-id="9ea4d-120">Adding Preceding Characters</span></span>

<span data-ttu-id="9ea4d-121">Följande XML-koden visar hur du lägger till tecken, till exempel Windows PowerShell-Kommandotolken som visas omedelbart före detta kommando (utan blanksteg mellanliggande).</span><span class="sxs-lookup"><span data-stu-id="9ea4d-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="9ea4d-122">Windows PowerShell® använder Windows PowerShell-Kommandotolken: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="9ea4d-123">Att lägga till kommandot</span><span class="sxs-lookup"><span data-stu-id="9ea4d-123">Adding the Command</span></span>

<span data-ttu-id="9ea4d-124">Följande XML-koden visar hur du lägger till kommandot faktiska för till exempel.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="9ea4d-125">När du lägger till kommandot, skriver du namnet (Använd inte alias) av cmdlets och parametrar.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="9ea4d-126">Kan också använda gemener när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="9ea4d-127">Att lägga till en beskrivning</span><span class="sxs-lookup"><span data-stu-id="9ea4d-127">Adding a Description</span></span>

<span data-ttu-id="9ea4d-128">Följande XML-koden visar hur du lägger till en beskrivning för det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="9ea4d-129">Windows PowerShell® använder en enda uppsättning \<maml:para > taggar för beskrivning, även om flera \<maml:para > taggar kan användas.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="9ea4d-130">Att lägga till exempel på utdata</span><span class="sxs-lookup"><span data-stu-id="9ea4d-130">Adding Example Output</span></span>

<span data-ttu-id="9ea4d-131">Följande XML-koden visar hur du lägger till kommandots utdata.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="9ea4d-132">Kommandot resultat information är valfri, men i vissa fall är det bra att demonstrera effekten av att använda specifika parametrar.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="9ea4d-133">Windows PowerShell® använder två uppsättningar av tom \<maml:para > taggar om du vill separera kommandoutdata från kommandot.</span><span class="sxs-lookup"><span data-stu-id="9ea4d-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```