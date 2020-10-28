---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en DSC-hämtningsklient
description: Den här artikeln är en översikt över den information som är tillgänglig för konfigurering av DSC-pull-klienten.
ms.openlocfilehash: 584af3aee46d801e363422ae7a197348231a1442
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646818"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="3ff6e-104">Konfigurera en DSC-hämtningsklient</span><span class="sxs-lookup"><span data-stu-id="3ff6e-104">Setting up a DSC pull client</span></span>

> <span data-ttu-id="3ff6e-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="3ff6e-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3ff6e-106">Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="3ff6e-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="3ff6e-107">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="3ff6e-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="3ff6e-108">Varje målnod måste uppmanas att använda pull-läge och tilldelas URL-adressen eller fil platsen där den kan kontakta pull-servern för att hämta konfigurationer och resurser, samt vart rapport data ska skickas.</span><span class="sxs-lookup"><span data-stu-id="3ff6e-108">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="3ff6e-109">I följande avsnitt förklaras hur du konfigurerar pull-klienter:</span><span class="sxs-lookup"><span data-stu-id="3ff6e-109">The following topics explain how to set up pull clients:</span></span>

- <span data-ttu-id="3ff6e-110">Konfigurera [en pull-klient med konfigurations namn](pullClientConfigNames.md) 
\*- Konfigurera [en pull-klient med konfigurations-ID](pullClientConfigID.md)</span><span class="sxs-lookup"><span data-stu-id="3ff6e-110">[Setting up a pull client using configuration names](pullClientConfigNames.md)
\*-[Setting up a pull client using configuration ID](pullClientConfigID.md)</span></span>

> [!NOTE]
> <span data-ttu-id="3ff6e-111">De här avsnitten gäller för PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="3ff6e-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="3ff6e-112">Om du vill konfigurera en pull-klient i PowerShell 4,0, se [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="3ff6e-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>
