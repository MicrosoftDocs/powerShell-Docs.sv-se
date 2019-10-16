---
title: Ge stöd för jokertecken i cmdlet-parametrar
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356142"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="bdf7f-102">Ge stöd för jokertecken i cmdlet-parametrar</span><span class="sxs-lookup"><span data-stu-id="bdf7f-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="bdf7f-103">Du måste ofta utforma en cmdlet för att kunna köras mot en grupp resurser i stället för till en enda resurs.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="bdf7f-104">En cmdlet kan till exempel behöva hitta alla filer i ett data lager som har samma namn eller tillägg.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="bdf7f-105">Du måste ge stöd för jokertecken när du skapar en cmdlet som ska köras mot en grupp med resurser.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="bdf7f-106">Användning av jokertecken kallas ibland *globbing*.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="bdf7f-107">Windows PowerShell-cmdletar som använder jokertecken</span><span class="sxs-lookup"><span data-stu-id="bdf7f-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="bdf7f-108">Många Windows PowerShell-cmdlets stöder jokertecken för sina parameter värden.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="bdf7f-109">Till exempel, nästan alla cmdletar som har en `Name`-eller `Path`-parameter stöder jokertecken för dessa parametrar.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="bdf7f-110">(Även om de flesta cmdletar som har en `Path`-parameter också har en `LiteralPath`-parameter som inte har stöd för jokertecken.) Följande kommando visar hur ett jokertecken används för att returnera alla cmdletar i den aktuella sessionen vars namn innehåller verbet get.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="bdf7f-111">Jokertecken som stöds</span><span class="sxs-lookup"><span data-stu-id="bdf7f-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="bdf7f-112">Windows PowerShell stöder följande jokertecken.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="bdf7f-113">Användning</span><span class="sxs-lookup"><span data-stu-id="bdf7f-113">Wildcard</span></span> |                             <span data-ttu-id="bdf7f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bdf7f-114">Description</span></span>                             |  <span data-ttu-id="bdf7f-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="bdf7f-115">Example</span></span>   |     <span data-ttu-id="bdf7f-116">Matchningar</span><span class="sxs-lookup"><span data-stu-id="bdf7f-116">Matches</span></span>      | <span data-ttu-id="bdf7f-117">Matchar inte</span><span class="sxs-lookup"><span data-stu-id="bdf7f-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="bdf7f-118">Matchar noll eller flera tecken, med början vid den angivna positionen</span><span class="sxs-lookup"><span data-stu-id="bdf7f-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="bdf7f-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="bdf7f-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="bdf7f-120">?</span><span class="sxs-lookup"><span data-stu-id="bdf7f-120">?</span></span>        | <span data-ttu-id="bdf7f-121">Matchar alla bokstäver vid angiven position</span><span class="sxs-lookup"><span data-stu-id="bdf7f-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="bdf7f-122">En, i, på</span><span class="sxs-lookup"><span data-stu-id="bdf7f-122">An, in, on</span></span>       | <span data-ttu-id="bdf7f-123">kördes</span><span class="sxs-lookup"><span data-stu-id="bdf7f-123">ran</span></span>            |
| <span data-ttu-id="bdf7f-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="bdf7f-124">[ ]</span></span>      | <span data-ttu-id="bdf7f-125">Matchar ett tecken intervall</span><span class="sxs-lookup"><span data-stu-id="bdf7f-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="bdf7f-126">bok, Cook, utseende</span><span class="sxs-lookup"><span data-stu-id="bdf7f-126">book, cook, look</span></span> | <span data-ttu-id="bdf7f-127">Nook, vidtog</span><span class="sxs-lookup"><span data-stu-id="bdf7f-127">nook, took</span></span>     |
| <span data-ttu-id="bdf7f-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="bdf7f-128">[ ]</span></span>      | <span data-ttu-id="bdf7f-129">Matchar de angivna tecknen</span><span class="sxs-lookup"><span data-stu-id="bdf7f-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="bdf7f-130">bok, Nook</span><span class="sxs-lookup"><span data-stu-id="bdf7f-130">book, nook</span></span>       | <span data-ttu-id="bdf7f-131">laga, titta</span><span class="sxs-lookup"><span data-stu-id="bdf7f-131">cook, look</span></span>     |

<span data-ttu-id="bdf7f-132">När du utformar cmdletar som stöder jokertecken kan du använda kombinationer av jokertecken.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="bdf7f-133">Följande kommando använder exempelvis cmdleten `Get-ChildItem` för att hämta alla. txt-filer som finns i mappen c:\Techdocs och som börjar med bokstäverna "a" till "l".</span><span class="sxs-lookup"><span data-stu-id="bdf7f-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="bdf7f-134">Föregående kommando använder jokertecknet `[a-l]` för att ange att fil namnet ska börja med tecknen "a" till och med "l" och använder jokertecknet `*` som plats hållare för alla tecken mellan den första bokstaven i fil namnet och **. txt** tillägg.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="bdf7f-135">I följande exempel används ett mönster med jokertecken som utesluter bokstaven "d", men innehåller alla andra bokstäver från "a" till "f".</span><span class="sxs-lookup"><span data-stu-id="bdf7f-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="bdf7f-136">Hantera tecken i mönster med jokertecken</span><span class="sxs-lookup"><span data-stu-id="bdf7f-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="bdf7f-137">Om det jokertecken du anger innehåller litterala tecken som inte ska tolkas som jokertecken använder du bakstrecks tecknet (`` ` ``) som ett escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="bdf7f-138">Om du anger litterala tecken int PowerShell-API: et använder du ett enda baktick.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="bdf7f-139">Använd två baktick när du anger litterala tecken i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="bdf7f-140">Följande mönster innehåller till exempel två hakparenteser som måste beaktas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="bdf7f-141">När det används i PowerShell-API: et använder du:</span><span class="sxs-lookup"><span data-stu-id="bdf7f-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="bdf7f-142">"John Svensson \` [\*]"</span><span class="sxs-lookup"><span data-stu-id="bdf7f-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="bdf7f-143">När det används från PowerShell-Kommandotolken:</span><span class="sxs-lookup"><span data-stu-id="bdf7f-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="bdf7f-144">"John Svensson \` @ no__t-1 [\* \`"] "</span><span class="sxs-lookup"><span data-stu-id="bdf7f-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="bdf7f-145">Det här mönstret matchar "John Svensson [Marketing]" eller "John Svensson [Development]".</span><span class="sxs-lookup"><span data-stu-id="bdf7f-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="bdf7f-146">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="bdf7f-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="bdf7f-147">Cmdlet-utdata och jokertecken</span><span class="sxs-lookup"><span data-stu-id="bdf7f-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="bdf7f-148">När cmdlet-parametrarna har stöd för jokertecken genererar åtgärden vanligt vis en mat ris utmatning.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="bdf7f-149">Ibland är det ingen mening att stödja mat ris utdata eftersom användaren bara kan använda ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="bdf7f-150">Till exempel stöder inte cmdleten `Set-Location` mat ris utdata eftersom användaren bara anger en enda plats.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="bdf7f-151">I den här instansen stöder cmdlet: en fortfarande jokertecken, men den framtvingar matchning till en enda plats.</span><span class="sxs-lookup"><span data-stu-id="bdf7f-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdf7f-152">Se även</span><span class="sxs-lookup"><span data-stu-id="bdf7f-152">See Also</span></span>

[<span data-ttu-id="bdf7f-153">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="bdf7f-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="bdf7f-154">WildcardPattern-klass</span><span class="sxs-lookup"><span data-stu-id="bdf7f-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
