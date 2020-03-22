---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Moduler som kräver godkännande av licensen
ms.openlocfilehash: a2f7ed72aae8579a6723f65b86dd0993f1a22afd
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082820"
---
# <a name="modules-requiring-license-acceptance"></a>Moduler som kräver godkännande av licensen

## <a name="synopsis"></a>SAMMANFATTNING

Juridiska avdelningar för vissa module-utgivare kräver att kunderna uttryckligen accepterar licensen innan de installerar sin modul från PowerShell-galleriet. Om en användare installerar, uppdaterar eller sparar en modul med PowerShellGet, oavsett om det är direkt eller som ett beroende för ett annat paket, och den modulen kräver att användaren godkänner en licens, måste användaren ange att den accepterar licensen eller att åtgärden Miss lyckas.

## <a name="publish-requirements-for-modules"></a>Publicera krav för moduler

Moduler som vill kräva att användare accepterar licens bör uppfylla följande krav:

- PSData-avsnittet av modulens manifest bör innehålla RequireLicenseAcceptance = $True.
- Modulen bör innehålla filen License. txt i rot katalogen.
- Module-manifestet ska innehålla licens-URI.
- Modulen bör publiceras med PowerShellGet-format version 2,0 och senare.

## <a name="impact-on-installsaveupdate-module"></a>Inverkan på installation/Spara/uppdatera-modul

- Installations-/Spara-/uppdaterings-cmdlets har stöd för en ny parameter **AcceptLicense** som beter sig som om användaren såg licensen.
- Om **RequiredLicenseAcceptance** är sant och **AcceptLicense** inte anges visas `license.txt`och du uppmanas att: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.
  - Om licensen accepteras
    - **Spara-modul:** modulen kopieras till användarens system
    - **Installera-modul:** modulen kopieras till användarens system till rätt mapp (baserat på omfång)
    - **Update-modul:** modulen har uppdaterats.
  - Om licensen nekas.
    - Åtgärden har avbrutits.
    - Alla cmdletar söker efter de metadata (**requireLicenseAcceptance** och format version) som säger att licens godkännande krävs
    - Om format versionen av klienten är äldre än 2,0 Miss lyckas åtgärden och användaren uppmanas att uppdatera klienten.
    - Om modulen publicerades med formatet version som är äldre än 2,0 ignoreras flaggan requireLicenseAcceptance.

## <a name="module-dependencies"></a>Modul-beroenden

- Om en beroende modul (något annat beror på modulen) krävs för att installera/Spara/uppdatera måste licens godkännanden (ovan) krävas.
- Om modulnamnet redan visas i den lokala katalogen som installeras i systemet skulle vi kringgå licens kontrollen.
- Vid installation/sparande/uppdatering, om en beroende modul kräver en licens, och licens godkännandet inte inträffar, Miss lyckas åtgärden och följande normala processer för paketet kunde inte installeras/sparas/uppdateras.

## <a name="impact-on--force"></a>Påverkan på Force

Det räcker inte att ange `–Force` för att godkänna en licens. `–AcceptLicense` krävs för att du ska kunna installera. Om `–Force` anges är RequiredLicenseAcceptance sant, och `–AcceptLicense` inte anges, Miss lyckas åtgärden.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Exempel 1: uppdatera modul manifest för att kräva licens godkännande

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Detta kommando uppdaterar manifest filen och anger flaggan RequireLicenseAcceptance till true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Exempel 2: installera modul som kräver licens godkännande

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Det här kommandot visar licensen från `license.txt`-filen och begär att användaren accepterar licensen.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 3: installera modul som kräver licens godkännande med-AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modulen installeras utan att du behöver ange en licens för att godkänna licens.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Exempel 4: installera modul som kräver licens godkännande med-force

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```Output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Exempel 5: installera modulen med beroenden som kräver licens godkännande

Modulens **ModuleWithDependency** är beroende av modulens **ModuleRequireLicenseAcceptance**. Användaren uppmanas att godkänna licens.

```powershell
Install-Module -Name ModuleWithDependency
```

```Output
License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 6: installera modulen med beroenden som kräver licens godkännande och-AcceptLicense

Modulens **ModuleWithDependency** är beroende av modulens **ModuleRequireLicenseAcceptance**. Användaren uppmanas inte att godkänna licensen eftersom **AcceptLicense** har angetts.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Exempel 7: installera modul som kräver licens godkännande på en klient som är äldre än PSGetFormatVersion 2,0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Exempel 8: Spara modul som kräver licens godkännande

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Det här kommandot visar licensen från `license.txt`-filen och begär att användaren accepterar licensen.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 9: Spara modul som kräver licens godkännande med-AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Modulen sparas utan att du behöver ange en licens för att godkänna licensen.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Exempel 10: Update-modulen som kräver licens godkännande

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Det här kommandot visar licensen från `license.txt`-filen och begär att användaren accepterar licensen.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 11: Update-modulen som kräver licens godkännande med-AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modulen uppdateras utan att du behöver ange en licens för att godkänna licens.

## <a name="more-details"></a>Mer information

[Kräv godkännande av licensen för skript](./script-license-acceptance.md)

[Kräv support för licens godkännande på PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
