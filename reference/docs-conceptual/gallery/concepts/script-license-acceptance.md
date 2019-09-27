---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Kräver godkännande av licens för skript
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328898"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Kräver godkännande av licens för skript

Licens godkännande stöds inte för skript. Scenariot där ett skript är beroende av en modul som kräver godkännande av licenser stöds dock.

Skript kommandon (install-script/Save-script/Update-script) har stöd för en ny parameter-AcceptLicense som beter sig som om användaren såg licensen. IF-AcceptLicense har inte angetts; användaren kommer att se License. txt för en beroende modul och uppmanas att godkänna licensen.

## <a name="examples"></a>FLER

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Exempel 1: Installera skript med beroenden som kräver licens godkännande

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Exempel 2: Installera skript med beroenden som kräver licens godkännande och-AcceptLicense

Skriptet ' ScriptRequireLicenseAcceptance ' är beroende av modulen ' ModuleRequireLicenseAcceptance '. Användaren uppmanas inte att godkänna licensen eftersom-AcceptLicense har angetts.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Mer information

- [Kräv support för licens godkännande för moduler](module-license-acceptance.md)
- [Kräv support för licens godkännande på PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Kräv godkännande av licensen vid distribuera till Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
