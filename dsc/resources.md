---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a><span data-ttu-id="a7c6e-103">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="a7c6e-103">DSC Resources</span></span>

><span data-ttu-id="a7c6e-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a7c6e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a7c6e-105">Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a7c6e-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="a7c6e-106">En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.</span><span class="sxs-lookup"><span data-stu-id="a7c6e-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="a7c6e-107">En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="a7c6e-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="a7c6e-108">Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.</span><span class="sxs-lookup"><span data-stu-id="a7c6e-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>  

<span data-ttu-id="a7c6e-109">I följande avsnitt beskrivs DSC-resurser:</span><span class="sxs-lookup"><span data-stu-id="a7c6e-109">The following topics describe DSC resources:</span></span>

- [<span data-ttu-id="a7c6e-110">Inbyggda DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="a7c6e-110">Built-In DSC resources</span></span>](builtInResource.md)
- [<span data-ttu-id="a7c6e-111">Skapa anpassade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="a7c6e-111">Build custom DSC resources</span></span>](authoringResource.md)
- [<span data-ttu-id="a7c6e-112">Inbyggda DSC-resurser för Linux</span><span class="sxs-lookup"><span data-stu-id="a7c6e-112">Built-In DSC resources for Linux</span></span>](lnxBuiltInResources.md)

