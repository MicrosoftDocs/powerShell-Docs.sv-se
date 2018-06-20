---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Användningsområden för Windows PowerShell ISE-skriptobjektmodellen
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951332"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="4fbeb-103">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="4fbeb-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="4fbeb-104">Objekt är kopplade till form och funktion i Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="4fbeb-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="4fbeb-105">Objektreferensen modellen innehåller information om medlemmen egenskaper och metoder som visar dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="4fbeb-106">Exempel som visar hur du kan använda skript för direkt åtkomst till dessa metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="4fbeb-107">Scripting object model gör det enklare att följande intervall av uppgifter.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="4fbeb-108">Anpassa utseendet på Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4fbeb-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="4fbeb-109">Du kan använda objektmodellen för att ändra programinställningarna och alternativ.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="4fbeb-110">T.ex, kan du ändra dem på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="4fbeb-111">Du kan ändra färgen för fel, varningar, utförlig utdata och debug matar ut.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="4fbeb-112">Du kan hämta eller ange bakgrundsfärger för kommando-rutan, utdatarutan och skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="4fbeb-113">Du kan ange förgrundsfärgen för utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-113">You can set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="4fbeb-114">Du kan ange teckensnitt och teckenstorlek för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="4fbeb-115">Du kan konfigurera varningar.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-115">You can configure warnings.</span></span> <span data-ttu-id="4fbeb-116">Den här inställningen inkluderar varningar som utfärdas när en fil öppnas i flera PowerShell flikar eller köra ett skript i filen innan filen har sparats.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="4fbeb-117">Du kan växla mellan att visa där skriptfönstret och utdatarutan är sida vid sida och en vy där skriptfönstret är ovanpå utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="4fbeb-118">Du kan docka fönstret kommandot ned eller upp i utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="4fbeb-119">Utöka funktionerna i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4fbeb-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="4fbeb-120">Du kan använda objektmodellen för att förbättra funktionerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="4fbeb-121">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-121">For example, you can:</span></span>

- <span data-ttu-id="4fbeb-122">Lägg till och ändra instansen av Windows PowerShell ISE sig själv.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="4fbeb-123">Om du vill ändra menyerna kan du exempelvis lägga till nya menyalternativ och mappa nya menyalternativ skript.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="4fbeb-124">Skapa skript som utför vissa av de uppgifter som du kan utföra med hjälp av knapparna och kommandon i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="4fbeb-125">Du kan exempelvis lägga till, ta bort eller välja en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="4fbeb-126">Komplement aktiviteter som kan utföras med hjälp av menykommandon och knappar.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="4fbeb-127">Exempelvis kan du byta namn på en PowerShell-flik.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="4fbeb-128">Ändra texten buffertar för kommando-rutan, utdatarutan och rutan skript som är kopplade till en fil.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="4fbeb-129">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-129">For example, you can:</span></span>
  - <span data-ttu-id="4fbeb-130">Hämta eller ange alla text.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-130">Get or set all text.</span></span>
  - <span data-ttu-id="4fbeb-131">Hämta eller ange en textmarkering.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="4fbeb-132">Kör ett skript eller kör en del av ett skript.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="4fbeb-133">Rulla en rad i vyn.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="4fbeb-134">Infoga texten vid en hatt position.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="4fbeb-135">Välj ett block med text.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-135">Select a block of text.</span></span>
  - <span data-ttu-id="4fbeb-136">Hämta senaste numret.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-136">Get the last line number.</span></span>
- <span data-ttu-id="4fbeb-137">Utföra filåtgärder.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-137">Perform file operations.</span></span> <span data-ttu-id="4fbeb-138">Du kan till exempel:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-138">For example, you can:</span></span>
  - <span data-ttu-id="4fbeb-139">Öppna en fil, spara en fil eller spara en fil med ett annat namn.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="4fbeb-140">Avgör om en fil har ändrats efter den senast sparades.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="4fbeb-141">Hämta namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-141">Get the file name.</span></span>
  - <span data-ttu-id="4fbeb-142">Välj en fil.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="4fbeb-143">Automatisera uppgifter</span><span class="sxs-lookup"><span data-stu-id="4fbeb-143">Automating tasks</span></span>

<span data-ttu-id="4fbeb-144">Du kan använda scripting object model kortkommandon för ofta förekommande åtgärder.</span><span class="sxs-lookup"><span data-stu-id="4fbeb-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fbeb-145">Se även</span><span class="sxs-lookup"><span data-stu-id="4fbeb-145">See also</span></span>

- [<span data-ttu-id="4fbeb-146">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="4fbeb-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)