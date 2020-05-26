---
title: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
description: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810626"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="6e2c2-103">Använda Visual Studio Code för att fjärredigera och fjärrfelsöka</span><span class="sxs-lookup"><span data-stu-id="6e2c2-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="6e2c2-104">För de som är bekanta med ISE kan du återkalla att du kan köra `psedit file.ps1` från den integrerade konsolen för att öppna filer – lokalt eller fjärranslutna i ISE.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="6e2c2-105">Den här funktionen är även tillgänglig i PowerShell-tillägget för VSCode.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="6e2c2-106">Den här guiden visar hur du gör.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e2c2-107">Krav</span><span class="sxs-lookup"><span data-stu-id="6e2c2-107">Prerequisites</span></span>

<span data-ttu-id="6e2c2-108">Den här guiden förutsätter att du har:</span><span class="sxs-lookup"><span data-stu-id="6e2c2-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="6e2c2-109">En fjär resurs (t. ex. en virtuell dator, en behållare) som du har åtkomst till</span><span class="sxs-lookup"><span data-stu-id="6e2c2-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="6e2c2-110">PowerShell som körs på den och värddatorn</span><span class="sxs-lookup"><span data-stu-id="6e2c2-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="6e2c2-111">VSCode och PowerShell-tillägget för VSCode</span><span class="sxs-lookup"><span data-stu-id="6e2c2-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="6e2c2-112">Den här funktionen fungerar i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="6e2c2-113">Den här funktionen fungerar även när du ansluter till en fjärrdator via WinRM, PowerShell Direct eller SSH.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="6e2c2-114">Om du vill använda SSH, men använder Windows, kontrollerar du [Win32-versionen av SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="6e2c2-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e2c2-115">`Open-EditorFile` `psedit` Kommandona och fungerar bara i den **integrerade PowerShell-konsolen** som skapats av PowerShell-tillägget för VSCode.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="6e2c2-116">Användnings exempel</span><span class="sxs-lookup"><span data-stu-id="6e2c2-116">Usage examples</span></span>

<span data-ttu-id="6e2c2-117">De här exemplen visar fjärrredigering och fel sökning från en MacBook Pro till en Ubuntu-VM som körs i Azure.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="6e2c2-118">Processen är identisk med Windows.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="6e2c2-119">Lokal fil redigering med Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="6e2c2-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="6e2c2-120">Med PowerShell-tillägget för VSCode igång och den integrerade PowerShell-konsolen öppnas, kan vi skriva `Open-EditorFile foo.ps1` eller `psedit foo.ps1` öppna den lokala foo. ps1-filen direkt i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo. ps1 fungerar lokalt](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="6e2c2-122">Filen `foo.ps1` måste redan finnas.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="6e2c2-123">Därifrån kan vi:</span><span class="sxs-lookup"><span data-stu-id="6e2c2-123">From there, we can:</span></span>

- <span data-ttu-id="6e2c2-124">Lägga till Bryt punkter i fästmarginal</span><span class="sxs-lookup"><span data-stu-id="6e2c2-124">Add breakpoints to the gutter</span></span>

  ![lägga till Bryt punkt i fästmarginal](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="6e2c2-126">Tryck på F5 för att felsöka PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-126">Hit F5 to debug the PowerShell script.</span></span>

  ![Felsöka det lokala PowerShell-skriptet](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="6e2c2-128">Vid fel sökning kan du interagera med fel söknings konsolen, kolla in variablerna i omfånget till vänster och alla andra standard verktyg för fel sökning.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="6e2c2-129">Fjärrstyrd redigering med Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="6e2c2-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="6e2c2-130">Nu ska vi komma igång med att redigera och felsöka filer.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="6e2c2-131">Stegen är nästan desamma, men det är bara en sak vi behöver göra för att först fylla i PowerShell-sessionen till fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="6e2c2-132">Det finns en cmdlet för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="6e2c2-133">Den kallas `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6e2c2-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="6e2c2-134">Den nedrullningsbara förklaringen av cmdleten är:</span><span class="sxs-lookup"><span data-stu-id="6e2c2-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="6e2c2-135">`Enter-PSSession -ComputerName foo`Starta en-session via WinRM</span><span class="sxs-lookup"><span data-stu-id="6e2c2-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="6e2c2-136">`Enter-PSSession -ContainerId foo`och `Enter-PSSession -VmId foo` starta en-session via PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="6e2c2-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="6e2c2-137">`Enter-PSSession -HostName foo`Starta en-session via SSH</span><span class="sxs-lookup"><span data-stu-id="6e2c2-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="6e2c2-138">Mer information finns i dokumentationen för [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="6e2c2-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="6e2c2-139">Eftersom vi kommer från macOS till en virtuell Ubuntu-dator i Azure använder vi SSH för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="6e2c2-140">Börja med att köra i den integrerade konsolen `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="6e2c2-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="6e2c2-141">Du är ansluten till fjärrsessionen när den `[<hostname>]` visas till vänster om din prompt.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Anropet till retur-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="6e2c2-143">Nu kan vi utföra samma steg som om vi redigerar ett lokalt skript.</span><span class="sxs-lookup"><span data-stu-id="6e2c2-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="6e2c2-144">Köra `Open-EditorFile test.ps1` eller `psedit test.ps1` för att öppna `test.ps1` fjärrfilen</span><span class="sxs-lookup"><span data-stu-id="6e2c2-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Öppna – EditorFile filen test. ps1](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="6e2c2-146">Redigera fil-/uppsättnings Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="6e2c2-146">Edit the file/set breakpoints</span></span>

   ![Redigera och ange Bryt punkter](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="6e2c2-148">Starta fel sökning (F5) fjärrfilen</span><span class="sxs-lookup"><span data-stu-id="6e2c2-148">Start debugging (F5) the remote file</span></span>

   ![Felsöka fjärrfilen](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="6e2c2-150">Om du har problem kan du öppna problem i [GitHub-lagrings platsen](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="6e2c2-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
