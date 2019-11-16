---
ms.date: 08/14/2018
keywords: PowerShell, cmdlet
title: Skriv och kör skript i Windows PowerShell ISE
ms.openlocfilehash: be54e26965a6d2f1472059820080a6a06c47dd26
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117567"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="3ec58-103">Skriv och kör skript i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3ec58-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="3ec58-104">Den här artikeln beskriver hur du skapar, redigerar, kör och sparar skript i fönstret skript.</span><span class="sxs-lookup"><span data-stu-id="3ec58-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="3ec58-105">Så här skapar och kör du skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-105">How to create and run scripts</span></span>

<span data-ttu-id="3ec58-106">Du kan öppna och redigera Windows PowerShell-filer i skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="3ec58-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="3ec58-107">Specifika filtyper av intresse i Windows PowerShell är skriptfiler (. ps1), skriptfiler (. psd1) och filer för skript-modul (. psm1).</span><span class="sxs-lookup"><span data-stu-id="3ec58-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="3ec58-108">Dessa filtyper är syntax som är färgade i redigerings fönstret för skript.</span><span class="sxs-lookup"><span data-stu-id="3ec58-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="3ec58-109">Andra vanliga filtyper som du kan öppna i skript fönstret är konfigurationsfiler (. ps1xml), XML-filer och textfiler.</span><span class="sxs-lookup"><span data-stu-id="3ec58-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="3ec58-110">Windows PowerShell-körnings principen avgör om du kan köra skript och läsa in Windows PowerShell-profiler och konfigurationsfiler.</span><span class="sxs-lookup"><span data-stu-id="3ec58-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="3ec58-111">Standard körnings principen, som är begränsad, förhindrar att alla skript körs och förhindrar inläsning av profiler.</span><span class="sxs-lookup"><span data-stu-id="3ec58-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="3ec58-112">Om du vill ändra körnings principen så att profiler kan läsas in och användas, se [set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) och [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="3ec58-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="3ec58-113">Så här skapar du en ny skript fil</span><span class="sxs-lookup"><span data-stu-id="3ec58-113">To create a new script file</span></span>

<span data-ttu-id="3ec58-114">I verktygsfältet klickar du på **nytt**eller på **nytt**på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="3ec58-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="3ec58-115">Den skapade filen visas på fliken ny fil på fliken aktuell PowerShell. kom ihåg att PowerShell-flikarna bara visas när det finns fler än en.</span><span class="sxs-lookup"><span data-stu-id="3ec58-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="3ec58-116">Som standard skapas en fil av typen script (. ps1), men den kan sparas med ett nytt namn och tillägg.</span><span class="sxs-lookup"><span data-stu-id="3ec58-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="3ec58-117">Du kan skapa flera skriptfiler på samma PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="3ec58-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="3ec58-118">Öppna ett befintligt skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-118">To open an existing script</span></span>

<span data-ttu-id="3ec58-119">Klicka på **Öppna**i verktygsfältet, eller klicka på **Öppna**på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="3ec58-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="3ec58-120">I dialog rutan **Öppna** väljer du den fil som du vill öppna.</span><span class="sxs-lookup"><span data-stu-id="3ec58-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="3ec58-121">Den öppna filen visas på en ny flik.</span><span class="sxs-lookup"><span data-stu-id="3ec58-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="3ec58-122">Stänga en skript-flik</span><span class="sxs-lookup"><span data-stu-id="3ec58-122">To close a script tab</span></span>

<span data-ttu-id="3ec58-123">Klicka på ikonen **Stäng** (X) på fliken Arkiv som du vill stänga eller Välj menyn **Arkiv** och klicka på **Stäng**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="3ec58-124">Om filen har ändrats sedan den senast sparades uppmanas du att spara eller ta bort den.</span><span class="sxs-lookup"><span data-stu-id="3ec58-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="3ec58-125">Så här visar du sökvägen till filen</span><span class="sxs-lookup"><span data-stu-id="3ec58-125">To display the file path</span></span>

<span data-ttu-id="3ec58-126">Peka på fil namnet på fliken fil.</span><span class="sxs-lookup"><span data-stu-id="3ec58-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="3ec58-127">Den fullständigt kvalificerade sökvägen till skript filen visas i en knapp beskrivning.</span><span class="sxs-lookup"><span data-stu-id="3ec58-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="3ec58-128">Köra ett skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-128">To run a script</span></span>

<span data-ttu-id="3ec58-129">I verktygsfältet klickar du på **Kör skript**eller på **Arkiv** -menyn och sedan på **Kör**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="3ec58-130">Köra en del av ett skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-130">To run a portion of a script</span></span>

1. <span data-ttu-id="3ec58-131">I fönstret skript väljer du en del av ett skript.</span><span class="sxs-lookup"><span data-stu-id="3ec58-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="3ec58-132">På **Arkiv** -menyn klickar du på **Kör markering**eller på verktygsfältet klickar du på **Kör markering**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="3ec58-133">Stoppa ett skript som körs</span><span class="sxs-lookup"><span data-stu-id="3ec58-133">To stop a running script</span></span>

<span data-ttu-id="3ec58-134">Det finns flera sätt att stoppa ett skript som körs.</span><span class="sxs-lookup"><span data-stu-id="3ec58-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="3ec58-135">Klicka på **stoppa åtgärd** i verktygsfältet</span><span class="sxs-lookup"><span data-stu-id="3ec58-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="3ec58-136">Tryck på CTRL + BREAK</span><span class="sxs-lookup"><span data-stu-id="3ec58-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="3ec58-137">Välj menyn **Arkiv** och klicka på **stoppa åtgärd**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="3ec58-138">Tryck på **CTRL + c** fungerar även om inte en text är markerad, där **CTRL + C** mappar till kopierings funktionen för den markerade texten.</span><span class="sxs-lookup"><span data-stu-id="3ec58-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="3ec58-139">Skriva och redigera text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="3ec58-140">Du kan kopiera, klippa ut, klistra in, söka och ersätta text i skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="3ec58-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="3ec58-141">Du kan också ångra och göra om den senaste åtgärden som du nyss utförde.</span><span class="sxs-lookup"><span data-stu-id="3ec58-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="3ec58-142">Kortkommandona för dessa åtgärder är samma kortkommandon som används för alla Windows-program.</span><span class="sxs-lookup"><span data-stu-id="3ec58-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="3ec58-143">Ange text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="3ec58-144">Flytta markören till skript fönstret genom att klicka någonstans i skript fönstret eller genom att klicka på **gå till skript fönstret** i menyn **Visa** .</span><span class="sxs-lookup"><span data-stu-id="3ec58-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="3ec58-145">Skapa ett skript.</span><span class="sxs-lookup"><span data-stu-id="3ec58-145">Create a script.</span></span> <span data-ttu-id="3ec58-146">Syntax färgning och TABB-ifyllnad ger en mer omfattande redigerings upplevelse i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="3ec58-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="3ec58-147">Mer information om hur du använder funktionen för slut för ande av flikar finns [i skript fönstret och konsol fönstret](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) .</span><span class="sxs-lookup"><span data-stu-id="3ec58-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="3ec58-148">Hitta text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="3ec58-149">Om du vill söka efter text var som helst, trycker du på **CTRL + F** eller klickar på **Sök i skript**på **Redigera** -menyn.</span><span class="sxs-lookup"><span data-stu-id="3ec58-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="3ec58-150">Om du vill hitta text efter markören trycker du på **F3** eller på menyn **Redigera** klickar du på **Sök nästa i skript**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="3ec58-151">Om du vill hitta text före markören trycker du på **Shift + F3** eller på **Redigera** -menyn och klickar på **Sök föregående i skript**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="3ec58-152">Söka efter och ersätta text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="3ec58-153">Tryck på **CTRL + H** eller på **Redigera** -menyn, klicka på **Ersätt i skript**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="3ec58-154">Ange den text som du vill söka efter och ersättnings texten och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="3ec58-155">För att gå till en viss textrad i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="3ec58-156">Tryck på **CTRL + G** eller på **Redigera** -menyn i rutan skript och klicka på **gå till rad**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="3ec58-157">Ange ett rad nummer.</span><span class="sxs-lookup"><span data-stu-id="3ec58-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="3ec58-158">Kopiera text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="3ec58-159">I rutan skript väljer du den text som du vill kopiera.</span><span class="sxs-lookup"><span data-stu-id="3ec58-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="3ec58-160">Tryck på **CTRL + C** eller, i verktygsfältet, klicka på **Kopiera** -ikonen eller på **Redigera** -menyn och klicka på **Kopiera**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="3ec58-161">Klippa ut text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="3ec58-162">I rutan skript väljer du den text som du vill klippa ut.</span><span class="sxs-lookup"><span data-stu-id="3ec58-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="3ec58-163">Tryck på **CTRL + X** eller, i verktygsfältet, klicka på **Klipp ut** -ikonen eller på **Redigera** -menyn och klicka på **Klipp ut**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="3ec58-164">Klistra in text i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="3ec58-165">Tryck på **CTRL + V** eller, i verktygsfältet, klicka på ikonen **Klistra in** eller på **Redigera** -menyn och klicka på **Klistra in**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="3ec58-166">Ångra en åtgärd i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="3ec58-167">Tryck på **CTRL + Z** eller, i verktygsfältet, klicka på **Ångra** -ikonen eller på **Redigera** -menyn och klicka på **Ångra**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="3ec58-168">Göra om en åtgärd i skript fönstret</span><span class="sxs-lookup"><span data-stu-id="3ec58-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="3ec58-169">Tryck på **CTRL + Y** eller, i verktygsfältet, klicka på ikonen **gör** om eller på **Redigera** -menyn och klicka på **gör**om.</span><span class="sxs-lookup"><span data-stu-id="3ec58-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="3ec58-170">Så här sparar du ett skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-170">How to save a script</span></span>

<span data-ttu-id="3ec58-171">En asterisk visas bredvid skript namnet för att markera en fil som inte har sparats sedan den ändrades.</span><span class="sxs-lookup"><span data-stu-id="3ec58-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="3ec58-172">Asterisken försvinner när filen sparas.</span><span class="sxs-lookup"><span data-stu-id="3ec58-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="3ec58-173">Så här sparar du ett skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-173">To save a script</span></span>

<span data-ttu-id="3ec58-174">Tryck på **CTRL + S** eller, klicka på ikonen **Spara** i verktygsfältet, eller klicka på **Spara**på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="3ec58-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="3ec58-175">Spara och namnge ett skript</span><span class="sxs-lookup"><span data-stu-id="3ec58-175">To save and name a script</span></span>

1. <span data-ttu-id="3ec58-176">Klicka på **Spara som**på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="3ec58-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="3ec58-177">Dialog rutan **Spara som** visas.</span><span class="sxs-lookup"><span data-stu-id="3ec58-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="3ec58-178">Ange ett namn på filen i rutan **fil namn** .</span><span class="sxs-lookup"><span data-stu-id="3ec58-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="3ec58-179">I rutan fil **format** väljer du en filtyp.</span><span class="sxs-lookup"><span data-stu-id="3ec58-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="3ec58-180">I rutan **fil format** väljer du exempelvis PowerShell-skript (\*. ps1).</span><span class="sxs-lookup"><span data-stu-id="3ec58-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="3ec58-181">Klicka på **Spara**.</span><span class="sxs-lookup"><span data-stu-id="3ec58-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="3ec58-182">Så här sparar du ett skript i ASCII-kodning</span><span class="sxs-lookup"><span data-stu-id="3ec58-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="3ec58-183">Som standard sparar Windows PowerShell ISE nya skriptfiler (. ps1), skript data filer (. psd1) och skriptfiler (. psm1) som Unicode (BigEndianUnicode) som standard. Om du vill spara ett skript i en annan kodning, t. ex. ASCII (ANSI), använder du metoderna **Save** eller **savee** som på objektet [$psISE. CurrentFile](object-model/the-ise-object-model-hierarchy.md) .</span><span class="sxs-lookup"><span data-stu-id="3ec58-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="3ec58-184">Följande kommando sparar ett nytt skript som skript. ps1 med ASCII-kodning.</span><span class="sxs-lookup"><span data-stu-id="3ec58-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="3ec58-185">Följande kommando ersätter den aktuella skript filen med en fil med samma namn, men med ASCII-kodning.</span><span class="sxs-lookup"><span data-stu-id="3ec58-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="3ec58-186">Följande kommando hämtar kodningen för den aktuella filen.</span><span class="sxs-lookup"><span data-stu-id="3ec58-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="3ec58-187">Windows PowerShell ISE stöder följande kodnings alternativ: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 och default.</span><span class="sxs-lookup"><span data-stu-id="3ec58-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="3ec58-188">Värdet för standard alternativet varierar i systemet.</span><span class="sxs-lookup"><span data-stu-id="3ec58-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="3ec58-189">Windows PowerShell ISE ändrar inte kodningen för skriptfiler när du använder Spara-eller Spara som-kommandon.</span><span class="sxs-lookup"><span data-stu-id="3ec58-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ec58-190">Se även</span><span class="sxs-lookup"><span data-stu-id="3ec58-190">See Also</span></span>

- [<span data-ttu-id="3ec58-191">Utforska Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="3ec58-191">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
