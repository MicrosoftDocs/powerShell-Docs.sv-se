---
title: Skapa en HelpInfo-XML-fil
ms.date: 09/13/2016
ms.openlocfilehash: e395746e51309477bbcbff51b4591de3f73ce0db
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893313"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a><span data-ttu-id="16b33-102">Skapa en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="16b33-102">How to Create a HelpInfo XML File</span></span>

<span data-ttu-id="16b33-103">I det här avsnittet beskrivs hur du skapar och fyller i en hjälp informations fil, som vanligt vis kallas "HelpInfo XML-fil", för den PowerShell-baserade hjälp funktionen.</span><span class="sxs-lookup"><span data-stu-id="16b33-103">This topics in this section explains how to create and populate a help information file, commonly known as a "HelpInfo XML file," for the PowerShell Updatable Help feature.</span></span>

## <a name="helpinfo-xml-file-overview"></a><span data-ttu-id="16b33-104">Översikt över HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="16b33-104">HelpInfo XML File Overview</span></span>

<span data-ttu-id="16b33-105">XML-filen HelpInfo är den främsta informations källan om uppdaterings bar hjälp för modulen.</span><span class="sxs-lookup"><span data-stu-id="16b33-105">The HelpInfo XML file is the primary source of information about Updatable Help for the module.</span></span> <span data-ttu-id="16b33-106">Den innehåller platsen för hjälpfilerna för modulerna, de användar gränssnitts kulturer som stöds och de versions nummer som uppdaterings bara hjälp använder för att avgöra om användaren har de senaste hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="16b33-106">It includes the location of the help files for the modules, the supported UI cultures, and the version numbers that Updatable Help uses to determine whether the user has the newest help files.</span></span>

<span data-ttu-id="16b33-107">Varje modul har bara en HelpInfo XML-fil, även om modulen innehåller flera hjälpfiler för flera användar gränssnitts kulturer.</span><span class="sxs-lookup"><span data-stu-id="16b33-107">Each module has just one HelpInfo XML file, even if the module includes multiple help files for multiple UI cultures.</span></span> <span data-ttu-id="16b33-108">Modulens författare skapar XML-filen HelpInfo och placerar den på Internet-platsen som anges av **HelpInfoUri** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="16b33-108">The module author creates the HelpInfo XML file and places it in the internet location that is specified by the **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="16b33-109">När modulens hjälpfiler uppdateras och överförs, uppdaterar modulen HelpInfo XML-filen och ersätter den ursprungliga HelpInfo XML-filen med den nya versionen.</span><span class="sxs-lookup"><span data-stu-id="16b33-109">When the module help files are updated and uploaded, the module author updates the HelpInfo XML file and replaces the original HelpInfo XML file with the new version.</span></span>

<span data-ttu-id="16b33-110">Det är viktigt att XML-filen HelpInfo underhålls noggrant.</span><span class="sxs-lookup"><span data-stu-id="16b33-110">It is critical that the HelpInfo XML file is carefully maintained.</span></span> <span data-ttu-id="16b33-111">Om du laddar upp nya filer, men glömmer att öka versions numren, kommer uppdaterings bara hjälp att ladda ned de nya filerna till användarnas datorer.</span><span class="sxs-lookup"><span data-stu-id="16b33-111">If you upload new files, but forget to increment the version numbers, Updatable Help will not download the new files to users' computers.</span></span> <span data-ttu-id="16b33-112">Om du lägger till hjälpfiler för en ny kultur för användar gränssnittet, men inte uppdaterar XML-HelpInfo eller placerar den på rätt plats, kommer uppdaterings bara hjälp att inte hämta de nya filerna.</span><span class="sxs-lookup"><span data-stu-id="16b33-112">if you add help files for a new UI culture, but don't update the HelpInfo XML file or place it in the correct location, Updatable Help will not download the new files.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="16b33-113">Innehåll i det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="16b33-113">In this section</span></span>

<span data-ttu-id="16b33-114">Det här avsnittet innehåller följande ämnen.</span><span class="sxs-lookup"><span data-stu-id="16b33-114">This section includes the following topics.</span></span>

- [<span data-ttu-id="16b33-115">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="16b33-115">HelpInfo XML Schema</span></span>](./helpinfo-xml-schema.md)

- [<span data-ttu-id="16b33-116">HelpInfo-XML-exempelfil</span><span class="sxs-lookup"><span data-stu-id="16b33-116">HelpInfo XML Sample File</span></span>](./helpinfo-xml-sample-file.md)

- [<span data-ttu-id="16b33-117">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="16b33-117">How to Name a HelpInfo XML File</span></span>](./how-to-name-a-helpinfo-xml-file.md)

- [<span data-ttu-id="16b33-118">Konfigurera versionsnummer för HelpInfo-XML-filer</span><span class="sxs-lookup"><span data-stu-id="16b33-118">How to Set HelpInfo XML Version Numbers</span></span>](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a><span data-ttu-id="16b33-119">Se även</span><span class="sxs-lookup"><span data-stu-id="16b33-119">See Also</span></span>

[<span data-ttu-id="16b33-120">Stöd för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="16b33-120">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)
