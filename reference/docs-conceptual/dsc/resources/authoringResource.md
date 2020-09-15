---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Bygg anpassade resurser för Desired Configuration för Windows PowerShell
ms.openlocfilehash: 203a2e3d0e118b86ae1fe959cc3508b6ed2733a8
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217584"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Bygg anpassade resurser för Desired Configuration för Windows PowerShell

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö. Det här avsnittet innehåller en översikt över hur du utvecklar resurser och länkar till ämnen med detaljerad information och exempel.

## <a name="dsc-resource-components"></a>DSC-resurs komponenter

En DSC-resurs är en Windows PowerShell-modul. Modulen innehåller både schemat (definitionen av de konfigurerbara egenskaperna) och implementeringen (koden som gör det faktiska arbetet som anges i en konfiguration) för resursen. Ett DSC-resurs schema kan definieras i en MOF-fil och implementeringen utförs av en-skript-modul. Från och med stöd för PowerShell-klasser i version 5 kan schemat och implementeringen båda definieras i en-klass. I följande avsnitt beskrivs mer information om hur du skapar DSC-resurser.

- [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
- [Implementera en DSC-resurs i C #](authoringResourceMofCS.md)
- [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md)
- [Sammansatta resurser: använda en DSC-konfiguration som en resurs](authoringResourceComposite.md)
- [Använda Resource designer-verktyget](authoringResourceMofDesigner.md)
