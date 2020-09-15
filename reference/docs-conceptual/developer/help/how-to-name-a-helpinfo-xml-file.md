---
title: Namnge en HelpInfo-XML-fil
ms.date: 09/12/2016
ms.openlocfilehash: 9505a7f66852a569d25ac0c1be86e68f870a7930
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892939"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="60d60-102">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="60d60-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="60d60-103">I det här avsnittet beskrivs det obligatoriska namn formatet för filer med uppdaterings bara hjälp information, vanligt vis kallade HelpInfo XML-filer.</span><span class="sxs-lookup"><span data-stu-id="60d60-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="60d60-104">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="60d60-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="60d60-105">En HelpInfo XML-fil måste ha ett namn med följande format.</span><span class="sxs-lookup"><span data-stu-id="60d60-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="60d60-106">Elementen i namnet är följande.</span><span class="sxs-lookup"><span data-stu-id="60d60-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="60d60-107">`<ModuleName>` -Värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.</span><span class="sxs-lookup"><span data-stu-id="60d60-107">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="60d60-108">`<ModuleGUID>` – Värdet för **GUID** -nyckeln i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="60d60-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="60d60-109">Om modulnamnet till exempel är "TestModule" och modulens GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 är namnet på HelpInfo XML-filen för modulen:</span><span class="sxs-lookup"><span data-stu-id="60d60-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
