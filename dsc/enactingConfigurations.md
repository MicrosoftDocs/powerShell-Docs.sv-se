---
ms.date: 10/16/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Tillämpa konfigurationer
ms.openlocfilehash: 28ca852eb00298c229be8104ecdfeabc47a10abc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="enacting-configurations"></a><span data-ttu-id="67dbd-103">Tillämpa konfigurationer</span><span class="sxs-lookup"><span data-stu-id="67dbd-103">Enacting configurations</span></span>

><span data-ttu-id="67dbd-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="67dbd-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="67dbd-105">Det finns två sätt att införa PowerShell önskad tillstånd Configuration (DSC) konfigurationer: push och pull-läge.</span><span class="sxs-lookup"><span data-stu-id="67dbd-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="67dbd-106">Push-läge</span><span class="sxs-lookup"><span data-stu-id="67dbd-106">Push mode</span></span>

<span data-ttu-id="67dbd-107">![Push-läge](images/pushModel.png "hur push läge fungerar")</span><span class="sxs-lookup"><span data-stu-id="67dbd-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="67dbd-108">Push-läge som refererar till en användare som aktivt tillämpa en konfiguration på målnoden genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67dbd-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="67dbd-109">När du skapar och sammanställa en konfiguration, kan genomför den i push-läge genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, ange parametern - Path för sökvägen konfigurationen MOF-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67dbd-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="67dbd-110">Om konfigurationen MOF finns i till exempel `C:\DSC\Configurations\localhost.mof`, du vill tillämpa den på den lokala datorn med följande kommando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="67dbd-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="67dbd-111">__Obs__: som standard körs DSC en konfiguration i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="67dbd-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="67dbd-112">Om du vill köra konfigurationen interaktivt anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) med den __-vänta__ parameter.</span><span class="sxs-lookup"><span data-stu-id="67dbd-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="67dbd-113">Pull-läge</span><span class="sxs-lookup"><span data-stu-id="67dbd-113">Pull mode</span></span>

<span data-ttu-id="67dbd-114">![Hämtar läget](images/pullModel.png "så här fungerar pull-")</span><span class="sxs-lookup"><span data-stu-id="67dbd-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="67dbd-115">Pull-klienter konfigureras i pull-läge för att få sina konfigurationer tillstånd från en fjärransluten pull-tjänst.</span><span class="sxs-lookup"><span data-stu-id="67dbd-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="67dbd-116">På samma sätt pull-tjänsten har ställts in att värdtjänsten för DSC och har etablerats med konfigurationer och resurser som krävs av pull-klienter.</span><span class="sxs-lookup"><span data-stu-id="67dbd-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="67dbd-117">Varje pull-klienter har en schemalagd händelse som utför en regelbunden kompatibilitetskontrollen på konfigurationen av noden.</span><span class="sxs-lookup"><span data-stu-id="67dbd-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="67dbd-118">När händelsen utlöses för första gången, gör en begäran till pull-tjänsten för att hämta den konfiguration som angetts i MGM om den lokala Configuration Manager (MGM) på pull-klienten.</span><span class="sxs-lookup"><span data-stu-id="67dbd-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="67dbd-119">Om konfigurationen finns på pull-tjänsten och överförs inledande kontroller, hämtas konfigurationen som pull-klienten, där den sedan körs av MGM.</span><span class="sxs-lookup"><span data-stu-id="67dbd-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="67dbd-120">MGM kontrollerar att klienten är kompatibla med konfigurationen med regelbundna intervall som anges av den **ConfigurationModeFrequencyMins** -egenskapen för MGM.</span><span class="sxs-lookup"><span data-stu-id="67dbd-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="67dbd-121">MGM om du söker efter uppdaterade konfigurationer på pull-tjänsten med regelbundna intervall som anges av den **RefreshModeFrequency** -egenskapen för MGM.</span><span class="sxs-lookup"><span data-stu-id="67dbd-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="67dbd-122">Information om hur du konfigurerar MGM finns [konfigurera den lokala Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="67dbd-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="67dbd-123">Den rekommenderade lösningen för värd för en Pull-tjänsten är molntjänst DSC [Azure Automation](https://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="67dbd-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="67dbd-124">Detta är värd för lösningen ger grafiska management, rapportering och centraliserad administration.</span><span class="sxs-lookup"><span data-stu-id="67dbd-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="67dbd-125">Mer information om hur du skapar en Pull-tjänst på Windows Server finns [ställer in en pull webbserver DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="67dbd-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="67dbd-126">Förstå dock att den här implementeringen har begränsad funktioner och kräver vissa ”gör det själv”-integration.</span><span class="sxs-lookup"><span data-stu-id="67dbd-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="67dbd-127">I följande avsnitt förklaras pull-tjänsten och -klienter:</span><span class="sxs-lookup"><span data-stu-id="67dbd-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="67dbd-128">Azure Automation DSC-översikt</span><span class="sxs-lookup"><span data-stu-id="67dbd-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="67dbd-129">Konfigurera en SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="67dbd-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="67dbd-130">Konfigurera en pull-klient</span><span class="sxs-lookup"><span data-stu-id="67dbd-130">Configuring a pull client</span></span>](pullClientConfigID.md)