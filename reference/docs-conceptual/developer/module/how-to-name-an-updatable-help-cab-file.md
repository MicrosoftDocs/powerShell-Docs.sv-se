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
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357437"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Namnge en CAB-fil för uppdateringsbar hjälp

I det här avsnittet beskrivs det namn format som krävs för det uppdaterbara hjälp skåpet (. CAB-filer).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Namnge en CAB-fil för uppdateringsbar hjälp

Ett uppdaterings Bart kabinett (. CAB-fil måste ha ett namn med följande format.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Elementen i namnet är följande.

Modulnamn värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.

ModuleGUID värdet för **GUID** -nyckeln i modul manifestet.

Värdet för användar gränssnittet i CAB-filen. Värdet måste matcha värdet för ett av **värdet** -elementen i HelpInfo XML-filen för modulen.

Om modulnamnet till exempel är "TestModule" är modulens GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 och användar gränssnitts kulturen är "en-US", namnet på CAB-filen skulle vara:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`