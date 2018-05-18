---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
title: exempelmall av ett känt problem eller begränsning uppskrivning
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
><span data-ttu-id="90651-103">Obs: ge en föreslagna beskrivande rubrik och en kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="90651-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="90651-104">Exempel: Felaktiga ExecutionPolicy fel</span><span class="sxs-lookup"><span data-stu-id="90651-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="90651-105">Användningen av PowerShell-moduler och DSC-resurser kan resultera i fel som rapporteras om körningsprincipen på Windows 7.</span><span class="sxs-lookup"><span data-stu-id="90651-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="90651-106">Lösning</span><span class="sxs-lookup"><span data-stu-id="90651-106">Resolution</span></span>

<span data-ttu-id="90651-107">Lös problemet genom att ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):</span><span class="sxs-lookup"><span data-stu-id="90651-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
