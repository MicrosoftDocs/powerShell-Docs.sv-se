---
title: Så här skapar du en formatering fil (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851690"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="57f6b-102">Skapa en formateringsfil (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="57f6b-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="57f6b-103">Det här avsnittet beskriver hur du skapar en formatering fil (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="57f6b-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="57f6b-104">Du kan också skapa en formatering fil genom att göra en kopia av en av filerna som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57f6b-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="57f6b-105">Om du gör en kopia av en befintlig fil, ta bort den befintliga digitala signaturen och lägga till en egen signatur i den nya filen.</span><span class="sxs-lookup"><span data-stu-id="57f6b-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="57f6b-106">Skapa en. format.ps1xml fil.</span><span class="sxs-lookup"><span data-stu-id="57f6b-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="57f6b-107">Skapa en textfil (.txt) med hjälp av en text-redigerare till exempel Anteckningar.</span><span class="sxs-lookup"><span data-stu-id="57f6b-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="57f6b-108">Kopiera följande rader till filen formatering.</span><span class="sxs-lookup"><span data-stu-id="57f6b-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="57f6b-109">Den \<Configuration >\</Configuration > taggar definierar roten `Configuration` noden.</span><span class="sxs-lookup"><span data-stu-id="57f6b-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="57f6b-110">Alla ytterligare XML-taggar ska stå inom den här noden.</span><span class="sxs-lookup"><span data-stu-id="57f6b-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="57f6b-111">Den <ViewDefinitions> </ViewDefinitions> taggar definiera den `ViewDefinitions` noden.</span><span class="sxs-lookup"><span data-stu-id="57f6b-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="57f6b-112">Alla vyer har definierats i den här noden.</span><span class="sxs-lookup"><span data-stu-id="57f6b-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="57f6b-113">Spara filen till Windows PowerShell-installationsmappen, till modulmappen eller i en undermapp till modulmappen.</span><span class="sxs-lookup"><span data-stu-id="57f6b-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="57f6b-114">Använd följande format för namn när du sparar filen: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="57f6b-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="57f6b-115">Formatering filer måste använda den `.format.ps1xml` tillägget.</span><span class="sxs-lookup"><span data-stu-id="57f6b-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="57f6b-116">Du är nu redo att lägga till vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="57f6b-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="57f6b-117">Det finns ingen gräns för antal vyer som kan definieras i en fil med formatering.</span><span class="sxs-lookup"><span data-stu-id="57f6b-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="57f6b-118">Du kan lägga till en enda vy för varje objekt, flera vyer för samma objekt eller en vy som används av flera objekt.</span><span class="sxs-lookup"><span data-stu-id="57f6b-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="57f6b-119">Se även</span><span class="sxs-lookup"><span data-stu-id="57f6b-119">See Also</span></span>

[<span data-ttu-id="57f6b-120">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="57f6b-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
