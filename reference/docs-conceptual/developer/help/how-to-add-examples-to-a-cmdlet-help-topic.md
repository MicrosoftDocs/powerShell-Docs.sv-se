---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till exempel i ett cmdlet-hjälpavsnitt
description: Lägga till exempel i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: 6b72e29c93740b7953d9b68fc8e68c02eb2f4dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654723"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="d50ba-103">Lägga till exempel i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="d50ba-103">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="d50ba-104">Saker att veta om exempel i cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="d50ba-104">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="d50ba-105">Lista alla parameter namn i kommandot, även om parameter namnen är valfria.</span><span class="sxs-lookup"><span data-stu-id="d50ba-105">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="d50ba-106">Detta hjälper användaren att tolka kommandot enkelt.</span><span class="sxs-lookup"><span data-stu-id="d50ba-106">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="d50ba-107">Undvik alias och del parameter namn, även om de fungerar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d50ba-107">Avoid aliases and partial parameter names, even though they work in PowerShell.</span></span>

- <span data-ttu-id="d50ba-108">I exempel beskrivningen förklarar du rationellt för kommandots konstruktion.</span><span class="sxs-lookup"><span data-stu-id="d50ba-108">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="d50ba-109">Förklara varför du har valt särskilda parametrar och värden och hur du använder variabler.</span><span class="sxs-lookup"><span data-stu-id="d50ba-109">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="d50ba-110">Om kommandot använder uttryck förklarar du dem i detalj.</span><span class="sxs-lookup"><span data-stu-id="d50ba-110">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="d50ba-111">Om kommandot använder egenskaper och metoder för objekt, särskilt egenskaper som inte visas i standard visningen, använder du exemplet som en affärs möjlighet för att berätta för användaren om objektet.</span><span class="sxs-lookup"><span data-stu-id="d50ba-111">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="d50ba-112">Hjälp vyer som visar exempel</span><span class="sxs-lookup"><span data-stu-id="d50ba-112">Help Views that Display Examples</span></span>

<span data-ttu-id="d50ba-113">Exempel visas bara i de detaljerade och fullständiga vyerna för cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="d50ba-113">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="d50ba-114">Lägga till en exempel nod</span><span class="sxs-lookup"><span data-stu-id="d50ba-114">Adding an Examples Node</span></span>

<span data-ttu-id="d50ba-115">Följande XML visar hur du lägger till en **exempel** -nod som innehåller en enda **exempel** -nod.</span><span class="sxs-lookup"><span data-stu-id="d50ba-115">The following XML shows how to add an **Examples** node that contains a single **Example** node.</span></span> <span data-ttu-id="d50ba-116">Lägg till ytterligare exempel-noder för varje exempel som du vill inkludera i avsnittet.</span><span class="sxs-lookup"><span data-stu-id="d50ba-116">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="d50ba-117">Lägga till en rubrik för exempel</span><span class="sxs-lookup"><span data-stu-id="d50ba-117">Adding an Example Title</span></span>

<span data-ttu-id="d50ba-118">Följande XML visar hur du lägger till en **rubrik** för exemplet.</span><span class="sxs-lookup"><span data-stu-id="d50ba-118">The following XML shows how to add a **title** for the example.</span></span> <span data-ttu-id="d50ba-119">**Rubriken** används för att ställa in exemplet från andra exempel.</span><span class="sxs-lookup"><span data-stu-id="d50ba-119">The **title** is used to set the example apart from other examples.</span></span> <span data-ttu-id="d50ba-120">PowerShell använder ett standard huvud som innehåller ett sekventiellt exempel nummer.</span><span class="sxs-lookup"><span data-stu-id="d50ba-120">PowerShell uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="d50ba-121">Lägga till föregående tecken</span><span class="sxs-lookup"><span data-stu-id="d50ba-121">Adding Preceding Characters</span></span>

<span data-ttu-id="d50ba-122">Följande XML visar hur du lägger till tecken, t. ex. Windows PowerShell-prompten, som visas omedelbart före kommandot example (utan några mellanliggande blank steg).</span><span class="sxs-lookup"><span data-stu-id="d50ba-122">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="d50ba-123">PowerShell använder Windows PowerShell-prompten: `C:\PS>` .</span><span class="sxs-lookup"><span data-stu-id="d50ba-123">PowerShell uses the Windows PowerShell prompt: `C:\PS>`.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="d50ba-124">Kommandot läggs till</span><span class="sxs-lookup"><span data-stu-id="d50ba-124">Adding the Command</span></span>

<span data-ttu-id="d50ba-125">Följande XML visar hur du lägger till det faktiska kommandot i exemplet.</span><span class="sxs-lookup"><span data-stu-id="d50ba-125">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="d50ba-126">När du lägger till kommandot skriver du hela namnet (Använd inte alias) för cmdlets och parametrar.</span><span class="sxs-lookup"><span data-stu-id="d50ba-126">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="d50ba-127">Använd också gemener när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="d50ba-127">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="d50ba-128">Lägga till en beskrivning</span><span class="sxs-lookup"><span data-stu-id="d50ba-128">Adding a Description</span></span>

<span data-ttu-id="d50ba-129">Följande XML visar hur du lägger till en beskrivning av exemplet.</span><span class="sxs-lookup"><span data-stu-id="d50ba-129">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="d50ba-130">PowerShell använder en enda uppsättning `<maml:para>` taggar för beskrivningen, även om flera `<maml:para>` taggar kan användas.</span><span class="sxs-lookup"><span data-stu-id="d50ba-130">PowerShell uses a single set of `<maml:para>` tags for the description, even though multiple `<maml:para>` tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="d50ba-131">Lägger till exempel utdata</span><span class="sxs-lookup"><span data-stu-id="d50ba-131">Adding Example Output</span></span>

<span data-ttu-id="d50ba-132">Följande XML visar hur du lägger till kommandots utdata.</span><span class="sxs-lookup"><span data-stu-id="d50ba-132">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="d50ba-133">Kommando resultat informationen är valfri, men i vissa fall är det bra att demonstrera effekterna av att använda vissa parametrar.</span><span class="sxs-lookup"><span data-stu-id="d50ba-133">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span>
<span data-ttu-id="d50ba-134">PowerShell använder två uppsättningar med tomma `<maml:para>` taggar för att separera kommandoutdata från kommandot.</span><span class="sxs-lookup"><span data-stu-id="d50ba-134">PowerShell uses two sets of blank `<maml:para>` tags to separate the command output from the command.</span></span>

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
