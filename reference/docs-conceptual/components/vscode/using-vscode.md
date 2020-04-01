---
title: Använda Visual Studio Code för PowerShell-utveckling
description: Använda Visual Studio Code för PowerShell-utveckling
ms.date: 11/07/2019
ms.openlocfilehash: 8644aa7c648d649651ca679238e0b79ff35ac579
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500898"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="66075-103">Använda Visual Studio Code för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="66075-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="66075-104">[Visual Studio Code](https://code.visualstudio.com/) är en plattforms oberoende (Windows-, MacOS-och Linux-skript redigerare) från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="66075-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="66075-105">Tillsammans med [PowerShell-tillägget](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)ger det en omfattande och interaktiv skript redigerings upplevelse, vilket gör det enklare att skriva pålitliga PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="66075-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="66075-106">Visual Studio Code med PowerShell-tillägget är den rekommenderade redigeraren för att skriva PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="66075-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="66075-107">Det stöder följande PowerShell-versioner:</span><span class="sxs-lookup"><span data-stu-id="66075-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="66075-108">PowerShell 7 och uppåt</span><span class="sxs-lookup"><span data-stu-id="66075-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="66075-109">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="66075-109">PowerShell Core 6</span></span>
- <span data-ttu-id="66075-110">Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="66075-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="66075-111">Innan du börjar ska du kontrol lera att PowerShell finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="66075-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="66075-112">För moderna arbets belastningar på Windows, macOS och Linux, se följande länkar:</span><span class="sxs-lookup"><span data-stu-id="66075-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="66075-113">[Installera PowerShell på Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="66075-113">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="66075-114">[Installera PowerShell på macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="66075-114">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="66075-115">[Installera PowerShell i Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="66075-115">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="66075-116">För traditionella Windows PowerShell-arbetsbelastningar, se [Installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="66075-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="66075-117">Visual Studio Code är inte samma sak som [Visual Studio](https://visualstudio.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="66075-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66075-118">[Windows PowerShell ISE][ise] är också fortfarande tillgängligt för Windows, men det är inte längre vid utveckling av aktiva funktioner och fungerar inte med PowerShell 7 och uppåt eller PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="66075-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="66075-119">Som en leverans komponent i Windows fortsätter den att vara officiellt tillgänglig för säkerhets-och högprioriterade service-korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="66075-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="66075-120">Vi har för närvarande inga planer på att ta bort ISE från Windows.</span><span class="sxs-lookup"><span data-stu-id="66075-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="66075-121">Redigera med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66075-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="66075-122">Installera Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="66075-122">Install Visual Studio Code.</span></span> <span data-ttu-id="66075-123">Mer information finns i Översikt över [konfiguration av Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="66075-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="66075-124">Det finns installations anvisningar för varje plattform:</span><span class="sxs-lookup"><span data-stu-id="66075-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="66075-125">**Windows**: följ installations anvisningarna på sidan som [körs i Visual Studio Code på Windows](https://code.visualstudio.com/docs/setup/windows) .</span><span class="sxs-lookup"><span data-stu-id="66075-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="66075-126">**MacOS**: följ installationsinstruktionerna på sidan [med Visual Studio Code på MacOS](https://code.visualstudio.com/docs/setup/mac) .</span><span class="sxs-lookup"><span data-stu-id="66075-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="66075-127">**Linux**: följ installations anvisningarna på sidan som [Kör Visual Studio Code på Linux](https://code.visualstudio.com/docs/setup/linux) .</span><span class="sxs-lookup"><span data-stu-id="66075-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="66075-128">Installera PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="66075-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="66075-129">Starta Visual Studio Code-appen genom att skriva `code` i en konsol eller `code-insiders` om du har installerat Visual Studio Code-Insiders.</span><span class="sxs-lookup"><span data-stu-id="66075-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="66075-130">Starta **Quick Open** på Windows eller Linux genom att trycka på <kbd>CTRL</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="66075-131">I macOS trycker du på <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="66075-132">Skriv `ext install powershell` i snabb öppning och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="66075-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="66075-133">Vyn **tillägg** öppnas i sido fältet.</span><span class="sxs-lookup"><span data-stu-id="66075-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="66075-134">Välj PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="66075-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="66075-135">Du bör se en Visual Studio Code-skärm som liknar följande bild:</span><span class="sxs-lookup"><span data-stu-id="66075-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="66075-137">Klicka på knappen **Installera** i PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="66075-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="66075-138">När du har installerat klickar du på **Läs in**igen om du ser knappen **Installera** **igen.**</span><span class="sxs-lookup"><span data-stu-id="66075-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="66075-139">När Visual Studio Code har lästs in på nytt är du redo för redigering.</span><span class="sxs-lookup"><span data-stu-id="66075-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="66075-140">Om du till exempel vill skapa en ny fil klickar du på **fil > ny**.</span><span class="sxs-lookup"><span data-stu-id="66075-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="66075-141">Spara genom att klicka på **arkiv > Spara** och ange ett fil namn, till exempel `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="66075-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="66075-142">Stäng filen genom att klicka på `X` bredvid fil namnet.</span><span class="sxs-lookup"><span data-stu-id="66075-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="66075-143">Avsluta Visual Studio Code genom att stänga av **filen >** .</span><span class="sxs-lookup"><span data-stu-id="66075-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="66075-144">Installera PowerShell-tillägget på begränsade system</span><span class="sxs-lookup"><span data-stu-id="66075-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="66075-145">Vissa system har kon figurer ATS på ett sätt som kräver att alla kod-signaturer kontrol leras och kräver att PowerShell Editor-tjänster godkänns manuellt för att köras i systemet.</span><span class="sxs-lookup"><span data-stu-id="66075-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="66075-146">En grupprincip uppdatering som ändrar körnings principen är en sannolik orsak om du har installerat PowerShell-tillägget men får ett fel som:</span><span class="sxs-lookup"><span data-stu-id="66075-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="66075-147">Om du vill godkänna PowerShell Editor-tjänster och PowerShell-tillägget för Visual Studio Code manuellt öppnar du en PowerShell-kommandotolk och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="66075-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="66075-148">Du tillfrågas om **vill du köra program vara från den här ej betrodda utgivaren?**</span><span class="sxs-lookup"><span data-stu-id="66075-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="66075-149">Skriv `A` för att köra filen.</span><span class="sxs-lookup"><span data-stu-id="66075-149">Type `A` to run the file.</span></span> <span data-ttu-id="66075-150">Öppna sedan Visual Studio Code och kontrol lera att PowerShell-tillägget fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="66075-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="66075-151">Om du fortfarande har problem med att komma igång kan du berätta om [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="66075-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="66075-152">PowerShell-tillägget för Visual Studio Code stöder inte körning i begränsat språk läge.</span><span class="sxs-lookup"><span data-stu-id="66075-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="66075-153">Mer information finns i [GitHub ärende spårning som stöder](https://github.com/PowerShell/vscode-powershell/issues/606) .</span><span class="sxs-lookup"><span data-stu-id="66075-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="66075-154">Använda en äldre version av PowerShell-tillägget för Windows PowerShell v3 och v4</span><span class="sxs-lookup"><span data-stu-id="66075-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="66075-155">Även om det aktuella PowerShell-tillägget [slutade stödja v3 och v4](https://github.com/PowerShell/vscode-powershell/issues/1310), kan du fortfarande använda den senaste versionen av tillägget som gjorde.</span><span class="sxs-lookup"><span data-stu-id="66075-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="66075-156">Det kommer inte att finnas några ytterligare korrigeringar till den här äldre versionen av tillägget.</span><span class="sxs-lookup"><span data-stu-id="66075-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="66075-157">Det tillhandahålls "i befintligt skick", men det är tillgängligt för dig om du fortfarande använder Windows PowerShell v3 och Windows PowerShell v4.</span><span class="sxs-lookup"><span data-stu-id="66075-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="66075-158">Öppna först fönstret tillägg och Sök efter `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="66075-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="66075-159">Klicka sedan på kugg hjulet och välj **installera en annan version...** .</span><span class="sxs-lookup"><span data-stu-id="66075-159">Then click the gear and select **Install another version...**.</span></span>

![Installera en annan version...](media/using-vscode/install-another-version.png)

<span data-ttu-id="66075-161">Välj sedan den **`2020.1.0`** versionen.</span><span class="sxs-lookup"><span data-stu-id="66075-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="66075-162">Den här versionen av tillägget var den senaste versionen som stöd för v3 och v4.</span><span class="sxs-lookup"><span data-stu-id="66075-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="66075-163">Lägg också till följande inställning så att tilläggs versionen inte uppdateras automatiskt:</span><span class="sxs-lookup"><span data-stu-id="66075-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="66075-164">Även om det fungerar i forseeable-framtiden kan Visual Studio Code implementera en ändring som bryter mot den här versionen av tillägget.</span><span class="sxs-lookup"><span data-stu-id="66075-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="66075-165">På grund av detta, och avsaknad av support, rekommenderar vi antingen:</span><span class="sxs-lookup"><span data-stu-id="66075-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="66075-166">Ladda ned PowerShell 7 – som är en sida-vid-sida-installation till Windows PowerShell och fungerar bäst med PowerShell-tillägget</span><span class="sxs-lookup"><span data-stu-id="66075-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="66075-167">Uppgradera till Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="66075-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="66075-168">Avsnittet [Redigera med Visual Studio Code](#editing-with-visual-studio-code) i den här artikeln länkar till var de ska installeras.</span><span class="sxs-lookup"><span data-stu-id="66075-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="66075-169">Välja en version av PowerShell som ska användas med tillägget</span><span class="sxs-lookup"><span data-stu-id="66075-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="66075-170">Med PowerShell Core-installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en viss version av PowerShell med PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="66075-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="66075-171">Använd följande steg för att välja version:</span><span class="sxs-lookup"><span data-stu-id="66075-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="66075-172">Öppna **paletten kommando** i Windows eller Linux med <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="66075-173">I macOS använder du <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="66075-174">Sök efter **session**.</span><span class="sxs-lookup"><span data-stu-id="66075-174">Search for **Session**.</span></span>
1. <span data-ttu-id="66075-175">Klicka på **PowerShell: Visa session-menyn**.</span><span class="sxs-lookup"><span data-stu-id="66075-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="66075-176">Välj den version av PowerShell som du vill använda i listan, till exempel: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="66075-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66075-177">Den här funktionen söker efter några välkända sökvägar på olika operativ system för att identifiera installations platser för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66075-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="66075-178">Om du har installerat PowerShell på en icke-typisk plats kan det hända att den inte visas inlednings vis i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="66075-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="66075-179">Du kan utöka session-menyn genom [att lägga till egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="66075-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="66075-180">Det finns ett annat sätt att komma till session-menyn.</span><span class="sxs-lookup"><span data-stu-id="66075-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="66075-181">När en PowerShell-fil är öppen i redigeraren visas ett grönt versions nummer längst ned till höger.</span><span class="sxs-lookup"><span data-stu-id="66075-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="66075-182">Om du klickar på det här versions numret visas session-menyn.</span><span class="sxs-lookup"><span data-stu-id="66075-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="66075-183">Lägga till egna PowerShell-sökvägar i session-menyn</span><span class="sxs-lookup"><span data-stu-id="66075-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="66075-184">Du kan lägga till andra sökvägar för PowerShell-körbara filer till sessionen via [Visual Studio-kod inställningen](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="66075-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="66075-185">Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa en lista om den inte finns i `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="66075-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="66075-186">Varje objekt måste ha:</span><span class="sxs-lookup"><span data-stu-id="66075-186">Each item must have:</span></span>

- <span data-ttu-id="66075-187">`exePath`: sökvägen till `pwsh` eller `powershell` körbar fil.</span><span class="sxs-lookup"><span data-stu-id="66075-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="66075-188">`versionName`: den text som visas i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="66075-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="66075-189">Du kan ställa in standard versionen av PowerShell att använda `powershell.powerShellDefaultVersion` inställningen genom att ställa in den på texten som visas i session-menyn (kallas även `versionName` i den senaste inställningen):</span><span class="sxs-lookup"><span data-stu-id="66075-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="66075-190">När du har konfigurerat den här inställningen startar du om Visual Studio Code eller läser in det aktuella Visual Studio Code-fönstret från **kommando-paletten**. Skriv **Developer: Läs in igen**.</span><span class="sxs-lookup"><span data-stu-id="66075-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="66075-191">Om du öppnar session-menyn visas nu ytterligare PowerShell-versioner!</span><span class="sxs-lookup"><span data-stu-id="66075-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="66075-192">Om du skapar PowerShell från källa är det ett bra sätt att testa din lokala version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66075-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="66075-193">Konfigurations inställningar för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66075-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="66075-194">Först, om du inte är bekant med hur du ändrar inställningarna i Visual Studio Code, rekommenderar vi att du tittar i [Visual Studio Codes inställningar dokumentation](https://code.visualstudio.com/docs/getstarted/settings).</span><span class="sxs-lookup"><span data-stu-id="66075-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="66075-195">Genom att följa stegen i föregående stycke kan du lägga till konfigurations inställningar i `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="66075-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="66075-196">Om du inte vill att de här inställningarna ska påverka alla filtyper kan du också använda Visual Studio Code för konfigurationer på olika språk.</span><span class="sxs-lookup"><span data-stu-id="66075-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="66075-197">Skapa en språkspecifik inställning genom att lägga till inställningar i ett `[<language-name>]`s fält.</span><span class="sxs-lookup"><span data-stu-id="66075-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="66075-198">Exempel:</span><span class="sxs-lookup"><span data-stu-id="66075-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="66075-199">Mer information om fil kodning i Visual Studio Code finns i [förstå fil kodning](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="66075-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="66075-200">Ta också en titt på hur du kan [REPLIKERA ISE-upplevelsen i Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) för andra tips om hur du konfigurerar Visual Studio Code för PowerShell-redigering.</span><span class="sxs-lookup"><span data-stu-id="66075-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="66075-201">Felsöka med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66075-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="66075-202">Ingen fel sökning på arbets ytan</span><span class="sxs-lookup"><span data-stu-id="66075-202">No-workspace debugging</span></span>

<span data-ttu-id="66075-203">Från och med Visual Studio Code version 1,9 kan du felsöka PowerShell-skript utan att öppna mappen som innehåller PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="66075-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="66075-204">Öppna PowerShell-skriptfilen med **filen > öppna fil...** , ange en Bryt punkt på en rad, tryck på <kbd>F9</kbd>och tryck sedan på <kbd>F5</kbd> för att starta fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="66075-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="66075-205">Du bör se fönstret fel söknings åtgärder, vilket gör att du kan bryta i fel söknings programmet, steg, återuppta och stoppa fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="66075-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="66075-206">Fel sökning av arbets yta</span><span class="sxs-lookup"><span data-stu-id="66075-206">Workspace debugging</span></span>

<span data-ttu-id="66075-207">Fel sökning av arbets ytan avser fel sökning i kontexten för en mapp som du har öppnat i Visual Studio Code från menyn **Arkiv** med **Öppna mapp..** .. Mappen som du öppnar är vanligt vis din PowerShell-projektmapp och/eller roten för git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="66075-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="66075-208">Även i det här läget kan du börja felsöka det markerade PowerShell-skriptet genom att trycka på <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="66075-209">Med fel sökning av arbets yta kan du dock definiera flera fel söknings konfigurationer förutom att bara Felsöka den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="66075-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="66075-210">Vi kommer åt dem i en stund.</span><span class="sxs-lookup"><span data-stu-id="66075-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="66075-211">Följ de här stegen för att skapa en fel söknings konfigurations fil:</span><span class="sxs-lookup"><span data-stu-id="66075-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="66075-212">Öppna **fel söknings** vyn i Windows eller Linux genom att trycka på <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="66075-213">I macOS trycker du på <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="66075-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="66075-214">Klicka på länken "skapa en starta. JSON-fil".</span><span class="sxs-lookup"><span data-stu-id="66075-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="66075-215">Visual Studio Code anger att du **väljer miljö**.</span><span class="sxs-lookup"><span data-stu-id="66075-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="66075-216">Välj **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="66075-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="66075-217">Välj slutligen den typ av fel sökning som du vill använda:</span><span class="sxs-lookup"><span data-stu-id="66075-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="66075-218">**Starta aktuell fil** – starta och Felsök filen i det för tillfället aktiva redigerings fönstret</span><span class="sxs-lookup"><span data-stu-id="66075-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="66075-219">**Starta skript** – starta och Felsök den angivna filen eller kommandot</span><span class="sxs-lookup"><span data-stu-id="66075-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="66075-220">**Interaktiv session** – Felsök kommandon som körs från den integrerade konsolen</span><span class="sxs-lookup"><span data-stu-id="66075-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="66075-221">**Koppla** -koppla fel sökaren till en PowerShell-värd process som körs</span><span class="sxs-lookup"><span data-stu-id="66075-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="66075-222">Resultatet är att Visual Studio Code skapar en katalog och en fil `.vscode\launch.json` i roten i din arbetsytans mapp.</span><span class="sxs-lookup"><span data-stu-id="66075-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="66075-223">Den här platsen är den plats där fel söknings konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="66075-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="66075-224">Om filerna finns på en git-lagringsplats vill du vanligt vis bekräfta `launch.json`-filen.</span><span class="sxs-lookup"><span data-stu-id="66075-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="66075-225">Innehållet i `launch.json`-filen är:</span><span class="sxs-lookup"><span data-stu-id="66075-225">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="66075-226">Den här filen representerar vanliga fel söknings scenarier.</span><span class="sxs-lookup"><span data-stu-id="66075-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="66075-227">När du öppnar den här filen i redigeraren visas knappen **Lägg till konfiguration...** .</span><span class="sxs-lookup"><span data-stu-id="66075-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="66075-228">Du kan klicka på den här knappen för att lägga till fler PowerShell-felsöknings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="66075-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="66075-229">En användbar konfiguration för att lägga till är **PowerShell: starta skript**.</span><span class="sxs-lookup"><span data-stu-id="66075-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="66075-230">Med den här konfigurationen kan du ange en fil med valfria argument som ska startas när du trycker på <kbd>F5</kbd> oavsett vilken fil som för närvarande är aktiv i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="66075-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="66075-231">När du har upprättat fel söknings konfigurationen kan du välja vilken konfiguration du vill använda under en felsökningssession.</span><span class="sxs-lookup"><span data-stu-id="66075-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="66075-232">Välj en konfiguration i list rutan Felsök konfiguration i **fel söknings** verktygsfältets verktygsfält.</span><span class="sxs-lookup"><span data-stu-id="66075-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="66075-233">Användbara resurser</span><span class="sxs-lookup"><span data-stu-id="66075-233">Useful resources</span></span>

<span data-ttu-id="66075-234">Det finns några videor och blogg inlägg som kan vara till hjälp för att komma igång med PowerShell-tillägget för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="66075-234">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="66075-235">Videoklipp</span><span class="sxs-lookup"><span data-stu-id="66075-235">Videos</span></span>

- [<span data-ttu-id="66075-236">Använda Visual Studio Code som standard-PowerShell-redigerare</span><span class="sxs-lookup"><span data-stu-id="66075-236">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="66075-237">Visual Studio Code: djup gå in i fel sökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="66075-237">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="66075-238">Blogginlägg</span><span class="sxs-lookup"><span data-stu-id="66075-238">Blog posts</span></span>

- <span data-ttu-id="66075-239">[PowerShell-tillägg][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="66075-239">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="66075-240">[Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="66075-240">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="66075-241">[Fel sökning av Visual Studio Code-vägledning][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="66075-241">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="66075-242">[Felsöka PowerShell i Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="66075-242">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="66075-243">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="66075-243">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="66075-244">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="66075-244">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="66075-245">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="66075-245">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="66075-246">[Felsöka PowerShell-skript i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="66075-246">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="66075-247">[Felsöka PowerShell-skript i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="66075-247">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="66075-248">PowerShell-tillägg för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66075-248">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="66075-249">Du hittar PowerShell-tilläggets källkod på [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="66075-249">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="66075-250">Om du är intresse rad av att bidra, är pull-begäran ett stort uppskattat.</span><span class="sxs-lookup"><span data-stu-id="66075-250">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="66075-251">Följ tillsammans med [Developer-dokumentationen på GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) för att komma igång.</span><span class="sxs-lookup"><span data-stu-id="66075-251">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="66075-252">Felsöka PowerShell-tillägget för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="66075-252">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="66075-253">Om du får problem med att använda Visual Studio Code för att utveckla PowerShell-skript, kan du ta en titt på [fel söknings guiden på GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="66075-253">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
