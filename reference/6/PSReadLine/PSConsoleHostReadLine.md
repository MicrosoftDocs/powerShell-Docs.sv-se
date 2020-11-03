---
external help file: PSReadLine-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: 339c1b0c4f241c243e7c526f3353a614c3bfd6d2
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273188"
---
# <span data-ttu-id="b4281-103">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="b4281-103">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="b4281-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b4281-104">SYNOPSIS</span></span>
<span data-ttu-id="b4281-105">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b4281-105">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="b4281-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b4281-106">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="b4281-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b4281-107">DESCRIPTION</span></span>

<span data-ttu-id="b4281-108">`PSConsoleHostReadLine` är huvud start punkten för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="b4281-108">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="b4281-109">PowerShell-konsolens värd laddar automatiskt PSReadLine-modulen och anropar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="b4281-109">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="b4281-110">Under normala drifts förhållanden är den här funktionen inte avsedd att användas från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b4281-110">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="b4281-111">Tilläggs punkten `PSConsoleHostReadLine` är speciell för konsol värden.</span><span class="sxs-lookup"><span data-stu-id="b4281-111">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="b4281-112">Värden anropar ett alias, en funktion eller ett skript med det här namnet.</span><span class="sxs-lookup"><span data-stu-id="b4281-112">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="b4281-113">PSReadLine definierar den här funktionen så att den anropas från konsol värden.</span><span class="sxs-lookup"><span data-stu-id="b4281-113">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="b4281-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b4281-114">EXAMPLES</span></span>

### <span data-ttu-id="b4281-115">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="b4281-115">Example 1</span></span>

<span data-ttu-id="b4281-116">Den här funktionen är inte avsedd att användas från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b4281-116">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="b4281-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b4281-117">PARAMETERS</span></span>

## <span data-ttu-id="b4281-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="b4281-118">INPUTS</span></span>

### <span data-ttu-id="b4281-119">Inget</span><span class="sxs-lookup"><span data-stu-id="b4281-119">None</span></span>

## <span data-ttu-id="b4281-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b4281-120">OUTPUTS</span></span>

### <span data-ttu-id="b4281-121">Inget</span><span class="sxs-lookup"><span data-stu-id="b4281-121">None</span></span>

## <span data-ttu-id="b4281-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b4281-122">NOTES</span></span>

## <span data-ttu-id="b4281-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b4281-123">RELATED LINKS</span></span>

[<span data-ttu-id="b4281-124">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b4281-124">about_PSReadLine</span></span>](./About/about_PSReadLine.md)
