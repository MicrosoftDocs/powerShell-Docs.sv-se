---
title: Skrivhjälp för PowerShell-cmdletar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083169"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="ddd2c-102">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="ddd2c-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="ddd2c-103">PowerShell-cmdlets kan vara användbart, men om inte din hjälpavsnitt Förklara tydligt vad cmdleten gör och hur du använder det, kan inte hämta används cmdleten eller, värsta fall kan det vara frustrerande användare.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="ddd2c-104">Filformat för XML-baserade cmdlet-hjälpen förbättrar konsekvens, men bra kräver mycket mer.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="ddd2c-105">Om du aldrig har skrivit cmdlet hjälp, kan du läsa följande riktlinjer.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="ddd2c-106">XML-schema som krävs för att skapa cmdlet-hjälpavsnittet beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="ddd2c-107">Börja med [skapar Cmdlet hjälpfilen](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="ddd2c-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="ddd2c-108">Avsnittet innehåller en beskrivning av de översta XML-noderna.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="ddd2c-109">Skriva riktlinjer för Cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="ddd2c-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="ddd2c-110">Skriva bra</span><span class="sxs-lookup"><span data-stu-id="ddd2c-110">Write well</span></span>
<span data-ttu-id="ddd2c-111">Inget ersätter ett välskriven ämne.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="ddd2c-112">Om du inte är en professionell skrivare, hitta en skrivare eller en redigerare som hjälper dig att.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="ddd2c-113">Ett annat alternativ är att kopiera dina hjälptext till Microsoft Word och använda grammatik och stavning kontrollerar för att förbättra ditt arbete.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="ddd2c-114">Skriv bara</span><span class="sxs-lookup"><span data-stu-id="ddd2c-114">Write simply</span></span>
<span data-ttu-id="ddd2c-115">Använd enkla ord och fraser.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-115">Use simple words and phrases.</span></span>
<span data-ttu-id="ddd2c-116">Undvik jargong.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-116">Avoid jargon.</span></span>
<span data-ttu-id="ddd2c-117">Överväg att många läsare är utrustade endast med en ordlista för andra språk och det aktuella hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="ddd2c-118">Skriva konsekvent</span><span class="sxs-lookup"><span data-stu-id="ddd2c-118">Write consistently</span></span>
<span data-ttu-id="ddd2c-119">Hjälp för relaterade cmdlets bör likna (till exempel get-x och set-x).</span><span class="sxs-lookup"><span data-stu-id="ddd2c-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="ddd2c-120">Använder standard beskrivningarna för standard parametrar, t.ex **kraft** och **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="ddd2c-121">(Kopiera dem från hjälp för core-cmdletarna.) Använda allmänna villkor.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="ddd2c-122">Till exempel, Använd ”parametern”, inte ”argumentet” och Använd ”cmdlet” inte ”kommandot” eller ”command-let”.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="ddd2c-123">Starta sammanfattning med ett verb</span><span class="sxs-lookup"><span data-stu-id="ddd2c-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="ddd2c-124">Fältet Sammanfattning informerar användaren vilka cmdleten, inte vad det är eller hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="ddd2c-125">Verb skapa en uppgiftsbaserad instruktion som informerar användarna om denna cmdlet uppfyller deras behov.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="ddd2c-126">Använda enkla verb som ”hämta”, ”skapa” och ”ändra”.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="ddd2c-127">Undvika (set), vilket kan vara vaga och avancerad ord som ”ändra”.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="ddd2c-128">Fokusera på objekt</span><span class="sxs-lookup"><span data-stu-id="ddd2c-128">Focus on objects</span></span>
<span data-ttu-id="ddd2c-129">De flesta ”hämta” cmdletar visas något, men deras primära funktion är att hämta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="ddd2c-130">I din hjälp att fokusera på objektet, så att användarna förstår att standardvisningen är ett av flera och att de kan använda metoder och egenskaper i objektet som du hämtade för dem på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="ddd2c-131">Skriva detaljerade beskrivningar</span><span class="sxs-lookup"><span data-stu-id="ddd2c-131">Write detailed descriptions</span></span>
<span data-ttu-id="ddd2c-132">Kort lista allt som cmdlet: en kan göra i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="ddd2c-133">Om den huvudsakliga funktionen är att ändra en egenskap, men cmdlet: en kan ändra alla egenskaper, lista du detta i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="ddd2c-134">Använd konventionella syntax</span><span class="sxs-lookup"><span data-stu-id="ddd2c-134">Use conventional syntax</span></span>
<span data-ttu-id="ddd2c-135">Använd standard Backus Naur formatet som är gemensamt för Windows och UNIX-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="ddd2c-136">Använd Microsoft .NET Framework-typer för parametervärden</span><span class="sxs-lookup"><span data-stu-id="ddd2c-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="ddd2c-137">Platshållare för värden (i syntax och parameteralternativ beskrivningarna) visar .NET Framework-typer av objekt som ska ta emot parametern.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="ddd2c-138">PowerShell-teamet utvecklade denna konvention för att lära ut användare om .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="ddd2c-139">Skriva fullständiga beskrivningar</span><span class="sxs-lookup"><span data-stu-id="ddd2c-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="ddd2c-140">Beskrivningar av parametern måste informera användare om två saker: vilka parametern gör (dess effekt) och de måste skriva för parametervärdena.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="ddd2c-141">Skriva praktiska exempel</span><span class="sxs-lookup"><span data-stu-id="ddd2c-141">Write practical examples</span></span>
<span data-ttu-id="ddd2c-142">Exemplen ska visa hur du använder alla parametrar, men viktigaste är att visa hur du använder cmdlet: en i verkliga uppgifter.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="ddd2c-143">Börja med ett enkelt exempel och skriva allt mer komplexa exempel.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="ddd2c-144">I det sista exemplet visa hur du använder cmdleten i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="ddd2c-145">Använd fältet Anteckningar</span><span class="sxs-lookup"><span data-stu-id="ddd2c-145">Use the Notes field</span></span>
<span data-ttu-id="ddd2c-146">Använd fältet Anteckningar för att förklara begreppen att användarna måste förstå cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="ddd2c-147">Du kan också använda anteckningar för att hjälpa användarna att undvika vanliga fel.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="ddd2c-148">Undvik att URL: er när den ändras.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="ddd2c-149">I stället ange villkor för användarna att söka efter.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="ddd2c-150">Testa din hjälp</span><span class="sxs-lookup"><span data-stu-id="ddd2c-150">Test your Help</span></span>
<span data-ttu-id="ddd2c-151">Testa hjälp precis som du testar din kod.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="ddd2c-152">Har vänner och kollegor läsa hjälpinnehåll och ge feedback.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="ddd2c-153">Du kan också samla in feedback från diskussionsgrupper.</span><span class="sxs-lookup"><span data-stu-id="ddd2c-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddd2c-154">Se även</span><span class="sxs-lookup"><span data-stu-id="ddd2c-154">See Also</span></span>

 [<span data-ttu-id="ddd2c-155">Så här skapar du filen Cmdlet-hjälpen</span><span class="sxs-lookup"><span data-stu-id="ddd2c-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="ddd2c-156">Hur du lägger till Cmdlet-namn och sammanfattning för en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-157">Hur du lägger till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="ddd2c-158">Lägga till Syntax i en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-159">Lägga till parametrar i en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="ddd2c-160">Hur du lägger till indata-typer till en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-161">Hur du lägger till returvärden för en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-162">Lägga till kommentarer om en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-163">Hur du lägger till exempel att en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-164">Lägga till länkarna till Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="ddd2c-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="ddd2c-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ddd2c-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)