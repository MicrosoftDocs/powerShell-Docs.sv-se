---
title: Fel rapportering för cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356569"
---
# <a name="cmdlet-error-reporting"></a><span data-ttu-id="64d00-102">Fel rapportering för cmdlet</span><span class="sxs-lookup"><span data-stu-id="64d00-102">Cmdlet error reporting</span></span>

<span data-ttu-id="64d00-103">-Cmdletar bör rapportera fel på olika sätt beroende på om felen avslutar fel eller om fel inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="64d00-103">Cmdlets should report errors differently depending on whether the errors are terminating errors or nonterminating errors.</span></span> <span data-ttu-id="64d00-104">Att avsluta fel är fel som leder till att pipelinen avslutas omedelbart eller fel som inträffar när det inte finns någon anledning att fortsätta att bearbeta.</span><span class="sxs-lookup"><span data-stu-id="64d00-104">Terminating errors are errors that cause the pipeline to be terminated immediately, or errors that occur when there's no reason to continue processing.</span></span> <span data-ttu-id="64d00-105">Fel som inte avslutas är de fel som rapporterar ett aktuellt fel tillstånd, men cmdleten kan fortsätta att bearbeta inobjekten.</span><span class="sxs-lookup"><span data-stu-id="64d00-105">Nonterminating errors are those errors that report a current error condition, but the cmdlet can continue to process input objects.</span></span> <span data-ttu-id="64d00-106">Om det inte finns några fel, meddelas användaren vanligt vis om problemet, men cmdleten fortsätter att bearbeta nästa indata-objekt.</span><span class="sxs-lookup"><span data-stu-id="64d00-106">With nonterminating errors, the user is typically notified of the problem, but the cmdlet continues to process the next input object.</span></span>

## <a name="terminating-and-nonterminating-errors"></a><span data-ttu-id="64d00-107">Avsluta och avbryta fel</span><span class="sxs-lookup"><span data-stu-id="64d00-107">Terminating and nonterminating errors</span></span>

<span data-ttu-id="64d00-108">Följande rikt linjer kan användas för att avgöra om ett fel tillstånd är ett avslutande fel eller ett fel som inte kan avslutas.</span><span class="sxs-lookup"><span data-stu-id="64d00-108">The following guidelines can be used to determine if an error condition is a terminating error or a nonterminating error.</span></span>

- <span data-ttu-id="64d00-109">Hindrar fel villkoret att din cmdlet bearbetar ytterligare indata-objekt?</span><span class="sxs-lookup"><span data-stu-id="64d00-109">Does the error condition prevent your cmdlet from successfully processing any further input objects?</span></span> <span data-ttu-id="64d00-110">I så fall är det ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="64d00-110">If so, this is a terminating error.</span></span>

- <span data-ttu-id="64d00-111">Är fel tillståndet relaterat till ett speciellt indatamängds objekt eller en delmängd av inobjekten?</span><span class="sxs-lookup"><span data-stu-id="64d00-111">Is the error condition related to a specific input object or a subset of input objects?</span></span> <span data-ttu-id="64d00-112">Om så är fallet, är det ett fel som inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="64d00-112">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="64d00-113">Accepterar cmdleten flera indata, så att bearbetningen kan lyckas på ett annat indata-objekt?</span><span class="sxs-lookup"><span data-stu-id="64d00-113">Does the cmdlet accept multiple input objects, such that processing may succeed on another input object?</span></span> <span data-ttu-id="64d00-114">Om så är fallet, är det ett fel som inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="64d00-114">If so, this is a nonterminating error.</span></span>

- <span data-ttu-id="64d00-115">-Cmdletar som kan acceptera flera inobjekt bör bestämma mellan vad som avslutas och inte avslutande fel, även om en viss situation endast gäller för ett enda inobjekt.</span><span class="sxs-lookup"><span data-stu-id="64d00-115">Cmdlets that can accept multiple input objects should decide between what are terminating and nonterminating errors, even when a particular situation applies to only a single input object.</span></span>

- <span data-ttu-id="64d00-116">Cmdletar kan ta emot valfritt antal inobjekt och skicka valfritt antal lyckade eller felaktiga objekt innan ett avslutande undantag utlöses.</span><span class="sxs-lookup"><span data-stu-id="64d00-116">Cmdlets can receive any number of input objects and send any number of success or error objects before throwing a terminating exception.</span></span> <span data-ttu-id="64d00-117">Det finns ingen relation mellan antalet mottagna inobjekt och antalet lyckade och felaktiga objekt som har skickats.</span><span class="sxs-lookup"><span data-stu-id="64d00-117">There's no relationship between the number of input objects received and the number of success and error objects sent.</span></span>

- <span data-ttu-id="64d00-118">Cmdletar som bara kan acceptera 0-1-indata-objekt och endast genererar 0-1-utdatafiler bör behandla fel som avslutas och generera undantags fel.</span><span class="sxs-lookup"><span data-stu-id="64d00-118">Cmdlets that can accept only 0-1 input objects and generate only 0-1 output objects should treat errors as terminating errors and generate terminating exceptions.</span></span>

## <a name="reporting-nonterminating-errors"></a><span data-ttu-id="64d00-119">Rapportera fel som inte avslutas</span><span class="sxs-lookup"><span data-stu-id="64d00-119">Reporting nonterminating errors</span></span>

<span data-ttu-id="64d00-120">Rapportering av ett fel som inte avslutas bör alltid utföras inom cmdletens implementering av metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) eller metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="64d00-120">The reporting of a nonterminating error should always be done within the cmdlet's implementation of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, or the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="64d00-121">Dessa typer av fel rapporteras genom att anropa metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , som i sin tur skickar en felpost till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="64d00-121">These types of errors are reported by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method that in turn sends an error record to the error stream.</span></span>

## <a name="reporting-terminating-errors"></a><span data-ttu-id="64d00-122">Rapportera avslutande fel</span><span class="sxs-lookup"><span data-stu-id="64d00-122">Reporting terminating errors</span></span>

<span data-ttu-id="64d00-123">Avslutande fel rapporteras genom att Utlös ande undantag eller genom att anropa metoden [system. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) .</span><span class="sxs-lookup"><span data-stu-id="64d00-123">Terminating errors are reported by throwing exceptions or by calling the [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="64d00-124">Tänk på att cmdlets också kan fånga upp och återanvända undantag, till exempel **OutOfMemory**, men de behöver inte rethrowa undantag eftersom PowerShell-körningen även kommer att fånga dem.</span><span class="sxs-lookup"><span data-stu-id="64d00-124">Be aware that cmdlets can also catch and rethrow exceptions such as **OutOfMemory**, however, they aren't required to rethrow exceptions as the PowerShell runtime will catch them as well.</span></span>

<span data-ttu-id="64d00-125">Du kan också definiera egna undantag för problem som är specifika för din situation eller lägga till ytterligare information i ett befintligt undantag med hjälp av fel posten.</span><span class="sxs-lookup"><span data-stu-id="64d00-125">You can also define your own exceptions for issues specific to your situation, or add additional information to an existing exception using its error record.</span></span>

## <a name="error-records"></a><span data-ttu-id="64d00-126">Fel poster</span><span class="sxs-lookup"><span data-stu-id="64d00-126">Error records</span></span>

<span data-ttu-id="64d00-127">PowerShell Beskriver ett fel tillstånd som inte avslutas med [system. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) -objekt.</span><span class="sxs-lookup"><span data-stu-id="64d00-127">PowerShell describes a nonterminating error condition with [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objects.</span></span> <span data-ttu-id="64d00-128">Varje-objekt innehåller information om fel kategori, ett valfritt mål objekt och information om fel tillståndet.</span><span class="sxs-lookup"><span data-stu-id="64d00-128">Each object provides error category information, an optional target object, and details about the error condition.</span></span>

### <a name="error-identifiers"></a><span data-ttu-id="64d00-129">Fel identifierare</span><span class="sxs-lookup"><span data-stu-id="64d00-129">Error identifiers</span></span>

<span data-ttu-id="64d00-130">Fel identifieraren är en enkel sträng som identifierar fel tillståndet i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="64d00-130">The error identifier is a simple string that identifies the error condition within the cmdlet.</span></span>
<span data-ttu-id="64d00-131">PowerShell kombinerar den här identifieraren med en cmdlet-identifierare för att skapa en fullständigt kvalificerad fel identifierare som kan användas senare vid filtrering av fel strömmar eller loggnings fel, vid svar på särskilda fel eller med andra användarspecifika aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="64d00-131">PowerShell combines this identifier with a cmdlet identifier to create a fully qualified error identifier that can be used later when filtering error streams or logging errors, when responding to specific errors, or with other user-specific activities.</span></span>

<span data-ttu-id="64d00-132">Följande rikt linjer bör följas när du anger fel identifierare:</span><span class="sxs-lookup"><span data-stu-id="64d00-132">The following guidelines should be followed when specifying error identifiers:</span></span>

- <span data-ttu-id="64d00-133">Tilldela olika kod Sök vägar olika, mycket detaljerade</span><span class="sxs-lookup"><span data-stu-id="64d00-133">Assign different, highly specific, error identifiers to different code paths.</span></span> <span data-ttu-id="64d00-134">Varje kod Sök väg som anropar [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) eller [system. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ska ha en egen fel identifierare.</span><span class="sxs-lookup"><span data-stu-id="64d00-134">Each code path that calls [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) or [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) should have its own error identifier.</span></span>

- <span data-ttu-id="64d00-135">Fel identifierare ska vara unika för CLR-typer (Common Language Runtime) för både avslutande och inte avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="64d00-135">Error identifiers should be unique to Common Language Runtime (CLR) exception types for both terminating and nonterminating errors.</span></span>

- <span data-ttu-id="64d00-136">Ändra inte semantiken för en fel identifierare mellan versioner av cmdleten eller PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="64d00-136">Don't change the semantics of an error identifier between versions of your cmdlet or PowerShell provider.</span></span> <span data-ttu-id="64d00-137">När semantiken för en fel identifierare har upprättats bör den vara konstant under hela livs cykeln för din cmdlet.</span><span class="sxs-lookup"><span data-stu-id="64d00-137">After the semantics of an error identifier is established, it should remain constant throughout the lifecycle of your cmdlet.</span></span>

- <span data-ttu-id="64d00-138">Om du vill avbryta fel använder du en unik fel identifierare för en viss CLR-undantags typ.</span><span class="sxs-lookup"><span data-stu-id="64d00-138">For terminating errors, use a unique error identifier for a particular CLR exception type.</span></span> <span data-ttu-id="64d00-139">Om undantags typen ändras använder du en ny fel-ID.</span><span class="sxs-lookup"><span data-stu-id="64d00-139">If the exception type changes, use a new error identifier.</span></span>

- <span data-ttu-id="64d00-140">Använd en unik fel identifierare för ett bestämt inobjekt för att avbryta fel.</span><span class="sxs-lookup"><span data-stu-id="64d00-140">For nonterminating errors, use a specific error identifier for a specific input object.</span></span>

- <span data-ttu-id="64d00-141">Välj text för den identifierare som tersely motsvarar det fel som rapporteras.</span><span class="sxs-lookup"><span data-stu-id="64d00-141">Choose text for the identifier that tersely corresponds to the error being reported.</span></span> <span data-ttu-id="64d00-142">Använd inte blank steg eller skiljetecken.</span><span class="sxs-lookup"><span data-stu-id="64d00-142">Don't use white space or punctuation.</span></span>

- <span data-ttu-id="64d00-143">Generera inte fel identifierare som inte är nyproducerade.</span><span class="sxs-lookup"><span data-stu-id="64d00-143">Don't generate error identifiers that aren't reproducible.</span></span> <span data-ttu-id="64d00-144">Generera till exempel inte identifierare som innehåller en process identifierare.</span><span class="sxs-lookup"><span data-stu-id="64d00-144">For example, don't generate identifiers that include a process identifier.</span></span> <span data-ttu-id="64d00-145">Fel identifierare är bara användbara när de motsvarar identifierare som visas av andra användare som har samma problem.</span><span class="sxs-lookup"><span data-stu-id="64d00-145">Error identifiers are useful only when they correspond to identifiers that are seen by other users who are experiencing the same problem.</span></span>

### <a name="error-categories"></a><span data-ttu-id="64d00-146">Fel kategorier</span><span class="sxs-lookup"><span data-stu-id="64d00-146">Error categories</span></span>

<span data-ttu-id="64d00-147">Fel kategorier används för att gruppera fel för användaren.</span><span class="sxs-lookup"><span data-stu-id="64d00-147">Error categories are used to group errors for the user.</span></span> <span data-ttu-id="64d00-148">PowerShell definierar dessa kategorier och cmdlets och PowerShell-leverantörer måste välja mellan dem när fel posten skapas.</span><span class="sxs-lookup"><span data-stu-id="64d00-148">PowerShell defines these categories and cmdlets and PowerShell providers must choose between them when generating the error record.</span></span>

<span data-ttu-id="64d00-149">En beskrivning av de fel kategorier som är tillgängliga finns i uppräkningen [system. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) .</span><span class="sxs-lookup"><span data-stu-id="64d00-149">For a description of the error categories that are available, see the [System.Management.Automation.ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="64d00-150">I allmänhet bör du undvika att använda **noerror**, **UndefinedError**och **GenericError** när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="64d00-150">In general, you should avoid using **NoError**, **UndefinedError**, and **GenericError** whenever possible.</span></span>

<span data-ttu-id="64d00-151">Användare kan visa fel baserat på kategori när de anger `$ErrorView` till **CategoryView**.</span><span class="sxs-lookup"><span data-stu-id="64d00-151">Users can view errors based on category when they set `$ErrorView` to **CategoryView**.</span></span>

## <a name="see-also"></a><span data-ttu-id="64d00-152">Se även</span><span class="sxs-lookup"><span data-stu-id="64d00-152">See also</span></span>

[<span data-ttu-id="64d00-153">Cmdlet-översikt</span><span class="sxs-lookup"><span data-stu-id="64d00-153">Cmdlet Overview</span></span>](./cmdlet-overview.md)

[<span data-ttu-id="64d00-154">Typer av cmdlet-utdata</span><span class="sxs-lookup"><span data-stu-id="64d00-154">Types of Cmdlet Output</span></span>](./types-of-cmdlet-output.md)

[<span data-ttu-id="64d00-155">Windows PowerShell-referens</span><span class="sxs-lookup"><span data-stu-id="64d00-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)
