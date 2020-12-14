---
description: Beskriver hur du redigerar kommandon i PowerShell-Kommandotolken.
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_line_editing?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Line_Editing
ms.openlocfilehash: 2b9a320b92bc0a61efc9f9ed75078b17cdd9cbc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708495"
---
# <a name="about-line-editing"></a><span data-ttu-id="c81d3-103">Om rad redigering</span><span class="sxs-lookup"><span data-stu-id="c81d3-103">About Line Editing</span></span>

## <a name="short-description"></a><span data-ttu-id="c81d3-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="c81d3-104">Short description</span></span>

<span data-ttu-id="c81d3-105">Beskriver hur du redigerar kommandon i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="c81d3-105">Describes how to edit commands at the PowerShell command prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="c81d3-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="c81d3-106">Long description</span></span>

<span data-ttu-id="c81d3-107">PowerShell-konsolen innehåller några användbara kortkommandon som hjälper dig att redigera kommandon i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="c81d3-107">The PowerShell console has some useful keyboard shortcuts to help you edit commands at the PowerShell command prompt.</span></span>

### <a name="add-a-line"></a><span data-ttu-id="c81d3-108">Lägg till en rad</span><span class="sxs-lookup"><span data-stu-id="c81d3-108">Add a line</span></span>

<span data-ttu-id="c81d3-109">Tryck på <kbd>SKIFT</kbd>RETUR om du vill lägga till en rad + <kbd></kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-109">To add a line, press <kbd>Shift</kbd>+<kbd>Enter</kbd>.</span></span>

<span data-ttu-id="c81d3-110">Du kan lägga till flera rader.</span><span class="sxs-lookup"><span data-stu-id="c81d3-110">You can add multiple lines.</span></span> <span data-ttu-id="c81d3-111">Alla ytterligare rader börjar med `>>` , och fortsättnings anvisningarna.</span><span class="sxs-lookup"><span data-stu-id="c81d3-111">Each additional line begins with `>>`, the continuation prompt.</span></span> <span data-ttu-id="c81d3-112">Kör kommandot genom att trycka på <kbd>RETUR</kbd> .</span><span class="sxs-lookup"><span data-stu-id="c81d3-112">Press <kbd>Enter</kbd> to execute the command.</span></span>

### <a name="move-left-and-right"></a><span data-ttu-id="c81d3-113">Flytta åt vänster och höger</span><span class="sxs-lookup"><span data-stu-id="c81d3-113">Move left and right</span></span>

<span data-ttu-id="c81d3-114">Om du vill flytta markören ett till vänster trycker du på <kbd>vänsterpilen</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-114">To move the cursor one character to the left, press the <kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="c81d3-115">Om du vill flytta markören ett ord till vänster trycker du på <kbd>CTRL</kbd> + <kbd>vänsterpil</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-115">To move the cursor one word to the left, press <kbd>Ctrl</kbd>+<kbd>Left arrow</kbd>.</span></span>

<span data-ttu-id="c81d3-116">Tryck <kbd>på högerpilen</kbd>för att flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="c81d3-116">To move the cursor one character to the right, press the <kbd>Right arrow</kbd>.</span></span>

<span data-ttu-id="c81d3-117">Tryck på <kbd>CTRL</kbd>HÖGERPIL om du vill flytta markören ett ord till höger + <kbd></kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-117">To move the cursor one word to the right, press <kbd>Ctrl</kbd>+<kbd>Right arrow</kbd>.</span></span>

### <a name="move-to-a-lines-beginning-or-end"></a><span data-ttu-id="c81d3-118">Flytta till en linjes början eller slutet</span><span class="sxs-lookup"><span data-stu-id="c81d3-118">Move to a line's beginning or end</span></span>

<span data-ttu-id="c81d3-119">Om du vill flytta till början av en rad trycker du på <kbd>Start</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-119">To move to the beginning of a line, press <kbd>Home</kbd>.</span></span>

<span data-ttu-id="c81d3-120">Tryck på <kbd>End</kbd>om du vill flytta till slutet av en rad.</span><span class="sxs-lookup"><span data-stu-id="c81d3-120">To move to the end of a line, press <kbd>End</kbd>.</span></span>

<span data-ttu-id="c81d3-121">Om rader har lagts till trycker du på <kbd>Home</kbd> eller <kbd>End</kbd> två gånger för att flytta till början eller slutet av raderna.</span><span class="sxs-lookup"><span data-stu-id="c81d3-121">If lines were added, press <kbd>Home</kbd> or <kbd>End</kbd> twice to move to the beginning or end of the lines.</span></span>

### <a name="delete-characters"></a><span data-ttu-id="c81d3-122">Ta bort tecken</span><span class="sxs-lookup"><span data-stu-id="c81d3-122">Delete characters</span></span>

<span data-ttu-id="c81d3-123">Om du vill ta bort ett tecken bakom markörens position trycker du på <kbd>Backsteg</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-123">To delete the character behind the cursor's position, press <kbd>Backspace</kbd>.</span></span>

<span data-ttu-id="c81d3-124">Tryck på <kbd>ta bort</kbd>om du vill ta bort symbolen vid markörens position.</span><span class="sxs-lookup"><span data-stu-id="c81d3-124">To delete the character at the cursor's position, press <kbd>Delete</kbd>.</span></span>

### <a name="delete-characters-from-a-line"></a><span data-ttu-id="c81d3-125">Ta bort tecken från en rad</span><span class="sxs-lookup"><span data-stu-id="c81d3-125">Delete characters from a line</span></span>

<span data-ttu-id="c81d3-126">Om du vill ta bort alla tecken från markörens position till slutet av en rad trycker du på <kbd>CTRL</kbd> + <kbd>End</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-126">To delete all the characters from the cursor's position to the end of a line, press <kbd>Ctrl</kbd>+<kbd>End</kbd>.</span></span>

<span data-ttu-id="c81d3-127">Om du vill ta bort alla tecken från markörens position till början av en rad trycker du på <kbd>CTRL</kbd> + <kbd>Home</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-127">To delete all the characters from the cursor's position to the beginning of a line, press <kbd>Ctrl</kbd>+<kbd>Home</kbd>.</span></span>

<span data-ttu-id="c81d3-128">Om rader har lagts till raderas tecknen från den aktuella raden och de rader som har lagts till.</span><span class="sxs-lookup"><span data-stu-id="c81d3-128">If lines were added, characters are deleted from the current line and the lines that were added.</span></span>

### <a name="insert-and-overstrike-mode"></a><span data-ttu-id="c81d3-129">Infoga och överstryknings läge</span><span class="sxs-lookup"><span data-stu-id="c81d3-129">Insert and overstrike mode</span></span>

<span data-ttu-id="c81d3-130">Om du vill ändra till överskrivnings läge trycker du på <kbd>Infoga</kbd>.</span><span class="sxs-lookup"><span data-stu-id="c81d3-130">To change to overwrite mode, press <kbd>Insert</kbd>.</span></span> <span data-ttu-id="c81d3-131">Återgå till infognings läge genom att trycka på <kbd>Infoga</kbd> igen.</span><span class="sxs-lookup"><span data-stu-id="c81d3-131">To return to insert mode, press <kbd>Insert</kbd> again.</span></span>

### <a name="tab-completion"></a><span data-ttu-id="c81d3-132">Slut för ande flik</span><span class="sxs-lookup"><span data-stu-id="c81d3-132">Tab completion</span></span>

<span data-ttu-id="c81d3-133">Du slutför ett cmdlet-namn, en parameter eller en sökväg genom att trycka på <kbd>TABB</kbd> -tangenten.</span><span class="sxs-lookup"><span data-stu-id="c81d3-133">To complete a cmdlet name, a parameter, or a path, press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="c81d3-134">Tryck på <kbd>tabbtangenten</kbd> igen om du vill bläddra i en lista med värden.</span><span class="sxs-lookup"><span data-stu-id="c81d3-134">To scroll through a list of values, press the <kbd>Tab</kbd> key again.</span></span>

## <a name="see-also"></a><span data-ttu-id="c81d3-135">Se även</span><span class="sxs-lookup"><span data-stu-id="c81d3-135">See also</span></span>

[<span data-ttu-id="c81d3-136">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="c81d3-136">about_Command_Syntax</span></span>](about_Command_Syntax.md)

[<span data-ttu-id="c81d3-137">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="c81d3-137">about_Path_Syntax</span></span>](about_Path_Syntax.md)

[<span data-ttu-id="c81d3-138">about_PSReadline</span><span class="sxs-lookup"><span data-stu-id="c81d3-138">about_PSReadline</span></span>](../../PSReadline/About/about_PSReadline.md)

