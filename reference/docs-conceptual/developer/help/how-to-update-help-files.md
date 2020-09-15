---
title: Uppdatera hjälpfiler
ms.date: 09/12/2016
ms.openlocfilehash: 80f7c8865729515de98648765fa36ce540e00162
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892956"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="923dd-102">Uppdatera hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="923dd-102">How to Update Help Files</span></span>

<span data-ttu-id="923dd-103">I det här avsnittet beskrivs hur du uppdaterar hjälpfiler för en modul som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="923dd-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="923dd-104">Uppdaterar hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="923dd-104">Updating Help Files</span></span>

<span data-ttu-id="923dd-105">Det finns många anledningar till att uppdatera hjälpfiler, till exempel korrigera fel, för att klargöra ett koncept, besvara en vanlig fråga, lägga till nya filer eller lägga till nya och bättre exempel.</span><span class="sxs-lookup"><span data-stu-id="923dd-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="923dd-106">Så här uppdaterar du en hjälp fil:</span><span class="sxs-lookup"><span data-stu-id="923dd-106">To update a help file:</span></span>

1. <span data-ttu-id="923dd-107">Ändra filerna.</span><span class="sxs-lookup"><span data-stu-id="923dd-107">Change the files.</span></span>
1. <span data-ttu-id="923dd-108">Översätt filerna till andra användar gränssnitts kulturer.</span><span class="sxs-lookup"><span data-stu-id="923dd-108">Translate the files into other UI cultures.</span></span>
1. <span data-ttu-id="923dd-109">Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="923dd-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>
1. <span data-ttu-id="923dd-110">Validera filerna mot XML-schemat.</span><span class="sxs-lookup"><span data-stu-id="923dd-110">Validate the files against the XML schema.</span></span>
1. <span data-ttu-id="923dd-111">Återskapa CAB-filerna för varje användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="923dd-111">Rebuild the CAB files for each UI culture.</span></span>
1. <span data-ttu-id="923dd-112">I XML-filen HelpInfo ökar du versions numret för CAB-filen för varje GRÄNSSNITTs kultur.</span><span class="sxs-lookup"><span data-stu-id="923dd-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>
1. <span data-ttu-id="923dd-113">Överför de nya CAB-filerna till den plats som anges av värdet för **HelpContentUri** -elementet i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="923dd-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="923dd-114">Ersätt de äldre CAB-filerna med de nya CAB-filerna.</span><span class="sxs-lookup"><span data-stu-id="923dd-114">Replace the older CAB files with the new CAB files.</span></span>
1. <span data-ttu-id="923dd-115">Ladda upp den uppdaterade HelpInfo XML-filen till den plats som anges av **HelpInfoUri** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="923dd-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="923dd-116">Ersätt den äldre HelpInfo XML-filen med den nya filen.</span><span class="sxs-lookup"><span data-stu-id="923dd-116">Replace the older HelpInfo XML file with the new file.</span></span>
