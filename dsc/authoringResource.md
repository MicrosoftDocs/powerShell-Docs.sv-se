---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skapa anpassade Windows PowerShell Desired State Configuration-resurser
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Skapa anpassade Windows PowerShell Desired State Configuration-resurser

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell önskad tillstånd Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö. (Mer information finns i [inbyggda Windows PowerShell önskad tillstånd Configuration resurser](builtInResource.md).) Det här avsnittet innehåller en översikt över hur du utvecklar resurserna och länkarna till avsnitt med specifik information och exempel.

## <a name="dsc-resource-components"></a>Komponenter för DSC-resurs

En DSC-resurs är en Windows PowerShell-modulen. Modulen innehåller både schema (definition av konfigurerbara egenskaper) och implementering (den kod som utför det faktiska arbetet som anges av en konfiguration) för resursen. Ett schema för DSC-resursen kan definieras i en MOF-fil och implementeringen utförs av en skriptmodul. Från och med stöd för PowerShell klasser i version 5, kan schemat och implementering både definieras i en klass. I följande avsnitt beskrivs i detalj hur du skapar DSC-resurser.

* [Skriva en anpassad DSC-resurs med MOF](authoringResourceMOF.md) 
* [Implementera en DSC-resurs i C#](authoringResourceMofCS.md) 
* [Skriva en anpassad DSC-resurs med PowerShell-klasser](authoringResourceClass.md) 
* [Sammansatta resurser: med hjälp av DSC-konfigurationen som en resurs](authoringResourceComposite.md) 
* [Med hjälp av verktyget resurs Designer](authoringResourceMofDesigner.md) 

