---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221858"
---
# <a name="class-based-dsc-resources"></a>Klassbaserade DSC-resurser

## <a name="defining-dsc-resources-with-classes"></a>Definiera DSC-resurser med klasser

Utifrån feedback har vi gjort redigering DSC klass-baserade resurser enklare och lättare att förstå.
De viktiga skillnaderna mellan en klass-baserade DSC-resurs och en cmdlet DSC-resursprovidern är:

* Det krävs inte en MOF-fil för schemat.
* En **DSCResource** undermapp i mappen modul krävs inte.
* En PowerShell-modulen fil kan innehålla flera klasser i DSC-resurs.

Mer information finns i [skriva en anpassad DSC-resurs med PowerShell klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).
