---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Skriv och kör skript i Windows PowerShell ISE
ms.openlocfilehash: 4a08d7d206d103dcb398964d7ce75bea1e76559a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67028968"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="2ed22-103">Skriv och kör skript i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2ed22-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="2ed22-104">Den här artikeln beskriver hur du skapa, redigera, köra och spara skript i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="2ed22-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="2ed22-105">Hur du skapar och kör skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-105">How to create and run scripts</span></span>

<span data-ttu-id="2ed22-106">Du kan öppna och redigera Windows PowerShell-filer i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="2ed22-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="2ed22-107">Specifika filtyper intressanta i Windows PowerShell är skriptfiler (.ps1), skriptfiler data (.psd1) och modulen skriptfiler (.psm1).</span><span class="sxs-lookup"><span data-stu-id="2ed22-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="2ed22-108">De här filtyperna är färgade i skriptfönstret redigeraren syntax.</span><span class="sxs-lookup"><span data-stu-id="2ed22-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="2ed22-109">Andra vanliga filtyper som du kan öppna i skriptfönstret är konfigurationsfiler (.ps1xml), XML-filer och textfiler.</span><span class="sxs-lookup"><span data-stu-id="2ed22-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="2ed22-110">Windows PowerShell-körningsprincipen avgör om du kan köra skript och läsa in Windows PowerShell-profiler och konfigurationsfiler.</span><span class="sxs-lookup"><span data-stu-id="2ed22-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="2ed22-111">Standardprincipen för körning begränsad, förhindrar alla skript från att köras och förhindrar inläsning av profiler.</span><span class="sxs-lookup"><span data-stu-id="2ed22-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="2ed22-112">Om du vill ändra körningsprincipen för att tillåta profiler att läsa in och används, se [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) och [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="2ed22-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="2ed22-113">Du skapar en ny skriptfil</span><span class="sxs-lookup"><span data-stu-id="2ed22-113">To create a new script file</span></span>

<span data-ttu-id="2ed22-114">I verktygsfältet klickar du på **New**, eller på den **filen** -menyn klickar du på **New**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="2ed22-115">Den skapade filen visas i en ny flik i filen under den aktuella PowerShell-fliken. Kom ihåg att PowerShell-flikar visas bara när det finns fler än en.</span><span class="sxs-lookup"><span data-stu-id="2ed22-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="2ed22-116">Som standard skapas en fil av typen skript (.ps1), men den kan sparas med ett nytt namn och tillägg.</span><span class="sxs-lookup"><span data-stu-id="2ed22-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="2ed22-117">Flera skriptfiler kan skapas i samma PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="2ed22-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="2ed22-118">Öppna ett befintligt skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-118">To open an existing script</span></span>

<span data-ttu-id="2ed22-119">I verktygsfältet klickar du på **öppna**, eller på den **filen** -menyn klickar du på **öppna**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="2ed22-120">I den **öppna** dialogrutan väljer du den fil du vill öppna.</span><span class="sxs-lookup"><span data-stu-id="2ed22-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="2ed22-121">Öppna filen visas i en ny flik.</span><span class="sxs-lookup"><span data-stu-id="2ed22-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="2ed22-122">Stäng fliken ett skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-122">To close a script tab</span></span>

<span data-ttu-id="2ed22-123">Klickar du på den **Stäng** ikonen (X) av fliken fil som du vill stänga eller Välj den **filen** menyn och klickar på **Stäng**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="2ed22-124">Om filen har ändrats sedan den senast sparades, uppmanas du att spara eller ta bort den.</span><span class="sxs-lookup"><span data-stu-id="2ed22-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="2ed22-125">Att visa sökvägen till filen</span><span class="sxs-lookup"><span data-stu-id="2ed22-125">To display the file path</span></span>

<span data-ttu-id="2ed22-126">På fliken Arkiv, pekar du på namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="2ed22-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="2ed22-127">Den fullständiga sökvägen till skriptfilen visas i en knappbeskrivning.</span><span class="sxs-lookup"><span data-stu-id="2ed22-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="2ed22-128">Att köra ett skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-128">To run a script</span></span>

<span data-ttu-id="2ed22-129">I verktygsfältet klickar du på **kör skript**, eller på den **filen** -menyn klickar du på **kör**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="2ed22-130">Att köra en del av ett skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-130">To run a portion of a script</span></span>

1. <span data-ttu-id="2ed22-131">I skriptfönstret, väljer du en del av ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ed22-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="2ed22-132">På den **filen** -menyn klickar du på **kör**, eller i verktygsfältet klickar du på **kör**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="2ed22-133">Stoppa en som kör skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-133">To stop a running script</span></span>

<span data-ttu-id="2ed22-134">Det finns flera sätt att sluta köra skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ed22-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="2ed22-135">Klicka på **stoppa åtgärden** i verktygsfältet</span><span class="sxs-lookup"><span data-stu-id="2ed22-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="2ed22-136">Tryck på CTRL + BREAK</span><span class="sxs-lookup"><span data-stu-id="2ed22-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="2ed22-137">Välj den **filen** menyn och klickar på **stoppa åtgärden**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="2ed22-138">Att trycka på **CTRL + C** fungerar även om inte text är markerad kan i så fall **CTRL + C** mappar till kopieringsfunktionen för den markerade texten.</span><span class="sxs-lookup"><span data-stu-id="2ed22-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="2ed22-139">Hur du skriver och redigerar text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="2ed22-140">Du kan kopiera, klippa ut, klistra in, söka och ersätta text i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="2ed22-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="2ed22-141">Du kan också ångra och gör om den senaste åtgärden som du precis har utfört.</span><span class="sxs-lookup"><span data-stu-id="2ed22-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="2ed22-142">Kortkommandon för dessa åtgärder är samma kortkommandon som används för alla Windows-program.</span><span class="sxs-lookup"><span data-stu-id="2ed22-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="2ed22-143">Ange text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="2ed22-144">Flytta markören till skriptfönstret genom att klicka i skriptfönstret eller genom att klicka på **går du till skriptfönstret** i den **visa** menyn.</span><span class="sxs-lookup"><span data-stu-id="2ed22-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="2ed22-145">Skapa ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ed22-145">Create a script.</span></span> <span data-ttu-id="2ed22-146">Syntaxfärgning och tabbifyllning ger en rikare redigering upplevelse i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2ed22-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="2ed22-147">Se [så Använd Tabbifyllning i skriptfönstret och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) mer information om hur du använder funktionen fliken slutförande för enklare att skriva.</span><span class="sxs-lookup"><span data-stu-id="2ed22-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="2ed22-148">Söka efter text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="2ed22-149">Du kan hitta text var som helst genom att trycka på **CTRL + F** eller på den **redigera** -menyn klickar du på **hitta i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="2ed22-150">Om du vill hitta text efter markören, trycker du på **F3** eller på den **redigera** -menyn klickar du på **Sök nästa i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="2ed22-151">Om du vill hitta text före markören, trycker du på **SKIFT + F3** eller på den **redigera** -menyn klickar du på **Sök föregående i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="2ed22-152">Söka efter och ersätta texten i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="2ed22-153">Tryck på **CTRL + H** eller på den **redigera** -menyn klickar du på **ersättas i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="2ed22-154">Ange den text som du vill att hitta och ersättningstexten, tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="2ed22-155">Gå till en viss rad med text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="2ed22-156">I skriptfönstret, trycker du på **CTRL + G** eller på den **redigera** -menyn klickar du på **går du till rad**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="2ed22-157">Ange ett radnummer.</span><span class="sxs-lookup"><span data-stu-id="2ed22-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="2ed22-158">Kopiera text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="2ed22-159">I skriptfönstret, väljer du den text som du vill kopiera.</span><span class="sxs-lookup"><span data-stu-id="2ed22-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="2ed22-160">Tryck på **CTRL + C** i verktygsfältet klickar du på den **kopia** ikonen eller på den **redigera** -menyn klickar du på **kopia**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="2ed22-161">Att klippa ut text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="2ed22-162">I skriptfönstret, väljer du den text som du vill minska.</span><span class="sxs-lookup"><span data-stu-id="2ed22-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="2ed22-163">Tryck på **CTRL + X** i verktygsfältet klickar du på den **klipp ut** ikon, eller på den **redigera** -menyn klickar du på **klipp ut**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="2ed22-164">Klistra in text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="2ed22-165">Tryck på **CTRL + V** i verktygsfältet klickar du på den **klistra in** ikon, eller på den **redigera** -menyn klickar du på **klistra in**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="2ed22-166">Ångra en åtgärd i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="2ed22-167">Tryck på **CTRL + Z** i verktygsfältet klickar du på den **ångra** ikon, eller på den **redigera** -menyn klickar du på **ångra**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="2ed22-168">Att göra om en åtgärd i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="2ed22-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="2ed22-169">Tryck på **CTRL + Y** i verktygsfältet klickar du på den **gör om** ikon, eller på den **redigera** -menyn klickar du på **gör om**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="2ed22-170">Hur du sparar ett skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-170">How to save a script</span></span>

<span data-ttu-id="2ed22-171">En asterisk visas bredvid namnet på skriptet för att markera en fil som inte har sparats sedan det ändrades.</span><span class="sxs-lookup"><span data-stu-id="2ed22-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="2ed22-172">Asterisken försvinner när filen sparas.</span><span class="sxs-lookup"><span data-stu-id="2ed22-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="2ed22-173">Spara ett skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-173">To save a script</span></span>

<span data-ttu-id="2ed22-174">Tryck på **CTRL + S** i verktygsfältet klickar du på den **spara** ikonen eller på den **filen** -menyn klickar du på **spara**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="2ed22-175">Spara och namnge ett skript</span><span class="sxs-lookup"><span data-stu-id="2ed22-175">To save and name a script</span></span>

1. <span data-ttu-id="2ed22-176">På den **filen** -menyn klickar du på **Spara som**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="2ed22-177">Den **Spara som** dialogrutan visas.</span><span class="sxs-lookup"><span data-stu-id="2ed22-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="2ed22-178">I den **filnamn** anger du ett namn för filen.</span><span class="sxs-lookup"><span data-stu-id="2ed22-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="2ed22-179">I den **filformat** väljer du en viss filtyp.</span><span class="sxs-lookup"><span data-stu-id="2ed22-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="2ed22-180">Till exempel i den **filformat** väljer ”PowerShell-skript (\*.ps1)”.</span><span class="sxs-lookup"><span data-stu-id="2ed22-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="2ed22-181">Klicka på **Spara**.</span><span class="sxs-lookup"><span data-stu-id="2ed22-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="2ed22-182">Spara ett skript i ASCII-kodning</span><span class="sxs-lookup"><span data-stu-id="2ed22-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="2ed22-183">Som standard sparar Windows PowerShell ISE nya skriptfiler (.ps1), skriptfiler data (.psd1) och modulen skriptfiler (.psm1) som Unicode (BigEndianUnicode) som standard. Â vill spara ett skript i en annan kodning, till exempel ASCII (ANSI), använder den **spara** eller **spara** metoder på det [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) objekt.</span><span class="sxs-lookup"><span data-stu-id="2ed22-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="2ed22-184">Följande kommando sparar ett nytt skript som MyScript.ps1 med ASCII-kodning.</span><span class="sxs-lookup"><span data-stu-id="2ed22-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="2ed22-185">Följande kommando ersätter den aktuella skriptfilen med en fil med samma namn men med ASCII-kod.</span><span class="sxs-lookup"><span data-stu-id="2ed22-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="2ed22-186">Följande kommando hämtar kodning av den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="2ed22-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="2ed22-187">Windows PowerShell ISE stöder följande kodningsalternativ: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 och standard.</span><span class="sxs-lookup"><span data-stu-id="2ed22-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="2ed22-188">Värdet för standardalternativet varierar beroende på systemet.</span><span class="sxs-lookup"><span data-stu-id="2ed22-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="2ed22-189">Windows PowerShell ISE inte ändra kodningen skriptfiler när du använder spara eller spara som kommandon.</span><span class="sxs-lookup"><span data-stu-id="2ed22-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ed22-190">Se även</span><span class="sxs-lookup"><span data-stu-id="2ed22-190">See Also</span></span>

- [<span data-ttu-id="2ed22-191">Utforska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="2ed22-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
