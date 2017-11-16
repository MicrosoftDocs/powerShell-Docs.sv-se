---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Klass-baserade DSC-resurser

## <a name="defining-dsc-resources-with-classes"></a>Definiera DSC-resurser med klasser

Utifrån feedback har vi gjort redigering DSC klass-baserade resurser enklare och lättare att förstå. De viktiga skillnaderna mellan en klass-baserade DSC-resurs och en cmdlet DSC-resursprovidern är:

* Det krävs inte en MOF-fil för schemat.
* En **DSCResource** undermapp i mappen modul krävs inte.
* En PowerShell-modulen fil kan innehålla flera klasser i DSC-resurs.

Mer information finns i [skriva en anpassad DSC-resurs med PowerShell klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).

