---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Bygg anpassade resurser för Desired Configuration för Windows PowerShell
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941175"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Bygg anpassade resurser för Desired Configuration för Windows PowerShell

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö. Det här avsnittet innehåller en översikt över hur du utvecklar resurser och länkar till ämnen med detaljerad information och exempel.

## <a name="dsc-resource-components"></a>DSC-resurs komponenter

En DSC-resurs är en Windows PowerShell-modul. Modulen innehåller både schemat (definitionen av de konfigurerbara egenskaperna) och implementeringen (koden som gör det faktiska arbetet som anges i en konfiguration) för resursen. Ett DSC-resurs schema kan definieras i en MOF-fil och implementeringen utförs av en-skript-modul. Från och med stöd för PowerShell-klasser i version 5 kan schemat och implementeringen båda definieras i en-klass. I följande avsnitt beskrivs mer information om hur du skapar DSC-resurser.

* [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
* [Implementera en DSC-resurs i C #](authoringResourceMofCS.md)
* [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md)
* [Sammansatta resurser: använda en DSC-konfiguration som en resurs](authoringResourceComposite.md)
* [Använda Resource designer-verktyget](authoringResourceMofDesigner.md)
