---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skapa anpassade Windows PowerShell Desired State Configuration-resurser
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404739"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Skapa anpassade Windows PowerShell Desired State Configuration-resurser

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö. Det här avsnittet innehåller en översikt över utveckling av resurserna och länkarna till avsnitt med specifik information och exempel.

## <a name="dsc-resource-components"></a>Komponenter för DSC-resurs

En DSC-resurs är en Windows PowerShell-modul. Modulen innehåller både schemat (definition av konfigurerbara egenskaper) och implementeringen (den kod som utför det faktiska arbetet som anges av en konfiguration) för resursen. Ett schema för DSC-resurs kan definieras i en MOF-fil och implementeringen utförs av en skriptmodul. Från och med hjälp av PowerShell-klasser i version 5, kan schemat och implementering vara definierade i en klass. I följande avsnitt beskrivs i detalj hur du skapar DSC-resurser.

* [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md)
* [Implementera en DSC-resurs iC#](authoringResourceMofCS.md)
* [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md)
* [Sammansatta resurser: Använda en DSC-konfiguration som en resurs](authoringResourceComposite.md)
* [Med hjälp av verktyget Resource Designer](../authoringResourceMofDesigner.md)
