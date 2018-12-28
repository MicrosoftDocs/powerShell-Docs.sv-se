---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Starta Windows Powershell
ms.assetid: 59b649a2-c90c-4cf4-bf95-a740c59148e7
ms.openlocfilehash: 9184e8b0e508610e7f4775f1032f3a69c93bb8c1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405351"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="ccb55-103">Starta Windows Powershell</span><span class="sxs-lookup"><span data-stu-id="ccb55-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="ccb55-104">PowerShell är en scripting motorn DLL-fil som är inbäddad i flera värdar.</span><span class="sxs-lookup"><span data-stu-id="ccb55-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="ccb55-105">De vanligaste värden startas är interaktiva kommandoraden PowerShell.exe och interaktiva Scripting Environment PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="ccb55-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="ccb55-106">Om du vill starta Windows PowerShell® på Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 och Windows 8, se [vanliga hanteringsuppgifter och navigering](https://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="ccb55-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="ccb55-107">Starta Windows PowerShell på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="ccb55-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="ccb55-108">Det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell Integrated Scripting Environment (ISE) på Windows® 7, Windows Server® 2008 R2 och Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="ccb55-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="ccb55-109">Den förklarar också hur du aktiverar valfri funktion för Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server® 2008 R2 och Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="ccb55-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="ccb55-110">Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3.0 eller Windows PowerShell 4.0, om tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="ccb55-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="ccb55-111">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="ccb55-111">From the Start Menu</span></span>

- <span data-ttu-id="ccb55-112">Klicka på **starta**, typ **PowerShell**, och klicka sedan på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="ccb55-113">Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klickar du på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="ccb55-114">I Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="ccb55-114">At the Command Prompt</span></span>

<span data-ttu-id="ccb55-115">I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell, skriver du:</span><span class="sxs-lookup"><span data-stu-id="ccb55-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="ccb55-116">Du kan också använda parametrarna för PowerShell.exe-programmet för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="ccb55-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="ccb55-117">Mer information finns i [PowerShell.exe-hjälpen](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="ccb55-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="ccb55-118">Med administrativa behörigheter (”Kör som administratör”)</span><span class="sxs-lookup"><span data-stu-id="ccb55-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="ccb55-119">Klicka på **starta**, typ **PowerShell**, högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="ccb55-120">Starta Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="ccb55-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="ccb55-121">Använd någon av följande metoder för att starta Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ccb55-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="ccb55-122">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="ccb55-122">From the Start Menu</span></span>

- <span data-ttu-id="ccb55-123">Klicka på **starta**, typ **ISE**, och klicka sedan på **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="ccb55-124">Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klickar du på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="ccb55-125">I Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="ccb55-125">At the Command Prompt</span></span>

<span data-ttu-id="ccb55-126">I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell, skriver du:</span><span class="sxs-lookup"><span data-stu-id="ccb55-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="ccb55-127">eller</span><span class="sxs-lookup"><span data-stu-id="ccb55-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="ccb55-128">Med administrativa behörigheter (”Kör som administratör”)</span><span class="sxs-lookup"><span data-stu-id="ccb55-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="ccb55-129">Klicka på **starta**, typ **ISE**, högerklicka på **Windows PowerShell ISE**, och klicka sedan på **kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="ccb55-130">Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="ccb55-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="ccb55-131">I Windows PowerShell 4.0 och Windows PowerShell 3.0, är Windows PowerShell ISE aktiverat som standard i alla versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="ccb55-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="ccb55-132">Om den inte redan är aktiverad, Windows Management Framework 4.0 eller Windows Management Framework 3.0 gör det möjligt.</span><span class="sxs-lookup"><span data-stu-id="ccb55-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="ccb55-133">I Windows PowerShell 2.0, är Windows PowerShell ISE aktiverat som standard på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="ccb55-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="ccb55-134">Det kan dock är en valfri funktion i Windows Server 2008 R2 och Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ccb55-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="ccb55-135">Följ anvisningarna nedan om du vill aktivera Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server 2008 R2 eller Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ccb55-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="ccb55-136">Aktivera Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="ccb55-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="ccb55-137">Starta Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="ccb55-137">Start Server Manager.</span></span>
2. <span data-ttu-id="ccb55-138">Klicka på **funktioner** och klicka sedan på **Lägg till funktioner**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="ccb55-139">I Välj funktioner klickar du på Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="ccb55-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="ccb55-140">Starta 32-bitarsversionen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ccb55-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="ccb55-141">När du installerar Windows PowerShell på en 64-bitarsdator **Windows PowerShell (x86)**, en 32-bitars version av Windows PowerShell är installerat förutom 64-bitarsversionen.</span><span class="sxs-lookup"><span data-stu-id="ccb55-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="ccb55-142">När du kör Windows PowerShell, körs 64-bitars version som standard.</span><span class="sxs-lookup"><span data-stu-id="ccb55-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="ccb55-143">Men du kan ibland behöva köra **Windows PowerShell (x86)**, t.ex. när du använder en modul som kräver 32-bitarsversionen eller när du ansluter via en fjärranslutning till en 32-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="ccb55-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="ccb55-144">Använd någon av följande procedurer för att starta en 32-bitars version av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ccb55-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="ccb55-145">I Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ccb55-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="ccb55-146">På den **starta** skärmen, Skriv **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="ccb55-147">Klicka på den **Windows PowerShell x86** panelen.</span><span class="sxs-lookup"><span data-stu-id="ccb55-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="ccb55-148">I **Serverhanteraren**, från den **verktyg** menyn och välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-149">Flytta markören till det övre högra hörnet, klicka på skrivbordet, **Search**, typ **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-150">Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ccb55-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="ccb55-151">I Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="ccb55-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="ccb55-152">På den **starta** skärmen, Skriv **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-153">I **Serverhanteraren**, från den **verktyg** menyn och välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-154">Flytta markören till det övre högra hörnet, klicka på skrivbordet, **Search**, typ **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-155">Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ccb55-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="ccb55-156">I Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="ccb55-156">In Windows® 8.1</span></span>

- <span data-ttu-id="ccb55-157">På den **starta** skärmen, Skriv **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="ccb55-158">Klicka på den **Windows PowerShell x86** panelen.</span><span class="sxs-lookup"><span data-stu-id="ccb55-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="ccb55-159">Om du kör [verktyg för fjärrserveradministration](https://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8.1 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn.</span><span class="sxs-lookup"><span data-stu-id="ccb55-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="ccb55-160">Välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-161">Flytta markören till det övre högra hörnet, klicka på skrivbordet, **Search**, typ **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-162">Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ccb55-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="ccb55-163">I Windows® 8</span><span class="sxs-lookup"><span data-stu-id="ccb55-163">In Windows® 8</span></span>

- <span data-ttu-id="ccb55-164">På den **starta** skärmen, flyttar markören till det övre högra hörnet, klickar du på **inställningar**, klickar du på **paneler**, och flyttar den **visa Administrationsverktyg** skjutreglaget till Ja.</span><span class="sxs-lookup"><span data-stu-id="ccb55-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="ccb55-165">Skriv **PowerShell** och klicka på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-166">Om du kör [verktyg för fjärrserveradministration](https://www.microsoft.com/download/details.aspx?id=28972) för Windows 8, kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn.</span><span class="sxs-lookup"><span data-stu-id="ccb55-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="ccb55-167">Välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-168">På den **starta** skärmen eller skrivbordet, Skriv **PowerShell (x86)** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="ccb55-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="ccb55-169">Ange via kommandoraden: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="ccb55-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>