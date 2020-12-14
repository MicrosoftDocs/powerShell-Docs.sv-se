---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 5714753b-2afd-4492-a5fd-01d9e2cff8b5
Module Name: PSReadLine
ms.date: 02/10/2020
schema: 2.0.0
title: PSReadLine
ms.openlocfilehash: da71d4ef896befaadd7ed64f9a013dc19508a54c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709043"
---
# <span data-ttu-id="fb6ef-102">PSReadLine-modul</span><span class="sxs-lookup"><span data-stu-id="fb6ef-102">PSReadLine Module</span></span>

## <span data-ttu-id="fb6ef-103">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fb6ef-103">Description</span></span>

<span data-ttu-id="fb6ef-104">Modulen PSReadLine innehåller cmdletar som gör att du kan anpassa redigerings miljön för kommando tolken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-104">The PSReadLine module contains cmdlets that let you customize the command-line editing environment in PowerShell.</span></span> <span data-ttu-id="fb6ef-105">De här artiklarna dokumenten PSReadLine v 2.0.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-105">These articles documents PSReadLine v2.0.</span></span> <span data-ttu-id="fb6ef-106">Den här versionen levereras i PowerShell V6 och Windows 10 oktober 2018-uppdateringen (build 1809).</span><span class="sxs-lookup"><span data-stu-id="fb6ef-106">This version ships in PowerShell v6 and the Windows 10 October 2018 Update (Build 1809).</span></span>

> [!NOTE]
> <span data-ttu-id="fb6ef-107">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-107">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="fb6ef-108">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-108">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="fb6ef-109">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-109">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="fb6ef-110">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-110">You can manually load the module if necessary.</span></span>

## <span data-ttu-id="fb6ef-111">PSReadLine-cmdletar</span><span class="sxs-lookup"><span data-stu-id="fb6ef-111">PSReadLine Cmdlets</span></span>

### [<span data-ttu-id="fb6ef-112">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="fb6ef-112">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="fb6ef-113">Den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-113">The main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="fb6ef-114">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="fb6ef-114">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)
<span data-ttu-id="fb6ef-115">Hämtar de kopplade nyckel funktionerna för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-115">Gets the bound key functions for the PSReadLine module.</span></span>

### [<span data-ttu-id="fb6ef-116">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="fb6ef-116">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)
<span data-ttu-id="fb6ef-117">Hämtar värden för de alternativ som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-117">Gets values for the options that can be configured.</span></span>

### [<span data-ttu-id="fb6ef-118">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="fb6ef-118">PSConsoleHostReadLine</span></span>](PSConsoleHostReadLine.md)
<span data-ttu-id="fb6ef-119">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-119">This function is the main entry point for PSReadLine.</span></span>

### [<span data-ttu-id="fb6ef-120">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="fb6ef-120">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)
<span data-ttu-id="fb6ef-121">Tar bort en nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-121">Removes a key binding.</span></span>

### [<span data-ttu-id="fb6ef-122">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="fb6ef-122">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
<span data-ttu-id="fb6ef-123">Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-123">Binds keys to user-defined or PSReadLine key handler functions.</span></span>

### [<span data-ttu-id="fb6ef-124">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="fb6ef-124">Set-PSReadLineOption</span></span>](Set-PSReadLineOption.md)
<span data-ttu-id="fb6ef-125">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="fb6ef-125">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

