---
title: Konfigurera versionsnummer för HelpInfo-XML-filer
ms.date: 09/12/2016
ms.openlocfilehash: 42164f98414da0b6f1a0021e9d860c57a63a9eec
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892990"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a>Konfigurera versionsnummer för HelpInfo-XML-filer

I det här avsnittet beskrivs hur du ställer in och ökar versions numren i en uppdaterings bar hjälp informations fil, som kallas för en "HelpInfo XML-fil".

## <a name="how-to-set-helpinfo-xml-version-numbers"></a>Konfigurera versionsnummer för HelpInfo-XML-filer

Versions numren i en HelpInfo XML-fil är viktiga för att det ska gå att uppdatera hjälpen. Cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) laddar bara ned nya hjälpfiler när versions numret för en GRÄNSSNITTS kultur i XML-HelpInfo är större än versions numret för denna gränssnitts kultur i den lokala HelpInfo-XML-filen, eller så finns det ingen lokal HelpInfo XML-fil.

XML-filen HelpInfo använder det versions nummer på 4 delar som definieras i klassen **system. version** i Microsoft .NET Framework. Formatet är `N1.N2.N3.N4`. Module-författare kan använda alla versions scheman som tillåts av klassen **system. version** . Uppdaterings bara hjälp kräver bara att versions numret för en användar gränssnitts kultur ökar när en ny version av CAB-filen för den användar gränssnitts kulturen överförs till den plats som anges av **HelpContentURI** -elementet i XML-filen för HelpInfo.

I följande exempel visas elementen i XML-filen HelpInfo för den tyska (de-DE) användar gränssnitts kulturen när versionen är 2.15.0.10.

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

Versions numret för en kultur i användar gränssnittet återspeglar versionen av CAB-filen för användar gränssnitts kulturen. Versions numret gäller hela CAB-filen. Du kan inte ange olika versions nummer för olika filer i CAB-filen. Versions numret för varje GRÄNSSNITTs kultur utvärderas oberoende och behöver inte vara relaterat till versions numren för andra användar gränssnitts kulturer som modulen stöder.
