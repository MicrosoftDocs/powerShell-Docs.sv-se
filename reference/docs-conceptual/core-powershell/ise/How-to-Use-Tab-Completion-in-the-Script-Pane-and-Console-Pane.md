---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd tabbifyllning i skriptfönstret och konsolfönstret
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="f21f4-103">Använd tabbifyllning i skriptfönstret och konsolfönstret</span><span class="sxs-lookup"><span data-stu-id="f21f4-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="f21f4-104">Flikavslutande innehåller automatisk hjälp när du skriver i rutan skript eller kommando-rutan.</span><span class="sxs-lookup"><span data-stu-id="f21f4-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="f21f4-105">Använd följande steg för att dra nytta av den här funktionen:</span><span class="sxs-lookup"><span data-stu-id="f21f4-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="f21f4-106">Att automatiskt slutföra en kommando-post</span><span class="sxs-lookup"><span data-stu-id="f21f4-106">To automatically complete a command entry</span></span>

<span data-ttu-id="f21f4-107">I kommando-fönstret eller Skriptfönster Skriv några tecken på ett kommando och tryck på TAB för att markera den önskade slutförande texten.</span><span class="sxs-lookup"><span data-stu-id="f21f4-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="f21f4-108">Om flera objekt som börjar med texten som du ursprungligen angav, fortsätter du att trycka på TABB tills objektet visas.</span><span class="sxs-lookup"><span data-stu-id="f21f4-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="f21f4-109">Flikavslutande kan hjälpa dig med att skriva en cmdlet-namn, parameternamn, variabelns namn, egenskapsnamn för objektet eller en sökväg till filen.</span><span class="sxs-lookup"><span data-stu-id="f21f4-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="f21f4-110">I rutan skript Slutför att trycka på TABB automatiskt kommandot endast när du redigerar .ps1, .psd1 eller .psm1-filer.</span><span class="sxs-lookup"><span data-stu-id="f21f4-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="f21f4-111">Flikavslutande fungerar helst när du skriver i rutan kommando.</span><span class="sxs-lookup"><span data-stu-id="f21f4-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="f21f4-112">Att automatiskt slutföra en post i cmdlet-parameter</span><span class="sxs-lookup"><span data-stu-id="f21f4-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="f21f4-113">Skriv en cmdlet som följd av ett bindestreck i fönstret rutan kommando eller skript och tryck sedan på FLIKEN.</span><span class="sxs-lookup"><span data-stu-id="f21f4-113">In the Command Pane or Script pane, type a cmdlet followed by a dash, and then press TAB.</span></span>

<span data-ttu-id="f21f4-114">Skriv till exempel `Get-Process -` och sedan på TABB flera gånger för att visa var och en av parametrarna för cmdleten i sin tur.</span><span class="sxs-lookup"><span data-stu-id="f21f4-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="f21f4-115">Se även</span><span class="sxs-lookup"><span data-stu-id="f21f4-115">See Also</span></span>

- [<span data-ttu-id="f21f4-116">Introduktion till Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f21f4-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="f21f4-117">Så här skapar du en PowerShell-fliken</span><span class="sxs-lookup"><span data-stu-id="f21f4-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)