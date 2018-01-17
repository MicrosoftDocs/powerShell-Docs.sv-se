---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Inbyggda Desired State Configuration-resurser för Linux"
ms.openlocfilehash: e268cb2ee8a246f18216b34e5e2a6d512f15e18c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="built-in-desired-state-configuration-resources-for-linux"></a><span data-ttu-id="e8b80-103">Inbyggda Desired State Configuration-resurser för Linux</span><span class="sxs-lookup"><span data-stu-id="e8b80-103">Built-In Desired State Configuration Resources for Linux</span></span>

<span data-ttu-id="e8b80-104">Resurser är byggstenar som du kan använda för att skriva ett skript med PowerShell önskad tillstånd Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="e8b80-104">Resources are building blocks that you can use to write a PowerShell Desired State Configuration (DSC) script.</span></span> <span data-ttu-id="e8b80-105">DSC för Linux innehåller en uppsättning inbyggda funktioner för att konfigurera resurser, till exempel filer och mappar, paket, miljövariabler och tjänster och processer.</span><span class="sxs-lookup"><span data-stu-id="e8b80-105">DSC for Linux comes with a set of built-in functionality for configuring resources such as files and folders, packages, environment variables, and services and processes.</span></span>

## <a name="built-in-resources"></a><span data-ttu-id="e8b80-106">Inbyggda resurser</span><span class="sxs-lookup"><span data-stu-id="e8b80-106">Built-in resources</span></span> 

<span data-ttu-id="e8b80-107">Följande tabell innehåller en lista över de här resurserna och länkarna till avsnitt som beskrivs i detalj.</span><span class="sxs-lookup"><span data-stu-id="e8b80-107">The following table provides a list of these resources and links to topics that describe them in detail.</span></span>

* <span data-ttu-id="e8b80-108">[nxArchive resurs](lnxArchiveResource.md)– ger dig möjlighet att packa upp (.tar, .zip) arkivfiler vid en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="e8b80-108">[nxArchive Resource](lnxArchiveResource.md)--Provides a mechanism to unpack archive (.tar, .zip) files at a specific path.</span></span>
* <span data-ttu-id="e8b80-109">[nxEnvironment resurs](lnxEnvironmentResource.md)--hanterar miljövariabler på målnoder.</span><span class="sxs-lookup"><span data-stu-id="e8b80-109">[nxEnvironment Resource](lnxEnvironmentResource.md)--Manages environment variables on target nodes.</span></span> 
* <span data-ttu-id="e8b80-110">[nxFile resurs](lnxFileResource.md)--hanterar Linux-filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="e8b80-110">[nxFile Resource](lnxFileResource.md)--Manages Linux files and directories.</span></span> 
* <span data-ttu-id="e8b80-111">[nxFileLine resurs](lnxFileLineResource.md)--hanterar enskilda rader i en Linux-fil.</span><span class="sxs-lookup"><span data-stu-id="e8b80-111">[nxFileLine Resource](lnxFileLineResource.md)--Manages individual lines in a Linux file.</span></span> 
* <span data-ttu-id="e8b80-112">[nxGroup resurs](lnxGroupResource.md)--hanterar lokala Linux-grupper.</span><span class="sxs-lookup"><span data-stu-id="e8b80-112">[nxGroup Resource](lnxGroupResource.md)--Manages local Linux groups.</span></span> 
* <span data-ttu-id="e8b80-113">[nxPackage resurs](lnxPackageResource.md)--hanterar paket på Linux-noder.</span><span class="sxs-lookup"><span data-stu-id="e8b80-113">[nxPackage Resource](lnxPackageResource.md)--Manages packages on Linux nodes.</span></span>
* <span data-ttu-id="e8b80-114">[nxScript resurs](lnxScriptResource.md)--kör skript på målnoder.</span><span class="sxs-lookup"><span data-stu-id="e8b80-114">[nxScript Resource](lnxScriptResource.md)--Runs scripts on target nodes.</span></span>
* <span data-ttu-id="e8b80-115">[nxService resurs](lnxServiceResource.md)--hanterar Linux-tjänster (Daemon).</span><span class="sxs-lookup"><span data-stu-id="e8b80-115">[nxService Resource](lnxServiceResource.md)--Manages Linux services (daemons).</span></span>
* <span data-ttu-id="e8b80-116">[nxSshAuthorizedKeys resurs](lnxSshAuthorizedKeysResource.md)--hanterar offentliga ssh nycklar för en Linux-användare.</span><span class="sxs-lookup"><span data-stu-id="e8b80-116">[nxSshAuthorizedKeys Resource](lnxSshAuthorizedKeysResource.md)--Manages public ssh keys for a Linux user.</span></span> 
* <span data-ttu-id="e8b80-117">[nxUser resurs](lnxUserResource.md)--hanterar lokala Linux-användare.</span><span class="sxs-lookup"><span data-stu-id="e8b80-117">[nxUser Resource](lnxUserResource.md)--Manages local Linux users.</span></span> 
  
