---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="5dcf3-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="5dcf3-103">DSC Resources</span></span>

><span data-ttu-id="5dcf3-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5dcf3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5dcf3-105">Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5dcf3-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="5dcf3-106">En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.</span><span class="sxs-lookup"><span data-stu-id="5dcf3-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="5dcf3-107">En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="5dcf3-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="5dcf3-108">Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.</span><span class="sxs-lookup"><span data-stu-id="5dcf3-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="5dcf3-109">I följande avsnitt beskrivs DSC-resurser:</span><span class="sxs-lookup"><span data-stu-id="5dcf3-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="5dcf3-110">Inbyggda DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="5dcf3-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="5dcf3-111">Skapa anpassade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="5dcf3-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="5dcf3-112">Inbyggda DSC-resurser för Linux</span><span class="sxs-lookup"><span data-stu-id="5dcf3-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)