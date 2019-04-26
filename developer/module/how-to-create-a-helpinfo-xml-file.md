---
title: Så här skapar du en HelpInfo XML-fil | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082421"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="163db-102">Skapa en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="163db-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="163db-103">Detta avsnitt i det här avsnittet beskrivs hur du skapar och fyller ett information hjälpfilen kallas en ”HelpInfo XML-fil”, för funktionen Windows PowerShell uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="163db-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="163db-104">Översikt över HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="163db-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="163db-105">HelpInfo XML-filen är den primära källan för information om uppdateringsbar hjälp för modulen.</span><span class="sxs-lookup"><span data-stu-id="163db-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="163db-106">Den innehåller platsen för hjälpfilerna för moduler, kulturer som stöds Användargränssnittet och versionsnumren som uppdateringsbar hjälp använder för att avgöra om användaren har de senaste hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="163db-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="163db-107">Varje modul har bara ett HelpInfo XML-fil, även om modulen innehåller flera hjälpfilerna för flera Användargränssnittet kulturer.</span><span class="sxs-lookup"><span data-stu-id="163db-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="163db-108">Modulägaren skapar HelpInfo XML-filen och placerar den i den Internet-plats som anges av den **HelpInfoUri** nyckeln i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="163db-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="163db-109">När modulen hjälpfilerna är uppdaterade och överförts, modulägaren uppdaterar HelpInfo XML-filen och ersätter den ursprungliga HelpInfo XML-filen med den nya versionen.</span><span class="sxs-lookup"><span data-stu-id="163db-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="163db-110">Det är viktigt att upprätthålls noggrant HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="163db-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="163db-111">Om du överför nya filer, men glömmer att öka versionsnumren, hämtas uppdateringsbar hjälp inte de nya filerna till användarna.</span><span class="sxs-lookup"><span data-stu-id="163db-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="163db-112">Om du lägger till hjälpfilerna för en ny UI-kultur, men inte uppdatera HelpInfo XML-filen eller placera den på rätt plats, hämta uppdateringsbar hjälp inte de nya filerna skapas.</span><span class="sxs-lookup"><span data-stu-id="163db-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="163db-113">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="163db-113">In this section</span></span>

<span data-ttu-id="163db-114">Det här avsnittet innehåller följande ämnen.</span><span class="sxs-lookup"><span data-stu-id="163db-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="163db-115">HelpInfo XML-Schema</span><span class="sxs-lookup"><span data-stu-id="163db-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="163db-116">HelpInfo XML-exempelfilen</span><span class="sxs-lookup"><span data-stu-id="163db-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="163db-117">Hur du namnger en HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="163db-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="163db-118">Hur du ställer in HelpInfo XML-versionsnummer</span><span class="sxs-lookup"><span data-stu-id="163db-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="163db-119">Se även</span><span class="sxs-lookup"><span data-stu-id="163db-119">See Also</span></span>

[<span data-ttu-id="163db-120">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="163db-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)