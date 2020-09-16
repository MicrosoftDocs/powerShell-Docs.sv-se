---
title: Moduler och snapin-moduler | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787316"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="b2578-102">Moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="b2578-102">Modules and Snap-ins</span></span>

<span data-ttu-id="b2578-103">Cmdletar kan läggas till i en session med hjälp av moduler (som introduceras av Windows PowerShell 2,0) eller snapin-moduler. När cmdleten har lagts till i sessionen kan den köras program mässigt av ett värd program eller interaktivt på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b2578-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="b2578-104">Vi rekommenderar att du använder moduler som leverans metod för att lägga till cmdlets i en session av följande anledningar:</span><span class="sxs-lookup"><span data-stu-id="b2578-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="b2578-105">Med moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten definieras.</span><span class="sxs-lookup"><span data-stu-id="b2578-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="b2578-106">Det finns inget behov av att implementera en snapin-klass.</span><span class="sxs-lookup"><span data-stu-id="b2578-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="b2578-107">Med moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formateringsattribut.</span><span class="sxs-lookup"><span data-stu-id="b2578-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="b2578-108">Snapin-moduler kan bara användas för att lägga till cmdlets och providers i sessionen.</span><span class="sxs-lookup"><span data-stu-id="b2578-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2578-109">Se även</span><span class="sxs-lookup"><span data-stu-id="b2578-109">See Also</span></span>

[<span data-ttu-id="b2578-110">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="b2578-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="b2578-111">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="b2578-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
