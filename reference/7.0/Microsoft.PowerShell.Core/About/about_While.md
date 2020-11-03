---
description: Beskriver en språk instruktion som du kan använda för att köra ett kommando block baserat på resultatet av ett villkorligt test.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 4008c1c8738b6911949d79882cc6909be2edbe97
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271154"
---
# <a name="about-while"></a><span data-ttu-id="ff6cc-104">Om medan</span><span class="sxs-lookup"><span data-stu-id="ff6cc-104">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="ff6cc-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ff6cc-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ff6cc-106">Beskriver en språk instruktion som du kan använda för att köra ett kommando block baserat på resultatet av ett villkorligt test.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-106">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="ff6cc-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ff6cc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ff6cc-108">While-instruktionen (kallas även en while-loop) är en språk konstruktion för att skapa en loop som kör kommandon i ett kommando block så länge ett villkorligt test utvärderas till true.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-108">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="ff6cc-109">While-instruktionen är enklare att konstruera än en for-instruktion eftersom dess syntax är mindre komplicerad.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-109">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="ff6cc-110">Dessutom är det mer flexibelt än den förskotts instruktionen eftersom du anger ett villkorsstyrt test i while-instruktionen för att styra hur många gånger slingan körs.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-110">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="ff6cc-111">Följande visar syntaxen för while-uttrycket:</span><span class="sxs-lookup"><span data-stu-id="ff6cc-111">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="ff6cc-112">När du kör en while-instruktion utvärderar PowerShell `<condition>` avsnittet i instruktionen innan du anger `<statement list>` avsnittet.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-112">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="ff6cc-113">Villkors delen i instruktionen matchar antingen sant eller falskt.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-113">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="ff6cc-114">Så länge villkoret är sant, kör PowerShell avsnittet igen `<statement list>` .</span><span class="sxs-lookup"><span data-stu-id="ff6cc-114">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="ff6cc-115">`<statement list>`Avsnittet i instruktionen innehåller ett eller flera kommandon som körs varje gången loopen anges eller upprepas.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-115">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="ff6cc-116">Till exempel visar följande while-uttryck talen 1 till 3 om variabeln $val inte har skapats eller om $val-variabeln har skapats och initierats till 0.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-116">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="ff6cc-117">I det här exemplet är villkoret ($val inte lika med 3) sant när $val \= 0, 1, 2.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-117">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="ff6cc-118">Varje gången genom loopen ökas $val med 1 med hjälp av den \+ \+ unära öknings operatorn ($val \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="ff6cc-118">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="ff6cc-119">Sista gången genom loopen $val \= 3.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-119">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="ff6cc-120">När $val är lika med 3, utvärderas villkors uttrycket till false och loopen avslutas.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-120">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="ff6cc-121">Om du vill skriva detta kommando i PowerShell-kommandotolken kan du ange det på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ff6cc-121">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="ff6cc-122">Observera att semikolonet separerar det första kommandot som lägger till 1 $val från det andra kommandot som skriver värdet för $val till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ff6cc-122">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff6cc-123">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="ff6cc-123">SEE ALSO</span></span>

[<span data-ttu-id="ff6cc-124">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="ff6cc-124">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="ff6cc-125">about_Do</span><span class="sxs-lookup"><span data-stu-id="ff6cc-125">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="ff6cc-126">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="ff6cc-126">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="ff6cc-127">about_For</span><span class="sxs-lookup"><span data-stu-id="ff6cc-127">about_For</span></span>](about_For.md)

[<span data-ttu-id="ff6cc-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="ff6cc-128">about_Language_Keywords</span></span>](about_Language_Keywords.md)
