---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 4a2dc39c2b6c380fb4ca94f9fd071ed9cdb35049
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
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

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[Kräv godkännande av licensen vid distribuera till Azure Automation](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)