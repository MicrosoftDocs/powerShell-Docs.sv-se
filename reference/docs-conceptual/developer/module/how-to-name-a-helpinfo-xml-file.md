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
# <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

I det här avsnittet beskrivs det obligatoriska namn formatet för filer med uppdaterings bara hjälp information, vanligt vis kallade HelpInfo XML-filer.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

En HelpInfo XML-fil måste ha ett namn med följande format.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Elementen i namnet är följande.

Modulnamn värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.

ModuleGUID värdet för **GUID** -nyckeln i modul manifestet.

Om modulnamnet till exempel är "TestModule" och modulens GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 är namnet på HelpInfo XML-filen för modulen:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`