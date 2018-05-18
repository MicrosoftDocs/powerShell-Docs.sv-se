---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Windows PowerShell Desired State Configuration-översikt
ms.openlocfilehash: c9069d7c9ce9c614330e36a42233b00363660a4b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="d02b2-103">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="d02b2-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="d02b2-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d02b2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d02b2-105">DSC är en plattform i PowerShell som gör det möjligt för dig att hantera IT-ADMINISTRATÖREN och utveckling infrastruktur med konfiguration som kod.</span><span class="sxs-lookup"><span data-stu-id="d02b2-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="d02b2-106">En översikt över företagets fördelar med hjälp av DSC, se [Desired Configuration översikt över för beslutsfattare](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="d02b2-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="d02b2-107">En översikt över engineering fördelarna med att använda DSC, se [Desired Configuration översikt över för Engineers](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="d02b2-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="d02b2-108">Om du vill börja använda DSC snabbt, se [DSC Snabbstart](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="d02b2-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="d02b2-109">Viktiga begrepp</span><span class="sxs-lookup"><span data-stu-id="d02b2-109">Key Concepts</span></span>

<span data-ttu-id="d02b2-110">DSC är en deklarativ plattform som används för konfiguration, distribution och hantering av system.</span><span class="sxs-lookup"><span data-stu-id="d02b2-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="d02b2-111">Det består av tre huvudkomponenter:</span><span class="sxs-lookup"><span data-stu-id="d02b2-111">It consists of three primary components:</span></span>

- <span data-ttu-id="d02b2-112">[Konfigurationer](configurations.md) är deklarativ PowerShell-skript som definierar och konfigurerar instanser av resurser.</span><span class="sxs-lookup"><span data-stu-id="d02b2-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="d02b2-113">Vid konfigurationen, DSC (och resurser som anropas av konfigurationen) kommer helt enkelt ”gör det så”, se till att systemet finns i tillståndet utvecklas av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d02b2-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="d02b2-114">DSC-konfigurationer är också idempotent: den lokala Configuration Manager (MGM) kommer att fortsätta att säkerställa att datorer har konfigurerats på det tillstånd konfigurationen deklarerar.</span><span class="sxs-lookup"><span data-stu-id="d02b2-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="d02b2-115">[Resurser](resources.md) DSC ”gör den det” tillhör.</span><span class="sxs-lookup"><span data-stu-id="d02b2-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="d02b2-116">De innehåller koden som placeras och hålla målet för en konfiguration i det angivna tillståndet.</span><span class="sxs-lookup"><span data-stu-id="d02b2-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="d02b2-117">Resurser finns i PowerShell-moduler och kan skrivas till modellen är något som allmänt som en fil eller en Windows-process eller så specifik som en IIS-server eller en virtuell dator som körs i Azure.</span><span class="sxs-lookup"><span data-stu-id="d02b2-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="d02b2-118">Den [lokala Configuration Manager (MGM)](metaConfig.md) är motorn som underlättar DSC interaktionen mellan resurser och konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="d02b2-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="d02b2-119">MGM genomsöker regelbundet systemet använder Kontrollflöde som implementeras av resurser för att säkerställa att tillståndet som definierats av en upprätthålls.</span><span class="sxs-lookup"><span data-stu-id="d02b2-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="d02b2-120">Om systemet har slut på tillstånd, anropar MGM koden i resurser för att ”gör den det” enligt konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d02b2-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d02b2-121">Se även</span><span class="sxs-lookup"><span data-stu-id="d02b2-121">See Also</span></span>

- [<span data-ttu-id="d02b2-122">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d02b2-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="d02b2-123">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="d02b2-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="d02b2-124">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="d02b2-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)