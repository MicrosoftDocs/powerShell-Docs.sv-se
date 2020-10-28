---
ms.date: 09/12/2016
ms.topic: reference
title: Namnge en HelpInfo-XML-fil
description: Namnge en HelpInfo-XML-fil
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659046"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="ba317-103">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="ba317-103">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="ba317-104">I det här avsnittet beskrivs det obligatoriska namn formatet för filer med uppdaterings bara hjälp information, vanligt vis kallade HelpInfo XML-filer.</span><span class="sxs-lookup"><span data-stu-id="ba317-104">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="ba317-105">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="ba317-105">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="ba317-106">En HelpInfo XML-fil måste ha ett namn med följande format.</span><span class="sxs-lookup"><span data-stu-id="ba317-106">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="ba317-107">Elementen i namnet är följande.</span><span class="sxs-lookup"><span data-stu-id="ba317-107">The elements of the name are as follows.</span></span>

- <span data-ttu-id="ba317-108">`<ModuleName>` -Värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.</span><span class="sxs-lookup"><span data-stu-id="ba317-108">`<ModuleName>` - The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

- <span data-ttu-id="ba317-109">`<ModuleGUID>` – Värdet för **GUID** -nyckeln i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="ba317-109">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="ba317-110">Om modulnamnet till exempel är "TestModule" och modulens GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 är namnet på HelpInfo XML-filen för modulen:</span><span class="sxs-lookup"><span data-stu-id="ba317-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
