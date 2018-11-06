---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998528"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Import-DscResource nyckelordet stöder - ModuleVersion-parametern

Vi har lagt till en ny parameter till den `Import-DscResource` dynamiska nyckelord som är tillgängliga vid redigering av DSC-konfigurationer. Konfiguration av författarna kan nu ange exakt vilka Modulversion för att läsa in DSC-resurser från. Den nya syntaxen för nyckelordet är:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Namn på**: namnen på en eller flera resurser för att importera.
* **ModuleName**: Modulnamnen eller ModuleSpecification objekt i en eller flera moduler att importera.
* **ModuleVersion**: Version av modulen att importera. Om används, måste ModuleName representera bara en modul med namnet.

I Windows PowerShell ISE visas så den med IntelliSense-stöd:

![](../images/Import-DscResource-Modversion.jpg)

**Obs**: den `–ModuleVersion` parametern kan bara användas i kombination med den `–ModuleName` parametern. Den kan inte användas med resursnamn endast med den `–Name` parametern.

Tidigare var det enda sättet att ange modulversionen vid inläsning av DSC-resurser med hjälp av modulen specifikationen objektet t.ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
