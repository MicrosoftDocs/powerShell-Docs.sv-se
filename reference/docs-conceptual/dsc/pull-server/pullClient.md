---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en DSC-hämtningsklient
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942799"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="eaa8f-103">Konfigurera en DSC-hämtningsklient</span><span class="sxs-lookup"><span data-stu-id="eaa8f-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="eaa8f-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="eaa8f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eaa8f-105">Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="eaa8f-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="eaa8f-106">Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="eaa8f-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="eaa8f-107">Varje målnod måste uppmanas att använda pull-läge och tilldelas URL-adressen eller fil platsen där den kan kontakta pull-servern för att hämta konfigurationer och resurser, samt vart rapport data ska skickas.</span><span class="sxs-lookup"><span data-stu-id="eaa8f-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="eaa8f-108">I följande avsnitt förklaras hur du konfigurerar pull-klienter:</span><span class="sxs-lookup"><span data-stu-id="eaa8f-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="eaa8f-109">Konfigurera en pullklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="eaa8f-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="eaa8f-110">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="eaa8f-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="eaa8f-111">De här avsnitten gäller för PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="eaa8f-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="eaa8f-112">Om du vill konfigurera en pull-klient i PowerShell 4,0, se [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="eaa8f-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>