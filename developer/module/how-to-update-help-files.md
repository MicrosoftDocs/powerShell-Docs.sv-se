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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846482"
---
# <a name="how-to-update-help-files"></a><span data-ttu-id="58d61-102">Uppdatera hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="58d61-102">How to Update Help Files</span></span>

<span data-ttu-id="58d61-103">Det här avsnittet förklarar hur du uppdaterar hjälpfilerna för en modul som har stöd för uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="58d61-103">This topic explains how to update help files for a module that supports Updatable Help.</span></span>

## <a name="updating-help-files"></a><span data-ttu-id="58d61-104">Uppdaterar hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="58d61-104">Updating Help Files</span></span>

<span data-ttu-id="58d61-105">Det finns många skäl att uppdatera hjälpfiler, till exempel hur du korrigerar fel, förstå ett koncept, besvara vanliga frågor, att lägga till nya filer eller att lägga till nya och bättre exempel.</span><span class="sxs-lookup"><span data-stu-id="58d61-105">There are many reasons to update help files, such as correcting errors, clarifying a concept, answering a frequently-asked question, adding new files, or adding new and better examples.</span></span>

<span data-ttu-id="58d61-106">Så här uppdaterar en hjälpfilen:</span><span class="sxs-lookup"><span data-stu-id="58d61-106">To update a help file:</span></span>

1. <span data-ttu-id="58d61-107">Ändra filerna.</span><span class="sxs-lookup"><span data-stu-id="58d61-107">Change the files.</span></span>

2. <span data-ttu-id="58d61-108">Omvandla filerna till andra UI-kulturer.</span><span class="sxs-lookup"><span data-stu-id="58d61-108">Translate the files into other UI cultures.</span></span>

3. <span data-ttu-id="58d61-109">Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje UI-kultur.</span><span class="sxs-lookup"><span data-stu-id="58d61-109">Collect all help files (new, changed, and unchanged) for the module in each UI culture.</span></span>

4. <span data-ttu-id="58d61-110">Validera filerna mot XML-schema.</span><span class="sxs-lookup"><span data-stu-id="58d61-110">Validate the files against the XML schema.</span></span>

5. <span data-ttu-id="58d61-111">Återskapa CAB-filer för varje UI-kultur.</span><span class="sxs-lookup"><span data-stu-id="58d61-111">Rebuild the CAB files for each UI culture.</span></span>

6. <span data-ttu-id="58d61-112">Öka versionsnumren för CAB-filen för varje UI-kultur i HelpInfo XML-fil.</span><span class="sxs-lookup"><span data-stu-id="58d61-112">In the HelpInfo XML file, increment the version numbers of the CAB file for each UI culture.</span></span>

7. <span data-ttu-id="58d61-113">Ladda upp nya CAB-filer till den plats som anges av värdet för den **HelpContentUri** element i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="58d61-113">Upload the new CAB files to the location that is specified by the value of the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="58d61-114">Ersätt de äldre CAB-filerna med de nya CAB-filerna.</span><span class="sxs-lookup"><span data-stu-id="58d61-114">Replace the older CAB files with the new CAB files.</span></span>

8. <span data-ttu-id="58d61-115">Överföra den uppdaterade HelpInfo XML-filen till den plats som anges av den **HelpInfoUri** nyckeln i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="58d61-115">Upload the updated HelpInfo XML file to the location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="58d61-116">Ersätt den äldre HelpInfo XML-filen med den nya filen.</span><span class="sxs-lookup"><span data-stu-id="58d61-116">Replace the older HelpInfo XML file with the new file.</span></span>