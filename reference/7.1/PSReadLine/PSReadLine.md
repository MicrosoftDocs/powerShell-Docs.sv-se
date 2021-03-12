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
ms.openlocfilehash: 3adfa4be7aae03120d2334a57c39d7e6351bcb16
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196215"
---
# <span data-ttu-id="dacb3-103">PSReadLine-modul</span><span class="sxs-lookup"><span data-stu-id="dacb3-103">PSReadLine Module</span></span>

## <span data-ttu-id="dacb3-104">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dacb3-104">Description</span></span>

<span data-ttu-id="dacb3-105">Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dacb3-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="dacb3-106">PowerShell 7,1 levereras med PSReadLine v 2.1.</span><span class="sxs-lookup"><span data-stu-id="dacb3-106">PowerShell 7.1 shipped with PSReadLine v2.1.</span></span> <span data-ttu-id="dacb3-107">Dessa artiklar dokument PSReadLine v 2.1.</span><span class="sxs-lookup"><span data-stu-id="dacb3-107">These articles document PSReadLine v2.1.</span></span>

> [!NOTE]
> <span data-ttu-id="dacb3-108">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="dacb3-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="dacb3-109">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="dacb3-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="dacb3-110">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="dacb3-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="dacb3-111">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="dacb3-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="dacb3-112">PSReadLine-cmdletar</span><span class="sxs-lookup"><span data-stu-id="dacb3-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="dacb3-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="dacb3-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="dacb3-114">Den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="dacb3-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="dacb3-115">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="dacb3-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="dacb3-116">Hämtar de kopplade nyckel funktionerna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="dacb3-116">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="dacb3-117">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="dacb3-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="dacb3-118">Hämtar värden för de alternativ som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="dacb3-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="dacb3-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="dacb3-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="dacb3-120">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="dacb3-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="dacb3-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="dacb3-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="dacb3-122">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="dacb3-122">Removes a key binding.</span></span>

### [<span data-ttu-id="dacb3-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="dacb3-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="dacb3-124">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="dacb3-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="dacb3-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="dacb3-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="dacb3-126">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="dacb3-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

