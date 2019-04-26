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
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067628"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="976de-102">Moduler och snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="976de-102">Modules and Snap-ins</span></span>

<span data-ttu-id="976de-103">Cmdlet: ar kan läggas till en session med hjälp av snapin-modulen eller modulerna (som presenteras av Windows PowerShell 2.0). När cmdleten har lagts till i sessionen som den kan köras via programmering genom att ett program eller interaktivt på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="976de-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="976de-104">Vi rekommenderar att du använder moduler som leveransmetod för att lägga till cmdlet: ar till ett av följande skäl:</span><span class="sxs-lookup"><span data-stu-id="976de-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="976de-105">Moduler kan du lägga till cmdlets genom att läsa in sammansättningen där cmdleten har definierats.</span><span class="sxs-lookup"><span data-stu-id="976de-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="976de-106">Det finns inget behov av att implementera en snapin-klass.</span><span class="sxs-lookup"><span data-stu-id="976de-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="976de-107">Moduler kan du lägga till andra resurser, till exempel variabler, funktioner, skript, typer och formatering filer och mer.</span><span class="sxs-lookup"><span data-stu-id="976de-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="976de-108">Snapin-moduler kan användas endast för att lägga till cmdlets och providers i sessionen.</span><span class="sxs-lookup"><span data-stu-id="976de-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="976de-109">Se även</span><span class="sxs-lookup"><span data-stu-id="976de-109">See Also</span></span>

[<span data-ttu-id="976de-110">Skriva ett Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="976de-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="976de-111">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="976de-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
