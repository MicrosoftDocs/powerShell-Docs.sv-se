---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en DSC-hämtningsklient
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942799"
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurera en DSC-hämtningsklient

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Varje målnod måste uppmanas att använda pull-läge och tilldelas URL-adressen eller fil platsen där den kan kontakta pull-servern för att hämta konfigurationer och resurser, samt vart rapport data ska skickas.

I följande avsnitt förklaras hur du konfigurerar pull-klienter:

* [Konfigurera en pullklient med konfigurationsnamn](pullClientConfigNames.md)
* [Konfigurera en pullklient med konfigurations-ID](pullClientConfigID.md)

> [!NOTE]
> De här avsnitten gäller för PowerShell 5,0. Om du vill konfigurera en pull-klient i PowerShell 4,0, se [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md).