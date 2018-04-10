---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: e393c8fe2e1ba8d68ba9aa1b656d1e5ebfad30e8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-resources"></a>DSC-resurser

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen. En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.

En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.  Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.

I följande avsnitt beskrivs DSC-resurser:

- [Inbyggda DSC-resurser](builtInResource.md)
- [Skapa anpassade DSC-resurser](authoringResource.md)
- [Inbyggda DSC-resurser för Linux](lnxBuiltInResources.md)