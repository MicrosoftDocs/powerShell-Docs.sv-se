---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Bygg anpassade resurser för Desired Configuration för Windows PowerShell
description: Den här artikeln innehåller en översikt över hur du utvecklar resurser och länkar till artiklar med detaljerad information och exempel.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656410"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Bygg anpassade resurser för Desired Configuration för Windows PowerShell

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö. Den här artikeln innehåller en översikt över hur du utvecklar resurser och länkar till artiklar med detaljerad information och exempel.

## <a name="dsc-resource-components"></a>DSC-resurs komponenter

En DSC-resurs är en Windows PowerShell-modul. Modulen innehåller både schemat (definitionen av de konfigurerbara egenskaperna) och implementeringen (koden som gör det faktiska arbetet som anges i en konfiguration) för resursen. Ett DSC-resurs schema kan definieras i en MOF-fil och implementeringen utförs av en-skript-modul. Från och med stöd för PowerShell-klasser i version 5 kan schemat och implementeringen båda definieras i en-klass. I följande artiklar beskrivs mer information om hur du skapar DSC-resurser.

- [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
- [Implementera en DSC-resurs i C #](authoringResourceMofCS.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md)
- [Sammansatta resurser: använda en DSC-konfiguration som en resurs](authoringResourceComposite.md)
- [Använda Resource designer-verktyget](authoringResourceMofDesigner.md)
