---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: "exempelmall av ett känt problem eller begränsning uppskrivning"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="595a0-103">Obs: ge en föreslagna beskrivande rubrik och en kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="595a0-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="595a0-104">Exempel: Felaktiga ExecutionPolicy fel</span><span class="sxs-lookup"><span data-stu-id="595a0-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="595a0-105">Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="595a0-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="595a0-106">Lösning</span><span class="sxs-lookup"><span data-stu-id="595a0-106">Resolution</span></span>

<span data-ttu-id="595a0-107">Lös problemet genom att ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="595a0-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

