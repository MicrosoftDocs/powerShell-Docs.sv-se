---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Användningsområden för Windows PowerShell ISE-skriptobjektmodellen
ms.openlocfilehash: e59593ef06911c709e92fa7a1eabd96d2636ca30
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030906"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="55c57-103">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="55c57-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="55c57-104">Objekt som är associerade med form och funktion i Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="55c57-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="55c57-105">Referens för objektmodell innehåller information om medlemmen egenskaper och metoder som exponerar dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="55c57-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="55c57-106">Exempel som visar hur du kan använda skript för direkt åtkomst till dessa metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="55c57-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="55c57-107">Scripting object model gör det enklare att följande intervall av uppgifter.</span><span class="sxs-lookup"><span data-stu-id="55c57-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="55c57-108">Anpassa utseendet på Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="55c57-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="55c57-109">Du kan använda object model för att ändra inställningar för program och alternativ.</span><span class="sxs-lookup"><span data-stu-id="55c57-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="55c57-110">Exempelvis kan ändra du dem på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="55c57-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="55c57-111">Du kan ändra färg på fel, varningar, utförlig utdata och utdata för felsökning.</span><span class="sxs-lookup"><span data-stu-id="55c57-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="55c57-112">Du kan hämta eller ange bakgrundsfärgerna för kommando-fönstret och utdatarutan skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="55c57-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="55c57-113">Du kan ange förgrundsfärgen för utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="55c57-113">You can set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="55c57-114">Du kan ange namn och storlek för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="55c57-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="55c57-115">Du kan konfigurera varningar.</span><span class="sxs-lookup"><span data-stu-id="55c57-115">You can configure warnings.</span></span> <span data-ttu-id="55c57-116">Den här inställningen innehåller varningar som utfärdas när en fil öppnas i flera PowerShell-flikar, eller när du kör ett skript i filen innan filen har sparats.</span><span class="sxs-lookup"><span data-stu-id="55c57-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="55c57-117">Du kan växla mellan en vy där skriptfönstret och utdatarutan är sida-vid-sida och en vy där skriptfönstret är ovanpå utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="55c57-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="55c57-118">Du kan docka fönstret kommando till längst ned eller upp i utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="55c57-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="55c57-119">Utöka funktionerna i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="55c57-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="55c57-120">Du kan använda object model för att förbättra funktionerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="55c57-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="55c57-121">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="55c57-121">For example, you can:</span></span>

- <span data-ttu-id="55c57-122">Lägga till och ändra instansen av Windows PowerShell ISE själva.</span><span class="sxs-lookup"><span data-stu-id="55c57-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="55c57-123">Om du vill ändra menyerna, kan du exempelvis lägga till nya menyalternativ och mappa nya menyalternativ till skript.</span><span class="sxs-lookup"><span data-stu-id="55c57-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="55c57-124">Skapa skript som kan utför vissa uppgifter som du kan utföra med hjälp av menykommandon och knappar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="55c57-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="55c57-125">Du kan till exempel lägga till, ta bort eller välja en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="55c57-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="55c57-126">Komplettera aktiviteter som kan utföras med hjälp av menykommandon och knappar.</span><span class="sxs-lookup"><span data-stu-id="55c57-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="55c57-127">Exempelvis kan du byta namn på en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="55c57-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="55c57-128">Ändra text buffertar för fönstret kommando, utdatarutan och skriptfönstret som är associerade med en fil.</span><span class="sxs-lookup"><span data-stu-id="55c57-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="55c57-129">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="55c57-129">For example, you can:</span></span>
  - <span data-ttu-id="55c57-130">Hämta eller ange all text.</span><span class="sxs-lookup"><span data-stu-id="55c57-130">Get or set all text.</span></span>
  - <span data-ttu-id="55c57-131">Hämta eller ange en textmarkering.</span><span class="sxs-lookup"><span data-stu-id="55c57-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="55c57-132">Köra ett skript eller köra en del av ett skript.</span><span class="sxs-lookup"><span data-stu-id="55c57-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="55c57-133">Rulla en rad i vyn.</span><span class="sxs-lookup"><span data-stu-id="55c57-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="55c57-134">Infoga text vid en hatt position.</span><span class="sxs-lookup"><span data-stu-id="55c57-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="55c57-135">Välj ett block med text.</span><span class="sxs-lookup"><span data-stu-id="55c57-135">Select a block of text.</span></span>
  - <span data-ttu-id="55c57-136">Hämta den senaste radnummer.</span><span class="sxs-lookup"><span data-stu-id="55c57-136">Get the last line number.</span></span>
- <span data-ttu-id="55c57-137">Utföra åtgärder för sammansättningsfiler.</span><span class="sxs-lookup"><span data-stu-id="55c57-137">Perform file operations.</span></span> <span data-ttu-id="55c57-138">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="55c57-138">For example, you can:</span></span>
  - <span data-ttu-id="55c57-139">Öppna en fil, sparar en fil eller spara en fil med hjälp av ett annat namn.</span><span class="sxs-lookup"><span data-stu-id="55c57-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="55c57-140">Avgör om en fil har ändrats efter det senast sparades.</span><span class="sxs-lookup"><span data-stu-id="55c57-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="55c57-141">Hämta namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="55c57-141">Get the file name.</span></span>
  - <span data-ttu-id="55c57-142">Välj en fil.</span><span class="sxs-lookup"><span data-stu-id="55c57-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="55c57-143">Automatisera uppgifter</span><span class="sxs-lookup"><span data-stu-id="55c57-143">Automating tasks</span></span>

<span data-ttu-id="55c57-144">Du kan använda skript: objektmodell för att skapa kortkommandon för återkommande åtgärder.</span><span class="sxs-lookup"><span data-stu-id="55c57-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="55c57-145">Se även</span><span class="sxs-lookup"><span data-stu-id="55c57-145">See also</span></span>

- [<span data-ttu-id="55c57-146">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="55c57-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
