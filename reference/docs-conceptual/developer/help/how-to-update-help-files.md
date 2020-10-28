---
ms.date: 09/12/2016
ms.topic: reference
title: Uppdatera hjälpfiler
description: Uppdatera hjälpfiler
ms.openlocfilehash: 19bf501cf91b1eb5dabb334c2179953590b40232
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649590"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="f382d-103">Uppdatera hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="f382d-103">How to Update Help Files</span></span>

<span data-ttu-id="f382d-104">I det här avsnittet beskrivs hur du uppdaterar hjälpfiler för en modul som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f382d-104">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="f382d-105">Uppdaterar hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="f382d-105">Updating Help Files</span></span>

<span data-ttu-id="f382d-106">Det finns många anledningar till att uppdatera hjälpfiler, till exempel korrigera fel, för att klargöra ett koncept, besvara en vanlig fråga, lägga till nya filer eller lägga till nya och bättre exempel.</span><span class="sxs-lookup"><span data-stu-id="f382d-106">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="f382d-107">Så här uppdaterar du en hjälp fil:</span><span class="sxs-lookup"><span data-stu-id="f382d-107">To update a help file:</span></span>

1. <span data-ttu-id="f382d-108">Ändra filerna.</span><span class="sxs-lookup"><span data-stu-id="f382d-108">Change the files.</span></span>
1. <span data-ttu-id="f382d-109">Översätt filerna till andra användar gränssnitts kulturer.</span><span class="sxs-lookup"><span data-stu-id="f382d-109">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="f382d-110">Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="f382d-110">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="f382d-111">Validera filerna mot XML-schemat.</span><span class="sxs-lookup"><span data-stu-id="f382d-111">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="f382d-112">Återskapa CAB-filerna för varje användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="f382d-112">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="f382d-113">I XML-filen HelpInfo ökar du versions numret för CAB-filen för varje GRÄNSSNITTs kultur.</span><span class="sxs-lookup"><span data-stu-id="f382d-113">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="f382d-114">Överför de nya CAB-filerna till den plats som anges av värdet för **HelpContentUri** -elementet i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="f382d-114">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="f382d-115">Ersätt de äldre CAB-filerna med de nya CAB-filerna.</span><span class="sxs-lookup"><span data-stu-id="f382d-115">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="f382d-116">Ladda upp den uppdaterade HelpInfo XML-filen till den plats som anges av **HelpInfoUri** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="f382d-116">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="f382d-117">Ersätt den äldre HelpInfo XML-filen med den nya filen.</span><span class="sxs-lookup"><span data-stu-id="f382d-117">Replace the older HelpInfo XML file with the new file.</span></span>
