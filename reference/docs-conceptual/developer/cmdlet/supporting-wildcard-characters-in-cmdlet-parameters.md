---
ms.date: 08/26/2019
ms.topic: reference
title: Ge stöd för jokertecken i cmdlet-parametrar
description: Ge stöd för jokertecken i cmdlet-parametrar
ms.openlocfilehash: 06693c62cd2613050bdeb9d6b12ad6e9597a9894
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646389"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="a64c2-103">Ge stöd för jokertecken i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="a64c2-103">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="a64c2-104">Du måste ofta utforma en cmdlet för att kunna köras mot en grupp resurser i stället för till en enda resurs.</span><span class="sxs-lookup"><span data-stu-id="a64c2-104">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="a64c2-105">En cmdlet kan till exempel behöva hitta alla filer i ett data lager som har samma namn eller tillägg.</span><span class="sxs-lookup"><span data-stu-id="a64c2-105">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="a64c2-106">Du måste ge stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.</span><span class="sxs-lookup"><span data-stu-id="a64c2-106">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="a64c2-107">Användning av jokertecken kallas ibland *globbing* .</span><span class="sxs-lookup"><span data-stu-id="a64c2-107">Using wildcard characters is sometimes referred to as *globbing* .</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="a64c2-108">Windows PowerShell-cmdletar som använder jokertecken</span><span class="sxs-lookup"><span data-stu-id="a64c2-108">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="a64c2-109">Många Windows PowerShell-cmdlets stöder jokertecken för sina parameter värden.</span><span class="sxs-lookup"><span data-stu-id="a64c2-109">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="a64c2-110">Till exempel nästan alla cmdletar som har en- `Name` eller- `Path` parameter stöder jokertecken för dessa parametrar.</span><span class="sxs-lookup"><span data-stu-id="a64c2-110">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="a64c2-111">(Även om de flesta cmdletar som har en `Path` parameter också har en `LiteralPath` parameter som inte stöder jokertecken.) Följande kommando visar hur ett jokertecken används för att returnera alla cmdletar i den aktuella sessionen vars namn innehåller verbet get.</span><span class="sxs-lookup"><span data-stu-id="a64c2-111">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="a64c2-112">Jokertecken som stöds</span><span class="sxs-lookup"><span data-stu-id="a64c2-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="a64c2-113">Windows PowerShell stöder följande jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a64c2-113">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="a64c2-114">Användning</span><span class="sxs-lookup"><span data-stu-id="a64c2-114">Wildcard</span></span> |                             <span data-ttu-id="a64c2-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a64c2-115">Description</span></span>                             |  <span data-ttu-id="a64c2-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="a64c2-116">Example</span></span>   |     <span data-ttu-id="a64c2-117">Matchar</span><span class="sxs-lookup"><span data-stu-id="a64c2-117">Matches</span></span>      | <span data-ttu-id="a64c2-118">Matchar inte</span><span class="sxs-lookup"><span data-stu-id="a64c2-118">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="a64c2-119">Matchar noll eller flera tecken, med början vid den angivna positionen</span><span class="sxs-lookup"><span data-stu-id="a64c2-119">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="a64c2-120">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="a64c2-120">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="a64c2-121">?</span><span class="sxs-lookup"><span data-stu-id="a64c2-121">?</span></span>        | <span data-ttu-id="a64c2-122">Matchar alla bokstäver vid angiven position</span><span class="sxs-lookup"><span data-stu-id="a64c2-122">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="a64c2-123">En, i, på</span><span class="sxs-lookup"><span data-stu-id="a64c2-123">An, in, on</span></span>       | <span data-ttu-id="a64c2-124">kördes</span><span class="sxs-lookup"><span data-stu-id="a64c2-124">ran</span></span>            |
| <span data-ttu-id="a64c2-125">[ ]</span><span class="sxs-lookup"><span data-stu-id="a64c2-125">[ ]</span></span>      | <span data-ttu-id="a64c2-126">Matchar ett tecken intervall</span><span class="sxs-lookup"><span data-stu-id="a64c2-126">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="a64c2-127">bok, Cook, utseende</span><span class="sxs-lookup"><span data-stu-id="a64c2-127">book, cook, look</span></span> | <span data-ttu-id="a64c2-128">Nook, vidtog</span><span class="sxs-lookup"><span data-stu-id="a64c2-128">nook, took</span></span>     |
| <span data-ttu-id="a64c2-129">[ ]</span><span class="sxs-lookup"><span data-stu-id="a64c2-129">[ ]</span></span>      | <span data-ttu-id="a64c2-130">Matchar de angivna tecknen</span><span class="sxs-lookup"><span data-stu-id="a64c2-130">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="a64c2-131">bok, Nook</span><span class="sxs-lookup"><span data-stu-id="a64c2-131">book, nook</span></span>       | <span data-ttu-id="a64c2-132">laga, titta</span><span class="sxs-lookup"><span data-stu-id="a64c2-132">cook, look</span></span>     |

<span data-ttu-id="a64c2-133">När du utformar cmdletar som stöder jokertecken kan du använda kombinationer av jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a64c2-133">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="a64c2-134">Följande kommando använder till exempel `Get-ChildItem` cmdleten för att hämta alla. txt-filer som finns i mappen c:\Techdocs och som börjar med bokstäverna "a" till "l".</span><span class="sxs-lookup"><span data-stu-id="a64c2-134">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="a64c2-135">Föregående kommando använder området jokertecken `[a-l]` för att ange att fil namnet ska börja med tecknen "a" till och med "l" och använder `*` jokertecknet som plats hållare för alla tecken mellan den första bokstaven i fil namnet och **. txt** -tillägget.</span><span class="sxs-lookup"><span data-stu-id="a64c2-135">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="a64c2-136">I följande exempel används ett mönster med jokertecken som utesluter bokstaven "d", men innehåller alla andra bokstäver från "a" till "f".</span><span class="sxs-lookup"><span data-stu-id="a64c2-136">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="a64c2-137">Hantera tecken i mönster med jokertecken</span><span class="sxs-lookup"><span data-stu-id="a64c2-137">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="a64c2-138">Om det jokertecken du anger innehåller litterala tecken som inte ska tolkas som jokertecken använder du bakstrecks tecknet ( `` ` `` ) som ett escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="a64c2-138">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="a64c2-139">Om du anger litterala tecken int PowerShell-API: et använder du ett enda baktick.</span><span class="sxs-lookup"><span data-stu-id="a64c2-139">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="a64c2-140">Använd två baktick när du anger litterala tecken i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="a64c2-140">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="a64c2-141">Följande mönster innehåller till exempel två hakparenteser som måste beaktas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="a64c2-141">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="a64c2-142">När det används i PowerShell-API: et använder du:</span><span class="sxs-lookup"><span data-stu-id="a64c2-142">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="a64c2-143">"John Svensson \` [\*"] "</span><span class="sxs-lookup"><span data-stu-id="a64c2-143">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="a64c2-144">När det används från PowerShell-Kommandotolken:</span><span class="sxs-lookup"><span data-stu-id="a64c2-144">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="a64c2-145">"John Svensson \` \` [\* \` "] "</span><span class="sxs-lookup"><span data-stu-id="a64c2-145">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="a64c2-146">Det här mönstret matchar "John Svensson [Marketing]" eller "John Svensson [Development]".</span><span class="sxs-lookup"><span data-stu-id="a64c2-146">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="a64c2-147">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a64c2-147">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="a64c2-148">Cmdlet-utdata och jokertecken</span><span class="sxs-lookup"><span data-stu-id="a64c2-148">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="a64c2-149">När cmdlet-parametrarna har stöd för jokertecken genererar åtgärden vanligt vis en mat ris utmatning.</span><span class="sxs-lookup"><span data-stu-id="a64c2-149">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="a64c2-150">Ibland är det ingen mening att stödja mat ris utdata eftersom användaren bara kan använda ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="a64c2-150">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="a64c2-151">Till exempel `Set-Location` stöder cmdleten inte mat ris utdata eftersom användaren bara anger en enda plats.</span><span class="sxs-lookup"><span data-stu-id="a64c2-151">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="a64c2-152">I den här instansen stöder cmdlet: en fortfarande jokertecken, men den framtvingar matchning till en enda plats.</span><span class="sxs-lookup"><span data-stu-id="a64c2-152">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="a64c2-153">Se även</span><span class="sxs-lookup"><span data-stu-id="a64c2-153">See Also</span></span>

[<span data-ttu-id="a64c2-154">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="a64c2-154">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="a64c2-155">WildcardPattern-klass</span><span class="sxs-lookup"><span data-stu-id="a64c2-155">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
