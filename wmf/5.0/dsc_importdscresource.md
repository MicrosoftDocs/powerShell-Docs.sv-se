---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: a3b176101bebf7081febd8629bddcfa0ae1e7540
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
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