---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Översikt över önskad tillstånds konfiguration i Windows PowerShell
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941728"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="eedc4-103">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="eedc4-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="eedc4-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="eedc4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eedc4-105">DSC är en hanterings plattform i PowerShell som gör att du kan hantera din IT-och utvecklings infrastruktur med konfiguration som kod.</span><span class="sxs-lookup"><span data-stu-id="eedc4-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="eedc4-106">En översikt över affärs fördelarna med att använda DSC finns i [Översikt över önskad tillstånds konfiguration för besluts fattare](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="eedc4-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="eedc4-107">En översikt över de tekniska fördelarna med att använda DSC finns i [Översikt över önskad tillstånds konfiguration för tekniker](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="eedc4-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="eedc4-108">Information om hur du börjar använda DSC snabbt finns i [snabb start för DSC](../quickstarts/website-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="eedc4-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="eedc4-109">Viktiga begrepp</span><span class="sxs-lookup"><span data-stu-id="eedc4-109">Key Concepts</span></span>

<span data-ttu-id="eedc4-110">DSC är en deklarativ plattform som används för konfiguration, distribution och hantering av system.</span><span class="sxs-lookup"><span data-stu-id="eedc4-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="eedc4-111">Det består av tre primära komponenter:</span><span class="sxs-lookup"><span data-stu-id="eedc4-111">It consists of three primary components:</span></span>

- <span data-ttu-id="eedc4-112">[Konfigurationer](../configurations/configurations.md) är deklarativ PowerShell-skript som definierar och konfigurerar instanser av resurser.</span><span class="sxs-lookup"><span data-stu-id="eedc4-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="eedc4-113">När du kör konfigurationen blir DSC (och de resurser som anropas av konfigurationen) bara "gör det så", vilket säkerställer att systemet finns i det tillstånd som anges av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="eedc4-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply "make it so", ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="eedc4-114">DSC-konfigurationer är också idempotenta: den lokala Configuration Manager (LCM) fortsätter att se till att datorerna är konfigurerade i det tillstånd som konfigurationen deklarerar.</span><span class="sxs-lookup"><span data-stu-id="eedc4-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="eedc4-115">[Resurser](../resources/resources.md) är "gör det så att det är en del av DSC.</span><span class="sxs-lookup"><span data-stu-id="eedc4-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="eedc4-116">De innehåller koden som anger och behåller målet för en konfiguration i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="eedc4-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="eedc4-117">Resurser finns i PowerShell-moduler och kan skrivas för att modellera saker som generiska som en fil eller en Windows-process, eller som är särskilt en IIS-server eller en virtuell dator som körs i Azure.</span><span class="sxs-lookup"><span data-stu-id="eedc4-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="eedc4-118">Den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md) är den motor som används av DSC för att förenkla interaktionen mellan resurser och konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="eedc4-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="eedc4-119">LCM avsöker regelbundet systemet med hjälp av kontroll flödet som implementeras av resurser för att säkerställa att det tillstånd som definieras av en konfiguration upprätthålls.</span><span class="sxs-lookup"><span data-stu-id="eedc4-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="eedc4-120">Om systemet inte är i rätt tillstånd, gör LCM anrop till koden i resurser för att "göra det" enligt konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="eedc4-120">If the system is out of state, the LCM makes calls to the code in resources to "make it so" according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="eedc4-121">Se även</span><span class="sxs-lookup"><span data-stu-id="eedc4-121">See Also</span></span>

- [<span data-ttu-id="eedc4-122">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="eedc4-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="eedc4-123">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="eedc4-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="eedc4-124">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="eedc4-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
