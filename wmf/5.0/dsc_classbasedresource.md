---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685755"
---
# <a name="class-based-dsc-resources"></a>Klassbaserade DSC-resurser

## <a name="defining-dsc-resources-with-classes"></a>Definiera DSC-resurser med klasser

Baserat på feedback, har vi gjort redigera DSC MOF-baserade resurser blir lättare att förstå.
De större skillnaderna mellan en klassbaserade DSC-resurs och en cmdlet DSC-resursprovider är:

* Det krävs inte en MOF-fil för schemat.
* En **DSCResource** undermapp i modulmappen är inte obligatoriskt.
* En PowerShell-filen för modulen kan innehålla flera DSC-resursklasser.

Mer information finns i [skriva en anpassad DSC-resurs med PowerShell-klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).
