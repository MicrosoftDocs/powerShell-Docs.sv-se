---
external help file: PSReadLine-help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: PSConsoleHostReadLine
ms.openlocfilehash: e02f06137395e187cfe86eb1aeb4b30dbb3f09f1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709049"
---
# <span data-ttu-id="fe2a7-102">PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="fe2a7-102">PSConsoleHostReadLine</span></span>

## <span data-ttu-id="fe2a7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fe2a7-103">SYNOPSIS</span></span>
<span data-ttu-id="fe2a7-104">Den här funktionen är den viktigaste start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-104">This function is the main entry point for PSReadLine.</span></span>

## <span data-ttu-id="fe2a7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fe2a7-105">SYNTAX</span></span>

```
PSConsoleHostReadLine
```

## <span data-ttu-id="fe2a7-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fe2a7-106">DESCRIPTION</span></span>

<span data-ttu-id="fe2a7-107">`PSConsoleHostReadLine` är huvud start punkten för PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-107">`PSConsoleHostReadLine` is the main entry point for the PSReadLine module.</span></span> <span data-ttu-id="fe2a7-108">PowerShell-konsolens värd laddar automatiskt PSReadLine-modulen och anropar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-108">The PowerShell console host automatically loads the PSReadLine module and calls this function.</span></span> <span data-ttu-id="fe2a7-109">Under normala drifts förhållanden är den här funktionen inte avsedd att användas från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-109">Under normal operating conditions, this function is not intended to be used from the command line.</span></span>

<span data-ttu-id="fe2a7-110">Tilläggs punkten `PSConsoleHostReadLine` är speciell för konsol värden.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-110">The extension point `PSConsoleHostReadLine` is special to the console host.</span></span> <span data-ttu-id="fe2a7-111">Värden anropar ett alias, en funktion eller ett skript med det här namnet.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-111">The host calls any alias, function, or script with this name.</span></span> <span data-ttu-id="fe2a7-112">PSReadLine definierar den här funktionen så att den anropas från konsol värden.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-112">PSReadLine defines this function so that it is called from the console host.</span></span>

## <span data-ttu-id="fe2a7-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fe2a7-113">EXAMPLES</span></span>

### <span data-ttu-id="fe2a7-114">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="fe2a7-114">Example 1</span></span>

<span data-ttu-id="fe2a7-115">Den här funktionen är inte avsedd att användas från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="fe2a7-115">This function is not intended to be used from the command line.</span></span>

## <span data-ttu-id="fe2a7-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fe2a7-116">PARAMETERS</span></span>

## <span data-ttu-id="fe2a7-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="fe2a7-117">INPUTS</span></span>

### <span data-ttu-id="fe2a7-118">Inga</span><span class="sxs-lookup"><span data-stu-id="fe2a7-118">None</span></span>

## <span data-ttu-id="fe2a7-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fe2a7-119">OUTPUTS</span></span>

### <span data-ttu-id="fe2a7-120">Inga</span><span class="sxs-lookup"><span data-stu-id="fe2a7-120">None</span></span>

## <span data-ttu-id="fe2a7-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fe2a7-121">NOTES</span></span>

## <span data-ttu-id="fe2a7-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fe2a7-122">RELATED LINKS</span></span>

[<span data-ttu-id="fe2a7-123">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="fe2a7-123">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

