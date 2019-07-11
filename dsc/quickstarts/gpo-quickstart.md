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
> <span data-ttu-id="546c9-103">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="546c9-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="546c9-104">Snabbstart: Konvertera en Grupprincip i DSC</span><span class="sxs-lookup"><span data-stu-id="546c9-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="546c9-105">Du kan skapa en DSC-konfiguration från en baslinje för Grupprincip eller Azure Security Center.</span><span class="sxs-lookup"><span data-stu-id="546c9-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="546c9-106">Den [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) modulen omfattar följande kommandon för att utföra den här uppgiften.</span><span class="sxs-lookup"><span data-stu-id="546c9-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="546c9-107">`ConvertFrom-GPO` -Konverterar grupp principer, lagras som filer.</span><span class="sxs-lookup"><span data-stu-id="546c9-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="546c9-108">Du kan också ange en katalog som innehåller flera principer som kommer att kombineras i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="546c9-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="546c9-109">Om du vill exportera grupprinciper i din miljö, använder den [säkerhetskopiera grupprincipobjekt](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, eller följ instruktionerna i [exportera ett grupprincipobjekt till en fil](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="546c9-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="546c9-110">`ConvertFrom-SCM` -Konverterar Security Compliance Manager baslinjer, lagras som `.xml` filer.</span><span class="sxs-lookup"><span data-stu-id="546c9-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="546c9-111">`ConvertFrom-ASC` -Baslinjer konverterar Azure Security Center, lagras som `.json` filer.</span><span class="sxs-lookup"><span data-stu-id="546c9-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="546c9-112">`Merge-GPOs` -Grupp konverterar principer tillämpas på en måldator.</span><span class="sxs-lookup"><span data-stu-id="546c9-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="546c9-113">De cmdletar som anges ovan konvertera en baslinje till en DSC `.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="546c9-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="546c9-114">Du kan också välja att spara ett konfigurationsskript (`.ps1`), som du kan redigera och kompilera om.</span><span class="sxs-lookup"><span data-stu-id="546c9-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="546c9-115">Cmdletarna identifiera kompileringsfel för resurser som saknas eller Dubblettresurs-block.</span><span class="sxs-lookup"><span data-stu-id="546c9-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="546c9-116">Resurs-block som skulle orsaka kompileringsfel är kommenterade.</span><span class="sxs-lookup"><span data-stu-id="546c9-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="546c9-117">I följande exempel konverterar en [Microsoft Säkerhetsbaslinje](https://www.microsoft.com/en-us/download/details.aspx?id=55319) i ett DSC-konfigurationsskript (`.ps1`) och `.mof` fil.</span><span class="sxs-lookup"><span data-stu-id="546c9-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="546c9-118">När du har kört kommandona, kan du se två filer i standardkatalogen för ”utdata” som skapats under den aktuella sökvägen.</span><span class="sxs-lookup"><span data-stu-id="546c9-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

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

<span data-ttu-id="546c9-119">Varje hanterad nod måste också följande två moduler:</span><span class="sxs-lookup"><span data-stu-id="546c9-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="546c9-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="546c9-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="546c9-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="546c9-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="546c9-122">**BaselineManagement** är en lösning som utvecklats av communityn för att kontrollera DSC mer synliga för Support för community-lösningar kommer från sköter underhåll själva för projektet och inte från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="546c9-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="546c9-123">Du kan öppna ett nytt ärende för **BaselineManagement** på [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="546c9-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="546c9-124">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="546c9-124">Next steps</span></span>

- <span data-ttu-id="546c9-125">Om du vill ladda upp dina konfigurationsskript till Azure Automation-Tillståndskonfiguration Se [komma igång](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="546c9-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="546c9-126">Lägg till den **SecurityPolicyDSC** och **AuditPolicyDSC** moduler till ditt [Automation-konto](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="546c9-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="546c9-127">Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="546c9-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
