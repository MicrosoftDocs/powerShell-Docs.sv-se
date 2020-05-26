---
title: Moduler och snapin-moduler | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: b3d8209ea7e3e8353e73ebce1531991ec9519c74
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811165"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="079d3-102">Moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="079d3-102">Modules and Snap-ins</span></span>

<span data-ttu-id="079d3-103">Cmdletar kan läggas till i en session med hjälp av moduler (som introduceras av Windows PowerShell 2,0) eller snapin-moduler. När cmdleten har lagts till i sessionen kan den köras program mässigt av ett värd program eller interaktivt på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="079d3-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="079d3-104">Vi rekommenderar att du använder moduler som leverans metod för att lägga till cmdlets i en session av följande anledningar:</span><span class="sxs-lookup"><span data-stu-id="079d3-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="079d3-105">Med moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten definieras.</span><span class="sxs-lookup"><span data-stu-id="079d3-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="079d3-106">Det finns inget behov av att implementera en snapin-klass.</span><span class="sxs-lookup"><span data-stu-id="079d3-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="079d3-107">Med moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formateringsattribut.</span><span class="sxs-lookup"><span data-stu-id="079d3-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="079d3-108">Snapin-moduler kan bara användas för att lägga till cmdlets och providers i sessionen.</span><span class="sxs-lookup"><span data-stu-id="079d3-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="079d3-109">Se även</span><span class="sxs-lookup"><span data-stu-id="079d3-109">See Also</span></span>

[<span data-ttu-id="079d3-110">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="079d3-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="079d3-111">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="079d3-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
