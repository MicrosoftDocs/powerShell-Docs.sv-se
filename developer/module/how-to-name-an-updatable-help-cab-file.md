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
ms.openlocfilehash: 23303489372cfe7e036fdea842ae75f7e47503c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850514"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Namnge en CAB-fil för uppdateringsbar hjälp

Det här avsnittet beskrivs nödvändiga namnformatet för uppdateringsbar hjälp-kabinettfil (. CAB-fil) filer.

## <a name="how-to-name-an-updatable-help-cab-file"></a>Namnge en CAB-fil för uppdateringsbar hjälp

En uppdateringsbar kabinettfil (. CAB-fil) måste ha ett namn med formatet.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Element i namnet är som följer.

Modulnamn värdet av den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.
Värdet för den **namn** egenskapen för den **ModuleInfo** objekt som den [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returnerar.

ModuleGUID värdet av den **GUID** nyckeln i modulmanifestet.

UICulture The UI kultur hjälpfiler i CAB-filen. Det här värdet måste matcha värdet för en av de **UICulture** element i HelpInfo XML-filen för modulen.

Till exempel om modulens namn är ”TestModule”, modulen GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, och kultur för Användargränssnittet är ”en-US”, namnet på CAB-filen är:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`