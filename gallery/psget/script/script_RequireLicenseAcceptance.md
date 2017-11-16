---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a>Att kräva godkännande av licens för skript

Godkännande av licens stöds inte för skript. Ett scenario där ett skript som är beroende av en modul som kräver godkännande av licens stöds dock.

Skriptet commands(Install-Script/Save-Script/Update-Script) stöder en ny parameter - AcceptLicense som fungerar som om användaren såg licensen. Om - AcceptLicense anges; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensvillkoren.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licens
Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'. Användaren uppmanas att godkänna licens.
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licens och -AcceptLicense
Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'. Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Mer information
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[Kräv godkännande av licens-stöd för moduler](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[Kräv godkännande av licens-stöd på PowerShellGallery](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Kräv godkännande av licens på Distribuera till Azure Automation](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
