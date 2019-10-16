---
title: Så här skapar du en format fil (. format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354959"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="d2a58-102">Skapa en formateringsfil (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="d2a58-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="d2a58-103">I det här avsnittet beskrivs hur du skapar en format fil (. format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="d2a58-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="d2a58-104">Du kan också skapa en fil för formatering genom att göra en kopia av en av filerna som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d2a58-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="d2a58-105">Om du gör en kopia av en befintlig fil tar du bort den befintliga digitala signaturen och lägger till din egen signatur i den nya filen.</span><span class="sxs-lookup"><span data-stu-id="d2a58-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="d2a58-106">För att skapa en. format. ps1xml-fil.</span><span class="sxs-lookup"><span data-stu-id="d2a58-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="d2a58-107">Skapa en textfil (. txt) med en text redigerare, till exempel Anteckningar.</span><span class="sxs-lookup"><span data-stu-id="d2a58-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="d2a58-108">Kopiera följande rader till format filen.</span><span class="sxs-lookup"><span data-stu-id="d2a58-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="d2a58-109">> Taggarna \<Configuration > \</Configuration definierar rot `Configuration`-noden.</span><span class="sxs-lookup"><span data-stu-id="d2a58-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="d2a58-110">Alla ytterligare XML-taggar kommer att stå inom den här noden.</span><span class="sxs-lookup"><span data-stu-id="d2a58-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="d2a58-111"><ViewDefinitions></ViewDefinitions> Taggarna definierar `ViewDefinitions`-noden.</span><span class="sxs-lookup"><span data-stu-id="d2a58-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="d2a58-112">Alla vyer definieras i den här noden.</span><span class="sxs-lookup"><span data-stu-id="d2a58-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="d2a58-113">Spara filen i installationsmappen för Windows PowerShell, till mappen modul eller till en undermapp i mappen modul.</span><span class="sxs-lookup"><span data-stu-id="d2a58-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="d2a58-114">Använd följande namn format när du sparar filen: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="d2a58-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="d2a58-115">Filer måste använda tillägget `.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="d2a58-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="d2a58-116">Nu kan du lägga till vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="d2a58-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="d2a58-117">Det finns ingen gräns för hur många vyer som kan definieras i en textfil.</span><span class="sxs-lookup"><span data-stu-id="d2a58-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="d2a58-118">Du kan lägga till en enskild vy för varje objekt, flera vyer för samma objekt eller en enskild vy som används av flera objekt.</span><span class="sxs-lookup"><span data-stu-id="d2a58-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2a58-119">Se även</span><span class="sxs-lookup"><span data-stu-id="d2a58-119">See Also</span></span>

[<span data-ttu-id="d2a58-120">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="d2a58-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
