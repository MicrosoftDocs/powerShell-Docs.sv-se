---
title: Med Visual Studio Code för fjärranslutna redigering och felsökning
description: Med Visual Studio Code för fjärranslutna redigering och felsökning
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655543"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="5617b-103">Med Visual Studio Code för fjärranslutna redigering och felsökning</span><span class="sxs-lookup"><span data-stu-id="5617b-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="5617b-104">För dig som har erfarenhet av ISE, du kanske kommer ihåg att du kan köra `psedit file.ps1` från integrerad konsol för att öppna filer – lokal eller fjärransluten - Högerklicka i ISE.</span><span class="sxs-lookup"><span data-stu-id="5617b-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="5617b-105">Den här funktionen är även tillgängliga i PowerShell-tillägget för VSCode eftersom det har visat sig.</span><span class="sxs-lookup"><span data-stu-id="5617b-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="5617b-106">Den här guiden visar hur du gör den.</span><span class="sxs-lookup"><span data-stu-id="5617b-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5617b-107">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="5617b-107">Prerequisites</span></span>

<span data-ttu-id="5617b-108">Den här guiden förutsätter att du har:</span><span class="sxs-lookup"><span data-stu-id="5617b-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="5617b-109">en fjärransluten resurs (t.ex.: en virtuell dator, en behållare) att du har åtkomst till</span><span class="sxs-lookup"><span data-stu-id="5617b-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="5617b-110">PowerShell som körs på den och värddatorn</span><span class="sxs-lookup"><span data-stu-id="5617b-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="5617b-111">VSCode och PowerShell-tillägget för VSCode</span><span class="sxs-lookup"><span data-stu-id="5617b-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="5617b-112">Den här funktionen fungerar i Windows PowerShell och PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="5617b-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="5617b-113">Den här funktionen fungerar även när du ansluter till en fjärrdator via WinRM, PowerShell Direct eller SSH.</span><span class="sxs-lookup"><span data-stu-id="5617b-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="5617b-114">Om du vill använda SSH, men använder Windows, Kolla in den [Win32-versionen av SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="5617b-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="5617b-115">Kom så går vi</span><span class="sxs-lookup"><span data-stu-id="5617b-115">Let's go</span></span>

<span data-ttu-id="5617b-116">I det här avsnittet kan gå jag igenom remote redigering och felsökning från min MacBook Pro för en Ubuntu-VM som körs i Azure.</span><span class="sxs-lookup"><span data-stu-id="5617b-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="5617b-117">Jag kan inte använda Windows, men **processen är identiska**.</span><span class="sxs-lookup"><span data-stu-id="5617b-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="5617b-118">Lokal fil Redigera med öppen EditorFile</span><span class="sxs-lookup"><span data-stu-id="5617b-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="5617b-119">Med PowerShell-tillägget för VSCode igång och integrerad PowerShell-konsolen öppnas, vi kan skriva `Open-EditorFile foo.ps1` eller `psedit foo.ps1` att öppna lokala foo.ps1 fil direkt i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="5617b-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Öppna EditorFile foo.ps1 arbetar lokalt](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="5617b-121">foo.ps1 måste redan finnas.</span><span class="sxs-lookup"><span data-stu-id="5617b-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="5617b-122">Därifrån kan vi:</span><span class="sxs-lookup"><span data-stu-id="5617b-122">From there, we can:</span></span>

<span data-ttu-id="5617b-123">lägga till brytpunkter fästmarginalen ![att lägga till brytpunkt om du vill fästmarginalen](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="5617b-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="5617b-124">och tryck på F5 för att felsöka PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="5617b-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="5617b-125">![Felsökning av lokal PowerShell-skriptet](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="5617b-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="5617b-126">När du felsöker, kan du interagera med Felsökningskonsolen, Kolla in variabler i området till vänster och de andra vanliga felsökningsverktyg.</span><span class="sxs-lookup"><span data-stu-id="5617b-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="5617b-127">Fjärrfil Redigera med öppen EditorFile</span><span class="sxs-lookup"><span data-stu-id="5617b-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="5617b-128">Nu ska vi gå in fjärrfil redigering och felsökning.</span><span class="sxs-lookup"><span data-stu-id="5617b-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="5617b-129">Stegen är nästan desamma finns det bara en sak som vi behöver göra först - ange våra PowerShell-session till fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="5617b-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="5617b-130">Det finns en cmdlet för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="5617b-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="5617b-131">Den kallas `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5617b-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="5617b-132">Watered ned förklaring av cmdlet: en är:</span><span class="sxs-lookup"><span data-stu-id="5617b-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="5617b-133">`Enter-PSSession -ComputerName foo` startar en session via WinRM</span><span class="sxs-lookup"><span data-stu-id="5617b-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="5617b-134">`Enter-PSSession -ContainerId foo` och `Enter-PSSession -VmId foo` starta en session via PowerShell Direct</span><span class="sxs-lookup"><span data-stu-id="5617b-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="5617b-135">`Enter-PSSession -HostName foo` startar en session via SSH</span><span class="sxs-lookup"><span data-stu-id="5617b-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="5617b-136">Mer information om `Enter-PSSession`, Kolla in dokumenten [här](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="5617b-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="5617b-137">Jag kommer att använda SSH för fjärrkörning eftersom jag från macOS för en Ubuntu-VM i Azure.</span><span class="sxs-lookup"><span data-stu-id="5617b-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="5617b-138">Först i konsolen integrerad vi köra våra Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="5617b-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="5617b-139">Du vet att du befinner dig i sessionen eftersom `[something]` visas till vänster om din fråga.</span><span class="sxs-lookup"><span data-stu-id="5617b-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![Anropet till Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="5617b-141">Därifrån kan göra vi de exakta stegen som om vi redigerade ett lokalt skript.</span><span class="sxs-lookup"><span data-stu-id="5617b-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="5617b-142">Kör `Open-EditorFile test.ps1` eller `psedit test.ps1` att öppna fjärransluten `test.ps1` filen ![öppen-EditorFile test.ps1-fil](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="5617b-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="5617b-143">Redigera filen/set-brytpunkter</span><span class="sxs-lookup"><span data-stu-id="5617b-143">Edit the file/set breakpoints</span></span> ![Redigera och ange brytpunkter](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="5617b-145">Starta felsökning (F5) fjärrfilen</span><span class="sxs-lookup"><span data-stu-id="5617b-145">Start debugging (F5) the remote file</span></span>

![Felsökning fjärrfilen](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="5617b-147">Det är allt det!</span><span class="sxs-lookup"><span data-stu-id="5617b-147">That's all there's to it!</span></span> <span data-ttu-id="5617b-148">Vi hoppas att den här guiden hjälpt Rensa upp frågor om remote felsökning och redigera PowerShell i VSCode.</span><span class="sxs-lookup"><span data-stu-id="5617b-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="5617b-149">Om du har problem kan passa på att öppna problem [på GitHub-lagringsplatsen](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5617b-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>
