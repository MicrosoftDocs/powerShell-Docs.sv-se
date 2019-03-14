---
title: Hur du ställer in HelpInfo XML-versionsnumren | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: d69e8a734aa96ff9b7911815fb43b81103548b59
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794356"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Konfigurera versionsnummer för HelpInfo-XML-filer

Det här avsnittet beskriver hur du ställer och öka versionsnumren i en uppdateringsbar hjälp Information-fil som kallas en ”HelpInfo XML-fil”.

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Konfigurera versionsnummer för HelpInfo-XML-filer

Versionsnummer i en HelpInfo XML-fil är viktiga för driften av uppdateringsbar hjälp. Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) hämtar nya hjälpfiler endast när det lägre versionsnumret för en UI-kultur i den fjärranslutna HelpInfo XML-filen är större än versionsnumret för den kulturen för Användargränssnittet i den lokala HelpInfo XML, eller om det finns ingen lokal HelpInfo XML-fil.

HelpInfo XML-filen använder 4 delar versionsnumret som definieras i den **System.Version** klass av Microsoft .NET Framework. Formatet är `N1.N2.N3.N4`. Modulskapare kan använda valfri versionsnumrering schema är tillåten enligt den **System.Version** klass. Uppdateringsbar hjälp kräver bara att versionsnumret för en UI kultur ökning när en ny version av CAB-filen för den kulturen överförs till den plats som anges av den **HelpContentURI** element i HelpInfo XML-filen.

I följande exempel visar elementen i HelpInfo XML-filen för tyska (de-DE) UI kultur när version är 2.15.0.10.

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Versionen av CAB-filen för den kulturen för Användargränssnittet visar versionsnumret för en UI-kultur. Versionsnumret som gäller för hela CAB-filen. Du kan inte ange olika versionsnummer används för olika filer i CAB-filen. Versionsnumret för varje UI-kultur utvärderas oberoende av varandra och behöver inte vara relaterade till versionsnummer för andra UI-kulturer som har stöd för modulen.