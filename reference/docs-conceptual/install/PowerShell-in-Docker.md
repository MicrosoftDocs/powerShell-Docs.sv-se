---
title: Använda PowerShell i Docker
description: Så här använder du PowerShell som är förinstallerat i en Docker-avbildning.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279952"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="95f4d-103">Använda PowerShell i Docker</span><span class="sxs-lookup"><span data-stu-id="95f4d-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="95f4d-104">Vi publicerar Docker-avbildningar med PowerShell förinstallerat.</span><span class="sxs-lookup"><span data-stu-id="95f4d-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="95f4d-105">Den här artikeln visar hur du kommer igång med PowerShell i Docker-behållaren.</span><span class="sxs-lookup"><span data-stu-id="95f4d-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="95f4d-106">Hitta tillgängliga bilder</span><span class="sxs-lookup"><span data-stu-id="95f4d-106">Finding available images</span></span>

<span data-ttu-id="95f4d-107">De publicerade avbildningarna kräver Docker 17,05 eller senare.</span><span class="sxs-lookup"><span data-stu-id="95f4d-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="95f4d-108">Det förväntas också att du kan köra Docker utan `sudo` eller lokal administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="95f4d-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="95f4d-109">Följ Docker-officiella [instruktioner][install] för att installera `docker` korrekt.</span><span class="sxs-lookup"><span data-stu-id="95f4d-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="95f4d-110">Versions behållare härleds från den officiella distributions avbildningen, till exempel `centos:7`, och installera sedan beroenden och installera sedan PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="95f4d-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="95f4d-111">Dessa behållare är Live på [Hub.Docker.com/r/Microsoft/PowerShell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="95f4d-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="95f4d-112">Mer information om dessa Docker-avbildningar finns i [PowerShell-Docker-][PowerShell-Docker] lagringsplatsen på GitHub.</span><span class="sxs-lookup"><span data-stu-id="95f4d-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="95f4d-113">Använda PowerShell i en behållare</span><span class="sxs-lookup"><span data-stu-id="95f4d-113">Using PowerShell in a container</span></span>

<span data-ttu-id="95f4d-114">Följande steg visar de Docker-kommandon som krävs för att ladda ned avbildningen och starta en interaktiv PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="95f4d-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="95f4d-115">Ta bort avbildningen när den inte längre behövs</span><span class="sxs-lookup"><span data-stu-id="95f4d-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="95f4d-116">Följande kommando används för att ta bort Docker-behållaren när du inte längre behöver den.</span><span class="sxs-lookup"><span data-stu-id="95f4d-116">The following command is used to delete the Docker container when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="95f4d-117">Juridisk information och licensiering</span><span class="sxs-lookup"><span data-stu-id="95f4d-117">Legal and Licensing</span></span>

<span data-ttu-id="95f4d-118">PowerShell licensieras enligt [MIT-licens][].</span><span class="sxs-lookup"><span data-stu-id="95f4d-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="95f4d-119">Windows Docker-fil och avbildnings licenser</span><span class="sxs-lookup"><span data-stu-id="95f4d-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="95f4d-120">Genom att begära och använda behållar-OS-avbildningen för Windows-behållare, godkänner du, förstår och godkänner tilläggs licens villkoren på Docker Hub:</span><span class="sxs-lookup"><span data-stu-id="95f4d-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="95f4d-121">[Windows Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="95f4d-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="95f4d-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="95f4d-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="95f4d-123">Telemetri</span><span class="sxs-lookup"><span data-stu-id="95f4d-123">Telemetry</span></span>

<span data-ttu-id="95f4d-124">Som standard samlar PowerShell in begränsad telemetri utan personligt identifierbar information för att hjälpa till att utveckla framtida versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95f4d-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="95f4d-125">Om du vill välja att inte skicka telemetri skapar du en miljö variabel som kallas `POWERSHELL_TELEMETRY_OPTOUT` inställd på värdet `1` innan du startar PowerShell från den installerade platsen.</span><span class="sxs-lookup"><span data-stu-id="95f4d-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="95f4d-126">Telemetrin som samlas in omfattas av [Microsofts sekretess policy][privacy].</span><span class="sxs-lookup"><span data-stu-id="95f4d-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT-licens]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
