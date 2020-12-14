---
description: Beskriver telemetri som samlats in i PowerShell och hur du ska välja ut.
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 677d43b405fdc92e6b68d6e903847b11cb671a2c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710003"
---
# <a name="about-telemetry"></a><span data-ttu-id="e5f9e-103">Om telemetri</span><span class="sxs-lookup"><span data-stu-id="e5f9e-103">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="e5f9e-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e5f9e-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="e5f9e-105">Beskriver telemetri som samlats in i PowerShell och hur du ska välja ut.</span><span class="sxs-lookup"><span data-stu-id="e5f9e-105">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="e5f9e-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e5f9e-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="e5f9e-107">PowerShell skickar grundläggande telemetridata till Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e5f9e-107">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="e5f9e-108">Med den här informationen kan vi bättre förstå de miljöer där PowerShell används och göra det möjligt för oss att prioritera nya funktioner och korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="e5f9e-108">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="e5f9e-109">Följande telemetri punkter registreras:</span><span class="sxs-lookup"><span data-stu-id="e5f9e-109">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="e5f9e-110">Antal PowerShell-starter efter typ (API vs-konsol)</span><span class="sxs-lookup"><span data-stu-id="e5f9e-110">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="e5f9e-111">Antal unika PowerShell-användning</span><span class="sxs-lookup"><span data-stu-id="e5f9e-111">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="e5f9e-112">Antal av följande körnings typer:</span><span class="sxs-lookup"><span data-stu-id="e5f9e-112">Count of the following execution types:</span></span>
  - <span data-ttu-id="e5f9e-113">Program (inbyggda kommandon)</span><span class="sxs-lookup"><span data-stu-id="e5f9e-113">Application (native commands)</span></span>
  - <span data-ttu-id="e5f9e-114">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="e5f9e-114">ExternalScript</span></span>
  - <span data-ttu-id="e5f9e-115">Skript</span><span class="sxs-lookup"><span data-stu-id="e5f9e-115">Script</span></span>
  - <span data-ttu-id="e5f9e-116">Funktion</span><span class="sxs-lookup"><span data-stu-id="e5f9e-116">Function</span></span>
  - <span data-ttu-id="e5f9e-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e5f9e-117">Cmdlet</span></span>
- <span data-ttu-id="e5f9e-118">Antal aktiverade Microsoft-ägda experimentella funktioner eller experimentella funktioner som levereras med PowerShell</span><span class="sxs-lookup"><span data-stu-id="e5f9e-118">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="e5f9e-119">Antal värdbaserade sessioner</span><span class="sxs-lookup"><span data-stu-id="e5f9e-119">Count of hosted sessions</span></span>
- <span data-ttu-id="e5f9e-120">Antal Microsoft-ägda moduler som lästs in</span><span class="sxs-lookup"><span data-stu-id="e5f9e-120">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="e5f9e-121">Dessa data inkluderar operativ systemets namn, OS-version, PowerShell-version och distributions kanal.</span><span class="sxs-lookup"><span data-stu-id="e5f9e-121">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="e5f9e-122">Om du vill välja bort den här Telemetrin ställer du in miljövariabeln POWERSHELL_TELEMETRY_OPTOUT till sant, ja eller 1.</span><span class="sxs-lookup"><span data-stu-id="e5f9e-122">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>

