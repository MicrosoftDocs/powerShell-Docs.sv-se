---
ms.date: 09/12/2016
ms.topic: reference
title: Namnge en CAB-fil för uppdateringsbar hjälp
description: Namnge en CAB-fil för uppdateringsbar hjälp
ms.openlocfilehash: 57ea188d07a382d1a986a49c9ae22c5919dafa8e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658919"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Namnge en CAB-fil för uppdateringsbar hjälp

I det här avsnittet förklaras det nödvändiga namn formatet för filer med uppdaterings bara hjälp skåp ( `.CAB` ).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Namnge en CAB-fil för uppdateringsbar hjälp

En uppdaterings bar kabinett `.CAB` fil () måste ha ett namn med följande format.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Elementen i namnet är följande.

- `<ModuleName>` -Värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.
- `<ModuleGUID>` – Värdet för **GUID** -nyckeln i modulen manifest.
- `<UICulture>` – Användar gränssnitts kulturen för hjälpfilerna i CAB-filen. Värdet måste matcha värdet för ett av **värdet** -elementen i HelpInfo XML-filen för modulen.

Om modulnamnet till exempel är "TestModule" är modulens GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 och användar gränssnitts kulturen är "en-US", namnet på CAB-filen skulle vara:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
