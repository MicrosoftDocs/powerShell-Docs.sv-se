---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa en formateringsfil (.format.ps1xml)
description: Skapa en formateringsfil (.format.ps1xml)
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652008"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="0f882-103">Skapa en formateringsfil (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="0f882-103">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="0f882-104">I det här avsnittet beskrivs hur du skapar en format fil (.format.ps1XML).</span><span class="sxs-lookup"><span data-stu-id="0f882-104">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="0f882-105">Du kan också skapa en fil för formatering genom att göra en kopia av en av filerna som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f882-105">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="0f882-106">Om du gör en kopia av en befintlig fil tar du bort den befintliga digitala signaturen och lägger till din egen signatur i den nya filen.</span><span class="sxs-lookup"><span data-stu-id="0f882-106">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="0f882-107">För att skapa en .format.ps1XML-fil.</span><span class="sxs-lookup"><span data-stu-id="0f882-107">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="0f882-108">Skapa en textfil (. txt) med en text redigerare, till exempel Anteckningar.</span><span class="sxs-lookup"><span data-stu-id="0f882-108">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="0f882-109">Kopiera följande rader till format filen.</span><span class="sxs-lookup"><span data-stu-id="0f882-109">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="0f882-110">`<Configuration></Configuration>`Taggarna definierar rotnoden `Configuration` .</span><span class="sxs-lookup"><span data-stu-id="0f882-110">The `<Configuration></Configuration>` tags define the root `Configuration` node.</span></span> <span data-ttu-id="0f882-111">Alla ytterligare XML-taggar kommer att stå inom den här noden.</span><span class="sxs-lookup"><span data-stu-id="0f882-111">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="0f882-112">`<ViewDefinitions></ViewDefinitions>`Taggarna definierar `ViewDefinitions` noden.</span><span class="sxs-lookup"><span data-stu-id="0f882-112">The `<ViewDefinitions></ViewDefinitions>` tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="0f882-113">Alla vyer definieras i den här noden.</span><span class="sxs-lookup"><span data-stu-id="0f882-113">All views are defined within this node.</span></span>

3. <span data-ttu-id="0f882-114">Spara filen i installationsmappen för Windows PowerShell, till mappen modul eller till en undermapp i mappen modul.</span><span class="sxs-lookup"><span data-stu-id="0f882-114">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="0f882-115">Använd följande namn format när du sparar filen:  `MyFile.format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="0f882-115">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="0f882-116">Filer måste använda `.format.ps1xml` tillägget.</span><span class="sxs-lookup"><span data-stu-id="0f882-116">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="0f882-117">Nu kan du lägga till vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="0f882-117">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="0f882-118">Det finns ingen gräns för hur många vyer som kan definieras i en textfil.</span><span class="sxs-lookup"><span data-stu-id="0f882-118">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="0f882-119">Du kan lägga till en enskild vy för varje objekt, flera vyer för samma objekt eller en enskild vy som används av flera objekt.</span><span class="sxs-lookup"><span data-stu-id="0f882-119">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f882-120">Se även</span><span class="sxs-lookup"><span data-stu-id="0f882-120">See Also</span></span>

[<span data-ttu-id="0f882-121">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="0f882-121">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
