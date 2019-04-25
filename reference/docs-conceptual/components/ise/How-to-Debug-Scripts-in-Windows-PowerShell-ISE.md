---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Felsök skript i Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086875"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a><span data-ttu-id="57b89-103">Felsök skript i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="57b89-103">How to Debug Scripts in Windows PowerShell ISE</span></span>

<span data-ttu-id="57b89-104">Den här artikeln beskriver hur du felsöker skript på en lokal dator med Windows PowerShell Integrated Scripting Environment (ISE) visual felsökningsfunktioner.</span><span class="sxs-lookup"><span data-stu-id="57b89-104">This article describes how to debug scripts on a local computer by using the Windows PowerShell Integrated Scripting Environment (ISE) visual debugging features.</span></span>

## <a name="how-to-manage-breakpoints"></a><span data-ttu-id="57b89-105">Så här hanterar du brytpunkter</span><span class="sxs-lookup"><span data-stu-id="57b89-105">How to manage breakpoints</span></span>

<span data-ttu-id="57b89-106">En brytpunkt är en avsedda platsen där du vill att pausa så att du kan kontrollera det aktuella tillståndet för variablerna och miljön där skriptet körs i ett skript.</span><span class="sxs-lookup"><span data-stu-id="57b89-106">A breakpoint is a designated spot in a script where you would like operation to pause so that you can examine the current state of the variables and the environment in which your script is running.</span></span> <span data-ttu-id="57b89-107">När skriptet har pausats av en brytpunkt, kan du köra kommandon i konsolfönstret för att undersöka tillståndet för ditt skript.</span><span class="sxs-lookup"><span data-stu-id="57b89-107">Once your script is paused by a breakpoint, you can run commands in the Console Pane to examine the state of your script.</span></span>  <span data-ttu-id="57b89-108">Du kan mata ut variabler eller köra andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="57b89-108">You can output variables or run other commands.</span></span> <span data-ttu-id="57b89-109">Du kan även ändra värdet för alla variabler som är synliga för kontexten för skriptet som körs för tillfället.</span><span class="sxs-lookup"><span data-stu-id="57b89-109">You can even modify the value of any variables that are visible to the context of the currently running script.</span></span> <span data-ttu-id="57b89-110">När du har undersökt vad du vill se, kan du återuppta användningen av skript.</span><span class="sxs-lookup"><span data-stu-id="57b89-110">After you have examined what you want to see, you can resume operation of the script.</span></span>

<span data-ttu-id="57b89-111">Du kan ange tre typer av brytpunkter i Windows PowerShell-felsökningsmiljö:</span><span class="sxs-lookup"><span data-stu-id="57b89-111">You can set three types of breakpoints in the Windows PowerShell debugging environment:</span></span>

1. <span data-ttu-id="57b89-112">**Rad brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-112">**Line breakpoint**.</span></span> <span data-ttu-id="57b89-113">Skriptet pausar när den angivna raden har nåtts under drift av skriptet</span><span class="sxs-lookup"><span data-stu-id="57b89-113">The script pauses when the designated line is reached during the operation of the script</span></span>

2. <span data-ttu-id="57b89-114">**Variabeln brytpunkt.**</span><span class="sxs-lookup"><span data-stu-id="57b89-114">**Variable breakpoint.**</span></span> <span data-ttu-id="57b89-115">Skriptet pausar när avsedda variabelns värde ändras.</span><span class="sxs-lookup"><span data-stu-id="57b89-115">The script pauses whenever the designated variable's value changes.</span></span>

3. <span data-ttu-id="57b89-116">**Kommandot brytpunkt.**</span><span class="sxs-lookup"><span data-stu-id="57b89-116">**Command breakpoint.**</span></span> <span data-ttu-id="57b89-117">Skriptet pausar när det angivna kommandot är håller på att köras under drift av skriptet.</span><span class="sxs-lookup"><span data-stu-id="57b89-117">The script pauses whenever the designated command is about to be run during the operation of the script.</span></span> <span data-ttu-id="57b89-118">Den kan innehålla parametrar för att filtrera ytterligare brytpunkt för den åtgärd som du vill.</span><span class="sxs-lookup"><span data-stu-id="57b89-118">It can include parameters to further filter the breakpoint to only the operation you want.</span></span> <span data-ttu-id="57b89-119">Kommandot kan också vara en funktion som du skapade.</span><span class="sxs-lookup"><span data-stu-id="57b89-119">The command can also be a function you created.</span></span>

<span data-ttu-id="57b89-120">Dessa i Windows PowerShell ISE felsökningsmiljö, kan endast rad brytpunkter anges med hjälp av menyn eller kortkommandon.</span><span class="sxs-lookup"><span data-stu-id="57b89-120">Of these, in the Windows PowerShell ISE debugging environment, only line breakpoints can be set by using the menu or the keyboard shortcuts.</span></span> <span data-ttu-id="57b89-121">De andra två typerna av brytpunkter kan ställas in, men de har angetts från konsolfönstret genom att använda den [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-121">The other two types of breakpoints can be set, but they are set from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet.</span></span> <span data-ttu-id="57b89-122">Det här avsnittet beskrivs hur du kan utföra fjärrfelsökning uppgifter i Windows PowerShell ISE genom att använda menyerna där det är tillgängligt och utföra fler kommandon från konsolfönstret med hjälp av skript.</span><span class="sxs-lookup"><span data-stu-id="57b89-122">This section describes how you can perform debugging tasks in Windows PowerShell ISE by using the menus where available, and perform a wider range of commands from the Console Pane by using scripting.</span></span>

### <a name="to-set-a-breakpoint"></a><span data-ttu-id="57b89-123">Ange en brytpunkt</span><span class="sxs-lookup"><span data-stu-id="57b89-123">To set a breakpoint</span></span>

<span data-ttu-id="57b89-124">Ställas kan in en brytpunkt i ett skript efter det att den har sparats.</span><span class="sxs-lookup"><span data-stu-id="57b89-124">A breakpoint can be set in a script only after it has been saved.</span></span> <span data-ttu-id="57b89-125">Högerklicka på den rad där du vill konfigurera en brytpunkt på rad och klicka sedan på **/Radera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-125">Right-click the line where you want to set a line breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="57b89-126">Alternativt klickar du på den rad där du vill ange en brytpunkt på rad, och tryck på **F9** eller på den **felsöka** -menyn klickar du på **/Radera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-126">Or, click the line where you want to set a line breakpoint, and press **F9** or, on the **Debug** menu, click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="57b89-127">Följande skript är ett exempel på hur du kan ange en variabel brytpunkt från konsolfönstret genom att använda den [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-127">The following script is an example of how you can set a variable breakpoint from the Console Pane by using the [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.</span></span>

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a><span data-ttu-id="57b89-128">Lista över alla brytpunkter</span><span class="sxs-lookup"><span data-stu-id="57b89-128">List all breakpoints</span></span>

<span data-ttu-id="57b89-129">Visar alla brytpunkter i den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="57b89-129">Displays all breakpoints in the current Windows PowerShell session.</span></span>

<span data-ttu-id="57b89-130">På den **felsöka** -menyn klickar du på **lista brytpunkter**.</span><span class="sxs-lookup"><span data-stu-id="57b89-130">On the **Debug** menu, click **List Breakpoints**.</span></span> <span data-ttu-id="57b89-131">Följande skript är ett exempel på hur du kan lista alla brytpunkter från konsolfönstret genom att använda den [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-131">The following script is an example of how you can list all breakpoints from the Console Pane by using the [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.</span></span>

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a><span data-ttu-id="57b89-132">Ta bort en brytpunkt</span><span class="sxs-lookup"><span data-stu-id="57b89-132">Remove a breakpoint</span></span>

<span data-ttu-id="57b89-133">Ta bort en brytpunkt tas den bort.</span><span class="sxs-lookup"><span data-stu-id="57b89-133">Removing a breakpoint deletes it.</span></span>

<span data-ttu-id="57b89-134">Om du tror att du kanske vill använda det igen senare bör du överväga att [inaktivera en brytpunkt](#disable-a-breakpoint) den i stället.</span><span class="sxs-lookup"><span data-stu-id="57b89-134">If you think you might want to use it again later, consider [Disable a Breakpoint](#disable-a-breakpoint) it instead.</span></span>
<span data-ttu-id="57b89-135">Högerklicka på den rad där du vill ta bort en brytpunkt och klicka sedan på **/Radera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-135">Right-click the line where you want to remove a breakpoint, and then click **Toggle Breakpoint**.</span></span>
<span data-ttu-id="57b89-136">Alternativt klickar du på den rad där du vill ta bort en brytpunkt på den **felsöka** -menyn klickar du på **/Radera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-136">Or, click the line where you want to remove a breakpoint, and on the **Debug** menu, click **Toggle Breakpoint**.</span></span>
<span data-ttu-id="57b89-137">Följande skript är ett exempel på hur du tar bort en brytpunkt med ett specifikt ID från konsolfönstret genom att använda den [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-137">The following script is an example of how to remove a breakpoint with a specified ID from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a><span data-ttu-id="57b89-138">Ta bort alla brytpunkter</span><span class="sxs-lookup"><span data-stu-id="57b89-138">Remove All Breakpoints</span></span>

<span data-ttu-id="57b89-139">Ta bort alla brytpunkter som definierats i den aktuella sessionen på den **felsöka** -menyn klickar du på **ta bort alla brytpunkter**.</span><span class="sxs-lookup"><span data-stu-id="57b89-139">To remove all breakpoints defined in the current session, on the **Debug** menu, click **Remove All Breakpoints**.</span></span>

<span data-ttu-id="57b89-140">Följande skript är ett exempel på hur du tar bort alla brytpunkter från konsolfönstret genom att använda den [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-140">The following script is an example of how to remove all breakpoints from the Console Pane by using the [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.</span></span>

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a><span data-ttu-id="57b89-141">Inaktivera en brytpunkt</span><span class="sxs-lookup"><span data-stu-id="57b89-141">Disable a Breakpoint</span></span>

<span data-ttu-id="57b89-142">Inaktivera en brytpunkt tar inte bort. Det inaktiverar den förrän den har aktiverats.</span><span class="sxs-lookup"><span data-stu-id="57b89-142">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="57b89-143">Om du vill inaktivera en specifik rad brytpunkt, högerklickar du på den rad där du vill inaktivera en brytpunkt och klicka sedan på **inaktivera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-143">To disable a specific line breakpoint, right-click the line where you want to disable a breakpoint, and then click **Disable Breakpoint**.</span></span> <span data-ttu-id="57b89-144">Alternativt klickar du på den rad där du vill inaktivera en brytpunkt, och tryck på **F9** eller på den **felsöka** -menyn klickar du på **inaktivera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-144">Or, click the line where you want to disable a breakpoint, and press **F9** or, on the **Debug** menu, click **Disable Breakpoint**.</span></span> <span data-ttu-id="57b89-145">Följande skript är ett exempel på hur du tar bort en brytpunkt med ett specifikt ID från konsolfönstret genom att använda den [inaktivera PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-145">The following script is an example of how you can remove a breakpoint with a specified ID from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a><span data-ttu-id="57b89-146">Inaktivera alla brytpunkter</span><span class="sxs-lookup"><span data-stu-id="57b89-146">Disable All Breakpoints</span></span>

<span data-ttu-id="57b89-147">Inaktivera en brytpunkt tar inte bort. Det inaktiverar den förrän den har aktiverats.</span><span class="sxs-lookup"><span data-stu-id="57b89-147">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span>  <span data-ttu-id="57b89-148">Att inaktivera alla brytpunkter i den aktuella sessionen på den **felsöka** -menyn klickar du på **inaktivera alla brytpunkter**.</span><span class="sxs-lookup"><span data-stu-id="57b89-148">To disable all breakpoints in the current session, on the **Debug** menu, click **Disable all Breakpoints**.</span></span> <span data-ttu-id="57b89-149">Följande skript är ett exempel på hur du kan inaktivera alla brytpunkter från konsolfönstret genom att använda den [inaktivera PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-149">The following script is an example of how you can disable all breakpoints from the Console Pane by using the [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.</span></span>

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a><span data-ttu-id="57b89-150">Aktivera en brytpunkt</span><span class="sxs-lookup"><span data-stu-id="57b89-150">Enable a Breakpoint</span></span>

<span data-ttu-id="57b89-151">Om du vill aktivera en specifik brytpunkt, högerklickar du på den rad där du vill aktivera en brytpunkt och klicka sedan på **aktivera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-151">To enable a specific breakpoint, right-click the line where you want to enable a breakpoint, and then click **Enable Breakpoint**.</span></span> <span data-ttu-id="57b89-152">Alternativt klickar du på den rad där du vill aktivera en brytpunkt och tryck sedan på **F9** eller på den **felsöka** -menyn klickar du på **aktivera brytpunkt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-152">Or, click the line where you want to enable a breakpoint, and then press **F9** or, on the **Debug** menu, click **Enable Breakpoint**.</span></span> <span data-ttu-id="57b89-153">Följande skript är ett exempel på hur du kan aktivera specifika brytpunkter från konsolfönstret genom att använda den [aktivera PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-153">The following script is an example of how you can enable specific breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a><span data-ttu-id="57b89-154">Aktivera alla brytpunkter</span><span class="sxs-lookup"><span data-stu-id="57b89-154">Enable All Breakpoints</span></span>

<span data-ttu-id="57b89-155">Aktivera alla brytpunkter som definierats i den aktuella sessionen på den **felsöka** -menyn klickar du på **aktivera alla brytpunkter**.</span><span class="sxs-lookup"><span data-stu-id="57b89-155">To enable all breakpoints defined in the current session, on the **Debug** menu, click **Enable all Breakpoints**.</span></span> <span data-ttu-id="57b89-156">Följande skript är ett exempel på hur du kan aktivera alla brytpunkter från konsolfönstret genom att använda den [aktivera PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="57b89-156">The following script is an example of how you can enable all breakpoints from the Console Pane by using the [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.</span></span>

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a><span data-ttu-id="57b89-157">Så här hanterar du en felsökningssession</span><span class="sxs-lookup"><span data-stu-id="57b89-157">How to manage a debugging session</span></span>

<span data-ttu-id="57b89-158">Innan du startar felsökning, måste du ange en eller flera brytpunkter.</span><span class="sxs-lookup"><span data-stu-id="57b89-158">Before you start debugging, you must set one or more breakpoints.</span></span> <span data-ttu-id="57b89-159">Du kan inte ange en brytpunkt, såvida inte det skript som du vill felsöka sparas.</span><span class="sxs-lookup"><span data-stu-id="57b89-159">You cannot set a breakpoint unless the script that you want to debug is saved.</span></span> <span data-ttu-id="57b89-160">Läs anvisningarna för hur du ställer in en brytpunkt [hantera brytpunkter](#how-to-manage-breakpoints) eller [Set-PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint).</span><span class="sxs-lookup"><span data-stu-id="57b89-160">For directions on of how to set a breakpoint, see [How to manage breakpoints](#how-to-manage-breakpoints) or [Set-PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint).</span></span> <span data-ttu-id="57b89-161">När du startar felsökning, kan du inte redigera ett skript tills du stoppa felsökningen.</span><span class="sxs-lookup"><span data-stu-id="57b89-161">After you start debugging, you cannot edit a script until you stop debugging.</span></span> <span data-ttu-id="57b89-162">Ett skript som har en eller flera brytpunkter som ställs in sparas automatiskt innan den körs.</span><span class="sxs-lookup"><span data-stu-id="57b89-162">A script that has one or more breakpoints set is automatically saved before it is run.</span></span>

### <a name="to-start-debugging"></a><span data-ttu-id="57b89-163">Att starta felsökning</span><span class="sxs-lookup"><span data-stu-id="57b89-163">To start debugging</span></span>

<span data-ttu-id="57b89-164">Tryck på **F5** i verktygsfältet klickar du på den **kör skript** ikonen eller på den **felsöka** menyn klickar du på **kör/Fortsätt**.</span><span class="sxs-lookup"><span data-stu-id="57b89-164">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu click **Run/Continue**.</span></span> <span data-ttu-id="57b89-165">Skriptet körs tills den första brytpunkten påträffas.</span><span class="sxs-lookup"><span data-stu-id="57b89-165">The script runs until it encounters the first breakpoint.</span></span> <span data-ttu-id="57b89-166">Den pausar igen där och visar den raden där det pausades.</span><span class="sxs-lookup"><span data-stu-id="57b89-166">It pauses operation there and highlights the line on which it paused.</span></span>

### <a name="to-continue-debugging"></a><span data-ttu-id="57b89-167">Att fortsätta felsökningen</span><span class="sxs-lookup"><span data-stu-id="57b89-167">To continue debugging</span></span>

<span data-ttu-id="57b89-168">Tryck på **F5** i verktygsfältet klickar du på den **kör skript** ikonen eller på den **felsöka** -menyn klickar du på **kör/Fortsätt** skriva i konsolfönstret **C** och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-168">Press **F5** or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu, click **Run/Continue** or, in the Console Pane, type **C** and then press **ENTER**.</span></span> <span data-ttu-id="57b89-169">Detta leder till att skriptet ska fortsätta att köra till nästa brytpunkt eller i slutet av skriptet om inga ytterligare brytpunkter uppstår.</span><span class="sxs-lookup"><span data-stu-id="57b89-169">This causes the script to continue running to the next breakpoint or to the end of the script if no further breakpoints are encountered.</span></span>

### <a name="to-view-the-call-stack"></a><span data-ttu-id="57b89-170">Visa anropsstacken</span><span class="sxs-lookup"><span data-stu-id="57b89-170">To view the call stack</span></span>

<span data-ttu-id="57b89-171">Anropsstacken visar den aktuella körningsplats i skriptet.</span><span class="sxs-lookup"><span data-stu-id="57b89-171">The call stack displays the current run location in the script.</span></span> <span data-ttu-id="57b89-172">Om skriptet körs i en funktion som anropades av en annan funktion, sedan som representeras i visningen av ytterligare rader i utdata.</span><span class="sxs-lookup"><span data-stu-id="57b89-172">If the script is running in a function that was called by a different function, then that is represented in the display by additional rows in the output.</span></span> <span data-ttu-id="57b89-173">Den nedersta raden visar det ursprungliga skriptet och raden i det som en funktion anropades.</span><span class="sxs-lookup"><span data-stu-id="57b89-173">The bottom-most row displays the original script and the line in it in which a function was called.</span></span> <span data-ttu-id="57b89-174">Nästa rad anger funktionen och raden i det som en annan funktion kanske har anropats.</span><span class="sxs-lookup"><span data-stu-id="57b89-174">The next line up shows that function and the line in it in which another function might have been called.</span></span>  <span data-ttu-id="57b89-175">Den översta raden visar aktuell kontext för den aktuella raden brytpunkten har angetts.</span><span class="sxs-lookup"><span data-stu-id="57b89-175">The top-most row shows the current context of the current line on which the breakpoint is set.</span></span>

<span data-ttu-id="57b89-176">När pausad, om du vill se aktuella anropsstacken, trycker du på **CTRL + SKIFT + D** eller på den **felsöka** -menyn klickar du på **visa anropsstack** skriva i konsolfönstret **K**  och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-176">While paused, to see the current call stack, press **CTRL+SHIFT+D** or, on the **Debug** menu, click **Display Call Stack** or, in the Console Pane, type **K** and then press **ENTER**.</span></span>

### <a name="to-stop-debugging"></a><span data-ttu-id="57b89-177">Att stoppa felsökningen</span><span class="sxs-lookup"><span data-stu-id="57b89-177">To stop debugging</span></span>

<span data-ttu-id="57b89-178">Tryck på **SKIFT F5** eller på den **felsöka** -menyn klickar du på **stoppa felsökare**, skriva i konsolfönstret **Q** och tryck sedan på  **Ange**.</span><span class="sxs-lookup"><span data-stu-id="57b89-178">Press **SHIFT-F5** or, on the **Debug** menu, click **Stop Debugger**, or, in the Console Pane, type **Q** and then press **ENTER**.</span></span>

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a><span data-ttu-id="57b89-179">Stega över, Stega in och steg när du felsöker</span><span class="sxs-lookup"><span data-stu-id="57b89-179">How to step over, step into, and step out while debugging</span></span>

<span data-ttu-id="57b89-180">Stega dig är processen att köra en instruktion i taget.</span><span class="sxs-lookup"><span data-stu-id="57b89-180">Stepping is the process of running one statement at a time.</span></span> <span data-ttu-id="57b89-181">Du kan stoppa på en rad med kod och granska värdena för variabler och tillståndet för systemet.</span><span class="sxs-lookup"><span data-stu-id="57b89-181">You can stop on a line of code, and examine the values of variables and the state of the system.</span></span> <span data-ttu-id="57b89-182">I följande tabell beskrivs vanliga felsökning uppgifter, till exempel Stega dig över, gå till och gå.</span><span class="sxs-lookup"><span data-stu-id="57b89-182">The following table describes common debugging tasks such as stepping over, stepping into, and stepping out.</span></span>

| <span data-ttu-id="57b89-183">Felsökning av uppgiften</span><span class="sxs-lookup"><span data-stu-id="57b89-183">Debugging Task</span></span> | <span data-ttu-id="57b89-184">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="57b89-184">Description</span></span> | <span data-ttu-id="57b89-185">Hur du utför i PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="57b89-185">How to accomplish it in PowerShell ISE</span></span> |
| --- | --- | --- |
| <span data-ttu-id="57b89-186">**Stega in**</span><span class="sxs-lookup"><span data-stu-id="57b89-186">**Step Into**</span></span> | <span data-ttu-id="57b89-187">Kör den aktuella instruktionen och sedan stoppas vid nästa instruktionen.</span><span class="sxs-lookup"><span data-stu-id="57b89-187">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="57b89-188">Om den aktuella instruktionen är en funktion eller skriptanrop sedan felsökare stegen i den funktion eller ett skript, annars avbryts vid nästa fel.</span><span class="sxs-lookup"><span data-stu-id="57b89-188">If the current statement is a function or script call, then the debugger steps into that function or script, otherwise it stops at the next statement.</span></span> | <span data-ttu-id="57b89-189">Tryck på **F11** eller på den **felsöka** -menyn klickar du på **Stega**, eller i konsolfönstret skriver **S** och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-189">Press **F11** or, on the **Debug** menu, click **Step Into**, or in the Console Pane, type **S** and press **ENTER**.</span></span> |
| <span data-ttu-id="57b89-190">**Hoppa över**</span><span class="sxs-lookup"><span data-stu-id="57b89-190">**Step Over**</span></span> | <span data-ttu-id="57b89-191">Kör den aktuella instruktionen och sedan stoppas vid nästa instruktionen.</span><span class="sxs-lookup"><span data-stu-id="57b89-191">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="57b89-192">Om den aktuella instruktionen är en funktion eller skriptanrop sedan felsökningsprogrammet körs hela funktionen eller skript och stoppas vid nästa fel efter funktionsanropet.</span><span class="sxs-lookup"><span data-stu-id="57b89-192">If the current statement is a function or script call, then the debugger executes the whole function or script, and it stops at the next statement after the function call.</span></span> | <span data-ttu-id="57b89-193">Tryck på **F10** eller på den **felsöka** -menyn klickar du på **Stega**, eller i konsolfönstret skriver **V** och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-193">Press **F10** or, on the **Debug** menu, click **Step Over**, or in the Console Pane, type **V** and press **ENTER**.</span></span> |
| <span data-ttu-id="57b89-194">**Stega ut**</span><span class="sxs-lookup"><span data-stu-id="57b89-194">**Step Out**</span></span> | <span data-ttu-id="57b89-195">Steg utanför den aktuella funktionen och upp en nivå om funktionen är kapslade.</span><span class="sxs-lookup"><span data-stu-id="57b89-195">Steps out of the current function and up one level if the function is nested.</span></span> <span data-ttu-id="57b89-196">Om i brödtext, körs skriptet i slutet eller till nästa brytpunkt.</span><span class="sxs-lookup"><span data-stu-id="57b89-196">If in the main body, the script is executed to the end, or to the next breakpoint.</span></span> <span data-ttu-id="57b89-197">Överhoppade instruktionerna körs, men inte stegvis via.</span><span class="sxs-lookup"><span data-stu-id="57b89-197">The skipped statements are executed, but not stepped through.</span></span> | <span data-ttu-id="57b89-198">Tryck på **SKIFT + F11**, eller på den **felsöka** -menyn klickar du på **Stega ut**, eller i konsolfönstret skriver **O** och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-198">Press **SHIFT+F11**, or on the **Debug** menu, click **Step Out**, or in the Console Pane, type **O** and press **ENTER**.</span></span> |
| <span data-ttu-id="57b89-199">**Fortsätta**</span><span class="sxs-lookup"><span data-stu-id="57b89-199">**Continue**</span></span> | <span data-ttu-id="57b89-200">Fortsätter körningen till slutet eller till nästa brytpunkt.</span><span class="sxs-lookup"><span data-stu-id="57b89-200">Continues execution to the end, or to the next breakpoint.</span></span> <span data-ttu-id="57b89-201">Överhoppade funktions- och anrop är körs, men inte stegvis via.</span><span class="sxs-lookup"><span data-stu-id="57b89-201">The skipped functions and invocations are executed, but not stepped through.</span></span> | <span data-ttu-id="57b89-202">Tryck på **F5** eller på den **felsöka** -menyn klickar du på **kör/Fortsätt**, eller i konsolfönstret skriver **C** och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-202">Press **F5** or, on the **Debug** menu, click **Run/Continue**, or in the Console Pane, type **C** and press **ENTER**.</span></span> |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a><span data-ttu-id="57b89-203">Så här visar du värdena för variabler vid felsökning</span><span class="sxs-lookup"><span data-stu-id="57b89-203">How to display the values of variables while debugging</span></span>

<span data-ttu-id="57b89-204">Du kan visa de aktuella värdena för variabler i skriptet som du går igenom koden.</span><span class="sxs-lookup"><span data-stu-id="57b89-204">You can display the current values of variables in the script as you step through the code.</span></span>

### <a name="to-display-the-values-of-standard-variables"></a><span data-ttu-id="57b89-205">Visa värdena för variabler som standard</span><span class="sxs-lookup"><span data-stu-id="57b89-205">To display the values of standard variables</span></span>

<span data-ttu-id="57b89-206">Använd någon av följande metoder:</span><span class="sxs-lookup"><span data-stu-id="57b89-206">Use one of the following methods:</span></span>

- <span data-ttu-id="57b89-207">Hovra över variabeln för att visa dess värde som en knappbeskrivning i fönstret skript.</span><span class="sxs-lookup"><span data-stu-id="57b89-207">In the Script Pane, hover over the variable to display its value as a tool tip.</span></span>

- <span data-ttu-id="57b89-208">I konsolfönstret skriver variabelnamn och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="57b89-208">In the Console Pane, type the variable name and press **ENTER**.</span></span>

<span data-ttu-id="57b89-209">Alla fönster i ISE är alltid i samma definitionsområde.</span><span class="sxs-lookup"><span data-stu-id="57b89-209">All panes in ISE are always in the same scope.</span></span> <span data-ttu-id="57b89-210">När du felsöker ett skript, kör därför de kommandon som du skriver i konsolfönstret i skriptet omfång.</span><span class="sxs-lookup"><span data-stu-id="57b89-210">Therefore, while you are debugging a script, the commands that you type in the Console Pane run in script scope.</span></span> <span data-ttu-id="57b89-211">På så sätt kan du använda konsolfönstret för att hitta värdena för variabler och anropa funktioner som definieras endast i skriptet.</span><span class="sxs-lookup"><span data-stu-id="57b89-211">This allows you to use the Console Pane to find the values of variables and call functions that are defined only in the script.</span></span>

### <a name="to-display-the-values-of-automatic-variables"></a><span data-ttu-id="57b89-212">Visa värden över automatiska variabler</span><span class="sxs-lookup"><span data-stu-id="57b89-212">To display the values of automatic variables</span></span>

<span data-ttu-id="57b89-213">Du kan använda föregående metod för att visa värdet för nästan alla variabler när du felsöker ett skript.</span><span class="sxs-lookup"><span data-stu-id="57b89-213">You can use the preceding method to display the value of almost all variables while you are debugging a script.</span></span> <span data-ttu-id="57b89-214">Dessa metoder fungerar dock inte för följande automatiska variabler.</span><span class="sxs-lookup"><span data-stu-id="57b89-214">However, these methods do not work for the following automatic variables.</span></span>

- <span data-ttu-id="57b89-215">$_</span><span class="sxs-lookup"><span data-stu-id="57b89-215">$_</span></span>

- <span data-ttu-id="57b89-216">$Input</span><span class="sxs-lookup"><span data-stu-id="57b89-216">$Input</span></span>

- <span data-ttu-id="57b89-217">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="57b89-217">$MyInvocation</span></span>

- <span data-ttu-id="57b89-218">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="57b89-218">$PSBoundParameters</span></span>

- <span data-ttu-id="57b89-219">$Args</span><span class="sxs-lookup"><span data-stu-id="57b89-219">$Args</span></span>

<span data-ttu-id="57b89-220">Om du försöker visa värdet för någon av dessa variabler, får du värdet för variabeln för en intern pipeline felsökningsprogrammet, inte värdet används av variabeln i skriptet.</span><span class="sxs-lookup"><span data-stu-id="57b89-220">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span> <span data-ttu-id="57b89-221">Du kan komma runt detta för några variabler ($_, $Input, $MyInvocation, $PSBoundParameters och $Args) med hjälp av följande metod:</span><span class="sxs-lookup"><span data-stu-id="57b89-221">You can work around this for a few variables ($_, $Input, $MyInvocation, $PSBoundParameters, and $Args) by using the following method:</span></span>

1. <span data-ttu-id="57b89-222">Tilldela värdet för den automatiska variabeln till en ny variabel i skriptet.</span><span class="sxs-lookup"><span data-stu-id="57b89-222">In the script, assign the value of the automatic variable to a new variable.</span></span>

2. <span data-ttu-id="57b89-223">Visa värdet för variabeln, antingen genom att hovra över den nya variabeln i skriptfönstret eller genom att skriva ny variabel i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="57b89-223">Display the value of the new variable, either by hovering over the new variable in the Script Pane, or by typing the new variable in the Console Pane.</span></span>

<span data-ttu-id="57b89-224">Till exempel om du vill visa värdet för variabeln $MyInvocation i skriptet, tilldela värdet till en ny variabel, till exempel $scriptname, och sedan hovra över eller Skriv $scriptname variabeln för att visa dess värde.</span><span class="sxs-lookup"><span data-stu-id="57b89-224">For example, to display the value of the $MyInvocation variable, in the script, assign the value to a new variable, such as $scriptname, and then hover over or type the $scriptname variable to display its value.</span></span>

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a><span data-ttu-id="57b89-225">Se även</span><span class="sxs-lookup"><span data-stu-id="57b89-225">See Also</span></span>

- [<span data-ttu-id="57b89-226">Utforska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="57b89-226">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)