---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>Klassbaserade DSC-resurser

## <a name="defining-dsc-resources-with-classes"></a>Definiera DSC-resurser med klasser

Utifrån feedback har vi gjort redigering DSC klass-baserade resurser enklare och lättare att förstå.
De viktiga skillnaderna mellan en klass-baserade DSC-resurs och en cmdlet DSC-resursprovidern är:

* Det krävs inte en MOF-fil för schemat.
* En **DSCResource** undermapp i mappen modul krävs inte.
* En PowerShell-modulen fil kan innehålla flera klasser i DSC-resurs.

Mer information finns i [skriva en anpassad DSC-resurs med PowerShell klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).