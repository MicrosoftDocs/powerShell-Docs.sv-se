---
title: Så här uppdaterar du hjälpfiler | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357423"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="11d99-102">Uppdatera hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="11d99-102">How to Update Help Files</span></span>

<span data-ttu-id="11d99-103">I det här avsnittet beskrivs hur du uppdaterar hjälpfiler för en modul som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="11d99-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="11d99-104">Uppdaterar hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="11d99-104">Updating Help Files</span></span>

<span data-ttu-id="11d99-105">Det finns många anledningar till att uppdatera hjälpfiler, till exempel korrigera fel, för att klargöra ett koncept, besvara en vanlig fråga, lägga till nya filer eller lägga till nya och bättre exempel.</span><span class="sxs-lookup"><span data-stu-id="11d99-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="11d99-106">Så här uppdaterar du en hjälp fil:</span><span class="sxs-lookup"><span data-stu-id="11d99-106">To update a help file:</span></span>

1. <span data-ttu-id="11d99-107">Ändra filerna.</span><span class="sxs-lookup"><span data-stu-id="11d99-107">Change the files.</span></span>

2. <span data-ttu-id="11d99-108">Översätt filerna till andra användar gränssnitts kulturer.</span><span class="sxs-lookup"><span data-stu-id="11d99-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="11d99-109">Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="11d99-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="11d99-110">Validera filerna mot XML-schemat.</span><span class="sxs-lookup"><span data-stu-id="11d99-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="11d99-111">Återskapa CAB-filerna för varje användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="11d99-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="11d99-112">I XML-filen HelpInfo ökar du versions numret för CAB-filen för varje GRÄNSSNITTs kultur.</span><span class="sxs-lookup"><span data-stu-id="11d99-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="11d99-113">Överför de nya CAB-filerna till den plats som anges av värdet för **HelpContentUri** -elementet i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="11d99-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="11d99-114">Ersätt de äldre CAB-filerna med de nya CAB-filerna.</span><span class="sxs-lookup"><span data-stu-id="11d99-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="11d99-115">Ladda upp den uppdaterade HelpInfo XML-filen till den plats som anges av **HelpInfoUri** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="11d99-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="11d99-116">Ersätt den äldre HelpInfo XML-filen med den nya filen.</span><span class="sxs-lookup"><span data-stu-id="11d99-116">Replace the older HelpInfo XML file with the new file.</span></span>