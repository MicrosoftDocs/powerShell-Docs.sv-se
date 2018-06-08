---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Skriv och kör skript i Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4d7c5352ef1dac6f63a50433676068f83a920db5
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34483125"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="794b6-103">Skriv och kör skript i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="794b6-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="794b6-104">Det här avsnittet beskriver hur du skapar, redigerar, kör och spara skript i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="794b6-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="794b6-105">Hur du skapar och kör skript</span><span class="sxs-lookup"><span data-stu-id="794b6-105">How to create and run scripts</span></span>

<span data-ttu-id="794b6-106">Du kan öppna och redigera filer i Windows PowerShell i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="794b6-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="794b6-107">Specifika filtyper av intresse för Windows PowerShell är skriptfiler (.ps1), skript datafiler (.psd1) och skriptfiler modul (.psm1).</span><span class="sxs-lookup"><span data-stu-id="794b6-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="794b6-108">De här filtyperna är syntax färgade i Redigeraren för skriptfönster.</span><span class="sxs-lookup"><span data-stu-id="794b6-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="794b6-109">Andra vanliga filtyper som du kan öppna i skriptfönstret är konfigurationsfiler (.ps1xml), XML-filer och textfiler.</span><span class="sxs-lookup"><span data-stu-id="794b6-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="794b6-110">Windows PowerShell-körningsprincipen avgör om du kan köra skript och ladda konfigurationsfiler och profiler för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="794b6-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="794b6-111">Körningsprincipen standard begränsad, förhindrar alla skript från att köras och förhindrar att läsa in profiler.</span><span class="sxs-lookup"><span data-stu-id="794b6-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="794b6-112">Om du vill ändra körningsprincipen för att tillåta profiler för att läsa in och användas [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) och [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="794b6-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="794b6-113">Skapa en ny skriptfil</span><span class="sxs-lookup"><span data-stu-id="794b6-113">To create a new script file</span></span>

<span data-ttu-id="794b6-114">I verktygsfältet klickar du på **ny** , eller på den **filen** -menyn klickar du på **ny**.</span><span class="sxs-lookup"><span data-stu-id="794b6-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="794b6-115">Skapade filen visas i en ny flik filen under aktuell PowerShell-fliken. Kom ihåg att PowerShell-flikar visas endast när det finns fler än en.</span><span class="sxs-lookup"><span data-stu-id="794b6-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="794b6-116">Som standard skapas en fil av typen skript (.ps1), men den kan sparas med ett nytt namn och filnamnstillägg.</span><span class="sxs-lookup"><span data-stu-id="794b6-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="794b6-117">Flera filer kan skapas på samma flik i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="794b6-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="794b6-118">Öppna ett befintligt skript</span><span class="sxs-lookup"><span data-stu-id="794b6-118">To open an existing script</span></span>

<span data-ttu-id="794b6-119">I verktygsfältet klickar du på **öppna**, eller på den **filen** -menyn klickar du på **öppna**.</span><span class="sxs-lookup"><span data-stu-id="794b6-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="794b6-120">I den **öppna** dialogrutan Välj filen som du vill öppna.</span><span class="sxs-lookup"><span data-stu-id="794b6-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="794b6-121">Öppna filen visas i en ny flik.</span><span class="sxs-lookup"><span data-stu-id="794b6-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="794b6-122">Stäng fliken ett skript</span><span class="sxs-lookup"><span data-stu-id="794b6-122">To close a script tab</span></span>

<span data-ttu-id="794b6-123">Klicka på fliken skript på det skript som du vill stänga och gör sedan något av följande:</span><span class="sxs-lookup"><span data-stu-id="794b6-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="794b6-124">Klicka på den **Stäng** ikon (X) på fliken skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="794b6-125">På den **filen** -menyn klickar du på **Stäng**.</span><span class="sxs-lookup"><span data-stu-id="794b6-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="794b6-126">Om filen har ändrats sedan den senast sparades, uppmanas du att spara eller ta bort den.</span><span class="sxs-lookup"><span data-stu-id="794b6-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="794b6-127">Så här visar du sökvägen till filen</span><span class="sxs-lookup"><span data-stu-id="794b6-127">To display the file path</span></span>

<span data-ttu-id="794b6-128">Peka på filnamnet på fliken Arkiv.</span><span class="sxs-lookup"><span data-stu-id="794b6-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="794b6-129">Den fullständiga sökvägen till skriptfilen visas i en knappbeskrivning.</span><span class="sxs-lookup"><span data-stu-id="794b6-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="794b6-130">Att köra ett skript</span><span class="sxs-lookup"><span data-stu-id="794b6-130">To run a script</span></span>

<span data-ttu-id="794b6-131">I verktygsfältet klickar du på **kör skriptet**, eller på den **filen** -menyn klickar du på **kör**.</span><span class="sxs-lookup"><span data-stu-id="794b6-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="794b6-132">Att köra en del av ett skript</span><span class="sxs-lookup"><span data-stu-id="794b6-132">To run a portion of a script</span></span>

1. <span data-ttu-id="794b6-133">Välj en del av ett skript i rutan skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="794b6-134">På den **filen** -menyn klickar du på **kör**, eller i verktygsfältet klickar du på **kör**.</span><span class="sxs-lookup"><span data-stu-id="794b6-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="794b6-135">Stoppa ett skript som körs</span><span class="sxs-lookup"><span data-stu-id="794b6-135">To stop a running script</span></span>

<span data-ttu-id="794b6-136">I verktygsfältet klickar du på **stoppa åtgärden**, tryck på CTRL + BREAK, eller på den **filen** -menyn klickar du på **stoppa åtgärden**.</span><span class="sxs-lookup"><span data-stu-id="794b6-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="794b6-137">När du trycker på **CTRL + C** fungerar även om vissa text är markerad, vilket innebär **CTRL + C** mappar till kopieringsfunktionen för den markerade texten.</span><span class="sxs-lookup"><span data-stu-id="794b6-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="794b6-138">Hur du skriver och redigera texten i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-138">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="794b6-139">Använd följande steg om du vill redigera texten i rutan skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="794b6-140">Du kan kopiera, Klipp ut, klistra in, söka och ersätta text.</span><span class="sxs-lookup"><span data-stu-id="794b6-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="794b6-141">Du kan också ångra och gör om den senaste åtgärden som du nyss utfört.</span><span class="sxs-lookup"><span data-stu-id="794b6-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="794b6-142">Kortkommandon för att utföra dessa åtgärder är samma som de som används för alla Windows-program.</span><span class="sxs-lookup"><span data-stu-id="794b6-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="794b6-143">Ange text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="794b6-144">Flytta markören till skriptfönstret genom att klicka i skriptfönstret eller genom att klicka på **går du till Skriptfönster** i den **visa** menyn.</span><span class="sxs-lookup"><span data-stu-id="794b6-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="794b6-145">Skapa ett skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-145">Create a script.</span></span> <span data-ttu-id="794b6-146">Syntaxen färgläggning och flikavslutande gör du detta en rikare upplevelse i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="794b6-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="794b6-147">Se [så Använd Flikavslutande i fönstret skript och konsolfönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) mer information om hur du använder funktionen fliken slutförande för att underlätta att skriva.</span><span class="sxs-lookup"><span data-stu-id="794b6-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="794b6-148">Söka efter text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="794b6-149">Om du vill söka efter text var som helst, trycker du på **CTRL + F** eller på den **redigera** -menyn klickar du på **hitta i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="794b6-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="794b6-150">Om du vill söka efter text efter markören trycker du på **F3** eller på den **redigera** -menyn klickar du på **Sök nästa i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="794b6-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="794b6-151">Om du vill söka efter text före markören trycker du på **SKIFT + F3** eller på den **redigera** -menyn klickar du på **Sök föregående i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="794b6-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="794b6-152">Söka efter och ersätta texten i rutan skript</span><span class="sxs-lookup"><span data-stu-id="794b6-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="794b6-153">Tryck på **CTRL + H** eller på den **redigera** -menyn klickar du på **ersätta i skriptet**.</span><span class="sxs-lookup"><span data-stu-id="794b6-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="794b6-154">Ange både den text som du vill söka efter och den text som du vill ersätta den och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="794b6-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="794b6-155">Gå till en viss textrad i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="794b6-156">I rutan skript trycker du på **CTRL + G** eller på den **redigera** -menyn klickar du på **går du till rad**.</span><span class="sxs-lookup"><span data-stu-id="794b6-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="794b6-157">Ange ett radnummer.</span><span class="sxs-lookup"><span data-stu-id="794b6-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="794b6-158">Kopiera text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="794b6-159">Välj den text som du vill kopiera i rutan skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="794b6-160">Tryck på **CTRL + C** i verktygsfältet klickar du på den **kopiera** ikonen, eller på den **redigera** -menyn klickar du på **kopiera**.</span><span class="sxs-lookup"><span data-stu-id="794b6-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="794b6-161">Att klippa ut text i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="794b6-162">Välj den text som du vill minska i rutan skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="794b6-163">Tryck på **CTRL + X** i verktygsfältet klickar du på den **klipp ut** ikonen, eller på den **redigera** -menyn klickar du på **klipp ut**.</span><span class="sxs-lookup"><span data-stu-id="794b6-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="794b6-164">Klistra in texten i rutan skript</span><span class="sxs-lookup"><span data-stu-id="794b6-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="794b6-165">Tryck på **CTRL + V** i verktygsfältet klickar du på den **klistra in** ikonen, eller på den **redigera** -menyn klickar du på **klistra in**.</span><span class="sxs-lookup"><span data-stu-id="794b6-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="794b6-166">Återställa en åtgärd i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="794b6-167">Tryck på **CTRL + Z** i verktygsfältet klickar du på den **ångra** ikonen, eller på den **redigera** -menyn klickar du på **ångra**.</span><span class="sxs-lookup"><span data-stu-id="794b6-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="794b6-168">Om en åtgärd i skriptfönstret</span><span class="sxs-lookup"><span data-stu-id="794b6-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="794b6-169">Tryck på **CTRL + Y** i verktygsfältet klickar du på den **gör om** ikonen, eller på den **redigera** -menyn klickar du på **gör om**.</span><span class="sxs-lookup"><span data-stu-id="794b6-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="794b6-170">Så här sparar du ett skript</span><span class="sxs-lookup"><span data-stu-id="794b6-170">How to save a script</span></span>

<span data-ttu-id="794b6-171">Använd följande steg för att spara och namnge ett skript.</span><span class="sxs-lookup"><span data-stu-id="794b6-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="794b6-172">En asterisk visas bredvid namnet på att markera en fil som inte har sparats eftersom den har ändrats.</span><span class="sxs-lookup"><span data-stu-id="794b6-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="794b6-173">Asterisken försvinner när filen sparas.</span><span class="sxs-lookup"><span data-stu-id="794b6-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="794b6-174">Att spara ett skript</span><span class="sxs-lookup"><span data-stu-id="794b6-174">To save a script</span></span>

<span data-ttu-id="794b6-175">Tryck på **CTRL + S** i verktygsfältet klickar du på den **spara** ikonen, eller på den **filen** -menyn klickar du på **spara**.</span><span class="sxs-lookup"><span data-stu-id="794b6-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="794b6-176">Spara och namnge ett skript</span><span class="sxs-lookup"><span data-stu-id="794b6-176">To save and name a script</span></span>

1. <span data-ttu-id="794b6-177">På den **filen** -menyn klickar du på **Spara som**.</span><span class="sxs-lookup"><span data-stu-id="794b6-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="794b6-178">Den **Spara som** visas dialogrutan.</span><span class="sxs-lookup"><span data-stu-id="794b6-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="794b6-179">I den **filnamn** anger du ett namn för filen.</span><span class="sxs-lookup"><span data-stu-id="794b6-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="794b6-180">I den **filformat** väljer du en filtyp.</span><span class="sxs-lookup"><span data-stu-id="794b6-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="794b6-181">Till exempel i den **filformat** väljer ' œPowerShell skript (\* .ps1)'.</span><span class="sxs-lookup"><span data-stu-id="794b6-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="794b6-182">Klicka på **Spara**.</span><span class="sxs-lookup"><span data-stu-id="794b6-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="794b6-183">För att spara ett skript i ASCII-kodning</span><span class="sxs-lookup"><span data-stu-id="794b6-183">To save a script in ASCII encoding</span></span>

<span data-ttu-id="794b6-184">Som standard sparas Windows PowerShell ISE nya skriptfiler (.ps1), skript datafiler (.psd1) och skriptfiler modul (.psm1) som Unicode (BigEndianUnicode) som standard. Â att spara ett skript i en annan kodning, till exempel ASCII (ANSI), använder den **spara** eller **SaveAs** metoder på det [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) objekt.</span><span class="sxs-lookup"><span data-stu-id="794b6-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="794b6-185">Följande kommando sparar ett nytt skript som MyScript.ps1 med ASCII-kodning.</span><span class="sxs-lookup"><span data-stu-id="794b6-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="794b6-186">Följande kommando ersätter den aktuella skriptfilen med en fil med samma namn men med ASCII-kodning.</span><span class="sxs-lookup"><span data-stu-id="794b6-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="794b6-187">Följande kommando hämtar kodning för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="794b6-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="794b6-188">Windows PowerShell ISE stöder följande alternativ för kodning: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 och standard.</span><span class="sxs-lookup"><span data-stu-id="794b6-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="794b6-189">Värdet för alternativet varierar beroende på systemet.</span><span class="sxs-lookup"><span data-stu-id="794b6-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="794b6-190">Windows PowerShell ISE inte ändra kodningen av skript som har skapats med andra program, även när du använder spara eller spara som-kommandon i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="794b6-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="794b6-191">Se även</span><span class="sxs-lookup"><span data-stu-id="794b6-191">See Also</span></span>

- [<span data-ttu-id="794b6-192">Utforska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="794b6-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)