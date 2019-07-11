---
ms.date: 07/09/2019
keywords: DSC, grupprincipobjekt, powershell, konfiguration, installation
title: Snabbstart – konvertera Grupprincip i DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67785140"
---
> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Snabbstart: Konvertera en Grupprincip i DSC

Du kan skapa en DSC-konfiguration från en baslinje för Grupprincip eller Azure Security Center. Den [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) modulen omfattar följande kommandon för att utföra den här uppgiften.

- `ConvertFrom-GPO` -Konverterar grupp principer, lagras som filer. Du kan också ange en katalog som innehåller flera principer som kommer att kombineras i en konfiguration.
  - Om du vill exportera grupprinciper i din miljö, använder den [säkerhetskopiera grupprincipobjekt](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, eller följ instruktionerna i [exportera ett grupprincipobjekt till en fil](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` -Konverterar Security Compliance Manager baslinjer, lagras som `.xml` filer.
- `ConvertFrom-ASC` -Baslinjer konverterar Azure Security Center, lagras som `.json` filer.
- `Merge-GPOs` -Grupp konverterar principer tillämpas på en måldator.

De cmdletar som anges ovan konvertera en baslinje till en DSC `.mof` fil. Du kan också välja att spara ett konfigurationsskript (`.ps1`), som du kan redigera och kompilera om. Cmdletarna identifiera kompileringsfel för resurser som saknas eller Dubblettresurs-block. Resurs-block som skulle orsaka kompileringsfel är kommenterade.

I följande exempel konverterar en [Microsoft Säkerhetsbaslinje](https://www.microsoft.com/en-us/download/details.aspx?id=55319) i ett DSC-konfigurationsskript (`.ps1`) och `.mof` fil.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

När du har kört kommandona, kan du se två filer i standardkatalogen för ”utdata” som skapats under den aktuella sökvägen.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Varje hanterad nod måste också följande två moduler:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** är en lösning som utvecklats av communityn för att kontrollera DSC mer synliga för Support för community-lösningar kommer från sköter underhåll själva för projektet och inte från Microsoft. Du kan öppna ett nytt ärende för **BaselineManagement** på [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Nästa steg

- Om du vill ladda upp dina konfigurationsskript till Azure Automation-Tillståndskonfiguration Se [komma igång](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Lägg till den **SecurityPolicyDSC** och **AuditPolicyDSC** moduler till ditt [Automation-konto](/azure/automation/shared-resources/modules).
- Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).
