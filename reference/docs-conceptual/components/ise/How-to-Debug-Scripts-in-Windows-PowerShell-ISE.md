---
ms.date: 01/02/2020
keywords: PowerShell, cmdlet
title: Felsök skript i Windows PowerShell ISE
ms.openlocfilehash: 6fbe340cbff832b5d0e2a5515ef432cec574a3c1
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500946"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a><span data-ttu-id="05f70-103">Felsök skript i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="05f70-103">How to Debug Scripts in Windows PowerShell ISE</span></span>

<span data-ttu-id="05f70-104">Den här artikeln beskriver hur du felsöker skript på en lokal dator med hjälp av fel söknings funktionerna i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="05f70-104">This article describes how to debug scripts on a local computer by using the Windows PowerShell Integrated Scripting Environment (ISE) visual debugging features.</span></span>

## <a name="how-to-manage-breakpoints"></a><span data-ttu-id="05f70-105">Hantera Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="05f70-105">How to manage breakpoints</span></span>

<span data-ttu-id="05f70-106">En Bryt punkt är en utsedd punkt i ett skript där du vill att åtgärden ska pausas så att du kan undersöka det aktuella läget för variablerna och miljön där skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="05f70-106">A breakpoint is a designated spot in a script where you would like operation to pause so that you can examine the current state of the variables and the environment in which your script is running.</span></span>
<span data-ttu-id="05f70-107">När skriptet har pausats med en Bryt punkt kan du köra kommandon i konsol fönstret för att kontrol lera status för skriptet.</span><span class="sxs-lookup"><span data-stu-id="05f70-107">Once your script is paused by a breakpoint, you can run commands in the Console Pane to examine the state of your script.</span></span> <span data-ttu-id="05f70-108">Du kan mata ut variabler eller köra andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="05f70-108">You can output variables or run other commands.</span></span> <span data-ttu-id="05f70-109">Du kan till och med ändra värdet för alla variabler som är synliga för kontexten för det skript som körs för tillfället.</span><span class="sxs-lookup"><span data-stu-id="05f70-109">You can even modify the value of any variables that are visible to the context of the currently running script.</span></span> <span data-ttu-id="05f70-110">När du har undersökt vad du vill se kan du återuppta körningen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="05f70-110">After you have examined what you want to see, you can resume operation of the script.</span></span>

<span data-ttu-id="05f70-111">Du kan ange tre typer av Bryt punkter i fel söknings miljön i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="05f70-111">You can set three types of breakpoints in the Windows PowerShell debugging environment:</span></span>

1. <span data-ttu-id="05f70-112">**Rad Bryt punkt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-112">**Line breakpoint**.</span></span> <span data-ttu-id="05f70-113">Skriptet pausar när den angivna raden har nåtts vid körning av skriptet</span><span class="sxs-lookup"><span data-stu-id="05f70-113">The script pauses when the designated line is reached during the operation of the script</span></span>

1. <span data-ttu-id="05f70-114">**Variabel Bryt punkt.**</span><span class="sxs-lookup"><span data-stu-id="05f70-114">**Variable breakpoint.**</span></span> <span data-ttu-id="05f70-115">Skriptet pausas när den angivna variabelns värde ändras.</span><span class="sxs-lookup"><span data-stu-id="05f70-115">The script pauses whenever the designated variable's value changes.</span></span>

1. <span data-ttu-id="05f70-116">**Kommando Bryt punkt.**</span><span class="sxs-lookup"><span data-stu-id="05f70-116">**Command breakpoint.**</span></span> <span data-ttu-id="05f70-117">Skriptet pausas när det angivna kommandot ska köras när skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="05f70-117">The script pauses whenever the designated command is about to be run during the operation of the script.</span></span> <span data-ttu-id="05f70-118">Den kan innehålla parametrar för att ytterligare filtrera Bryt punkten till den åtgärd som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="05f70-118">It can include parameters to further filter the breakpoint to only the operation you want.</span></span> <span data-ttu-id="05f70-119">Kommandot kan också vara en funktion som du har skapat.</span><span class="sxs-lookup"><span data-stu-id="05f70-119">The command can also be a function you created.</span></span>

<span data-ttu-id="05f70-120">Av dessa, i Windows PowerShell ISE fel söknings miljö, kan endast rad Bryt punkter anges med hjälp av menyn eller kortkommandona.</span><span class="sxs-lookup"><span data-stu-id="05f70-120">Of these, in the Windows PowerShell ISE debugging environment, only line breakpoints can be set by using the menu or the keyboard shortcuts.</span></span> <span data-ttu-id="05f70-121">De andra två typerna av Bryt punkter kan anges, men de ställs in från konsol fönstret med hjälp av cmdleten [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-121">The other two types of breakpoints can be set, but they are set from the Console Pane by using the [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) cmdlet.</span></span> <span data-ttu-id="05f70-122">I det här avsnittet beskrivs hur du kan utföra fel sökning av uppgifter i Windows PowerShell ISE genom att använda menyerna där de är tillgängliga och utföra ett bredare antal kommandon från konsol fönstret med hjälp av skript.</span><span class="sxs-lookup"><span data-stu-id="05f70-122">This section describes how you can perform debugging tasks in Windows PowerShell ISE by using the menus where available, and perform a wider range of commands from the Console Pane by using scripting.</span></span>

### <a name="to-set-a-breakpoint"></a><span data-ttu-id="05f70-123">Ange en brytpunkt</span><span class="sxs-lookup"><span data-stu-id="05f70-123">To set a breakpoint</span></span>

<span data-ttu-id="05f70-124">En Bryt punkt kan bara anges i ett skript när den har sparats.</span><span class="sxs-lookup"><span data-stu-id="05f70-124">A breakpoint can be set in a script only after it has been saved.</span></span> <span data-ttu-id="05f70-125">Högerklicka på linjen där du vill ange en rad Bryt punkt och klicka sedan på **Växla Bryt punkt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-125">Right-click the line where you want to set a line breakpoint, and then click **Toggle Breakpoint**.</span></span> <span data-ttu-id="05f70-126">Alternativt klickar du på linjen där du vill ange en rad Bryt punkt och trycker på <kbd>F9</kbd> eller klickar på **Växla Bryt punkt**på **fel söknings** menyn.</span><span class="sxs-lookup"><span data-stu-id="05f70-126">Or, click the line where you want to set a line breakpoint, and press <kbd>F9</kbd> or, on the **Debug** menu, click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="05f70-127">Följande skript är ett exempel på hur du kan ange en variabel Bryt punkt från konsol fönstret med hjälp av cmdleten [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-127">The following script is an example of how you can set a variable breakpoint from the Console Pane by using the [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a><span data-ttu-id="05f70-128">Lista alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="05f70-128">List all breakpoints</span></span>

<span data-ttu-id="05f70-129">Visar alla Bryt punkter i den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="05f70-129">Displays all breakpoints in the current Windows PowerShell session.</span></span>

<span data-ttu-id="05f70-130">På **fel söknings** menyn klickar du på **list Bryt punkter**.</span><span class="sxs-lookup"><span data-stu-id="05f70-130">On the **Debug** menu, click **List Breakpoints**.</span></span> <span data-ttu-id="05f70-131">Följande skript är ett exempel på hur du kan visa alla Bryt punkter från konsol fönstret med hjälp av cmdleten [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-131">The following script is an example of how you can list all breakpoints from the Console Pane by using the [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a><span data-ttu-id="05f70-132">Ta bort en Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="05f70-132">Remove a breakpoint</span></span>

<span data-ttu-id="05f70-133">Borttagning av en Bryt punkt tar bort den.</span><span class="sxs-lookup"><span data-stu-id="05f70-133">Removing a breakpoint deletes it.</span></span>

<span data-ttu-id="05f70-134">Om du tror att du kanske vill använda den igen senare bör du [inaktivera en Bryt punkt](#disable-a-breakpoint) i stället.</span><span class="sxs-lookup"><span data-stu-id="05f70-134">If you think you might want to use it again later, consider [Disable a Breakpoint](#disable-a-breakpoint) it instead.</span></span> <span data-ttu-id="05f70-135">Högerklicka på linjen där du vill ta bort en Bryt punkt och klicka sedan på **ToggleBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="05f70-135">Right-click the line where you want to remove a breakpoint, and then click **ToggleBreakpoint**.</span></span>
<span data-ttu-id="05f70-136">Du kan också klicka på den rad där du vill ta bort en Bryt punkt och på **fel söknings** menyn klickar du på **Växla Bryt punkt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-136">Or, click the line where you want to remove a breakpoint, and on the **Debug** menu, click **Toggle Breakpoint**.</span></span> <span data-ttu-id="05f70-137">Följande skript är ett exempel på hur du tar bort en Bryt punkt med ett angivet ID från konsol fönstret med hjälp av cmdleten [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-137">The following script is an example of how to remove a breakpoint with a specified ID from the Console Pane by using the [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a><span data-ttu-id="05f70-138">Ta bort alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="05f70-138">Remove All Breakpoints</span></span>

<span data-ttu-id="05f70-139">Om du vill ta bort alla Bryt punkter som definierats i den aktuella sessionen klickar du på **ta bort alla Bryt punkter**på **Felsök** -menyn.</span><span class="sxs-lookup"><span data-stu-id="05f70-139">To remove all breakpoints defined in the current session, on the **Debug** menu, click **Remove All Breakpoints**.</span></span>

<span data-ttu-id="05f70-140">Följande skript är ett exempel på hur du tar bort alla Bryt punkter från konsol fönstret med hjälp av cmdleten [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-140">The following script is an example of how to remove all breakpoints from the Console Pane by using the [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a><span data-ttu-id="05f70-141">Inaktivera en Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="05f70-141">Disable a Breakpoint</span></span>

<span data-ttu-id="05f70-142">Om du inaktiverar en Bryt punkt tas den inte bort. den stänger av den tills den är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="05f70-142">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span> <span data-ttu-id="05f70-143">Om du vill inaktivera en speciell rad Bryt punkt högerklickar du på linjen där du vill inaktivera en Bryt punkt och klickar sedan på **inaktivera Bryt punkt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-143">To disable a specific line breakpoint, right-click the line where you want to disable a breakpoint, and then click **Disable Breakpoint**.</span></span> <span data-ttu-id="05f70-144">Eller klicka på den rad där du vill inaktivera en Bryt punkt och tryck på <kbd>F9</kbd> eller på **fel söknings** menyn, klicka på **inaktivera Bryt punkt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-144">Or, click the line where you want to disable a breakpoint, and press <kbd>F9</kbd> or, on the **Debug** menu, click **Disable Breakpoint**.</span></span> <span data-ttu-id="05f70-145">Följande skript är ett exempel på hur du kan ta bort en Bryt punkt med ett angivet ID från konsol fönstret med hjälp av cmdleten [disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-145">The following script is an example of how you can remove a breakpoint with a specified ID from the Console Pane by using the [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a><span data-ttu-id="05f70-146">Inaktivera alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="05f70-146">Disable All Breakpoints</span></span>

<span data-ttu-id="05f70-147">Om du inaktiverar en Bryt punkt tas den inte bort. den stänger av den tills den är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="05f70-147">Disabling a breakpoint does not remove it; it turns it off until it is enabled.</span></span> <span data-ttu-id="05f70-148">Om du vill inaktivera alla Bryt punkter i den aktuella sessionen går du till **Felsök** -menyn och klickar på **inaktivera alla Bryt punkter**.</span><span class="sxs-lookup"><span data-stu-id="05f70-148">To disable all breakpoints in the current session, on the **Debug** menu, click **Disable all Breakpoints**.</span></span> <span data-ttu-id="05f70-149">Följande skript är ett exempel på hur du kan inaktivera alla Bryt punkter från konsol fönstret med hjälp av cmdleten [disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-149">The following script is an example of how you can disable all breakpoints from the Console Pane by using the [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a><span data-ttu-id="05f70-150">Aktivera en Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="05f70-150">Enable a Breakpoint</span></span>

<span data-ttu-id="05f70-151">Om du vill aktivera en speciell Bryt punkt högerklickar du på linjen där du vill aktivera en Bryt punkt och klickar sedan på **Aktivera Bryt punkt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-151">To enable a specific breakpoint, right-click the line where you want to enable a breakpoint, and then click **Enable Breakpoint**.</span></span> <span data-ttu-id="05f70-152">Du kan också klicka på den rad där du vill aktivera en Bryt punkt och sedan trycka på <kbd>F9</kbd> eller klicka på **Aktivera Bryt punkt**på **fel söknings** menyn.</span><span class="sxs-lookup"><span data-stu-id="05f70-152">Or, click the line where you want to enable a breakpoint, and then press <kbd>F9</kbd> or, on the **Debug** menu, click **Enable Breakpoint**.</span></span> <span data-ttu-id="05f70-153">Följande skript är ett exempel på hur du kan aktivera vissa Bryt punkter från konsol fönstret med hjälp av cmdleten [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-153">The following script is an example of how you can enable specific breakpoints from the Console Pane by using the [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a><span data-ttu-id="05f70-154">Aktivera alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="05f70-154">Enable All Breakpoints</span></span>

<span data-ttu-id="05f70-155">Om du vill aktivera alla Bryt punkter som definierats i den aktuella sessionen går du till **Felsök** -menyn och klickar på **Aktivera alla Bryt punkter**.</span><span class="sxs-lookup"><span data-stu-id="05f70-155">To enable all breakpoints defined in the current session, on the **Debug** menu, click **Enable all Breakpoints**.</span></span> <span data-ttu-id="05f70-156">Följande skript är ett exempel på hur du kan aktivera alla Bryt punkter från konsol fönstret med hjälp av cmdleten [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) .</span><span class="sxs-lookup"><span data-stu-id="05f70-156">The following script is an example of how you can enable all breakpoints from the Console Pane by using the [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) cmdlet.</span></span>

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a><span data-ttu-id="05f70-157">Så här hanterar du en felsökningssession</span><span class="sxs-lookup"><span data-stu-id="05f70-157">How to manage a debugging session</span></span>

<span data-ttu-id="05f70-158">Innan du börjar felsöka måste du ange en eller flera Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="05f70-158">Before you start debugging, you must set one or more breakpoints.</span></span> <span data-ttu-id="05f70-159">Du kan inte ange en Bryt punkt om inte skriptet som du vill felsöka har sparats.</span><span class="sxs-lookup"><span data-stu-id="05f70-159">You cannot set a breakpoint unless the script that you want to debug is saved.</span></span> <span data-ttu-id="05f70-160">Instruktioner för hur du ställer in en Bryt punkt finns i [Hantera Bryt punkter](#how-to-manage-breakpoints) eller [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint).</span><span class="sxs-lookup"><span data-stu-id="05f70-160">For directions on of how to set a breakpoint, see [How to manage breakpoints](#how-to-manage-breakpoints) or [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint).</span></span>
<span data-ttu-id="05f70-161">När du har startat fel sökningen kan du inte redigera ett skript förrän du har stoppat fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="05f70-161">After you start debugging, you cannot edit a script until you stop debugging.</span></span> <span data-ttu-id="05f70-162">Ett skript som har en eller flera Bryt punkter sparas automatiskt innan det körs.</span><span class="sxs-lookup"><span data-stu-id="05f70-162">A script that has one or more breakpoints set is automatically saved before it is run.</span></span>

### <a name="to-start-debugging"></a><span data-ttu-id="05f70-163">Starta fel sökning</span><span class="sxs-lookup"><span data-stu-id="05f70-163">To start debugging</span></span>

<span data-ttu-id="05f70-164">Tryck på <kbd>F5</kbd> eller klicka på **Kör skript** ikonen i verktygsfältet eller på **fel söknings** menyn klickar du på **Kör/Fortsätt**.</span><span class="sxs-lookup"><span data-stu-id="05f70-164">Press <kbd>F5</kbd> or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu click **Run/Continue**.</span></span> <span data-ttu-id="05f70-165">Skriptet körs tills det påträffar den första Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="05f70-165">The script runs until it encounters the first breakpoint.</span></span> <span data-ttu-id="05f70-166">Åtgärden pausar där och markerar den rad där den pausades.</span><span class="sxs-lookup"><span data-stu-id="05f70-166">It pauses operation there and highlights the line on which it paused.</span></span>

### <a name="to-continue-debugging"></a><span data-ttu-id="05f70-167">För att fortsätta fel sökningen</span><span class="sxs-lookup"><span data-stu-id="05f70-167">To continue debugging</span></span>

<span data-ttu-id="05f70-168">Tryck på <kbd>F5</kbd> eller klicka på ikonen **Kör skript** i verktygsfältet eller på **fel söknings** menyn, klicka på **Kör/fortsätt** eller i konsol fönstret, skriv `C` och tryck sedan på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-168">Press <kbd>F5</kbd> or, on the toolbar, click the **Run Script** icon, or on the **Debug** menu, click **Run/Continue** or, in the Console Pane, type `C` and then press <kbd>ENTER</kbd>.</span></span> <span data-ttu-id="05f70-169">Detta gör att skriptet fortsätter att köras till nästa Bryt punkt eller till slutet av skriptet om inga ytterligare Bryt punkter påträffas.</span><span class="sxs-lookup"><span data-stu-id="05f70-169">This causes the script to continue running to the next breakpoint or to the end of the script if no further breakpoints are encountered.</span></span>

### <a name="to-view-the-call-stack"></a><span data-ttu-id="05f70-170">Visa anrops stacken</span><span class="sxs-lookup"><span data-stu-id="05f70-170">To view the call stack</span></span>

<span data-ttu-id="05f70-171">Anrops stacken visar den aktuella körnings platsen i skriptet.</span><span class="sxs-lookup"><span data-stu-id="05f70-171">The call stack displays the current run location in the script.</span></span> <span data-ttu-id="05f70-172">Om skriptet körs i en funktion som anropades av en annan funktion visas detta i visningen av ytterligare rader i utdata.</span><span class="sxs-lookup"><span data-stu-id="05f70-172">If the script is running in a function that was called by a different function, then that is represented in the display by additional rows in the output.</span></span> <span data-ttu-id="05f70-173">Den nedersta raden visar det ursprungliga skriptet och den rad i vilken en funktion anropades.</span><span class="sxs-lookup"><span data-stu-id="05f70-173">The bottom-most row displays the original script and the line in it in which a function was called.</span></span> <span data-ttu-id="05f70-174">Nästa rad i visar funktionen och den rad i vilken en annan funktion kan ha anropats.</span><span class="sxs-lookup"><span data-stu-id="05f70-174">The next line up shows that function and the line in it in which another function might have been called.</span></span> <span data-ttu-id="05f70-175">Den översta raden visar den aktuella kontexten för den aktuella raden som Bryt punkten har angetts på.</span><span class="sxs-lookup"><span data-stu-id="05f70-175">The top-most row shows the current context of the current line on which the breakpoint is set.</span></span>

<span data-ttu-id="05f70-176">När du är pausad kan du se den aktuella anrops stacken genom att trycka på <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> eller, på **fel söknings** menyn, klicka på **Visa anrops stack** eller, i rutan konsol, skriva `K` och sedan trycka på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-176">While paused, to see the current call stack, press <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd> or, on the **Debug** menu, click **Display Call Stack** or, in the Console Pane, type `K` and then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-stop-debugging"></a><span data-ttu-id="05f70-177">Stoppa fel sökningen</span><span class="sxs-lookup"><span data-stu-id="05f70-177">To stop debugging</span></span>

<span data-ttu-id="05f70-178">Tryck på <kbd>SHIFT</kbd>+<kbd>F5</kbd> eller på **fel** söknings menyn, klicka på **stoppa fel sökning**eller Skriv `Q` i konsol fönstret och tryck sedan på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-178">Press <kbd>SHIFT</kbd>+<kbd>F5</kbd> or, on the **Debug** menu, click **Stop Debugger**, or, in the Console Pane, type `Q` and then press <kbd>ENTER</kbd>.</span></span>

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a><span data-ttu-id="05f70-179">Stega över, stega och stega under fel sökning</span><span class="sxs-lookup"><span data-stu-id="05f70-179">How to step over, step into, and step out while debugging</span></span>

<span data-ttu-id="05f70-180">Steging är en process för att köra en instruktion i taget.</span><span class="sxs-lookup"><span data-stu-id="05f70-180">Stepping is the process of running one statement at a time.</span></span> <span data-ttu-id="05f70-181">Du kan stoppa en kodrad och undersöka värdena för variabler och systemets tillstånd.</span><span class="sxs-lookup"><span data-stu-id="05f70-181">You can stop on a line of code, and examine the values of variables and the state of the system.</span></span> <span data-ttu-id="05f70-182">I följande tabell beskrivs vanliga fel söknings uppgifter, t. ex. att gå över, integrera och Stega ut.</span><span class="sxs-lookup"><span data-stu-id="05f70-182">The following table describes common debugging tasks such as stepping over, stepping into, and stepping out.</span></span>

| <span data-ttu-id="05f70-183">Fel söknings uppgift</span><span class="sxs-lookup"><span data-stu-id="05f70-183">Debugging Task</span></span> |                                                                                                                   <span data-ttu-id="05f70-184">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="05f70-184">Description</span></span>                                                                                                                    |                                                      <span data-ttu-id="05f70-185">Så här åstadkommer du det i PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="05f70-185">How to accomplish it in PowerShell ISE</span></span>                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="05f70-186">**Stega in**</span><span class="sxs-lookup"><span data-stu-id="05f70-186">**Step Into**</span></span>  | <span data-ttu-id="05f70-187">Kör den aktuella instruktionen och stoppar sedan nästa instruktion.</span><span class="sxs-lookup"><span data-stu-id="05f70-187">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="05f70-188">Om den aktuella instruktionen är en funktion eller ett skript anrop, kommer fel söknings stegen till den funktionen eller skriptet, annars stoppas vid nästa instruktion.</span><span class="sxs-lookup"><span data-stu-id="05f70-188">If the current statement is a function or script call, then the debugger steps into that function or script, otherwise it stops at the next statement.</span></span>                      | <span data-ttu-id="05f70-189">Tryck på <kbd>F11</kbd> eller på **fel söknings** menyn, klicka på **stega i**eller i konsol fönstret, skriv `S` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-189">Press <kbd>F11</kbd> or, on the **Debug** menu, click **Step Into**, or in the Console Pane, type `S` and press <kbd>ENTER</kbd>.</span></span>                 |
| <span data-ttu-id="05f70-190">**Steg över**</span><span class="sxs-lookup"><span data-stu-id="05f70-190">**Step Over**</span></span>  | <span data-ttu-id="05f70-191">Kör den aktuella instruktionen och stoppar sedan nästa instruktion.</span><span class="sxs-lookup"><span data-stu-id="05f70-191">Executes the current statement and then stops at the next statement.</span></span> <span data-ttu-id="05f70-192">Om den aktuella instruktionen är en funktion eller ett skript anrop, kör fel söknings programmet hela funktionen eller skriptet och stannar vid nästa instruktion efter funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="05f70-192">If the current statement is a function or script call, then the debugger executes the whole function or script, and it stops at the next statement after the function call.</span></span> | <span data-ttu-id="05f70-193">Tryck på <kbd>F10</kbd> eller på **fel söknings** menyn, klicka på **steg över**eller i konsol fönstret, skriv `V` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-193">Press <kbd>F10</kbd> or, on the **Debug** menu, click **Step Over**, or in the Console Pane, type `V` and press <kbd>ENTER</kbd>.</span></span>                 |
| <span data-ttu-id="05f70-194">**Gå ut**</span><span class="sxs-lookup"><span data-stu-id="05f70-194">**Step Out**</span></span>   | <span data-ttu-id="05f70-195">Steg ut ur den aktuella funktionen och upp en nivå om funktionen är kapslad.</span><span class="sxs-lookup"><span data-stu-id="05f70-195">Steps out of the current function and up one level if the function is nested.</span></span> <span data-ttu-id="05f70-196">Om i huvud texten körs skriptet till slutet eller till nästa Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="05f70-196">If in the main body, the script is executed to the end, or to the next breakpoint.</span></span> <span data-ttu-id="05f70-197">De överhoppade instruktionerna körs, men är inte stegvisa.</span><span class="sxs-lookup"><span data-stu-id="05f70-197">The skipped statements are executed, but not stepped through.</span></span>                   | <span data-ttu-id="05f70-198">Tryck på <kbd>SHIFT</kbd>+<kbd>F11</kbd>eller på **fel söknings** menyn, klicka på **Stega ut**eller Skriv `O` i konsol fönstret och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-198">Press <kbd>SHIFT</kbd>+<kbd>F11</kbd>, or on the **Debug** menu, click **Step Out**, or in the Console Pane, type `O` and press <kbd>ENTER</kbd>.</span></span> |
| <span data-ttu-id="05f70-199">**Bestå**</span><span class="sxs-lookup"><span data-stu-id="05f70-199">**Continue**</span></span>   | <span data-ttu-id="05f70-200">Fortsätter körningen till slutet eller till nästa Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="05f70-200">Continues execution to the end, or to the next breakpoint.</span></span> <span data-ttu-id="05f70-201">De överhoppade funktionerna och anropen utförs, men inte stegvisa.</span><span class="sxs-lookup"><span data-stu-id="05f70-201">The skipped functions and invocations are executed, but not stepped through.</span></span>                                                                                                          | <span data-ttu-id="05f70-202">Tryck på <kbd>F5</kbd> eller på **Felsök** -menyn, klicka på **Kör/Fortsätt**eller i konsol fönstret, skriv `C` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-202">Press <kbd>F5</kbd> or, on the **Debug** menu, click **Run/Continue**, or in the Console Pane, type `C` and press <kbd>ENTER</kbd>.</span></span>               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a><span data-ttu-id="05f70-203">Så här visar du värden för variabler under fel sökning</span><span class="sxs-lookup"><span data-stu-id="05f70-203">How to display the values of variables while debugging</span></span>

<span data-ttu-id="05f70-204">Du kan visa de aktuella värdena för variabler i skriptet när du går igenom koden.</span><span class="sxs-lookup"><span data-stu-id="05f70-204">You can display the current values of variables in the script as you step through the code.</span></span>

### <a name="to-display-the-values-of-standard-variables"></a><span data-ttu-id="05f70-205">Visa värden för standardvariabler</span><span class="sxs-lookup"><span data-stu-id="05f70-205">To display the values of standard variables</span></span>

<span data-ttu-id="05f70-206">Använd en av följande metoder:</span><span class="sxs-lookup"><span data-stu-id="05f70-206">Use one of the following methods:</span></span>

- <span data-ttu-id="05f70-207">Hovra över variabeln i rutan skript och visa dess värde som en verktygs beskrivning.</span><span class="sxs-lookup"><span data-stu-id="05f70-207">In the Script Pane, hover over the variable to display its value as a tool tip.</span></span>

- <span data-ttu-id="05f70-208">I konsol fönstret skriver du variabelns namn och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="05f70-208">In the Console Pane, type the variable name and press <kbd>ENTER</kbd>.</span></span>

<span data-ttu-id="05f70-209">Alla fönster i ISE är alltid i samma omfång.</span><span class="sxs-lookup"><span data-stu-id="05f70-209">All panes in ISE are always in the same scope.</span></span> <span data-ttu-id="05f70-210">När du felsöker ett skript kan du därför köra de kommandon som du skriver i konsol fönstret i skript omfång.</span><span class="sxs-lookup"><span data-stu-id="05f70-210">Therefore, while you are debugging a script, the commands that you type in the Console Pane run in script scope.</span></span> <span data-ttu-id="05f70-211">På så sätt kan du använda konsol fönstret för att hitta värden för variabler och anropa funktioner som bara definieras i skriptet.</span><span class="sxs-lookup"><span data-stu-id="05f70-211">This allows you to use the Console Pane to find the values of variables and call functions that are defined only in the script.</span></span>

### <a name="to-display-the-values-of-automatic-variables"></a><span data-ttu-id="05f70-212">Visa värden för automatiska variabler</span><span class="sxs-lookup"><span data-stu-id="05f70-212">To display the values of automatic variables</span></span>

<span data-ttu-id="05f70-213">Du kan använda föregående metod för att visa värdet för nästan alla variabler medan du felsöker ett skript.</span><span class="sxs-lookup"><span data-stu-id="05f70-213">You can use the preceding method to display the value of almost all variables while you are debugging a script.</span></span> <span data-ttu-id="05f70-214">Dessa metoder fungerar dock inte för följande automatiska variabler.</span><span class="sxs-lookup"><span data-stu-id="05f70-214">However, these methods do not work for the following automatic variables.</span></span>

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

<span data-ttu-id="05f70-215">Om du försöker visa värdet för någon av dessa variabler får du värdet för den variabeln för i en intern pipeline som fel sökaren använder, inte värdet för variabeln i skriptet.</span><span class="sxs-lookup"><span data-stu-id="05f70-215">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span> <span data-ttu-id="05f70-216">Du kan kringgå detta för några få variabler (`$_`, `$Input`, `$MyInvocation`, `$PSBoundParameters`och `$Args`) med hjälp av följande metod:</span><span class="sxs-lookup"><span data-stu-id="05f70-216">You can work around this for a few variables (`$_`, `$Input`, `$MyInvocation`, `$PSBoundParameters`, and `$Args`) by using the following method:</span></span>

1. <span data-ttu-id="05f70-217">I skriptet tilldelar du värdet för den automatiska variabeln till en ny variabel.</span><span class="sxs-lookup"><span data-stu-id="05f70-217">In the script, assign the value of the automatic variable to a new variable.</span></span>

1. <span data-ttu-id="05f70-218">Visa värdet för den nya variabeln, antingen genom att hovra över den nya variabeln i skript fönstret eller genom att skriva den nya variabeln i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="05f70-218">Display the value of the new variable, either by hovering over the new variable in the Script Pane, or by typing the new variable in the Console Pane.</span></span>

<span data-ttu-id="05f70-219">Om du till exempel vill visa värdet för variabeln `$MyInvocation`, i skriptet, tilldelar du värdet till en ny variabel, till exempel `$scriptName`, och hovrar sedan över eller skriver `$scriptName` variabeln för att visa dess värde.</span><span class="sxs-lookup"><span data-stu-id="05f70-219">For example, to display the value of the `$MyInvocation` variable, in the script, assign the value to a new variable, such as `$scriptName`, and then hover over or type the `$scriptName` variable to display its value.</span></span>

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a><span data-ttu-id="05f70-220">Se även</span><span class="sxs-lookup"><span data-stu-id="05f70-220">See Also</span></span>

[<span data-ttu-id="05f70-221">Utforska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="05f70-221">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
