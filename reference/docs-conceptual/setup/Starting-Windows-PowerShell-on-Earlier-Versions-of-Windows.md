---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Starta Windows PowerShell på tidigare versioner av Windows"
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: 52e3acc1fd3009ecad3b7134008e38d4edfb5ca7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="87647-103">Starta Windows PowerShell på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="87647-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="87647-104">Det här avsnittet beskrivs hur du startar Windows PowerShell och Windows PowerShell Integrated Scripting Environment (ISE) på Windows 7, Windows Server® 2008 R2 och Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="87647-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="87647-105">Det beskriver även hur du aktiverar valfri funktion för Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server® 2008 R2 och Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="87647-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="87647-106">Om du vill installera Windows PowerShell 4.0 på system som stöds, hämta och installera [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="87647-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="87647-107">Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="87647-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="87647-108">Om du vill installera Windows PowerShell 3.0 på system som stöds, hämta och installera [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="87647-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="87647-109">Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="87647-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="87647-110">Så här startar du Windows PowerShell på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="87647-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="87647-111">Använd någon av följande metoder för att starta den installerade versionen av Windows PowerShell 3.0 eller Windows PowerShell 4.0, i tillämpliga fall.</span><span class="sxs-lookup"><span data-stu-id="87647-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="87647-112">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="87647-112">From the Start Menu</span></span>

- <span data-ttu-id="87647-113">Klicka på **starta**, typen **PowerShell**, och klicka sedan på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="87647-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

- <span data-ttu-id="87647-114">Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klicka på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="87647-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="87647-115">I Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="87647-115">At the Command Prompt</span></span>

- <span data-ttu-id="87647-116">I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell skriver du:</span><span class="sxs-lookup"><span data-stu-id="87647-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="87647-117">Du kan också använda parametrarna för PowerShell.exe-programmet för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="87647-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="87647-118">Mer information finns i [PowerShell.exe-hjälpen](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="87647-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="87647-119">Med administrativa privilegier (”Kör som administratör”)</span><span class="sxs-lookup"><span data-stu-id="87647-119">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="87647-120">Klicka på **starta**, typen **PowerShell**, högerklicka på **Windows PowerShell**, och klicka sedan på **kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="87647-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="87647-121">Så här startar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="87647-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="87647-122">Använd någon av följande metoder för att starta Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="87647-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="87647-123">Från Start-menyn</span><span class="sxs-lookup"><span data-stu-id="87647-123">From the Start Menu</span></span>

- <span data-ttu-id="87647-124">Klicka på **starta**, typen **ISE**, och klicka sedan på **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="87647-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

- <span data-ttu-id="87647-125">Från den **starta** -menyn klickar du på **starta**, klickar du på **alla program**, klickar du på **tillbehör**, klicka på den **Windows PowerShell**  mappen och klicka sedan på **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="87647-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="87647-126">I Kommandotolken</span><span class="sxs-lookup"><span data-stu-id="87647-126">At the Command Prompt</span></span>

- <span data-ttu-id="87647-127">I Cmd.exe, Windows PowerShell eller Windows PowerShell ISE för att starta Windows PowerShell skriver du:</span><span class="sxs-lookup"><span data-stu-id="87647-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="87647-128">eller</span><span class="sxs-lookup"><span data-stu-id="87647-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="87647-129">Med administrativa privilegier (”Kör som administratör”)</span><span class="sxs-lookup"><span data-stu-id="87647-129">With Administrative privileges ("Run as administrator")</span></span>

1. <span data-ttu-id="87647-130">Klicka på **starta**, typen **ISE**, högerklicka på **Windows PowerShell ISE**, och klicka sedan på **kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="87647-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="87647-131">Så här aktiverar du Windows PowerShell ISE på tidigare versioner av Windows</span><span class="sxs-lookup"><span data-stu-id="87647-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="87647-132">I Windows PowerShell 4.0 och Windows PowerShell 3.0, är Windows PowerShell ISE aktiverad som standard på alla versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="87647-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="87647-133">Om den inte redan är aktiverad, kan Windows Management Framework 4.0 eller Windows Management Framework 3.0 den.</span><span class="sxs-lookup"><span data-stu-id="87647-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="87647-134">I Windows PowerShell 2.0, är Windows PowerShell ISE aktiverad som standard på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="87647-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="87647-135">Det kan dock är en valfri funktion i Windows Server 2008 R2 och Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="87647-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="87647-136">Använd följande procedur för att aktivera Windows PowerShell ISE i Windows PowerShell 2.0 på Windows Server 2008 R2 eller Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="87647-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="87647-137">Så här aktiverar du Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="87647-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="87647-138">Starta Serverhanteraren.</span><span class="sxs-lookup"><span data-stu-id="87647-138">Start Server Manager.</span></span>

2. <span data-ttu-id="87647-139">Klicka på **funktioner** och klicka sedan på **Lägg till funktioner**.</span><span class="sxs-lookup"><span data-stu-id="87647-139">Click **Features** and then click **Add Features**.</span></span>

3. <span data-ttu-id="87647-140">I Välj funktioner klickar du på Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="87647-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

