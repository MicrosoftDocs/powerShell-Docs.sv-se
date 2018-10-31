---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Moduler som kräver godkännande av licensen
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002675"
---
# <a name="modules-requiring-license-acceptance"></a>Moduler som kräver godkännande av licensen

## <a name="synopsis"></a>SAMMANFATTNING

Juridiska avdelningar för vissa modulen utgivare kräva att kunder uttryckligen måste acceptera licensvillkoren innan du installerar sina modul från PowerShell-galleriet. Om en användare installerar, uppdaterar eller sparar en modul med PowerShellGet, direkt eller som ett beroende för ett annat paket och modulen kräver att användaren godkänner en licens, måste användaren ange de accepterar licensen eller åtgärden misslyckas.

## <a name="publish-requirements-for-modules"></a>Publicera krav för moduler

Moduler som vill att användarna ska acceptera licensen bör uppfylla följande krav:

- PSData-avsnittet i modulmanifestet bör innehålla RequireLicenseAcceptance = $True.
- Modulen bör innehålla filen license.txt i rotkatalogen.
- Modulmanifestet ska innehålla Uri-licens.
- Modulen ska publiceras med PowerShellGet Format Version 2.0 och senare.

## <a name="impact-on-installsaveupdate-module"></a>Påverkan på Install/spara/Update-Module

- Installera/spara/uppdatera cmdletar har stöd för en ny parameter – AcceptLicense som beter sig som om användaren såg licensen.
- Om RequiredLicenseAcceptance är SANT och – AcceptLicense har inte angetts, användaren ska visas i license.txt och du uppmanas att göra med: &quot;godkänner du licensvillkoren (Ja/Nej/YesToAll/NoToAll)&quot;.
  - Om licensen är godkänt
    - **Save-Module:** modulen ska kopieras till användaren&#39;s system
    - **Install-Module:** modulen ska kopieras till användaren&#39;s system till rätt mapp (baserat på omfång)
    - **Update-modul:** modulen kommer att uppdateras.
  - Om licensen har nekats.
    - Åtgärden kommer att avbrytas.
    - Alla cmdletar ska söka efter metadata (requireLicenseAcceptance och formatversion) visas ett godkännande av licensen är obligatoriskt
    - Om formatversion av klienten är äldre än 2.0, misslyckas åtgärden och be användaren att uppdatera klienten.
    - Om modulen har publicerats med formatet versioner äldre än 2.0 kommer requireLicenseAcceptance flaggan att ignoreras.

## <a name="module-dependencies"></a>Modulberoenden

- Under installationen/spara/uppdatering måste igen om en beroende-modul (något annat beroende på modulen) kräver godkännande av licensen och licens godkännande beteende (ovan) utföras.
- Om modulversionen finns redan i den lokala katalogen som är installerad på systemet, skulle vi kringgå Licenskontroll.
- Under installationen/spara/uppdatera åtgärden om en beroende modul måste ha en licens och godkännande av licensen inte genomförs åtgärden misslyckas och följa normala processer för paketet kunde inte installera/spara/uppdatera.

## <a name="impact-on--force"></a>Påverkan på - Force

Ange `–Force` är inte tillräckliga för att acceptera en licens. `–AcceptLicense` krävs för behörighet att installera. Om `–Force` anges RequiredLicenseAcceptance är True, och `–AcceptLicense` inte anges misslyckas åtgärden.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Exempel 1: Uppdatera modulen Manifest att kräva godkännande av licensen

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Det här kommandot uppdaterar manifestfilen och anger flaggan RequireLicenseAcceptance till true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Exempel 2: Installera modulen kräver godkännande av licensen

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

Det här kommandot visar licensen från filen license.txt och uppmanar användaren att acceptera licensen.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 3: Installera modulen kräver godkännande av licensen med - AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modulen har installerats utan någon uppmaning att acceptera licensen.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Exempel 4: Installera modulen kräver godkännande av licensen med - Force

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Exempel 5: Installera modulen med beroenden som kräver godkännande av licensen

Modulen ModuleWithDependency är beroende av modulen ”ModuleRequireLicenseAcceptance”. Användaren uppmanas att acceptera licensen.

```powershell
Install-Module -Name ModuleWithDependency
```

```output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 6: Installera modulen med beroenden som kräver godkännande av licensen och -AcceptLicense

Modulen ModuleWithDependency är beroende av modulen ”ModuleRequireLicenseAcceptance”. Användaren behöver inte ange att acceptera licensen eftersom - AcceptLicense har angetts.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Exempel 7: Installera modulen kräver godkännande av licensen på en klient som är äldre än PSGetFormatVersion 2.0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Exempel 8: Spara modul som kräver godkännande av licensen

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
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

Det här kommandot visar licensen från filen license.txt och uppmanar användaren att acceptera licensen.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 9: Spara modul som kräver godkännande av licensen med - AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Modulen sparas utan någon uppmaning att acceptera licensen.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Exempel 10: Uppdatera modulen kräver godkännande av licensen

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

Det här kommandot visar licensen från filen license.txt och uppmanar användaren att acceptera licensen.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 11: Uppdatera modulen kräver godkännande av licensen med - AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modulen uppdateras utan någon uppmaning att acceptera licensen.

## <a name="more-details"></a>Mer information

[Kräv godkännande av licensen för skript](./script-license-acceptance.md)

[Kräv godkännande av licensen stöd på PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
