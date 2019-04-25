---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en PowerShell-flik i Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 080fe89bf1443f51460589b445431913fa20b4b8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057748"
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="46de0-103">Skapa en PowerShell-flik i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="46de0-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>

<span data-ttu-id="46de0-104">Flikarna i den Windows PowerShell Integrated Scripting Environment (ISE) kan du samtidigt skapar och använder flera körningsmiljöer inom samma program.</span><span class="sxs-lookup"><span data-stu-id="46de0-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="46de0-105">Varje PowerShell-flik motsvarar en separat körningsmiljö eller -session.</span><span class="sxs-lookup"><span data-stu-id="46de0-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> [!NOTE]
> <span data-ttu-id="46de0-106">Variabler, funktioner och alias som du skapar i en flik överför inte till en annan.</span><span class="sxs-lookup"><span data-stu-id="46de0-106">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="46de0-107">De är olika Windows PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="46de0-107">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="46de0-108">Använd följande steg för att öppna eller stänga en flik i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="46de0-108">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="46de0-109">Byt namn på en flik genom att ange den [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) egenskap i Windows PowerShell-flik skript-objektet.</span><span class="sxs-lookup"><span data-stu-id="46de0-109">To rename a tab, set the [DisplayName](object-model/The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="46de0-110">Du skapar och använder en ny PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="46de0-110">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="46de0-111">På den **filen** -menyn klickar du på **nya PowerShell-flik**. Den nya PowerShell-fliken öppnas alltid som det aktiva fönstret.</span><span class="sxs-lookup"><span data-stu-id="46de0-111">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="46de0-112">PowerShell-flikar numreras stegvis i den ordning som de är öppna.</span><span class="sxs-lookup"><span data-stu-id="46de0-112">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="46de0-113">Varje flik är associerad med sin egen Windows PowerShell-konsolfönster.</span><span class="sxs-lookup"><span data-stu-id="46de0-113">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="46de0-114">Du kan ha upp till 32 PowerShell flikar med sin egen session som är öppna samtidigt (detta är begränsade till 8 om Windows PowerShell ISE 2.0.)</span><span class="sxs-lookup"><span data-stu-id="46de0-114">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="46de0-115">Observera att klicka på den **New** eller **öppna** ikoner i verktygsfältet inte skapa en ny flik med en separat session.</span><span class="sxs-lookup"><span data-stu-id="46de0-115">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="46de0-116">Dessa knappar öppna i stället en ny eller befintlig skriptfil på fliken är aktiva för tillfället med en session.</span><span class="sxs-lookup"><span data-stu-id="46de0-116">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="46de0-117">Du kan ha flera skript öppnas filerna med varje flik och sessionen.</span><span class="sxs-lookup"><span data-stu-id="46de0-117">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="46de0-118">Flikarna skriptet för en session visas endast under flikarna sessionen när den associerade sessionen är aktiv.</span><span class="sxs-lookup"><span data-stu-id="46de0-118">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="46de0-119">Klicka på fliken om du vill aktivera en PowerShell-flik. Att välja från alla PowerShell-flikar som är öppna på de **visa** menyn, klicka på fliken PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="46de0-119">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="46de0-120">Du skapar och använder en ny flik för fjärr-PowerShell</span><span class="sxs-lookup"><span data-stu-id="46de0-120">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="46de0-121">På den **filen** -menyn klickar du på **ny Remote PowerShell-flik** att upprätta en session på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="46de0-121">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="46de0-122">En dialogruta visas och du uppmanas att ange information som krävs för att upprätta anslutningen.</span><span class="sxs-lookup"><span data-stu-id="46de0-122">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="46de0-123">Fliken fjärrsessioner funktioner precis som en lokal PowerShell-flik men kommandon och skript körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="46de0-123">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="46de0-124">Att stänga en PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="46de0-124">To close a PowerShell Tab</span></span>

<span data-ttu-id="46de0-125">Du kan använda någon av följande metoder för att stänga en flik:</span><span class="sxs-lookup"><span data-stu-id="46de0-125">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="46de0-126">Klicka på fliken som du vill stänga.</span><span class="sxs-lookup"><span data-stu-id="46de0-126">Click the tab that you want to close.</span></span>

- <span data-ttu-id="46de0-127">På den **filen** -menyn klickar du på **stänger PowerShell-flik**, eller klicka på Stäng (**X**) på en aktiv flik att Stäng fliken.</span><span class="sxs-lookup"><span data-stu-id="46de0-127">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="46de0-128">Om du har osparade öppna filer i PowerShell-flik att du stänger, uppmanas du att spara eller ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="46de0-128">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="46de0-129">Läs mer om hur du sparar ett skript, [så Spara ett skriptet](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="46de0-129">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="46de0-130">Se även</span><span class="sxs-lookup"><span data-stu-id="46de0-130">See Also</span></span>

- [<span data-ttu-id="46de0-131">Introduktion till Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="46de0-131">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="46de0-132">Hur du använder konsolfönstret i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="46de0-132">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)