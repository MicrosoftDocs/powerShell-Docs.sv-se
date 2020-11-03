---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: a404461e2b92f269d581b18c3ebe7643aa86c3a4
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2020
ms.locfileid: "93269817"
---
# <span data-ttu-id="00078-103">PSReadLine-modul</span><span class="sxs-lookup"><span data-stu-id="00078-103">PSReadLine Module</span></span>

## <span data-ttu-id="00078-104">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="00078-104">Description</span></span>

<span data-ttu-id="00078-105">Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00078-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="00078-106">De här artiklarna dokumenten PSReadLine v 2.0.</span><span class="sxs-lookup"><span data-stu-id="00078-106">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="00078-107">Den här versionen levereras i PowerShell V6 och Windows 10 oktober 2018-uppdateringen (build 1809).</span><span class="sxs-lookup"><span data-stu-id="00078-107">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="00078-108">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="00078-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="00078-109">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="00078-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="00078-110">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="00078-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="00078-111">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="00078-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="00078-112">PSReadLine-cmdletar</span><span class="sxs-lookup"><span data-stu-id="00078-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="00078-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="00078-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="00078-114">Den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="00078-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="00078-115">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="00078-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="00078-116">Hämtar de kopplade nyckel funktionerna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="00078-116">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="00078-117">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="00078-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="00078-118">Hämtar värden för de alternativ som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="00078-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="00078-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="00078-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="00078-120">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="00078-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="00078-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="00078-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="00078-122">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="00078-122">Removes a key binding.</span></span>

### [<span data-ttu-id="00078-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="00078-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="00078-124">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="00078-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="00078-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="00078-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="00078-126">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="00078-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

