---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Starta Windows Powershell
ms.openlocfilehash: 32ed85510899ea239c9dc332a023554ce9b53e47
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810444"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="2fe90-103">Starta Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="2fe90-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="2fe90-104">Windows PowerShell är en skript motor `.DLL` som är inbäddad i flera värdar.</span><span class="sxs-lookup"><span data-stu-id="2fe90-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="2fe90-105">De vanligaste värdarna som du kommer igång är de interaktiva kommando rads **PowerShell. exe** och den interaktiva skript miljön **powershell_ise. exe**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="2fe90-106">För att starta Windows PowerShell® på Windows Server® 2012 R2, Windows® 8,1, Windows Server 2012 och Windows 8, se [vanliga hanterings uppgifter och navigering i Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="2fe90-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="2fe90-107">PowerShell-kärnan har bytt namn till binär</span><span class="sxs-lookup"><span data-stu-id="2fe90-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="2fe90-108">PowerShell Core, som kallas PowerShell, är version 6 och högre som är öppen källkod och använder .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2fe90-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="2fe90-109">Versioner som stöds finns i Windows, macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="2fe90-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="2fe90-110">Från och med PowerShell 6 har PowerShell-binärfilen bytt namn till **pwsh. exe** för Windows och **pwsh** för MacOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="2fe90-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="2fe90-111">Du kan starta PowerShell Preview-versioner med **pwsh-Preview**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="2fe90-112">Mer information finns i [Vad är nytt i PowerShell Core 6,0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) och [om pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="2fe90-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="2fe90-113">Använd följande länkar för att hitta cmdlet-referensen och installations dokumentationen för PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="2fe90-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="2fe90-114">Dokument</span><span class="sxs-lookup"><span data-stu-id="2fe90-114">Document</span></span> | <span data-ttu-id="2fe90-115">Länk</span><span class="sxs-lookup"><span data-stu-id="2fe90-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="2fe90-116">Cmdlet-referens</span><span class="sxs-lookup"><span data-stu-id="2fe90-116">Cmdlet reference</span></span> | [<span data-ttu-id="2fe90-117">PowerShell Module Browser</span><span class="sxs-lookup"><span data-stu-id="2fe90-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="2fe90-118">Windows-installation</span><span class="sxs-lookup"><span data-stu-id="2fe90-118">Windows installation</span></span> | [<span data-ttu-id="2fe90-119">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="2fe90-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="2fe90-120">macOS-installation</span><span class="sxs-lookup"><span data-stu-id="2fe90-120">macOS installation</span></span> | [<span data-ttu-id="2fe90-121">Installera PowerShell Core på macOS</span><span class="sxs-lookup"><span data-stu-id="2fe90-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="2fe90-122">Linux-installation</span><span class="sxs-lookup"><span data-stu-id="2fe90-122">Linux installation</span></span> | [<span data-ttu-id="2fe90-123">Installera PowerShell Core på Linux</span><span class="sxs-lookup"><span data-stu-id="2fe90-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="2fe90-124">Information om hur du visar innehåll för andra PowerShell-versioner finns i [så här använder du PowerShell-dokumentationen](../how-to-use-docs.md).</span><span class="sxs-lookup"><span data-stu-id="2fe90-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="2fe90-125">Starta Windows PowerShell i tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="2fe90-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="2fe90-126">I det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell ISE (Integrated Scripting Environment) på Windows® 7, Windows Server® 2008 R2 och Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="2fe90-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="2fe90-127">Den innehåller också information om hur du aktiverar den valfria funktionen för Windows PowerShell ISE i Windows PowerShell 2,0 på Windows Server® 2008 R2 och Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="2fe90-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="2fe90-128">Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3,0 eller Windows PowerShell 4,0, där det är tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="2fe90-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="2fe90-129">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="2fe90-129">From the Start Menu</span></span>

- <span data-ttu-id="2fe90-130">Klicka på **Start**, Skriv **PowerShell**och klicka sedan på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="2fe90-131">Gå till **Start** -menyn, klicka på **Start**, klicka på **alla program**, klicka på **tillbehör**, klicka på **Windows PowerShell** -mappen och klicka sedan på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="2fe90-132">I kommando tolken</span><span class="sxs-lookup"><span data-stu-id="2fe90-132">At the Command Prompt</span></span>

<span data-ttu-id="2fe90-133">I **cmd. exe**, Windows PowerShell eller Windows PowerShell ISE startar du Windows PowerShell genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="2fe90-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="2fe90-134">Du kan också använda parametrarna för **PowerShell. exe** -programmet för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="2fe90-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="2fe90-135">Mer information finns i [kommando rads hjälpen för PowerShell. exe](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span><span class="sxs-lookup"><span data-stu-id="2fe90-135">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="2fe90-136">Med administratörs behörighet (kör som administratör)</span><span class="sxs-lookup"><span data-stu-id="2fe90-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="2fe90-137">Klicka på **Start**, Skriv **PowerShell**, högerklicka på **Windows PowerShell**och klicka sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="2fe90-138">Så här startar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="2fe90-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="2fe90-139">Använd någon av följande metoder för att starta Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="2fe90-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="2fe90-140">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="2fe90-140">From the Start Menu</span></span>

- <span data-ttu-id="2fe90-141">Klicka på **Start**, Skriv **ISE**och klicka sedan på **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="2fe90-142">Gå till **Start** -menyn, klicka på **Start**, klicka på **alla program**, klicka på **tillbehör**, klicka på **Windows PowerShell** -mappen och klicka sedan på **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="2fe90-143">I kommando tolken</span><span class="sxs-lookup"><span data-stu-id="2fe90-143">At the Command Prompt</span></span>

<span data-ttu-id="2fe90-144">I **cmd. exe**, Windows PowerShell eller Windows PowerShell ISE startar du Windows PowerShell genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="2fe90-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="2fe90-145">eller</span><span class="sxs-lookup"><span data-stu-id="2fe90-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="2fe90-146">Med administratörs behörighet (kör som administratör)</span><span class="sxs-lookup"><span data-stu-id="2fe90-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="2fe90-147">Klicka på **Start**, Skriv **ISE**, högerklicka på **Windows PowerShell ISE**och klicka sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="2fe90-148">Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="2fe90-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="2fe90-149">I Windows PowerShell 4,0 och Windows PowerShell 3,0 är Windows PowerShell ISE aktiverat som standard i alla versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="2fe90-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="2fe90-150">Om den inte redan är aktive rad kan du använda Windows Management Framework 4,0 eller Windows Management Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="2fe90-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="2fe90-151">I Windows PowerShell 2,0 är Windows PowerShell ISE aktiverat som standard i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2fe90-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="2fe90-152">Men på Windows Server 2008 R2 och Windows Server 2008 är det en valfri funktion.</span><span class="sxs-lookup"><span data-stu-id="2fe90-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="2fe90-153">Använd följande procedur om du vill aktivera Windows PowerShell ISE i Windows PowerShell 2,0 på Windows Server 2008 R2 eller Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="2fe90-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="2fe90-154">Aktivera Windows PowerShell ISE (Integrated Scripting Environment)</span><span class="sxs-lookup"><span data-stu-id="2fe90-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="2fe90-155">Starta Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="2fe90-155">Start Server Manager.</span></span>
2. <span data-ttu-id="2fe90-156">Klicka på **funktioner** och sedan på **Lägg till funktioner**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="2fe90-157">I Välj funktioner klickar du på Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="2fe90-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="2fe90-158">Starta 32-bitars versionen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2fe90-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="2fe90-159">När du installerar Windows PowerShell på en 64-bitars dator installeras **Windows PowerShell (x86)** och en 32-bitars version av Windows PowerShell installeras förutom 64-bitars versionen.</span><span class="sxs-lookup"><span data-stu-id="2fe90-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="2fe90-160">När du kör Windows PowerShell körs 64-bitars versionen som standard.</span><span class="sxs-lookup"><span data-stu-id="2fe90-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="2fe90-161">Du kan dock ibland behöva köra **Windows PowerShell (x86)**, till exempel när du använder en modul som kräver 32-bitars versionen eller när du ansluter fjärran slutet till en 32-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="2fe90-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="2fe90-162">Använd någon av följande procedurer för att starta en 32-bitars version av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fe90-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="2fe90-163">I Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2fe90-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="2fe90-164">Skriv **Windows PowerShell (x86)** på **Start** skärmen.</span><span class="sxs-lookup"><span data-stu-id="2fe90-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="2fe90-165">Klicka på **Windows PowerShell x86** -panelen.</span><span class="sxs-lookup"><span data-stu-id="2fe90-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="2fe90-166">I **Serverhanteraren**väljer du **Windows PowerShell (x86)** från **verktyg** -menyn.</span><span class="sxs-lookup"><span data-stu-id="2fe90-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-167">Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök**, Skriv **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-168">Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2fe90-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="2fe90-169">I Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="2fe90-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="2fe90-170">På **Start** skärmen skriver du **PowerShell** och klickar sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-171">I **Serverhanteraren**väljer du **Windows PowerShell (x86)** från **verktyg** -menyn.</span><span class="sxs-lookup"><span data-stu-id="2fe90-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-172">Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök**, Skriv **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-173">Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2fe90-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="2fe90-174">I Windows® 8,1</span><span class="sxs-lookup"><span data-stu-id="2fe90-174">In Windows® 8.1</span></span>

- <span data-ttu-id="2fe90-175">Skriv **Windows PowerShell (x86)** på **Start** skärmen.</span><span class="sxs-lookup"><span data-stu-id="2fe90-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="2fe90-176">Klicka på **Windows PowerShell x86** -panelen.</span><span class="sxs-lookup"><span data-stu-id="2fe90-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="2fe90-177">Om du kör [verktyg för fjärrserveradministration](https://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8,1 kan du också öppna Windows PowerShell x86 från menyn **Server ManagerTools** .</span><span class="sxs-lookup"><span data-stu-id="2fe90-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="2fe90-178">Välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-179">Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök**, Skriv **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-180">Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2fe90-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="2fe90-181">I Windows® 8</span><span class="sxs-lookup"><span data-stu-id="2fe90-181">In Windows® 8</span></span>

- <span data-ttu-id="2fe90-182">På **Start** skärmen flyttar du markören till det övre högra hörnet, klickar på **Inställningar**, klickar på **paneler**och flyttar sedan skjutreglaget **Visa administrations verktyg** till **Ja**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="2fe90-183">Skriv sedan **PowerShell** och klicka på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-184">Om du kör [verktyg för fjärrserveradministration](https://www.microsoft.com/download/details.aspx?id=28972) för Windows 8 kan du också öppna Windows PowerShell x86 från menyn **Server ManagerTools** .</span><span class="sxs-lookup"><span data-stu-id="2fe90-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="2fe90-185">Välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-186">Skriv **PowerShell (x86)** på **Start** skärmen eller Skriv bordet och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="2fe90-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2fe90-187">Via kommando rad anger du:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2fe90-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
