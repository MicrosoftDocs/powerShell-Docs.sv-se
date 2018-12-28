---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Konfigurera en pullklient med DSC
ms.openlocfilehash: b7cd6dc0087eb8368c5467df4c3c7266ed704451
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404691"
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurera en pullklient med DSC

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Varje målnoden måste vara ett meddelande om att använda pull-läge och de angivna Webbadressen eller filnamnet platsen där den kontaktar pull-servern för att hämta konfigurationer och resurser, och där det ska skicka rapportdata.

I följande avsnitt förklarar hur du ställer in pull-klienter:

* [Konfigurera en pullklient med konfigurationsnamn](pullClientConfigNames.md)
* [Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)

> **Obs**: Dessa avsnitt gäller för PowerShell 5.0. Om du vill konfigurera en hämtningsklient i PowerShell 4.0 finns i [konfigurera en hämtningsklient med konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md).