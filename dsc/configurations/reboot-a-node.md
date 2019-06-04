---
ms.date: 01/17/2019
keywords: DSC, powershell, konfiguration, installation
title: Starta om en nod
ms.openlocfilehash: 106fa1e7b0e3aaf3070ec05548d51140fe9a7725
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470743"
---
# <a name="reboot-a-node"></a><span data-ttu-id="c1cbc-103">Starta om en nod</span><span class="sxs-lookup"><span data-stu-id="c1cbc-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="c1cbc-104">Det här avsnittet vi berättar hur du starta om en nod.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="c1cbc-105">För att omstart ska lyckas den **ActionAfterReboot** och **RebootNodeIfNeeded** LCM inställningar måste konfigureras korrekt.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="c1cbc-106">Mer information om lokala Configuration Manager-inställningar, se [konfigurera den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md), eller [konfigurera den lokala Konfigurationshanteraren (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="c1cbc-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="c1cbc-107">Noder kan startas från inom en resurs med hjälp av den `$global:DSCMachineStatus` flaggan.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="c1cbc-108">Ställa in den här flaggan `1` i den `Set-TargetResource` funktionen tvingar MGM om du vill starta om noden direkt efter den **ange** -metoden för den aktuella resursen.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="c1cbc-109">Med den här flaggan den **xPendingReboot** resurs identifierar om en omstart väntar utanför DSC.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="c1cbc-110">Din [konfigurationer](configurations.md) kan utföra åtgärder som kräver noden ska startas om.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="c1cbc-111">Det kan innefatta saker som:</span><span class="sxs-lookup"><span data-stu-id="c1cbc-111">This could include things such as:</span></span>

- <span data-ttu-id="c1cbc-112">Windows-uppdateringar</span><span class="sxs-lookup"><span data-stu-id="c1cbc-112">Windows updates</span></span>
- <span data-ttu-id="c1cbc-113">Programinstallation</span><span class="sxs-lookup"><span data-stu-id="c1cbc-113">Software install</span></span>
- <span data-ttu-id="c1cbc-114">Byter namn på fil</span><span class="sxs-lookup"><span data-stu-id="c1cbc-114">File renames</span></span>
- <span data-ttu-id="c1cbc-115">Byt namn på datorn</span><span class="sxs-lookup"><span data-stu-id="c1cbc-115">Computer rename</span></span>

<span data-ttu-id="c1cbc-116">Den **xPendingReboot** resource kontrollerar specifik dator platser för att avgöra om en omstart väntar.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="c1cbc-117">Om noden måste startas om utanför DSC, den **xPendingReboot** resurs anger den `$global:DSCMachineStatus` flaggan till `1` tvingar fram en omstart och lösa väntande villkoret.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="c1cbc-118">Alla DSC-resurser kan instruera MGM om du vill starta om noden genom att ange den här flaggan i den `Set-TargetResource` funktion.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="c1cbc-119">Mer information finns i [skriva en anpassad DSC-resurs med MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c1cbc-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="c1cbc-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1cbc-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="c1cbc-121">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="c1cbc-121">Properties</span></span>

| <span data-ttu-id="c1cbc-122">Egenskap</span><span class="sxs-lookup"><span data-stu-id="c1cbc-122">Property</span></span> | <span data-ttu-id="c1cbc-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c1cbc-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c1cbc-124">Namn</span><span class="sxs-lookup"><span data-stu-id="c1cbc-124">Name</span></span>| <span data-ttu-id="c1cbc-125">Den obligatoriska parametern måste vara unikt för varje instans av resurs i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="c1cbc-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="c1cbc-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="c1cbc-127">Hoppa över omstarter som utlöses av komponenten Component-Based Servicing.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="c1cbc-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="c1cbc-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="c1cbc-129">Hoppa över omstarter som utlöses av Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="c1cbc-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="c1cbc-130">SkipPendingFileRename</span></span> | <span data-ttu-id="c1cbc-131">Hoppa över väntar på Byt namn på omstarter.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="c1cbc-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="c1cbc-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="c1cbc-133">Hoppa över omstarter som utlöses av ConfigMgr-klienten.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="c1cbc-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="c1cbc-134">SkipComputerRename</span></span> | <span data-ttu-id="c1cbc-135">Hoppa över omstarter som utlöses av datorn byter namn på.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="c1cbc-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c1cbc-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="c1cbc-137">Stöd i v5.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-137">Supported in v5.</span></span> <span data-ttu-id="c1cbc-138">Kör resursen som den angivna användaren.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="c1cbc-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c1cbc-139">DependsOn</span></span> | <span data-ttu-id="c1cbc-140">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c1cbc-141">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="c1cbc-142">Mer information finns i [använder DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="c1cbc-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="c1cbc-143">Exempel</span><span class="sxs-lookup"><span data-stu-id="c1cbc-143">Example</span></span>

<span data-ttu-id="c1cbc-144">I följande exempel installeras Microsoft Exchange med hjälp av den [xExchange](https://github.com/PowerShell/xExchange) resurs.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="c1cbc-145">Under installationen den **xPendingReboot** resursen används för att starta om noden.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="c1cbc-146">Det här exemplet kräver autentiseringsuppgifter för ett konto som har behörighet att lägga till en Exchange-server i skogen.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="c1cbc-147">Mer information om hur du använder autentiseringsuppgifter i DSC finns [hantering av autentiseringsuppgifter i DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c1cbc-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="c1cbc-148">Det här exemplet förutsätts att du har konfigurerat din lokala Configuration Manager för att tillåta omstarter och fortsätta konfigurationen efter en omstart.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="c1cbc-149">Var du hämtar</span><span class="sxs-lookup"><span data-stu-id="c1cbc-149">Where to Download</span></span>

<span data-ttu-id="c1cbc-150">Du kan hämta de resurser som används i det här avsnittet på följande platser eller med hjälp av PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="c1cbc-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="c1cbc-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="c1cbc-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="c1cbc-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="c1cbc-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
