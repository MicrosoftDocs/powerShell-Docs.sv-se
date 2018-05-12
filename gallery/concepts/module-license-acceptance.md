---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Moduler som kräver godkännande av licensen
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="modules-requiring-license-acceptance"></a>Moduler som kräver godkännande av licensen

## <a name="synopsis"></a>SAMMANFATTNING

Juridiska avdelningar för vissa modulen utgivare kräva att kunder uttryckligen måste acceptera licensvillkoren innan du installerar sina modul från PowerShell-galleriet. Om en användare installerar uppdateringar eller sparar en modul med PowerShellGet, direkt eller som ett beroende för ett annat objekt, och att modulen kräver att användaren godkänner du en licens, måste användaren ange de godkänner licensvillkoren, annars misslyckas åtgärden.

## <a name="publish-requirements-for-modules"></a>Publicera krav för moduler

Moduler som användarna ska acceptera licens ska uppfylla följande krav:

- PSData avsnitt i modulmanifestet bör innehålla RequireLicenseAcceptance = $True.
- Modulen bör innehålla filen license.txt i rotkatalogen.
- Modulmanifestet bör innehålla licens Uri.
- Modulen måste publiceras med PowerShellGet Format Version 2.0 och senare.

## <a name="impact-on-installsaveupdate-module"></a>Påverkan på Installera/Save/Update-modul

- Cmdlets för installation-spara-uppdateringen stöder en ny parameter – AcceptLicense som fungerar som om användaren såg licensen.
- Om RequiredLicenseAcceptance är True och – AcceptLicense har inte angetts, användaren ska visas license.txt och du får: &quot;godkänner du licensvillkoren (Ja/Nej/YesToAll/NoToAll)&quot;.
  - Om licensen godkänns
    - **Spara-modul:** modulen ska kopieras till användaren&#39;s system
    - **Installera-modul:** modulen ska kopieras till användaren&#39;s system till rätt mapp (baserat på omfattningen)
    - **Update-modul:** modulen kommer att uppdateras.
  - Om licensen har nekats.
    - Åtgärden kommer att avbrytas.
- Alla cmdletar kommer att söka efter metadata (requireLicenseAcceptance och Format Version) där det står att ett godkännande av licens krävs
  - Om formatet för version av klienten är äldre än 2.0, misslyckas åtgärden och be användaren att uppdatera klienten.
  - Om modulen har publicerats med formatversion som är äldre än 2.0 ignoreras requireLicenseAcceptance flaggan.


 ## <a name="module-dependencies"></a>Modulen beroenden
- Under installationen-spara-uppdateringen kommer igen om en beroende-modul (något annat beror på modulen) kräver godkännande av licens och sedan licens godkännande beteendet (ovan) att krävas.
- Om modulversionen finns redan i den lokala katalogen som är installerad på systemet, skulle vi kringgå Licenskontroll.
- Under installationen-spara-uppdateringen igen om en beroende modul kräver en licens och godkännande av licens inte genomförs åtgärden misslyckas och följa normala processer för objektet kunde inte installera-spara-uppdateringen.

 ## <a name="impact-on--force"></a>Påverkan på - Force

Ange – Force inte är tillräckliga för att godkänna en licens. – AcceptLicense krävs för behörighet att installera. Om – Force anges RequiredLicenseAcceptance är True, och – AcceptLicense har inte angetts, misslyckas åtgärden.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Exempel 1: Uppdatera modulen Manifest att kräva godkännande av licens

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Det här kommandot uppdaterar manifestfilen och ställer in flaggan RequireLicenseAcceptance till true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Exempel 2: Installera modulen som kräver godkännande av licens

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

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

Det här kommandot visar licens från filen license.txt och uppmanar användaren att acceptera licensvillkoren.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 3: Installera modulen som kräver godkännande av licens med - AcceptLicense

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modulen installeras utan prompten att acceptera licens.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Exempel 4: Installera modulen som kräver godkännande av licens med - Force

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Exempel 5: Installera modulen med beroenden som kräver godkännande av licens

Modulen ModuleWithDependency beror på modulen 'ModuleRequireLicenseAcceptance'. Användaren uppmanas att godkänna licens.

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 6: Installera modulen med beroenden som kräver godkännande av licens och -AcceptLicense

Modulen ModuleWithDependency beror på modulen 'ModuleRequireLicenseAcceptance'. Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Exempel 7: Installera modulen som kräver godkännande av licens på en klient som är äldre än PSGetFormatVersion 2.0

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Exempel 8: Spara modulen som kräver godkännande av licens

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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

Det här kommandot visar licens från filen license.txt och uppmanar användaren att acceptera licensvillkoren.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 9: Spara modulen som kräver godkännande av licens med - AcceptLicense

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Modulen sparas utan någon tillfrågas om du vill acceptera licens.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Exempel 10: Uppdatera modulen som kräver godkännande av licens

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

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

Det här kommandot visar licens från filen license.txt och uppmanar användaren att acceptera licensvillkoren.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Exempel 11: Uppdatera modulen som kräver godkännande av licens med - AcceptLicense

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Modulen uppdateras utan någon tillfrågas om du vill acceptera licens.

## <a name="more-details"></a>Mer information

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[Kräv godkännande av licensen för skript](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[Kräv godkännande av licens-stöd på PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)