---
ms.date: 07/09/2019
keywords: DSC, GPO, PowerShell, konfiguration, installation
title: Snabb start – konvertera grupprincip till DSC
ms.openlocfilehash: 852710f261ea1d57228c05d4093c1d78584e0ca5
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89236245"
---
# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="76625-103">Snabb start: konvertera grupprincip till DSC</span><span class="sxs-lookup"><span data-stu-id="76625-103">Quickstart: Convert Group Policy into DSC</span></span>

> <span data-ttu-id="76625-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="76625-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="76625-105">Du kan generera en DSC-konfiguration från en grupprincip eller Azure Security Center bas linje.</span><span class="sxs-lookup"><span data-stu-id="76625-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="76625-106">[BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) -modulen innehåller följande kommandon för att utföra den här uppgiften.</span><span class="sxs-lookup"><span data-stu-id="76625-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="76625-107">`ConvertFrom-GPO` – Konverterar grup principer, lagrade som filer.</span><span class="sxs-lookup"><span data-stu-id="76625-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="76625-108">Du kan också ange en katalog som innehåller flera principer som ska kombineras till en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="76625-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="76625-109">Om du vill exportera grup principer i din miljö använder du cmdleten [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) eller följer instruktionerna i [Exportera ett grup princip objekt till en fil](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="76625-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="76625-110">`ConvertFrom-SCM` – Konverterar bas linjer för säkerhetscompliance Manager, lagrade som `.xml` filer.</span><span class="sxs-lookup"><span data-stu-id="76625-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="76625-111">`ConvertFrom-ASC` – Konverterar Azure Security Center bas linjer, lagrade som `.json` filer.</span><span class="sxs-lookup"><span data-stu-id="76625-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="76625-112">`Merge-GPOs` – Konverterar grup principer som tillämpas på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="76625-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="76625-113">Cmdletarna som anges ovan konverterar en bas linje till en DSC- `.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="76625-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="76625-114">Du kan också välja att generera ett konfigurations skript ( `.ps1` ) som du kan redigera och kompilera om.</span><span class="sxs-lookup"><span data-stu-id="76625-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="76625-115">Cmdletarna identifierar kompileringsfel för saknade resurser eller duplicerade resurs block.</span><span class="sxs-lookup"><span data-stu-id="76625-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="76625-116">Resurs block som orsakar kompileringsfel är kommenterade.</span><span class="sxs-lookup"><span data-stu-id="76625-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="76625-117">I följande exempel konverteras en [Microsoft Security-bas linje](https://www.microsoft.com/download/details.aspx?id=55319) till ett DSC-konfigurationsobjekt ( `.ps1` ) och en `.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="76625-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="76625-118">När du har kört kommandona visas två filer i standard katalogen "utdata" som skapats under din nuvarande sökväg.</span><span class="sxs-lookup"><span data-stu-id="76625-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="76625-119">Varje hanterad nod behöver också följande två moduler:</span><span class="sxs-lookup"><span data-stu-id="76625-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="76625-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="76625-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="76625-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="76625-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="76625-122">**BaselineManagement** är en lösning som har utvecklats av communityn för att göra DSC mer synligt för support för Community-lösningar som kommer från projekt underhållen och inte från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="76625-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="76625-123">Du kan öppna ett nytt ärende för **BaselineManagement** på [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="76625-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="76625-124">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="76625-124">Next steps</span></span>

- <span data-ttu-id="76625-125">Information om hur du överför konfigurations skriptet till Azure Automation tillstånds konfiguration finns [komma igång](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="76625-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/azure/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="76625-126">Lägg till **SecurityPolicyDSC** -och **AuditPolicyDSC** -modulerna i ditt [Automation-konto](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="76625-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="76625-127">Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="76625-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
