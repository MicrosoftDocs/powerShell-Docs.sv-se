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
# <a name="about-telemetry"></a>Om telemetri

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver telemetri som samlats in i PowerShell och hur du ska välja ut.

## <a name="long-description"></a>LÅNG BESKRIVNING

PowerShell skickar grundläggande telemetridata till Microsoft.
Med den här informationen kan vi bättre förstå de miljöer där PowerShell används och göra det möjligt för oss att prioritera nya funktioner och korrigeringar.
Följande telemetri punkter registreras:

- Antal PowerShell-starter efter typ (API vs-konsol)
- Antal unika PowerShell-användning
- Antal av följande körnings typer:
  - Program (inbyggda kommandon)
  - ExternalScript
  - Skript
  - Funktion
  - Cmdlet
- Antal aktiverade Microsoft-ägda experimentella funktioner eller experimentella funktioner som levereras med PowerShell
- Antal värdbaserade sessioner
- Antal Microsoft-ägda moduler som lästs in

Dessa data inkluderar operativ systemets namn, OS-version, PowerShell-version och distributions kanal.

Om du vill välja bort den här Telemetrin ställer du in miljövariabeln POWERSHELL_TELEMETRY_OPTOUT till sant, ja eller 1.

