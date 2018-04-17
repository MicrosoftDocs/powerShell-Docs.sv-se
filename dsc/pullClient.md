---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Installera en DSC pull-klient
ms.openlocfilehash: 4c56671313b93cc12ce9460ce41e1710e0d6a526
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="43b59-103">Installera en DSC pull-klient</span><span class="sxs-lookup"><span data-stu-id="43b59-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="43b59-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="43b59-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43b59-105">Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="43b59-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="43b59-106">Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="43b59-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="43b59-107">Varje målnoden måste uppmanas att använda pull-läge och angivna URL- eller platsen där den kontaktar pull-servern för att hämta konfigurationer och resurser och den bör skicka rapportdata.</span><span class="sxs-lookup"><span data-stu-id="43b59-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="43b59-108">I följande avsnitt förklaras hur du ställer in pull-klienter:</span><span class="sxs-lookup"><span data-stu-id="43b59-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="43b59-109">Konfigurera en pullklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="43b59-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="43b59-110">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="43b59-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="43b59-111">**Obs**: dessa avsnitt gäller för PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="43b59-111">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="43b59-112">Om du vill konfigurera en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="43b59-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>