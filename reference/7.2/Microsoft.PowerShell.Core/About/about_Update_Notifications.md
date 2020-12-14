---
description: Meddelar användare om start av PowerShell att en ny version av PowerShell har släppts.
Locale: en-US
ms.date: 01/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Update_Notifications
ms.openlocfilehash: 1a9f8cfec15f83566fdb77175dcc1aed6d9e8c34
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708851"
---
# <a name="about-update-notifications"></a><span data-ttu-id="762e6-103">Om uppdaterings meddelanden</span><span class="sxs-lookup"><span data-stu-id="762e6-103">About Update Notifications</span></span>

## <a name="short-description"></a><span data-ttu-id="762e6-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="762e6-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="762e6-105">Meddelar användare om start av PowerShell att en ny version av PowerShell har släppts.</span><span class="sxs-lookup"><span data-stu-id="762e6-105">Notifies users on startup of PowerShell that a new version of PowerShell has been released.</span></span>

## <a name="long-description"></a><span data-ttu-id="762e6-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="762e6-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="762e6-107">Från och med PowerShell 7,0 använder PowerShell uppdaterings meddelanden för att varna användarna om att det finns uppdateringar till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="762e6-107">Beginning with PowerShell 7.0, PowerShell uses update notifications to alert users to the existence of updates to PowerShell.</span></span> <span data-ttu-id="762e6-108">En gång per dag frågar PowerShell en online tjänst för att avgöra om det finns en nyare version.</span><span class="sxs-lookup"><span data-stu-id="762e6-108">Once per day, PowerShell queries an online service to determine if a newer version is available.</span></span>

> [!NOTE]
> <span data-ttu-id="762e6-109">Även om uppdaterings kontrollen sker under den första sessionen under en viss 24-timmarsperiod, kan du av prestanda skäl bara se meddelandet i början av efterföljande sessioner.</span><span class="sxs-lookup"><span data-stu-id="762e6-109">While the update check happens during the first session in a given 24-hour period, for performance reasons, the notification will only be shown on the start of subsequent sessions.</span></span> <span data-ttu-id="762e6-110">Av prestanda skäl kommer kontrollen inte att starta förrän minst tre sekunder efter att sessionen har påbörjats.</span><span class="sxs-lookup"><span data-stu-id="762e6-110">Also for performance reasons, the check will not start until at least 3 seconds after the session begins.</span></span>

<span data-ttu-id="762e6-111">Som standard prenumererar PowerShell på en av två olika meddelande kanaler, beroende på dess version/gren.</span><span class="sxs-lookup"><span data-stu-id="762e6-111">By default, PowerShell subscribes to one of two different notification channels depending on its version/branch.</span></span> <span data-ttu-id="762e6-112">Allmänt tillgängliga (GA) versioner av PowerShell returnerar endast aviseringar för uppdaterade GA-versioner.</span><span class="sxs-lookup"><span data-stu-id="762e6-112">Supported, Generally Available (GA) versions of PowerShell only return notifications for updated GA releases.</span></span> <span data-ttu-id="762e6-113">För hands versions-och Release Candidate (RC)-versioner meddelar uppdateringar om uppdateringar för Preview-, RC-och GA-versioner.</span><span class="sxs-lookup"><span data-stu-id="762e6-113">Preview and Release Candidate (RC) releases notify of updates to preview, RC, and GA releases.</span></span>

<span data-ttu-id="762e6-114">Du kan ändra beteendet för uppdaterings aviseringar med hjälp av `POWERSHELL_UPDATECHECK` miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="762e6-114">The update notification behavior can be changed using the `POWERSHELL_UPDATECHECK` environment variable.</span></span> <span data-ttu-id="762e6-115">Följande värden stöds:</span><span class="sxs-lookup"><span data-stu-id="762e6-115">The following values are supported:</span></span>

- <span data-ttu-id="762e6-116">`Off` inaktiverar funktionen för uppdaterings avisering</span><span class="sxs-lookup"><span data-stu-id="762e6-116">`Off` turns off the update notification feature</span></span>
- <span data-ttu-id="762e6-117">`Default` är detsamma som att inte definiera `POWERSHELL_UPDATECHECK` :</span><span class="sxs-lookup"><span data-stu-id="762e6-117">`Default` is the same as not defining `POWERSHELL_UPDATECHECK`:</span></span>
  - <span data-ttu-id="762e6-118">GA-versioner meddelar uppdateringar till GA-versioner</span><span class="sxs-lookup"><span data-stu-id="762e6-118">GA releases notify of updates to GA releases</span></span>
  - <span data-ttu-id="762e6-119">Preview/RC-versioner meddelar uppdateringar för GA och för hands versioner</span><span class="sxs-lookup"><span data-stu-id="762e6-119">Preview/RC releases notify of updates to GA and preview releases</span></span>
- <span data-ttu-id="762e6-120">`LTS` endast meddelanden om uppdateringar av LTS (långsiktig service) GA-versioner</span><span class="sxs-lookup"><span data-stu-id="762e6-120">`LTS` only notifies of updates to long-term-servicing (LTS) GA releases</span></span>

<span data-ttu-id="762e6-121">Följande slut punkter används för närvarande för att fastställa den senaste versionen av varje kanal:</span><span class="sxs-lookup"><span data-stu-id="762e6-121">The following endpoints are currently used for determining the latest version of each channel:</span></span>

- <span data-ttu-id="762e6-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span><span class="sxs-lookup"><span data-stu-id="762e6-122">`LTS`: https://aka.ms/pwsh-buildinfo-lts</span></span>
- <span data-ttu-id="762e6-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span><span class="sxs-lookup"><span data-stu-id="762e6-123">`Stable`: https://aka.ms/pwsh-buildinfo-stable</span></span>
- <span data-ttu-id="762e6-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span><span class="sxs-lookup"><span data-stu-id="762e6-124">`Preview`: https://aka.ms/pwsh-buildinfo-preview</span></span>

<span data-ttu-id="762e6-125">Uppdaterings meddelandet ger inte något sätt att automatiskt uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="762e6-125">The update notification doesn't provide any way to automatically update PowerShell.</span></span> <span data-ttu-id="762e6-126">I framtiden kan det finnas fler instruktioner eller funktioner att uppdatera från PowerShell, men idag bör du använda samma installations metod som du använde för att installera PowerShell för att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="762e6-126">In the future, there may be more instructions or capabilities to update from within PowerShell, but today, you should use the same install mechanism you used to install PowerShell to update it.</span></span>

