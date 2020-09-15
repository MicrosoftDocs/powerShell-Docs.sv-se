---
title: Namnge en CAB-fil för uppdateringsbar hjälp
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893007"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="059d3-102">Namnge en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="059d3-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="059d3-103">I det här avsnittet förklaras det nödvändiga namn formatet för filer med uppdaterings bara hjälp skåp ( `.CAB` ).</span><span class="sxs-lookup"><span data-stu-id="059d3-103">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="059d3-104">Namnge en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="059d3-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="059d3-105">En uppdaterings bar kabinett `.CAB` fil () måste ha ett namn med följande format.</span><span class="sxs-lookup"><span data-stu-id="059d3-105">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="059d3-106">Elementen i namnet är följande.</span><span class="sxs-lookup"><span data-stu-id="059d3-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="059d3-107">`<ModuleName>` -Värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.</span><span class="sxs-lookup"><span data-stu-id="059d3-107">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="059d3-108">`<ModuleGUID>` – Värdet för **GUID** -nyckeln i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="059d3-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="059d3-109">`<UICulture>` – Användar gränssnitts kulturen för hjälpfilerna i CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="059d3-109">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="059d3-110">Värdet måste matcha värdet för ett av **värdet** -elementen i HelpInfo XML-filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="059d3-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="059d3-111">Om modulnamnet till exempel är "TestModule" är modulens GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 och användar gränssnitts kulturen är "en-US", namnet på CAB-filen skulle vara:</span><span class="sxs-lookup"><span data-stu-id="059d3-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
