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
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811193"
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
