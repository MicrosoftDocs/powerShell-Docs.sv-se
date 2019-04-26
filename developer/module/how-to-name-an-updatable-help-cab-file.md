---
title: Hur du namnger en uppdateringsbar hjälp CAB-fil | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082370"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="9a248-102">Namnge en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="9a248-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="9a248-103">Det här avsnittet beskrivs nödvändiga namnformatet för uppdateringsbar hjälp-kabinettfil (. CAB-fil) filer.</span><span class="sxs-lookup"><span data-stu-id="9a248-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="9a248-104">Namnge en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="9a248-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="9a248-105">En uppdateringsbar kabinettfil (. CAB-fil) måste ha ett namn med formatet.</span><span class="sxs-lookup"><span data-stu-id="9a248-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="9a248-106">Element i namnet är som följer.</span><span class="sxs-lookup"><span data-stu-id="9a248-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="9a248-107">Modulnamn värdet av den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="9a248-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="9a248-108">ModuleGUID värdet av den **GUID** nyckeln i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="9a248-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="9a248-109">UICulture The UI kultur hjälpfiler i CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="9a248-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="9a248-110">Det här värdet måste matcha värdet för en av de **UICulture** element i HelpInfo XML-filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="9a248-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="9a248-111">Till exempel om modulens namn är ”TestModule”, modulen GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, och kultur för Användargränssnittet är ”en-US”, namnet på CAB-filen är:</span><span class="sxs-lookup"><span data-stu-id="9a248-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`