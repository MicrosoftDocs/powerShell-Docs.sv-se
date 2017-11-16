---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Syftet med Windows PowerShell ISE Scripting Object Model
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="32342-103">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="32342-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="32342-104">Objekt är kopplade till form och funktion i Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="32342-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="32342-105">Objektreferensen modellen innehåller information om medlemmen egenskaper och metoder som visar dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="32342-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="32342-106">Exempel som visar hur du kan använda skript för direkt åtkomst till dessa metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="32342-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="32342-107">Scripting object model gör det enklare att följande intervall av uppgifter.</span><span class="sxs-lookup"><span data-stu-id="32342-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="32342-108">Anpassa utseendet på Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="32342-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="32342-109">Du kan använda objektmodellen för att ändra programinställningarna och alternativ.</span><span class="sxs-lookup"><span data-stu-id="32342-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="32342-110">T.ex, kan du ändra dem på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="32342-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="32342-111">Du kan ändra färgen för fel, varningar, utförlig utdata och debug matar ut.</span><span class="sxs-lookup"><span data-stu-id="32342-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

- <span data-ttu-id="32342-112">Du kan hämta eller ange bakgrundsfärger för kommando-rutan, utdatarutan och skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="32342-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

- <span data-ttu-id="32342-113">Du kan ange förgrundsfärgen för utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="32342-113">You can set the foreground color for the Output pane.</span></span>

- <span data-ttu-id="32342-114">Du kan ange teckensnitt och teckenstorlek för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="32342-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="32342-115">Du kan konfigurera varningar.</span><span class="sxs-lookup"><span data-stu-id="32342-115">You can configure warnings.</span></span> <span data-ttu-id="32342-116">Den här inställningen inkluderar varningar som utfärdas när en fil öppnas i flera PowerShell flikar eller köra ett skript i filen innan filen har sparats.</span><span class="sxs-lookup"><span data-stu-id="32342-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

- <span data-ttu-id="32342-117">Du kan växla mellan att visa där skriptfönstret och utdatarutan är sida vid sida och en vy där skriptfönstret är ovanpå utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="32342-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="32342-118">Du kan docka fönstret kommandot ned eller upp i utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="32342-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="32342-119">Utöka funktionerna i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="32342-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="32342-120">Du kan använda objektmodellen för att förbättra funktionerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="32342-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="32342-121">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="32342-121">For example, you can:</span></span>

- <span data-ttu-id="32342-122">Lägg till och ändra instansen av Windows PowerShell ISE sig själv.</span><span class="sxs-lookup"><span data-stu-id="32342-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="32342-123">Om du vill ändra menyerna kan du exempelvis lägga till nya menyalternativ och mappa nya menyalternativ skript.</span><span class="sxs-lookup"><span data-stu-id="32342-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

- <span data-ttu-id="32342-124">Skapa skript som utför vissa av de uppgifter som du kan utföra med hjälp av knapparna och kommandon i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="32342-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="32342-125">Du kan exempelvis lägga till, ta bort eller välja en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="32342-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

- <span data-ttu-id="32342-126">Komplement aktiviteter som kan utföras med hjälp av menykommandon och knappar.</span><span class="sxs-lookup"><span data-stu-id="32342-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="32342-127">Exempelvis kan du byta namn på en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="32342-127">For example, you can rename a PowerShell tab.</span></span>

- <span data-ttu-id="32342-128">Ändra texten buffertar för kommando-rutan, utdatarutan och rutan skript som är kopplade till en fil.</span><span class="sxs-lookup"><span data-stu-id="32342-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="32342-129">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="32342-129">For example, you can:</span></span>

    -   <span data-ttu-id="32342-130">Hämta eller ange alla text.</span><span class="sxs-lookup"><span data-stu-id="32342-130">Get or set all text.</span></span>

    -   <span data-ttu-id="32342-131">Hämta eller ange en textmarkering.</span><span class="sxs-lookup"><span data-stu-id="32342-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="32342-132">Kör ett skript eller kör en del av ett skript.</span><span class="sxs-lookup"><span data-stu-id="32342-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="32342-133">Rulla en rad i vyn.</span><span class="sxs-lookup"><span data-stu-id="32342-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="32342-134">Infoga texten vid en hatt position.</span><span class="sxs-lookup"><span data-stu-id="32342-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="32342-135">Välj ett block med text.</span><span class="sxs-lookup"><span data-stu-id="32342-135">Select a block of text.</span></span>

    -   <span data-ttu-id="32342-136">Hämta senaste numret.</span><span class="sxs-lookup"><span data-stu-id="32342-136">Get the last line number.</span></span>

- <span data-ttu-id="32342-137">Utföra filåtgärder.</span><span class="sxs-lookup"><span data-stu-id="32342-137">Perform file operations.</span></span> <span data-ttu-id="32342-138">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="32342-138">For example, you can:</span></span>

    -   <span data-ttu-id="32342-139">Öppna en fil, spara en fil eller spara en fil med ett annat namn.</span><span class="sxs-lookup"><span data-stu-id="32342-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="32342-140">Avgör om en fil har ändrats efter den senast sparades.</span><span class="sxs-lookup"><span data-stu-id="32342-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="32342-141">Hämta namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="32342-141">Get the file name.</span></span>

    -   <span data-ttu-id="32342-142">Välj en fil.</span><span class="sxs-lookup"><span data-stu-id="32342-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="32342-143">Automatisera uppgifter</span><span class="sxs-lookup"><span data-stu-id="32342-143">Automating tasks</span></span>
 <span data-ttu-id="32342-144">Du kan använda scripting object model kortkommandon för ofta förekommande åtgärder.</span><span class="sxs-lookup"><span data-stu-id="32342-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="32342-145">Se även</span><span class="sxs-lookup"><span data-stu-id="32342-145">See Also</span></span>
- [<span data-ttu-id="32342-146">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="32342-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="32342-147">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="32342-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="32342-148">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="32342-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
