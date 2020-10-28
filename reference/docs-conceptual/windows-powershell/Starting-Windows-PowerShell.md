---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Starta Windows Powershell
description: I den här artikeln förklaras hur du startar olika versioner av PowerShell.
ms.openlocfilehash: 47da7d85c9f7e6966a7f7e809c77979cd24cf129
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664015"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="adf4b-104">Starta Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="adf4b-104">Starting Windows PowerShell</span></span>

<span data-ttu-id="adf4b-105">Windows PowerShell är en skript motor `.DLL` som är inbäddad i flera värdar.</span><span class="sxs-lookup"><span data-stu-id="adf4b-105">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="adf4b-106">De vanligaste värdarna som du kommer igång är den interaktiva kommando raden `powershell.exe` och den interaktiva skript miljön `powershell_ise.exe` .</span><span class="sxs-lookup"><span data-stu-id="adf4b-106">The most common hosts you'll start are the interactive command-line `powershell.exe` and the Interactive Scripting Environment `powershell_ise.exe`.</span></span>

<span data-ttu-id="adf4b-107">För att starta Windows PowerShell &reg; på Windows server &reg; 2012 R2, Windows &reg; 8,1, Windows Server 2012 och Windows 8, se [vanliga hanterings uppgifter och navigering i Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="adf4b-107">To start Windows PowerShell&reg; on Windows Server&reg; 2012 R2, Windows&reg; 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="adf4b-108">PowerShell-kärnan har bytt namn till binär</span><span class="sxs-lookup"><span data-stu-id="adf4b-108">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="adf4b-109">PowerShell Core, som kallas PowerShell, är version 6 och högre som är öppen källkod och använder .NET Core.</span><span class="sxs-lookup"><span data-stu-id="adf4b-109">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="adf4b-110">Versioner som stöds finns i Windows, macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="adf4b-110">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="adf4b-111">Från och med PowerShell 6 ändrades PowerShell-binärfilen namn `pwsh.exe` för Windows och `pwsh` MacOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="adf4b-111">Beginning in PowerShell 6, the PowerShell binary was renamed `pwsh.exe` for Windows and `pwsh` for macOS and Linux.</span></span> <span data-ttu-id="adf4b-112">Du kan starta PowerShell Preview-versioner med `pwsh-preview` .</span><span class="sxs-lookup"><span data-stu-id="adf4b-112">You can start PowerShell preview versions using `pwsh-preview`.</span></span> <span data-ttu-id="adf4b-113">Mer information finns i [Vad är nytt i PowerShell Core 6,0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) och [om pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh).</span><span class="sxs-lookup"><span data-stu-id="adf4b-113">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh).</span></span>

<span data-ttu-id="adf4b-114">Använd följande länkar för att hitta cmdlet-referensen och installations dokumentationen för PowerShell 7:</span><span class="sxs-lookup"><span data-stu-id="adf4b-114">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="adf4b-115">Dokument</span><span class="sxs-lookup"><span data-stu-id="adf4b-115">Document</span></span> | <span data-ttu-id="adf4b-116">Länk</span><span class="sxs-lookup"><span data-stu-id="adf4b-116">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="adf4b-117">Cmdlet-referens</span><span class="sxs-lookup"><span data-stu-id="adf4b-117">Cmdlet reference</span></span> | [<span data-ttu-id="adf4b-118">PowerShell Module Browser</span><span class="sxs-lookup"><span data-stu-id="adf4b-118">PowerShell Module Browser</span></span>](/powershell/module/) |
| <span data-ttu-id="adf4b-119">Windows-installation</span><span class="sxs-lookup"><span data-stu-id="adf4b-119">Windows installation</span></span> | [<span data-ttu-id="adf4b-120">Installera PowerShell Core i Windows</span><span class="sxs-lookup"><span data-stu-id="adf4b-120">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows) |
| <span data-ttu-id="adf4b-121">macOS-installation</span><span class="sxs-lookup"><span data-stu-id="adf4b-121">macOS installation</span></span> | [<span data-ttu-id="adf4b-122">Installera PowerShell Core på macOS</span><span class="sxs-lookup"><span data-stu-id="adf4b-122">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos) |
| <span data-ttu-id="adf4b-123">Linux-installation</span><span class="sxs-lookup"><span data-stu-id="adf4b-123">Linux installation</span></span> | [<span data-ttu-id="adf4b-124">Installera PowerShell Core på Linux</span><span class="sxs-lookup"><span data-stu-id="adf4b-124">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux) |

<span data-ttu-id="adf4b-125">Information om hur du visar innehåll för andra PowerShell-versioner finns i [så här använder du PowerShell-dokumentationen](../how-to-use-docs.md).</span><span class="sxs-lookup"><span data-stu-id="adf4b-125">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="adf4b-126">Starta Windows PowerShell i tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="adf4b-126">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="adf4b-127">I det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell ISE (Integrated Scripting Environment) på Windows &reg; 7, Windows Server &reg; 2008 R2 och Windows Server &reg; 2008.</span><span class="sxs-lookup"><span data-stu-id="adf4b-127">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows&reg; 7, Windows Server&reg; 2008 R2, and Windows Server&reg; 2008.</span></span> <span data-ttu-id="adf4b-128">Den innehåller också information om hur du aktiverar den valfria funktionen för Windows PowerShell ISE i Windows PowerShell 2,0 på Windows Server &reg; 2008 R2 och Windows Server &reg; 2008.</span><span class="sxs-lookup"><span data-stu-id="adf4b-128">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server&reg; 2008 R2 and Windows Server&reg; 2008.</span></span>

<span data-ttu-id="adf4b-129">Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3,0 eller Windows PowerShell 4,0, där det är tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="adf4b-129">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="adf4b-130">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="adf4b-130">From the Start Menu</span></span>

- <span data-ttu-id="adf4b-131">Klicka på **Start** , Skriv **PowerShell** och klicka sedan på **Windows PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-131">Click **Start** , type **PowerShell** , and then click **Windows PowerShell** .</span></span>
- <span data-ttu-id="adf4b-132">Gå till **Start** -menyn, klicka på **Start** , klicka på **alla program** , klicka på **tillbehör** , klicka på **Windows PowerShell** -mappen och klicka sedan på **Windows PowerShell** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-132">From the **Start** menu, click **Start** , click **All Programs** , click **Accessories** , click the **Windows PowerShell** folder, and then click **Windows PowerShell** .</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="adf4b-133">I kommando tolken</span><span class="sxs-lookup"><span data-stu-id="adf4b-133">At the Command Prompt</span></span>

<span data-ttu-id="adf4b-134">I **cmd.exe** , Windows powershell eller Windows PowerShell ISE startar du Windows PowerShell genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="adf4b-134">In **cmd.exe** , Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="adf4b-135">Du kan också använda parametrarna i `powershell.exe` programmet för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="adf4b-135">You can also use the parameters of the `powershell.exe` program to customize the session.</span></span> <span data-ttu-id="adf4b-136">Mer information finns i [PowerShell.exe Command-Line hjälp](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span><span class="sxs-lookup"><span data-stu-id="adf4b-136">For more information, see [PowerShell.exe Command-Line Help](/powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_exe).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="adf4b-137">Med administratörs behörighet (kör som administratör)</span><span class="sxs-lookup"><span data-stu-id="adf4b-137">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="adf4b-138">Klicka på **Start** , Skriv **PowerShell** , högerklicka på **Windows PowerShell** och klicka sedan på **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-138">Click **Start** , type **PowerShell** , right-click **Windows PowerShell** , and then click **Run as administrator** .</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="adf4b-139">Så här startar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="adf4b-139">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="adf4b-140">Använd någon av följande metoder för att starta Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="adf4b-140">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="adf4b-141">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="adf4b-141">From the Start Menu</span></span>

- <span data-ttu-id="adf4b-142">Klicka på **Start** , Skriv **ISE** och klicka sedan på **Windows PowerShell ISE** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-142">Click **Start** , type **ISE** , and then click **Windows PowerShell ISE** .</span></span>
- <span data-ttu-id="adf4b-143">Gå till **Start** -menyn, klicka på **Start** , klicka på **alla program** , klicka på **tillbehör** , klicka på **Windows PowerShell** -mappen och klicka sedan på **Windows PowerShell ISE** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-143">From the **Start** menu, click **Start** , click **All Programs** , click **Accessories** , click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE** .</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="adf4b-144">I kommando tolken</span><span class="sxs-lookup"><span data-stu-id="adf4b-144">At the Command Prompt</span></span>

<span data-ttu-id="adf4b-145">I `cmd.exe` , Windows PowerShell eller Windows PowerShell ISE, för att starta Windows PowerShell, skriver du:</span><span class="sxs-lookup"><span data-stu-id="adf4b-145">In `cmd.exe`, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="adf4b-146">eller</span><span class="sxs-lookup"><span data-stu-id="adf4b-146">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="adf4b-147">Med administratörs behörighet (kör som administratör)</span><span class="sxs-lookup"><span data-stu-id="adf4b-147">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="adf4b-148">Klicka på **Start** , Skriv **ISE** , högerklicka på **Windows PowerShell ISE** och klicka sedan på **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-148">Click **Start** , type **ISE** , right-click **Windows PowerShell ISE** , and then click **Run as administrator** .</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="adf4b-149">Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="adf4b-149">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="adf4b-150">I Windows PowerShell 4,0 och Windows PowerShell 3,0 är Windows PowerShell ISE aktiverat som standard i alla versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="adf4b-150">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="adf4b-151">Om den inte redan är aktive rad kan du använda Windows Management Framework 4,0 eller Windows Management Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="adf4b-151">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="adf4b-152">I Windows PowerShell 2,0 är Windows PowerShell ISE aktiverat som standard i Windows 7.</span><span class="sxs-lookup"><span data-stu-id="adf4b-152">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="adf4b-153">Men på Windows Server 2008 R2 och Windows Server 2008 är det en valfri funktion.</span><span class="sxs-lookup"><span data-stu-id="adf4b-153">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="adf4b-154">Använd följande procedur om du vill aktivera Windows PowerShell ISE i Windows PowerShell 2,0 på Windows Server 2008 R2 eller Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="adf4b-154">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="adf4b-155">Aktivera Windows PowerShell ISE (Integrated Scripting Environment)</span><span class="sxs-lookup"><span data-stu-id="adf4b-155">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="adf4b-156">Starta Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="adf4b-156">Start Server Manager.</span></span>
2. <span data-ttu-id="adf4b-157">Klicka på **funktioner** och sedan på **Lägg till funktioner** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-157">Click **Features** and then click **Add Features** .</span></span>
3. <span data-ttu-id="adf4b-158">I Välj funktioner klickar du på Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="adf4b-158">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="adf4b-159">Starta 32-bitars versionen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="adf4b-159">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="adf4b-160">När du installerar Windows PowerShell på en 64-bitars dator installeras **Windows PowerShell (x86)** och en 32-bitars version av Windows PowerShell installeras förutom 64-bitars versionen.</span><span class="sxs-lookup"><span data-stu-id="adf4b-160">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)** , a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="adf4b-161">När du kör Windows PowerShell körs 64-bitars versionen som standard.</span><span class="sxs-lookup"><span data-stu-id="adf4b-161">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="adf4b-162">Du kan dock ibland behöva köra **Windows PowerShell (x86)** , till exempel när du använder en modul som kräver 32-bitars versionen eller när du ansluter fjärran slutet till en 32-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="adf4b-162">However, you might occasionally need to run **Windows PowerShell (x86)** , such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="adf4b-163">Använd någon av följande procedurer för att starta en 32-bitars version av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="adf4b-163">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-serverreg-2012-r2"></a><span data-ttu-id="adf4b-164">I Windows Server &reg; 2012 R2</span><span class="sxs-lookup"><span data-stu-id="adf4b-164">In Windows Server&reg; 2012 R2</span></span>

- <span data-ttu-id="adf4b-165">Skriv **Windows PowerShell (x86)** på **Start** skärmen.</span><span class="sxs-lookup"><span data-stu-id="adf4b-165">On the **Start** screen, type **Windows PowerShell (x86)** .</span></span> <span data-ttu-id="adf4b-166">Klicka på **Windows PowerShell x86** -panelen.</span><span class="sxs-lookup"><span data-stu-id="adf4b-166">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="adf4b-167">I **Serverhanteraren** väljer du **Windows PowerShell (x86)** från **verktyg** -menyn.</span><span class="sxs-lookup"><span data-stu-id="adf4b-167">In **Server Manager** , from the **Tools** menu, select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-168">Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök** , Skriv **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-168">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell x86** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-169">Via kommando rad anger du: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="adf4b-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-serverreg-2012"></a><span data-ttu-id="adf4b-170">I Windows Server &reg; 2012</span><span class="sxs-lookup"><span data-stu-id="adf4b-170">In Windows Server&reg; 2012</span></span>

- <span data-ttu-id="adf4b-171">På **Start** skärmen skriver du **PowerShell** och klickar sedan på **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-171">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-172">I **Serverhanteraren** väljer du **Windows PowerShell (x86)** från **verktyg** -menyn.</span><span class="sxs-lookup"><span data-stu-id="adf4b-172">In **Server Manager** , from the **Tools** menu, select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-173">Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök** , Skriv **PowerShell** och klicka sedan på **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-173">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-174">Via kommando rad anger du: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="adf4b-174">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windowsreg-81"></a><span data-ttu-id="adf4b-175">I Windows &reg; 8,1</span><span class="sxs-lookup"><span data-stu-id="adf4b-175">In Windows&reg; 8.1</span></span>

- <span data-ttu-id="adf4b-176">Skriv **Windows PowerShell (x86)** på **Start** skärmen.</span><span class="sxs-lookup"><span data-stu-id="adf4b-176">On the **Start** screen, type **Windows PowerShell (x86)** .</span></span> <span data-ttu-id="adf4b-177">Klicka på **Windows PowerShell x86** -panelen.</span><span class="sxs-lookup"><span data-stu-id="adf4b-177">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="adf4b-178">Om du kör [verktyg för fjärrserveradministration](https://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8,1 kan du också öppna Windows PowerShell x86 från menyn **Server ManagerTools** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-178">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="adf4b-179">Välj **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-179">Select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-180">Flytta markören till det övre högra hörnet på Skriv bordet, klicka på **Sök** , Skriv **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-180">On the desktop, move the cursor to the upper right corner, click **Search** , type **PowerShell x86** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-181">Via kommando rad anger du: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="adf4b-181">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windowsreg-8"></a><span data-ttu-id="adf4b-182">I Windows &reg; 8</span><span class="sxs-lookup"><span data-stu-id="adf4b-182">In Windows&reg; 8</span></span>

- <span data-ttu-id="adf4b-183">På **Start** skärmen flyttar du markören till det övre högra hörnet, klickar på **Inställningar** , klickar på **paneler** och flyttar sedan skjutreglaget **Visa administrations verktyg** till **Ja** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-183">On the **Start** screen, move the cursor to the upper right corner, click **Settings** , click **Tiles** , and then move the **Show Administrative Tools** slider to **Yes** .</span></span> <span data-ttu-id="adf4b-184">Skriv sedan **PowerShell** och klicka på **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-184">Then, type **PowerShell** and click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-185">Om du kör [verktyg för fjärrserveradministration](https://www.microsoft.com/download/details.aspx?id=28972) för Windows 8 kan du också öppna Windows PowerShell x86 från menyn **Server ManagerTools** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-185">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="adf4b-186">Välj **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-186">Select **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-187">Skriv **PowerShell (x86)** på **Start** skärmen eller Skriv bordet och klicka sedan på **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="adf4b-187">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)** .</span></span>
- <span data-ttu-id="adf4b-188">Via kommando rad anger du: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="adf4b-188">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
