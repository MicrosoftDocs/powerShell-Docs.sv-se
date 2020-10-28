---
ms.date: 09/13/2016
ms.topic: reference
title: Moduler och snapin-moduler
description: Moduler och snapin-moduler
ms.openlocfilehash: de4ff1de9a29b78d7783fe7ed0265f5516db1fb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658684"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="c7183-103">Moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="c7183-103">Modules and Snap-ins</span></span>

<span data-ttu-id="c7183-104">Cmdletar kan läggas till i en session med hjälp av moduler (som introduceras av Windows PowerShell 2,0) eller snapin-moduler. När cmdleten har lagts till i sessionen kan den köras program mässigt av ett värd program eller interaktivt på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c7183-104">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="c7183-105">Vi rekommenderar att du använder moduler som leverans metod för att lägga till cmdlets i en session av följande anledningar:</span><span class="sxs-lookup"><span data-stu-id="c7183-105">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="c7183-106">Med moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten definieras.</span><span class="sxs-lookup"><span data-stu-id="c7183-106">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="c7183-107">Det finns inget behov av att implementera en snapin-klass.</span><span class="sxs-lookup"><span data-stu-id="c7183-107">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="c7183-108">Med moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formateringsattribut.</span><span class="sxs-lookup"><span data-stu-id="c7183-108">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="c7183-109">Snapin-moduler kan bara användas för att lägga till cmdlets och providers i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c7183-109">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7183-110">Se även</span><span class="sxs-lookup"><span data-stu-id="c7183-110">See Also</span></span>

[<span data-ttu-id="c7183-111">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="c7183-111">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="c7183-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="c7183-112">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
