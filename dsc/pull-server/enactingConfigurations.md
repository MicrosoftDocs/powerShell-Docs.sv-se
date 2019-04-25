---
ms.date: 10/16/2017
keywords: DSC, powershell, konfiguration, installation
title: Tillämpa konfigurationer
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079956"
---
# <a name="enacting-configurations"></a><span data-ttu-id="6c735-103">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="6c735-103">Enacting configurations</span></span>

><span data-ttu-id="6c735-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6c735-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6c735-105">Det finns två sätt att införa PowerShell Desired State Configuration (DSC) konfigurationer: push och pull-läge.</span><span class="sxs-lookup"><span data-stu-id="6c735-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="6c735-106">Push-läge</span><span class="sxs-lookup"><span data-stu-id="6c735-106">Push mode</span></span>

<span data-ttu-id="6c735-107">![Push-läget](../images/pushModel.png "push hur fungerar det")</span><span class="sxs-lookup"><span data-stu-id="6c735-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="6c735-108">Push-läge refererar till en användare som aktivt använder en konfiguration till målnoden genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6c735-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="6c735-109">När du skapar och kompilera en konfiguration, du kan införa det i push-läget genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, ange parametern - Path för cmdlet: en till sökvägen där konfigurationen MOF finns.</span><span class="sxs-lookup"><span data-stu-id="6c735-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="6c735-110">Exempel: om konfigurationen MOF finns på `C:\DSC\Configurations\localhost.mof`, du vill tillämpa den på den lokala datorn med följande kommando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="6c735-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="6c735-111">__Obs__: Som standard körs DSC en konfiguration i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="6c735-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="6c735-112">Du kan köra konfigurationen interaktivt genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) med den __-vänta__ parametern.</span><span class="sxs-lookup"><span data-stu-id="6c735-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="6c735-113">Pull-läge</span><span class="sxs-lookup"><span data-stu-id="6c735-113">Pull mode</span></span>

<span data-ttu-id="6c735-114">![Pull-läge](../images/pullModel.png "hämta hur fungerar det")</span><span class="sxs-lookup"><span data-stu-id="6c735-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="6c735-115">Pull-klienter är konfigurerade för att få sina konfigurationer av önskat tillstånd från en fjärransluten hämtningstjänst i pull-läge.</span><span class="sxs-lookup"><span data-stu-id="6c735-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="6c735-116">På samma sätt, pull-tjänsten har ställts in till värdtjänsten DSC och har etablerats med konfigurationer och resurser som krävs av pull-klienter.</span><span class="sxs-lookup"><span data-stu-id="6c735-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="6c735-117">Varje pull-klienter har en schemalagd händelse som utför en regelbunden kompatibilitetskontrollen på konfigurationen av noden.</span><span class="sxs-lookup"><span data-stu-id="6c735-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="6c735-118">När händelsen utlöses för första gången, gör en begäran till pull-tjänsten för att hämta den konfiguration som har angetts i LCM i den lokala Configuration Manager (LCM) på pull-klienten.</span><span class="sxs-lookup"><span data-stu-id="6c735-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="6c735-119">Om konfigurationen finns på pull-tjänsten och den skickar sin första verifieringskontroller, laddas konfigurationen ned till pull-klienten, där det sedan körs av LCM.</span><span class="sxs-lookup"><span data-stu-id="6c735-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="6c735-120">LCM kontrollerar att klienten är kompatibel med konfigurationen med jämna mellanrum som anges av den **ConfigurationModeFrequencyMins** egenskapen för LCM.</span><span class="sxs-lookup"><span data-stu-id="6c735-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="6c735-121">LCM söker efter uppdaterade konfigurationer på pull-tjänsten med jämna mellanrum som anges av den **RefreshModeFrequency** egenskapen för LCM.</span><span class="sxs-lookup"><span data-stu-id="6c735-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="6c735-122">Information om hur du konfigurerar LCM finns i [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="6c735-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="6c735-123">Den rekommenderade lösningen som värd för en Pull-tjänst är molntjänst DSC [Azure Automation](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="6c735-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="6c735-124">Detta är värd för lösningen ger grafisk hantering, rapportering och centraliserad administration.</span><span class="sxs-lookup"><span data-stu-id="6c735-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="6c735-125">Mer information om hur du konfigurerar en Pull-tjänst på Windows Server finns i [att konfigurera en DSC-webbpullserver](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="6c735-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="6c735-126">Förstå men att den här implementeringen har begränsade funktioner och kräver vissa ”gör det själv”-integrering.</span><span class="sxs-lookup"><span data-stu-id="6c735-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="6c735-127">I följande avsnitt förklarar hämtningstjänsten och klienter:</span><span class="sxs-lookup"><span data-stu-id="6c735-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="6c735-128">Översikt över Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="6c735-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="6c735-129">Konfigurera en SMB-pullserver</span><span class="sxs-lookup"><span data-stu-id="6c735-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="6c735-130">Konfigurera en pullklient</span><span class="sxs-lookup"><span data-stu-id="6c735-130">Configuring a pull client</span></span>](pullClientConfigID.md)
