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
# <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

Det här avsnittet beskrivs nödvändiga namnformatet för uppdateringsbar hjälp Information-filer, ofta kallade HelpInfo XML-filer.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

En HelpInfo XML-fil måste ha ett namn med formatet.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Element i namnet är som följer.

Modulnamn värdet av den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.

ModuleGUID värdet av den **GUID** nyckeln i modulmanifestet.

Om modulen är ”TestModule” och att modulen GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, blir till exempel namnet på HelpInfo XML-filen för modulen:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`