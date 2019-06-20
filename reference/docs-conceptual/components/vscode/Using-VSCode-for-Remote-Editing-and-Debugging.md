---
title: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
description: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263979"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="47af3-103">Använda Visual Studio Code för att fjärredigera och fjärrfelsöka</span><span class="sxs-lookup"><span data-stu-id="47af3-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="47af3-104">För dig som är bekanta med ISE, du kanske kommer ihåg att du kan köra `psedit file.ps1` från integrerad konsol för att öppna filer – lokal eller fjärransluten - Högerklicka i ISE.</span><span class="sxs-lookup"><span data-stu-id="47af3-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="47af3-105">Den här funktionen är också tillgänglig i PowerShell-tillägget för VSCode.</span><span class="sxs-lookup"><span data-stu-id="47af3-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="47af3-106">Den här guiden visar hur du gör den.</span><span class="sxs-lookup"><span data-stu-id="47af3-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47af3-107">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="47af3-107">Prerequisites</span></span>

<span data-ttu-id="47af3-108">Den här guiden förutsätter att du har:</span><span class="sxs-lookup"><span data-stu-id="47af3-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="47af3-109">en fjärransluten resurs (t.ex.: en virtuell dator, en behållare) att du har åtkomst till</span><span class="sxs-lookup"><span data-stu-id="47af3-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="47af3-110">PowerShell som körs på den och värddatorn</span><span class="sxs-lookup"><span data-stu-id="47af3-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="47af3-111">VSCode och PowerShell-tillägget för VSCode</span><span class="sxs-lookup"><span data-stu-id="47af3-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="47af3-112">Den här funktionen fungerar i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="47af3-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="47af3-113">Den här funktionen fungerar även när du ansluter till en fjärrdator via WinRM, PowerShell Direct eller SSH.</span><span class="sxs-lookup"><span data-stu-id="47af3-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="47af3-114">Om du vill använda SSH, men använder Windows, Kolla in den [Win32-versionen av SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="47af3-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47af3-115">Den `Open-EditorFile` och `psedit` kommandona fungerar bara den **PowerShell integrerad konsol** som skapas av PowerShell-tillägget för VSCode.</span><span class="sxs-lookup"><span data-stu-id="47af3-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="47af3-116">Exempel på användning</span><span class="sxs-lookup"><span data-stu-id="47af3-116">Usage examples</span></span>

<span data-ttu-id="47af3-117">De här exemplen visar remote redigering och felsökning från en MacBook Pro för en Ubuntu-VM som körs i Azure.</span><span class="sxs-lookup"><span data-stu-id="47af3-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="47af3-118">Processen är identiska på Windows.</span><span class="sxs-lookup"><span data-stu-id="47af3-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="47af3-119">Lokal fil Redigera med öppen EditorFile</span><span class="sxs-lookup"><span data-stu-id="47af3-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="47af3-120">Med PowerShell-tillägget för VSCode igång och integrerad PowerShell-konsolen öppnas, vi kan skriva `Open-EditorFile foo.ps1` eller `psedit foo.ps1` att öppna lokala foo.ps1 fil direkt i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="47af3-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Öppna EditorFile foo.ps1 arbetar lokalt](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="47af3-122">Filen `foo.ps1` måste redan finnas.</span><span class="sxs-lookup"><span data-stu-id="47af3-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="47af3-123">Därifrån kan vi:</span><span class="sxs-lookup"><span data-stu-id="47af3-123">From there, we can:</span></span>

- <span data-ttu-id="47af3-124">Lägga till brytpunkter fästmarginalen</span><span class="sxs-lookup"><span data-stu-id="47af3-124">Add breakpoints to the gutter</span></span>

  ![att lägga till brytpunkt till fästmarginalen](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="47af3-126">Tryck på F5 för att felsöka PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="47af3-126">Hit F5 to debug the PowerShell script.</span></span>

  ![Felsökning av lokal PowerShell-skriptet](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="47af3-128">När du felsöker, kan du interagera med Felsökningskonsolen, Kolla in variabler i området till vänster och de andra vanliga felsökningsverktyg.</span><span class="sxs-lookup"><span data-stu-id="47af3-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="47af3-129">Fjärrfil Redigera med öppen EditorFile</span><span class="sxs-lookup"><span data-stu-id="47af3-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="47af3-130">Nu ska vi gå in fjärrfil redigering och felsökning.</span><span class="sxs-lookup"><span data-stu-id="47af3-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="47af3-131">Stegen är nästan desamma finns det bara en sak som vi behöver göra först - ange våra PowerShell-session till fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="47af3-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="47af3-132">Det finns en cmdlet för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="47af3-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="47af3-133">Den kallas `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="47af3-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="47af3-134">Watered ned förklaring av cmdlet: en är:</span><span class="sxs-lookup"><span data-stu-id="47af3-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="47af3-135">`Enter-PSSession -ComputerName foo` startar en session via WinRM</span><span class="sxs-lookup"><span data-stu-id="47af3-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="47af3-136">`Enter-PSSession -ContainerId foo` och `Enter-PSSession -VmId foo` starta en session via PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="47af3-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="47af3-137">`Enter-PSSession -HostName foo` startar en session via SSH</span><span class="sxs-lookup"><span data-stu-id="47af3-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="47af3-138">Mer information finns i dokumentationen för [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="47af3-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="47af3-139">Eftersom vi från macOS en Ubuntu VM i Azure, använder vi SSH för fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="47af3-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="47af3-140">Kör först följande i konsolen integrerad `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="47af3-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="47af3-141">Du är ansluten till fjärrsessionen när `[<hostname>]` visar upp till vänster om din fråga.</span><span class="sxs-lookup"><span data-stu-id="47af3-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Anropet till Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="47af3-143">Nu kan vi göra likadant som om vi redigerar ett lokalt skript.</span><span class="sxs-lookup"><span data-stu-id="47af3-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="47af3-144">Kör `Open-EditorFile test.ps1` eller `psedit test.ps1` att öppna fjärransluten `test.ps1` fil</span><span class="sxs-lookup"><span data-stu-id="47af3-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Öppna EditorFile test.ps1-fil](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="47af3-146">Redigera filen/set-brytpunkter</span><span class="sxs-lookup"><span data-stu-id="47af3-146">Edit the file/set breakpoints</span></span>

   ![Redigera och ange brytpunkter](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="47af3-148">Starta felsökning (F5) fjärrfilen</span><span class="sxs-lookup"><span data-stu-id="47af3-148">Start debugging (F5) the remote file</span></span>

   ![Felsökning fjärrfilen](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="47af3-150">Om du har problem kan du öppna problem i den [GitHub-lagringsplatsen](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="47af3-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
