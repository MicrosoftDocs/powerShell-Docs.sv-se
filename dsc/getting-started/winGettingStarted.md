---
ms.date: 08/15/2019
keywords: DSC, PowerShell, konfiguration, installation
title: Kom igång med önskad tillstånds konfiguration (DSC) för Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988930"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="31441-103">Kom igång med önskad tillstånds konfiguration (DSC) för Windows</span><span class="sxs-lookup"><span data-stu-id="31441-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="31441-104">I det här avsnittet beskrivs hur du kommer igång med PowerShell (Desired State Configuration) för Windows.</span><span class="sxs-lookup"><span data-stu-id="31441-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="31441-105">Allmän information om DSC finns i [Kom igång med önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="31441-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="31441-106">Operativ system versioner som stöds i Windows</span><span class="sxs-lookup"><span data-stu-id="31441-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="31441-107">Följande versioner stöds:</span><span class="sxs-lookup"><span data-stu-id="31441-107">The following versions are supported:</span></span>

- <span data-ttu-id="31441-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="31441-108">Windows Server 2019</span></span>
- <span data-ttu-id="31441-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="31441-109">Windows Server 2016</span></span>
- <span data-ttu-id="31441-110">Windows Server 2012R2</span><span class="sxs-lookup"><span data-stu-id="31441-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="31441-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="31441-111">Windows Server 2012</span></span>
- <span data-ttu-id="31441-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="31441-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="31441-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="31441-113">Windows 10</span></span>
- <span data-ttu-id="31441-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="31441-114">Windows 8.1</span></span>
- <span data-ttu-id="31441-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="31441-115">Windows 7</span></span>

<span data-ttu-id="31441-116">Den fristående produkt-SKU: n för [Hyper-V-server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) innehåller ingen implementering av önskade tillstånds agentkonfigurationerna så att den inte kan hanteras av PowerShell DSC eller Azure Automation tillstånds konfiguration.</span><span class="sxs-lookup"><span data-stu-id="31441-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="31441-117">Installerar DSC</span><span class="sxs-lookup"><span data-stu-id="31441-117">Installing DSC</span></span>

<span data-ttu-id="31441-118">PowerShell Desired State Configuration ingår i Windows och uppdateras via Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="31441-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="31441-119">Den senaste versionen är [Windows Management Framework 5,1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="31441-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="31441-120">Du behöver inte aktivera Windows Server-funktionen "DSC-service" för att kunna hantera en dator med DSC.</span><span class="sxs-lookup"><span data-stu-id="31441-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="31441-121">Funktionen behövs bara när du skapar en Windows pull Server-instans.</span><span class="sxs-lookup"><span data-stu-id="31441-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="31441-122">Använda DSC för Windows</span><span class="sxs-lookup"><span data-stu-id="31441-122">Using DSC for Windows</span></span>

<span data-ttu-id="31441-123">I följande avsnitt beskrivs hur du skapar och kör DSC-konfigurationer på Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="31441-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="31441-124">Skapa ett MOF-dokument för konfiguration</span><span class="sxs-lookup"><span data-stu-id="31441-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="31441-125">Nyckelordet Windows PowerShell-konfiguration används för att skapa en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="31441-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="31441-126">Följande steg beskriver hur du skapar ett konfigurations dokument med hjälp av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="31441-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="31441-127">Definiera en konfiguration och generera konfigurations dokumentet:</span><span class="sxs-lookup"><span data-stu-id="31441-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="31441-128">Installera en modul som innehåller DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="31441-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="31441-129">Windows PowerShell Desired State Configuration inkluderar inbyggda moduler som innehåller DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="31441-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="31441-130">Du kan också läsa in moduler från externa källor som PowerShell-galleriet med hjälp av PowerShellGet-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="31441-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="31441-131">Tillämpa konfigurationen på datorn</span><span class="sxs-lookup"><span data-stu-id="31441-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="31441-132">Konfigurations dokument (MOF-filer) kan tillämpas på datorn med cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="31441-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="31441-133">Hämta konfigurationens aktuella tillstånd</span><span class="sxs-lookup"><span data-stu-id="31441-133">Get the current state of the configuration</span></span>

<span data-ttu-id="31441-134">Cmdlet [: en get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) frågar efter datorns aktuella status och returnerar de aktuella värdena för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="31441-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="31441-135">Cmdlet: en [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) returnerar den aktuella meta-konfigurationen som tillämpas på datorn.</span><span class="sxs-lookup"><span data-stu-id="31441-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="31441-136">Ta bort den aktuella konfigurationen från en dator</span><span class="sxs-lookup"><span data-stu-id="31441-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="31441-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="31441-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="31441-138">Konfigurera inställningar i lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="31441-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="31441-139">Använd en MOF-fil för meta-konfiguration på datorn med cmdleten [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="31441-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="31441-140">Kräver sökvägen till MOF för meta-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="31441-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="31441-141">Loggfiler för önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="31441-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="31441-142">Loggar för DSC skrivs till händelse loggen i Windows i sökvägen `Microsoft-Windows-Dsc/Operational`.</span><span class="sxs-lookup"><span data-stu-id="31441-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="31441-143">Ytterligare loggar för fel sökning kan aktive ras enligt stegen i [var DSC-händelseloggar](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="31441-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
