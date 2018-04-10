---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7eaa4dfb68bc299ad31bce81af96b6a760c4fcc5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="85cdf-102">Skapa anpassade typer med hjälp av PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="85cdf-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="85cdf-103">Vi har förbättrat PowerShell-språk för att definiera klasser och andra användardefinierade typer med hjälp av formella syntax och semantik som liknar andra objektorienterad programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="85cdf-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="85cdf-104">Målet är att utvecklare och IT-proffs att använda PowerShell för ett brett spektrum av användningsområden, förenkla utvecklingen av PowerShell artefakter (t.ex DSC-resurser) och påskynda täckning av management.</span><span class="sxs-lookup"><span data-stu-id="85cdf-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="85cdf-105">Scenarier som stöds i den här versionen</span><span class="sxs-lookup"><span data-stu-id="85cdf-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="85cdf-106">Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språk</span><span class="sxs-lookup"><span data-stu-id="85cdf-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="85cdf-107">Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterad programming konstruktioner, till exempel klasser, egenskaper, metoder och så vidare.</span><span class="sxs-lookup"><span data-stu-id="85cdf-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="85cdf-108">Arv support med klassen i PowerShell och klassen grundläggande DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="85cdf-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="85cdf-109">Felsöka typer med hjälp av PowerShell-språk</span><span class="sxs-lookup"><span data-stu-id="85cdf-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="85cdf-110">Skapa och hantera undantag med hjälp av formella metoder och på rätt nivå</span><span class="sxs-lookup"><span data-stu-id="85cdf-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>