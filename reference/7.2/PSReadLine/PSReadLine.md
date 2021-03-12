---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: 9425f72ce4002fa871ef6b687d76f92ddf6b489e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103193896"
---
# <span data-ttu-id="12ae1-102">PSReadLine-modul</span><span class="sxs-lookup"><span data-stu-id="12ae1-102">PSReadLine Module</span></span>

## <span data-ttu-id="12ae1-103">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12ae1-103">Description</span></span>

<span data-ttu-id="12ae1-104">Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12ae1-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="12ae1-105">De här artiklarna dokumenterar den aktuella Beta versionen av PSReadLine v-2.2.0.</span><span class="sxs-lookup"><span data-stu-id="12ae1-105">These articles document the current beta version of PSReadLine v2.2.0.</span></span>

> [!NOTE]
> <span data-ttu-id="12ae1-106">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="12ae1-106">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="12ae1-107">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="12ae1-107">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="12ae1-108">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="12ae1-108">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="12ae1-109">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="12ae1-109">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="12ae1-110">PSReadLine-cmdletar</span><span class="sxs-lookup"><span data-stu-id="12ae1-110">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="12ae1-111">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="12ae1-111">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="12ae1-112">Den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="12ae1-112">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="12ae1-113">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="12ae1-113">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="12ae1-114">Hämtar de kopplade nyckel funktionerna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="12ae1-114">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="12ae1-115">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="12ae1-115">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="12ae1-116">Hämtar värden för de alternativ som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="12ae1-116">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="12ae1-117">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="12ae1-117">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="12ae1-118">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="12ae1-118">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="12ae1-119">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="12ae1-119">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="12ae1-120">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="12ae1-120">Removes a key binding.</span></span>

### [<span data-ttu-id="12ae1-121">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="12ae1-121">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="12ae1-122">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="12ae1-122">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="12ae1-123">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="12ae1-123">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="12ae1-124">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="12ae1-124">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

