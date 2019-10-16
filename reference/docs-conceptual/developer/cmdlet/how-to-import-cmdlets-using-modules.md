---
title: Så här importerar du cmdlets med hjälp av moduler | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355547"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="ea142-102">Importera cmdlets med hjälp av moduler</span><span class="sxs-lookup"><span data-stu-id="ea142-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="ea142-103">I den här artikeln beskrivs hur du importerar cmdletar till en PowerShell-session med hjälp av en binär modul.</span><span class="sxs-lookup"><span data-stu-id="ea142-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="ea142-104">Medlemmar i moduler kan omfatta cmdlets, providrar, functions, variabler, alias och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="ea142-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="ea142-105">Snapin-moduler kan bara innehålla cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="ea142-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="ea142-106">Så här läser du in cmdletar med hjälp av en modul</span><span class="sxs-lookup"><span data-stu-id="ea142-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="ea142-107">Skapa en modul som har samma namn som den sammansättnings fil där cmdletarna implementeras.</span><span class="sxs-lookup"><span data-stu-id="ea142-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="ea142-108">I den här proceduren skapas mappen modul i mappen Windows `system32`.</span><span class="sxs-lookup"><span data-stu-id="ea142-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="ea142-109">Kontrol lera att miljövariabeln `PSModulePath` innehåller sökvägen till din nya modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="ea142-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="ea142-110">Som standard läggs System-mappen redan till i miljövariabeln `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="ea142-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="ea142-111">Om du vill visa `PSModulePath` skriver du: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="ea142-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="ea142-112">Kopiera cmdlet-sammansättningen till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="ea142-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="ea142-113">Lägg till en modul manifest fil (`.psd1`) i modulens rotmapp.</span><span class="sxs-lookup"><span data-stu-id="ea142-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="ea142-114">PowerShell använder modulen manifest för att importera modulen.</span><span class="sxs-lookup"><span data-stu-id="ea142-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="ea142-115">Mer information finns i [så här skriver du ett manifest för PowerShell-modul](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="ea142-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="ea142-116">Kör följande kommando för att lägga till cmdletarna i sessionen:</span><span class="sxs-lookup"><span data-stu-id="ea142-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="ea142-117">Den här proceduren kan användas för att testa dina cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ea142-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="ea142-118">Den lägger till alla cmdletar i sammansättningen till sessionen.</span><span class="sxs-lookup"><span data-stu-id="ea142-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="ea142-119">Mer information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="ea142-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea142-120">Se även</span><span class="sxs-lookup"><span data-stu-id="ea142-120">See also</span></span>

[<span data-ttu-id="ea142-121">Så här skriver du ett manifest för PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="ea142-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="ea142-122">Importera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="ea142-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="ea142-123">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="ea142-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="ea142-124">Installera moduler</span><span class="sxs-lookup"><span data-stu-id="ea142-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="ea142-125">Ändra installations Sök vägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="ea142-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="ea142-126">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="ea142-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
