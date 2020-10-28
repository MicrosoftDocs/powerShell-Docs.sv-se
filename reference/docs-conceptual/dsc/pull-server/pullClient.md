---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Konfigurera en DSC-hämtningsklient
description: Den här artikeln är en översikt över den information som är tillgänglig för konfigurering av DSC-pull-klienten.
ms.openlocfilehash: 584af3aee46d801e363422ae7a197348231a1442
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646818"
---
# <a name="setting-up-a-dsc-pull-client"></a>Konfigurera en DSC-hämtningsklient

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst* ) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Varje målnod måste uppmanas att använda pull-läge och tilldelas URL-adressen eller fil platsen där den kan kontakta pull-servern för att hämta konfigurationer och resurser, samt vart rapport data ska skickas.

I följande avsnitt förklaras hur du konfigurerar pull-klienter:

- Konfigurera [en pull-klient med konfigurations namn](pullClientConfigNames.md) 
*- Konfigurera [en pull-klient med konfigurations-ID](pullClientConfigID.md)

> [!NOTE]
> De här avsnitten gäller för PowerShell 5,0. Om du vill konfigurera en pull-klient i PowerShell 4,0, se [Konfigurera en pull-klient med konfigurations-ID i PowerShell 4,0](pullClientConfigID4.md).
