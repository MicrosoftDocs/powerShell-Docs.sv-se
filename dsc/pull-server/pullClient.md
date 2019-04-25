---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en DSC-hämtningsklient
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079650"
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurera en DSC-hämtningsklient

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna Webbadressen eller filnamnet platsen där den kontaktar pull-servern för att hämta konfigurationer och resurser, och där det ska skicka rapportdata.

I följande avsnitt förklarar hur du ställer in pull-klienter:

* [Konfigurera en pullklient med konfigurationsnamn](pullClientConfigNames.md)
* [Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)

> [!NOTE]
> Dessa avsnitt gäller för PowerShell 5.0. Om du vill konfigurera en hämtningsklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md).