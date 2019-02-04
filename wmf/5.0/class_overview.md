---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686448"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="391da-102">Skapa anpassade typer med hjälp av PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="391da-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="391da-103">Vi har förbättrat PowerShell-språket för att definiera klasser och andra användardefinierade typer med hjälp av formella syntax och semantik som påminner andra objektorienterat programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="391da-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="391da-104">Målet är så att utvecklare och IT-proffs kan använda PowerShell för ett bredare spektrum av användningsfall, förenkla utvecklingen av PowerShell-artefakter (t.ex DSC-resurser) och påskynda täckning av hantering av Surface-enheter.</span><span class="sxs-lookup"><span data-stu-id="391da-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="391da-105">Scenarier som stöds i den här versionen</span><span class="sxs-lookup"><span data-stu-id="391da-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="391da-106">Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket</span><span class="sxs-lookup"><span data-stu-id="391da-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="391da-107">Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterad programming konstruktioner som klasser, egenskaper, metoder, osv.</span><span class="sxs-lookup"><span data-stu-id="391da-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="391da-108">Arv support med klassen i PowerShell och klassen grundläggande DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="391da-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="391da-109">Felsöka typer med hjälp av PowerShell-språket</span><span class="sxs-lookup"><span data-stu-id="391da-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="391da-110">Skapa och hantera undantag genom att använda formella mekanismer och på rätt nivå</span><span class="sxs-lookup"><span data-stu-id="391da-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
