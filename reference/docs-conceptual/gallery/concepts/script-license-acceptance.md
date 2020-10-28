---
ms.date: 06/09/2017
title: Kräver godkännande av licens för skript
description: Artikeln förklarar hur du arbetar med skript som publicerats i PowerShell-galleriet som kräver godkännande av en slut användar licens.
ms.openlocfilehash: d82974810fd1e73ef8d9e5771fc430d0f7964e87
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656085"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Kräver godkännande av licens för skript

Licens godkännande stöds inte för skript. Scenariot där ett skript är beroende av en modul som kräver godkännande av licenser stöds dock.

Skript kommandona PowerShellGet stöder parametern **AcceptLicense** som beter sig som om användaren såg licensen. Om **AcceptLicense** inte anges visas `license.txt` filen för en beroende modul och du uppmanas att godkänna licensen.

## <a name="examples"></a>EXEMPEL

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exempel 1: installera skript med beroenden som kräver licens godkännande

Skriptet ' ScriptRequireLicenseAcceptance ' är beroende av modulen ' ModuleRequireLicenseAcceptance '. Användaren uppmanas att godkänna licens.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 2: installera skript med beroenden som kräver licens godkännande och-AcceptLicense

Skriptet ' ScriptRequireLicenseAcceptance ' är beroende av modulen ' ModuleRequireLicenseAcceptance '. Användaren uppmanas inte att godkänna licensen eftersom-AcceptLicense har angetts.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Mer information

- [Kräv support för licens godkännande för moduler](module-license-acceptance.md)
- [Kräv support för licens godkännande på PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
