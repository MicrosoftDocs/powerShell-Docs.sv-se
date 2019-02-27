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
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848092"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

Det här avsnittet beskrivs nödvändiga namnformatet för uppdateringsbar hjälp Information-filer, ofta kallade HelpInfo XML-filer.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

En HelpInfo XML-fil måste ha ett namn med formatet.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Element i namnet är som följer.

Modulnamn värdet av den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.
Värdet för den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.

ModuleGUID värdet av den **GUID** nyckeln i modulmanifestet.

Om modulen är ”TestModule” och att modulen GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, blir till exempel namnet på HelpInfo XML-filen för modulen:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`