---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Kräver godkännande av licensen för skript
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002590"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Kräver godkännande av licensen för skript

Godkännande av licensen finns inte stöd för skript. Ett scenario där ett skript beror på en modul som kräver godkännande av licensen stöds dock.

Skriptet commands(Install-Script/Save-Script/Update-Script) stöd för en ny parameter - AcceptLicense som fungerar som om användaren såg licensen. Om inte anges - AcceptLicense; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensen.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licensen

Skriptet ScriptRequireLicenseAcceptance är beroende av modulen ”ModuleRequireLicenseAcceptance”. Användaren uppmanas att acceptera licensen.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licensen och -AcceptLicense

Skriptet ScriptRequireLicenseAcceptance är beroende av modulen ”ModuleRequireLicenseAcceptance”. Användaren behöver inte ange att acceptera licensen eftersom - AcceptLicense har angetts.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Mer information

- [Kräv godkännande av licensen stöd för moduler](module-license-acceptance.md)
- [Kräv godkännande av licensen stöd på PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
