---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva hjälp för PowerShell-cmdletar
description: Skriva hjälp för PowerShell-cmdletar
ms.openlocfilehash: b1deaa5998dbc54add93764db785d57afcc0a779
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658105"
---
# <a name="writing-help-for-powershell-cmdlets"></a><span data-ttu-id="74a62-103">Skriva hjälp för PowerShell-cmdletar</span><span class="sxs-lookup"><span data-stu-id="74a62-103">Writing Help for PowerShell Cmdlets</span></span>

<span data-ttu-id="74a62-104">PowerShell-cmdletar kan vara användbara, men om inte hjälp avsnitten tydligt förklarar vad cmdleten gör och hur du använder den, kan cmdleten inte användas eller, till och med sämre, vara frustrerande användare.</span><span class="sxs-lookup"><span data-stu-id="74a62-104">PowerShell cmdlets can be useful, but unless your Help topics clearly explain what the cmdlet does and how to use it, the cmdlet may not get used or, even worse, it might frustrate users.</span></span> <span data-ttu-id="74a62-105">Hjälp fil formatet för XML-baserad cmdlet förbättrar konsekvensen, men den fantastiska hjälpen kräver mycket mer.</span><span class="sxs-lookup"><span data-stu-id="74a62-105">The XML-based cmdlet Help file format enhances consistency, but great help requires much more.</span></span>

<span data-ttu-id="74a62-106">Om du aldrig har skrivit cmdlet-hjälpen kan du läsa följande rikt linjer.</span><span class="sxs-lookup"><span data-stu-id="74a62-106">If you have never written cmdlet Help, review the following guidelines.</span></span> <span data-ttu-id="74a62-107">Det XML-schema som krävs för att redigera cmdlet-hjälp avsnittet beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="74a62-107">The XML schema required to author the cmdlet Help topic is described in the following section.</span></span> <span data-ttu-id="74a62-108">Börja med att [skapa cmdlet-hjälp filen](./how-to-create-the-cmdlet-help-file.md).</span><span class="sxs-lookup"><span data-stu-id="74a62-108">Start with [Creating the Cmdlet Help File](./how-to-create-the-cmdlet-help-file.md).</span></span> <span data-ttu-id="74a62-109">Avsnittet innehåller en beskrivning av XML-noder på översta nivån.</span><span class="sxs-lookup"><span data-stu-id="74a62-109">That topic includes a description of the top-level XML nodes.</span></span>

## <a name="writing-guidelines-for-cmdlet-help"></a><span data-ttu-id="74a62-110">Skriv rikt linjer för cmdlet-hjälp</span><span class="sxs-lookup"><span data-stu-id="74a62-110">Writing Guidelines for Cmdlet Help</span></span>

### <a name="write-well"></a><span data-ttu-id="74a62-111">Skriva bra</span><span class="sxs-lookup"><span data-stu-id="74a62-111">Write well</span></span>

<span data-ttu-id="74a62-112">Ingenting ersätter ett välskrivet ämne.</span><span class="sxs-lookup"><span data-stu-id="74a62-112">Nothing replaces a well-written topic.</span></span> <span data-ttu-id="74a62-113">Om du inte är en professionell skrivare kan du söka efter en skrivare eller redigerare som hjälper dig.</span><span class="sxs-lookup"><span data-stu-id="74a62-113">If you are not a professional writer, find a writer or editor to help you.</span></span> <span data-ttu-id="74a62-114">Ett annat alternativ är att kopiera din hjälp text till Microsoft Word och använda grammatik-och stavnings kontrollerna för att förbättra ditt arbete.</span><span class="sxs-lookup"><span data-stu-id="74a62-114">Another alternative is to copy your Help text into Microsoft Word and use the grammar and spelling checks to improve your work.</span></span>

### <a name="write-simply"></a><span data-ttu-id="74a62-115">Skriv bara</span><span class="sxs-lookup"><span data-stu-id="74a62-115">Write simply</span></span>

<span data-ttu-id="74a62-116">Använd enkla ord och fraser.</span><span class="sxs-lookup"><span data-stu-id="74a62-116">Use simple words and phrases.</span></span> <span data-ttu-id="74a62-117">Undvik jargong.</span><span class="sxs-lookup"><span data-stu-id="74a62-117">Avoid jargon.</span></span> <span data-ttu-id="74a62-118">Tänk på att många läsare bara är utrustade med en ord lista för främmande språk och ditt hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="74a62-118">Consider that many readers are equipped only with a foreign-language dictionary and your Help topic.</span></span>

### <a name="write-consistently"></a><span data-ttu-id="74a62-119">Skriv konsekvent</span><span class="sxs-lookup"><span data-stu-id="74a62-119">Write consistently</span></span>

<span data-ttu-id="74a62-120">Hjälp för relaterade cmdlets bör vara liknande (till exempel get-x och set-x).</span><span class="sxs-lookup"><span data-stu-id="74a62-120">Help for related cmdlets should be similar (for example, get-x and set-x).</span></span> <span data-ttu-id="74a62-121">Använd standard beskrivningarna för standard parametrar som **Force** och **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="74a62-121">Use the standard descriptions for standard parameters, like **Force** and **InputObject** .</span></span> <span data-ttu-id="74a62-122">(Kopiera dem från hjälp för Core-cmdletar.) Använd standard villkor.</span><span class="sxs-lookup"><span data-stu-id="74a62-122">(Copy them from Help for the core cmdlets.) Use standard terms.</span></span> <span data-ttu-id="74a62-123">Använd till exempel "parameter", inte "argument" och Använd "cmdlet" inte "Command" eller "kommando-let".</span><span class="sxs-lookup"><span data-stu-id="74a62-123">For example, use "parameter", not "argument", and use "cmdlet" not "command" or "command-let."</span></span>

### <a name="start-the-synopsis-with-a-verb"></a><span data-ttu-id="74a62-124">Starta sammanfattningen med ett verb</span><span class="sxs-lookup"><span data-stu-id="74a62-124">Start the synopsis with a verb</span></span>

<span data-ttu-id="74a62-125">I fältet Sammanfattning informerar du användaren vad cmdleten gör, inte vad det är eller hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="74a62-125">The synopsis field informs the user what the cmdlet does, not what it is or how it works.</span></span> <span data-ttu-id="74a62-126">Verben skapar ett uppgifts baserat uttryck som informerar användare om denna cmdlet uppfyller deras krav.</span><span class="sxs-lookup"><span data-stu-id="74a62-126">Verbs create a task-based statement that informs users if this cmdlet meets their requirements.</span></span> <span data-ttu-id="74a62-127">Använd enkla verb som "Get", "skapa" och "ändra".</span><span class="sxs-lookup"><span data-stu-id="74a62-127">Use simple verbs like "get", "create", and "change."</span></span> <span data-ttu-id="74a62-128">Undvik "Set", som kan vara vagt och snygga ord som "ändra".</span><span class="sxs-lookup"><span data-stu-id="74a62-128">Avoid "set", which can be vague and fancy words like "modify".</span></span>

### <a name="focus-on-objects"></a><span data-ttu-id="74a62-129">Fokusera på objekt</span><span class="sxs-lookup"><span data-stu-id="74a62-129">Focus on objects</span></span>

<span data-ttu-id="74a62-130">De flesta "Get"-cmdletar visar något, men deras primära funktion är att hämta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="74a62-130">Most "get" cmdlets display something, but their primary function is to get an object.</span></span> <span data-ttu-id="74a62-131">I hjälpen fokuserar du på objektet så att användarna förstår att standard visningen är ett av många, och att de kan använda metoderna och egenskaperna för objektet som du har hämtat för dem på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="74a62-131">In your Help, focus on the object, so that users understand that the default display is one of many, and that they can use the methods and properties of the object that you retrieved for them in different ways.</span></span>

### <a name="write-detailed-descriptions"></a><span data-ttu-id="74a62-132">Skriv detaljerade beskrivningar</span><span class="sxs-lookup"><span data-stu-id="74a62-132">Write detailed descriptions</span></span>

<span data-ttu-id="74a62-133">Visa en kort lista över allt som cmdleten kan göra i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="74a62-133">Briefly list everything that the cmdlet can do in the detailed description.</span></span> <span data-ttu-id="74a62-134">Om huvud funktionen är att ändra en egenskap, men cmdleten kan ändra alla egenskaper, visar du detta i den detaljerade beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="74a62-134">If the main function is to change one property, but the cmdlet can change all properties, list this in the detailed description.</span></span>

### <a name="use-conventional-syntax"></a><span data-ttu-id="74a62-135">Använd konventionell syntax</span><span class="sxs-lookup"><span data-stu-id="74a62-135">Use conventional syntax</span></span>

<span data-ttu-id="74a62-136">Använd standard Backus-Naur formatet som är vanligt för kommando rads hjälpen för Windows och UNIX.</span><span class="sxs-lookup"><span data-stu-id="74a62-136">Use the standard Backus-Naur format which is common for Windows and UNIX command-line Help.</span></span>

### <a name="use-microsoft-net-types-for-parameter-values"></a><span data-ttu-id="74a62-137">Använd Microsoft .NET typer för parameter värden</span><span class="sxs-lookup"><span data-stu-id="74a62-137">Use Microsoft .NET types for parameter values</span></span>

<span data-ttu-id="74a62-138">Plats hållarna för parameter värden (i beskrivningarna syntax och parameter) visar de .NET Framework typer av objekt som parametern accepterar.</span><span class="sxs-lookup"><span data-stu-id="74a62-138">The placeholders for parameter values (in the syntax and parameter descriptions) show the .NET Framework types of the objects that the parameter will accept.</span></span> <span data-ttu-id="74a62-139">PowerShell-teamet utvecklade denna konvention för att hjälpa att lära användare om .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74a62-139">The PowerShell team developed this convention to help teach users about the .NET Framework.</span></span>

### <a name="write-complete-parameter-descriptions"></a><span data-ttu-id="74a62-140">Skriv fullständiga parameter beskrivningar</span><span class="sxs-lookup"><span data-stu-id="74a62-140">Write complete parameter descriptions</span></span>

<span data-ttu-id="74a62-141">Parameter beskrivningar måste informera användare av två saker: vad parametern gör (dess funktion) och vad de måste ange för parameter värden.</span><span class="sxs-lookup"><span data-stu-id="74a62-141">Parameter descriptions must inform users of two things: what the parameter does (its effect) and what they must type for the parameter values.</span></span>

### <a name="write-practical-examples"></a><span data-ttu-id="74a62-142">Skriv praktiska exempel</span><span class="sxs-lookup"><span data-stu-id="74a62-142">Write practical examples</span></span>

<span data-ttu-id="74a62-143">Exemplen bör visa hur du använder alla parametrar, men det viktigaste är att visa hur du använder cmdleten i verkliga uppgifter.</span><span class="sxs-lookup"><span data-stu-id="74a62-143">The examples should show how to use all of the parameters, but the most important thing is to show how to use the cmdlet in real-world tasks.</span></span> <span data-ttu-id="74a62-144">Börja med ett enkelt exempel och skriv allt fler komplexa exempel.</span><span class="sxs-lookup"><span data-stu-id="74a62-144">Start with a simple example and write increasingly complex examples.</span></span> <span data-ttu-id="74a62-145">I det sista exemplet visar vi hur du använder cmdleten i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="74a62-145">In the final example, show how to use the cmdlet in a pipeline.</span></span>

### <a name="use-the-notes-field"></a><span data-ttu-id="74a62-146">Använd fältet Anteckningar</span><span class="sxs-lookup"><span data-stu-id="74a62-146">Use the Notes field</span></span>

<span data-ttu-id="74a62-147">Använd fältet Anteckningar om du vill förklara de koncept som användarna behöver för att förstå cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74a62-147">Use the Notes field to explain concepts that users need to understand the cmdlet.</span></span> <span data-ttu-id="74a62-148">Du kan också använda kommentarer för att hjälpa användarna att undvika vanliga fel.</span><span class="sxs-lookup"><span data-stu-id="74a62-148">You can also use notes to help users avoid common errors.</span></span> <span data-ttu-id="74a62-149">Undvik URL: er när de ändras.</span><span class="sxs-lookup"><span data-stu-id="74a62-149">Avoid URLs as they change.</span></span> <span data-ttu-id="74a62-150">Ange i stället användar villkor för att söka efter.</span><span class="sxs-lookup"><span data-stu-id="74a62-150">Instead, provide users terms to search for.</span></span>

### <a name="test-your-help"></a><span data-ttu-id="74a62-151">Testa din hjälp</span><span class="sxs-lookup"><span data-stu-id="74a62-151">Test your Help</span></span>

<span data-ttu-id="74a62-152">Testa hjälpen precis som du testar koden.</span><span class="sxs-lookup"><span data-stu-id="74a62-152">Test the Help just like you test your code.</span></span> <span data-ttu-id="74a62-153">Låt vänner och kollegor läsa ditt hjälp innehåll och ge feedback.</span><span class="sxs-lookup"><span data-stu-id="74a62-153">Have friends and colleagues read your Help content and provide feedback.</span></span> <span data-ttu-id="74a62-154">Du kan också begära feedback från diskussions grupper.</span><span class="sxs-lookup"><span data-stu-id="74a62-154">You can also solicit feedback from newsgroups.</span></span>

## <a name="see-also"></a><span data-ttu-id="74a62-155">Se även</span><span class="sxs-lookup"><span data-stu-id="74a62-155">See Also</span></span>

 [<span data-ttu-id="74a62-156">Skapa cmdlet-hjälpfilen</span><span class="sxs-lookup"><span data-stu-id="74a62-156">How to Create the Cmdlet Help File</span></span>](./how-to-create-the-cmdlet-help-file.md)

 [<span data-ttu-id="74a62-157">Lägga till cmdlet-namnet och sammanfattningen i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="74a62-157">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-158">Så här lägger du till den detaljerade beskrivningen i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="74a62-158">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="74a62-159">Lägga till syntax till ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="74a62-159">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-160">Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="74a62-160">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="74a62-161">Så här lägger du till indatatyper i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="74a62-161">How to add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-162">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="74a62-162">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-163">Lägga till anteckningar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="74a62-163">How to Add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-164">Lägga till exempel i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="74a62-164">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-165">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="74a62-165">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="74a62-166">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="74a62-166">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
