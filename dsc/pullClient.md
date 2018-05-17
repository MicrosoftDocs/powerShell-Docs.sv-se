---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Installera en DSC pull-klient
ms.openlocfilehash: 7f8758bd7145518e30e9c28b74d0db5d74dfaab3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="setting-up-a-dsc-pull-client"></a>Installera en DSC pull-klient

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Varje målnoden måste uppmanas att använda pull-läge och angivna URL- eller platsen där den kontaktar pull-servern för att hämta konfigurationer och resurser och den bör skicka rapportdata.

I följande avsnitt förklaras hur du ställer in pull-klienter:

* [Konfigurera en pullklient med konfigurationsnamn](pullClientConfigNames.md)
* [Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)

> **Obs**: dessa avsnitt gäller för PowerShell 5.0. Om du vill konfigurera en pull-klient i PowerShell 4.0 finns [installera en pull-klient med hjälp av konfigurations-ID i PowerShell 4.0](pullClientConfigID4.md).