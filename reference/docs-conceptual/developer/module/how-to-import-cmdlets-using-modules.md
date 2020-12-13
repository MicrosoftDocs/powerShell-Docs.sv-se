---
ms.date: 08/28/2019
ms.topic: reference
title: Importera cmdlets med hjälp av moduler
description: Importera cmdlets med hjälp av moduler
ms.openlocfilehash: 485a4be4d2accaf050a6536e7f92a0673f62a30b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657295"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="f6a29-103">Importera cmdlets med hjälp av moduler</span><span class="sxs-lookup"><span data-stu-id="f6a29-103">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="f6a29-104">I den här artikeln beskrivs hur du importerar cmdletar till en PowerShell-session med hjälp av en binär modul.</span><span class="sxs-lookup"><span data-stu-id="f6a29-104">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="f6a29-105">Medlemmar i moduler kan omfatta cmdlets, providrar, functions, variabler, alias och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="f6a29-105">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="f6a29-106">Snapin-moduler kan bara innehålla cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="f6a29-106">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="f6a29-107">Så här läser du in cmdletar med hjälp av en modul</span><span class="sxs-lookup"><span data-stu-id="f6a29-107">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="f6a29-108">Skapa en modul som har samma namn som den sammansättnings fil där cmdletarna implementeras.</span><span class="sxs-lookup"><span data-stu-id="f6a29-108">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="f6a29-109">I den här proceduren skapas mappen modul i Windows- `system32` mappen.</span><span class="sxs-lookup"><span data-stu-id="f6a29-109">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="f6a29-110">Kontrol lera att `PSModulePath` miljövariabeln innehåller sökvägen till din nya modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="f6a29-110">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="f6a29-111">Som standard har System-mappen redan lagts till i `PSModulePath` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="f6a29-111">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="f6a29-112">Om du vill visa `PSModulePath` skriver du: `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="f6a29-112">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="f6a29-113">Kopiera cmdlet-sammansättningen till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="f6a29-113">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="f6a29-114">Lägg till en modul för manifest fil ( `.psd1` ) i modulens rotmapp.</span><span class="sxs-lookup"><span data-stu-id="f6a29-114">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="f6a29-115">PowerShell använder modulen manifest för att importera modulen.</span><span class="sxs-lookup"><span data-stu-id="f6a29-115">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="f6a29-116">Mer information finns i [så här skriver du ett manifest för PowerShell-modul](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f6a29-116">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="f6a29-117">Kör följande kommando för att lägga till cmdletarna i sessionen:</span><span class="sxs-lookup"><span data-stu-id="f6a29-117">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="f6a29-118">Den här proceduren kan användas för att testa dina cmdletar.</span><span class="sxs-lookup"><span data-stu-id="f6a29-118">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="f6a29-119">Den lägger till alla cmdletar i sammansättningen till sessionen.</span><span class="sxs-lookup"><span data-stu-id="f6a29-119">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="f6a29-120">Mer information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="f6a29-120">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6a29-121">Se även</span><span class="sxs-lookup"><span data-stu-id="f6a29-121">See also</span></span>

[<span data-ttu-id="f6a29-122">Skriva ett PowerShell-modulmanifest</span><span class="sxs-lookup"><span data-stu-id="f6a29-122">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="f6a29-123">Importera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="f6a29-123">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="f6a29-124">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="f6a29-124">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="f6a29-125">Installera moduler</span><span class="sxs-lookup"><span data-stu-id="f6a29-125">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="f6a29-126">Ändra installationssökvägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="f6a29-126">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="f6a29-127">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6a29-127">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
