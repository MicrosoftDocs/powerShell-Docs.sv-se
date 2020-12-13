---
ms.date: 09/12/2016
ms.topic: reference
title: Namnge en HelpInfo-XML-fil
description: Namnge en HelpInfo-XML-fil
ms.openlocfilehash: 55bc2ef9530fc457e4d9ddf18e79e7226c991663
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659046"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

I det här avsnittet beskrivs det obligatoriska namn formatet för filer med uppdaterings bara hjälp information, vanligt vis kallade HelpInfo XML-filer.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Namnge en HelpInfo-XML-fil

En HelpInfo XML-fil måste ha ett namn med följande format.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Elementen i namnet är följande.

- `<ModuleName>` -Värdet för egenskapen **Name** för det **ModuleInfo** -objekt som cmdleten [Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) returnerar.

- `<ModuleGUID>` – Värdet för **GUID** -nyckeln i modulen manifest.

Om modulnamnet till exempel är "TestModule" och modulens GUID är 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 är namnet på HelpInfo XML-filen för modulen:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`
