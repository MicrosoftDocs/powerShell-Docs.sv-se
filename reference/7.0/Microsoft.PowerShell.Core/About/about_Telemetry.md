---
description: Beskriver telemetri som samlats in i PowerShell och hur du ska välja ut.
keywords: powershell
Locale: en-US
ms.date: 08/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_telemetry?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Telemetry
ms.openlocfilehash: 4aeab828d66d1f015946051419facd81ce2b78c1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269924"
---
# <a name="about-telemetry"></a><span data-ttu-id="6f086-104">Om telemetri</span><span class="sxs-lookup"><span data-stu-id="6f086-104">About Telemetry</span></span>

## <a name="short-description"></a><span data-ttu-id="6f086-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6f086-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="6f086-106">Beskriver telemetri som samlats in i PowerShell och hur du ska välja ut.</span><span class="sxs-lookup"><span data-stu-id="6f086-106">Describes the telemetry collected in PowerShell and how to opt-out.</span></span>

## <a name="long-description"></a><span data-ttu-id="6f086-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6f086-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6f086-108">PowerShell skickar grundläggande telemetridata till Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6f086-108">PowerShell sends basic telemetry data to Microsoft.</span></span>
<span data-ttu-id="6f086-109">Med den här informationen kan vi bättre förstå de miljöer där PowerShell används och göra det möjligt för oss att prioritera nya funktioner och korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="6f086-109">This data allows us to better understand the environments where PowerShell is used and enables us to prioritize new features and fixes.</span></span>
<span data-ttu-id="6f086-110">Följande telemetri punkter registreras:</span><span class="sxs-lookup"><span data-stu-id="6f086-110">The following telemetry points are recorded:</span></span>

- <span data-ttu-id="6f086-111">Antal PowerShell-starter efter typ (API vs-konsol)</span><span class="sxs-lookup"><span data-stu-id="6f086-111">Count of PowerShell Starts by type (API vs console)</span></span>
- <span data-ttu-id="6f086-112">Antal unika PowerShell-användning</span><span class="sxs-lookup"><span data-stu-id="6f086-112">Count of unique PowerShell usage</span></span>
- <span data-ttu-id="6f086-113">Antal av följande körnings typer:</span><span class="sxs-lookup"><span data-stu-id="6f086-113">Count of the following execution types:</span></span>
  - <span data-ttu-id="6f086-114">Program (inbyggda kommandon)</span><span class="sxs-lookup"><span data-stu-id="6f086-114">Application (native commands)</span></span>
  - <span data-ttu-id="6f086-115">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="6f086-115">ExternalScript</span></span>
  - <span data-ttu-id="6f086-116">Skript</span><span class="sxs-lookup"><span data-stu-id="6f086-116">Script</span></span>
  - <span data-ttu-id="6f086-117">Funktion</span><span class="sxs-lookup"><span data-stu-id="6f086-117">Function</span></span>
  - <span data-ttu-id="6f086-118">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f086-118">Cmdlet</span></span>
- <span data-ttu-id="6f086-119">Antal aktiverade Microsoft-ägda experimentella funktioner eller experimentella funktioner som levereras med PowerShell</span><span class="sxs-lookup"><span data-stu-id="6f086-119">Count of enabled Microsoft owned experimental features or experimental features shipped with PowerShell</span></span>
- <span data-ttu-id="6f086-120">Antal värdbaserade sessioner</span><span class="sxs-lookup"><span data-stu-id="6f086-120">Count of hosted sessions</span></span>
- <span data-ttu-id="6f086-121">Antal Microsoft-ägda moduler som lästs in</span><span class="sxs-lookup"><span data-stu-id="6f086-121">Count of Microsoft owned modules loaded</span></span>

<span data-ttu-id="6f086-122">Dessa data inkluderar operativ systemets namn, OS-version, PowerShell-version och distributions kanal.</span><span class="sxs-lookup"><span data-stu-id="6f086-122">This data includes the OS name, OS version, the PowerShell version, and the distribution channel.</span></span>

<span data-ttu-id="6f086-123">Om du vill välja bort den här Telemetrin ställer du in miljövariabeln POWERSHELL_TELEMETRY_OPTOUT till sant, ja eller 1.</span><span class="sxs-lookup"><span data-stu-id="6f086-123">To opt-out of this telemetry, set the environment variable POWERSHELL_TELEMETRY_OPTOUT to true, yes, or 1.</span></span>
