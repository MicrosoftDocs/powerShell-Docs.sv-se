---
ms.date: 10/16/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Tillämpa konfigurationer
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941735"
---
# <a name="enacting-configurations"></a><span data-ttu-id="d2233-103">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d2233-103">Enacting configurations</span></span>

><span data-ttu-id="d2233-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="d2233-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d2233-105">Det finns två sätt att dra i PowerShell-konfigurationer för Desired State Configuration (DSC): push-läge och pull-läge.</span><span class="sxs-lookup"><span data-stu-id="d2233-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="d2233-106">Push-läge</span><span class="sxs-lookup"><span data-stu-id="d2233-106">Push mode</span></span>

<span data-ttu-id="d2233-107">![Push-läge],(../images/pushModel.png "hur push-läge fungerar")</span><span class="sxs-lookup"><span data-stu-id="d2233-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="d2233-108">Push-läge refererar till en användare som aktivt använder en konfiguration på en målnod genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="d2233-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="d2233-109">När du har skapat och kompilerat en konfiguration kan du använda den i push-läge genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) , ange parametern-Path för cmdleten till den sökväg där MOF-konfigurationsfilen finns.</span><span class="sxs-lookup"><span data-stu-id="d2233-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="d2233-110">Om t. ex. konfigurations-MOF finns på `C:\DSC\Configurations\localhost.mof`, kan du tillämpa den på den lokala datorn med följande kommando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="d2233-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="d2233-111">__Obs__: Som standard kör DSC en konfiguration som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="d2233-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="d2233-112">Anropa [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) med parametern __-wait__ för att köra konfigurationen interaktivt.</span><span class="sxs-lookup"><span data-stu-id="d2233-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="d2233-113">Pull-läge</span><span class="sxs-lookup"><span data-stu-id="d2233-113">Pull mode</span></span>

<span data-ttu-id="d2233-114">![Pull-läge](../images/pullModel.png "hur pull-läge fungerar")</span><span class="sxs-lookup"><span data-stu-id="d2233-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="d2233-115">I pull-läge konfigureras pull-klienter för att hämta sina önskade tillstånds konfigurationer från en fjärran sluten pull-tjänst.</span><span class="sxs-lookup"><span data-stu-id="d2233-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="d2233-116">På samma sätt har pull-tjänsten kon figurer ATS som värd för DSC-tjänsten och har etablerats med de konfigurationer och resurser som krävs av pull-klienterna.</span><span class="sxs-lookup"><span data-stu-id="d2233-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="d2233-117">Varje pull-klient har en schemalagd händelse som utför en periodisk kontroll av nodens konfiguration.</span><span class="sxs-lookup"><span data-stu-id="d2233-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="d2233-118">När händelsen utlöses första gången gör den lokala Configuration Manager (LCM) på mottagar klienten en begäran till pull-tjänsten för att hämta konfigurationen som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="d2233-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="d2233-119">Om konfigurationen finns i pull-tjänsten och den skickar inledande verifierings kontroller, hämtas konfigurationen till pull-klienten, där den körs av LCM.</span><span class="sxs-lookup"><span data-stu-id="d2233-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="d2233-120">LCM kontrollerar att klienten följer konfigurationen med jämna mellanrum som anges av egenskapen **ConfigurationModeFrequencyMins** för LCM.</span><span class="sxs-lookup"><span data-stu-id="d2233-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="d2233-121">LCM söker efter uppdaterade konfigurationer i pull-tjänsten med jämna mellanrum som anges av egenskapen **RefreshModeFrequency** för LCM.</span><span class="sxs-lookup"><span data-stu-id="d2233-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="d2233-122">Information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="d2233-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="d2233-123">Den rekommenderade lösningen för att vara värd för en pull-tjänst är DSC-molnet, [Azure Automation](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="d2233-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="d2233-124">Detta är en värdbaserad lösning som ger grafisk hantering, rapportering och centraliserad administration.</span><span class="sxs-lookup"><span data-stu-id="d2233-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="d2233-125">Mer information om hur du konfigurerar en pull-tjänst på Windows Server finns i [Konfigurera en DSC-webb hämtnings Server](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="d2233-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="d2233-126">Vi förstår dock att den här implementeringen har begränsade funktioner och kräver en del "gör det själv"-integrering.</span><span class="sxs-lookup"><span data-stu-id="d2233-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="d2233-127">I följande avsnitt förklaras hämtnings tjänsten och klienter:</span><span class="sxs-lookup"><span data-stu-id="d2233-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="d2233-128">Översikt över Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="d2233-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="d2233-129">Konfigurera en SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="d2233-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="d2233-130">Konfigurera en pull-klient</span><span class="sxs-lookup"><span data-stu-id="d2233-130">Configuring a pull client</span></span>](pullClientConfigID.md)
