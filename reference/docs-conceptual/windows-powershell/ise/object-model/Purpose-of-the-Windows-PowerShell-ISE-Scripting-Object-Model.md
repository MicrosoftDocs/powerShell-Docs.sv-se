---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Användningsområden för Windows PowerShell ISE-skriptobjektmodellen
ms.openlocfilehash: 1f48df112bd19297baa311116e79d3d7603d7c81
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811053"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="9d749-103">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="9d749-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="9d749-104">Objekt är kopplade till form och funktion i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="9d749-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9d749-105">Objekt modell referensen innehåller information om medlems egenskaper och metoder som dessa objekt exponerar.</span><span class="sxs-lookup"><span data-stu-id="9d749-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="9d749-106">Exempel finns för att visa hur du kan använda skript för att komma åt dessa metoder och egenskaper direkt.</span><span class="sxs-lookup"><span data-stu-id="9d749-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="9d749-107">Skript objekt modellen gör följande olika uppgifter enklare.</span><span class="sxs-lookup"><span data-stu-id="9d749-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="9d749-108">Anpassa utseendet på Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9d749-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="9d749-109">Du kan använda objekt modellen för att ändra program inställningar och-alternativ.</span><span class="sxs-lookup"><span data-stu-id="9d749-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="9d749-110">Du kan till exempel ändra dem på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="9d749-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="9d749-111">Ändra färg på fel, varningar, utförliga utdata och fel söknings utdata.</span><span class="sxs-lookup"><span data-stu-id="9d749-111">Change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="9d749-112">Hämta eller ange bakgrunds färger för kommando fönstret, fönstret utdata och skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="9d749-112">Get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="9d749-113">Ange förgrunds färgen för fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="9d749-113">Set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="9d749-114">Ange teckensnitts namn och tecken storlek för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d749-114">Set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="9d749-115">Konfigurera varningar.</span><span class="sxs-lookup"><span data-stu-id="9d749-115">Configure warnings.</span></span> <span data-ttu-id="9d749-116">Den här inställningen innehåller varningar som utfärdas när en fil öppnas i flera PowerShell-flikar eller när ett skript i filen körs innan filen har sparats.</span><span class="sxs-lookup"><span data-stu-id="9d749-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="9d749-117">Växla mellan en vy där skript fönstret och utdatafönstret visas sida vid sida och en vy där skript fönstret visas överst i fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="9d749-117">Switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span>
- <span data-ttu-id="9d749-118">Docka kommando fönstret längst ned eller överst i fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="9d749-118">Dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="9d749-119">Förbättra funktionerna i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9d749-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="9d749-120">Du kan använda objekt modellen för att förbättra funktionerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d749-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="9d749-121">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="9d749-121">For example, you can:</span></span>

- <span data-ttu-id="9d749-122">Lägg till och ändra instansen för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d749-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="9d749-123">Om du till exempel vill ändra menyerna kan du lägga till nya meny alternativ och mappa de nya meny alternativen till skript.</span><span class="sxs-lookup"><span data-stu-id="9d749-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="9d749-124">Skapa skript som utför några av de uppgifter som du kan utföra med hjälp av meny kommandona och knapparna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="9d749-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="9d749-125">Du kan till exempel lägga till, ta bort eller välja en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="9d749-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="9d749-126">Komplettera uppgifter som kan utföras med hjälp av Meny kommandon och knappar.</span><span class="sxs-lookup"><span data-stu-id="9d749-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="9d749-127">Du kan till exempel byta namn på en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="9d749-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="9d749-128">Ändra textbuffertar för kommando fönstret, fönstret utdata och skript fönstret som är associerade med en fil.</span><span class="sxs-lookup"><span data-stu-id="9d749-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="9d749-129">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="9d749-129">For example, you can:</span></span>
  - <span data-ttu-id="9d749-130">Hämta eller ange all text.</span><span class="sxs-lookup"><span data-stu-id="9d749-130">Get or set all text.</span></span>
  - <span data-ttu-id="9d749-131">Hämta eller ange ett text val.</span><span class="sxs-lookup"><span data-stu-id="9d749-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="9d749-132">Kör ett skript eller kör en vald del av ett skript.</span><span class="sxs-lookup"><span data-stu-id="9d749-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="9d749-133">Rulla en rad till vyn.</span><span class="sxs-lookup"><span data-stu-id="9d749-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="9d749-134">Infoga text i cirkumflex.</span><span class="sxs-lookup"><span data-stu-id="9d749-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="9d749-135">Välj ett textblock.</span><span class="sxs-lookup"><span data-stu-id="9d749-135">Select a block of text.</span></span>
  - <span data-ttu-id="9d749-136">Hämta det sista rad numret.</span><span class="sxs-lookup"><span data-stu-id="9d749-136">Get the last line number.</span></span>
- <span data-ttu-id="9d749-137">Utför fil åtgärder.</span><span class="sxs-lookup"><span data-stu-id="9d749-137">Perform file operations.</span></span> <span data-ttu-id="9d749-138">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="9d749-138">For example, you can:</span></span>
  - <span data-ttu-id="9d749-139">Öppna en fil, spara en fil eller spara en fil med hjälp av ett annat namn.</span><span class="sxs-lookup"><span data-stu-id="9d749-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="9d749-140">Avgör om en fil har ändrats efter att den senast sparades.</span><span class="sxs-lookup"><span data-stu-id="9d749-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="9d749-141">Hämta fil namnet.</span><span class="sxs-lookup"><span data-stu-id="9d749-141">Get the file name.</span></span>
  - <span data-ttu-id="9d749-142">Välj en fil.</span><span class="sxs-lookup"><span data-stu-id="9d749-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="9d749-143">Automatisera uppgifter</span><span class="sxs-lookup"><span data-stu-id="9d749-143">Automating tasks</span></span>

<span data-ttu-id="9d749-144">Du kan använda skript objekt modellen för att skapa kortkommandon för frekventa åtgärder.</span><span class="sxs-lookup"><span data-stu-id="9d749-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d749-145">Se även</span><span class="sxs-lookup"><span data-stu-id="9d749-145">See also</span></span>

- [<span data-ttu-id="9d749-146">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="9d749-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
