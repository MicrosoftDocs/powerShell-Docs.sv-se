---
title: 'Så här importerar du cmdlet: ar med moduler | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849016"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="fb7b4-102">Importera cmdlets med hjälp av moduler</span><span class="sxs-lookup"><span data-stu-id="fb7b4-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="fb7b4-103">Det här avsnittet beskriver hur du importerar cmdlet: ar till en Windows PowerShell-session med hjälp av en binär modul.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="fb7b4-104">Medlemmarna i moduler kan innehålla cmdlets, providers, funktioner, variabler, alias och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="fb7b4-105">Snapin-moduler kan innehålla endast-cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="fb7b4-106">Hur du läser in cmdlet: ar med en modul</span><span class="sxs-lookup"><span data-stu-id="fb7b4-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="fb7b4-107">Skapa en modul-mapp som har samma namn som sammansättningsfilen där cmdletarna har implementerats.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="fb7b4-108">I den här proceduren modulmappen skapas i den `system32` mapp.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="fb7b4-109">Se till att den `PSModulePath` miljövariabeln innehåller sökvägen till den nya modulmappen.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="fb7b4-110">Som standard systemmappen har redan lagts till i `PSModulePath` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="fb7b4-111">Kopiera cmdlet-sammansättningen i modulmappen.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="fb7b4-112">Kör följande kommando för att lägga till cmdlets till sessionen:</span><span class="sxs-lookup"><span data-stu-id="fb7b4-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="fb7b4-113">Den här proceduren kan användas för att testa dina cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="fb7b4-114">Det lägger till alla cmdletar i sammansättningen till sessionen.</span><span class="sxs-lookup"><span data-stu-id="fb7b4-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="fb7b4-115">Mer information om de olika typerna av moduler, olika sätt att läsa in moduler och hur du begränsar den del av en modul som exporteras, finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="fb7b4-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb7b4-116">Se även</span><span class="sxs-lookup"><span data-stu-id="fb7b4-116">See Also</span></span>

[<span data-ttu-id="fb7b4-117">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fb7b4-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="fb7b4-118">Installera moduler</span><span class="sxs-lookup"><span data-stu-id="fb7b4-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)