---
title: Stöd för jokertecken i Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059617"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="961d3-102">Ge stöd för jokertecken i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="961d3-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="961d3-103">Du får ofta att utforma en cmdlet för att köra mot en grupp med resurser i stället för mot en enskild resurs.</span><span class="sxs-lookup"><span data-stu-id="961d3-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="961d3-104">Till exempel behöva en cmdlet att hitta alla filer i ett datalager som har samma namn eller tillägg.</span><span class="sxs-lookup"><span data-stu-id="961d3-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="961d3-105">Du måste tillhandahålla support för jokertecken när du utformar en cmdlet som ska köras mot en grupp med resurser.</span><span class="sxs-lookup"><span data-stu-id="961d3-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="961d3-106">Använda jokertecken är kallas ibland *globbing*.</span><span class="sxs-lookup"><span data-stu-id="961d3-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="961d3-107">Windows PowerShell-cmdletar som använder jokertecken</span><span class="sxs-lookup"><span data-stu-id="961d3-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="961d3-108">Många Windows PowerShell-cmdletar stöder jokertecken för sina parametervärden.</span><span class="sxs-lookup"><span data-stu-id="961d3-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="961d3-109">Till exempel nästan alla cmdlet som har en `Name` eller `Path` parametern har stöd för jokertecken för dessa parametrar.</span><span class="sxs-lookup"><span data-stu-id="961d3-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="961d3-110">(Även om de flesta cmdletar som har en `Path` parametern också ha en `LiteralPath` parameter som inte stöder jokertecken.) Följande kommando visar hur ett jokertecken används för att returnera alla cmdletar i den aktuella sessionen vars namn innehåller Get-verbet.</span><span class="sxs-lookup"><span data-stu-id="961d3-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="961d3-111">**PS > get-kommandot get -\***</span><span class="sxs-lookup"><span data-stu-id="961d3-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="961d3-112">Jokertecken stöds</span><span class="sxs-lookup"><span data-stu-id="961d3-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="961d3-113">Windows PowerShell har stöd för följande jokertecken.</span><span class="sxs-lookup"><span data-stu-id="961d3-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="961d3-114">Jokertecken</span><span class="sxs-lookup"><span data-stu-id="961d3-114">Wildcard character</span></span>|<span data-ttu-id="961d3-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="961d3-115">Description</span></span>|<span data-ttu-id="961d3-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="961d3-116">Example</span></span>|<span data-ttu-id="961d3-117">Matchningar</span><span class="sxs-lookup"><span data-stu-id="961d3-117">Matches</span></span>|<span data-ttu-id="961d3-118">Matchar inte</span><span class="sxs-lookup"><span data-stu-id="961d3-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="961d3-119">Matchar noll eller flera tecken, med början vid den angivna positionen</span><span class="sxs-lookup"><span data-stu-id="961d3-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="961d3-120">a\*</span><span class="sxs-lookup"><span data-stu-id="961d3-120">a\*</span></span>|<span data-ttu-id="961d3-121">En, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="961d3-121">A, ag, Apple</span></span>||
|<span data-ttu-id="961d3-122">?</span><span class="sxs-lookup"><span data-stu-id="961d3-122">?</span></span>|<span data-ttu-id="961d3-123">Matchningar anycharacter vid den angivna positionen</span><span class="sxs-lookup"><span data-stu-id="961d3-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="961d3-124">?n</span><span class="sxs-lookup"><span data-stu-id="961d3-124">?n</span></span>|<span data-ttu-id="961d3-125">En i, på</span><span class="sxs-lookup"><span data-stu-id="961d3-125">An, in, on</span></span>|<span data-ttu-id="961d3-126">kördes</span><span class="sxs-lookup"><span data-stu-id="961d3-126">ran</span></span>|
|<span data-ttu-id="961d3-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="961d3-127">[ ]</span></span>|<span data-ttu-id="961d3-128">Matchar ett teckenintervall</span><span class="sxs-lookup"><span data-stu-id="961d3-128">Matches a range of characters</span></span>|<span data-ttu-id="961d3-129">[a-l]ook</span><span class="sxs-lookup"><span data-stu-id="961d3-129">[a-l]ook</span></span>|<span data-ttu-id="961d3-130">bok, Cooköarna, utseende</span><span class="sxs-lookup"><span data-stu-id="961d3-130">book, cook, look</span></span>|<span data-ttu-id="961d3-131">tog</span><span class="sxs-lookup"><span data-stu-id="961d3-131">took</span></span>|
|<span data-ttu-id="961d3-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="961d3-132">[ ]</span></span>|<span data-ttu-id="961d3-133">Matchar de angivna tecken</span><span class="sxs-lookup"><span data-stu-id="961d3-133">Matches the specified characters</span></span>|<span data-ttu-id="961d3-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="961d3-134">[bc]ook</span></span>|<span data-ttu-id="961d3-135">bok, Cooköarna</span><span class="sxs-lookup"><span data-stu-id="961d3-135">book, cook</span></span>|<span data-ttu-id="961d3-136">Titta</span><span class="sxs-lookup"><span data-stu-id="961d3-136">look</span></span>|

<span data-ttu-id="961d3-137">När du utformar cmdletar som stöder jokertecken Tillåt kombinationer av jokertecken.</span><span class="sxs-lookup"><span data-stu-id="961d3-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="961d3-138">Till exempel följande kommando använder de `Get-ChildItem` cmdlet för att hämta alla txt-filer som finns i mappen c:\Techdocs och som börjar med ”a” till ”l”.</span><span class="sxs-lookup"><span data-stu-id="961d3-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="961d3-139">**Get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="961d3-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="961d3-140">Föregående kommando använder jokertecknet intervallet **[a-l]** att ange att filnamnet ska börja med tecknen ”a” till ”l”.</span><span class="sxs-lookup"><span data-stu-id="961d3-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="961d3-141">Kommandot använder sedan den \* jokertecknet som platshållare för några tecken mellan den första bokstaven i filnamnet och filnamnstillägget .txt.</span><span class="sxs-lookup"><span data-stu-id="961d3-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="961d3-142">I följande exempel används ett intervall med jokerteckensmönster som utesluter bokstaven ”d” men innehåller alla andra bokstäver från ”a” till ”f”.</span><span class="sxs-lookup"><span data-stu-id="961d3-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="961d3-143">**Get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="961d3-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="961d3-144">Hantering av vanliga tecken i mönster med jokertecken</span><span class="sxs-lookup"><span data-stu-id="961d3-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="961d3-145">Om mönstret med jokertecken som du anger innehåller vanliga tecken, använder du backtick citattecken (') som escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="961d3-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="961d3-146">När du anger strängtecken programmässigt kan du använda en enda backtick.</span><span class="sxs-lookup"><span data-stu-id="961d3-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="961d3-147">När du anger strängtecken i Kommandotolken, använder du två grava accenter.</span><span class="sxs-lookup"><span data-stu-id="961d3-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="961d3-148">Följande mönster innehåller till exempel två hakparenteser som måste vidtas bokstavligt.</span><span class="sxs-lookup"><span data-stu-id="961d3-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="961d3-149">”John Smith \`[\*”] ”(anges via programmering)</span><span class="sxs-lookup"><span data-stu-id="961d3-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="961d3-150">”John Smith \` \`[\*\`”] ”(som anges i Kommandotolken)</span><span class="sxs-lookup"><span data-stu-id="961d3-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="961d3-151">Det här mönstret matchar ”John Smith [marknadsföring]” eller ”John Smith [utveckling]”.</span><span class="sxs-lookup"><span data-stu-id="961d3-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="961d3-152">Cmdlet-utdata och jokertecken</span><span class="sxs-lookup"><span data-stu-id="961d3-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="961d3-153">Om cmdlet-parametrarna har stöd för jokertecken, genererar en cmdlet-åtgärd vanligtvis matrisutdata.</span><span class="sxs-lookup"><span data-stu-id="961d3-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="961d3-154">Ibland kan det vara bra utan att stödja en matris som utdata eftersom användaren kan använda endast en post i taget.</span><span class="sxs-lookup"><span data-stu-id="961d3-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="961d3-155">Till exempel den `Set-Location` cmdlet har stöd för en matris som utdata eftersom användaren anger en enda plats.</span><span class="sxs-lookup"><span data-stu-id="961d3-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="961d3-156">Cmdlet: en har fortfarande stöd för jokertecken i den här instansen, men tvingas av lösningen till en enda plats.</span><span class="sxs-lookup"><span data-stu-id="961d3-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="961d3-157">Se även</span><span class="sxs-lookup"><span data-stu-id="961d3-157">See Also</span></span>

[<span data-ttu-id="961d3-158">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="961d3-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="961d3-159">WildcardPattern-klass</span><span class="sxs-lookup"><span data-stu-id="961d3-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
