---
title: Skriva hjälp för PowerShell-cmdletar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: fd565e8bf8429d91d785664c8cc69d1843439219
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560601"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="34164-102">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="34164-102">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="34164-103">PowerShell-cmdletar kan vara användbara, men om inte hjälp avsnitten tydligt förklarar vad cmdleten gör och hur du använder den, kan cmdleten inte användas eller, till och med sämre, vara frustrerande användare.</span><span class="sxs-lookup"><span data-stu-id="34164-103">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span>
<span data-ttu-id="34164-104">Hjälp fil formatet för XML-baserad cmdlet förbättrar konsekvensen, men den fantastiska hjälpen kräver mycket mer.</span><span class="sxs-lookup"><span data-stu-id="34164-104">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="34164-105">Om du aldrig har skrivit cmdlet-hjälpen kan du läsa följande rikt linjer.</span><span class="sxs-lookup"><span data-stu-id="34164-105">If you have never written cmdlet Help, review the following guidelines.</span></span>
<span data-ttu-id="34164-106">Det XML-schema som krävs för att redigera cmdlet-hjälp avsnittet beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="34164-106">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span>
<span data-ttu-id="34164-107">Börja med att [skapa cmdlet-hjälp filen](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="34164-107">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span>
<span data-ttu-id="34164-108">Avsnittet innehåller en beskrivning av XML-noder på översta nivån.</span><span class="sxs-lookup"><span data-stu-id="34164-108">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="34164-109">Skriv rikt linjer för cmdlet-hjälp</span><span class="sxs-lookup"><span data-stu-id="34164-109">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="34164-110">Skriva bra</span><span class="sxs-lookup"><span data-stu-id="34164-110">Write well</span></span>
<span data-ttu-id="34164-111">Ingenting ersätter ett välskrivet ämne.</span><span class="sxs-lookup"><span data-stu-id="34164-111">Nothing replaces a well-written topic.</span></span>
<span data-ttu-id="34164-112">Om du inte är en professionell skrivare kan du söka efter en skrivare eller redigerare som hjälper dig.</span><span class="sxs-lookup"><span data-stu-id="34164-112">If you are not a professional writer, find a writer or editor to help you.</span></span>
<span data-ttu-id="34164-113">Ett annat alternativ är att kopiera din hjälp text till Microsoft Word och använda grammatik-och stavnings kontrollerna för att förbättra ditt arbete.</span><span class="sxs-lookup"><span data-stu-id="34164-113">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="34164-114">Skriv bara</span><span class="sxs-lookup"><span data-stu-id="34164-114">Write simply</span></span>
<span data-ttu-id="34164-115">Använd enkla ord och fraser.</span><span class="sxs-lookup"><span data-stu-id="34164-115">Use simple words and phrases.</span></span>
<span data-ttu-id="34164-116">Undvik jargong.</span><span class="sxs-lookup"><span data-stu-id="34164-116">Avoid jargon.</span></span>
<span data-ttu-id="34164-117">Tänk på att många läsare bara är utrustade med en ord lista för främmande språk och ditt hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="34164-117">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="34164-118">Skriv konsekvent</span><span class="sxs-lookup"><span data-stu-id="34164-118">Write consistently</span></span>
<span data-ttu-id="34164-119">Hjälp för relaterade cmdlets bör vara liknande (till exempel get-x och set-x).</span><span class="sxs-lookup"><span data-stu-id="34164-119">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span>
<span data-ttu-id="34164-120">Använd standard beskrivningarna för standard parametrar som **Force** och **InputObject**.</span><span class="sxs-lookup"><span data-stu-id="34164-120">Use the standard descriptions for standard parameters, like **Force** and **InputObject**.</span></span>
<span data-ttu-id="34164-121">(Kopiera dem från hjälp för Core-cmdletar.) Använd standard villkor.</span><span class="sxs-lookup"><span data-stu-id="34164-121">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span>
<span data-ttu-id="34164-122">Använd till exempel "parameter", inte "argument" och Använd "cmdlet" inte "Command" eller "kommando-let".</span><span class="sxs-lookup"><span data-stu-id="34164-122">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="34164-123">Starta sammanfattningen med ett verb</span><span class="sxs-lookup"><span data-stu-id="34164-123">Start the synopsis with a verb</span></span>
<span data-ttu-id="34164-124">I fältet Sammanfattning informerar du användaren vad cmdleten gör, inte vad det är eller hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="34164-124">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span>
<span data-ttu-id="34164-125">Verben skapar ett uppgifts baserat uttryck som informerar användare om denna cmdlet uppfyller deras krav.</span><span class="sxs-lookup"><span data-stu-id="34164-125">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span>
<span data-ttu-id="34164-126">Använd enkla verb som "Get", "skapa" och "ändra".</span><span class="sxs-lookup"><span data-stu-id="34164-126">Use simple verbs like "get", "create", and "change."</span></span>
<span data-ttu-id="34164-127">Undvik "Set", som kan vara vagt och snygga ord som "ändra".</span><span class="sxs-lookup"><span data-stu-id="34164-127">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="34164-128">Fokusera på objekt</span><span class="sxs-lookup"><span data-stu-id="34164-128">Focus on objects</span></span>
<span data-ttu-id="34164-129">De flesta "Get"-cmdletar visar något, men deras primära funktion är att hämta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="34164-129">Most "get" cmdlets display something, but their primary function is to get an object.</span></span>
<span data-ttu-id="34164-130">I hjälpen fokuserar du på objektet så att användarna förstår att standard visningen är ett av många, och att de kan använda metoderna och egenskaperna för objektet som du har hämtat för dem på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="34164-130">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="34164-131">Skriv detaljerade beskrivningar</span><span class="sxs-lookup"><span data-stu-id="34164-131">Write detailed descriptions</span></span>
<span data-ttu-id="34164-132">Visa en kort lista över allt som cmdleten kan göra i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="34164-132">Briefly list everything that the cmdlet can do in the detailed description.</span></span>
<span data-ttu-id="34164-133">Om huvud funktionen är att ändra en egenskap, men cmdleten kan ändra alla egenskaper, visar du detta i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="34164-133">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="34164-134">Använd konventionell syntax</span><span class="sxs-lookup"><span data-stu-id="34164-134">Use conventional syntax</span></span>
<span data-ttu-id="34164-135">Använd det vanliga Naur-formatet som är vanligt för kommando rads hjälpen för Windows och UNIX.</span><span class="sxs-lookup"><span data-stu-id="34164-135">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a><span data-ttu-id="34164-136">Använd Microsoft .NET Framework-typer för parameter värden</span><span class="sxs-lookup"><span data-stu-id="34164-136">Use Microsoft .NET Framework types for parameter values</span></span>
<span data-ttu-id="34164-137">Plats hållarna för parameter värden (i beskrivningarna syntax och parameter) visar de .NET Framework typer av objekt som parametern accepterar.</span><span class="sxs-lookup"><span data-stu-id="34164-137">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span>
<span data-ttu-id="34164-138">PowerShell-teamet utvecklade denna konvention för att hjälpa att lära användare om .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34164-138">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="34164-139">Skriv fullständiga parameter beskrivningar</span><span class="sxs-lookup"><span data-stu-id="34164-139">Write complete parameter descriptions</span></span>
<span data-ttu-id="34164-140">Parameter beskrivningar måste informera användare av två saker: vad parametern gör (dess funktion) och vad de måste ange för parameter värden.</span><span class="sxs-lookup"><span data-stu-id="34164-140">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="34164-141">Skriv praktiska exempel</span><span class="sxs-lookup"><span data-stu-id="34164-141">Write practical examples</span></span>
<span data-ttu-id="34164-142">Exemplen bör visa hur du använder alla parametrar, men det viktigaste är att visa hur du använder cmdleten i verkliga uppgifter.</span><span class="sxs-lookup"><span data-stu-id="34164-142">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span>
<span data-ttu-id="34164-143">Börja med ett enkelt exempel och skriv allt fler komplexa exempel.</span><span class="sxs-lookup"><span data-stu-id="34164-143">Start with a simple example and write increasingly complex examples.</span></span>
<span data-ttu-id="34164-144">I det sista exemplet visar vi hur du använder cmdleten i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="34164-144">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="34164-145">Använd fältet Anteckningar</span><span class="sxs-lookup"><span data-stu-id="34164-145">Use the Notes field</span></span>
<span data-ttu-id="34164-146">Använd fältet Anteckningar om du vill förklara de koncept som användarna behöver för att förstå cmdleten.</span><span class="sxs-lookup"><span data-stu-id="34164-146">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span>
<span data-ttu-id="34164-147">Du kan också använda kommentarer för att hjälpa användarna att undvika vanliga fel.</span><span class="sxs-lookup"><span data-stu-id="34164-147">You can also use notes to help users avoid common errors.</span></span>
<span data-ttu-id="34164-148">Undvik URL: er när de ändras.</span><span class="sxs-lookup"><span data-stu-id="34164-148">Avoid URLs as they change.</span></span>
<span data-ttu-id="34164-149">Ange i stället användar villkor för att söka efter.</span><span class="sxs-lookup"><span data-stu-id="34164-149">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="34164-150">Testa din hjälp</span><span class="sxs-lookup"><span data-stu-id="34164-150">Test your Help</span></span>
<span data-ttu-id="34164-151">Testa hjälpen precis som du testar koden.</span><span class="sxs-lookup"><span data-stu-id="34164-151">Test the Help just like you test your code.</span></span>
<span data-ttu-id="34164-152">Låt vänner och kollegor läsa ditt hjälp innehåll och ge feedback.</span><span class="sxs-lookup"><span data-stu-id="34164-152">Have friends and colleagues read your Help content and provide feedback.</span></span>
<span data-ttu-id="34164-153">Du kan också begära feedback från diskussions grupper.</span><span class="sxs-lookup"><span data-stu-id="34164-153">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="34164-154">Se även</span><span class="sxs-lookup"><span data-stu-id="34164-154">See Also</span></span>

 [<span data-ttu-id="34164-155">Skapa cmdlet-hjälpfilen</span><span class="sxs-lookup"><span data-stu-id="34164-155">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="34164-156">Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="34164-156">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-157">Så här lägger du till den detaljerade beskrivningen i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="34164-157">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="34164-158">Lägga till syntax till ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="34164-158">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-159">Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="34164-159">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="34164-160">Så här lägger du till indatatyper i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="34164-160">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-161">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="34164-161">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-162">Lägga till anteckningar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="34164-162">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-163">Lägga till exempel i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="34164-163">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-164">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="34164-164">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="34164-165">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="34164-165">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
