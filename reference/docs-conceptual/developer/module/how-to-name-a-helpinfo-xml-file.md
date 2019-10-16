---
title: Så här namnger du en HelpInfo XML-fil | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357465"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="05ef1-102">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="05ef1-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="05ef1-103">I det här avsnittet beskrivs det obligatoriska namn formatet för filer med uppdaterings bara hjälp information, vanligt vis kallade HelpInfo XML-filer.</span><span class="sxs-lookup"><span data-stu-id="05ef1-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="05ef1-104">Namnge en HelpInfo-XML-fil</span><span class="sxs-lookup"><span data-stu-id="05ef1-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="05ef1-105">En HelpInfo XML-fil måste ha ett namn med följande format.</span><span class="sxs-lookup"><span data-stu-id="05ef1-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="05ef1-106">Elementen i namnet är följande.</span><span class="sxs-lookup"><span data-stu-id="05ef1-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="05ef1-107">Modulnamn värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.</span><span class="sxs-lookup"><span data-stu-id="05ef1-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="05ef1-108">ModuleGUID värdet för **GUID** -nyckeln i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="05ef1-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="05ef1-109">Om modulnamnet till exempel är "TestModule" och modulens GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 är namnet på HelpInfo XML-filen för modulen:</span><span class="sxs-lookup"><span data-stu-id="05ef1-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`