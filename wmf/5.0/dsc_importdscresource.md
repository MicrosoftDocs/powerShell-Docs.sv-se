---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219658"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a>Importera DscResource nyckelordet stöder ModuleVersion - parameter

Vi har lagt till en ny parameter till den `Import-DscResource` dynamiska nyckelord som är tillgänglig vid redigering av DSC-konfigurationer. Konfiguration av författarna kan nu ange exakt vilka Modulversion för att läsa in DSC-resurser från. Den nya syntaxen för nyckelordet är:

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* **Namnet**: namnen på en eller flera resurser för att importera.
* **Modulnamn**: Modulnamnen eller ModuleSpecification objekt av en eller flera moduler att importera.
* **ModuleVersion**: versionen för modulen av import. Om används, måste Modulnamn representera bara en modul med namnet.

I Windows PowerShell ISE visas den med IntelliSense:

![](../images/Import-DscResource-Modversion.jpg)

**Obs**: den `–ModuleVersion` parametern kan bara användas i kombination med den `–ModuleName` parameter. Den kan inte användas med resursnamn endast med den `–Name` parameter.

Innan var det enda sättet att ange modulversionen vid inläsning av DSC-resurser med hjälp av specifikationen Modulobjekt t.ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`
