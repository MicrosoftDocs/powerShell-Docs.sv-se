---
title: Använda PowerShell i Docker
description: Så här använder du PowerShell som är förinstallerat i en Docker-avbildning.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: b16a31a04ca863ab55c7c9718b1a1a973e61ee46
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80646379"
---
# <a name="using-powershell-in-docker"></a>Använda PowerShell i Docker

Vi publicerar Docker-avbildningar med PowerShell förinstallerat. Den här artikeln visar hur du kommer igång med PowerShell i Docker-behållaren.

## <a name="finding-available-images"></a>Hitta tillgängliga bilder

De publicerade avbildningarna kräver Docker 17,05 eller senare. Det förväntas också att du kan köra Docker utan `sudo` eller lokal administratörs behörighet. Följ Docker-officiella [instruktioner][install] för att installera `docker` på rätt sätt.

Versions behållare härleds från den officiella distributions avbildningen, `centos:7`till exempel, och installera sedan beroenden och installera sedan PowerShell-paketet.

Dessa behållare är Live på [Hub.Docker.com/r/Microsoft/PowerShell][docker-release].

Mer information om dessa Docker-avbildningar finns i [PowerShell-Docker-][PowerShell-Docker] lagringsplatsen på GitHub.

## <a name="using-powershell-in-a-container"></a>Använda PowerShell i en behållare

Följande steg visar de Docker-kommandon som krävs för att ladda ned avbildningen och starta en interaktiv PowerShell-session.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>Ta bort avbildningen när den inte längre behövs

Följande kommando används för att ta bort Docker-avbildningen när du inte längre behöver den.

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>Juridisk information och licensiering

PowerShell licensieras enligt [MIT-licensen][].

### <a name="windows-docker-file-and-image-licenses"></a>Windows Docker-fil och avbildnings licenser

Genom att begära och använda behållar-OS-avbildningen för Windows-behållare, godkänner du, förstår och godkänner tilläggs licens villkoren på Docker Hub:

- [Windows Server Core][Window Server Core]
- [Nano Server][Nano Server]

### <a name="telemetry"></a>Telemetri

Som standard samlar PowerShell in begränsad telemetri utan personligt identifierbar information för att hjälpa till att utveckla framtida versioner av PowerShell. Om du vill välja att inte skicka telemetri skapar du en miljö variabel `POWERSHELL_TELEMETRY_OPTOUT` som kallas inställd på värdet `1` innan du startar PowerShell från den installerade platsen. Telemetrin som samlas in omfattas av [Microsofts sekretess policy][privacy].

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[MIT-licens]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
