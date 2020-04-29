---
ms.date: 01/17/2019
keywords: DSC, PowerShell, konfiguration, installation
title: Starta om en nod
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942001"
---
# <a name="reboot-a-node"></a><span data-ttu-id="271e8-103">Starta om en nod</span><span class="sxs-lookup"><span data-stu-id="271e8-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="271e8-104">Det här avsnittet innehåller information om hur du startar om en nod.</span><span class="sxs-lookup"><span data-stu-id="271e8-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="271e8-105">För att datorn ska kunna starta om måste inställningarna för **ActionAfterReboot** och **RebootNodeIfNeeded** -LCM vara korrekt konfigurerade.</span><span class="sxs-lookup"><span data-stu-id="271e8-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="271e8-106">Läs om lokala Configuration Manager inställningar i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md)eller [konfigurera den lokala Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="271e8-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="271e8-107">Noder kan startas om från en resurs med hjälp av `$global:DSCMachineStatus` flaggan.</span><span class="sxs-lookup"><span data-stu-id="271e8-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="271e8-108">Om du anger den `1` här flaggan `Set-TargetResource` till i funktionen tvingas LCM att starta om noden direkt efter **set** -metoden för den aktuella resursen.</span><span class="sxs-lookup"><span data-stu-id="271e8-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="271e8-109">Med den här flaggan identifierar **PendingReboot** -resursen i modulen [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC-resurs om en omstart väntar utanför DSC.</span><span class="sxs-lookup"><span data-stu-id="271e8-109">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="271e8-110">Dina [konfigurationer](configurations.md) kan utföra steg som kräver att noden startas om.</span><span class="sxs-lookup"><span data-stu-id="271e8-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="271e8-111">Detta kan innefatta saker som:</span><span class="sxs-lookup"><span data-stu-id="271e8-111">This could include things such as:</span></span>

- <span data-ttu-id="271e8-112">Windows-uppdateringar</span><span class="sxs-lookup"><span data-stu-id="271e8-112">Windows updates</span></span>
- <span data-ttu-id="271e8-113">Program varu installation</span><span class="sxs-lookup"><span data-stu-id="271e8-113">Software install</span></span>
- <span data-ttu-id="271e8-114">Filen har bytt namn</span><span class="sxs-lookup"><span data-stu-id="271e8-114">File renames</span></span>
- <span data-ttu-id="271e8-115">Dator namn</span><span class="sxs-lookup"><span data-stu-id="271e8-115">Computer rename</span></span>

<span data-ttu-id="271e8-116">**PendingReboot** -resursen kontrollerar vissa dator platser för att avgöra om en omstart väntar.</span><span class="sxs-lookup"><span data-stu-id="271e8-116">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="271e8-117">Om noden kräver en omstart utanför DSC, anger **PendingReboot** -resursen `$global:DSCMachineStatus` flaggan för att `1` tvinga fram en omstart och lösa det väntande tillståndet.</span><span class="sxs-lookup"><span data-stu-id="271e8-117">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="271e8-118">Alla DSC-resurser kan instruera LCM att starta om noden genom att ställa in den här `Set-TargetResource` flaggan i funktionen.</span><span class="sxs-lookup"><span data-stu-id="271e8-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="271e8-119">Mer information finns i [skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="271e8-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="271e8-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="271e8-120">Syntax</span></span>

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="271e8-121">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="271e8-121">Properties</span></span>

| <span data-ttu-id="271e8-122">Egenskap</span><span class="sxs-lookup"><span data-stu-id="271e8-122">Property</span></span> | <span data-ttu-id="271e8-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="271e8-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="271e8-124">Name</span><span class="sxs-lookup"><span data-stu-id="271e8-124">Name</span></span>| <span data-ttu-id="271e8-125">Obligatorisk parameter som måste vara unik per instans av resursen inom en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="271e8-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="271e8-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="271e8-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="271e8-127">Hoppa över omstarter som utlösts av komponent-Based Servicing-komponenten.</span><span class="sxs-lookup"><span data-stu-id="271e8-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="271e8-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="271e8-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="271e8-129">Hoppa över omstarter som utlösts av Windows Update.</span><span class="sxs-lookup"><span data-stu-id="271e8-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="271e8-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="271e8-130">SkipPendingFileRename</span></span> | <span data-ttu-id="271e8-131">Hoppa över väntande fil namn omstarter.</span><span class="sxs-lookup"><span data-stu-id="271e8-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="271e8-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="271e8-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="271e8-133">Hoppa över omstarter som utlösts av ConfigMgr-klienten.</span><span class="sxs-lookup"><span data-stu-id="271e8-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="271e8-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="271e8-134">SkipComputerRename</span></span> | <span data-ttu-id="271e8-135">Hoppa över omstarter som utlöses av dator namn.</span><span class="sxs-lookup"><span data-stu-id="271e8-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="271e8-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="271e8-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="271e8-137">Stöds i v5.</span><span class="sxs-lookup"><span data-stu-id="271e8-137">Supported in v5.</span></span> <span data-ttu-id="271e8-138">Kör resursen som den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="271e8-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="271e8-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="271e8-139">DependsOn</span></span> | <span data-ttu-id="271e8-140">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="271e8-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="271e8-141">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är **resourceName** och dess typ är **resourcetype**, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="271e8-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="271e8-142">Mer information finns i [using DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="271e8-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="271e8-143">Exempel</span><span class="sxs-lookup"><span data-stu-id="271e8-143">Example</span></span>

<span data-ttu-id="271e8-144">I följande exempel installeras Microsoft Exchange med hjälp av [xExchange](https://github.com/PowerShell/xExchange) -resursen.</span><span class="sxs-lookup"><span data-stu-id="271e8-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="271e8-145">Under installationen används **PendingReboot** -resursen för att starta om noden.</span><span class="sxs-lookup"><span data-stu-id="271e8-145">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="271e8-146">Det här exemplet kräver autentiseringsuppgifterna för ett konto som har behörighet att lägga till en Exchange-Server i skogen.</span><span class="sxs-lookup"><span data-stu-id="271e8-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="271e8-147">Mer information om hur du använder autentiseringsuppgifter i DSC finns i [Hantera autentiseringsuppgifter i DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="271e8-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="271e8-148">I det här exemplet förutsätts att du har konfigurerat din lokala Configuration Manager att tillåta omstarter och fortsätta konfigurationen efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="271e8-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="271e8-149">Var du vill ladda ned</span><span class="sxs-lookup"><span data-stu-id="271e8-149">Where to Download</span></span>

<span data-ttu-id="271e8-150">Du kan hämta resurserna som används i det här avsnittet på följande platser eller med hjälp av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="271e8-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="271e8-151">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="271e8-151">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="271e8-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="271e8-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
