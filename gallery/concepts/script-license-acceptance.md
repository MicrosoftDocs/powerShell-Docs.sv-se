---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Att kräva godkännande av licens för skript
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34049015"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Att kräva godkännande av licens för skript

Godkännande av licens stöds inte för skript. Ett scenario där ett skript som är beroende av en modul som kräver godkännande av licens stöds dock.

Skriptet commands(Install-Script/Save-Script/Update-Script) stöder en ny parameter - AcceptLicense som fungerar som om användaren såg licensen. Om - AcceptLicense anges; användaren ska visas license.txt för beroende modulen och du uppmanas att acceptera licensvillkoren.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exempel 1: Installationsskriptet med beroenden som kräver godkännande av licens

Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'. Användaren uppmanas att godkänna licens.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 2: Installationsskriptet med beroenden som kräver godkännande av licens och -AcceptLicense

Skriptet ScriptRequireLicenseAcceptance beror på modulen 'ModuleRequireLicenseAcceptance'. Användaren uppmanas inte att godkänna licens eftersom - AcceptLicense har angetts.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Mer information

- [Kräv godkännande av licens-stöd för moduler](module-license-acceptance.md)
- [Kräv godkännande av licens-stöd på PowerShellGallery](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)