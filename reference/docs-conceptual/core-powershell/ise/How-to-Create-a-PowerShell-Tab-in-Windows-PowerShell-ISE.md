---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Så här skapar du en PowerShell-flik i Windows PowerShell ISE"
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="6bd9e-103">Så här skapar du en PowerShell-flik i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6bd9e-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="6bd9e-104">Flikarna i den Windows PowerShell Integrated Scripting Environment (ISE) kan du skapa och använda flera körning miljöer inom samma program samtidigt.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="6bd9e-105">Varje flik PowerShell motsvarar en separat körningsmiljö eller session.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="6bd9e-106">**OBS**:</span><span class="sxs-lookup"><span data-stu-id="6bd9e-106">**NOTE**:</span></span>
>
> <span data-ttu-id="6bd9e-107">Variabler, funktioner och alias som du skapar i en flik utför inte till en annan.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="6bd9e-108">De är olika Windows PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="6bd9e-109">Använd följande steg för att öppna eller stänga en flik i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="6bd9e-110">Byt namn på en flik genom att ange den [DisplayName](The-PowerShellTab-Object.md#displayname) egenskapen i fliken i Windows PowerShell-skript objektet.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="6bd9e-111">Skapa och använda en ny flik i PowerShell</span><span class="sxs-lookup"><span data-stu-id="6bd9e-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="6bd9e-112">På den **filen** -menyn klickar du på **ny PowerShell-flik**. Fliken PowerShell öppnas alltid som det aktiva fönstret.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="6bd9e-113">PowerShell-flikar numreras inkrementellt i den ordning som de är öppna.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="6bd9e-114">Varje flik är associerad med sin egen Windows PowerShell-konsolfönster.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="6bd9e-115">Du kan ha upp till 32 PowerShell flikar med sin egen session som är öppna samtidigt (detta är begränsad till 8 i Windows PowerShell ISE 2.0.)</span><span class="sxs-lookup"><span data-stu-id="6bd9e-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="6bd9e-116">Observera att klicka på den **ny** eller **öppna** ikoner i verktygsfältet inte skapa en ny flik med en separat session.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="6bd9e-117">Knapparna Öppna i stället en ny eller befintlig skriptfil på fliken aktiva med en session.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="6bd9e-118">Du kan ha flera skript filer öppna med varje flik och sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="6bd9e-119">Flikarna skriptet för en session visas endast under flikarna sessionen när den associerade sessionen är aktiv.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="6bd9e-120">Klicka på fliken om du vill aktivera en PowerShell-flik. Att välja från alla PowerShell flikar som är öppna på de **visa** -menyn klickar du på fliken PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="6bd9e-121">Skapa och använda en ny flik för fjärr-PowerShell</span><span class="sxs-lookup"><span data-stu-id="6bd9e-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="6bd9e-122">På den **filen** -menyn klickar du på **Remote PowerShell fliken** att upprätta en session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="6bd9e-123">En dialogruta visas och du uppmanas att ange information som krävs för att upprätta anslutningen.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="6bd9e-124">Fliken fjärrsessioner funktioner precis som en lokal PowerShell-fliken, men kommandon och skript körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="6bd9e-125">Att stänga en PowerShell-fliken</span><span class="sxs-lookup"><span data-stu-id="6bd9e-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="6bd9e-126">Du kan använda någon av följande metoder för att stänga en flik:</span><span class="sxs-lookup"><span data-stu-id="6bd9e-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="6bd9e-127">Klicka på fliken som du vill avsluta.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="6bd9e-128">På den **filen** -menyn klickar du på **stänga PowerShell fliken**, eller klicka på knappen Stäng (**X**) på en aktiv fliken för att stänga fliken.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="6bd9e-129">Om du har osparade öppna filer på fliken PowerShell att du stänger, du uppmanas att spara eller ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="6bd9e-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="6bd9e-130">Mer information om hur du sparar ett skript finns [hur du sparar ett skriptet](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="6bd9e-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="6bd9e-131">Se även</span><span class="sxs-lookup"><span data-stu-id="6bd9e-131">See Also</span></span>

- [<span data-ttu-id="6bd9e-132">Med hjälp av Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6bd9e-132">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="6bd9e-133">Hur du använder konsolfönstret i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6bd9e-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

