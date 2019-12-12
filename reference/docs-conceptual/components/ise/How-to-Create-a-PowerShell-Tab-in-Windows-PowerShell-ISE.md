---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Skapa en PowerShell-flik i Windows PowerShell ISE
ms.openlocfilehash: 7baf9a4051a196045d53eebf8ce5260bdc1bc55a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030582"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="e8070-103">Skapa en PowerShell-flik i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e8070-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="e8070-104">Med hjälp av flikarna i Windows PowerShell ISE (Integrated Scripting Environment) kan du samtidigt skapa och använda flera körnings miljöer i samma program.</span><span class="sxs-lookup"><span data-stu-id="e8070-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="e8070-105">Varje PowerShell-flik motsvarar en annan körnings miljö eller-session.</span><span class="sxs-lookup"><span data-stu-id="e8070-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="e8070-106">Variabler, funktioner och alias som du skapar på en flik överför inte över till en annan.</span><span class="sxs-lookup"><span data-stu-id="e8070-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="e8070-107">De är olika Windows PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e8070-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="e8070-108">Använd följande steg för att öppna eller stänga en flik i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8070-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="e8070-109">Om du vill byta namn på en flik anger du egenskapen [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) på Windows PowerShell-fliken skript objekt.</span><span class="sxs-lookup"><span data-stu-id="e8070-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="e8070-110">Skapa och använda en ny PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="e8070-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="e8070-111">På **Arkiv** -menyn klickar du på **ny PowerShell-flik**. Den nya PowerShell-fliken öppnas alltid som det aktiva fönstret.</span><span class="sxs-lookup"><span data-stu-id="e8070-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="e8070-112">PowerShell-flikar är stegvisa numrerade i den ordning som de är öppna.</span><span class="sxs-lookup"><span data-stu-id="e8070-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="e8070-113">Varje flik är kopplad till ett eget fönster i Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e8070-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="e8070-114">Du kan ha upp till 32 PowerShell-flikar med sin egen session öppen i taget (detta är begränsat till 8 på Windows PowerShell ISE 2,0.)</span><span class="sxs-lookup"><span data-stu-id="e8070-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="e8070-115">Observera att om du klickar på de **nya** eller **Öppna** ikonerna i verktygsfältet skapas ingen ny flik med en separat session.</span><span class="sxs-lookup"><span data-stu-id="e8070-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="e8070-116">I stället öppnar dessa knappar en ny eller befintlig skript fil på den aktuella aktiva fliken med en session.</span><span class="sxs-lookup"><span data-stu-id="e8070-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="e8070-117">Du kan ha flera öppna skriptfiler med varje flik och session.</span><span class="sxs-lookup"><span data-stu-id="e8070-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="e8070-118">Skript flikarna för en session visas bara under session-flikarna när den associerade sessionen är aktiv.</span><span class="sxs-lookup"><span data-stu-id="e8070-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="e8070-119">Klicka på fliken om du vill aktivera en PowerShell-flik. Om du vill välja bland alla PowerShell-flikar som är öppna, klickar du på den PowerShell-flik som du vill använda på **Visa** -menyn.</span><span class="sxs-lookup"><span data-stu-id="e8070-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="e8070-120">Skapa och använda en ny fjärran sluten PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="e8070-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="e8070-121">På **Arkiv** -menyn klickar du på **ny fjärran sluten PowerShell-flik** för att upprätta en session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e8070-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="e8070-122">En dialog ruta visas där du uppmanas att ange information som krävs för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="e8070-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="e8070-123">Fjärrfliken fungerar precis som en lokal PowerShell-flik, men kommandona och skripten körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e8070-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="e8070-124">Stänga en PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="e8070-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="e8070-125">Om du vill stänga en flik kan du använda någon av följande metoder:</span><span class="sxs-lookup"><span data-stu-id="e8070-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="e8070-126">Klicka på den flik som du vill stänga.</span><span class="sxs-lookup"><span data-stu-id="e8070-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="e8070-127">På **Arkiv** -menyn klickar du på **Stäng PowerShell-fliken**eller på knappen Stäng (**X**) på en aktiv flik för att stänga fliken.</span><span class="sxs-lookup"><span data-stu-id="e8070-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="e8070-128">Om du har osparade filer öppna på fliken PowerShell som du stänger, uppmanas du att spara eller ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="e8070-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="e8070-129">Mer information om hur du sparar ett skript finns i [så här sparar du ett skript](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="e8070-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8070-130">Se även</span><span class="sxs-lookup"><span data-stu-id="e8070-130">See Also</span></span>

- [<span data-ttu-id="e8070-131">Vi presenterar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e8070-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="e8070-132">Använda konsol fönstret i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="e8070-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
