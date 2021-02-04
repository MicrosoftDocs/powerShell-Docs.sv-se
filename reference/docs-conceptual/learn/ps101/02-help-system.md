---
title: Hjälpsystemet
description: Att hantera hjälp systemet är nyckeln till att lyckas med PowerShell.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: cfb12f57b7bb6c514f4e19a93dfe9c77245bd977
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216139"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="fede3-103">Kapitel 2 – hjälp systemet</span><span class="sxs-lookup"><span data-stu-id="fede3-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="fede3-104">Två grupper av IT-proffs har fått ett skriftligt test utan åtkomst till en dator för att fastställa deras skicklighets nivå med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fede3-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="fede3-105">PowerShell-nybörjare placerades i en grupp och experter i en annan.</span><span class="sxs-lookup"><span data-stu-id="fede3-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="fede3-106">Baserat på resultatet av testet verkar det inte vara mycket skillnad på skicklighets nivån mellan de två grupperna.</span><span class="sxs-lookup"><span data-stu-id="fede3-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="fede3-107">Båda grupperna har fått ett andra test som liknar det första.</span><span class="sxs-lookup"><span data-stu-id="fede3-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="fede3-108">Den här gången har de fått åtkomst till en dator med PowerShell som inte hade till gång till Internet.</span><span class="sxs-lookup"><span data-stu-id="fede3-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="fede3-109">Resultatet från det andra testet visade en stor skillnad på skicklighets nivån mellan de två grupperna.</span><span class="sxs-lookup"><span data-stu-id="fede3-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="fede3-110">Experter vet inte alltid svaren, men de vet hur de kan ta reda på svaren.</span><span class="sxs-lookup"><span data-stu-id="fede3-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="fede3-111">Vad var skillnaden i resultatet från det första och andra testet mellan dessa två grupper?</span><span class="sxs-lookup"><span data-stu-id="fede3-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="fede3-112">Skillnaderna som observerats i de här två testerna beror på att experter inte kan komma ihåg hur man använder tusentals kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fede3-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="fede3-113">De lär sig att använda hjälp systemet i PowerShell mycket bra.</span><span class="sxs-lookup"><span data-stu-id="fede3-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="fede3-114">Detta gör att de kan hitta de nödvändiga kommandona vid behov och hur du använder dessa kommandon när de har hittat dem.</span><span class="sxs-lookup"><span data-stu-id="fede3-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="fede3-115">Jag har hört Jeffrey Snover, inventeringen av PowerShell, anger en liknande artikel ett antal gånger.</span><span class="sxs-lookup"><span data-stu-id="fede3-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="fede3-116">Att hantera hjälp systemet är nyckeln till att lyckas med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fede3-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="fede3-117">Identifierings möjligheten</span><span class="sxs-lookup"><span data-stu-id="fede3-117">Discoverability</span></span>

<span data-ttu-id="fede3-118">Kompilerade kommandon i PowerShell kallas cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fede3-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="fede3-119">Cmdleten är uttalad "kommando-let" (inte CMD-let).</span><span class="sxs-lookup"><span data-stu-id="fede3-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="fede3-120">Cmdlets-namn har formatet "verb-Substantiv"-kommandon som gör dem lättare att upptäcka.</span><span class="sxs-lookup"><span data-stu-id="fede3-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="fede3-121">Till exempel är cmdleten för att bestämma vilka processer som körs `Get-Process` och cmdleten för att hämta en lista över tjänster och deras status `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="fede3-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="fede3-122">Det finns andra typer av kommandon i PowerShell, till exempel alias och funktioner som kommer att täckas senare i denna bok.</span><span class="sxs-lookup"><span data-stu-id="fede3-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="fede3-123">Termen PowerShell-kommando är en generisk term som ofta används för att referera till valfri typ av kommando i PowerShell, oavsett om det är en cmdlet, en funktion eller ett alias.</span><span class="sxs-lookup"><span data-stu-id="fede3-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="fede3-124">De tre Core-cmdletarna i PowerShell</span><span class="sxs-lookup"><span data-stu-id="fede3-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="fede3-125">`Get-Member` (omfattas av kapitel 3)</span><span class="sxs-lookup"><span data-stu-id="fede3-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="fede3-126">En fråga jag är ofta ombedd Hur tar du reda på vad kommandona är i PowerShell?</span><span class="sxs-lookup"><span data-stu-id="fede3-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="fede3-127">Både `Get-Command` och `Get-Help` kan användas för att fastställa kommandon.</span><span class="sxs-lookup"><span data-stu-id="fede3-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="fede3-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="fede3-128">Get-Help</span></span>

<span data-ttu-id="fede3-129">`Get-Help` är ett kommando för flera syften.</span><span class="sxs-lookup"><span data-stu-id="fede3-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="fede3-130">`Get-Help` hjälper dig att lära dig hur du använder kommandon när du har hittat dem.</span><span class="sxs-lookup"><span data-stu-id="fede3-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="fede3-131">`Get-Help` kan också användas för att hitta kommandon, men på ett annat och mer indirekt sätt jämfört med `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="fede3-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="fede3-132">När `Get-Help` används för att hitta kommandon söker den först efter jokertecken matchningar av kommando namn baserat på angivna indata.</span><span class="sxs-lookup"><span data-stu-id="fede3-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="fede3-133">Om ingen matchning hittas genomsöks hjälp avsnitten i själva hjälpen och om ingen matchning hittas returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="fede3-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="fede3-134">Motsats till populär tro `Get-Help` kan användas för att hitta kommandon som inte har hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fede3-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="fede3-135">Det första du behöver veta om hjälp systemet i PowerShell är hur du använder- `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fede3-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="fede3-136">Följande kommando används för att visa hjälp avsnittet för `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fede3-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="fede3-137">Från och med PowerShell version 3 levereras PowerShell-hjälpen inte med operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="fede3-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="fede3-138">Första gången `Get-Help` körs för ett kommando visas det föregående meddelandet.</span><span class="sxs-lookup"><span data-stu-id="fede3-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="fede3-139">Om `help` funktionen eller `man` aliaset används i stället för `Get-Help` cmdleten får du inte den här frågan.</span><span class="sxs-lookup"><span data-stu-id="fede3-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="fede3-140">Om du svarar ja genom att trycka på <kbd>Y</kbd> körs `Update-Help` cmdleten, vilket kräver Internet åtkomst som standard.</span><span class="sxs-lookup"><span data-stu-id="fede3-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="fede3-141">`Y` kan anges i antingen versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="fede3-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="fede3-142">När hjälpen har hämtats och uppdateringen är klar returneras hjälp avsnittet för det angivna kommandot:</span><span class="sxs-lookup"><span data-stu-id="fede3-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="fede3-143">Ta en stund att köra det exemplet på datorn, granska utdata och anteckna hur informationen grupperas:</span><span class="sxs-lookup"><span data-stu-id="fede3-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="fede3-144">NAMN</span><span class="sxs-lookup"><span data-stu-id="fede3-144">NAME</span></span>
- <span data-ttu-id="fede3-145">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fede3-145">SYNOPSIS</span></span>
- <span data-ttu-id="fede3-146">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fede3-146">SYNTAX</span></span>
- <span data-ttu-id="fede3-147">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fede3-147">DESCRIPTION</span></span>
- <span data-ttu-id="fede3-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fede3-148">RELATED LINKS</span></span>
- <span data-ttu-id="fede3-149">REMARKS</span><span class="sxs-lookup"><span data-stu-id="fede3-149">REMARKS</span></span>

<span data-ttu-id="fede3-150">Som du kan se kan hjälp avsnitten innehålla en enorma mängd information och detta är inte ens hela hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="fede3-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="fede3-151">Även om den inte är speciell för PowerShell, är en parameter ett sätt att tillhandahålla inmatade för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="fede3-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="fede3-152">`Get-Help` har många parametrar som kan specificeras för att returnera hela hjälp avsnittet eller en delmängd av den.</span><span class="sxs-lookup"><span data-stu-id="fede3-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="fede3-153">I avsnittet syntax i hjälp avsnittet som visas i den föregående uppsättningen med resultat visas alla parametrar för `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fede3-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="fede3-154">Vid första inblicken visas samma parametrar i listan sex olika tider.</span><span class="sxs-lookup"><span data-stu-id="fede3-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="fede3-155">Vart och ett av dessa olika block i avsnittet syntax är en parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="fede3-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="fede3-156">Det innebär att `Get-Help` cmdleten har sex olika parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="fede3-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="fede3-157">Om du tar en närmare titt ser du att minst en parameter är annorlunda i varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="fede3-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="fede3-158">Parameter uppsättningar kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="fede3-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="fede3-159">När en unik parameter som bara finns i en av parameter uppsättningarna används kan endast parametrar som finns i den parameter uppsättningen användas.</span><span class="sxs-lookup"><span data-stu-id="fede3-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="fede3-160">Det går till exempel inte att ange både **fullständig** och **detaljerad** parameter på samma tidpunkt eftersom de finns i olika parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="fede3-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="fede3-161">Var och en av följande parametrar finns i olika parameter uppsättningar:</span><span class="sxs-lookup"><span data-stu-id="fede3-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="fede3-162">Fullständig</span><span class="sxs-lookup"><span data-stu-id="fede3-162">Full</span></span>
- <span data-ttu-id="fede3-163">Detaljerad</span><span class="sxs-lookup"><span data-stu-id="fede3-163">Detailed</span></span>
- <span data-ttu-id="fede3-164">Exempel</span><span class="sxs-lookup"><span data-stu-id="fede3-164">Examples</span></span>
- <span data-ttu-id="fede3-165">Online</span><span class="sxs-lookup"><span data-stu-id="fede3-165">Online</span></span>
- <span data-ttu-id="fede3-166">Parameter</span><span class="sxs-lookup"><span data-stu-id="fede3-166">Parameter</span></span>
- <span data-ttu-id="fede3-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="fede3-167">ShowWindow</span></span>

<span data-ttu-id="fede3-168">All den encryptiska syntaxen, till exempel fyrkantiga hakparenteser och vinkelparenteser i avsnittet syntax betyder något men kommer att tas med i bilaga A till denna bok.</span><span class="sxs-lookup"><span data-stu-id="fede3-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="fede3-169">Det är viktigt att lära sig att lära sig den krypterade syntaxen ofta är svår att bevaras för någon som är ny för PowerShell och som inte kan använda den varje dag.</span><span class="sxs-lookup"><span data-stu-id="fede3-169">While important, learning the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="fede3-170">Mer information för att bättre förstå den krypterade syntaxen finns i [bilaga A][].</span><span class="sxs-lookup"><span data-stu-id="fede3-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="fede3-171">För nybörjare finns det ett enklare sätt att ta reda på samma information, förutom på vanligt språk.</span><span class="sxs-lookup"><span data-stu-id="fede3-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="fede3-172">När den **fullständiga** parametern i `Get-Help` anges returneras hela hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="fede3-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="fede3-173">Ta en stund att köra det exemplet på datorn, granska utdata och anteckna hur informationen grupperas:</span><span class="sxs-lookup"><span data-stu-id="fede3-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="fede3-174">NAMN</span><span class="sxs-lookup"><span data-stu-id="fede3-174">NAME</span></span>
- <span data-ttu-id="fede3-175">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fede3-175">SYNOPSIS</span></span>
- <span data-ttu-id="fede3-176">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fede3-176">SYNTAX</span></span>
- <span data-ttu-id="fede3-177">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fede3-177">DESCRIPTION</span></span>
- <span data-ttu-id="fede3-178">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fede3-178">PARAMETERS</span></span>
- <span data-ttu-id="fede3-179">INDATA</span><span class="sxs-lookup"><span data-stu-id="fede3-179">INPUTS</span></span>
- <span data-ttu-id="fede3-180">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fede3-180">OUTPUTS</span></span>
- <span data-ttu-id="fede3-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fede3-181">NOTES</span></span>
- <span data-ttu-id="fede3-182">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fede3-182">EXAMPLES</span></span>
- <span data-ttu-id="fede3-183">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fede3-183">RELATED LINKS</span></span>

<span data-ttu-id="fede3-184">Observera att om du använder den **fullständiga** parametern returnerade flera ytterligare avsnitt, varav en är avsnittet parametrar som innehåller mer information än i avsnittet om syntax för kryptering.</span><span class="sxs-lookup"><span data-stu-id="fede3-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="fede3-185">Den **fullständiga** parametern är en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="fede3-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="fede3-186">En parameter som inte kräver ett värde kallas för en växel parameter.</span><span class="sxs-lookup"><span data-stu-id="fede3-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="fede3-187">När en växel parameter anges är värdet true och när det inte är det är värdet false.</span><span class="sxs-lookup"><span data-stu-id="fede3-187">When a switch parameter is specified, its value is true and when it's not, its value is false.</span></span>

<span data-ttu-id="fede3-188">Om du har arbetat genom det här kapitlet i PowerShell-konsolen har du märkt att föregående kommando visar det fullständiga hjälp avsnittet för `Get-Help` reste på skärmen utan att ge dig möjlighet att läsa det.</span><span class="sxs-lookup"><span data-stu-id="fede3-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="fede3-189">Det finns ett bättre sätt.</span><span class="sxs-lookup"><span data-stu-id="fede3-189">There's a better way.</span></span>

<span data-ttu-id="fede3-190">`Help` är en funktion som rör `Get-Help` en funktion med namnet `more` , som är en omslutning för den `more.com` körbara filen i Windows.</span><span class="sxs-lookup"><span data-stu-id="fede3-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="fede3-191">I PowerShell-konsolen visas `help` en sida med hjälp i taget.</span><span class="sxs-lookup"><span data-stu-id="fede3-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="fede3-192">I ISE fungerar det på samma sätt som `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="fede3-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="fede3-193">Min rekommendation är att använda `help` funktionen i stället för `Get-Help` cmdleten eftersom den ger en bättre upplevelse och är mindre för att skriva.</span><span class="sxs-lookup"><span data-stu-id="fede3-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="fede3-194">Mindre text är dock inte alltid en bra sak.</span><span class="sxs-lookup"><span data-stu-id="fede3-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="fede3-195">Om du vill spara dina kommandon som ett skript eller dela dem med någon annan, måste du se till att använda fullständiga cmdlet-och parameter namn.</span><span class="sxs-lookup"><span data-stu-id="fede3-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="fede3-196">De fullständiga namnen är själv dokumenterade, vilket gör dem lättare att förstå.</span><span class="sxs-lookup"><span data-stu-id="fede3-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="fede3-197">Tänk på nästa person som måste läsa och förstå dina kommandon.</span><span class="sxs-lookup"><span data-stu-id="fede3-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="fede3-198">Det kan vara du.</span><span class="sxs-lookup"><span data-stu-id="fede3-198">It could be you.</span></span> <span data-ttu-id="fede3-199">Dina medarbetare och dig själv är tacksamma.</span><span class="sxs-lookup"><span data-stu-id="fede3-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="fede3-200">Prova att köra följande kommandon i PowerShell-konsolen på datorn för Windows 10 Lab-miljön.</span><span class="sxs-lookup"><span data-stu-id="fede3-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="fede3-201">Har du tittat på eventuella skillnader i utdata från de tidigare listade kommandona när du körde dem på din dator med Windows 10 Lab-miljön?</span><span class="sxs-lookup"><span data-stu-id="fede3-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="fede3-202">Det finns inga andra skillnader än de två sista alternativen returnerar resultatet en sida i taget.</span><span class="sxs-lookup"><span data-stu-id="fede3-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="fede3-203"><kbd>Blank steg</kbd> används för att visa nästa sida med innehåll när du använder `Help` funktionen och <kbd>CTRL</kbd> + <kbd>C</kbd> avbryter kommandon som körs i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="fede3-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="fede3-204">I det första exemplet används `Get-Help` -cmdleten, den andra använder `Help` funktionen och den tredje utelämnar **namn** parametern när `Help` funktionen används.</span><span class="sxs-lookup"><span data-stu-id="fede3-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="fede3-205">**Name** är en positions parameter och den används i samma position i det exemplet.</span><span class="sxs-lookup"><span data-stu-id="fede3-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="fede3-206">Det innebär att värdet kan anges utan att ange parameter namnet, så länge själva värdet anges på rätt plats.</span><span class="sxs-lookup"><span data-stu-id="fede3-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="fede3-207">Hur vet jag vilken position du ska ange värdet i?</span><span class="sxs-lookup"><span data-stu-id="fede3-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="fede3-208">Genom att läsa hjälpen som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="fede3-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="fede3-209">Observera att **parametern** parameter i föregående exempel användes med funktionen Help för att endast returnera information från hjälp avsnittet för parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="fede3-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="fede3-210">Detta är mycket mer koncist än att försöka manuellt gå igenom vad som ibland ser ut som ett hundra sid hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fede3-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="fede3-211">Baserat på dessa resultat kan du se att **Name** -parametern är positionerad och måste anges i position noll (den första positionen) när den används i position.</span><span class="sxs-lookup"><span data-stu-id="fede3-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="fede3-212">Ordningen som parametrar anges i spelar ingen roll om parameter namnet har angetts.</span><span class="sxs-lookup"><span data-stu-id="fede3-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="fede3-213">En annan viktig del av informationen är att **namn** parametern förväntar sig att data typen för värdet ska vara en enskild sträng, som anges av `<String>` .</span><span class="sxs-lookup"><span data-stu-id="fede3-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="fede3-214">Om du har accepterat flera strängar visas data typen som `<String[]>` .</span><span class="sxs-lookup"><span data-stu-id="fede3-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="fede3-215">Ibland vill du bara Visa hela hjälp avsnittet för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="fede3-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="fede3-216">Det finns ett antal andra parametrar förutom **fullständig** som kan anges med `Get-Help` eller `Help` .</span><span class="sxs-lookup"><span data-stu-id="fede3-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="fede3-217">Prova att köra följande kommandon på datorn för Windows 10 Lab-miljön:</span><span class="sxs-lookup"><span data-stu-id="fede3-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="fede3-218">Jag använder vanligt vis `help <command name>` parametern **fullständig** eller **online** .</span><span class="sxs-lookup"><span data-stu-id="fede3-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="fede3-219">Om jag bara är intresse rad av exemplen använder jag parametern **exempel** och om jag bara är intresse rad av en speciell parameter använder jag **parametern** parameter.</span><span class="sxs-lookup"><span data-stu-id="fede3-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="fede3-220">Parametern **ShowWindow** öppnar hjälp avsnittet i ett separat sökbart fönster som kan placeras på en annan övervakare om du har flera bildskärmar.</span><span class="sxs-lookup"><span data-stu-id="fede3-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="fede3-221">Jag har undvikt parametern **ShowWindow** eftersom det finns ett känt fel där den inte visar hela hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="fede3-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="fede3-222">Om du vill ha hjälp i ett separat fönster, är min rekommendation att antingen använda parametern **online** eller använda den **fullständiga** parametern och skicka resultatet till `Out-GridView` , som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="fede3-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="fede3-223">Både `Out-GridView` cmdleten och **ShowWindow** -parametern för `Get-Help` cmdleten kräver ett operativ system med ett grafiskt användar gränssnitt (grafiskt användar gränssnitt).</span><span class="sxs-lookup"><span data-stu-id="fede3-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="fede3-224">De genererar ett fel meddelande om du försöker använda någon av dem på Windows Server som har installerats med installations alternativet Server Core (utan användar gränssnitt).</span><span class="sxs-lookup"><span data-stu-id="fede3-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="fede3-225">Om du vill använda `Get-Help` för att söka efter kommandon använder du jokertecknet asterisk ( `*` ) med parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="fede3-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="fede3-226">Ange en term som du söker efter kommandon på som värde för parametern **Name** enligt följande exempel.</span><span class="sxs-lookup"><span data-stu-id="fede3-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="fede3-227">I det föregående exemplet `*` behövs inte jokertecken och utelämnar dem ger samma resultat.</span><span class="sxs-lookup"><span data-stu-id="fede3-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="fede3-228">`Get-Help` lägger automatiskt till jokertecken i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="fede3-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="fede3-229">Föregående kommando ger samma resultat som att ange `*` jokertecknet för varje process slut.</span><span class="sxs-lookup"><span data-stu-id="fede3-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="fede3-230">Jag vill lägga till dem eftersom det är det alternativ som alltid fungerar konsekvent.</span><span class="sxs-lookup"><span data-stu-id="fede3-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="fede3-231">Annars krävs de i vissa scenarier och inte andra.</span><span class="sxs-lookup"><span data-stu-id="fede3-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="fede3-232">När du lägger till ett jokertecken i mitten av värdet läggs de inte längre automatiskt till i bakgrunden till det värde som du har angett.</span><span class="sxs-lookup"><span data-stu-id="fede3-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="fede3-233">Inga resultat returneras av det kommandot om inte `*` jokertecknet läggs till i början, slutet eller både början och slutet av `pr*cess` .</span><span class="sxs-lookup"><span data-stu-id="fede3-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="fede3-234">Om det angivna värdet börjar med ett bindestreck, genereras ett fel eftersom PowerShell tolkar det som ett parameter namn och det inte finns något sådant parameter namn för `Get-Help` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fede3-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="fede3-235">Om det du försöker söka efter är kommandon som slutar med `-process` , behöver du bara lägga till `*` jokertecknet i början av värdet.</span><span class="sxs-lookup"><span data-stu-id="fede3-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="fede3-236">När du söker efter PowerShell-kommandon med `Get-Help` , vill du vara lite mer vagt i stället för att vara för speciell med det du söker efter.</span><span class="sxs-lookup"><span data-stu-id="fede3-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="fede3-237">Söker efter `process` tidigare hittade endast kommandon som finns `process` i namnet på kommandot och bara returnerade resultaten.</span><span class="sxs-lookup"><span data-stu-id="fede3-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="fede3-238">När `Get-Help` används för att söka efter `processes` hittas inga matchningar för kommando namn, så den utför en sökning i alla hjälp avsnitt i PowerShell på systemet och returnerar eventuella matchningar som hittas.</span><span class="sxs-lookup"><span data-stu-id="fede3-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="fede3-239">Detta gör att det returnerar ett enorma antal resultat.</span><span class="sxs-lookup"><span data-stu-id="fede3-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="fede3-240">Använd `Help` om du vill söka efter `process` returnerade 10 resultat och använda det för att söka efter `processes` returnerade 68-resultat.</span><span class="sxs-lookup"><span data-stu-id="fede3-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="fede3-241">Om det bara finns ett resultat visas själva hjälp avsnittet i stället för en lista med kommandon.</span><span class="sxs-lookup"><span data-stu-id="fede3-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="fede3-242">Nu kan du Thiagarajan myten som `Help` i PowerShell bara kan hitta kommandon som har hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fede3-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="fede3-243">Observera att det `more` inte finns något hjälp avsnitt i föregående exempel, men `Help` systemet i PowerShell kunde hitta det.</span><span class="sxs-lookup"><span data-stu-id="fede3-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="fede3-244">Den hittade bara en matchning och returnerade den grundläggande syntax som visas när ett kommando saknar hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fede3-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="fede3-245">PowerShell innehåller flera koncept hjälp avsnitt (om).</span><span class="sxs-lookup"><span data-stu-id="fede3-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="fede3-246">Följande kommando kan användas för att returnera en lista över alla **om** hjälp avsnitt i systemet.</span><span class="sxs-lookup"><span data-stu-id="fede3-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="fede3-247">Om du begränsar resultatet till ett enda om-hjälp avsnitt visas det faktiska hjälp avsnittet i stället för att returnera en lista.</span><span class="sxs-lookup"><span data-stu-id="fede3-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="fede3-248">Hjälp systemet i PowerShell måste uppdateras för **att det ska** gå att presentera hjälp avsnitten.</span><span class="sxs-lookup"><span data-stu-id="fede3-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="fede3-249">Om den första uppdateringen av hjälp systemet misslyckades på din dator, kommer filerna inte att vara tillgängliga förrän `Update-Help` cmdleten har körts utan problem.</span><span class="sxs-lookup"><span data-stu-id="fede3-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="fede3-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="fede3-250">Get-Command</span></span>

<span data-ttu-id="fede3-251">`Get-Command` är utformad för att hjälpa dig att hitta kommandon.</span><span class="sxs-lookup"><span data-stu-id="fede3-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="fede3-252">Om `Get-Command` du kör utan parametrar returneras en lista över alla kommandon i systemet.</span><span class="sxs-lookup"><span data-stu-id="fede3-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="fede3-253">Följande exempel visar hur du använder `Get-Command` cmdleten för att avgöra vilka kommandon som finns för att arbeta med processer:</span><span class="sxs-lookup"><span data-stu-id="fede3-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="fede3-254">Observera i föregående exempel där kördes `Get-Command` , parametern **Substantiv** används och `Process` anges som värde för parametern **Substantiv** .</span><span class="sxs-lookup"><span data-stu-id="fede3-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="fede3-255">Vad händer om du inte vet hur du använder `Get-Command` cmdleten?</span><span class="sxs-lookup"><span data-stu-id="fede3-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="fede3-256">Du kan använda `Get-Help` för att visa hjälp avsnittet för `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="fede3-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="fede3-257">Parametrarna **Name**, **Substantiv** och **verb** accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="fede3-257">The **Name**, **Noun**, and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="fede3-258">I följande exempel visas jokertecken som används med parametern **Name** :</span><span class="sxs-lookup"><span data-stu-id="fede3-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="fede3-259">Jag är inte en fläkt med att använda jokertecken med parametern **Name** `Get-Command` , eftersom den även returnerar körbara filer som inte är ursprungliga PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="fede3-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="fede3-260">Om du kommer att använda jokertecken med parametern **Name** rekommenderar vi att du begränsar resultatet med parametern **CommandType** .</span><span class="sxs-lookup"><span data-stu-id="fede3-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="fede3-261">Ett bättre alternativ är att använda antingen **verb** -eller **Substantiv** -parametern eller båda, eftersom bara PowerShell-kommandon har både verb och substantiv.</span><span class="sxs-lookup"><span data-stu-id="fede3-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="fede3-262">Har du hittat något fel med hjälp avsnittet?</span><span class="sxs-lookup"><span data-stu-id="fede3-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="fede3-263">De goda nyheterna är att hjälp avsnitten för PowerShell har öppnats och är tillgängliga i [PowerShell-dokument-][] lagringsplatsen på GitHub.</span><span class="sxs-lookup"><span data-stu-id="fede3-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="fede3-264">Betala vidarebefordran genom att inte bara åtgärda den felaktiga informationen för dig själv, utan även för alla andra.</span><span class="sxs-lookup"><span data-stu-id="fede3-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="fede3-265">Du behöver bara förgrening i PowerShell-dokumentationens lagrings plats på GitHub, uppdatera hjälp avsnittet och skicka en pull-begäran.</span><span class="sxs-lookup"><span data-stu-id="fede3-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="fede3-266">När pull-begäran har godkänts är den korrigerade dokumentationen tillgänglig för alla.</span><span class="sxs-lookup"><span data-stu-id="fede3-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="fede3-267">Hjälp om uppdatering</span><span class="sxs-lookup"><span data-stu-id="fede3-267">Updating Help</span></span>

<span data-ttu-id="fede3-268">Den lokala kopian av PowerShell-hjälpen har tidigare uppdaterat hjälp avsnittet om första gången på ett kommando begärdes.</span><span class="sxs-lookup"><span data-stu-id="fede3-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="fede3-269">Vi rekommenderar att regelbundet uppdatera hjälp systemet, eftersom det kan finnas uppdateringar av hjälp innehållet från tid till tid.</span><span class="sxs-lookup"><span data-stu-id="fede3-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="fede3-270">`Update-Help`Cmdleten används för att uppdatera hjälp avsnitten.</span><span class="sxs-lookup"><span data-stu-id="fede3-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="fede3-271">Den kräver Internet åtkomst som standard och för att köra PowerShell som administratör.</span><span class="sxs-lookup"><span data-stu-id="fede3-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri
property in the module manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="fede3-272">Ett par moduler returnerade fel, vilket inte är ovanligt.</span><span class="sxs-lookup"><span data-stu-id="fede3-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="fede3-273">Om datorn inte har till gång till Internet kan du använda `Save-Help` cmdleten på en annan dator som har Internet åtkomst för att först spara den uppdaterade hjälp informationen till en fil resurs i nätverket och sedan använda **SourcePath** -parametern för `Update-Help` för att ange den här nätverks platsen för hjälp avsnitten.</span><span class="sxs-lookup"><span data-stu-id="fede3-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="fede3-274">Överväg att konfigurera en schemalagd aktivitet eller lägga till en del logik i ditt profil skript i PowerShell för att regelbundet uppdatera hjälp innehållet på datorn.</span><span class="sxs-lookup"><span data-stu-id="fede3-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="fede3-275">Profil skript beskrivs i ett kommande kapitel.</span><span class="sxs-lookup"><span data-stu-id="fede3-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="fede3-276">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="fede3-276">Summary</span></span>

<span data-ttu-id="fede3-277">I det här kapitlet har du lärt dig hur du hittar kommandon med både `Get-Help` och `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="fede3-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="fede3-278">Du har lärt dig hur du använder hjälp systemet för att ta reda på hur du använder kommandon när du har hittat dem.</span><span class="sxs-lookup"><span data-stu-id="fede3-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="fede3-279">Du har också lärt dig hur du uppdaterar innehållet i hjälp avsnitten när det finns uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="fede3-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="fede3-280">Mitt utmaning till dig är att lära dig ett PowerShell-kommando per dag.</span><span class="sxs-lookup"><span data-stu-id="fede3-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="fede3-281">Genomgång</span><span class="sxs-lookup"><span data-stu-id="fede3-281">Review</span></span>

1. <span data-ttu-id="fede3-282">Är **DisplayName** -parametern för `Get-Service` positional?</span><span class="sxs-lookup"><span data-stu-id="fede3-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="fede3-283">Hur många parameter uppsättningar `Get-Process` har cmdleten?</span><span class="sxs-lookup"><span data-stu-id="fede3-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="fede3-284">Vilka PowerShell-kommandon finns för att arbeta med händelse loggar?</span><span class="sxs-lookup"><span data-stu-id="fede3-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="fede3-285">Vad är PowerShell-kommandot för att returnera en lista med PowerShell-processer som körs på datorn?</span><span class="sxs-lookup"><span data-stu-id="fede3-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="fede3-286">Hur uppdaterar du hjälp innehållet för PowerShell som lagras på datorn?</span><span class="sxs-lookup"><span data-stu-id="fede3-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="fede3-287">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="fede3-287">Recommended Reading</span></span>

<span data-ttu-id="fede3-288">Om du vill veta mer om de ämnen som beskrivs i det här kapitlet rekommenderar vi att du läser följande PowerShell-hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fede3-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="fede3-289">[Get – hjälp][]</span><span class="sxs-lookup"><span data-stu-id="fede3-289">[Get-Help][]</span></span>
- <span data-ttu-id="fede3-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="fede3-290">[Get-Command][]</span></span>
- <span data-ttu-id="fede3-291">[Uppdatera – hjälp][]</span><span class="sxs-lookup"><span data-stu-id="fede3-291">[Update-Help][]</span></span>
- <span data-ttu-id="fede3-292">[Spara – hjälp][]</span><span class="sxs-lookup"><span data-stu-id="fede3-292">[Save-Help][]</span></span>
- <span data-ttu-id="fede3-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="fede3-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="fede3-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="fede3-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="fede3-295">I nästa kapitel lär du dig om `Get-Member` cmdleten samt objekt, egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="fede3-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get – hjälp]: /powershell/module/microsoft.powershell.core/get-help
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Uppdatera – hjälp]: /powershell/module/microsoft.powershell.core/update-help
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Spara – hjälp]: /powershell/module/microsoft.powershell.core/save-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-dokumentation]: https://github.com/powershell/powershell
[PowerShell-Docs]: https://github.com/powershell/powershell
[Bilaga A]: appendix-a.md
[Appendix A]: appendix-a.md
