---
description: Beskriver en språk instruktion som du kan använda för att köra ett kommando block baserat på resultatet av ett villkorligt test.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 37c277a5919ba5fc39f953e05edaf58d159f3e7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709661"
---
# <a name="about-while"></a><span data-ttu-id="2c91c-103">Om medan</span><span class="sxs-lookup"><span data-stu-id="2c91c-103">About While</span></span>

## <a name="short-description"></a><span data-ttu-id="2c91c-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2c91c-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="2c91c-105">Beskriver en språk instruktion som du kan använda för att köra ett kommando block baserat på resultatet av ett villkorligt test.</span><span class="sxs-lookup"><span data-stu-id="2c91c-105">Describes a language statement that you can use to run a command block based on the results of a conditional test.</span></span>

## <a name="long-description"></a><span data-ttu-id="2c91c-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2c91c-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="2c91c-107">While-instruktionen (kallas även en while-loop) är en språk konstruktion för att skapa en loop som kör kommandon i ett kommando block så länge ett villkorligt test utvärderas till true.</span><span class="sxs-lookup"><span data-stu-id="2c91c-107">The While statement (also known as a While loop) is a language construct for creating a loop that runs commands in a command block as long as a conditional test evaluates to true.</span></span> <span data-ttu-id="2c91c-108">While-instruktionen är enklare att konstruera än en for-instruktion eftersom dess syntax är mindre komplicerad.</span><span class="sxs-lookup"><span data-stu-id="2c91c-108">The While statement is easier to construct than a For statement because its syntax is less complicated.</span></span> <span data-ttu-id="2c91c-109">Dessutom är det mer flexibelt än den förskotts instruktionen eftersom du anger ett villkorsstyrt test i while-instruktionen för att styra hur många gånger slingan körs.</span><span class="sxs-lookup"><span data-stu-id="2c91c-109">In addition, it is more flexible than the Foreach statement because you specify a conditional test in the While statement to control how many times the loop runs.</span></span>

<span data-ttu-id="2c91c-110">Följande visar syntaxen för while-uttrycket:</span><span class="sxs-lookup"><span data-stu-id="2c91c-110">The following shows the While statement syntax:</span></span>

```powershell
while (<condition>){<statement list>}
```

<span data-ttu-id="2c91c-111">När du kör en while-instruktion utvärderar PowerShell `<condition>` avsnittet i instruktionen innan du anger `<statement list>` avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2c91c-111">When you run a While statement, PowerShell evaluates the `<condition>` section of the statement before entering the `<statement list>` section.</span></span> <span data-ttu-id="2c91c-112">Villkors delen i instruktionen matchar antingen sant eller falskt.</span><span class="sxs-lookup"><span data-stu-id="2c91c-112">The condition portion of the statement resolves to either true or false.</span></span> <span data-ttu-id="2c91c-113">Så länge villkoret är sant, kör PowerShell avsnittet igen `<statement list>` .</span><span class="sxs-lookup"><span data-stu-id="2c91c-113">As long as the condition remains true, PowerShell reruns the `<statement list>` section.</span></span>

<span data-ttu-id="2c91c-114">`<statement list>`Avsnittet i instruktionen innehåller ett eller flera kommandon som körs varje gången loopen anges eller upprepas.</span><span class="sxs-lookup"><span data-stu-id="2c91c-114">The `<statement list>` section of the statement contains one or more commands that are run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="2c91c-115">Till exempel visar följande while-uttryck talen 1 till 3 om variabeln $val inte har skapats eller om $val-variabeln har skapats och initierats till 0.</span><span class="sxs-lookup"><span data-stu-id="2c91c-115">For example, the following While statement displays the numbers 1 through 3 if the $val variable has not been created or if the $val variable has been created and initialized to 0.</span></span>

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

<span data-ttu-id="2c91c-116">I det här exemplet är villkoret ($val inte lika med 3) sant när $val \= 0, 1, 2.</span><span class="sxs-lookup"><span data-stu-id="2c91c-116">In this example, the condition ($val is not equal to 3) is true while $val \= 0, 1, 2.</span></span> <span data-ttu-id="2c91c-117">Varje gången genom loopen ökas $val med 1 med hjälp av den \+ \+ unära öknings operatorn ($val \+ \+ ).</span><span class="sxs-lookup"><span data-stu-id="2c91c-117">Each time through the loop, $val is incremented by 1 using the \+\+ unary increment operator ($val\+\+).</span></span> <span data-ttu-id="2c91c-118">Sista gången genom loopen $val \= 3.</span><span class="sxs-lookup"><span data-stu-id="2c91c-118">The last time through the loop, $val \= 3.</span></span> <span data-ttu-id="2c91c-119">När $val är lika med 3, utvärderas villkors uttrycket till false och loopen avslutas.</span><span class="sxs-lookup"><span data-stu-id="2c91c-119">When $val equals 3, the condition statement evaluates to false, and the loop exits.</span></span>

<span data-ttu-id="2c91c-120">Om du vill skriva detta kommando i PowerShell-kommandotolken kan du ange det på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="2c91c-120">To conveniently write this command at the PowerShell command prompt, you can enter it in the following way:</span></span>

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

<span data-ttu-id="2c91c-121">Observera att semikolonet separerar det första kommandot som lägger till 1 $val från det andra kommandot som skriver värdet för $val till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2c91c-121">Notice that the semicolon separates the first command that adds 1 to $val from the second command that writes the value of $val to the console.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c91c-122">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="2c91c-122">SEE ALSO</span></span>

[<span data-ttu-id="2c91c-123">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="2c91c-123">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="2c91c-124">about_Do</span><span class="sxs-lookup"><span data-stu-id="2c91c-124">about_Do</span></span>](about_Do.md)

[<span data-ttu-id="2c91c-125">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="2c91c-125">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="2c91c-126">about_For</span><span class="sxs-lookup"><span data-stu-id="2c91c-126">about_For</span></span>](about_For.md)

[<span data-ttu-id="2c91c-127">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="2c91c-127">about_Language_Keywords</span></span>](about_Language_Keywords.md)

