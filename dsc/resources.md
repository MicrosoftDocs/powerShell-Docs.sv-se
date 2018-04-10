---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="94085-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="94085-103">DSC Resources</span></span>

><span data-ttu-id="94085-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="94085-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="94085-105">Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="94085-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="94085-106">En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.</span><span class="sxs-lookup"><span data-stu-id="94085-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="94085-107">En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="94085-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="94085-108">Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.</span><span class="sxs-lookup"><span data-stu-id="94085-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="94085-109">I följande avsnitt beskrivs DSC-resurser:</span><span class="sxs-lookup"><span data-stu-id="94085-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="94085-110">Inbyggda DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="94085-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="94085-111">Skapa anpassade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="94085-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="94085-112">Inbyggda DSC-resurser för Linux</span><span class="sxs-lookup"><span data-stu-id="94085-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)