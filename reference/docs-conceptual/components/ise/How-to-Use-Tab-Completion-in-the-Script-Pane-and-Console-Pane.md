---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd tabbifyllning i skriptfönstret och konsolfönstret
ms.openlocfilehash: 9fcb85668673adb1de596660d37e56f6607a4064
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030990"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="782e8-103">Använd tabbifyllning i skriptfönstret och konsolfönstret</span><span class="sxs-lookup"><span data-stu-id="782e8-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="782e8-104">Tabbifyllning ger automatisk hjälp när du skriver i skriptfönstret eller kommando-rutan.</span><span class="sxs-lookup"><span data-stu-id="782e8-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="782e8-105">Använd följande steg för att dra nytta av den här funktionen:</span><span class="sxs-lookup"><span data-stu-id="782e8-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="782e8-106">Att automatiskt slutföra en kommando-post</span><span class="sxs-lookup"><span data-stu-id="782e8-106">To automatically complete a command entry</span></span>

<span data-ttu-id="782e8-107">I kommando-fönstret eller skriptfönstret, skriva några tecken på ett kommando och tryck sedan på FLIKEN för att markera den önskade slutförande-texten.</span><span class="sxs-lookup"><span data-stu-id="782e8-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="782e8-108">Om flera objekt som börjar med texten som du ursprungligen har angett och sedan fortsätta att trycka på Tab tills det önskade objektet visas.</span><span class="sxs-lookup"><span data-stu-id="782e8-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="782e8-109">Tabbifyllning kan hjälpa till med att skriva en cmdlet-namn, parameternamn, variabelnamn, objektnamn för egenskap eller en sökväg till filen.</span><span class="sxs-lookup"><span data-stu-id="782e8-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="782e8-110">I fönstret skript Slutför att trycka på TAB automatiskt ett kommando endast när du redigerar .ps1, .psd1 eller .psm1-filer.</span><span class="sxs-lookup"><span data-stu-id="782e8-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="782e8-111">Tabbifyllning fungerar som helst när du skriver i rutan kommando.</span><span class="sxs-lookup"><span data-stu-id="782e8-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="782e8-112">Att automatiskt slutföra en post i cmdlet-parameter</span><span class="sxs-lookup"><span data-stu-id="782e8-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="782e8-113">Skriv en cmdlet följt av ett tankstreck och tryck på FLIKEN i fönstret rutan för kommandot eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="782e8-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="782e8-114">Skriv exempelvis `Get-Process -` och sedan på TABB flera gånger för att visa var och en av parametrarna för cmdleten i tur och ordning.</span><span class="sxs-lookup"><span data-stu-id="782e8-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="782e8-115">Se även</span><span class="sxs-lookup"><span data-stu-id="782e8-115">See Also</span></span>

- [<span data-ttu-id="782e8-116">Introduktion till Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="782e8-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="782e8-117">Så här skapar du en PowerShell-flik</span><span class="sxs-lookup"><span data-stu-id="782e8-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
