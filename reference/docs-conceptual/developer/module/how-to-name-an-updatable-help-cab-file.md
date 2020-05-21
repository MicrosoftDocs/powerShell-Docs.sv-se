---
title: Så här namnger du en uppdaterings bar CAB-fil | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560567"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="5dbea-102">Namnge en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="5dbea-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="5dbea-103">I det här avsnittet beskrivs det namn format som krävs för det uppdaterbara hjälp skåpet (. CAB-filer).</span><span class="sxs-lookup"><span data-stu-id="5dbea-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="5dbea-104">Namnge en CAB-fil för uppdateringsbar hjälp</span><span class="sxs-lookup"><span data-stu-id="5dbea-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="5dbea-105">Ett uppdaterings Bart kabinett (. CAB-fil måste ha ett namn med följande format.</span><span class="sxs-lookup"><span data-stu-id="5dbea-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="5dbea-106">Elementen i namnet är följande.</span><span class="sxs-lookup"><span data-stu-id="5dbea-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="5dbea-107">Modulnamn värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.</span><span class="sxs-lookup"><span data-stu-id="5dbea-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="5dbea-108">ModuleGUID värdet för **GUID** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="5dbea-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="5dbea-109">Värdet för användar gränssnittet i CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="5dbea-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="5dbea-110">Värdet måste matcha värdet för ett av **värdet** -elementen i HelpInfo XML-filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="5dbea-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="5dbea-111">Om modulnamnet till exempel är "TestModule" är modulens GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 och användar gränssnitts kulturen är "en-US", namnet på CAB-filen skulle vara:</span><span class="sxs-lookup"><span data-stu-id="5dbea-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
