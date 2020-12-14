---
description: Beskriver PowerShell-sessioner (PSSessions) och förklarar hur du upprättar en permanent anslutning till en fjärrdator.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: edc7109f3f79376ac1d348d3c3cd65e3a8d3e69c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708471"
---
# <a name="about-pssessions"></a><span data-ttu-id="959c9-103">Om PSSessions</span><span class="sxs-lookup"><span data-stu-id="959c9-103">About PSSessions</span></span>

## <a name="short-description"></a><span data-ttu-id="959c9-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="959c9-104">Short Description</span></span>
<span data-ttu-id="959c9-105">Beskriver PowerShell-sessioner (PSSessions) och förklarar hur du upprättar en permanent anslutning till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="959c9-105">Describes PowerShell sessions (PSSessions) and explains how to establish a persistent connection to a remote computer.</span></span>

## <a name="long-description"></a><span data-ttu-id="959c9-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="959c9-106">Long Description</span></span>

<span data-ttu-id="959c9-107">Om du vill köra PowerShell-kommandon på en fjärrdator kan du använda parametern **computername** för en cmdlet, eller så kan du skapa en PowerShell-session (PSSession) och köra kommandon i PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-107">To run PowerShell commands on a remote computer, you can use the **ComputerName** parameter of a cmdlet, or you can create a PowerShell session (PSSession) and run commands in the PSSession.</span></span>

<span data-ttu-id="959c9-108">När du skapar en PSSession upprättar PowerShell en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="959c9-108">When you create a PSSession, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="959c9-109">Använd en PSSession för att köra en serie relaterade kommandon på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="959c9-109">Use a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="959c9-110">Kommandon som körs i samma PSSession kan dela data, till exempel värden för variabler, alias och funktioner.</span><span class="sxs-lookup"><span data-stu-id="959c9-110">Commands that run in the same PSSession can share data, such as the values of variables, aliases, and functions.</span></span>

<span data-ttu-id="959c9-111">Du kan också skapa en PSSession på den lokala datorn och köra kommandon i den.</span><span class="sxs-lookup"><span data-stu-id="959c9-111">You can also create a PSSession on the local computer and run commands in it.</span></span>
<span data-ttu-id="959c9-112">En lokal PSSession använder PowerShell-infrastrukturen för fjärr kommunikation för att skapa och underhålla PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-112">A local PSSession uses the PowerShell remoting infrastructure to create and maintain the PSSession.</span></span>

<span data-ttu-id="959c9-113">Från och med Windows PowerShell 3,0 är PSSessions oberoende av de sessioner som de skapas i.</span><span class="sxs-lookup"><span data-stu-id="959c9-113">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they are created.</span></span> <span data-ttu-id="959c9-114">Aktiva PSSessions underhålls på fjärrdatorn (eller datorn på fjärrplatsen eller "Server sidan" i anslutningen).</span><span class="sxs-lookup"><span data-stu-id="959c9-114">Active PSSessions are maintained on the remote computer (or the computer at the remote end or "server-side" of the connection).</span></span> <span data-ttu-id="959c9-115">Därför kan du koppla från PSSession och återansluta till den vid ett senare tillfälle från samma dator eller från en annan dator.</span><span class="sxs-lookup"><span data-stu-id="959c9-115">As a result, you can disconnect from the PSSession and reconnect to it at a later time from the same computer or from a different computer.</span></span>

<span data-ttu-id="959c9-116">I det här avsnittet beskrivs hur du skapar, använder, hämtar och tar bort PSSessions.</span><span class="sxs-lookup"><span data-stu-id="959c9-116">This topic explains how to create, use, get, and delete PSSessions.</span></span> <span data-ttu-id="959c9-117">Mer avancerad information finns i [about_PSSession_Details](about_PSSession_Details.md).</span><span class="sxs-lookup"><span data-stu-id="959c9-117">For more advanced information, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

<span data-ttu-id="959c9-118">Obs: PSSessions använder PowerShell-fjärrinfrastrukturen.</span><span class="sxs-lookup"><span data-stu-id="959c9-118">Note: PSSessions use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="959c9-119">För att kunna använda PSSessions måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="959c9-119">To use PSSessions, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="959c9-120">Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="959c9-120">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

<span data-ttu-id="959c9-121">I Windows Vista och senare versioner av Windows måste du starta PowerShell med alternativet "kör som administratör" för att kunna skapa en PSSession på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="959c9-121">In Windows Vista and later versions of Windows, to create a PSSession on a local computer, you must start PowerShell with the "Run as administrator" option.</span></span>

## <a name="what-is-a-session"></a><span data-ttu-id="959c9-122">Vad är en session?</span><span class="sxs-lookup"><span data-stu-id="959c9-122">What Is a Session?</span></span>

<span data-ttu-id="959c9-123">En session är en miljö där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="959c9-123">A session is an environment in which PowerShell runs.</span></span>

<span data-ttu-id="959c9-124">Varje gången du startar PowerShell skapas en session åt dig, och du kan köra kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="959c9-124">Each time you start PowerShell, a session is created for you, and you can run commands in the session.</span></span> <span data-ttu-id="959c9-125">Du kan också lägga till objekt i din session, till exempel moduler och snapin-moduler, och du kan skapa objekt, till exempel variabler, funktioner och alias.</span><span class="sxs-lookup"><span data-stu-id="959c9-125">You can also add items to your session, such as modules and snap-ins, and you can create items, such as variables, functions, and aliases.</span></span> <span data-ttu-id="959c9-126">Dessa objekt finns bara i sessionen och tas bort när sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="959c9-126">These items exist only in the session and are deleted when the session ends.</span></span>

<span data-ttu-id="959c9-127">Du kan också skapa användar hanterade sessioner som kallas "PowerShell-sessioner" eller "PSSessions" på den lokala datorn eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="959c9-127">You can also create user-managed sessions, known as " PowerShell sessions" or "PSSessions," on the local computer or on a remote computer.</span></span> <span data-ttu-id="959c9-128">Precis som Standardsessionen kan du köra kommandon i en PSSession och lägga till och skapa objekt.</span><span class="sxs-lookup"><span data-stu-id="959c9-128">Like the default session, you can run commands in a PSSession and add and create items.</span></span> <span data-ttu-id="959c9-129">Men till skillnad från den session som startar automatiskt kan du kontrol lera de PSSessions som du skapar.</span><span class="sxs-lookup"><span data-stu-id="959c9-129">However, unlike the session that starts automatically, you can control the PSSessions that you create.</span></span> <span data-ttu-id="959c9-130">Du kan hämta, skapa, konfigurera och ta bort dem, koppla från och återansluta till dem och köra flera kommandon i samma PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-130">You can get, create, configure, and remove them, disconnect and reconnect to them, and run multiple commands in the same PSSession.</span></span> <span data-ttu-id="959c9-131">PSSession förblir tillgänglig tills du tar bort den eller tids gränsen uppnåddes.</span><span class="sxs-lookup"><span data-stu-id="959c9-131">The PSSession remains available until you delete it or it times out.</span></span>

<span data-ttu-id="959c9-132">Normalt skapar du en PSSession för att köra en serie relaterade kommandon på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="959c9-132">Typically, you create a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="959c9-133">När du skapar en PSSession på en fjärrdator upprättar PowerShell en permanent anslutning till fjärrdatorn för att stödja sessionen.</span><span class="sxs-lookup"><span data-stu-id="959c9-133">When you create a PSSession on a remote computer, PowerShell establishes a persistent connection to the remote computer to support the session.</span></span>

<span data-ttu-id="959c9-134">Om du använder parametern **computername** för `Invoke-Command` `Enter-PSSession` cmdleten eller för att köra ett fjärrkommando, eller om du vill starta en interaktiv session, skapar PowerShell en tillfällig session på fjärrdatorn och stänger sessionen så snart kommandot är slutfört eller så snart den interaktiva sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="959c9-134">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlet to run a remote command or to start an interactive session, PowerShell creates a temporary session on the remote computer and closes the session as soon as the command is complete or as soon as the interactive session ends.</span></span> <span data-ttu-id="959c9-135">Du kan inte kontrol lera dessa tillfälliga sessioner och du kan inte använda dem för mer än ett enda kommando eller en enkel interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="959c9-135">You cannot control these temporary sessions, and you cannot use them for more than a single command or a single interactive session.</span></span>

<span data-ttu-id="959c9-136">I PowerShell är den aktuella sessionen den session som du arbetar i.</span><span class="sxs-lookup"><span data-stu-id="959c9-136">In PowerShell, the "current session" is the session that you are working in.</span></span> <span data-ttu-id="959c9-137">Den aktuella sessionen kan referera till en session, inklusive en tillfällig session eller en PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-137">The "current session" can refer to any session, including a temporary session or a PSSession.</span></span>

## <a name="why-use-a-pssession"></a><span data-ttu-id="959c9-138">Varför ska jag använda en PSSession?</span><span class="sxs-lookup"><span data-stu-id="959c9-138">Why Use a PSSession?</span></span>

<span data-ttu-id="959c9-139">Använd en PSSession när du behöver en permanent anslutning till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="959c9-139">Use a PSSession when you need a persistent connection to a remote computer.</span></span>
<span data-ttu-id="959c9-140">Med en PSSession kan du köra en serie kommandon som delar data, till exempel värdet för variabler, innehållet i en funktion eller definitionen av ett alias.</span><span class="sxs-lookup"><span data-stu-id="959c9-140">With a PSSession, you can run a series of commands that share data, such as the value of variables, the contents of a function, or the definition of an alias.</span></span>

<span data-ttu-id="959c9-141">Du kan köra fjärrkommandon utan att skapa en PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-141">You can run remote commands without creating a PSSession.</span></span> <span data-ttu-id="959c9-142">Använd parametern **computername** för fjärraktiverade cmdlet: ar för att köra ett enskilt kommando eller en serie orelaterade kommandon på en eller flera datorer.</span><span class="sxs-lookup"><span data-stu-id="959c9-142">Use the **ComputerName** parameter of remote-enabled cmdlets to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="959c9-143">När du använder parametern **computername** för `Invoke-Command` eller `Enter-PSSession` , upprättar PowerShell en tillfällig anslutning till fjärrdatorn och stänger sedan anslutningen så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="959c9-143">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection to the remote computer and then closes the connection as soon as the command is complete.</span></span> <span data-ttu-id="959c9-144">Alla data element som du skapar försvinner när anslutningen stängs.</span><span class="sxs-lookup"><span data-stu-id="959c9-144">Any data elements that you create are lost when the connection is closed.</span></span>

<span data-ttu-id="959c9-145">Andra cmdletar som har en **computername** -parameter, till exempel `Get-Eventlog` och `Get-WmiObject` , använder olika fjärr kommunikations tekniker för att samla in data.</span><span class="sxs-lookup"><span data-stu-id="959c9-145">Other cmdlets that have a **ComputerName** parameter, such as `Get-Eventlog` and `Get-WmiObject`, use different remoting technologies to gather data.</span></span> <span data-ttu-id="959c9-146">Ingen skapar en permanent anslutning som en PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-146">None create a persistent connection like a PSSession.</span></span>

## <a name="how-to-create-a-pssession"></a><span data-ttu-id="959c9-147">Så här skapar du en PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-147">How to Create a PSSession</span></span>

<span data-ttu-id="959c9-148">Använd cmdleten för att skapa en PSSession `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="959c9-148">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="959c9-149">Om du vill skapa PSSession på en fjärrdator använder du parametern **computername** för `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="959c9-149">To create the PSSession on a remote computer, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="959c9-150">Följande kommando skapar till exempel en ny PSSession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="959c9-150">For example, the following command creates a new PSSession on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

<span data-ttu-id="959c9-151">När du skickar kommandot `New-PSSession` skapar PSSession och returnerar ett objekt som representerar PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-151">When you submit the command, `New-PSSession` creates the PSSession and returns an object that represents the PSSession.</span></span> <span data-ttu-id="959c9-152">Du kan spara objektet i en variabel när du skapar PSSession, eller så kan du använda ett `Get-PSSession` kommando för att hämta PSSession vid ett senare tillfälle.</span><span class="sxs-lookup"><span data-stu-id="959c9-152">You can save the object in a variable when you create the PSSession, or you can use a `Get-PSSession` command to get the PSSession at a later time.</span></span>

<span data-ttu-id="959c9-153">Följande kommando skapar till exempel en ny PSSession på Server01-datorn och sparar det resulterande objektet i variabeln $ps.</span><span class="sxs-lookup"><span data-stu-id="959c9-153">For example, the following command creates a new PSSession on the Server01 computer and saves the resulting object in the $ps variable.</span></span>

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a><span data-ttu-id="959c9-154">Så här skapar du PSSessions på flera datorer</span><span class="sxs-lookup"><span data-stu-id="959c9-154">How to Create PSSessions on Multiple Computers</span></span>

<span data-ttu-id="959c9-155">Om du vill skapa PSSessions på flera datorer använder du parametern **computername** för `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="959c9-155">To create PSSessions on multiple computers, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="959c9-156">Ange namnen på fjärrdatorerna i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="959c9-156">Type the names of the remote computers in a comma-separated list.</span></span>

<span data-ttu-id="959c9-157">Om du till exempel vill skapa PSSessions på Server01-, Server02-och Server03-datorerna skriver du:</span><span class="sxs-lookup"><span data-stu-id="959c9-157">For example, to create PSSessions on the Server01, Server02, and Server03 computers, type:</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="959c9-158">`New-PSSession` skapar en PSSession på varje fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="959c9-158">`New-PSSession` creates one PSSession on each of the remote computers.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="959c9-159">Så här hämtar du PSSessions</span><span class="sxs-lookup"><span data-stu-id="959c9-159">How to Get PSSessions</span></span>

<span data-ttu-id="959c9-160">Om du vill hämta PSSessions som har skapats i den aktuella sessionen använder du `Get-PSSession` cmdleten utan parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="959c9-160">To get the PSSessions that were created in your current session, use the `Get-PSSession` cmdlet without the **ComputerName** parameter.</span></span> <span data-ttu-id="959c9-161">`Get-PSSession` returnerar samma typ av objekt som `New-PSSession` returneras.</span><span class="sxs-lookup"><span data-stu-id="959c9-161">`Get-PSSession` returns the same type of object that `New-PSSession` returns.</span></span>

<span data-ttu-id="959c9-162">Följande kommando hämtar alla PSSessions som skapades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="959c9-162">The following command gets all the PSSessions that were created in the current session.</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="959c9-163">Standard visningen av PSSessions visar deras ID och standard visnings namn.</span><span class="sxs-lookup"><span data-stu-id="959c9-163">The default display of the PSSessions shows their ID and a default display name.</span></span> <span data-ttu-id="959c9-164">Du kan tilldela ett alternativt visnings namn när du skapar sessionen.</span><span class="sxs-lookup"><span data-stu-id="959c9-164">You can assign an alternate display name when you create the session.</span></span>

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

<span data-ttu-id="959c9-165">Du kan också spara PSSessions i en variabel.</span><span class="sxs-lookup"><span data-stu-id="959c9-165">You can also save the PSSessions in a variable.</span></span> <span data-ttu-id="959c9-166">Följande kommando hämtar PSSessions och sparar dem i \$ ps123-variabeln.</span><span class="sxs-lookup"><span data-stu-id="959c9-166">The following command gets the PSSessions and saves them in the \$ps123 variable.</span></span>

```powershell
$ps123 = Get-PSSession
```

<span data-ttu-id="959c9-167">När du använder PSSession-cmdlet: arna kan du referera till en PSSession med hjälp av dess ID, efter dess namn eller med dess instans-ID (GUID).</span><span class="sxs-lookup"><span data-stu-id="959c9-167">When using the PSSession cmdlets, you can refer to a PSSession by its ID, by its name, or by its instance ID (a GUID).</span></span> <span data-ttu-id="959c9-168">Följande kommando hämtar ett PSSession efter dess ID och sparar det i ps01- \$ variabeln.</span><span class="sxs-lookup"><span data-stu-id="959c9-168">The following command gets a PSSession by its ID and saves it in the \$ps01 variable.</span></span>

```powershell
$ps01 = Get-PSSession -Id 1
```

<span data-ttu-id="959c9-169">Från och med Windows PowerShell 3,0 underhålls PSSessions på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="959c9-169">Beginning in Windows PowerShell 3.0, PSSessions are maintained on the remote computer.</span></span> <span data-ttu-id="959c9-170">Om du vill hämta PSSessions som du har skapat på vissa fjärrdatorer använder du parametern **computername** för `Get-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="959c9-170">To get PSSessions that you created on particular remote computers, use the **ComputerName** parameter of the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="959c9-171">Följande kommando hämtar PSSessions som du skapade på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="959c9-171">The following command gets the PSSessions that you created on the Server01 remote computer.</span></span> <span data-ttu-id="959c9-172">Detta inkluderar PSSessions som skapats i den aktuella sessionen och i andra sessioner på den lokala datorn eller andra datorer.</span><span class="sxs-lookup"><span data-stu-id="959c9-172">This includes PSSessions created in the current session and in other sessions on the local computer or other computers.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

<span data-ttu-id="959c9-173">I Windows PowerShell 2,0 `Get-PSSession` hämtar endast de PSSessions som skapades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="959c9-173">In Windows PowerShell 2.0, `Get-PSSession` gets only the PSSessions that were created in the current session.</span></span> <span data-ttu-id="959c9-174">Den hämtar inte PSSessions som har skapats i andra sessioner eller på andra datorer, även om sessionerna är anslutna till och kör kommandon på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="959c9-174">It does not get PSSessions that were created in other sessions or on other computers, even if the sessions are connected to and are running commands on the local computer.</span></span>

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="959c9-175">Köra kommandon i en PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-175">How to Run Commands in a PSSession</span></span>

<span data-ttu-id="959c9-176">Använd cmdleten om du vill köra ett kommando i en eller flera PSSessions `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="959c9-176">To run a command in one or more PSSessions, use the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="959c9-177">Använd parametern session för att ange PSSessions och parametern **script block** för att ange kommandot.</span><span class="sxs-lookup"><span data-stu-id="959c9-177">Use the Session parameter to specify the PSSessions and the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="959c9-178">Om du till exempel vill köra ett `Get-ChildItem` kommando ("dir") i vart och ett av de tre PSSessions som sparas i variabeln $ps 123, skriver du:</span><span class="sxs-lookup"><span data-stu-id="959c9-178">For example, to run a `Get-ChildItem` ("dir") command in each of the three PSSessions saved in the $ps123 variable, type:</span></span>

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a><span data-ttu-id="959c9-179">Ta bort PSSessions</span><span class="sxs-lookup"><span data-stu-id="959c9-179">How to Delete PSSessions</span></span>

<span data-ttu-id="959c9-180">När du är färdig med PSSession använder du `Remove-PSSession` cmdleten för att ta bort PSSession och för att frigöra de resurser som används.</span><span class="sxs-lookup"><span data-stu-id="959c9-180">When you are finished with the PSSession, use the `Remove-PSSession` cmdlet to delete the PSSession and to release the resources that it was using.</span></span>

```powershell
Remove-PSSession -Session $ps
```

<span data-ttu-id="959c9-181">eller</span><span class="sxs-lookup"><span data-stu-id="959c9-181">or</span></span>

```powershell
Remove-PSSession -Id 1
```

<span data-ttu-id="959c9-182">Om du vill ta bort en PSSession från en fjärrdator använder du parametern **computername** för `Remove-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="959c9-182">To remove a PSSession from a remote computer, use the **ComputerName** parameter of the `Remove-PSSession` cmdlet.</span></span>

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

<span data-ttu-id="959c9-183">Om du inte tar bort PSSession är PSSession fortfarande tillgängligt för användning tills tids gränsen uppnåddes.</span><span class="sxs-lookup"><span data-stu-id="959c9-183">If you do not delete the PSSession, the PSSession remains available for use until it times out.</span></span>

<span data-ttu-id="959c9-184">Du kan också använda **idleTimeout** -parametern för `New-PSSessionOption` cmdlet: en för att ange en förfallo tid för en inaktiv PSSession.</span><span class="sxs-lookup"><span data-stu-id="959c9-184">You can also use the **IdleTimeout** parameter of the `New-PSSessionOption` cmdlet to set an expiration time for an idle PSSession.</span></span> <span data-ttu-id="959c9-185">Mer information finns i [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span><span class="sxs-lookup"><span data-stu-id="959c9-185">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="the-pssession-cmdlets"></a><span data-ttu-id="959c9-186">PSSession-cmdletar</span><span class="sxs-lookup"><span data-stu-id="959c9-186">The PSSession Cmdlets</span></span>

<span data-ttu-id="959c9-187">Om du vill ha en lista över PSSession-cmdletar skriver du:</span><span class="sxs-lookup"><span data-stu-id="959c9-187">For a list of PSSession cmdlets, type:</span></span>

```powershell
Get-Help *-PSSession
```

- <span data-ttu-id="959c9-188">Connect-PSSession: ansluter en PSSession till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="959c9-188">Connect-PSSession: Connects a PSSession to the current session</span></span>
- <span data-ttu-id="959c9-189">Koppla från-PSSession: kopplar från en PSSession från den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="959c9-189">Disconnect-PSSession: Disconnects a PSSession from the current session</span></span>
- <span data-ttu-id="959c9-190">Retur-PSSession: startar en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="959c9-190">Enter-PSSession: Starts an interactive session</span></span>
- <span data-ttu-id="959c9-191">Exit-PSSession: avslutar en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="959c9-191">Exit-PSSession: Ends an interactive session</span></span>
- <span data-ttu-id="959c9-192">Get-PSSession: hämtar PSSessions i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="959c9-192">Get-PSSession: Gets the PSSessions in the current session</span></span>
- <span data-ttu-id="959c9-193">New-PSSession: skapar en ny PSSession på en lokal eller fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="959c9-193">New-PSSession: Creates a new PSSession on a local or remote computer</span></span>
- <span data-ttu-id="959c9-194">Receive-PSSession: hämtar resultatet från kommandon som kördes i en frånkopplad session</span><span class="sxs-lookup"><span data-stu-id="959c9-194">Receive-PSSession: Gets the results of commands that ran in a disconnected session</span></span>
- <span data-ttu-id="959c9-195">Remove-PSSession: tar bort PSSessions i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="959c9-195">Remove-PSSession: Deletes the PSSessions in the current session</span></span>

## <a name="for-more-information"></a><span data-ttu-id="959c9-196">Mer information</span><span class="sxs-lookup"><span data-stu-id="959c9-196">For More Information</span></span>

<span data-ttu-id="959c9-197">Mer information om PSSessions finns i [about_PSSession_Details](about_PSSession_Details.md).</span><span class="sxs-lookup"><span data-stu-id="959c9-197">For more information about PSSessions, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="959c9-198">Se även</span><span class="sxs-lookup"><span data-stu-id="959c9-198">See Also</span></span>

[<span data-ttu-id="959c9-199">about_Remote</span><span class="sxs-lookup"><span data-stu-id="959c9-199">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="959c9-200">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="959c9-200">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="959c9-201">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="959c9-201">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="959c9-202">Anslut – PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-202">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="959c9-203">Koppla från-PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-203">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="959c9-204">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-204">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="959c9-205">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-205">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="959c9-206">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-206">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="959c9-207">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="959c9-207">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="959c9-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="959c9-209">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="959c9-209">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)

