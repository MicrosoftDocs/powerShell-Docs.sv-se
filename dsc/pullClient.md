---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Installera en DSC pull-klient
ms.openlocfilehash: e6d73187566db2756ae24dabe0a825fffb5ecce0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="124d1-103">Installera en DSC pull-klient</span><span class="sxs-lookup"><span data-stu-id="124d1-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="124d1-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="124d1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="124d1-105">Varje målnoden måste uppmanas att använda pull-läge och angivna URL- eller platsen där den kontaktar pull-servern för att hämta konfigurationer och resurser och den bör skicka rapportdata.</span><span class="sxs-lookup"><span data-stu-id="124d1-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="124d1-106">I följande avsnitt förklaras hur du ställer in pull-klienter:</span><span class="sxs-lookup"><span data-stu-id="124d1-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="124d1-107">Konfigurera en pullklient med konfigurationsnamn</span><span class="sxs-lookup"><span data-stu-id="124d1-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="124d1-108">Konfigurera en pullklient med konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="124d1-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="124d1-109">**Obs**: dessa avsnitt gäller för PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="124d1-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="124d1-110">Om du vill konfigurera en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="124d1-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>