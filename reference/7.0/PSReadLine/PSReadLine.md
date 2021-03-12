---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113630
Help Version: 7.0.1.0
keywords: powershell
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: fc059318507b7a875eedf47692c1b6e3572efbbc
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195550"
---
# <span data-ttu-id="c2226-103">PSReadLine-modul</span><span class="sxs-lookup"><span data-stu-id="c2226-103">PSReadLine Module</span></span>

## <span data-ttu-id="c2226-104">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c2226-104">Description</span></span>

<span data-ttu-id="c2226-105">Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2226-105">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="c2226-106">Dessa artiklar dokument PSReadLine v 2.0.</span><span class="sxs-lookup"><span data-stu-id="c2226-106">These articles document PSReadLine v2.0.</span></span> <span data-ttu-id="c2226-107">Den här versionen levereras i PowerShell V6 och Windows 10 oktober 2018-uppdateringen (build 1809).</span><span class="sxs-lookup"><span data-stu-id="c2226-107">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="c2226-108">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="c2226-108">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="c2226-109">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="c2226-109">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="c2226-110">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="c2226-110">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="c2226-111">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="c2226-111">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="c2226-112">PSReadLine-cmdletar</span><span class="sxs-lookup"><span data-stu-id="c2226-112">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="c2226-113">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="c2226-113">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="c2226-114">Den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c2226-114">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="c2226-115">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c2226-115">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="c2226-116">Hämtar nyckel bindningarna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="c2226-116">Gets the key bindings for the PSReadLine module.</span></span>

### [<span data-ttu-id="c2226-117">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c2226-117">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="c2226-118">Hämtar värden för de alternativ som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="c2226-118">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="c2226-119">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="c2226-119">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="c2226-120">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="c2226-120">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="c2226-121">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c2226-121">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="c2226-122">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="c2226-122">Removes a key binding.</span></span>

### [<span data-ttu-id="c2226-123">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="c2226-123">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="c2226-124">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="c2226-124">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="c2226-125">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="c2226-125">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="c2226-126">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="c2226-126">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

