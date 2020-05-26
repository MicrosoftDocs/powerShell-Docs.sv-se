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
ms.openlocfilehash: 1f09146a9e6456584f67edb52407193d8a9330ce
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811298"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="f9ef0-102">Skapa en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="f9ef0-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="f9ef0-103">I det här avsnittet beskrivs hur du skapar och fyller i en hjälp informations fil, som kallas för en "HelpInfo XML-fil", för den uppdaterings bara hjälp funktionen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the Windows PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="f9ef0-104">Översikt över HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="f9ef0-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="f9ef0-105">XML-filen HelpInfo är den främsta informations källan om uppdaterings bar hjälp för modulen.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="f9ef0-106">Den innehåller platsen för hjälpfilerna för modulerna, de användar gränssnitts kulturer som stöds och de versions nummer som uppdaterings bara hjälp använder för att avgöra om användaren har de senaste hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="f9ef0-107">Varje modul har bara en HelpInfo XML-fil, även om modulen innehåller flera hjälpfiler för flera användar gränssnitts kulturer.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="f9ef0-108">Modulens författare skapar XML-filen HelpInfo och placerar den på Internet-platsen som anges av **HelpInfoUri** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-108">The module author creates the HelpInfo XML file and places it in the Internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="f9ef0-109">När modulens hjälpfiler uppdateras och överförs, uppdaterar modulen HelpInfo XML-filen och ersätter den ursprungliga HelpInfo XML-filen med den nya versionen.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="f9ef0-110">Det är viktigt att XML-filen HelpInfo underhålls noggrant.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="f9ef0-111">Om du laddar upp nya filer, men glömmer att öka versions numren, kommer uppdaterings bara hjälp att ladda ned de nya filerna till användarnas datorer.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="f9ef0-112">Om du lägger till hjälpfiler för en ny kultur för användar gränssnittet, men inte uppdaterar XML-HelpInfo eller placerar den på rätt plats, kommer uppdaterings bara hjälp att inte hämta de nya filerna.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f9ef0-113">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="f9ef0-113">In this section</span></span>

<span data-ttu-id="f9ef0-114">Det här avsnittet innehåller följande ämnen.</span><span class="sxs-lookup"><span data-stu-id="f9ef0-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="f9ef0-115">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="f9ef0-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="f9ef0-116">HelpInfo-XML-exempelfil</span><span class="sxs-lookup"><span data-stu-id="f9ef0-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="f9ef0-117">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="f9ef0-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="f9ef0-118">Konfigurera versionsnummer för HelpInfo-XML-filer</span><span class="sxs-lookup"><span data-stu-id="f9ef0-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="f9ef0-119">Se även</span><span class="sxs-lookup"><span data-stu-id="f9ef0-119">See Also</span></span>

[<span data-ttu-id="f9ef0-120">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="f9ef0-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
