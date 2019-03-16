---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en pullklient med DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054262"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="fb9d5-103">Konfigurera en pullklient med DSC</span><span class="sxs-lookup"><span data-stu-id="fb9d5-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="fb9d5-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fb9d5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fb9d5-105">Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="fb9d5-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="fb9d5-106">Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="fb9d5-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="fb9d5-107">Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna Webbadressen eller filnamnet platsen där den kontaktar pull-servern för att hämta konfigurationer och resurser, och där det ska skicka rapportdata.</span><span class="sxs-lookup"><span data-stu-id="fb9d5-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="fb9d5-108">I följande avsnitt förklarar hur du ställer in pull-klienter:</span><span class="sxs-lookup"><span data-stu-id="fb9d5-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="fb9d5-109">Konfigurera en pullklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="fb9d5-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="fb9d5-110">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="fb9d5-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="fb9d5-111">Dessa avsnitt gäller för PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="fb9d5-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="fb9d5-112">Om du vill konfigurera en hämtningsklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="fb9d5-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>