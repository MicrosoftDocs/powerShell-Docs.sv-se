---
title: Hur du namnger en HelpInfo XML-fil | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082404"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="ec61a-102">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="ec61a-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="ec61a-103">Det här avsnittet beskrivs nödvändiga namnformatet för uppdateringsbar hjälp Information-filer, ofta kallade HelpInfo XML-filer.</span><span class="sxs-lookup"><span data-stu-id="ec61a-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="ec61a-104">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="ec61a-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="ec61a-105">En HelpInfo XML-fil måste ha ett namn med formatet.</span><span class="sxs-lookup"><span data-stu-id="ec61a-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="ec61a-106">Element i namnet är som följer.</span><span class="sxs-lookup"><span data-stu-id="ec61a-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="ec61a-107">Modulnamn värdet av den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="ec61a-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="ec61a-108">ModuleGUID värdet av den **GUID** nyckeln i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="ec61a-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="ec61a-109">Om modulen är ”TestModule” och att modulen GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, blir till exempel namnet på HelpInfo XML-filen för modulen:</span><span class="sxs-lookup"><span data-stu-id="ec61a-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`