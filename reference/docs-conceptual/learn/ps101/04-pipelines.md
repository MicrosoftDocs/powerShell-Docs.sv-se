---
title: En-liners och pipelinen
description: En PowerShell-liner är en kontinuerlig pipeline, som innehåller flera kommandon, för att utföra en enskild uppgift.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 4244c34628e8f2ee8d54471fc2d5ad81a870e739
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436360"
---
# <a name="chapter-4---one-liners-and-the-pipeline"></a><span data-ttu-id="b7b45-103">Kapitel 4 – en-liners och pipelinen</span><span class="sxs-lookup"><span data-stu-id="b7b45-103">Chapter 4 - One-liners and the pipeline</span></span>

<span data-ttu-id="b7b45-104">När jag först startade Learning PowerShell, och det inte gick att utföra en uppgift med en PowerShell-liner, gick jag tillbaka till det grafiska användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b7b45-104">When I first started learning PowerShell, if I couldn't accomplish a task with a PowerShell one-liner, I went back to the GUI.</span></span> <span data-ttu-id="b7b45-105">Med tiden har jag skapat mina kunskaper för att skriva skript, funktioner och moduler.</span><span class="sxs-lookup"><span data-stu-id="b7b45-105">Over time, I built my skills up to writing scripts, functions, and modules.</span></span> <span data-ttu-id="b7b45-106">Tillåt inte att du blir överbelastad av några av de mer avancerade exempel som du kan se på Internet.</span><span class="sxs-lookup"><span data-stu-id="b7b45-106">Don't allow yourself to become overwhelmed by some of the more advanced examples you may see on the internet.</span></span> <span data-ttu-id="b7b45-107">Ingen är en naturlig expert med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7b45-107">No one is a natural expert with PowerShell.</span></span> <span data-ttu-id="b7b45-108">Vi var nybörjare på en och samma tillfälle.</span><span class="sxs-lookup"><span data-stu-id="b7b45-108">We were all beginners at one time.</span></span>

<span data-ttu-id="b7b45-109">Jag har fått råd för att erbjuda dem som fortfarande använder GUI-gränssnittet för administration: installera hanterings verktygen på din administratörs arbets Station och hantera dina servrar via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="b7b45-109">I have a bit of advice to offer those of you who are still using the GUI for administration: install the management tools on your admin workstation and manage your servers remotely.</span></span> <span data-ttu-id="b7b45-110">På så sätt spelar det ingen roll om servern kör en GUI-eller Server Core-installation av operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="b7b45-110">This way it won't matter if the server is running a GUI or Server Core installation of the operating system.</span></span>
<span data-ttu-id="b7b45-111">Det hjälper dig att förbereda dig för att hantera servrar via en fjärr anslutning med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7b45-111">It's going to help prepare you for managing servers remotely with PowerShell.</span></span>

<span data-ttu-id="b7b45-112">Precis som i föregående kapitel måste du vara noga med att följa anvisningarna i Windows 10 Lab Environment-datorn.</span><span class="sxs-lookup"><span data-stu-id="b7b45-112">As with previous chapters, be sure to follow along on your Windows 10 lab environment computer.</span></span>

## <a name="one-liners"></a><span data-ttu-id="b7b45-113">En-liners</span><span class="sxs-lookup"><span data-stu-id="b7b45-113">One-Liners</span></span>

<span data-ttu-id="b7b45-114">En PowerShell-liner är en kontinuerlig pipeline och inte nödvändigt vis ett kommando som finns på en fysisk rad.</span><span class="sxs-lookup"><span data-stu-id="b7b45-114">A PowerShell one-liner is one continuous pipeline and not necessarily a command that’s on one physical line.</span></span> <span data-ttu-id="b7b45-115">Alla kommandon som finns på en fysisk rad är inte en-liners.</span><span class="sxs-lookup"><span data-stu-id="b7b45-115">Not all commands that are on one physical line are one-liners.</span></span>

<span data-ttu-id="b7b45-116">Även om följande kommando finns på flera fysiska rader, är det en PowerShell-liner eftersom det är en kontinuerlig pipeline.</span><span class="sxs-lookup"><span data-stu-id="b7b45-116">Even though the following command is on multiple physical lines, it's a PowerShell one-liner because it's one continuous pipeline.</span></span> <span data-ttu-id="b7b45-117">Det kan skrivas på en fysisk rad, men jag har valt rad brytning vid pipe-symbolen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-117">It could be written on one physical line, but I've chosen to line break at the pipe symbol.</span></span> <span data-ttu-id="b7b45-118">Pipe-symbolen är en av de tecken där en naturlig rad brytning tillåts i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7b45-118">The pipe symbol is one of the characters where a natural line break is allowed in PowerShell.</span></span>

```powershell
Get-Service |
  Where-Object CanPauseAndContinue -eq $true |
    Select-Object -Property *
```

```Output
Name                : LanmanWorkstation
RequiredServices    : {NSI, MRxSmb20, Bowser}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Workstation
DependentServices   : {SessionEnv, Netlogon, Browser}
MachineName         : .
ServiceName         : LanmanWorkstation
ServicesDependedOn  : {NSI, MRxSmb20, Bowser}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : Netlogon
RequiredServices    : {LanmanWorkstation}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Netlogon
DependentServices   : {}
MachineName         : .
ServiceName         : Netlogon
ServicesDependedOn  : {LanmanWorkstation}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :

Name                : vmicheartbeat
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Heartbeat Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicheartbeat
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmickvpexchange
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Data Exchange Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmickvpexchange
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicrdv
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Remote Desktop Virtualization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicrdv
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicshutdown
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Guest Shutdown Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmicshutdown
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmictimesync
RequiredServices    : {VmGid}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Time Synchronization Service
DependentServices   : {}
MachineName         : .
ServiceName         : vmictimesync
ServicesDependedOn  : {VmGid}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : vmicvss
RequiredServices    : {}
CanPauseAndContinue : True
CanShutdown         : False
CanStop             : True
DisplayName         : Hyper-V Volume Shadow Copy Requestor
DependentServices   : {}
MachineName         : .
ServiceName         : vmicvss
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :

Name                : Winmgmt
RequiredServices    : {RPCSS}
CanPauseAndContinue : True
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Management Instrumentation
DependentServices   : {wscsvc, NcaSvc, iphlpsvc}
MachineName         : .
ServiceName         : Winmgmt
ServicesDependedOn  : {RPCSS}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Automatic
Site                :
Container           :
```

<span data-ttu-id="b7b45-119">Naturliga rad brytningar kan ske på vanliga tecken, inklusive kommatecken ( `,` ) och inledande hakparenteser ( `[` ), klammerparenteser ( `{` ) och parenteser ( `(` ).</span><span class="sxs-lookup"><span data-stu-id="b7b45-119">Natural line breaks can occur at commonly used characters including comma (`,`) and opening brackets (`[`), braces (`{`), and parenthesis (`(`).</span></span> <span data-ttu-id="b7b45-120">Andra som inte är så vanliga inkluderar semikolon ( `;` ), likhets tecken ( `=` ) och båda inledande och dubbla citat tecken ( `'` , `"` ).</span><span class="sxs-lookup"><span data-stu-id="b7b45-120">Others that aren't so common include the semicolon (`;`), equals sign (`=`), and both opening single and double quotes (`'`,`"`).</span></span>

<span data-ttu-id="b7b45-121">Med hjälp av `` ` `` ett kontroversiellt-ämne () eller grav accent som ett linje fortsättnings avstånd.</span><span class="sxs-lookup"><span data-stu-id="b7b45-121">Using the backtick (`` ` ``) or grave accent character as a line continuation character is a controversial topic.</span></span> <span data-ttu-id="b7b45-122">Min rekommendation är att försöka undvika det om det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="b7b45-122">My recommendation is to try to avoid it if at all possible.</span></span> <span data-ttu-id="b7b45-123">Jag ser ofta PowerShell-kommandon som skrivs med ett bakstreck direkt efter ett naturligt rad brytnings kort.</span><span class="sxs-lookup"><span data-stu-id="b7b45-123">I often see PowerShell commands written using a backtick immediately after a natural line break character.</span></span>
<span data-ttu-id="b7b45-124">Det finns ingen anledning att det finns där.</span><span class="sxs-lookup"><span data-stu-id="b7b45-124">There's no reason for it to be there.</span></span>

```powershell
Get-Service -Name w32time |
>> Select-Object -Property *
```

```Output
Name                : w32time
RequiredServices    : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
DisplayName         : Windows Time
DependentServices   : {}
MachineName         : .
ServiceName         : w32time
ServicesDependedOn  : {}
ServiceHandle       : SafeServiceHandle
Status              : Running
ServiceType         : Win32ShareProcess
StartType           : Manual
Site                :
Container           :
```

<span data-ttu-id="b7b45-125">Kommandona som visas i föregående två exempel fungerar bra i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-125">The commands shown in the previous two examples work fine in the PowerShell console.</span></span> <span data-ttu-id="b7b45-126">Men om du försöker köra dem i konsol fönstret i PowerShell ISE genereras ett fel.</span><span class="sxs-lookup"><span data-stu-id="b7b45-126">But if you try to run them in the console pane of the PowerShell ISE, they'll generate an error.</span></span> <span data-ttu-id="b7b45-127">Konsol fönstret i PowerShell ISE väntar inte på att resten av kommandot ska anges på nästa rad som PowerShell-konsolen gör.</span><span class="sxs-lookup"><span data-stu-id="b7b45-127">The console pane of the PowerShell ISE doesn't wait for the rest of the command to be entered on the next line like the PowerShell console does.</span></span> <span data-ttu-id="b7b45-128">Undvik det här problemet i konsol fönstret i PowerShell ISE genom att använda <kbd>Shift</kbd> + <kbd>Enter</kbd> i stället för att trycka på <kbd>RETUR</kbd> när du fortsätter ett kommando på en annan rad.</span><span class="sxs-lookup"><span data-stu-id="b7b45-128">To avoid this problem in the console pane of the PowerShell ISE, use <kbd>Shift</kbd>+<kbd>Enter</kbd> instead of just pressing <kbd>Enter</kbd> when continuing a command on another line.</span></span>

<span data-ttu-id="b7b45-129">Det här nästa exemplet är inte en PowerShell-liner eftersom det inte är en kontinuerlig pipeline.</span><span class="sxs-lookup"><span data-stu-id="b7b45-129">This next example isn't a PowerShell one-liner because it's not one continuous pipeline.</span></span> <span data-ttu-id="b7b45-130">Det är två separata kommandon på en rad, åtskilda med semikolon.</span><span class="sxs-lookup"><span data-stu-id="b7b45-130">It's two separate commands on one line, separated by a semicolon.</span></span>

```powershell
$Service = 'w32time'; Get-Service -Name $Service
```

```powershell
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="b7b45-131">Många programmerings-och skript språk kräver ett semikolon i slutet av varje rad.</span><span class="sxs-lookup"><span data-stu-id="b7b45-131">Many programming and scripting languages require a semicolon at the end of each line.</span></span> <span data-ttu-id="b7b45-132">Även om de kan användas på det sättet i PowerShell rekommenderas de inte eftersom de inte behövs.</span><span class="sxs-lookup"><span data-stu-id="b7b45-132">While they can be used that way in PowerShell, it's not recommended because they're not needed.</span></span>

## <a name="filtering-left"></a><span data-ttu-id="b7b45-133">Filtrera vänster</span><span class="sxs-lookup"><span data-stu-id="b7b45-133">Filtering Left</span></span>

<span data-ttu-id="b7b45-134">Resultatet av de kommandon som visas i det här kapitlet har filtrerats ned till en delmängd.</span><span class="sxs-lookup"><span data-stu-id="b7b45-134">The results of the commands shown in this chapter have been filtered down to a subset.</span></span> <span data-ttu-id="b7b45-135">Används till exempel `Get-Service` med parametern **Name** för att filtrera listan över tjänster som bara returnerats till Windows tids tjänst.</span><span class="sxs-lookup"><span data-stu-id="b7b45-135">For example, `Get-Service` was used with the **Name** parameter to filter the list of services that were returned to only the Windows Time service.</span></span>

<span data-ttu-id="b7b45-136">I pipelinen vill du alltid filtrera resultaten nedåt till det du söker så tidigt som möjligt.</span><span class="sxs-lookup"><span data-stu-id="b7b45-136">In the pipeline, you always want to filter the results down to what you're looking for as early as possible.</span></span> <span data-ttu-id="b7b45-137">Detta görs med parametrar på det första kommandot eller längst till vänster.</span><span class="sxs-lookup"><span data-stu-id="b7b45-137">This is accomplished using parameters on the first command or, the one to the far left.</span></span>
<span data-ttu-id="b7b45-138">Detta kallas ibland _filtrering av Left_.</span><span class="sxs-lookup"><span data-stu-id="b7b45-138">This is sometimes called _filtering left_.</span></span>

<span data-ttu-id="b7b45-139">I följande exempel används parametern **Name** för `Get-Service` att omedelbart filtrera resultaten till Windows tids tjänst.</span><span class="sxs-lookup"><span data-stu-id="b7b45-139">The following example uses the **Name** parameter of `Get-Service` to immediately filter the results to the Windows Time service only.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="b7b45-140">Det är inte ovanligt att se exempel där kommandot är skickas för `Where-Object` att utföra filtreringen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-140">It's not uncommon to see examples where the command is piped to `Where-Object` to perform the filtering.</span></span>

```powershell
Get-Service | Where-Object Name -eq w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  W32Time            Windows Time
```

<span data-ttu-id="b7b45-141">Det första exemplet filtrerar på källan och returnerar bara resultatet för Windows tids tjänst.</span><span class="sxs-lookup"><span data-stu-id="b7b45-141">The first example filters at the source and only returns the results for the Windows Time service.</span></span>
<span data-ttu-id="b7b45-142">Det andra exemplet returnerar alla tjänster och skickar dem sedan till ett annat kommando för att utföra filtreringen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-142">The second example returns all the services then pipes them to another command to perform the filtering.</span></span> <span data-ttu-id="b7b45-143">Det kanske inte ser ut som ett stort avtal i det här exemplet, Tänk på att du har frågat om en lista över Active Directory användare.</span><span class="sxs-lookup"><span data-stu-id="b7b45-143">While this may not seem like a big deal in this example, imagine if you were querying a list of Active Directory users.</span></span> <span data-ttu-id="b7b45-144">Vill du verkligen returnera informationen för många tusentals användar konton från Active Directory endast för att skicka dem till ett annat kommando som filtrerar dem ned till en liten delmängd?</span><span class="sxs-lookup"><span data-stu-id="b7b45-144">Do you really want to return the information for many thousands of user accounts from Active Directory only to pipe them to another command that filters them down to a tiny subset?</span></span> <span data-ttu-id="b7b45-145">Min rekommendation är att alltid filtrera från vänster även om det inte verkar vara så viktigt.</span><span class="sxs-lookup"><span data-stu-id="b7b45-145">My recommendation is to always filter left even when it doesn't seem to matter.</span></span> <span data-ttu-id="b7b45-146">Du kommer att använda den för att automatiskt filtrera från vänster när det verkligen spelar någon roll.</span><span class="sxs-lookup"><span data-stu-id="b7b45-146">You'll be so use to it that you'll automatically filter left when it really does matter.</span></span>

<span data-ttu-id="b7b45-147">När jag har haft någon talan om för mig att du har angett kommandona i spelar ingen roll.</span><span class="sxs-lookup"><span data-stu-id="b7b45-147">I once had someone tell me that the order you specify the commands in doesn't matter.</span></span> <span data-ttu-id="b7b45-148">Det gick inte att göra ytterligare från sanningen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-148">That couldn't be further from the truth.</span></span> <span data-ttu-id="b7b45-149">Den ordning som kommandona anges i spelar själva roll när filtreringen utförs.</span><span class="sxs-lookup"><span data-stu-id="b7b45-149">The order that the commands are specified in does indeed matter when performing filtering.</span></span> <span data-ttu-id="b7b45-150">Anta till exempel scenariot där du använder `Select-Object` för att välja bara några få egenskaper och `Where-Object` filtrera på egenskaper som inte kommer att visas i valet.</span><span class="sxs-lookup"><span data-stu-id="b7b45-150">For example, consider the scenario where you are using `Select-Object` to select only a few properties and `Where-Object` to filter on properties that won't be in the selection.</span></span> <span data-ttu-id="b7b45-151">I så fall måste filtreringen först inträffa, annars finns inte egenskapen i pipelinen när du försöker utföra filtreringen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-151">In that scenario, the filtering must occur first, otherwise the property won't exist in the pipeline when try to perform the filtering.</span></span>

```powershell
Get-Service |
Select-Object -Property DisplayName, Running, Status |
Where-Object CanPauseAndContinue
```

<span data-ttu-id="b7b45-152">Kommandot i föregående exempel returnerar inte några resultat eftersom egenskapen **CanStopAndContinue** inte finns när resultatet av `Select-Object` är skickas till `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-152">The command in the previous example doesn't return any results because the **CanStopAndContinue** property doesn't exist when the results of `Select-Object` are piped to `Where-Object`.</span></span> <span data-ttu-id="b7b45-153">Den aktuella egenskapen har inte marker ATS.</span><span class="sxs-lookup"><span data-stu-id="b7b45-153">That particular property wasn't "selected".</span></span> <span data-ttu-id="b7b45-154">I själva verket har den filtrerats bort. Ändra ordning på `Select-Object` och `Where-Object` genererar önskade resultat.</span><span class="sxs-lookup"><span data-stu-id="b7b45-154">In essence, it was filtered out. Reversing the order of `Select-Object` and `Where-Object` produces the desired results.</span></span>

```powershell
Get-Service |
Where-Object CanPauseAndContinue |
Select-Object -Property DisplayName, Status
```

```Output
DisplayName                                    Status
-----------                                    ------
Workstation                                    Running
Netlogon                                       Running
Hyper-V Heartbeat Service                      Running
Hyper-V Data Exchange Service                  Running
Hyper-V Remote Desktop Virtualization Service  Running
Hyper-V Guest Shutdown Service                 Running
Hyper-V Time Synchronization Service           Running
Hyper-V Volume Shadow Copy Requestor           Running
Windows Management Instrumentation             Running
```

## <a name="the-pipeline"></a><span data-ttu-id="b7b45-155">Pipelinen</span><span class="sxs-lookup"><span data-stu-id="b7b45-155">The Pipeline</span></span>

<span data-ttu-id="b7b45-156">Som du har sett i många av exemplen som visas hittills i denna bok, kan många gånger använda utdata från ett kommando som indata för ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="b7b45-156">As you've seen in many of the examples shown so far throughout this book, many times the output of one command can be used as input for another command.</span></span> <span data-ttu-id="b7b45-157">I kapitel 3 `Get-Member` användes för att avgöra vilken typ av objekt ett kommando genererar.</span><span class="sxs-lookup"><span data-stu-id="b7b45-157">In Chapter 3, `Get-Member` was used to determine what type of object a command produces.</span></span> <span data-ttu-id="b7b45-158">Kapitel 3 visar också hur du använder **ParameterType** -parametern för `Get-Command` för att avgöra vilka kommandon som godkände den typen av indatatyper, även om de inte nödvändigt vis är inaktuella.</span><span class="sxs-lookup"><span data-stu-id="b7b45-158">Chapter 3 also showed using the **ParameterType** parameter of `Get-Command` to determine what commands accepted that type of input, although not necessarily by pipeline input.</span></span>

<span data-ttu-id="b7b45-159">Beroende på hur grundligt ett kommando bidrar är, kan det innehålla avsnittet **indata** och **utdata** .</span><span class="sxs-lookup"><span data-stu-id="b7b45-159">Depending on how thorough a commands help is, it may include an **INPUTS** and **OUTPUTS** section.</span></span>

```powershell
help Stop-Service -Full
```

```Output
...
INPUTS
    System.ServiceProcess.ServiceController, System.String
        You can pipe a service object or a string that contains the name of a service
        to this cmdlet.

OUTPUTS
    None, System.ServiceProcess.ServiceController
        This cmdlet generates a System.ServiceProcess.ServiceController object that
        represents the service, if you use the PassThru parameter. Otherwise, this
        cmdlet does not generate any output.
...
```

<span data-ttu-id="b7b45-160">Endast det relevanta avsnittet av hjälpen visas i föregående resultat.</span><span class="sxs-lookup"><span data-stu-id="b7b45-160">Only the relevant section of the help is shown in the previous results.</span></span> <span data-ttu-id="b7b45-161">Som du kan se anger **indata** avsnittet att ett **ServiceController** eller ett **String** -objekt kan skickas till `Stop-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b7b45-161">As you can see, the **INPUTS** section states that a **ServiceController** or a **String** object can be piped to the `Stop-Service` cmdlet.</span></span> <span data-ttu-id="b7b45-162">Det visar inte vilka parametrar som accepterar den typen av inaktuella indatatyper.</span><span class="sxs-lookup"><span data-stu-id="b7b45-162">It doesn't tell you which parameters accept that type of input.</span></span> <span data-ttu-id="b7b45-163">Ett av de enklaste sätten att fastställa att informationen är att titta igenom de olika parametrarna i den fullständiga versionen av hjälpen för `Stop-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b7b45-163">One of the easiest ways to determine that information is to look through the different parameters in the full version of the help for the `Stop-Service` cmdlet.</span></span>

```powershell
help Stop-Service -Full
```

```powershell
...
-DisplayName <String[]>
    Specifies the display names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false

-InputObject <ServiceController[]>
    Specifies ServiceController objects that represent the services to stop. Enter a
    variable that contains the objects, or type a command or expression that gets the
    objects.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByValue)
    Accept wildcard characters?  false

-Name <String[]>
    Specifies the service names of the services to stop. Wildcard characters are
    permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  false
...
```

<span data-ttu-id="b7b45-164">Jag har återigen visat den relevanta delen av hjälpen i den föregående uppsättningen med resultat.</span><span class="sxs-lookup"><span data-stu-id="b7b45-164">Once again, I've only shown the relevant portion of the help in the previous set of results.</span></span> <span data-ttu-id="b7b45-165">Observera att parametern **DisplayName** inte accepterar pipeline-indatatyper, **InputObject** -parametern godkänner pipeline-inmatade **värden** för **ServiceController** -objekt och parametern **Name** accepterar pipeline-inmatade **med värde** för **sträng** objekt.</span><span class="sxs-lookup"><span data-stu-id="b7b45-165">Notice that the **DisplayName** parameter doesn't accept pipeline input, the **InputObject** parameter accepts pipeline input **by value** for **ServiceController** objects, and the **Name** parameter accepts pipeline input **by value** for **string** objects.</span></span> <span data-ttu-id="b7b45-166">Den accepterar också pipeline-inmatade **efter egenskaps namn**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-166">It also accepts pipeline input **by property name**.</span></span>

<span data-ttu-id="b7b45-167">När en parameter accepterar pipeline-inmatade med både egenskaps namn och värde, försöker den alltid **med värdet** först.</span><span class="sxs-lookup"><span data-stu-id="b7b45-167">When a parameter accepts pipeline input by both property name and by value, it always tries **by value** first.</span></span> <span data-ttu-id="b7b45-168">Om **värdet** inte kan utföras försöker det **med ett egenskaps namn**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-168">If **by value** fails, then it tries **by property name**.</span></span> <span data-ttu-id="b7b45-169">**Värdet** är lite missvisande.</span><span class="sxs-lookup"><span data-stu-id="b7b45-169">**By value** is a little misleading.</span></span> <span data-ttu-id="b7b45-170">Jag föredrar att anropa den **efter typ**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-170">I prefer to call it **by type**.</span></span> <span data-ttu-id="b7b45-171">Det innebär att om du rör resultatet av ett kommando som skapar en **ServiceController** objekt typ till `Stop-Service` , binder det inmatade objekt till **InputObject** -parametern.</span><span class="sxs-lookup"><span data-stu-id="b7b45-171">This means if you pipe the results of a command that produces a **ServiceController** object type to `Stop-Service`, it binds that input to the **InputObject** parameter.</span></span> <span data-ttu-id="b7b45-172">Men om du rör resultatet av ett kommando som producerar **sträng** utdata till `Stop-Service` binder det till **namn** parametern.</span><span class="sxs-lookup"><span data-stu-id="b7b45-172">But if you pipe the results of a command that produces **String** output to `Stop-Service`, it binds it to the **Name** parameter.</span></span> <span data-ttu-id="b7b45-173">Om du lägger till resultatet av ett kommando som inte genererar ett **ServiceController** -eller **String** -objekt till `Stop-Service` , men det genererar utdata som innehåller en egenskap som heter **Name**, binder egenskapen **Name** från utdata till **Name** -parametern för `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-173">If you pipe the results of a command that doesn't produce a **ServiceController** or **String** object to `Stop-Service`, but it does produce output containing a property called **Name**, then it binds the **Name** property from the output to the **Name** parameter of `Stop-Service`.</span></span>

<span data-ttu-id="b7b45-174">Bestäm vilken typ av utdata som `Get-Service` kommandot genererar.</span><span class="sxs-lookup"><span data-stu-id="b7b45-174">Determine what type of output the `Get-Service` command produces.</span></span>

```powershell
Get-Service -Name w32time | Get-Member
```

```Output
   TypeName: System.ServiceProcess.ServiceController
```

<span data-ttu-id="b7b45-175">`Get-Service`skapar en ServiceController objekt typ.</span><span class="sxs-lookup"><span data-stu-id="b7b45-175">`Get-Service` produces a ServiceController object type.</span></span>

<span data-ttu-id="b7b45-176">Som du såg tidigare i hjälpen, **InputObject** -parametern för `Stop-Service` accepterar **ServiceController** -objekt via pipelinen **efter värde** (efter typ).</span><span class="sxs-lookup"><span data-stu-id="b7b45-176">As you previously saw in the help, the **InputObject** parameter of `Stop-Service` accepts **ServiceController** objects via the pipeline **by value** (by type).</span></span> <span data-ttu-id="b7b45-177">Det innebär att när resultatet av `Get-Service` cmdleten är skickas `Stop-Service` , binder de till **InputObject** -parametern för `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-177">This means that when the results of the `Get-Service` cmdlet are piped to `Stop-Service`, they bind to the **InputObject** parameter of `Stop-Service`.</span></span>

```powershell
Get-Service -Name w32time | Stop-Service
```

<span data-ttu-id="b7b45-178">Nu kan du prova sträng inmatade.</span><span class="sxs-lookup"><span data-stu-id="b7b45-178">Now to try string input.</span></span> <span data-ttu-id="b7b45-179">Pipe `w32time` för att `Get-Member` bara bekräfta att det är en sträng.</span><span class="sxs-lookup"><span data-stu-id="b7b45-179">Pipe `w32time` to `Get-Member` just to confirm that it's a string.</span></span>

```powershell
'w32time' | Get-Member
```

```Output
   TypeName: System.String
```

<span data-ttu-id="b7b45-180">Som tidigare har visats i hjälpen, rör sig en sträng för att `Stop-Service` binda den **efter värde** till **namn** parametern för `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-180">As previously shown in the help, piping a string to `Stop-Service` binds it **by value** to the **Name** parameter of `Stop-Service`.</span></span> <span data-ttu-id="b7b45-181">Testa detta genom att skicka vidare `w32time` till `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-181">Test this by piping `w32time` to `Stop-Service`.</span></span>

```powershell
'w32time' | Stop-Service
```

<span data-ttu-id="b7b45-182">Lägg märke till att jag använde enkla citat tecken runt strängen i föregående exempel `w32time` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-182">Notice that in the previous example, I used single quotes around the string `w32time`.</span></span> <span data-ttu-id="b7b45-183">I PowerShell bör du alltid använda enkla citat tecken i stället för dubbla citat tecken om inte innehållet i den citerade strängen innehåller en variabel som måste utökas till det faktiska värdet.</span><span class="sxs-lookup"><span data-stu-id="b7b45-183">In PowerShell, you should always use single quotes instead of double quotes unless the contents of the quoted string contains a variable that needs to be expanded to its actual value.</span></span> <span data-ttu-id="b7b45-184">Med hjälp av enkla citat tecken behöver inte PowerShell parsa innehållet i citat tecken så att koden körs lite snabbare.</span><span class="sxs-lookup"><span data-stu-id="b7b45-184">By using single quotes, PowerShell doesn't have to parse the contents contained within the quotes so your code runs a little faster.</span></span>

<span data-ttu-id="b7b45-185">Skapa ett anpassat objekt för att testa pipeline-inmatade efter egenskaps namn för parametern **Name** i `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-185">Create a custom object to test pipeline input by property name for the **Name** parameter of `Stop-Service`.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
>> Name = 'w32time'
>> }
```

<span data-ttu-id="b7b45-186">Innehållet i **CustomObject** -variabeln är en **PSCustomObject** objekt typ och innehåller en egenskap med namnet **Name**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-186">The contents of the **CustomObject** variable is a **PSCustomObject** object type and it contains a property named **Name**.</span></span>

```powershell
$CustomObject | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Name        NoteProperty string Name=w32time
```

<span data-ttu-id="b7b45-187">Om du omger `$CustomObject` variabeln med citat tecken vill du använda dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b7b45-187">If you were to surround the `$CustomObject` variable with quotes, you want to use double quotes.</span></span>
<span data-ttu-id="b7b45-188">Annars är den litterala strängen `$CustomObject` skickas till `Get-Member` i stället för värdet som variabeln innehåller, med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b7b45-188">Otherwise, using single quotes, the literal string `$CustomObject` is piped to `Get-Member` instead of the value contained by the variable.</span></span>

<span data-ttu-id="b7b45-189">Även om innehållet i `$CustomObject` till `Stop-Service` cmdleten binds till **Name** -parametern, binds den här tiden **efter egenskaps namn** i stället för **värdet** eftersom innehållet i `$CustomObject` är ett objekt som har en egenskap med namnet **Name**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-189">Although piping the contents of `$CustomObject` to `Stop-Service` cmdlet binds to the **Name** parameter, this time it binds **by property name** instead of **by value** because the contents of `$CustomObject` is an object that has a property named **Name**.</span></span>

<span data-ttu-id="b7b45-190">I det här exemplet skapar jag ett annat anpassat objekt med ett annat egenskaps namn, t. ex. **tjänst**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-190">In this example, I create another custom object using a different property name, such as **Service**.</span></span>

```powershell
$CustomObject = [pscustomobject]@{
  Service = 'w32time'
}
```

<span data-ttu-id="b7b45-191">Ett fel genereras vid försök att skicka `$CustomObject` en pipe till `Stop-Service` eftersom det inte genererar ett **ServiceController** -eller **String** -objekt, och det har inte någon egenskap med namnet **Name**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-191">An error is generated when trying to pipe `$CustomObject` to `Stop-Service` because it doesn't produce a **ServiceController** or **String** object, and it doesn't have a property named **Name**.</span></span>

```powershell
$CustomObject | Stop-Service
```

```Output
Stop-Service : Cannot find any service with service name '@{Service=w32time}'.
At line:1 char:17
+ $CustomObject | Stop-Service
+
    + CategoryInfo          : ObjectNotFound: (@{Service=w32time}:String) [Stop-Service]
   , ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.S
   topServiceCommand
```

<span data-ttu-id="b7b45-192">Om utdata från ett kommando inte raderas med inmatnings alternativen för pipelinen för ett annat kommando, `Select-Object` kan användas för att byta namn på egenskapen så att egenskaperna är korrekt.</span><span class="sxs-lookup"><span data-stu-id="b7b45-192">If the output of one command doesn't line up with the pipeline input options for another command, `Select-Object` can be used to rename the property so that the properties lineup correctly.</span></span>

```powershell
$CustomObject |
  Select-Object -Property @{name='Name';expression={$_.Service}} |
    Stop-Service
```

<span data-ttu-id="b7b45-193">I det här exemplet `Select-Object` användes för att byta namn på **tjänst** egenskapen till en egenskap med namnet **Name**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-193">In this example, `Select-Object` was used to rename the **Service** property to a property named **Name**.</span></span>

<span data-ttu-id="b7b45-194">Syntaxen det här exemplet kan förefalla lite komplicerat vid första.</span><span class="sxs-lookup"><span data-stu-id="b7b45-194">The syntax this example may seem a little complicated at first.</span></span> <span data-ttu-id="b7b45-195">Det jag har lärt dig är att du aldrig får lära dig syntaxen genom att kopiera och klistra in kod.</span><span class="sxs-lookup"><span data-stu-id="b7b45-195">What I have learned is that you'll never learn the syntax by copy and pasting code.</span></span> <span data-ttu-id="b7b45-196">Ta tid att ange koden i.</span><span class="sxs-lookup"><span data-stu-id="b7b45-196">Take the time to type the code in.</span></span> <span data-ttu-id="b7b45-197">Efter några gånger blir det andra natur.</span><span class="sxs-lookup"><span data-stu-id="b7b45-197">After a few times, it becomes second nature.</span></span> <span data-ttu-id="b7b45-198">Att ha flera övervakare är en enorm förmån eftersom du kan visa exempel koden på en skärm och skriva den i en annan.</span><span class="sxs-lookup"><span data-stu-id="b7b45-198">Having multiple monitors is a huge benefit because you can display the example code on one screen and type it in on another one.</span></span>

<span data-ttu-id="b7b45-199">Ibland kanske du vill använda en parameter som inte accepterar pipeline-inflöden.</span><span class="sxs-lookup"><span data-stu-id="b7b45-199">Occasionally, you may want to use a parameter that doesn't accept pipeline input.</span></span> <span data-ttu-id="b7b45-200">Följande exempel visar hur du använder utdata från ett kommando som indata för ett annat.</span><span class="sxs-lookup"><span data-stu-id="b7b45-200">The following example demonstrates using the output of one command as input for another.</span></span> <span data-ttu-id="b7b45-201">Spara först visnings namnet för ett par Windows-tjänster i en textfil.</span><span class="sxs-lookup"><span data-stu-id="b7b45-201">First save the display name for a couple of Windows services into a text file.</span></span>

```powershell
'Background Intelligent Transfer Service', 'Windows Time' |
Out-File -FilePath $env:TEMP\services.txt
```

<span data-ttu-id="b7b45-202">Du kan köra kommandot som tillhandahåller de utdata som krävs inom parentes som värdet för parametern för kommandot som kräver indatan.</span><span class="sxs-lookup"><span data-stu-id="b7b45-202">You can run the command that provides the needed output within parentheses as the value for the parameter of the command requiring the input.</span></span>

```powershell
Stop-Service -DisplayName (Get-Content -Path $env:TEMP\services.txt)
```

<span data-ttu-id="b7b45-203">Detta är precis som drifts ordningen i algebra för dem som kommer ihåg hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="b7b45-203">This is just like order of operations in Algebra for those of you who remember how it works.</span></span> <span data-ttu-id="b7b45-204">Kommandot inom parentes körs alltid före den yttre delen av kommandot.</span><span class="sxs-lookup"><span data-stu-id="b7b45-204">The command within parentheses always runs prior to the outer portion of the command.</span></span>

## <a name="powershellget"></a><span data-ttu-id="b7b45-205">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="b7b45-205">PowerShellGet</span></span>

<span data-ttu-id="b7b45-206">PowerShellGet är en PowerShell-modul som innehåller kommandon för att upptäcka, installera, publicera och uppdatera PowerShell-moduler (och andra artefakter) till eller från en NuGet-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="b7b45-206">PowerShellGet is a PowerShell module that contains commands for discovering, installing, publishing, and updating PowerShell modules (and other artifacts) to or from a NuGet repository.</span></span> <span data-ttu-id="b7b45-207">PowerShellGet levereras med PowerShell version 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b7b45-207">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="b7b45-208">Den är tillgänglig som en separat nedladdning för PowerShell version 3,0 och högre.</span><span class="sxs-lookup"><span data-stu-id="b7b45-208">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="b7b45-209">Microsoft är värd för en NuGet-lagringsplats online som kallas för [PowerShell-galleriet][].</span><span class="sxs-lookup"><span data-stu-id="b7b45-209">Microsoft hosts an online NuGet repository called the [PowerShell Gallery][].</span></span> <span data-ttu-id="b7b45-210">Även om den här lagrings platsen är värd för Microsoft, skrivs majoriteten av modulerna i lagrings platsen inte av Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b7b45-210">Although this repository is hosted by Microsoft, the majority of the modules contained within the repository aren't written by Microsoft.</span></span> <span data-ttu-id="b7b45-211">All kod som hämtas från PowerShell-galleriet bör granskas noggrant i en isolerad test miljö innan den anses vara lämplig för användning i en produktions miljö.</span><span class="sxs-lookup"><span data-stu-id="b7b45-211">Any code obtain from the PowerShell Gallery should be thoroughly reviewed in an isolated test environment before being considered suitable for use in a production environment.</span></span>

<span data-ttu-id="b7b45-212">De flesta företag vill ha sina egna interna privata NuGet-lagringsplatser där de bara kan publicera sina interna användnings moduler och moduler som de har laddat ned från andra källor när de har verifierat att de inte är skadliga.</span><span class="sxs-lookup"><span data-stu-id="b7b45-212">Most companies will want to host their own internal private NuGet repository where they can post their internal use only modules as well as modules that they've downloaded from other sources once they've validated them as being non-malicious.</span></span>

<span data-ttu-id="b7b45-213">Använd `Find-Module` cmdleten som är en del av PowerShellGet-modulen för att hitta en modul i PowerShell-galleriet som jag skrev med namnet MrToolkit.</span><span class="sxs-lookup"><span data-stu-id="b7b45-213">Use the `Find-Module` cmdlet that's part of the PowerShellGet module to find a module in the PowerShell Gallery that I wrote named MrToolkit.</span></span>

```powershell
Find-Module -Name MrToolkit
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with
NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or
'C:\Users\MrAdmin\AppData\Local\PackageManagement\ProviderAssemblies'. You can also
install the NuGet provider by running 'Install-PackageProvider -Name NuGet
-MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the
NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1        MrToolkit                           PSGallery            Misc PowerShell Tools
```

<span data-ttu-id="b7b45-214">Första gången du använder ett av kommandona från PowerShellGet-modulen uppmanas du att installera NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="b7b45-214">The first time you use one of the commands from the PowerShellGet module, you'll be prompted to install the NuGet provider.</span></span>

<span data-ttu-id="b7b45-215">Du installerar MrToolkit-modulen genom att skicka det tidigare kommandot till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-215">To install the MrToolkit module, pipe the previous command to `Install-Module`.</span></span>

```powershell
Find-Module -Name MrToolkit | Install-Module
```

```Output
Untrusted repository
You are installing the modules from an untrusted repository. If you trust this
repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet.
Are you sure you want to install the modules from
'https://www.powershellgallery.com/api/v2/'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): y
```

<span data-ttu-id="b7b45-216">Eftersom PowerShell-galleriet är ett ej betrott lager, uppmanas du att godkänna installationen av modulen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-216">Since the PowerShell Gallery is an untrusted repository, it prompts you to approve the installation of the module.</span></span>

## <a name="finding-pipeline-input-the-easy-way"></a><span data-ttu-id="b7b45-217">Hitta pipeline-inmatare det enkla sättet</span><span class="sxs-lookup"><span data-stu-id="b7b45-217">Finding pipeline input the easy way</span></span>

<span data-ttu-id="b7b45-218">MrToolkit-modulen innehåller en funktion med namnet `Get-MrPipelineInput` .</span><span class="sxs-lookup"><span data-stu-id="b7b45-218">The MrToolkit module contains a function named `Get-MrPipelineInput`.</span></span> <span data-ttu-id="b7b45-219">Denna cmdlet kan användas för att enkelt avgöra vilka parametrar i ett kommando som accepterar pipeline-inflöde, vilken typ av objekt som de accepterar, och om de accepterar pipeline-inmatade **efter värde** eller **egenskaps namn**.</span><span class="sxs-lookup"><span data-stu-id="b7b45-219">This cmdlet can be used to easily determine which parameters of a command accept pipeline input, what type of object they accept, and if they accept pipeline input **by value** or **by property name**.</span></span>

```powershell
Get-MrPipelineInput -Name Stop-Service
```

```Output
ParameterName ParameterType                             ValueFromPipeline ValueFromPipelineByPropertyName
------------- -------------                             ----------------- ---------------
InputObject   System.ServiceProcess.ServiceController[]              True           False
Name          System.String[]                                        True            True
```

<span data-ttu-id="b7b45-220">Som du ser kan samma information som vi tidigare fastställde genom att gå igenom hjälpen enkelt bestämmas med den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="b7b45-220">As you can see, the same information we previously determined by sifting through the help can easily be determined with this function.</span></span>

## <a name="summary"></a><span data-ttu-id="b7b45-221">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="b7b45-221">Summary</span></span>

<span data-ttu-id="b7b45-222">I det här kapitlet har du lärt dig om PowerShell One-liners.</span><span class="sxs-lookup"><span data-stu-id="b7b45-222">In this chapter, you've learned about PowerShell one-liners.</span></span> <span data-ttu-id="b7b45-223">Du har lärt dig att antalet fysiska rader som ett kommando är på inte har något att göra med om det är en PowerShell-liner.</span><span class="sxs-lookup"><span data-stu-id="b7b45-223">You've learned that the number of physical lines that a command is on has nothing to do with whether or not it's a PowerShell one-liner.</span></span> <span data-ttu-id="b7b45-224">Du har också lärt dig om filtrering, till vänster, pipelinen och PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="b7b45-224">You've also learned about filtering left, the pipeline, and PowerShellGet.</span></span>

## <a name="review"></a><span data-ttu-id="b7b45-225">Granska</span><span class="sxs-lookup"><span data-stu-id="b7b45-225">Review</span></span>

1. <span data-ttu-id="b7b45-226">Vad är en PowerShell-liner?</span><span class="sxs-lookup"><span data-stu-id="b7b45-226">What is a PowerShell one-liner?</span></span>
1. <span data-ttu-id="b7b45-227">Vad är några av de tecken där naturliga rad brytningar kan uppstå i PowerShell?</span><span class="sxs-lookup"><span data-stu-id="b7b45-227">What are some of the characters where natural line breaks can occur in PowerShell?</span></span>
1. <span data-ttu-id="b7b45-228">Varför ska du filtrera kvar?</span><span class="sxs-lookup"><span data-stu-id="b7b45-228">Why should you filter left?</span></span>
1. <span data-ttu-id="b7b45-229">Vilka är de två sätt som ett PowerShell-kommando kan acceptera för pipeline-inmatade?</span><span class="sxs-lookup"><span data-stu-id="b7b45-229">What are the two ways that a PowerShell command can accept pipeline input?</span></span>
1. <span data-ttu-id="b7b45-230">Varför ska du inte lita på kommandon som du hittar i PowerShell-galleriet?</span><span class="sxs-lookup"><span data-stu-id="b7b45-230">Why shouldn't you trust commands found in the PowerShell Gallery?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="b7b45-231">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="b7b45-231">Recommended Reading</span></span>

- <span data-ttu-id="b7b45-232">[about_Pipelines][]</span><span class="sxs-lookup"><span data-stu-id="b7b45-232">[about_Pipelines][]</span></span>
- <span data-ttu-id="b7b45-233">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="b7b45-233">[about_Command_Syntax][]</span></span>
- <span data-ttu-id="b7b45-234">[about_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="b7b45-234">[about_Parameters][]</span></span>
- <span data-ttu-id="b7b45-235">[PowerShellGet: det stora enkla sättet att identifiera, installera och uppdatera PowerShell-moduler][psget]</span><span class="sxs-lookup"><span data-stu-id="b7b45-235">[PowerShellGet: The BIG EASY way to discover, install, and update PowerShell modules][psget]</span></span>

<!-- link references-->
[about_Pipelines]: /powershell/module/microsoft.powershell.core/about/about_pipelines
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[about_Parameters]: /powershell/module/microsoft.powershell.core/about/about_parameters
[psget]: https://mikefrobbins.com/2015/04/23/powershellget-the-big-easy-way-to-discover-install-and-update-powershell-modules/
[PowerShell-galleriet]: https://www.powershellgallery.com/
[PowerShell Gallery]: https://www.powershellgallery.com/
