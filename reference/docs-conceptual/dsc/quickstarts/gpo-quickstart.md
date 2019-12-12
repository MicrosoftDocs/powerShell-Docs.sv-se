---
ms.date: 07/09/2019
keywords: DSC, GPO, PowerShell, konfiguration, installation
title: Snabb start – konvertera grupprincip till DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941609"
---
> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Snabb start: konvertera grupprincip till DSC

Du kan generera en DSC-konfiguration från en grupprincip eller Azure Security Center bas linje. [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) -modulen innehåller följande kommandon för att utföra den här uppgiften.

- `ConvertFrom-GPO` – konverterar grup principer, lagrade som filer. Du kan också ange en katalog som innehåller flera principer som ska kombineras till en konfiguration.
  - Om du vill exportera grup principer i din miljö använder du cmdleten [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) eller följer instruktionerna i [Exportera ett grup princip objekt till en fil](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` – konverterar bas linjer för säkerhetskompatibilitets hanteraren, lagrade som `.xml` filer.
- `ConvertFrom-ASC` – konverterar Azure Security Center-bas linjer, lagrade som `.json` filer.
- `Merge-GPOs` – konverterar grup principer som tillämpas på en måldator.

Cmdletarna som anges ovan konverterar en bas linje till en DSC `.mof`-fil. Du kan också välja att generera ett konfigurations skript (`.ps1`), som du kan redigera och kompilera om. Cmdletarna identifierar kompileringsfel för saknade resurser eller duplicerade resurs block. Resurs block som orsakar kompileringsfel är kommenterade.

I följande exempel konverteras en [Microsofts säkerhets bas linje](https://www.microsoft.com/en-us/download/details.aspx?id=55319) till ett DSC-konfigurations skript (`.ps1`) och `.mof` fil.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

När du har kört kommandona visas två filer i standard katalogen "utdata" som skapats under din nuvarande sökväg.

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

Varje hanterad nod behöver också följande två moduler:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** är en lösning som har utvecklats av communityn för att göra DSC mer synligt för support för Community-lösningar som kommer från projekt underhållen och inte från Microsoft. Du kan öppna ett nytt ärende för **BaselineManagement** på [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Nästa steg

- Information om hur du överför konfigurations skriptet till Azure Automation tillstånds konfiguration finns [komma igång](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Lägg till **SecurityPolicyDSC** -och **AuditPolicyDSC** -modulerna i ditt [Automation-konto](/azure/automation/shared-resources/modules).
- Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).
