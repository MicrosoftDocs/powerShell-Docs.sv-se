---
title: Flödeskontroll
description: PowerShell innehåller metoder för att skapa slingor, fatta beslut och logiskt styra flödet av kod i skript.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4f0d7b7f5f3c12bb9475af5aed42b2d32cfbc14d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "84436311"
---
# <a name="chapter-6---flow-control"></a><span data-ttu-id="35044-103">Kapitel 6 – flödes kontroll</span><span class="sxs-lookup"><span data-stu-id="35044-103">Chapter 6 - Flow control</span></span>

## <a name="scripting"></a><span data-ttu-id="35044-104">Använda skript</span><span class="sxs-lookup"><span data-stu-id="35044-104">Scripting</span></span>

<span data-ttu-id="35044-105">När du går från att skriva PowerShell en-liners för att skriva skript så låter det mycket mer komplicerat än det verkligen är.</span><span class="sxs-lookup"><span data-stu-id="35044-105">When you move from writing PowerShell one-liners to writing scripts, it sounds a lot more complicated than it really is.</span></span> <span data-ttu-id="35044-106">Ett skript är inget annat än samma eller liknande kommandon som du skulle kunna köra interaktivt i PowerShell-konsolen, förutom att de har sparats som en `.PS1` fil.</span><span class="sxs-lookup"><span data-stu-id="35044-106">A script is nothing more than the same or similar commands that you would run interactively in the PowerShell console, except they're saved as a `.PS1` file.</span></span> <span data-ttu-id="35044-107">Det finns vissa skript konstruktioner som du kan använda som en `foreach` loop i stället för `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="35044-107">There are some scripting constructs that you may use such as a `foreach` loop instead of the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="35044-108">För nybörjare kan skillnaderna vara förvirrande särskilt när du anser att det `foreach` är både en skript konstruktion och ett alias för `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="35044-108">To beginners, the differences can be confusing especially when you consider that `foreach` is both a scripting construct and an alias for the `ForEach-Object` cmdlet.</span></span>

## <a name="looping"></a><span data-ttu-id="35044-109">Loopar</span><span class="sxs-lookup"><span data-stu-id="35044-109">Looping</span></span>

<span data-ttu-id="35044-110">En av fördelarna med PowerShell är att när du har gått igenom hur du gör något för ett objekt är det nästan lika enkelt att göra samma uppgift för hundratals objekt.</span><span class="sxs-lookup"><span data-stu-id="35044-110">One of the great things about PowerShell is, once you figure out how to do something for one item, it's almost as easy to do the same task for hundreds of items.</span></span> <span data-ttu-id="35044-111">Upprepa bara objekten med någon av de många olika typerna av slingor i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35044-111">Simply loop through the items using one of the many different types of loops in PowerShell.</span></span>

### <a name="foreach-object"></a><span data-ttu-id="35044-112">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="35044-112">ForEach-Object</span></span>

<span data-ttu-id="35044-113">`ForEach-Object` är en cmdlet för att söka igenom objekt i en pipeline, till exempel med PowerShell en-liners.</span><span class="sxs-lookup"><span data-stu-id="35044-113">`ForEach-Object` is a cmdlet for iterating through items in a pipeline such as with PowerShell one-liners.</span></span> <span data-ttu-id="35044-114">`ForEach-Object` strömmar objekten via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="35044-114">`ForEach-Object` streams the objects through the pipeline.</span></span>

<span data-ttu-id="35044-115">Även om parametern **module** i `Get-Command` accepterar flera värden som är strängar, accepterar den bara dem via pipeline-inmatade efter egenskaps namn eller via parameter inmatade.</span><span class="sxs-lookup"><span data-stu-id="35044-115">Although the **Module** parameter of `Get-Command` accepts multiple values that are strings, it only accepts them via pipeline input by property name or via parameter input.</span></span> <span data-ttu-id="35044-116">I följande scenario måste du använda cmdleten om jag vill skicka två strängar efter värde till `Get-Command` för användning med parametern **module** `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="35044-116">In the following scenario, if I want to pipe two strings by value to `Get-Command` for use with the **Module** parameter, I would need to use the `ForEach-Object` cmdlet.</span></span>

```powershell
'ActiveDirectory', 'SQLServer' |
   ForEach-Object {Get-Command -Module $_} |
     Group-Object -Property ModuleName -NoElement |
         Sort-Object -Property Count -Descending
```

```Output
Count Name
----- ----
  147 ActiveDirectory
   82 SqlServer
```

<span data-ttu-id="35044-117">I föregående exempel `$_` är det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="35044-117">In the previous example, `$_` is the current object.</span></span> <span data-ttu-id="35044-118">Från och med PowerShell version 3,0 `$PSItem` kan användas i stället för `$_` .</span><span class="sxs-lookup"><span data-stu-id="35044-118">Beginning with PowerShell version 3.0, `$PSItem` can be used instead of `$_`.</span></span> <span data-ttu-id="35044-119">Men jag tycker att de flesta erfarna PowerShell-användare föredrar att använda `$_` eftersom det är bakåtkompatibelt och mindre för att skriva.</span><span class="sxs-lookup"><span data-stu-id="35044-119">But I find that most experienced PowerShell users still prefer using `$_` since it's backward compatible and less to type.</span></span>

<span data-ttu-id="35044-120">När du använder `foreach` nyckelordet måste du lagra alla objekt i minnet innan du går igenom dem, vilket kan vara svårt om du inte vet hur många objekt du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="35044-120">When using the `foreach` keyword, you must store all of the items in memory before iterating through them, which could be difficult if you don't know how many items you're working with.</span></span>

```powershell
$ComputerName = 'DC01', 'WEB01'
foreach ($Computer in $ComputerName) {
  Get-ADComputer -Identity $Computer
}
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="35044-121">Många gånger en loop, till exempel `foreach` eller `ForEach-Object` är nödvändig.</span><span class="sxs-lookup"><span data-stu-id="35044-121">Many times a loop such as `foreach` or `ForEach-Object` is necessary.</span></span> <span data-ttu-id="35044-122">Annars visas ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="35044-122">Otherwise you'll receive an error message.</span></span>

```powershell
Get-ADComputer -Identity 'DC01', 'WEB01'
```

```Output
Get-ADComputer : Cannot convert 'System.Object[]' to the type
'Microsoft.ActiveDirectory.Management.ADComputer' required by parameter 'Identity'.
Specified method is not supported.
At line:1 char:26
+ Get-ADComputer -Identity 'DC01', 'WEB01'
+                          ```````````````
    + CategoryInfo          : InvalidArgument: (:) [Get-ADComputer], ParameterBindingExc
   eption
    + FullyQualifiedErrorId : CannotConvertArgument,Microsoft.ActiveDirectory.Management
   .Commands.GetADComputer
```

<span data-ttu-id="35044-123">Andra gånger kan du få samma resultat samtidigt som du eliminerar slingan helt.</span><span class="sxs-lookup"><span data-stu-id="35044-123">Other times, you can get the same results while eliminating the loop altogether.</span></span> <span data-ttu-id="35044-124">Läs cmdlet-hjälpen för att förstå dina alternativ.</span><span class="sxs-lookup"><span data-stu-id="35044-124">Consult the cmdlet help to understand your options.</span></span>

```powershell
'DC01', 'WEB01' | Get-ADComputer
```

```Output
DistinguishedName : CN=DC01,OU=Domain Controllers,DC=mikefrobbins,DC=com
DNSHostName       : dc01.mikefrobbins.com
Enabled           : True
Name              : DC01
ObjectClass       : computer
ObjectGUID        : c38da20c-a484-469d-ba4c-bab3fb71ae8e
SamAccountName    : DC01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1001
UserPrincipalName :

DistinguishedName : CN=WEB01,CN=Computers,DC=mikefrobbins,DC=com
DNSHostName       : web01.mikefrobbins.com
Enabled           : True
Name              : WEB01
ObjectClass       : computer
ObjectGUID        : 33aa530e-1e31-40d8-8c78-76a18b673c33
SamAccountName    : WEB01$
SID               : S-1-5-21-2989741381-570885089-3319121794-1107
UserPrincipalName :
```

<span data-ttu-id="35044-125">Som du kan se i föregående exempel accepterar **identitets** parametern för `Get-ADComputer` bara ett enda värde när den tillhandahålls via parameter indata, men den tillåter flera objekt när indatan tillhandahålls via pipeline-indata.</span><span class="sxs-lookup"><span data-stu-id="35044-125">As you can see in the previous examples, the **Identity** parameter for `Get-ADComputer` only accepts a single value when provided via parameter input, but it allows for multiple items when the input is provided via pipeline input.</span></span>

### <a name="for"></a><span data-ttu-id="35044-126">För</span><span class="sxs-lookup"><span data-stu-id="35044-126">For</span></span>

<span data-ttu-id="35044-127">En `for` loop upprepas när ett angivet villkor är sant.</span><span class="sxs-lookup"><span data-stu-id="35044-127">A `for` loop iterates while a specified condition is true.</span></span> <span data-ttu-id="35044-128">`for`Loopen är inte något som jag använder ofta, men den använder sig av den.</span><span class="sxs-lookup"><span data-stu-id="35044-128">The `for` loop is not something that I use often, but it does have its uses.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
}
```

```Output
Sleeping for 1 seconds
Sleeping for 2 seconds
Sleeping for 3 seconds
Sleeping for 4 seconds
```

<span data-ttu-id="35044-129">I föregående exempel itererar loopen fyra gånger genom att börja med siffran ett och fortsätta så länge som räknarvärdet `$i` är mindre än 5.</span><span class="sxs-lookup"><span data-stu-id="35044-129">In the previous example, the loop will iterate four times by starting off with the number one and continue as long as the counter variable `$i` is less than 5.</span></span> <span data-ttu-id="35044-130">Den försätts i vilo läge i totalt 10 sekunder.</span><span class="sxs-lookup"><span data-stu-id="35044-130">It will sleep for a total of 10 seconds.</span></span>

### <a name="do"></a><span data-ttu-id="35044-131">Gör följande</span><span class="sxs-lookup"><span data-stu-id="35044-131">Do</span></span>

<span data-ttu-id="35044-132">Det finns två olika `do` slingor i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35044-132">There are two different `do` loops in PowerShell.</span></span> <span data-ttu-id="35044-133">`Do Until` körs när det angivna villkoret är falskt.</span><span class="sxs-lookup"><span data-stu-id="35044-133">`Do Until` runs while the specified condition is false.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  }
  elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
until ($guess -eq $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
```

<span data-ttu-id="35044-134">Föregående exempel är ett tal spel som fortsätter tills värdet du antar motsvarar samma siffra som `Get-Random` cmdleten genererade.</span><span class="sxs-lookup"><span data-stu-id="35044-134">The previous example is a numbers game that continues until the value you guess equals the same number that the `Get-Random` cmdlet generated.</span></span>

<span data-ttu-id="35044-135">`Do While` är bara tvärtom.</span><span class="sxs-lookup"><span data-stu-id="35044-135">`Do While` is just the opposite.</span></span> <span data-ttu-id="35044-136">Den körs så länge det angivna villkoret utvärderas till sant.</span><span class="sxs-lookup"><span data-stu-id="35044-136">It runs as long as the specified condition evaluates to true.</span></span>

```powershell
$number = Get-Random -Minimum 1 -Maximum 10
do {
  $guess = Read-Host -Prompt "What's your guess?"
  if ($guess -lt $number) {
    Write-Output 'Too low!'
  } elseif ($guess -gt $number) {
    Write-Output 'Too high!'
  }
}
while ($guess -ne $number)
```

```Output
What's your guess?: 1
Too low!
What's your guess?: 2
Too low!
What's your guess?: 3
Too low!
What's your guess?: 4
```

<span data-ttu-id="35044-137">Samma resultat uppnås med en `Do While` slinga genom att du återställer test villkoret till inte lika med.</span><span class="sxs-lookup"><span data-stu-id="35044-137">The same results are achieved with a `Do While` loop by reversing the test condition to not equals.</span></span>

<span data-ttu-id="35044-138">`Do` loopar körs alltid minst en gång eftersom villkoret utvärderas i slutet av slingan.</span><span class="sxs-lookup"><span data-stu-id="35044-138">`Do` loops always run at least once because the condition is evaluated at the end of the loop.</span></span>

### <a name="while"></a><span data-ttu-id="35044-139">Tiden</span><span class="sxs-lookup"><span data-stu-id="35044-139">While</span></span>

<span data-ttu-id="35044-140">På samma sätt som `Do While` slingan `While` körs loopen så länge det angivna villkoret är sant.</span><span class="sxs-lookup"><span data-stu-id="35044-140">Similar to the `Do While` loop, a `While` loop runs as long as the specified condition is true.</span></span> <span data-ttu-id="35044-141">Skillnaden är dock att en `While` slinga utvärderar villkoret överst i slingan innan koden körs.</span><span class="sxs-lookup"><span data-stu-id="35044-141">The difference however, is that a `While` loop evaluates the condition at the top of the loop before any code is run.</span></span> <span data-ttu-id="35044-142">Så den körs inte om villkoret utvärderas till false.</span><span class="sxs-lookup"><span data-stu-id="35044-142">So it doesn't run if the condition evaluates to false.</span></span>

```powershell
$date = Get-Date -Date 'November 22'
while ($date.DayOfWeek -ne 'Thursday') {
  $date = $date.AddDays(1)
}
Write-Output $date
```

```Output
Thursday, November 23, 2017 12:00:00 AM
```

<span data-ttu-id="35044-143">Det föregående exemplet beräknar vilken dag som tacksägelse dag är på USA.</span><span class="sxs-lookup"><span data-stu-id="35044-143">The previous example calculates what day Thanksgiving Day is on in the United States.</span></span> <span data-ttu-id="35044-144">Den är alltid den fjärde torsdagen november.</span><span class="sxs-lookup"><span data-stu-id="35044-144">It's always on the fourth Thursday of November.</span></span> <span data-ttu-id="35044-145">Loopen börjar med 22-dagen i november och lägger till en dag medan vecko dagen inte är lika med torsdag.</span><span class="sxs-lookup"><span data-stu-id="35044-145">So the loop starts with the 22nd day of November and adds a day while the day of the week isn't equal to Thursday.</span></span> <span data-ttu-id="35044-146">Om 22 är en torsdag körs inte loopen alls.</span><span class="sxs-lookup"><span data-stu-id="35044-146">If the 22nd is a Thursday, the loop doesn't run at all.</span></span>

## <a name="break-continue-and-return"></a><span data-ttu-id="35044-147">Bryt, Fortsätt och returnera</span><span class="sxs-lookup"><span data-stu-id="35044-147">Break, Continue, and Return</span></span>

<span data-ttu-id="35044-148">`Break` är utformad för att bryta ut ur en slinga.</span><span class="sxs-lookup"><span data-stu-id="35044-148">`Break` is designed to break out of a loop.</span></span> <span data-ttu-id="35044-149">Den används också ofta med `switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="35044-149">It's also commonly used with the `switch` statement.</span></span>

```powershell
for ($i = 1; $i -lt 5; $i++) {
  Write-Output "Sleeping for $i seconds"
  Start-Sleep -Seconds $i
  break
}
```

```Output
Sleeping for 1 seconds
```

<span data-ttu-id="35044-150">`break`Instruktionen som visas i föregående exempel gör att slingan avslutas vid den första iterationen.</span><span class="sxs-lookup"><span data-stu-id="35044-150">The `break` statement shown in the previous example causes the loop to exit on the first iteration.</span></span>

<span data-ttu-id="35044-151">Continue är utformat för att hoppa till nästa iteration av en slinga.</span><span class="sxs-lookup"><span data-stu-id="35044-151">Continue is designed to skip to the next iteration of a loop.</span></span>

```powershell
while ($i -lt 5) {
  $i += 1
  if ($i -eq 3) {
    continue
  }
  Write-Output $i
}
```

```Output
1
2
4
5
```

<span data-ttu-id="35044-152">I föregående exempel kommer siffrorna 1, 2, 4 och 5 att matas ut.</span><span class="sxs-lookup"><span data-stu-id="35044-152">The previous example will output the numbers 1, 2, 4, and 5.</span></span> <span data-ttu-id="35044-153">Den hoppar över nummer 3 och fortsätter med nästa iteration av slingan.</span><span class="sxs-lookup"><span data-stu-id="35044-153">It skips number 3 and continues with the next iteration of the loop.</span></span> <span data-ttu-id="35044-154">Det fungerar ungefär som `break` `continue` i loopen förutom för den aktuella iterationen.</span><span class="sxs-lookup"><span data-stu-id="35044-154">Similar to `break`, `continue` breaks out of the loop except only for the current iteration.</span></span> <span data-ttu-id="35044-155">Körningen fortsätter med nästa iteration i stället för att bryta ut ur loopen och stoppa.</span><span class="sxs-lookup"><span data-stu-id="35044-155">Execution continues with the next iteration instead of breaking out of the loop and stopping.</span></span>

<span data-ttu-id="35044-156">Return är utformad för att avsluta det befintliga omfånget.</span><span class="sxs-lookup"><span data-stu-id="35044-156">Return is designed to exit out of the existing scope.</span></span>

```powershell
$number = 1..10
foreach ($n in $number) {
  if ($n -ge 4) {
    Return $n
  }
}
```

```Output
4
```

<span data-ttu-id="35044-157">Observera att i föregående exempel returnerar utdata det första resultatet och finns kvar i slingan.</span><span class="sxs-lookup"><span data-stu-id="35044-157">Notice that in the previous example, return outputs the first result and then exists out of the loop.</span></span> <span data-ttu-id="35044-158">En mer grundlig förklaring av resultat instruktionen finns i en av mina blogg artiklar: ["PowerShell Return Keyword"][].</span><span class="sxs-lookup"><span data-stu-id="35044-158">A more thorough explanation of the result statement can be found in one of my blog articles: ["The PowerShell return keyword"][].</span></span>

## <a name="summary"></a><span data-ttu-id="35044-159">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="35044-159">Summary</span></span>

<span data-ttu-id="35044-160">I det här kapitlet har du lärt dig om de olika typerna av slingor som finns i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="35044-160">In this chapter, you've learned about the different types of loops that exist in PowerShell.</span></span>

## <a name="review"></a><span data-ttu-id="35044-161">Genomgång</span><span class="sxs-lookup"><span data-stu-id="35044-161">Review</span></span>

1. <span data-ttu-id="35044-162">Vad är skillnaden i `ForEach-Object` cmdleten och den uppbyggda skript konstruktionen?</span><span class="sxs-lookup"><span data-stu-id="35044-162">What is the difference in the `ForEach-Object` cmdlet and the foreach scripting construct?</span></span>
1. <span data-ttu-id="35044-163">Vad är den främsta fördelen med att använda en while-loop i stället för att göra det eller göra tills loop.</span><span class="sxs-lookup"><span data-stu-id="35044-163">What is the primary advantage of using a While loop instead of a Do While or Do Until loop.</span></span>
1. <span data-ttu-id="35044-164">Hur skiljer sig Break-och Continue-satserna?</span><span class="sxs-lookup"><span data-stu-id="35044-164">How do the break and continue statements differ?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="35044-165">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="35044-165">Recommended Reading</span></span>

- <span data-ttu-id="35044-166">[-Objekt][]</span><span class="sxs-lookup"><span data-stu-id="35044-166">[ForEach-Object][]</span></span>
- <span data-ttu-id="35044-167">[about_ForEach][]</span><span class="sxs-lookup"><span data-stu-id="35044-167">[about_ForEach][]</span></span>
- <span data-ttu-id="35044-168">[about_For][]</span><span class="sxs-lookup"><span data-stu-id="35044-168">[about_For][]</span></span>
- <span data-ttu-id="35044-169">[about_Do][]</span><span class="sxs-lookup"><span data-stu-id="35044-169">[about_Do][]</span></span>
- <span data-ttu-id="35044-170">[about_While][]</span><span class="sxs-lookup"><span data-stu-id="35044-170">[about_While][]</span></span>
- <span data-ttu-id="35044-171">[about_Break][]</span><span class="sxs-lookup"><span data-stu-id="35044-171">[about_Break][]</span></span>
- <span data-ttu-id="35044-172">[about_Continue][]</span><span class="sxs-lookup"><span data-stu-id="35044-172">[about_Continue][]</span></span>
- <span data-ttu-id="35044-173">[about_Return][]</span><span class="sxs-lookup"><span data-stu-id="35044-173">[about_Return][]</span></span>

<!-- link references -->
[-Objekt]: /powershell/module/microsoft.powershell.core/foreach-object
[ForEach-Object]: /powershell/module/microsoft.powershell.core/foreach-object
[about_ForEach]: /powershell/module/microsoft.powershell.core/about/about_foreach
[about_For]: /powershell/module/microsoft.powershell.core/about/about_for
[about_Do]: /powershell/module/microsoft.powershell.core/about/about_do
[about_While]: /powershell/module/microsoft.powershell.core/about/about_while
[about_Break]: /powershell/module/microsoft.powershell.core/about/about_break
[about_Continue]: /powershell/module/microsoft.powershell.core/about/about_continue
[about_Return]: /powershell/module/microsoft.powershell.core/about/about_return
["Nyckelordet" PowerShell Return "]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
["The PowerShell return keyword"]: https://mikefrobbins.com/2015/07/23/the-powershell-return-keyword/
